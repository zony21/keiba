# Horse Racing AI Scoring Logic v4.0

## Status

This document is the official scoring logic for new races.

It supersedes `docs/scoring_logic_v3.md` for active evaluation. Version 3 remains in the repository as historical reference only.

## Objective

Evaluate every horse through three separate stages without mixing historical ability, supporting race conditions, race-day information, or betting strategy.

The revision addresses the following failure patterns identified in the 2026 Kokura Kinen review:

- Hidden ability was not sufficiently captured when finish position understated race quality.
- Improving horses could be eliminated before supporting factors were reviewed.
- A rigid Stage 1 cutoff could remove a serious contender.
- Draw penalties were applied without enough interaction with start speed, tactical speed, running style, and course evidence.
- A large difference between AI assessment and the betting market was recorded but did not force a structured recheck.

The purpose is not to retroactively fit one race result. Every new rule must be applicable to future races using factual evidence.

# Global Principles

1. Evaluate each horse independently and sequentially.
2. Use only verified source material.
3. Record missing information as `Unknown`; never convert it automatically to zero or weakness.
4. Do not award duplicate points for the same evidence unless the separate meaning is explicitly explained.
5. Do not use odds or betting popularity in Stage 1 or Stage 2.
6. Do not create race marks, expected-value rankings, or betting selections before all three stages are complete.
7. Preserve pre-race scores after the result. Post-race review may propose future changes but must not rewrite the historical prediction.
8. A post-race result alone is not proof that a category was wrong. Changes require a repeatable causal explanation.

# Stage 1 — Historical Ability

Maximum score: **30 points**

Stage 1 answers:

> How strong and repeatable is this horse based only on historical race evidence?

## 1. Similar-Condition Performance — 0 to 10

Evaluate:

- Today's distance and nearby distances
- Course geometry and small-turn suitability
- Track direction
- Surface and historical going
- Similar class
- Similar field size and race shape

Priority:

1. Direct evidence at today's distance and course type
2. Evidence within approximately ±200m
3. Strong middle-distance evidence at 2400m to 2600m when relevant
4. Similar small-turn or short-straight evidence
5. General middle-distance evidence

Distance similarity and course similarity must be evaluated separately.

## 2. Demonstrated Race Ability — 0 to 8

Evaluate:

- Margin after class and condition adjustment
- Quality of opponents
- Strength of the winner and horses finishing nearby
- Running position and trip
- Closing section
- Ability to sustain speed
- Performance under pressure

Finish position alone is insufficient.

Opponent quality must consider who the horse raced against, not only the nominal class label.

## 3. Hidden Ability — 0 to 3

This category captures verified ability that the final placing may understate.

Eligible evidence includes:

- Small defeat margin against strong opposition
- Strong performance after a documented wide trip, blocked run, slow start, pace disadvantage, or unsuitable condition
- Sustained performance after racing against the dominant pace pattern
- Better sectional or position evidence than the final placing suggests
- Competitive performance under a materially unfavorable weight or draw

Rules:

- The disadvantage must be supported by supplied facts.
- Do not invent trouble or excuse every poor result.
- The same incident may not receive full credit again under another category.
- A horse receives 0 when no verified hidden-ability evidence exists.

## 4. Improvement Trend — -2 to +5

Evaluate the latest races, normally the most recent five starts.

Use:

- Condition-adjusted margin trend
- Class-adjusted race-content trend
- Running-position improvement
- Closing-section improvement
- Increased distance range or tactical range
- Evidence of physical or competitive development contained in the supplied records

Guideline:

- `+4 to +5`: clear repeated improvement against equal or stronger opposition
- `+2 to +3`: meaningful positive progression
- `0 to +1`: stable or slightly improving
- `-1 to -2`: verified decline after adjusting for conditions

One poor race does not prove decline. One good race does not prove sustained improvement.

## 5. Winning Ability and Consistency — 0 to 4

Evaluate:

- Win rate
- Top-two and top-three frequency
- Ability to finish first
- Repeatability under relevant conditions
- Dependence on one narrow race shape
- Sample size

## 6. Age and Sex Historical Adjustment — 0 to -4

This is deduction-only and must use the race-specific historical reference when available.

Rules:

- Age alone must not create a large deduction without evidence of decline.
- Sex or gelding status alone must not create an automatic deduction.
- Actual recent performance is more important than a broad historical trend.
- The combined deduction may not exceed -4.

## Stage 1 Formula

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

# Stage 2 — Supporting Condition Factors

Maximum score: **30 points**

Stage 2 answers:

> Which qualified horses receive additional support from jockey, pedigree, training, performance profile, pace adaptability, and tactical flexibility for today's race?

Stage 2 must not repeat Stage 1 historical ability or handicap scoring.

## Qualification

A horse proceeds to Stage 2 when any one of the following is true:

1. Stage 1 score is 21 or higher.
2. Stage 1 score is at least 18, Hidden Ability is at least 2, and Demonstrated Race Ability is at least 6.
3. The horse is within the top six of the completed Stage 1 ability ranking.

The top-six safety rule is applied only after all Stage 1 evaluations are complete.

Every qualification reason must be recorded.

## Categories

### 1. Jockey Performance — 0 to 5

