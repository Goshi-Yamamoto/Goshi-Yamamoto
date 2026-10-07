---
type: brief
engagement: perfect-competition
capability: marginal-analysis
date: 2026-09-30
status: committed
---

# Perfect Competition — Engagement Brief

## The problem
This farm needs to determine the optimal combination of crop varieties, cultivation beds, and human resources to maximize profit. The farm can grow a maximum of 20 beds of tomatoes, 20 beds of carrots, and 30 beds of mesclun during the 36-week season. The revenue per bed is $8,800 for tomatoes, $2,094 for carrots, and $2,700 for mesclun. Even though the total crop capacity is 70 beds, the farm has space for only 64 beds. The farm also has a limited amount of labor available, consisting of 720 owner hours plus up to four temporary workers at 1,440 hours each for a total of 6,480 hours, and it must pay $20,000 in fixed costs for the season. However, it cannot control crop prices. Furthermore, the decision-making deadline is in July, after which the plan cannot be altered.


## What I am assuming
The data derived from these two tables serve as the foundational assumptions for my analysis, treated as accurate and reliable information. Consulting these tables allows for a precise understanding of the revenue, profit, and cost metrics associated with each crop. The first table presents data on cultivation beds, revenue, labor requirements, fertilizer costs, and the rate of diminishing returns. The second table details cultivation periods, fixed costs, analysis expenses, cultivation bed costs, and worker productivity. While I proceed with calculations and projections based on these parameters, it is also essential to verify the reliability of the data whenever possible. 

- **Dataset: Price**
  - Revenue per bed: Tomatoes = $8,800, Carrots = $2,094, Mesclun = $2,700
  - Fertilizer cost per bed: Tomatoes = $880, Carrots = $440, Mesclun = $880
  - Wage rates: $17.36/hr for temporary labor (implied $34.72/hr for owner labor)
  - Fixed costs: $20,000 for the season
- **Dataset: Rates**
  - Diminishing-returns penalty rates: Tomatoes = 10%, Carrots = 2.5%, Mesclun = 1.25%
- **Dataset: Hours**:
  - Total available labor cap: 6,480 hours (720 owner hours + up to 4 temporary workers at 1,440 hours each)
  - Base labor per week per bed: Tomatoes = 2.5 hrs, Carrots = 0.833 hrs, Mesclun = 1.25 hrs
  - Season length: 36 weeks
  - Land capacity: 64 available beds (individual caps sum to 70: Tomatoes 20, Carrots 20, Mesclun 30)
  - Labor requirement formula: Labor(q) = q × (hrs/wk/bed) × 36 × (1 + diminishing_rate)^q


## Hypothesis
Firstly, I expect the optimal mix to be 20 beds of tomatoes, 20 beds of carrots, and 24 beds of mesclun because of the high revenue, the low diminishing-returns rate, and the cost of fertilizer.
A comparison of these three crops revealed that in terms of revenue, tomatoes are in first place ($8,800), mesclun is in second place ($2,700), and carrots are in third place ($2,094). While 1.25% has the lowest diminishing-returns rate of change for mesclun, 2.5% (carrots) is second, and 10% (tomatoes) is third, the cost of fertilizer for carrots ($440) is half the cost of fertilizer for tomatoes and mesclun ($880). Therefore, I decided to allocate the maximum number of planting beds to tomatoes and carrots, and assign the remaining 24 beds to mesclun.

## Labor Analysis
- **Analysis: The 20th tomato bed cost in labor hours**
  - Total Labor for 20 Tomato Beds: 20 × 2.5 × 36 × (1 + 0.10)^20 = 12,109.5 hours
  - Total Labor for 19 Tomato Beds: 19 × 2.5 × 36 × (1 + 0.10)^19 = 10,458.2 hours
  - Marginal Labor for the 20th Tomato Bed: 12,109.5 - 10,458.2 = 1,651.3 hours
  - The labor cost for the 20th Tomato bed: $17.36 × 1,651.3 = $28,666.57
- **Analysis: The 20th tomato bed profit**
  - The labor cost for the 20th Tomato bed + Fertilizer cost per bed ($880) > Revenue per bed ($8,800)
The revenue from the 20th bed of tomatoes is much lower than its marginal cost. As a price taker in a perfectly competitive market, it is not reasonable to produce when the price is lower than the marginal cost ($P < MC$). Therefore, the 20th bed of tomatoes does not earn its place.


## How I would know I was wrong
While I bet on the maximum number of 20 beds for tomatoes, my initial reasoning was clearly wrong because of the labor cost. I would also say that if the Solver's answer exceeds 24 beds of mesclun, my reasoning was also wrong.
