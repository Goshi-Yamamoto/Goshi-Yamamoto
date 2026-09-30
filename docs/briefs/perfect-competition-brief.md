---
type: brief
engagement: perfect-competition
capability: marginal-analysis
date: 2026-09-30
status: committed
---

# Perfect Competition — Engagement Brief

## The problem
This farm needs to determine the optimal combination of crop varieties, cultivation beds, and human resources to maximize profit. The farm can grow a maximum of 20 beds of tomatoes, 20 beds of carrots, and 30 beds of mesclun during the 36-week season. The revenue per bed is $8,800 for tomatoes, $2,094 for carrots, and $2,700 for mesclun. Even though the total crop capacity is 70 beds, the farm has space for only 64 beds. The farm also has a limited amount of labor available, and it must pay $20,000 in fixed costs for the season. However, it cannot control crop prices. Furthermore, the decision-making deadline is in July, after which the plan cannot be altered.


## What I am assuming
The data derived from these two tables serve as the foundational assumptions for my analysis, treated as accurate and reliable information. Consulting these tables allows for a precise understanding of the revenue, profit, and cost metrics associated with each crop. The first table presents data on cultivation beds, revenue, labor requirements, fertilizer costs, and the rate of diminishing returns. The second table details cultivation periods, fixed costs, analysis expenses, cultivation bed costs, and worker productivity. While I proceed with calculations and projections based on these parameters, it is also essential to verify the reliability of the data whenever possible. 


## Hypothesis
I expect the optimal mix to be 20 beds of tomatoes, 20 beds of carrots, and 24 beds of mesclun because of the high revenue, the low diminishing-returns rate, and the cost of fertilizer.
A comparison of these three crops revealed that in terms of revenue, tomatoes are in first place ($8,800), mesclun is in second place ($2,700), and carrots are in third place ($2,094). While 1.25% has the lowest diminishing-returns rate of change for mesclun, 2.5% (carrots) is second, and 10% (tomatoes) is third, the cost of fertilizer for carrots ($440) is half the cost of fertilizer for tomatoes and mesclun ($880). Therefore, I decided to allocate the maximum number of planting beds to tomatoes and carrots, and assign the remaining 24 beds to mesclun.


## How I would know I was wrong
I bet on the maximum number of 20 beds for tomatoes and carrots. If the Solver's answer does not support the maximum number of beds, my reasoning was wrong. I can also say that if the Solver's answer exceeds 24 beds of mesclun, my reasoning was also wrong.