Use recent, course, distance, similar-condition, and horse-jockey combination evidence.

### 2. Pedigree Support — 0 to 4

Use pedigree only as supporting evidence for distance, course, surface, going, stamina, speed, and acceleration.

### 3. Training Condition — -2 to +6

Use measurable workout evidence, comparison with previous preparation, sectional pattern, and documented maintenance or improvement.

### 4. Career Performance Rate — 0 to 4

Evaluate win, top-two, and top-three rates with sample-size adjustment. Do not re-score complete historical ability.

### 5. Relevant Personal Best — 0 to 4

Use a verified best performance under comparable conditions. Adjust for course, distance, going, pace, and recency.

### 6. Pace Adaptability — 0 to 4

Evaluate verified performance across slow, middle, and fast pace environments.

A horse with evidence under multiple pace structures receives more credit than a horse requiring one exact pace.

### 7. Position Flexibility — 0 to 3

Evaluate whether the horse can obtain competitive results from more than one tactical position.

Use factual evidence for:

- Ability to lead, stalk, race midfield, or close
- Recovery from a slower start
- Ability to avoid being trapped by one mandatory running position
- Compatibility between the jockey and the horse's tactical options

Do not reward theoretical versatility without race evidence.

## Stage 2 Formula

```text
Jockey Performance       0..5
+ Pedigree Support        0..4
+ Training Condition     -2..6
+ Career Performance Rate 0..4
+ Relevant Personal Best  0..4
+ Pace Adaptability       0..4
+ Position Flexibility    0..3
= Stage 2 Condition Score
```

Maximum: **30**

# Stage 3 — Race-Day Conditions

Maximum score: **30 points**

Stage 3 answers:

> How do confirmed race-day conditions, projected field shape, official draw, and the latest market affect each Stage 2 qualifier?

## 1. Weather Suitability — 0 to 4

Evaluate only from historical evidence and confirmed weather.

## 2. Track Condition Suitability — 0 to 6

Evaluate confirmed going using verified race records.

## 3. Race Pace Scenario — -2 to +8

Evaluate:

- Projected number of pace setters
- Expected early pressure
- Horse's preferred pace
- Ability to perform when the projected pace differs from its ideal pace
- Likely position entering the first turn

## 4. Draw and Trip Interaction — -3 to +5

Do not score the draw in isolation.

Evaluate the interaction of:

- Official draw
- Start performance
- Early tactical speed
- Preferred running position
- Distance to the first turn
- Course geometry
- Historical course evidence
- Risk of covering extra ground
- Risk of becoming boxed in

An outside draw is not automatically a major negative. A horse with sufficient start speed, tactical flexibility, and direct course evidence may receive only a small deduction or no deduction.

An inside draw is not automatically positive when it materially increases traffic or position risk for that horse.

## 5. Official Race-Day Factors — -1 to +3

Use only confirmed information such as:

- Official body weight and change when supplied
- Late scratch effects
- Equipment or rider changes officially confirmed
- Other operational changes not already scored

Subjective paddock impressions are prohibited unless the project later adopts a separate verified paddock-data standard.

## 6. Latest Odds — -2 to +4

Odds are supplementary market evidence, not proof of ability.

Evaluate:

- Strength or weakness of market support
- Whether support is consistent with verified evidence
- Whether the price movement is material

Do not determine expected value or betting strategy inside Stage 3.

## Market Discrepancy Recheck Flag

Record:

- AI rank before odds
- Market rank
- Absolute rank difference
- Recheck status
- Recheck conclusion

A mandatory factual recheck is triggered when:

- The rank difference is 5 or more; or
- A market top-three horse was excluded before Stage 3; or
- A high Stage 1 or Stage 2 horse receives unusually weak market support.

The recheck must inspect source completeness, identity mapping, missing evidence, scoring arithmetic, and duplicated or omitted categories.

The recheck must not automatically change a score merely to match the market.

## Stage 3 Formula

```text
Weather Suitability       0..4
+ Track Condition         0..6
+ Race Pace Scenario      -2..8
+ Draw and Trip Interaction -3..5
+ Official Race-Day Factors -1..3
+ Latest Odds             -2..4
= Stage 3 Race-Day Score
```

Maximum: **30**

# Final Integration

After all stages are complete:

```text
Combined Score = Stage 1 + Stage 2 + Stage 3
```

Only then may the system create:

- Ability ranking
- Condition ranking
- Race-day ranking
- Final race marks
- Expected-value ranking
- Betting combinations
- Stake allocation
- Pass/no-bet decision

A horse excluded from Stage 2 is not automatically prohibited from appearing as a market-warning note, but it cannot be promoted into the scored final ranking without completing the required Stage 2 and Stage 3 evaluations.

When a mandatory market discrepancy recheck identifies missing or erroneous source processing, complete the missing evaluation before final prediction.

# Post-Race Review

For every race, preserve the original scores and record:

- Final result
- Prediction result
- Stake, return, and ROI
- Under-evaluated placed horses
- Over-evaluated predicted horses
- Missing data
- Feature omissions
- Stage-gate failures
- Draw and pace interaction errors
- Market discrepancy warnings
- Proposed logic changes

A proposed change becomes official only when it is generalizable, evidence-based, and documented in the versioned scoring logic.