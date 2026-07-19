# Stage 3 Evaluation Workflow

## Status

This document defines the official Stage 3 execution workflow under `docs/scoring_logic_v4.md`.

## Purpose

Stage 3 evaluates confirmed race-day information, the projected field shape, the official draw, and the latest betting market.

Stage 1 evaluates historical ability.

Stage 2 evaluates supporting condition factors and tactical adaptability.

Stage 3 answers:

> How do today's confirmed conditions alter the prospects of each Stage 2 qualifier?

Stage 3 produces the **Stage 3 Race-Day Score only**.

It must not determine expected value, betting strategy, or final race marks.

## Prerequisite

Stage 3 starts only after Stage 1 and Stage 2 are complete under v4.

Required inputs:

- `results/stage1/stage1_scores.md`
- `results/stage1/ability_ranking.md`
- `results/stage2/stage2_scores.md`
- `results/stage2/stage2_ranking.md`
- Official field and draw
- Confirmed weather
- Confirmed track condition
- Latest authorized odds snapshot
- Projected pace and field composition

Optional confirmed inputs:

- Official body weight
- Late scratches
- Official rider or equipment changes

## Evaluation Scope

Evaluate every Stage 2 qualifier.

A horse outside Stage 2 may trigger a market discrepancy warning, but it must not be inserted into the scored final ranking without completing the required Stage 2 and Stage 3 evaluations.

When the discrepancy recheck identifies missing or erroneous source processing, complete the missing evaluation before the final prediction.

## Evaluation Categories

Maximum Stage 3 Score: **30 points**

### 1. Weather Suitability — 0 to 4

Evaluate confirmed weather using verified historical evidence.

Do not infer suitability from pedigree alone when actual race evidence exists.

### 2. Track Condition Suitability — 0 to 6

Evaluate confirmed going using verified race records.

Use direct evidence first and comparable-condition evidence second.

### 3. Race Pace Scenario — -2 to +8

Evaluate:

- Number of likely pace setters
- Expected early pressure
- Expected overall pace
- Horse's verified preferred pace
- Pace adaptability from Stage 2
- Likely position entering the first turn
- Ability to remain competitive when the pace differs from the ideal scenario

The pace score must use the projected field composition, not a generic running-style label alone.

### 4. Draw and Trip Interaction — -3 to +5

Never score the official draw in isolation.

Evaluate the interaction of:

- Official draw
- Start consistency
- Early tactical speed
- Preferred running position
- Position flexibility from Stage 2
- Distance to the first turn
- Course geometry
- Historical course evidence
- Extra-ground risk
- Traffic and boxed-in risk

Rules:

- An outside draw is not automatically a major negative.
- An outside horse with verified start speed, tactical flexibility, and direct course evidence may receive only a small deduction or no deduction.
- An inside draw is not automatically positive when it creates material traffic risk for that horse.
- Record the expected first-turn route and the factual reason for the adjustment.
- Do not duplicate a general course-suitability score from Stage 1.

### 5. Official Race-Day Factors — -1 to +3

Use only confirmed information not already scored above, including:

- Official body weight and change, when supplied
- Late scratch effects
- Official rider or equipment changes
- Other confirmed operational changes

Subjective paddock impressions are prohibited unless a later version introduces a separate verified paddock-data standard.

Missing race-day factors are neutral and must be recorded as unknown.

### 6. Latest Odds — -2 to +4

Odds are supplementary market evidence, not proof of ability.

Evaluate:

- Strength or weakness of market support
- Material odds movement when multiple authorized snapshots exist
- Whether market support is consistent with verified evidence
- Whether unusually weak support requires a source recheck

Do not calculate expected value or define betting strategy inside this category.

## Market Discrepancy Recheck

For every horse in the full field, record when possible:

- AI rank before odds
- Market rank
- Absolute rank difference
- Stage reached
- Recheck trigger
- Recheck conclusion

A mandatory recheck is triggered when any of the following is true:

1. AI rank and market rank differ by 5 or more positions.
2. A market top-three horse did not qualify for Stage 3.
3. A high Stage 1 or Stage 2 horse has unusually weak market support.
4. Horse identity or official-number mapping is inconsistent.

The recheck must inspect:

- Source completeness
- Horse identity mapping
- Missing race records
- Score arithmetic
- Category omissions
- Duplicate scoring
- Stage qualification logic

The recheck must not automatically change a score to match the market.

Possible conclusions:

- `NO_CHANGE_MARKET_ONLY`
- `SOURCE_MISSING_REEVALUATE`
- `IDENTITY_MAPPING_ERROR`
- `SCORING_ERROR_REEVALUATE`
- `QUALIFICATION_RESCUE_REQUIRED`
- `UNRESOLVED`

## Final Score

```text
Weather Suitability          0..4
+ Track Condition            0..6
+ Race Pace Scenario         -2..8
+ Draw and Trip Interaction  -3..5
+ Official Race-Day Factors  -1..3
+ Latest Odds                -2..4
= Stage 3 Race-Day Score
```

Maximum: **30**

The total may be negative. Do not normalize artificially.

## Prohibited Information

Never include:

- Betting combinations
- Stake allocation
- Expected-value ranking
- Final race marks
- Final prediction
- Unsupported paddock impressions
- Unsupported speculation

## Per-Horse Output

Create:

```text
results/stage3/XX_horse_name.md
```

Required sections:

1. Evaluation Status
2. Horse Identification
3. Stage 1 and Stage 2 References
4. Official Race-Day Conditions
5. Projected Pace and First-Turn Route
6. Stage 3 Scoring
7. Final Stage 3 Score
8. Market Discrepancy Recheck
9. Assessment
10. Missing Information

Required scoring table:

| Category | Score |
|---|---:|
| Weather Suitability | X / 4 |
| Track Condition | X / 6 |
| Race Pace Scenario | X / 8 |
| Draw and Trip Interaction | X / 5 |
| Official Race-Day Factors | X / 3 |
| Latest Odds | X / 4 |
| **Total** | **XX / 30** |

Negative category scores must be displayed explicitly.

## Stage 3 Score List

Maintain:

```text
results/stage3/stage3_scores.md
```

Required columns:

- Source ID
- Official Number
- Horse Name
- Stage 1 Score
- Stage 2 Score
- Stage 3 Category Scores
- Stage 3 Total
- Combined Score
- Market Rank
- AI/Market Rank Difference
- Recheck Status

## Stage 3 Ranking

Create:

```text
results/stage3/stage3_ranking.md
```

Only after:

- Every Stage 2 qualifier has a completed Stage 3 evaluation.
- Every mandatory market discrepancy recheck is resolved or explicitly marked unresolved.
- All identity mappings and score arithmetic are verified.

Sort by completed Stage 3 total and include the combined Stage 1 + Stage 2 + Stage 3 score.

Do not include race marks, betting value, or betting strategy.

## Completion Criteria

Stage 3 is complete only when:

- Every qualified horse is evaluated under v4.
- `stage3_scores.md` is complete.
- `stage3_ranking.md` is complete.
- Every required market discrepancy recheck is documented.
- Draw scoring explains its interaction with start speed, tactical speed, position flexibility, and course geometry.
- No expected value, race marks, or betting strategy appear in Stage 3 outputs.

Only after completion may the final prediction process integrate the three stages and determine betting strategy.