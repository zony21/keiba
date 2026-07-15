# keiba

競馬予想を特徴量ベースで全頭評価し、採点・予想・結果検証を蓄積するリポジトリ。

## Official Logic

- `docs/scoring_logic_v3.md`
- `templates/feature_stage1.csv`
- `templates/race_score.csv`

`scoring_logic_v2.md`以前は検証履歴として残すが、新規レースでは使用しない。

## Stage 1 Workflow

1. Save race materials under `races/YYYY/YYYYMMDD_RaceName/docs/`.
2. Evaluate horses in predefined batches using feature-by-feature comparison.
3. Complete all Stage 1 evaluations.
4. Verify consistency only after every horse has been scored.
5. Finalize the Stage 1 Ability Ranking.

## Stage 2 Workflow

Stage 2 evaluates **today's race conditions only**. Historical ability is inherited from Stage 1 and must not be evaluated again.

### Horse Selection

- Only horses with a **Stage 1 Score greater than 20** proceed to Stage 2.
- Horses scoring **20 or below are eliminated** before Stage 2 begins.

### Evaluation Flow

For each qualified horse:

1. Read the Stage 1 result.
2. Read `data.md`.
3. Read `career.md`.
4. Evaluate today's race conditions.
5. Update `results/stage2/XX_horse_name.md`.
6. Immediately update `results/stage2/stage2_scores.md`.

### Evaluation Categories (30 points)

- Course Suitability (0–8)
- Distance Suitability (0–6)
- Track Condition Suitability (-2–4)
- Expected Pace Suitability (-4–6)
- Running Style Suitability (-2–6)

Do not use odds, popularity, betting strategy, race-day body weight, workouts, or paddock information.

Missing information must be recorded as "Missing Information" and must never be treated as zero.

After every qualified horse has been evaluated, create `results/stage2/stage2_ranking.md` and proceed to Stage 3.

## Overall Workflow

1. Stage 1: Historical Ability (30)
2. Stage 2: Today's Conditions (30)
3. Stage 3: Race-day Information (10)
4. Combine scores
5. Determine expected value and betting strategy
6. Save prediction results
7. Perform post-race review