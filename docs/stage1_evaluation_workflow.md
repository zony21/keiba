# Stage 1 Evaluation Workflow

## Status

This document defines the final official Stage 1 evaluation workflow.

For Stage 1 work, this document supersedes any older Stage 1 execution method that requires four-horse batches, cross-horse comparison during scoring, or interim ability rankings.

Stage 1 must evaluate each horse independently and sequentially.

---

## Purpose

Repository:

`https://github.com/zony21/keiba`

Evaluate each horse individually using historical performance only.

Stage 1 produces the **Ability Score** only.

Stage 1 must not determine:

- Betting strategy
- Expected value ranking
- Ability ranking before all horses have been evaluated
- Race marks such as `◎`, `○`, or `▲`
- Final prediction

---

## Prohibited Information

Do not use:

- Odds
- Betting-market popularity for ranking
- Race-day information
- Final betting strategy
- Race-day body weight
- Workout evaluation
- Paddock condition
- Race-day track condition

Historical body weight recorded in past races may be used only as factual race-history evidence.

---

## Repository Structure

Source materials:

```text
docs/
```

AI-generated outputs:

```text
results/
    stage1/
    stage2/
    stage3/
    final/
```

Never write AI-generated race analysis into `docs/`.

---

## Required Input

For each horse:

```text
docs/horses/XX/data.md
docs/horses/XX/career.md
```

Reference documents:

```text
docs/race_info_en.md
docs/kokura_kinen_historical_winner_ages.md
```

---

## Evaluation Order

Evaluate horses one by one in horse-number order.

Example:

```text
Horse 01
↓
Horse 02
↓
Horse 03
↓
...
```

Do not wait until four horses have been completed.

For each horse:

1. Read `data.md`.
2. Read `career.md`.
3. Review the recent races.
4. Calculate the Stage 1 score.
5. Create or update the individual Stage 1 result file.
6. Immediately update `results/stage1/stage1_scores.md`.
7. Move to the next horse.

---

# Stage 1 Scoring Categories

## 1. Similar Condition Performance

Score range:

`0 to 12`

Evaluate:

- Distance suitability
- Course suitability
- Track direction
- Small-course suitability
- Similar-class performance
- Similar race conditions

### Distance Evaluation Priority

1. Win at today's distance, normally 2000m.
2. Win at 1800m or 2200m.
3. Placing or strong performance at 2000m.
4. Strong performance or victory at 2400m to 2600m.
5. Other middle-distance performance.
6. Long-distance-only performance.

### Distance Rules

- Direct 2000m evidence remains the highest priority.
- Strong performances at 2400m to 2600m are positive evidence of stamina, versatility, and distance range.
- If a horse has already demonstrated 2000m ability, longer-distance success must not reduce its score.
- Long-distance performance without evidence near 2000m receives less credit than direct 2000m suitability.
- Missing distance or course information must not be treated as zero.

---

## 2. Race Ability

Score range:

`0 to 8`

Evaluate:

- Opponent quality
- Race class
- Margin
- Race content
- Closing speed
- Running position
- Overall performance quality

### Additional Guidance

- Recent victories near today's distance deserve additional credit.
- Winning at a similar distance is evidence of practical race ability.
- Strong performances at 2400m to 2600m may support this category when achieved against quality opposition.
- Finish position alone is insufficient; class, margin, running position, and race content must also be considered.
- Do not award duplicate credit to multiple categories for exactly the same evidence without explaining the distinct meaning of each score.

---

## 3. Recent Trend

Score range:

`-6 to +6`

Evaluate whether the horse is:

- Improving
- Stable
- Declining

Use recent races only, normally the latest five starts.

Rules:

- Evaluate only factual race results.
- Do not guess.
- One poor race alone does not necessarily indicate decline.
- Adjust for factual changes in race class, distance, surface, pace, and race conditions when the supplied data supports doing so.
- Do not conveniently ignore poor results.

---

## 4. Winning Ability and Consistency

Score range:

`0 to 4`

Evaluate:

- Win rate
- Ability to finish first
- Stability
- Repeatability
- Frequency of strong finishes

### Additional Guidance

- Recent victories receive more weight than older victories.
- Recent wins near today's distance deserve particularly strong credit.
- Repeated recent top-two finishes should be rewarded even when some graded-race defeats are present.
- A horse with placings but no supplied recent victory should not automatically receive full winning-ability credit.
- If the supplied record is too short to establish a reliable rate, record that limitation under Missing Information.

---

## 5. Age and Sex Historical Adjustment

Score range:

`0 to -4`

This category is deduction-only.

Reference:

```text
docs/kokura_kinen_historical_winner_ages.md
```

Evaluate:

- Age
- Sex: Male, Female, or Gelding
- Historical Kokura Kinen winner distribution
- Evidence of actual age-related decline

### General Age Guideline

| Age | Adjustment |
|---:|---:|
| 3 | 0 to -1 |
| 4 | 0 |
| 5 | 0 |
| 6 | 0 to -1 |
| 7 | -1 to -2 |
| 8 | -2 to -3 |
| 9 or older | -4 |

### Sex Guideline

| Sex | Adjustment |
|---|---:|
| Male | 0 |
| Female | 0 to -1 |
| Gelding | 0 to -1 |

