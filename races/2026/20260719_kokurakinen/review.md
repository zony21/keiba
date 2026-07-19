# 2026 Kokura Kinen Post-Race Review

## Official Result

| Finish | No. | Horse | Pre-Race Status |
|---:|---:|---|---|
| 1 | 01 | Zendan Hayabusa | Outside the final shortlist |
| 2 | 17 | Giovanni | Caution candidate |
| 3 | 18 | Raze Drama | Fourth-ranked final candidate |

## Pre-Race Prediction

- Win candidate: 06 Gaia Mente
- Second choice: 09 G T Adamant
- Third choice: 02 Tagano Abby
- Fourth choice: 18 Raze Drama
- Caution candidate: 17 Giovanni

Projected order:

1. 06 Gaia Mente
2. 09 G T Adamant
3. 02 Tagano Abby
4. 17 Giovanni
5. 18 Raze Drama

## Final Betting Plan

The user excluded win bets and requested trifecta tickets.

| Bet Type | Combination | Stake |
|---|---|---:|
| Wide | 06-09 | 500 JPY |
| Wide | 02-06 | 300 JPY |
| Wide | 02-09 | 200 JPY |
| Quinella | 06-09 | 300 JPY |
| Trio | 02-06-09 | 200 JPY |
| Trifecta | 06→09→02 | 200 JPY |
| Trifecta | 06→02→09 | 100 JPY |
| Trifecta | 09→06→02 | 100 JPY |
| Trifecta | 09→02→06 | 100 JPY |
| **Total** |  | **2,000 JPY** |

## Betting Result

- Total stake: 2,000 JPY
- Payout: 0 JPY
- Net result: -2,000 JPY
- Return rate: 0%
- Outcome: Missed

## What Was Evaluated Correctly

### Giovanni was not completely discarded

Giovanni did not pass the formal Stage 2 shortlist, but was restored as a caution candidate because of strong market support and baseline ability. The horse finished second, so the decision to retain a high-market-confidence horse outside the formal shortlist was valid.

### Raze Drama remained in the final candidate group

Raze Drama was negatively adjusted for the outermost draw but remained the fourth-ranked final candidate. The horse finished third. Its direct Kokura 2000m evidence and ability to race prominently were correctly recognized.

### The race was correctly treated as vulnerable to positional variance

The prediction acknowledged that an 18-runner Kokura 2000m race could be strongly affected by position, ground loss, and traffic. This risk assessment was directionally correct, but it was not converted into an effective longshot selection or diversified ticket structure.

## Main Errors

### 1. Zendan Hayabusa was materially underestimated

This was the largest prediction failure. Zendan Hayabusa won at win odds of 32.4 despite being outside the final shortlist.

The review should re-examine whether the model underweighted:

- the benefit of horse number 01 and minimum ground loss;
- suitability for a tight-turning small course;
- early position and tactical flexibility;
- weight conditions;
- recent margins, sectional context, and race level rather than finishing position alone;
- improvement and development potential;
- upside created by a favorable race shape;
- the winning pattern of an overlooked horse receiving an efficient inside trip.

The problem was not simply failure to select a longshot. The feature set may have failed to represent the combination of conditions that created a realistic winning path.

### 2. Stage 2 eliminated Giovanni too aggressively

Giovanni finished second but was excluded from the formal Stage 3 scoring group because only four Stage 2 qualifiers advanced.

Potential changes:

- preserve an automatic review slot for strong Stage 1 horses;
- trigger a re-check when the model and the top three market rankings strongly disagree;
- retain two or three reserve candidates after Stage 2;
- replace binary pass/fail elimination with graded continuation groups;
- require an explicit elimination reason for a high-ability or heavily supported horse.

### 3. The outer-draw penalty for Raze Drama was too strong

Raze Drama received strong Stage 1 and Stage 2 scores, but its Stage 3 score dropped substantially because of horse number 18. The horse still finished third.

Outer-draw adjustments should not be applied in isolation. They should be conditioned on:

