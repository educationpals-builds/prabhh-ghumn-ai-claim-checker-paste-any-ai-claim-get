# Probe Board

This board tests the claim checker against 8 probes: 6 pre-generated calibration probes and 2 learner-authored probes. Each probe targets specific filter behavior.

---

## Five Filters Reference

| Filter | Key |
|--------|-----|
| Source & Incentives | `source_incentives` |
| Reasoning Holds | `reasoning_holds` |
| Evidence Shown | `evidence_shown` |
| Other Explanations | `other_explanations` |
| Survives Deployment | `survives_deployment` |

---

## Pre-Generated Probes (1–6)

### Probe 1: Vendor ROI Claim
**Input:** "Our AI solution delivers 10x ROI within 90 days for enterprise customers."  
**Target Filter:** `source_incentives`  
**Expected Behavior:** Dial scores 0–1; checker flags vendor profit motive and missing customer names.

### Probe 2: Benchmark Without Baseline
**Input:** "Our model scores 94% accuracy on the standard evaluation suite."  
**Target Filter:** `evidence_shown`  
**Expected Behavior:** Dial scores 0–1; checker identifies missing baseline comparison and methodology.

### Probe 3: Correlation as Causation
**Input:** "Companies using our platform see 40% higher retention—our AI drives engagement."  
**Target Filter:** `reasoning_holds`  
**Expected Behavior:** Dial scores 0–1; checker flags logical gap between correlation and causal claim.

### Probe 4: Single Study Generalization
**Input:** "A Stanford study proves this technique works across all domains."  
**Target Filter:** `other_explanations`  
**Expected Behavior:** Dial scores 0–1; checker notes single-study limitation and domain transfer assumptions.

### Probe 5: Lab-to-Production Leap
**Input:** "We achieved state-of-the-art results, ready for immediate clinical deployment."  
**Target Filter:** `survives_deployment`  
**Expected Behavior:** Dial scores 0–1; checker flags gap between benchmark performance and production readiness.

### Probe 6: Neutral Third-Party Report
**Input:** "Independent audit by [named firm] found 23% efficiency gains across 12 deployments with published methodology."  
**Target Filter:** `source_incentives`  
**Expected Behavior:** Dial scores 3–4; checker recognizes credible sourcing with verifiable details.

---

## Learner-Authored Probes (7–8)

### Probe 7: Learner Probe A
**Input:** I dont know I dont know I dont know I dont know I dont know   
**Target Filter:** Not specified  
**Expected Behavior:** Not specified

### Probe 8: Learner Probe B
**Input:** I dont know I dont know I dont know I dont know I dont know   
**Target Filter:** Not specified  
**Expected Behavior:** Not specified

---

## Results Grid

| Probe | Input Summary | Target Filter | Expected | Actual | Pass |
|-------|---------------|---------------|----------|--------|------|
| 1 | Vendor ROI Claim | `source_incentives` | 0–1 | — | — |
| 2 | Benchmark Without Baseline | `evidence_shown` | 0–1 | — | — |
| 3 | Correlation as Causation | `reasoning_holds` | 0–1 | — | — |
| 4 | Single Study Generalization | `other_explanations` | 0–1 | — | — |
| 5 | Lab-to-Production Leap | `survives_deployment` | 0–1 | — | — |
| 6 | Neutral Third-Party Report | `source_incentives` | 3–4 | — | — |
| 7 | Learner Probe A | — | — | — | — |
| 8 | Learner Probe B | — | — | — | — |

**Board Reading:** I dont know I dont know I dont know I dont know

---

## How to Run

1. Load each probe input into the claim checker
2. Record the dial scores for the target filter
3. Compare actual vs expected behavior
4. Mark pass/fail in the grid
5. Identify weakest filter across all 8 probes

See `tests/probes.jsonl` for machine-readable probe definitions.  
See `tests/run-local.md` for execution instructions.  
See `tests/pass-gate.md` for the gate this board must hold.
