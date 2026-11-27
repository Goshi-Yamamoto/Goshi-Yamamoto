---
type: spec
engagement: research-paper
capability: elasticity-analysis
date: 2026-11-27
status: committed
---

# Arabica Coffee Price and Cafe Pricing — Model Specification

## Purpose

This model finds the coffee price that gives the highest monthly contribution profit for a small cafe in Hawaii.

The model uses a 12 oz hot black coffee with a base price of $5.00 and 2,000 cups sold per month. It also tests how the result changes when customer price elasticity, coffee-cost pass-through, and food assumptions change.

## Inputs — the named contract

| **Name** | **Value** | **Unit** | **Source** |
| --- | ---: | --- | --- |
| `BASE_PRICE` | 5.00 | USD per cup | Research Brief assumption |
| `BASE_QTY` | 2000 | cups per month | Research Brief assumption |
| `CUP_SIZE_OZ` | 12 | oz per cup | Research Brief assumption |
| `COFFEE_G_PER_CUP` | 19.5 | grams roasted coffee per cup | Specialty Coffee Association (2017) |
| `ROAST_LOSS_PCT` | 15% | weight loss | Franca et al. (2009) |
| `GREEN_PRICE_2023` | 4.54 | USD per kg | World Bank (2026) |
| `GREEN_PRICE_2025` | 8.47 | USD per kg | World Bank (2026) |
| `ROASTED_BEAN_BASE` | 12.00 | USD per lb | Bellwether Coffee (2026) |
| `PASS_THROUGH_MIN` | 0% | percentage | Model assumption |
| `PASS_THROUGH_MAX` | 100% | percentage | Model assumption |
| `PASS_THROUGH_STEP` | 10% | percentage-point step | Model assumption |
| `CUP_COST` | 0.12 | USD per cup | Staples (n.d.-a) |
| `LID_COST` | 0.10 | USD per lid | Staples (n.d.-b) |
| `CUP_LID_COST` | 0.22 | USD per coffee | Staples (n.d.-a; n.d.-b) |
| `CARD_RATE` | 2.6% | percentage of sales | Square (n.d.-b) |
| `CARD_FIXED_FEE` | 0.15 | USD per transaction | Square (n.d.-b) |
| `FOOD_ATTACH_BASE` | 40% | percentage of customers | Starbucks Corporation (2023) |
| `FOOD_ATTACH_LOW` | 25% | percentage of customers | Sensitivity assumption |
| `FOOD_ATTACH_HIGH` | 50% | percentage of customers | Sensitivity assumption |
| `FOOD_PRICE` | 5.00 | USD per food purchase | Square (n.d.-a) |
| `FOOD_COST_PCT` | 40% | percentage of food price | QuickStok (n.d.) |
| `FOOD_COST_LOW` | 35% | percentage of food price | Sensitivity assumption |
| `FOOD_COST_HIGH` | 45% | percentage of food price | Sensitivity assumption |
| `ELASTICITY_LOW` | -0.5 | elasticity | Hawaii Department of Agriculture (2024) |
| `ELASTICITY_MID1` | -1.0 | elasticity | Koerner (2002) |
| `ELASTICITY_MID2` | -2.0 | elasticity | Nakamura & Zerom (2009), Table 5 |
| `ELASTICITY_HIGH` | -3.5 | elasticity | Nakamura & Zerom (2009), Table 5 |
| `ELASTICITY_MIN` | -4.0 | elasticity | Model assumption |
| `ELASTICITY_MAX` | -0.5 | elasticity | Model assumption |
| `ELASTICITY_STEP` | 0.1 | elasticity step | Model assumption |
| `PRICE_SEARCH_MIN` | -20% | price change | Model assumption |
| `PRICE_SEARCH_MAX` | +40% | price change | Model assumption |
| `PRICE_STEP` | 1% | percentage-point step | Model assumption |
| `SEARCH_MIN_USED` | -50% | price change | Boundary Rule |
| `SEARCH_MAX_USED` | +60% | price change | Boundary Rule |

The World Bank values are annual averages from the `Coffee, Arabica` series. I will also calculate the 2023 and 2025 averages from the 12 monthly observations for each year as a check.

## Structure

