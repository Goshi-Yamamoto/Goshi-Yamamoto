---
type: brief
engagement: research-paper
capability: elasticity-analysis
date: 2026-11-26
status: committed
---

# Research Brief

**Research Topic: The Increase in Arabica Coffee Prices from 2023 to 2025 and Pricing Decisions for Small Cafes in Hawaii**

## The Problem
International Arabica green coffee prices increased from 2023 to 2025. This may have increased coddee-bean for small cafes in Hawaii that use Arabica coffee beans.

Cafe owners may consider raising their selling prices to respond to higher costs. However, if customers buy less coffee because of the higher price, the price increase may reduce profit instead. Customers are also affected because they must decide whether to continue buying coffee at the higher price or choose another cafe.

I am interested in how much a small cafe should change its price to maximize monthly contribution profit when its costs increase.

In this research, I will estimate how the increase in green coffee bean prices from 2023 to 2025 affects the cost per cup. I will also search for the optimal price change and examine how customer price elasticity and the coffee-cost pass-through rate affect that result. I will also compare different pricing strategies under different levels of customer price elasticity. Finally, I will make a pricing recommendation for small cafe owners in Hawaii.

## What I Am Assuming
### Cafe and Product
I assume a small cafe in Hawaii sells a 12 oz hot black coffee made with imported Arabica beans. Hawaiian-grown coffee, such as Kona coffee, is not included because its pricing is different.

The base selling price is assumed to be **$5.00 per cup**, and the cafe sells **2,000 cups per month** at this price.

### Pricing Strategy
The model will search for the price change that produces the highest monthly contribution profit. I will test price changes in 1 percentage-point steps, including both price decreases and price increases.

If the optimal price is found at the upper or lower end of the search range, I will expand the range and run the model again. This helps prevent the search range itself from deciding the result.
I will also keep four simple strategies as reference points

* No price increase
* An increase equal to the cost increase
* A 5% increase
* A 10% increase

These strategies are useful because they represent simple choices that a cafe owner may realistically consider.

### Demand and Quantity
The main model will use a linear demand curve that passes through the base point of $5.00 and 2,000 cups per month.

The elasticity values in this research represent elasticity at the base price of $5.00, not at every price on the demand curve. Because the demand curve is linear, elasticity changes as the price changes.

I use linear demand because it allows the model to find a finite optimal price. I will also use a constant-elasticity demand model as a robustness check in the appendix.

### Customer Price Elasticity
I will test customer price elasticity over a range from approximately -0.5 to -4.0. I will focus on four main scenarios:

* -0.5: A relatively inelastic reference case. Table 3 of Akiyama and Varangis (1990) reports price elasticities around this level for several coffee-importing countries, including -0.54 for Austria, -0.51 for the United Kingdom, -0.49 for Greece, and -0.46 for the United States.
* -1.0: A middle reference case. Koerner (2002) reports average own-price elasticities for roasted coffee in Germany ranging from about -0.59 to -1.12 across different model specifications.
* -2.0: A more elastic reference case. In Table 5 of Nakamura and Zerom (2010), the OLS2 specification reports a median price elasticity of 1.96 in absolute value, which is close to -2.0 when written as a demand elasticity.
* -3.5: A high-elasticity reference case. In the random-coefficients specification in Table 5 of Nakamura and Zerom (2010), the median price elasticity is 3.46 in absolute value, which is close to -3.5.

The 1.96 and 3.46 values come from different model specifications in the same study, so I use them as reference estimates rather than as direct measurements of two different real-world cafe situations.

These studies also do not directly measure customers at a small cafe in Hawaii. Therefore, the four elasticity values are used as economic scenarios rather than exact estimates.

The elasticity faced by one cafe may also depend on competitor behavior. In a monopolistically competitive market, if only one cafe raises its price, customers may switch to nearby competitors, making the cafe's residual demand more elastic. If nearby cafes also raise their prices, customers have fewer cheaper substitutes, so demand may become less elastic.

### Coffee Cost per Cup
I will use approximately 19.5 grams of roasted coffee per 12 oz cup. This is based on the Specialty Coffee Association (SCA, 2017) brewing ratio of about 55 grams per liter.

For roasting weight loss, I will use 15% as the base value, based on Franca et al. (2009) for medium roast coffee.

For green coffee prices, I will use the World Bank Pink Sheet monthly Coffee, Arabica price series. I will calculate the 2023 and 2025 annual averages myself by averaging the 12 monthly observations for each year.

