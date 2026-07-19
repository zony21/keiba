# Kokura Kinen Review — Logic Revision Tracking

## Status

Implemented in official scoring logic v4.

The original pre-race scores, prediction, and post-race review remain unchanged.

## Source Review

- `races/2026/20260719_kokurakinen/review.md`

## Official Revised Logic

- `docs/scoring_logic_v4.md`
- `docs/stage1_evaluation_workflow.md`
- `docs/stage2_evaluation_workflow.md`
- `docs/stage3_evaluation_workflow.md`

## Review Finding to Logic Mapping

| Review finding | v4 response |
|---|---|
| Zendan Hayabusa's winning path was not represented | Added Hidden Ability, stronger opponent-quality review, Improvement Trend, and separate course-geometry evidence |
| Giovanni was eliminated too early | Added Hidden-Ability Rescue and completed-ranking Top-Six Safety Net for Stage 2 qualification |
| Raze Drama received an excessive outer-draw penalty | Replaced isolated draw scoring with Draw and Trip Interaction using start speed, tactical speed, position flexibility, first-turn distance, and course evidence |
| AI and market rankings disagreed without a formal correction process | Added mandatory Market Discrepancy Recheck with explicit trigger conditions and conclusions |
| Pace labels were too simple | Added Pace Adaptability in Stage 2 and field-composition-based Race Pace Scenario scoring in Stage 3 |
| Tactical options were underrepresented | Added Position Flexibility in Stage 2 |
| Old global logic conflicted with active workflows | Set `scoring_logic_v4.md` as the official version and aligned Stage 1, Stage 2, and Stage 3 maximum scores at 30 each |

## Non-Retroactive Rule

The 2026 Kokura Kinen prediction must not be recalculated and presented as though v4 had been used before the race.

Any retrospective v4 test must be stored separately and clearly labeled as a backtest.

## Validation Requirement

Before making further weight changes, test v4 across multiple completed races and record:

- Stage 1 top-three capture rate
- Stage 2 qualification rate for eventual top-three finishers
- Stage 3 draw-adjustment accuracy
- Market discrepancy trigger frequency
- Win, place, and top-three ranking accuracy
- Betting return and portfolio concentration

A single race result is not sufficient evidence for another scoring-weight revision.