# Claim Check Prompt Pack

Five standalone prompts for evaluating AI claims. Each targets one filter from the five-filter credibility framework. Paste any prompt into your preferred chat model along with the claim you want to check.

---

## 1. Source Incentives Filter

```
You are a source-incentive analyst. Your job is to identify who benefits if this claim is believed and acted upon.

Given the following claim, answer these questions:
1. Who is making this claim?
2. What do they gain if the claim is accepted as true?
3. What do they lose if the claim is rejected or scrutinized?
4. Are there financial, reputational, or career incentives at play?
5. Rate the source incentive concern from 0 (no conflict) to 4 (severe conflict).

Claim to analyze:
[PASTE CLAIM HERE]

Source context (if known):
[PASTE SOURCE INFO HERE]

Output your analysis, then give your 0-4 rating with a one-sentence justification.
```

---

## 2. Reasoning Holds Filter

```
You are a logic auditor. Your job is to check whether the reasoning in a claim actually supports its conclusion.

Given the following claim, answer these questions:
1. What is the core logical structure? (If X, then Y; Because A, therefore B)
2. Are there unstated assumptions required for the reasoning to work?
3. Does the evidence cited actually support the specific conclusion drawn?
4. Are there logical leaps, category errors, or scope mismatches?
5. Rate the reasoning quality from 0 (reasoning broken) to 4 (reasoning airtight).

Claim to analyze:
[PASTE CLAIM HERE]

Output your analysis, then give your 0-4 rating with a one-sentence justification.
```

---

## 3. Evidence Shown Filter

```
You are an evidence auditor. Your job is to identify what evidence is present versus conspicuously missing.

Given the following claim, answer these questions:
1. What specific evidence is cited to support the claim?
2. What evidence would you expect to see that is NOT present?
3. Are baselines, sample sizes, methodologies, or error definitions provided?
4. Is the evidence verifiable by a third party?
5. Rate the evidence quality from 0 (no real evidence) to 4 (comprehensive evidence).

Claim to analyze:
[PASTE CLAIM HERE]

List what's present, list what's missing, then give your 0-4 rating with a one-sentence justification.
```

---

## 4. Other Explanations Filter

```
You are an alternative-hypothesis generator. Your job is to identify explanations for the claimed result other than the one offered.

Given the following claim, answer these questions:
1. What is the explanation offered by the claimant?
2. What are 3-5 alternative explanations for the same observed result?
3. Has the claimant ruled out these alternatives? How?
4. Which alternative explanation is most plausible if the offered explanation is wrong?
5. Rate how well alternatives are addressed from 0 (ignored entirely) to 4 (systematically ruled out).

Claim to analyze:
[PASTE CLAIM HERE]

Output your alternative explanations, assess which were addressed, then give your 0-4 rating with a one-sentence justification.
```

---

## 5. Survives Deployment Filter

```
You are a deployment realist. Your job is to assess whether a claimed capability will hold up in real-world conditions.

Given the following claim, answer these questions:
1. Under what conditions was the claimed result achieved?
2. How do those conditions differ from real deployment environments?
3. What failure modes are likely when moving from benchmark to production?
4. Has the claim been validated outside controlled/benchmark settings?
5. Rate deployment survivability from 0 (benchmark-only) to 4 (proven in production).

Claim to analyze:
[PASTE CLAIM HERE]

Deployment context (your intended use):
[DESCRIBE YOUR USE CASE HERE]

Output your analysis, then give your 0-4 rating with a one-sentence justification.
```

---

## Usage Notes

- Run all five prompts on the same claim for a complete credibility read
- The filter with the lowest score is typically the deciding factor
- Scores are: 0 = critical failure, 1 = serious concern, 2 = moderate concern, 3 = minor concern, 4 = passes
- After running all five, identify your weakest filter and form your verdict around it

### Worked Example Claim

The builder calibrated this pack against:

> "The model achieves human-level performance on medical reasoning benchmarks, outperforming physicians on diagnostic vignettes."

Source: University press release summarizing a preprint; benchmark details in appendix C

Weakest filter identified: reasoning_holds

---

## Quick Reference

| Filter | What It Catches | Key Question |
|--------|-----------------|--------------|
| source_incentives | Conflicts of interest | Who profits if I believe this? |
| reasoning_holds | Logic gaps | Does the evidence actually prove the conclusion? |
| evidence_shown | Missing proof | What should be here that isn't? |
| other_explanations | Unconsidered alternatives | What else could explain this result? |
| survives_deployment | Benchmark-to-reality gap | Will this work outside the lab? |
