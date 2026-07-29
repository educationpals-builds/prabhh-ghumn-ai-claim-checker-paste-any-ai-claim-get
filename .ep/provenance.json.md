{
  "schema": "baw.v3.provenance",
  "build_name": "AI claim checker — paste any AI claim, get a credibility read",
  "composition": "shipgen",
  "fields": {
    "claim_text": {
      "source": "learner",
      "chars": 127,
      "words": 14
    },
    "claim_source": {
      "source": "learner",
      "chars": 80,
      "words": 11
    },
    "why_it_matters": {
      "source": "learner",
      "chars": 59,
      "words": 11
    },
    "decision_deadline": {
      "source": "learner",
      "chars": 26,
      "words": 4
    },
    "credibility_note": {
      "source": "learner",
      "chars": 106,
      "words": 23
    },
    "filter_ratings": {
      "source": "learner",
      "chars": 109,
      "words": 1
    },
    "evidence_note": {
      "source": "learner",
      "chars": 63,
      "words": 12
    },
    "weakest_filter": {
      "source": "learner",
      "chars": 15,
      "words": 1
    },
    "sharpest_question": {
      "source": "learner",
      "chars": 47,
      "words": 9
    },
    "flip_condition": {
      "source": "learner",
      "chars": 51,
      "words": 10
    },
    "verdict_call": {
      "source": "learner",
      "chars": 57,
      "words": 13
    },
    "claim_stream": {
      "source": "learner",
      "chars": 59,
      "words": 15
    },
    "advisor_stance": {
      "source": "learner",
      "chars": 59,
      "words": 15
    },
    "advisor_run_verdict": {
      "source": "learner",
      "chars": 59,
      "words": 15
    },
    "learner_probes": {
      "source": "learner",
      "chars": 147,
      "words": 31
    },
    "board_reading": {
      "source": "learner",
      "chars": 47,
      "words": 12
    },
    "pass_gate": {
      "source": "learner",
      "chars": 59,
      "words": 15
    }
  },
  "ai_drafted": [
    "METHOD.md",
    "README.md",
    "STORY.md",
    "VERIFY.md",
    "blueprints/claim-checker.md",
    "charter.md",
    "data/seeded-claims.md",
    "prompts/claim-check-pack.md",
    "skills/claim-advisor.skill.md",
    "tests/pass-gate.md",
    "tests/probe-board.md",
    "tests/probes.jsonl",
    "tests/run-local.md"
  ],
  "note": "Learner field values inserted verbatim; AI drafted listed paths."
}