- early speed;
- distance to the first turn;
- number of competing front-runners;
- ability to obtain position without excessive effort;
- jockey positioning tendencies;
- direct course evidence;
- expected pace pressure.

The direction of the penalty was reasonable, but the magnitude appears excessive.

### 4. Betting concentration was too high

All tickets were centered on 06, 09, and 02. Once those three failed to occupy the top positions, the entire portfolio failed.

The prediction ranking and the betting portfolio should be treated as separate decisions. Future ticket construction should include:

- a primary structure using the highest-rated horses;
- a secondary structure using one market-supported reserve;
- a longshot structure using one high-upside horse with a plausible race path;
- protection against one of the top three ratings failing.

### 5. The model did not convert uncertainty into ticket coverage

The pre-race analysis already recognized uncertainty from the large field, short straight, and positional risk. However, the tickets remained narrow and deterministic.

When uncertainty is high, the system should either:

- widen coverage;
- reduce total stake;
- move from exact-order bets toward combination bets;
- or declare the race unsuitable for concentrated betting.

## Stage-by-Stage Review

### Stage 1

Review the scoring of Zendan Hayabusa and Giovanni using only pre-race historical information.

Required analysis:

- identify which categories caused the low score;
- compare those categories with the actual winning and placing factors;
- separate lack of data from incorrect weighting;
- test whether recent improvement was captured;
- verify whether course, distance, position, weight, and versatility were scored consistently.

Do not change weights solely because of one race. First test the proposed changes against multiple historical races.

### Stage 2

The four-horse qualification rule was too restrictive for this race.

Recommended structure:

- Core qualifiers: top four Stage 2 horses;
- Reserve qualifiers: next two horses or any horse meeting a rescue condition;
- Market-disagreement review: mandatory when a top-three market horse is excluded;
- Longshot review: one horse with a plausible course-and-pace winning path.

### Stage 3

Stage 3 correctly identified Raze Drama as a candidate but over-penalized the outside draw.

Recommended changes:

- make draw impact conditional rather than fixed;
- calculate whether early speed can offset draw loss;
- distinguish win probability from place probability;
- score race-shape upside and downside separately;
- preserve reserve horses through the final race-day review.

### Final Prediction and Betting

The final prediction should separately output:

1. Most likely winner;
2. Most likely top-three horses;
3. Best value candidates;
4. High-upside longshot;
5. Betting portfolio by risk level.

This prevents a single combined ranking from controlling every betting decision.

## Data and Feature Gaps

The following data should be verified or added before changing the scoring logic:

- official pace and sectional data;
- running positions at each call;
- final three-furlong time;
- margin and race-level context;
- carried weight differences;
- jockey decisions and path taken;
- ground-loss estimates;
- bias by draw and running style on the race day;
- whether the predicted middle pace matched the actual race;
- reasons the predicted top three failed.

## Proposed Improvement Priorities

1. Re-score Zendan Hayabusa and document the exact missed factors.
2. Re-score Giovanni and review the Stage 2 elimination threshold.
3. Recalculate Raze Drama with a conditional outer-draw penalty.
4. Add reserve candidates to Stage 2 and Stage 3.
5. Separate win probability, place probability, and expected value.
6. Add portfolio diversification rules for high-uncertainty races.
7. Validate every scoring change across multiple completed races before adoption.

## Overall Assessment

The main failure occurred before the final betting stage. Zendan Hayabusa was not identified as a realistic winning candidate, and Giovanni was removed from formal Stage 3 evaluation despite finishing second.

Raze Drama's third-place finish shows that the underlying ability and course analysis had useful signal, but the outer-draw adjustment was too severe. The final betting plan then amplified the evaluation error by concentrating nearly all exposure on 06, 09, and 02.

The highest-priority improvement is not simply to add more longshots. It is to identify horses with a credible winning path that is created by the interaction of draw, position, pace, weight, recent improvement, and course suitability. The Stage 2 elimination process and Stage 3 conditional adjustments should be revised only after re-testing these hypotheses across several historical races.