I will test coffee-cost pass-through rates from 0% to 100%. The 50% and 100% cases will remain useful reference points.
International green coffee prices do not include all costs faced by a small cafe in Hawaii, such as freight and local distribution costs. I will identify this as a limitation.

### Profit Measure

To compare pricing strategies, I will use monthly contribution profit.
The calculation will include variable costs such as:

* Coffee beans
* Cups and other packaging
* Payment processing fees
* Food contribution profit connected with each customer

Payment processing fees will be treated as a percentage of sales, so the fee will change when the selling price changes.

I assume that one customer purchases one coffee in the main model. Food is treated as a complementary product because a customer who stops buying coffee may also stop buying food.

I will use one assumed food contribution profit per customer in the main model and test different values in the sensitivity analysis.

Fixed costs, such as rent and fixed labor costs, are assumed to remain unchanged between pricing strategies.

## Hypothesis

### Hypothesis 1: Size of the Cost Increase

I expect that the increase in international Arabica green coffee bean prices from 2023 to 2025 will have a relatively small effect on the ingredient cost per cup compared with the **$5.00 selling price**.

Even under the **100% pass-through scenario**, I expect the cost increase to be **less than $0.50 per cup**.

### Hypothesis 2: Factors Affecting the Optimal Price

I expect that differences in customer price elasticity will have a greater effect on the price increase that maximizes monthly contribution profit than differences in the coffee bean cost pass-through rate.

More specifically, I expect changes in elasticity from approximately -0.5 to -4.0 to produce a larger change in the optimal price than changes in the pass-through rate from 0% to 100%.

## How I Would Know I Was Wrong

### Hypothesis 1

I will calculate the increase in ingredient cost per cup using the 2023 and 2025 annual average Arabica green coffee bean prices, 19.5 grams of roasted coffee per cup, and a 15% roasting weight loss.

If the estimated increase in ingredient cost is **$0.50 or more per cup** under the 100% pass-through scenario, I will revise my expectation that the impact is small.

I use **$0.50** as the decision point because it is equal to **10% of the $5.00 base selling price**.

### Hypothesis 2

I will compare the change in the optimal price under two conditions.

First, I will change elasticity from approximately -0.5 to -4.0 while holding the coffee-cost pass-through rate at 100%.

Second, I will change the pass-through rate from 0% to 100% while holding elasticity at -2.0.

I will compare the difference between the highest and lowest optimal price changes in percentage points. Because the model searches in 1 percentage-point steps, differences smaller than one percentage point cannot be identified separately.

If changing elasticity causes a smaller or equal change in the optimal price compared with changing the pass-through rate, I will revise my expectation that elasticity is the more important factor.

## Limitations

This research is based on a simulation, so the results depend on the assumptions used in the model.

First, international green coffee prices do not include all costs of bringing coffee to Hawaii, such as freight and local distribution costs.

Second, the elasticity values do not come directly from customers of a small Hawaii cafe. The estimates from Akiyama and Varangis (1990), Koerner (2002), and Nakamura and Zerom (2010) come from different coffee markets and model specifications. The elasticity faced by one cafe may also change depending on the pricing decisions of nearby competitors.

Third, the food contribution profit is an assumed value rather than observed data from a specific cafe. I will test different values in the sensitivity analysis.

Finally, the results show what happens under the assumptions of the model. They do not directly prove how actual cafe customers will respond to price changes.

## References
* Akiyama, T., & Varangis, P. N. (1990). The Impact of the International Coffee Agreement on Producing Countries. The World Bank Economic Review, 4(2), 157–173.
* Franca, A. S., Oliveira, L. S., Oliveira, R. C. S., Agresti, P. C. M., & Augusti, R. (2009). A preliminary evaluation of the effect of processing temperature on coffee roasting degree assessment. Journal of Food Engineering, 92(3), 345–352.
* Koerner, J. (2002). The Dark Side of Coffee: Price War in the German Market for Roasted Coffee. University of Kiel.
* Nakamura, E., & Zerom, D. (2010). Accounting for Incomplete Pass-Through. Review of Economic Studies, 77(3), 1192–1230.
* Specialty Coffee Association. (2017). SCA Minimum Certification Requirements for Coffee Brewers.
* World Bank. Commodity Price Data (The Pink Sheet): Coffee, Arabica.
