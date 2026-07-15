# Stage 2 Evaluation Workflow

## Purpose

Stage 2 evaluates the factors that affect how well a qualified horse may perform in today's race.

Stage 1 has already evaluated historical ability. Stage 2 must not repeat the Stage 1 ability assessment.

Stage 1 answers:

> How strong is this horse based on historical performance?

Stage 2 answers:

> How favorable are the current supporting factors for this horse today?

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

Additional reference files may include:

- `docs/jockeys/`
- Pedigree reference data
- Training and workout records
- Official handicap weights

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
- Paddock evaluation
- Unsupported speculation

Training information is allowed because it is now an official Stage 2 category.

Race-day body weight remains Stage 3 information unless the Stage 3 policy is changed separately.

---

## Evaluation Order

Evaluate qualified horses one by one.

For each qualified horse:

1. Read the Stage 1 result.
2. Read `docs/horses/XX/data.md`.
3. Read `docs/horses/XX/career.md`.
4. Read `docs/race_info_en.md`.
5. Read available jockey, pedigree, training, personal-best, and handicap information.
6. Evaluate all Stage 2 categories.
7. Create or replace `results/stage2/XX_horse_name.md`.
8. Immediately update `results/stage2/stage2_scores.md`.
9. Continue to the next qualified horse.

Do not wait until several horses have been completed before saving results.

---

## Stage 2 Categories

Maximum Stage 2 Score: **30 points**

### 1. Jockey Performance

Score: **0 to 5**

Evaluate:

- Recent jockey performance
- Win rate, top-two rate, and top-three rate
- Performance at today's racecourse
- Performance at today's distance
- Performance under similar race conditions
- Previous results with the same horse
- Ability to execute the horse's preferred running style

Do not evaluate a jockey only by reputation or name recognition.

Use factual statistics and race results.

### 2. Pedigree

Score: **0 to 4**

Evaluate:

- Sire-line suitability for today's distance
- Dam-sire suitability
- Course and surface tendencies
- Track-condition tendencies
- Stamina, speed, and acceleration characteristics relevant to today's race

Pedigree is supplementary evidence.

Do not allow pedigree assumptions to override the horse's actual race record.

### 3. Training Condition

Score: **-3 to +6**

Evaluate:

- Final workout
- Intermediate training pattern
- Workout time
- Sectional splits
- Acceleration or deceleration through the workout
- Paired-work result when available
- Comparison with the horse's previous-race training
- Whether the horse appears to be improving, maintaining, or declining based on factual workout data

Do not use vague comments such as "looks good" without measurable evidence.

Missing training information is neutral and must be recorded under Missing Information.

### 4. Overall Career Performance Rate

Score: **0 to 5**

Evaluate the horse's full career record using:

- Career win rate
- Top-two rate
- Top-three rate
- Total number of starts
- Performance consistency
- Performance under conditions related to today's race

Always consider sample size.

A high rate from very few starts must not automatically receive the maximum score.

This category summarizes career performance rates only. It must not become a complete re-evaluation of Stage 1 ability.

### 5. Personal Best Performance

Score: **0 to 5**

Evaluate the horse's best verified performance relevant to today's race.

Possible evidence includes:

- Best time at today's distance
- Best time at a similar distance
- Best performance at today's racecourse or a similar course
- Best final-section time
- Best verified speed figure or rating when officially supplied
- Best finishing margin or strongest competitive performance
- Conditions under which the personal best was recorded

Do not compare raw times across different racecourses, distances, track conditions, or pace environments without adjustment.

Prioritize a personal best recorded under conditions similar to today's race.

Consider how recent the performance is and whether it appears reproducible.

### 6. Handicap Weight

Score: **-3 to +5**

Evaluate:

- Today's assigned weight
- Results under the same or similar weight
- Results under a heavier weight
- Change from the previous race
- Weight relative to other qualified horses
- Historical handicap-race performance
- Relationship between weight changes and actual race performance

Scoring priorities:

1. Strong performance under the same weight
2. Strong performance under a heavier weight
3. Verified effect of a weight increase or decrease
4. Historical handicap-race performance
5. Neutral treatment when evidence is unavailable

Do not automatically reward a light weight.

Do not automatically penalize a heavy weight.

The score must reflect demonstrated weight-carrying ability and today's actual assignment.

---

## Final Score

The Stage 2 Score is calculated as:

```text
Jockey Performance
+ Pedigree
+ Training Condition
+ Overall Career Performance Rate
+ Personal Best Performance
+ Handicap Weight
= Stage 2 Condition Score
```

Maximum: **30 points**

The total may become negative.

Do not artificially normalize or adjust scores to fit a preferred range.

---

## Evidence Requirement

Every numerical score must include factual evidence.

Acceptable evidence includes:

- Jockey win, top-two, and top-three statistics
- Jockey course and distance results
- Horse-and-jockey combination results
- Official pedigree information
- Training times and sectional splits
- Career win rate, top-two rate, and top-three rate
- Number of career starts
- Personal-best times, margins, ratings, or final-section records
- Historical results under similar weights
- Previous-race weight changes
- Official handicap assignment

Avoid unsupported statements such as:

- The jockey should suit the horse
- The pedigree looks ideal
- The workout seems good
- The light weight should help
- The horse will probably improve

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
3. Today's Race Information
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

## Today's Race Information

- Racecourse: ...
- Distance: ...
- Surface: ...
- Assigned Weight: ...
- Jockey: ...

## Stage 2 Scoring

- Jockey Performance: 4 / 5
- Pedigree: 3 / 4
- Training Condition: 4 / 6
- Overall Career Performance Rate: 4 / 5
- Personal Best Performance: 4 / 5
- Handicap Weight: 3 / 5

## Final Stage 2 Score

22 / 30

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

The Combined Score is included for reference, but Stage 2 itself must not repeat the complete Stage 1 ability assessment.

---

## Re-evaluation Policy

Whenever the Stage 2 policy changes:

- Re-evaluate every previously scored horse.
- Replace previous Stage 2 evaluations.
- Do not preserve old-policy scores as active results.

The previous Course, Distance, Track Condition, Expected Pace, and Running Style category model is no longer the active Stage 2 scoring policy.

---

## Completion Criteria

Stage 2 is complete only after:

- Every horse with a Stage 1 Score greater than 20 has been evaluated using the current six categories.
- `results/stage2/stage2_scores.md` has been updated.
- `results/stage2/stage2_ranking.md` has been created.

Only then may the workflow proceed to Stage 3.
