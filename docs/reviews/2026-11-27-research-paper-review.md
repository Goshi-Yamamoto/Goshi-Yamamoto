# Goshi Yamamoto — feedback, sweep of 2026-11-27

## Research paper — a second read of your plan and model

**What I read**, at `main`: `docs/briefs/2026-11-26-research-brief.md`, `capabilities/economic-research/spec.md`, both new figures in `analysis/figures/`, and the research-paper entries in `prompt-log.md`. I did not open `capabilities/economic-research/model.xlsx` cell by cell this pass; I checked the per-cup arithmetic from the spec's inputs instead. If a file that matters is missing, reply here and name it.

Goshi, the brief answers every question from my last read: the model now searches for the best price instead of choosing among four, linear demand is the main case with constant elasticity as the check, each elasticity has a source and a note on what it does and does not measure, the cost per cup has its four inputs, and food enters as a complement. The model is built, checked with Solver from two starting points, and audited. Figure 1 already answers Hypothesis 1. Figure 2 raises the question that matters most now.

1. **Why does the model cut prices so deeply?** Figure 2 recommends a coffee price cut of about 30 to 40% at elasticities of -2.0 and below, and the constant-elasticity run stops at your lower bound for every elasticity. Add up what one more coffee costs you (beans, cup and lid, the per-transaction fee) and what it brings in through food at a 40% attach rate. Which is larger? If one more coffee brings in more food margin than it costs, what price does any demand model want, and is that what you believe about a small cafe?
2. **Does food attach stay at 40% when the price falls?** A 35% coffee price cut in your model brings in new coffee customers, and 40% of them buy food. Would new customers drawn by a cheaper coffee buy food at the same rate as your regulars? What would the optimal price be at your 25% attach rate?
3. **Hypothesis 2.** Figure 2's three pass-through lines nearly sit on top of each other, while elasticity moves the result from a large increase to a large cut. That supports Hypothesis 2. How much of the elasticity effect comes from the food assumption rather than from coffee demand itself?
4. **The recommendation.** The paper is four pages. Which one or two numbers from the model will a cafe owner act on?
5. **Mechanical.** The spec's Conventions (item 6) and Validation Rule 11 still say the search runs from -20% to +40%; your audit expanded it to -50% to +60%. Update both so the spec describes the model as built. "Bried" appears twice in `prompt-log.md`.