1. **Inputs**: Stores the baseline cafe assumptions, coffee costs, packaging costs, payment fees, food assumptions, elasticity values, and price-search range.
2. **Coffee Cost Model**: Calculates the base bean cost per cup and the increase in bean cost from 2023 to 2025.
3. **Demand Model**: Calculates monthly coffee quantity at each tested price.
4. **Food Contribution Model**: Calculates food purchases, food revenue, and food variable cost.
5. **Contribution Profit Model**: Calculates total revenue, variable costs, and monthly contribution profit.
6. **Price Search**: Tests price changes from -20% to +40% in 1 percentage-point steps.
7. **Sensitivity & Robustness**: Tests different elasticity, pass-through, food-attach, food-cost, and demand assumptions.
8. **Figures**: Creates the two main figures for the research paper.
9. **Checks & Audit**: Checks formulas, assumptions, and model results.

## Calculation Logic

The model uses the following formulas:

1. **Roasted Coffee Used per Cup**
   - `COFFEE_G_PER_CUP` = 55 g/L × 0.355 L
   - `COFFEE_G_PER_CUP` ≈ 19.5 g

2. **Green Coffee Needed per Cup**
   - `GREEN_G_PER_CUP` = `COFFEE_G_PER_CUP` / (1 - `ROAST_LOSS_PCT`)

3. **Base Bean Cost per Cup**
   - `BASE_BEAN_COST_PER_CUP` = `ROASTED_BEAN_BASE` × `COFFEE_G_PER_CUP` / 453.6

4. **Green Coffee Price Increase**
   - `GREEN_PRICE_CHANGE` = `GREEN_PRICE_2025` - `GREEN_PRICE_2023`

5. **Bean Cost Increase per Cup**
   - `BEAN_COST_INCREASE_PER_CUP` = (`GREEN_PRICE_CHANGE` / 1000) × `GREEN_G_PER_CUP` × `PASS_THROUGH`

6. **New Bean Cost per Cup**
   - `NEW_BEAN_COST_PER_CUP` = `BASE_BEAN_COST_PER_CUP` + `BEAN_COST_INCREASE_PER_CUP`

7. **Test Coffee Price**
   - `TEST_PRICE` = `BASE_PRICE` × (1 + `PRICE_CHANGE_PCT`)

8. **Linear Demand Quantity**
   - `QTY_CHANGE` = (`ELASTICITY` × `BASE_QTY` / `BASE_PRICE`) × (`TEST_PRICE` - `BASE_PRICE`)
   - `TEST_QTY` = MAX(0, `BASE_QTY` + `QTY_CHANGE`)

9. **Constant-Elasticity Demand Quantity**
   - `TEST_QTY` = `BASE_QTY` × (`TEST_PRICE` / `BASE_PRICE`)^`ELASTICITY`

10. **Monthly Coffee Bean Cost**
   - `MONTHLY_BEAN_COST` = `TEST_QTY` × `NEW_BEAN_COST_PER_CUP`

11. **Coffee Revenue**
   - `COFFEE_REVENUE` = `TEST_PRICE` × `TEST_QTY`

12. **Food Purchases**
   - `FOOD_PURCHASES` = `TEST_QTY` × `FOOD_ATTACH_RATE`

13. **Food Revenue**
   - `FOOD_REVENUE` = `FOOD_PURCHASES` × `FOOD_PRICE`

14. **Food Variable Cost**
   - `FOOD_VAR_COST` = `FOOD_REVENUE` × `FOOD_COST_PCT`

15. **Packaging Cost**
   - `PACKAGING_COST` = `TEST_QTY` × `CUP_LID_COST`

16. **Total Revenue**
   - `TOTAL_REVENUE` = `COFFEE_REVENUE` + `FOOD_REVENUE`

17. **Payment Processing Cost**
   - `PROCESSING_COST` = (`TOTAL_REVENUE` × `CARD_RATE`) + (`TEST_QTY` × `CARD_FIXED_FEE`)

18. **Monthly Contribution Profit**
   - `MONTHLY_CONTRIBUTION_PROFIT` = `TOTAL_REVENUE` - `MONTHLY_BEAN_COST` - `PACKAGING_COST` - `FOOD_VAR_COST` - `PROCESSING_COST`

19. **Cost-Based Price Increase**
   - `COST_BASED_INCREASE_PCT` = `BEAN_COST_INCREASE_PER_CUP` / `BASE_PRICE`

## Conventions

The model follows these rules:

1. **Baseline Point**: The base coffee price is $5.00 and monthly sales are 2,000 cups.
2. **Linear Demand**: Each elasticity value applies at the $5.00 and 2,000-cup baseline point.
3. **Elasticity Range**: The model tests elasticity from -0.5 to -4.0 in steps of 0.1.
4. **Elasticity Reference Cases**:
   - -0.5 = relatively inelastic
   - -1.0 = middle case
   - -2.0 = more elastic
   - -3.5 = high-elasticity case
