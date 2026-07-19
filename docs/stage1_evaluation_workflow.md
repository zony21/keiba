# Stage 1 Evaluation Workflow

## Status

This document defines the official Stage 1 execution workflow under `docs/scoring_logic_v4.md`.

For new races, v4 supersedes all older Stage 1 scoring and batch-processing rules.

## Purpose

Evaluate each horse independently and sequentially using historical performance only.

Stage 1 produces the **Ability Score** only.

Stage 1 must not determine:

- Betting strategy
- Expected value
- Race marks
- Final prediction
- Race-day suitability

## Prohibited Information

Do not use:

- Odds
- Betting-market popularity
- Race-day body weight
- Race-day weather or going
- Paddock impressions
- Final betting strategy

Historical popularity may be read only when it is already part of a stored race record and is used as supporting context for performance versus expectation. It must never be used to rank horses.

## Required Inputs

For each horse:

```text
docs/horses/XX/data.md
docs/horses/XX/career.md
```

Race reference:

```text
docs/race_info_en.md
```

Race-specific historical references may also be used when stored under `docs/`.

AI-generated evaluation must be written under:

```text
results/stage1/
```

Never write generated evaluation into `docs/`.

## Evaluation Order

Evaluate horses one by one in source horse-number order.

For every horse:

1. Read `data.md`.
2. Read `career.md`.
3. Verify horse identity and race number mapping.
4. Review recent races, normally the latest five starts.
5. Extract factual features.
6. Calculate every Stage 1 category.
7. Create or replace the individual result file.
8. Immediately update `results/stage1/stage1_scores.md`.
9. Continue to the next horse.

Do not wait for a four-horse batch.

## Scoring Categories

Maximum: **30 points**

### 1. Similar-Condition Performance — 0 to 10

Evaluate distance and course similarity independently.

Use:

- Today's distance
- Approximately ±200m evidence
- Relevant 2400m to 2600m evidence
- Course geometry
- Small-turn suitability
- Track direction
- Surface and historical going
- Similar class and field structure

Direct evidence receives priority, but strong longer-distance performance is positive evidence when the horse has also shown middle-distance suitability.

### 2. Demonstrated Race Ability — 0 to 8

Use:

- Condition-adjusted margin
- Opponent quality
- Strength of the winner and nearby finishers
- Running position and trip
- Closing section
- Sustained speed
- Competitive performance under pressure

Finish position alone is insufficient.

### 3. Hidden Ability — 0 to 3

Award only for verified evidence that the final placing understated the performance.

Eligible evidence includes:

- Small defeat margin against strong opposition
- Documented wide trip, blocked run, slow start, or pace disadvantage
- Strong performance against the dominant pace pattern
- Sectional or position evidence materially better than the placing
- Competitive performance under a clearly unfavorable weight or draw

Do not invent excuses. Record the exact factual evidence.

### 4. Improvement Trend — -2 to +5

Evaluate the latest races after adjusting for class, distance, surface, pace, and race conditions.

Use:

- Margin trend
- Race-content trend
- Running-position development
- Closing-section development
- Increased tactical or distance range
- Repeated evidence of improvement or decline

One race alone is normally insufficient for an extreme score.

### 5. Winning Ability and Consistency — 0 to 4

Evaluate:

- Win rate
- Top-two and top-three frequency
- Ability to finish first
- Repeatability under relevant conditions
- Race-shape dependence
- Sample size

### 6. Age and Sex Historical Adjustment — 0 to -4

This category is deduction-only.

Use race-specific historical evidence when available, but actual recent performance is more important than age or sex alone.

Do not automatically deduct because a horse is female or a gelding. Do not apply a large age deduction without evidence of decline.

## Final Score

```text
Similar-Condition Performance      0..10
+ Demonstrated Race Ability         0..8
+ Hidden Ability                    0..3
+ Improvement Trend                -2..5
+ Winning Ability and Consistency   0..4
+ Age and Sex Adjustment           -4..0
= Stage 1 Ability Score
```

Maximum: **30**

The theoretical minimum may be below zero. Do not normalize artificially.

## Evidence Extraction

For recent races, verify when available:

- Racecourse
- Distance
- Surface
- Track direction
- Going
- Class
- Field size
- Weight carried
- Finish position
- Margin
- Running position
- Final section
- Winner and nearby opponents
- Pace
- Documented trip disadvantage

Unknown information is neutral. Record it under `Missing Information`.

## Individual Output

Create:

```text
results/stage1/XX_horse_name.md
```

Required sections:

1. Evaluation Status
2. Source Files
3. Basic Information
4. Recent Race Review
5. Feature Evidence
6. Stage 1 Scoring
7. Final Stage 1 Score
8. Assessment
9. Missing Information
10. Notes

The scoring table must contain:

| Category | Score |
|---|---:|
| Similar-Condition Performance | X / 10 |
| Demonstrated Race Ability | X / 8 |
| Hidden Ability | X / 3 |
| Improvement Trend | X |
| Winning Ability and Consistency | X / 4 |
| Age and Sex Historical Adjustment | X |
| **Total** | **XX / 30** |

Every numerical score requires factual evidence.

## Stage 1 Score List

Maintain:

```text
results/stage1/stage1_scores.md
```

Required columns:

- Source ID
- Official Number, when known
- Horse Name
- Similar-Condition Score
- Race Ability Score
- Hidden Ability Score
- Improvement Trend Score
- Consistency Score
- Age/Sex Adjustment
- Total Score
- Status

Keep source-number order. Do not sort by score while evaluation is incomplete.

## Ability Ranking

Create:

```text
results/stage1/ability_ranking.md
```

Only after every horse has been evaluated using v4.

Sort by total Stage 1 score and retain the category breakdown needed for Stage 2 qualification.

## Stage 2 Qualification Metadata

After the final Stage 1 ranking is complete, record whether each horse qualifies for Stage 2 under one of these rules:

1. Total score of 21 or higher.
2. Total score of at least 18, Hidden Ability of at least 2, and Demonstrated Race Ability of at least 6.
3. Top six in the completed Stage 1 ranking.

Record the exact qualification rule. Do not use odds or popularity.

## Missing Information Policy

- Unknown is neutral.
- Never assign zero merely because evidence is absent.
- Never invent margins, pace, sectional times, trip trouble, suitability, or opponent quality.
- Distinguish missing evidence from demonstrated weakness.
- Reduce confidence when material information is missing.

## Re-evaluation Policy

When the official Stage 1 logic changes:

- Re-evaluate every horse in the active race.
- Replace active Stage 1 result files and scores.
- Preserve historical race predictions after the race; do not rewrite them retroactively.
- Do not create the final ability ranking until all required re-evaluations are complete.

## Completion Criteria

Stage 1 is complete only when:

- Every horse has a v4 individual evaluation.
- `stage1_scores.md` contains every horse.
- All source and official number mappings are verified or explicitly unresolved.
- `ability_ranking.md` is complete.
- Stage 2 qualification reasons are recorded.
- No odds, race marks, expected value, or betting strategy appear in Stage 1 outputs.