# Stage 2 Evaluation Workflow

## Purpose

Stage 2 evaluates today's race conditions only.

Stage 1 has already evaluated historical ability. Stage 2 must not evaluate ability again.

Stage 1 answers:

> How strong is this horse?

Stage 2 answers:

> How suitable is this horse for today's race?

Stage 2 produces the **Stage 2 Condition Score only**.

---

## Prerequisite

Stage 2 starts only after Stage 1 has been completed.

The following files must already exist:

- `results/stage1/stage1_scores.md`
- `results/stage1/ability_ranking.md`
- `docs/horses/XX/data.md`
- `docs/horses/XX/career.md`
- `docs/race_info_en.md`

AI-generated analysis must be written under `results/`.

Never write AI-generated evaluation results into `docs/`.

---

## Horse Selection

Do not evaluate every horse.

Only horses whose Stage 1 Score is **greater than 20 points** proceed to Stage 2.

- Stage 1 Score of 21 or higher: qualified for Stage 2
- Stage 1 Score of 20 or lower: eliminated before Stage 2

This fixed threshold replaces the previous average-score filtering method.

---

## Prohibited Information

Never use the following information in Stage 2:

- Odds
- Betting market popularity
- Betting strategy
- Expected value
- Final prediction
- Race marks such as `◎`, `○`, `▲`, or `△`
- Stage 3 information
- Race-day body weight
- Workout evaluation
- Paddock evaluation

Historical information may be used only as factual evidence for suitability to today's conditions.

---

## Evaluation Order

Evaluate qualified horses one by one.

For each qualified horse:

1. Read the Stage 1 result.
2. Read `docs/horses/XX/data.md`.
3. Read `docs/horses/XX/career.md`.
4. Read `docs/race_info_en.md`.
5. Evaluate today's race conditions.
6. Create or replace `results/stage2/XX_horse_name.md`.
7. Immediately update `results/stage2/stage2_scores.md`.
8. Continue to the next qualified horse.

Do not wait until several horses have been completed before saving results.

---

## Stage 2 Categories

Maximum Stage 2 Score: **30 points**

### 1. Course Suitability

Score: **0 to 8**

Evaluate:

- Performance at today's racecourse
- Performance on similar small racecourses
- Right-handed performance when applicable
- Similar course layouts and characteristics
- Historical course suitability
- Running-style compatibility with the course

Evidence should include factual results such as wins, placings, competitive finishes, margins, and race positions.

### 2. Distance Suitability

Score: **0 to 6**

Evaluate today's distance first.

Priority:

1. Win at today's distance
2. Strong placing at today's distance
3. Win at a nearby distance such as 1800m or 2200m for a 2000m race
4. Strong performance at 2400m to 2600m
5. Other middle-distance performances

Do not penalize a horse simply because it has also succeeded over longer distances.

Strong longer-distance results may support stamina and versatility when the horse has also demonstrated middle-distance ability.

### 3. Track Condition Suitability

Score: **-2 to +4**

Evaluate only the expected track condition for today's race.

Examples:

- Firm or good
- Yielding
- Soft
- Heavy

Use actual historical performance before pedigree assumptions.

Unknown evidence is neutral. Do not assume suitability and do not assign a poor score only because evidence is unavailable.

### 4. Expected Pace Suitability

Score: **-4 to +6**

Evaluate:

- Expected race pace
- Historical pace preference
- Performance under similar pace scenarios
- Ability to maintain position or finish strongly under the projected flow

Typical pace classifications include:

- Fast pace
- Average pace
- Slow pace

Every score must be supported by race-history evidence.

### 5. Running Style Suitability

Score: **-2 to +6**

Classify the horse's historical running style using factual race positions.

Examples:

- Front-runner
- Stalker
- Mid-pack runner
- Closer

Evaluate the interaction between:

- Today's course
- Today's expected pace
- Historical running style
- Historical performance from similar positions

Do not score running style in isolation from the expected race flow.

---

## Final Score

The Stage 2 Score is calculated as:

```text
Course Suitability
+ Distance Suitability
+ Track Condition Suitability
+ Expected Pace Suitability
+ Running Style Suitability
= Stage 2 Condition Score
```

Maximum: **30 points**

The total may become negative.

Do not artificially normalize or adjust scores to fit a preferred range.

---

## Evidence Requirement

Every numerical score must include factual evidence.

Acceptable evidence includes:

- Course record
- Similar-course record
- Distance record
- Track-condition record
- Historical running positions
- Pace suitability
- Finish position
- Margin
- Competitive performance under similar conditions

Avoid unsupported statements such as:

- Should suit today's race
- Probably improves
- Looks ideal
- Expected to run well

Every conclusion must be traceable to supplied race history or official reference documents.

---

## Missing Information Policy

Unknown information is neutral.

Never interpret missing information as poor suitability.

Do not assign zero merely because evidence is unavailable.

Do not invent or infer unsupported suitability.

Record unavailable items under:

```text
Missing Information
```

---

## Per-Horse Output

Create one file for every evaluated horse:

```text
results/stage2/XX_horse_name.md
```

Each file must contain:

1. Evaluation Status
2. Stage 1 Reference
3. Today's Race Conditions
4. Stage 2 Scoring
5. Final Stage 2 Score
6. Evidence and Assessment
7. Missing Information
8. Notes

Example structure:

```markdown
# Horse Name

## Evaluation Status

Completed

## Stage 1 Reference

Stage 1 Score: 22 / 30

## Today's Race Conditions

- Racecourse: ...
- Distance: ...
- Surface: ...
- Direction: ...
- Expected Track Condition: ...
- Expected Pace: ...

## Stage 2 Scoring

- Course Suitability: 7 / 8
- Distance Suitability: 5 / 6
- Track Condition Suitability: 2
- Expected Pace Suitability: 4
- Running Style Suitability: 5

## Final Stage 2 Score

23 / 30

## Evidence and Assessment

- ...
- ...

## Missing Information

- ...

## Notes

- ...
```

---

## Stage 2 Score List

Maintain:

```text
results/stage2/stage2_scores.md
```

Required columns:

- Horse Number
- Horse Name
- Stage 1 Score
- Stage 2 Score

Rules:

- Update the file immediately after each horse is evaluated.
- Keep horse-number order.
- Do not rank horses in this file.
- Replace old scores when a horse is re-evaluated.

---

## Stage 2 Ranking

Create:

```text
results/stage2/stage2_ranking.md
```

Only create or finalize this file after:

- Every qualified horse has been evaluated.
- Every required re-evaluation has finished.

Sort by Stage 2 Score.

Include:

- Rank
- Horse Number
- Horse Name
- Stage 1 Score
- Stage 2 Score
- Combined Score

The Combined Score is included for reference, but Stage 2 itself remains a condition-suitability evaluation and must not re-score ability.

---

## Re-evaluation Policy

Whenever the Stage 2 policy changes:

- Re-evaluate every previously scored horse.
- Replace previous Stage 2 evaluations.
- Do not preserve old-policy scores as active results.

---

## Completion Criteria

Stage 2 is complete only after:

- Every horse with a Stage 1 Score greater than 20 has been evaluated.
- `results/stage2/stage2_scores.md` has been updated.
- `results/stage2/stage2_ranking.md` has been created.

Only then may the workflow proceed to Stage 3.