5. **Pass-Through Range**: The model tests pass-through from 0% to 100% in steps of 10%.
6. **Price Search**: The model tests price changes from -20% to +40% in 1 percentage-point steps.
7. **Reference Pricing Strategies**:
   - No price increase
   - Cost-based increase
   - 5% price increase
   - 10% price increase
8. **Cost-Based Increase Rule**:
   - `COST_BASED_INCREASE_PCT` = `BEAN_COST_INCREASE_PER_CUP` / `BASE_PRICE`
9. **Boundary Rule**:
   - If the best price is at -20% or +40%, I will expand the search range and run the model again.
   - In the constant-elasticity model, if elasticity is -1 or higher and there is no finite profit-maximizing price, I will record **no finite optimum**.
10. **One Customer Rule**: One coffee purchase is treated as one customer and one transaction.
11. **Food Complement Rule**: If a coffee customer is lost, the model also includes the possible loss of a food purchase.
12. **Fixed Costs**: Rent and fixed labor costs are not included because they do not change between pricing strategies.
13. **2023 Bean Benchmark**: The $12/lb roasted-bean price is used as a practical benchmark for the 2023 wholesale roasted-coffee price.
14. **Industry Benchmarks**: The $12/lb bean price and 40% food-cost rate are industry reference values, not direct observations from one Hawaii cafe.

## Validation Rules

The completed model must pass the following checks:

1. **Baseline Demand Check**
   - At `TEST_PRICE = $5.00`, `TEST_QTY` must equal 2,000 cups for every elasticity scenario.

2. **Coffee Usage Check**
   - 55 g/L × 0.355 L should give approximately 19.5 g of roasted coffee per cup.

3. **Roasting Loss Check**
   - `GREEN_G_PER_CUP` must be greater than 19.5 g.

4. **Bean Cost Check**
   - `BASE_BEAN_COST_PER_CUP` must use the $12/lb benchmark.
   - `BEAN_COST_INCREASE_PER_CUP` must use the difference between the 2025 and 2023 World Bank prices.
   - At 0% pass-through, the increase must equal $0.
   - At 100% pass-through, the full calculated increase must be included.

5. **Packaging Check**
   - `CUP_COST` = $0.12.
   - `LID_COST` = $0.10.
   - `CUP_LID_COST` = $0.22.
   - `PACKAGING_COST` must equal `TEST_QTY × CUP_LID_COST`.

6. **Food Contribution Check**
   - At a $5.00 food price and 40% food cost:
   - Food variable cost = $2.00.
   - Food contribution per food purchase = $3.00.

7. **Food-Attach Check**
   - At a 40% food-attach rate, expected food purchases must equal `TEST_QTY × 40%`.

8. **Processing Fee Check**
   - The model must charge 2.6% of sales plus $0.15 per transaction.

9. **Elasticity Step Check**
   - The model must test elasticity from -0.5 to -4.0 in steps of 0.1.

10. **Pass-Through Step Check**
   - The model must test pass-through from 0% to 100% in steps of 10%.

11. **Price Search Check**
   - Every 1 percentage-point change from -20% to +40% must be tested.
   - If the best result is at either end, the search range must be expanded.

12. **Constant-Elasticity Check**
   - The model must use:
   - `TEST_QTY = BASE_QTY × (TEST_PRICE / BASE_PRICE)^ELASTICITY`
   - If there is no finite optimum for elasticity of -1 or higher, record **no finite optimum**.

13. **Formula and Error Checks**
   - Calculated cells must use formulas instead of manually entered results.
   - There should be no `#REF!`, `#DIV/0!`, or `#NAME?` errors.
   - Quantity cannot be below zero.

## Success Criteria

The research will be complete when:

1. The model calculates the increase in coffee-bean cost per cup from 2023 to 2025.
2. The model compares the increase with the $0.50 threshold.
3. The model finds the optimal price under different elasticity and pass-through values.
4. The model shows whether elasticity or pass-through has the larger effect on the optimal price.
5. The final pricing recommendation is supported by the model results.

## Figures

### Figure 1 — Increase in Coffee Bean Cost per Cup

Figure 1 will show the increase in coffee-bean cost per cup under different pass-through rates.

- X-axis: Pass-through from 0% to 100%
- X-axis step: 10%
- Y-axis: Bean-cost increase per cup
- Reference line: $0.50 per cup

This figure will be used to test Hypothesis 1.

### Figure 2 — Optimal Price Change by Elasticity and Pass-Through

Figure 2 will show the optimal coffee price change across the full elasticity range.

