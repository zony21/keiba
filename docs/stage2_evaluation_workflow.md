# Stage 2 Evaluation Workflow

## Status

This document defines the official Stage 2 execution workflow under `docs/scoring_logic_v4.md`.

## Purpose

Stage 2 evaluates supporting factors that affect how well a qualified horse may perform in today's race.

Stage 1 answers:

> How strong and repeatable is this horse based on historical performance?

Stage 2 answers:

> How favorable are the jockey, pedigree, training, pace adaptability, and tactical options for this horse in today's race framework?

Stage 2 produces the **Stage 2 Condition Score only**.

It must not determine race marks, expected value, betting strategy, or the final prediction.

## Prerequisite

Stage 2 starts only after Stage 1 has been completed for every horse under v4.

Required files:

- `results/stage1/stage1_scores.md`
- `results/stage1/ability_ranking.md`
- Individual Stage 1 result files
- `docs/horses/XX/data.md`
- `docs/horses/XX/career.md`
- `docs/race_info_en.md`

Additional verified sources may include:

- `docs/jockeys/`
- Pedigree data
- Training and workout records
- Career statistics
- Verified personal-best records

AI-generated analysis must be written under `results/stage2/`.

## Qualification

A horse proceeds to Stage 2 when any one of the following is true:

### Rule A — Standard Qualification

Stage 1 total score is **21 or higher**.

### Rule B — Hidden-Ability Rescue

All of the following are true:

- Stage 1 total score is at least 18.
- Hidden Ability is at least 2.
- Demonstrated Race Ability is at least 6.

### Rule C — Ranking Safety Net

The horse is within the **top six** of the completed Stage 1 ability ranking.

The top-six rule is applied only after all Stage 1 evaluations are complete.

For every qualified horse, record `A`, `B`, `C`, or every applicable rule. Do not use odds or popularity to qualify a horse.

The rescue and safety-net rules prevent a rigid total-score cutoff from eliminating a contender whose verified race quality or hidden ability requires further evaluation.

## Prohibited Information

Never use:

- Odds
- Betting-market popularity
- Expected value
- Betting strategy
- Race marks
- Final prediction
- Paddock impressions
- Race-day body weight
- Unsupported speculation

Training information is allowed because it is an official Stage 2 category.

Do not repeat handicap scoring or complete historical ability scoring from Stage 1.

## Evaluation Order

Evaluate qualified horses one by one.

For each horse:

1. Verify the Stage 1 score and qualification rule.
2. Read the individual Stage 1 result.
3. Read the horse source files and race information.
4. Read verified jockey, pedigree, training, career-rate, personal-best, pace, and tactical evidence.
5. Score all Stage 2 categories.
6. Create or replace the individual Stage 2 result file.
7. Immediately update `results/stage2/stage2_scores.md`.
8. Continue to the next qualified horse.

## Stage 2 Categories

Maximum Stage 2 Score: **30 points**

### 1. Jockey Performance — 0 to 5

Evaluate:

- Recent jockey performance
- Win, top-two, and top-three rates
- Today's racecourse and distance record
- Similar-condition record
- Previous results with the horse
- Ability to execute the horse's verified tactical options

Use facts, not reputation.

### 2. Pedigree Support — 0 to 4

Evaluate:

- Distance support
- Course and surface tendencies
- Going tendencies
- Stamina, speed, and acceleration characteristics relevant to today's race

Pedigree is supplementary and must not override actual race evidence.

### 3. Training Condition — -2 to +6

Evaluate:

- Final workout
- Intermediate pattern
- Workout time and sectionals
- Acceleration or deceleration
- Paired-work result when available
- Comparison with previous preparation
- Verified maintenance, improvement, or decline

Missing training information is neutral and must reduce confidence rather than automatically reduce the score.

### 4. Career Performance Rate — 0 to 4

Evaluate:

- Career win rate
- Top-two rate
- Top-three rate
- Number of starts
- Sample reliability
- Relevant-condition rate

This category summarizes rates only. It must not become a second complete Stage 1 evaluation.

### 5. Relevant Personal Best — 0 to 4

Evaluate the best verified performance relevant to today's race.

Possible evidence:

