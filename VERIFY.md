# Verification Protocol

This document explains how a stranger can verify that the claim checker works as intended.

## The Sample Claim

Paste this claim into the checker (via `/verify` or by starting a new check):

> "The model achieves human-level performance on medical reasoning benchmarks, outperforming physicians on diagnostic vignettes."

**Source context:** University press release summarizing a preprint; benchmark details in appendix C

## What to Confirm

The checker must identify the missing-evidence artifact. For this claim, the builder's evidence note states:

> There is no evidence available yet. How do you suggest we test?

A passing verification means the checker:

1. Processes the claim through the five filters (source_incentives, reasoning_holds, evidence_shown, other_explanations, survives_deployment)
2. Flags the **evidence_shown** filter as problematic
3. Names a specific missing artifact—the checker should call out what evidence is absent (baseline comparisons, sample sizes, methodology details, real-world validation data, or similar)

## Verification Steps

1. Open the claim checker
2. Paste the sample claim verbatim
3. Let the checker run its five-filter analysis
4. Confirm the output explicitly names what evidence is missing
5. Compare the checker's weakest-filter call against the builder's designation: **reasoning_holds**

## Pass Criteria

The verification passes if the checker surfaces the evidence gap. The checker should not accept the claim at face value given the stated context (a press release summarizing a preprint with benchmark details buried in an appendix).

## Decision Context

This claim matters because: Six months of lab roadmap gets committed to this base model

The decision deadline is: Lab meeting, next Thursday

A stranger verifying this checker should see it flag the evidence gap before that deadline would arrive.
