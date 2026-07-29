# AI Claim Checker

A five-filter credibility checker for AI claims. Paste any claim, get a structured read.

## How This Checker Was Built

This checker was built through a structured workshop: pin a real claim, run it through five filters, call a verdict, then wire the judgment into a reusable tool. The worked example below is the builder's own run—their calibration is baked into the checker.

## Worked Example

**The claim, verbatim:**

> "The model achieves human-level performance on medical reasoning benchmarks, outperforming physicians on diagnostic vignettes."

**Source:** University press release summarizing a preprint; benchmark details in appendix C

**What this decides:** Six months of lab roadmap gets committed to this base model

**Decision deadline:** Lab meeting, next Thursday

**Source & incentives:** We will be able to use this in our company and reduce our dependence on human labor by 15% if we deploy it

**Five-filter dial scores:**

| Filter | Score (0–4) |
|--------|-------------|
| source_incentives | 0 |
| reasoning_holds | 0 |
| evidence_shown | 0 |
| other_explanations | 0 |
| survives_deployment | 0 |

**Weakest filter:** reasoning_holds

**Evidence note:** There is no evidence available yet. How do you suggest we test?

**Verdict:** cant decide what to write here so I am going to skip this

**Flip condition:** the evidence is false, then it would flip the read.

**Sharpest question:** Is the data backed up by real world exeriments.

See [charter.md](charter.md) for the full run record.

## One-Paste Rebuild Block

To rebuild this checker in any chat model:

1. Copy the system instructions from [blueprints/claim-checker.md](blueprints/claim-checker.md)
2. Paste into your model's system prompt
3. Start a conversation with a claim to check

The checker uses five filters:
- **source_incentives** — Who benefits from this claim being believed?
- **reasoning_holds** — Does the logic survive scrutiny?
- **evidence_shown** — What's present vs. conspicuously missing?
- **other_explanations** — What else could explain the result?
- **survives_deployment** — Will this hold in real-world conditions?

## Repository Structure

- `charter.md` — The builder's full run: claim, stakes, dials, verdict
- `blueprints/claim-checker.md` — One-paste system instructions for the checker
- `prompts/claim-check-pack.md` — Five standalone prompts, one per filter
- `METHOD.md` — The framework explained
- `VERIFY.md` — How to verify this checker works
- `skills/claim-advisor.skill.md` — Portable skill file for assistant runtimes
- `data/seeded-claims.md` — Calibration record with seeded claims
- `tests/probe-board.md` — All 8 probes with results
- `tests/pass-gate.md` — The gate this checker must hold
- `tests/probes.jsonl` — Machine-readable probe export
- `tests/run-local.md` — Run-anywhere guide
- `STORY.md` — The builder's story

## Verification

See [VERIFY.md](VERIFY.md) for how a stranger can verify this checker works as claimed.

<!-- educationpals-build-verified -->
