# Pass Gate

The quality gate this claim checker must hold before deployment and on every re-certification run.

---

## Gate Definition

**Learner-defined gate:**

> I dont know I dont know I dont know I dont know I dont know

---

## Gate Components

| Component | Value |
|-----------|-------|
| **Metric** | *(not specified)* |
| **Threshold** | *(not specified)* |
| **Re-run cadence** | *(not specified)* |

---

## Contested-Call Rulings

When the checker and a human evaluator disagree on a dial score, the ruling is recorded here with the opposing case preserved.

### Atlas's Opposing Cases

During calibration, the following contested calls were identified:

| Probe | Filter | Checker Score | Atlas Score | Ruling | Opposing Case |
|-------|--------|---------------|-------------|--------|---------------|
| *(No contested calls recorded — gate definition incomplete)* | — | — | — | — | — |

---

## How This Gate Works

1. **Run the probe board** — Execute all 8 probes from `tests/probes.jsonl`
2. **Score against expected behaviors** — Compare actual dial outputs to target behaviors
3. **Check threshold** — Verify the metric meets or exceeds the threshold
4. **Record contested calls** — When checker and human disagree, preserve both readings
5. **Pass or fail** — Gate holds only if threshold is met

---

## Re-Certification

The gate should be re-run:
- After any change to the system prompt in `blueprints/claim-checker.md`
- After updating the advisor stance in `skills/claim-advisor.skill.md`
- On the cadence specified in the gate definition above

---

## Current Status

**Gate status:** INCOMPLETE — learner gate definition does not specify metric, threshold, or re-run trigger.

See `tests/probe-board.md` for the full probe results that feed this gate.
