# Stage 2 Evaluation Workflow

## Purpose

Stage 2 evaluates the supporting factors that affect how well a qualified horse may perform in today's race.

Stage 1 has already evaluated historical ability and handicap suitability. Stage 2 must not repeat either assessment.

Stage 1 answers:

> How strong is this horse based on historical performance and handicap conditions?

Stage 2 answers:

> How favorable are the jockey, pedigree, training, career-rate, and personal-best factors for this horse today?

Stage 2 produces the **Stage 2 Condition Score only**.

---

## Prerequisite

Stage 2 starts only after Stage 1 has been completed.

Required files:

- `results/stage1/stage1_scores.md`
- `results/stage1/ability_ranking.md`
- `docs/horses/XX/data.md`
- `docs/horses/XX/career.md`
- `docs/race_info_en.md`

Additional reference files may include:

- `docs/jockeys/`
- Pedigree reference data
- Training and workout records
- Verified personal-best records

Handicap information is not scored in Stage 2. It is evaluated in Stage 1 under `docs/scoring_logic_v3.md`.

AI-generated analysis must be written under `results/`.
Never write AI-generated evaluation results into `docs/`.

---

## Horse Selection

Do not evaluate every horse.

Only horses whose Stage 1 Score is **greater than 20 points** proceed to Stage 2.

- Stage 1 Score of 21 or higher: qualified
- Stage 1 Score of 20 or lower: eliminated before Stage 2

---

## Prohibited Information

Never use:

- Odds
- Betting market popularity
- Betting strategy
- Expected value
- Final prediction
- Race marks such as `◎`, `○`, `▲`, or `△`
- Paddock evaluation
- Race-day body weight
- Handicap weight scoring
- Unsupported speculation

Training information is allowed because it is an official Stage 2 category.

---

## Evaluation Order

Evaluate qualified horses one by one.

For each qualified horse:

1. Read the Stage 1 result.
2. Read `docs/horses/XX/data.md`.
3. Read `docs/horses/XX/career.md`.
4. Read `docs/race_info_en.md`.
5. Read available jockey, pedigree, training, career-rate, and personal-best information.
6. Evaluate all Stage 2 categories.
7. Create or replace `results/stage2/XX_horse_name.md`.
8. Immediately update `results/stage2/stage2_scores.md`.
9. Continue to the next qualified horse.

---

## Stage 2 Categories

Maximum Stage 2 Score: **30 points**

### 1. Jockey Performance

Score: **0 to 6**

Evaluate:

- Recent jockey performance
- Win rate, top-two rate, and top-three rate
- Performance at today's racecourse
- Performance at today's distance
- Performance under similar race conditions
- Previous results with the same horse
- Ability to execute the horse's preferred running style

Use factual statistics and race results. Do not score reputation or name recognition.

### 2. Pedigree

Score: **0 to 5**

Evaluate:

- Sire-line suitability for today's distance
- Dam-sire suitability
- Course and surface tendencies
- Track-condition tendencies
- Stamina, speed, and acceleration characteristics relevant to today's race

Pedigree is supplementary evidence and must not override actual race performance.

### 3. Training Condition

Score: **-3 to +7**

Evaluate:

- Final workout
- Intermediate training pattern
- Workout time
- Sectional splits
- Acceleration or deceleration through the workout
- Paired-work result when available
- Comparison with previous-race training
- Evidence of improvement, maintenance, or decline

Do not use vague comments without measurable evidence.
Missing training information is neutral and must be recorded under Missing Information.

### 4. Overall Career Performance Rate

Score: **0 to 6**

Evaluate the horse's full career record using:

- Career win rate
- Top-two rate
- Top-three rate
- Total number of starts
- Performance consistency
- Performance under conditions related to today's race

Always consider sample size. A high rate from very few starts must not automatically receive the maximum score.

This category summarizes career performance rates only. It must not become a complete re-evaluation of Stage 1 ability.

### 5. Personal Best Performance

Score: **0 to 6**

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
Consider recency and reproducibility.

---

## Final Score

```text
Jockey Performance
+ Pedigree
+ Training Condition
+ Overall Career Performance Rate
+ Personal Best Performance
= Stage 2 Condition Score
```

Maximum: **30 points**

The total may become negative.
Do not artificially normalize scores.

---

## Evidence Requirement

Every numerical score must include factual evidence.

Acceptable evidence includes:

- Jockey win, top-two, and top-three statistics
- Jockey course and distance results
- Horse-and-jockey combination results
- Official pedigree information
- Training times and sectional splits
- Career win, top-two, and top-three rates
- Number of career starts
- Personal-best times, margins, ratings, or final-section records

Avoid unsupported statements such as:

- The jockey should suit the horse
- The pedigree looks ideal
- The workout seems good
- The horse will probably improve

Every conclusion must be traceable to supplied race history or official reference documents.

---

## Missing Information Policy

Unknown information is neutral.

- Never interpret missing information as poor suitability.
- Do not assign zero merely because evidence is unavailable.
- Do not invent unsupported suitability.
- Record unavailable items under `Missing Information`.

---

## Per-Horse Output

Create:

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

Example scoring section:

```markdown
## Stage 2 Scoring

- Jockey Performance: 5 / 6
- Pedigree: 4 / 5
- Training Condition: 5 / 7
- Overall Career Performance Rate: 5 / 6
- Personal Best Performance: 5 / 6

## Final Stage 2 Score

24 / 30
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

- Update immediately after each horse.
- Keep horse-number order.
- Do not rank in this file.
- Replace old scores when re-evaluated.

---

## Stage 2 Ranking

Create:

```text
results/stage2/stage2_ranking.md
```

Only after every qualified horse and every required re-evaluation has been completed.

Sort by Stage 2 Score and include:

- Rank
- Horse Number
- Horse Name
- Stage 1 Score
- Stage 2 Score
- Combined Score

---

## Re-evaluation Policy

Whenever the Stage 2 policy changes:

- Re-evaluate every previously scored horse.
- Replace previous Stage 2 evaluations.
- Do not preserve old-policy scores as active results.

The former Handicap Weight category is no longer part of Stage 2. Handicap evaluation has moved to Stage 1.

---

## Completion Criteria

Stage 2 is complete only after:

- Every horse with a Stage 1 Score greater than 20 has been evaluated using the current five categories.
- `results/stage2/stage2_scores.md` has been updated.
- `results/stage2/stage2_ranking.md` has been created.

Only then may the workflow proceed to Stage 3.
