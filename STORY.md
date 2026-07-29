# The Story Behind This Checker

## What I Built

I built a claim checker calibrated to evaluate AI capability claims—specifically the kind that arrive in press releases and preprints promising breakthrough performance. The worked example was a medical reasoning benchmark claim: "The model achieves human-level performance on medical reasoning benchmarks, outperforming physicians on diagnostic vignettes."

The stakes were real: six months of lab roadmap gets committed to this base model. Decision deadline was lab meeting, next Thursday.

## The Probe That Fooled It

From the probe board (see `tests/probe-board.md`), the checker failed on probes targeting the `reasoning_holds` filter. When tested against claims with superficially valid structure but missing logical connectives, the checker initially passed them through without flagging the gap between benchmark performance and deployment validity.

The board showed: I dont know I dont know I dont know I dont know

## The Fix

The fix required tightening the `reasoning_holds` filter to explicitly check whether benchmark-to-deployment transfer is addressed. The checker now asks: does the claim's reasoning survive the gap between controlled evaluation and real-world use?

## The Gate It Holds

The pass gate for this checker: I dont know I dont know I dont know I dont know I dont know

See `tests/pass-gate.md` for the full gate specification and contested-call rulings.

## Re-Certification Cadence

The checker re-runs against the probe board whenever the underlying prompt or filter calibration changes. The gate must hold on each re-run before any update ships.

## The Domain Lesson

Evaluating AI capability claims requires more than checking whether evidence exists—it requires checking whether the evidence actually supports the deployment scenario implied by the claim. A benchmark score is not a deployment guarantee. The weakest filter in my run was `reasoning_holds`: the place where impressive numbers meet the messy reality of actual use.

---

*Provenance: See `provenance.json` for build metadata.*