The figure will include three lines:

- 0% pass-through
- 50% pass-through
- 100% pass-through

Main items:

- X-axis: Elasticity from -0.5 to -4.0
- X-axis step: 0.1
- Y-axis: Optimal coffee price change (%)

This figure will show how elasticity and pass-through affect the cafe's pricing decision.

## Sensitivity and Robustness Checks

The model will test:

1. Elasticity from **-0.5 to -4.0** in steps of 0.1.
2. Pass-through from **0% to 100%** in steps of 10%.
3. Food-attach rates of **25%, 40%, and 50%**.
4. Food-cost rates of **35%, 40%, and 45%**.
5. Linear demand and constant-elasticity demand.
6. A wider price-search range if the best result is at a boundary.
7. The four reference pricing strategies.

## Limitations

1. International Arabica prices do not include all costs of bringing coffee to Hawaii, such as freight and local distribution.
2. The elasticity values come from different coffee markets and model specifications and do not directly measure customers at one small Hawaii cafe.
3. The elasticity faced by one cafe may change when nearby cafes change their prices.
4. The $12/lb roasted-coffee benchmark comes from a 2026 Bellwether Coffee article, so it may be higher than the actual wholesale price in 2023.
5. The Bellwether price is an industry estimate rather than academic evidence.
6. The $5 food price is based on Square menu-price data from another U.S. city, not Hawaii.
7. The 40% food-cost rate is an industry benchmark rather than data from one Hawaii cafe.
8. The 40% food-attach rate comes from Starbucks and may not represent a small independent cafe.
9. The cup and lid prices are current Staples prices and may change over time.
10. The constant-elasticity model may not have a finite optimal price in some cases.
11. The model is a simulation and does not directly measure actual customer behavior.

## Outputs

The model reports the following results:

1. **Coffee Bean Cost**
   - `GREEN_PRICE_2023`
   - `GREEN_PRICE_2025`
   - `BASE_BEAN_COST_PER_CUP`
   - `BEAN_COST_INCREASE_PER_CUP`
   - `NEW_BEAN_COST_PER_CUP`
   - `MONTHLY_BEAN_COST`

2. **Optimal Coffee Price**
   - `OPTIMAL_PRICE_CHANGE_PCT`
   - `OPTIMAL_COFFEE_PRICE`
   - `OPTIMAL_MONTHLY_QTY`

3. **Monthly Revenue**
   - `COFFEE_REVENUE`
   - `FOOD_REVENUE`
   - `TOTAL_REVENUE`

4. **Monthly Variable Costs**
   - Coffee bean cost
   - Packaging cost
   - Food variable cost
   - Payment processing fees

5. **Monthly Contribution Profit**
   - `MONTHLY_CONTRIBUTION_PROFIT`

6. **Reference Strategy Results**
   - No price increase
   - Cost-based increase
   - 5% price increase
   - 10% price increase

7. **Hypothesis Results**
   - Hypothesis 1: Whether the bean-cost increase at 100% pass-through is below or above $0.50 per cup.
   - Hypothesis 2: Range of optimal price changes when elasticity changes from -0.5 to -4.0 while pass-through is fixed at 100%.
   - Hypothesis 2 comparison: Range of optimal price changes when pass-through changes from 0% to 100% while elasticity is fixed at -2.0.
   - The two ranges will be compared in percentage points.

8. **Sensitivity Results**
   - Elasticity results
   - Pass-through results
   - Food-attach results
   - Food-cost results
   - Linear-demand and constant-elasticity results

## Audit Findings

The final model will document the following checks:

1. **Source Check**: Confirm all outside values with the linked public sources.
2. **World Bank Check**: Recalculate the 2023 and 2025 annual averages from the 12 monthly observations.
3. **Bean Cost Check**: Confirm that the green-coffee price increase correctly moves through the pass-through formula.
4. **Packaging Check**: Confirm that the cup and lid costs total $0.22 per coffee and are included in monthly contribution profit.
5. **Demand Check**: Confirm that all linear demand curves pass through the $5.00 / 2,000-cup baseline.
6. **Boundary Check**: Expand the price-search range if the best result is at a boundary.
7. **Constant-Elasticity Check**: Record **no finite optimum** when needed.
8. **Figure Check**: Confirm that Figure 2 includes 0%, 50%, and 100% pass-through lines.
9. **Food Sensitivity Check**: Compare food-attach and food-cost assumptions.
10. **AI Source Verification**: Check AI-suggested values with the public source before using them.

## Audit Results (2026-11-27)