### Adjustment Rules

- Do not automatically deduct because a horse is female.
- Do not automatically deduct because a horse is a gelding.
- Historical trends are supporting evidence only.
- The combined age-and-sex deduction must not exceed `-4`.
- A five-year-old male normally receives no deduction.
- Actual recent decline is more important than age alone.

---

# Final Score

```text
Total
=
Similar Condition Performance
+
Race Ability
+
Recent Trend
+
Winning Ability and Consistency
+
Age and Sex Historical Adjustment
```

Maximum score:

`30`

The theoretical minimum may be below zero.

Do not artificially force the score into a positive range.

---

# Individual Output Format

For every horse, create:

```text
results/stage1/XX_horse_name.md
```

Each file must contain:

1. Evaluation Status
2. Source Files
3. Basic Information
4. Recent Race Review
5. Scoring
6. Final Stage 1 Score
7. Assessment
8. Missing Information
9. Notes

Recommended structure:

```markdown
# Horse Name

## 1. Evaluation Status

- Status: Completed
- Stage: Stage 1 Ability Evaluation
- Policy: Final individual-evaluation policy

## 2. Source Files

- `docs/horses/XX/data.md`
- `docs/horses/XX/career.md`
- `docs/race_info_en.md`
- `docs/kokura_kinen_historical_winner_ages.md`

## 3. Basic Information

| Item | Value |
|---|---|
| Horse Number | XX |
| Horse Name | Horse Name |
| Sex / Age | Male, 5yo |

## 4. Recent Race Review

1. Race evidence
2. Race evidence
3. Race evidence

## 5. Scoring

### Similar Condition Performance: X / 12

- Factual evidence

### Race Ability: X / 8

- Factual evidence

### Recent Trend: X

- Factual evidence

### Winning Ability and Consistency: X / 4

- Factual evidence

### Age and Sex Historical Adjustment: X

- Factual evidence

## 6. Final Stage 1 Score

| Category | Score |
|---|---:|
| Similar Condition Performance | X / 12 |
| Race Ability | X / 8 |
| Recent Trend | X |
| Winning Ability and Consistency | X / 4 |
| Age and Sex Historical Adjustment | X |
| **Total** | **XX / 30** |

## 7. Assessment

Evidence-based summary only.

## 8. Missing Information

- Unknown information

## 9. Notes

- Odds and popularity were not used.
- No expected-value judgment, race marks, betting strategy, or final prediction is included.
```

---

# Stage 1 Score List

Maintain:

```text
results/stage1/stage1_scores.md
```

Required columns:

- Horse Number
- Horse Name
- Score

Rules:

- Update the file immediately after each horse.
- Keep horse-number order.
- Do not sort by score.
- Replace old scores when a horse is re-evaluated.
- Do not use the list as an interim ranking.

Example:

```markdown
| Horse Number | Horse Name | Score |
|---:|---|---:|
| 01 | Horse A | 21 / 30 |
| 02 | Horse B | 18 / 30 |
```

---

# Ability Ranking

Create:

```text
results/stage1/ability_ranking.md
```

Create it only after:

- Every horse has been evaluated.
- Every horse uses the latest Stage 1 policy.
- All required re-evaluations are complete.

The ability ranking is sorted by final Stage 1 score.

Do not create or update an ability ranking while evaluation is still in progress.

---

# Re-evaluation Policy

Whenever the Stage 1 scoring policy changes:

- Re-evaluate every previously scored horse.
- Replace the previous evaluation.
- Replace the previous score in `stage1_scores.md`.
- Do not maintain separate old-policy and new-policy result versions.
- Do not create the final ability ranking until all re-evaluations are complete.

---

# Missing Information Policy

Unknown information is neutral.

Never interpret missing information as poor ability.

Rules:

- Record unknown items under `Missing Information`.
- Reduce confidence when necessary.
- Do not assign zero merely because evidence is unavailable.
- Do not invent suitability, results, margins, pace, running positions, or sectional times.
- Distinguish information shortage from demonstrated weakness.

---

# Independence Rule

Evaluate every horse independently.

Do not compare horses during individual Stage 1 scoring.

Cross-horse comparison is permitted only after every horse has been evaluated using the same scoring policy.

Until then:

- Do not create rankings.
- Do not assign race marks.
- Do not determine betting strategy.
- Do not discuss expected value.

---

# Evidence Requirement

Every numerical score must include factual evidence.

Acceptable evidence includes:

- Finish position
- Distance
- Race class
- Margin
- Running position
- Final 3F
- Pace
- Course
- Track direction
- Recent sequence of results
- Confirmed wins and placings

Avoid unsupported statements such as:

- Looks talented
- Should improve
- Probably suits Kokura
- May be popular
- Expected to run well

Every conclusion must be traceable to the supplied race history or official reference documents.

---

# Language

GitHub files:

`English`

Chat conversation:

`Japanese`

---

# Completion Criteria

Stage 1 is complete only after:

- Every horse has been evaluated.
- `results/stage1/stage1_scores.md` has been updated.
- `results/stage1/ability_ranking.md` has been created.

Only then may the workflow proceed to Stage 2.
