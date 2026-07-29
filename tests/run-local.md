# Run Local

Three ways to run the probe board against your claim checker, from zero-setup to CI.

---

## Rung 1: Manual (No Setup)

Paste each probe into your checker and compare the output to the expected behavior.

### Protocol

For each probe in `tests/probes.jsonl`:

1. Copy the `input` field (the claim text)
2. Paste it into your claim checker
3. Compare the checker's dial ratings against `expected`
4. Mark pass/fail for each filter target

### Manual Grid Template

| Probe | Input (first 40 chars) | Target Filter | Expected | Actual | Pass? |
|-------|------------------------|---------------|----------|--------|-------|
| 1     | ...                    | reasoning_holds | ... | ___ | ☐ |
| 2     | ...                    | evidence_shown | ... | ___ | ☐ |
| ...   | ...                    | ... | ... | ___ | ☐ |

Record your results beside each probe. The expected line lives in the JSONL.

---

## Rung 2: Script (~20 Lines)

A minimal runner that reads `tests/probes.jsonl`, calls your model, and prints the graded grid.

### Requirements

- API key in environment variable `CHECKER_API_KEY`
- Python 3.8+ with `requests`

### Runner Script

```python
#!/usr/bin/env python3
import os, json, requests

API_KEY = os.environ.get("CHECKER_API_KEY")
ENDPOINT = os.environ.get("CHECKER_ENDPOINT", "https://api.example.com/v1/chat")

def run_probe(probe):
    resp = requests.post(ENDPOINT, headers={"Authorization": f"Bearer {API_KEY}"},
        json={"messages": [{"role": "user", "content": probe["input"]}]})
    return resp.json().get("content", "")

def grade(output, expected):
    # Check if expected filter behavior appears in output
    return all(k in output.lower() for k in expected.get("flags", []))

with open("tests/probes.jsonl") as f:
    probes = [json.loads(line) for line in f if line.strip()]

print(f"{'ID':<6} {'Name':<30} {'Target':<20} {'Pass':<6}")
print("-" * 64)
passed = 0
for p in probes:
    out = run_probe(p)
    ok = grade(out, p.get("expected", {}))
    passed += ok
    print(f"{p['id']:<6} {p['name'][:28]:<30} {p['targets'][0]:<20} {'✓' if ok else '✗':<6}")

print("-" * 64)
print(f"Gate: {passed}/{len(probes)} probes passed")
```

### Usage

```bash
export CHECKER_API_KEY="your-key-here"
export CHECKER_ENDPOINT="https://your-checker-endpoint/v1/chat"
python run_probes.py
```

The script prints the graded grid and gate verdict at the end.

---

## Rung 3: Eval Tool / CI

Load `tests/probes.jsonl` into any eval runner so the board re-runs automatically when you change prompts.

### JSONL Format

Each line in `tests/probes.jsonl`:

```json
{"id": "probe_01", "name": "...", "input": "...", "targets": ["reasoning_holds"], "expected": {...}, "invariant": "..."}
```

### Integration Options

**Generic eval runner:**
```bash
eval-runner --probes tests/probes.jsonl --model your-checker --output results.json
```

**CI workflow (GitHub Actions example):**
```yaml
- name: Run probe board
  env:
    CHECKER_API_KEY: ${{ secrets.CHECKER_API_KEY }}
  run: python run_probes.py > board_results.txt

- name: Check gate
  run: grep "Gate:" board_results.txt | grep -q "8/8" || exit 1
```

The board re-runs on every prompt change. Failures block merge.

---

## Diffing Against the EP-Certified Board

After running locally, compare your results to the certified board on the listing:

1. Run the script and save output: `python run_probes.py > local_board.txt`
2. Download the EP-certified board from the listing page
3. Diff the two:

```bash
diff local_board.txt certified_board.txt
```

Any drift shows where your local checker diverges from the certified version. If you've modified prompts, this tells you which probes broke.

### What Drift Means

- **Same pass/fail, different dial values**: Calibration shift—review the filter in question
- **Pass → Fail**: Regression—your change broke something
- **Fail → Pass**: Improvement—but verify it's not a false positive

Re-run the full board before requesting re-certification.