- Best adjusted performance at today's distance
- Best performance at the course or a similar course
- Best closing section
- Best verified speed figure or rating
- Strongest competitive performance
- Recency and reproducibility

Do not compare raw times across materially different courses, distances, going, or pace environments without adjustment.

### 6. Pace Adaptability — 0 to 4

Evaluate verified performance under different pace structures:

- Slow
- Middle
- Fast
- Increasing pace
- Sustained pressure

Reward evidence that the horse can remain competitive when the race does not develop exactly as preferred.

Do not award theoretical adaptability without race evidence.

### 7. Position Flexibility — 0 to 3

Evaluate verified ability to perform from more than one tactical position.

Use evidence for:

- Leading
- Stalking
- Midfield racing
- Closing
- Recovering from a slow start
- Adjusting when the intended position is unavailable

A horse that requires one exact position may receive a lower score even when strong under ideal conditions.

## Final Score

```text
Jockey Performance        0..5
+ Pedigree Support         0..4
+ Training Condition      -2..6
+ Career Performance Rate  0..4
+ Relevant Personal Best   0..4
+ Pace Adaptability        0..4
+ Position Flexibility     0..3
= Stage 2 Condition Score
```

Maximum: **30**

The total may be negative. Do not normalize artificially.

## Evidence Requirement

Every numerical score must include factual evidence traceable to stored source material.

Acceptable evidence includes:

- Jockey statistics
- Horse-jockey combination results
- Official pedigree information
- Workout times and sectionals
- Career performance rates and sample size
- Verified personal-best records
- Historical pace performance
- Historical running positions and tactical changes

Avoid vague statements such as:

- The jockey should suit the horse.
- The pedigree looks ideal.
- The horse appears versatile.
- The workout seems good.

## Missing Information Policy

Unknown information is neutral.

- Do not assign zero merely because evidence is absent.
- Record unavailable information.
- Reduce confidence where necessary.
- Do not invent pace adaptability, tactical flexibility, training quality, or pedigree suitability.

## Per-Horse Output

Create:

```text
results/stage2/XX_horse_name.md
```

Required sections:

1. Evaluation Status
2. Stage 1 Reference
3. Qualification Rule
4. Today's Race Information
5. Stage 2 Scoring
6. Final Stage 2 Score
7. Evidence and Assessment
8. Missing Information
9. Notes

Required scoring table:

| Category | Score |
|---|---:|
| Jockey Performance | X / 5 |
| Pedigree Support | X / 4 |
| Training Condition | X / 6 |
| Career Performance Rate | X / 4 |
| Relevant Personal Best | X / 4 |
| Pace Adaptability | X / 4 |
| Position Flexibility | X / 3 |
| **Total** | **XX / 30** |

## Stage 2 Score List

Maintain:

```text
results/stage2/stage2_scores.md
```

Required columns:

- Source ID
- Official Number, when known
- Horse Name
- Stage 1 Score
- Qualification Rule
- Stage 2 Category Scores
- Stage 2 Total
- Combined Stage 1 + Stage 2
- Status

Keep source-number order while evaluation is incomplete.

## Stage 2 Ranking

Create:

```text
results/stage2/stage2_ranking.md
```

Only after every qualified horse is complete.

Include:

- Rank
- Horse identifiers
- Qualification rule
- Stage 1 score
- Stage 2 score
- Combined score
- Hidden Ability
- Pace Adaptability
- Position Flexibility

## Re-evaluation Policy

Whenever the official Stage 2 policy changes:

- Re-evaluate every active-race qualifier.
- Reapply qualification rules after Stage 1 is completed under the current policy.
- Replace active Stage 2 evaluations and score lists.
- Do not rewrite completed historical race predictions after the result.

## Completion Criteria

Stage 2 is complete only after:

- Qualification rules A, B, and C have been applied to the complete Stage 1 field.
- Every qualified horse has a v4 Stage 2 evaluation.
- `stage2_scores.md` is complete.
- `stage2_ranking.md` is complete.
- Missing information and confidence limitations are recorded.
- No odds, expected value, race marks, or betting strategy appear in Stage 2 outputs.

Only then may the workflow proceed to Stage 3.