* Validation Rules: All checks on the Checks sheet returned TRUE, so the main formulas and model checks passed.

* Expanded Search Range: The original -20% to +40% search had some optimal results at the boundary. Following the Boundary Rule, I expanded the range to -50% to +60%, and all linear-demand scenarios were inside the range after the expansion.

* Constant-Elasticity Demand: I expected no finite optimum mainly when elasticity was -1 or higher. In the actual model, all tested elasticity values from -0.5 to -4.0 produced no finite optimum under the constant-elasticity demand model.

* Manual Verification: I completed three additional checks. First, my manual calculation matched the model result of $10,083.97. Second, I changed CARD_RATE and CUP_COST and confirmed that the checks reacted and the profit change matched my manual calculation, then I returned the inputs to their original values. Third, I confirmed that the values in Figure 1 and Figure 2 matched the values in the model tables.

* World Bank Check: My calculated annual averages were $4.5408/kg for 2023 and $8.47/kg for 2025. These match the Pink Sheet annual values of approximately $4.54/kg and $8.47/kg.

* Solver Check: I used GRG Nonlinear with starting points of -20% and +20%. For the four linear-demand scenarios, the Solver results were within 0.5 percentage points of the grid-search results, with a maximum difference of 0.48 percentage points, and both starting points gave the same results. For constant-elasticity demand, Solver stopped at the lower bound of -50%, which supports the finding that the tested range did not contain a finite optimum.

* Floating-Point Error: The 0% rows contain very small floating-point differences, but these differences are too small to affect the model results or conclusions.


## Sources

- Hawaii Department of Agriculture. (2024). [*Final Report on the Economic Study on Changes in Coffee Labeling Law*](https://dab.hawaii.gov/wp-content/uploads/2023/11/Act-222-SLH-2022-FINAL-Report-on-Econ-Study-on-Changes-in-Coffee-Labeling-Law.pdf).
- Franca, A. S., Oliveira, L. S., Oliveira, R. C. S., Agresti, P. C. M., & Augusti, R. (2009). [*A preliminary evaluation of the effect of processing temperature on coffee roasting degree assessment*](https://www.academia.edu/55160596/A_preliminary_evaluation_of_the_effect_of_processing_temperature_on_coffee_roasting_degree_assessment). *Journal of Food Engineering, 92*(3), 345–352.
- Koerner, J. (2002). [*The Dark Side of Coffee: Price War in the German Market for Roasted Coffee*](https://macau.uni-kiel.de/servlets/MCRFileNodeServlet/macau_derivate_00006476/FE0204.pdf). University of Kiel.
- Nakamura, E., & Zerom, D. (2009). [*Accounting for incomplete pass-through*](https://www.nber.org/system/files/working_papers/w15255/w15255.pdf) (NBER Working Paper No. 15255). National Bureau of Economic Research.
- Specialty Coffee Association. (2017). [*SCA Minimum Certification Requirements for Coffee Brewers*](https://sca.coffee/s/2017-SCA-CHB-Program-Requirements-ba6g.pdf).
- World Bank. (2026). [*Commodity Price Data (The Pink Sheet): Coffee, Arabica*](https://thedocs.worldbank.org/en/doc/74e8be41ceb20fa0da750cda2f6b9e4e-0050012026/related/CMO-Pink-Sheet-June-2026.pdf).
- Bellwether Coffee. (2026). [*What wholesale coffee really costs per pound*](https://bellwethercoffee.com/blog/cost-of-wholesale-coffee-per-pound).
- QuickStok. (n.d.). [*Food cost percentage calculator for cafes*](https://www.quickstok.ai/tools/food-cost-calculator).
- Square. (n.d.-a). [*Bakery and coffee shop prices in Los Angeles*](https://squareup.com/us/en/menu-pricing/bakery-and-coffee-shop-prices-in-los-angeles).
- Square. (n.d.-b). [*Square processing fees*](https://squareup.com/help/us/en/article/5068-what-are-square-s-fees).
- Staples. (n.d.-a). [*Perk 12 oz paper hot cups*](https://www.staples.com/perk-paper-hot-cup-12-oz-white-blue-500-carton-pk54367ct/product_24375255).
- Staples. (n.d.-b). [*Perk plastic hot cup lids*](https://www.staples.com/perk-plastic-hot-cup-lid-10-12-16-oz-white-500-carton-pk54369ct/product_24375257).
- Starbucks Corporation. (2023). [*Q3 FY2023 earnings call transcript*](https://s203.q4cdn.com/326826266/files/doc_events/2023/08/1/SBUXQ32023EarningsCall.pdf).
