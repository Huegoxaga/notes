# Quantitative Analysis

## Time Value of Money

- The time value of money (TVM) is the concept that money you have now is worth more than the identical sum in the future due to its potential earning capacity, the time value can be:
  - `Present Value (PV)` is the current value before making the investment
  - `Future Value (FV)` is the future value after making the investment
- `Interest` is the difference between the amount of money lent and the amount of money later repaid
- The `Interest Rate` is the amount charged, expressed as a percentage of the principal, by a lender to a borrower for the use of assets

### Components of Interest Rate

- The interest rate is consisted of the following components:
  - Risk Premium Components - this part compensate the risk for lending, it includes:
    - Default Risk Premium - it reflects the borrower's financial status
    - Liquidity Premium - it reflects the demand of the debt covenants(which is the debt agreement or financial contracts for loans and bonds) in the market, or the cost of selling it
    - Maturity Risk Premium - the longer the term, the higher the risk. The lender needs more courage to lend out for a longer period
  - Risk-free Components(Nominal Risk-free Rate) - this part compensate the losses of the lender for not having the money on hand, it equals the minimum returns if the lender use the money to make any investment elsewhere. In the U.S, the interest rate of Treasury Bill (T-Bill, a short-term U.S. government debt ) is used as a benchmark for this component, it includes:
    - Inflation Premium - it guarantees the purchasing power of the money after the borrower returns the money, it matches the expect inflation rate
    - Real Risk-free Rate - this is the incentives for the lender to lend the money
- The interest rate can be called differently based on different interpretation
  - The `Required Rate of Return` for the lenders or investors
  - The interest rate can be seen as a `Discounted Rate` by discounting the future value of the total return
  - It can be treated as the `Opportunity Cost` of the current consumption of the money if not lending it

### Interest Calculation

- This base unit of time over which an interest rate is calculated is called the interest period
  - If the time period of an interest rate is not spcified, it is an annual interest rate
- `Nominal interest rate` is the conventional method of stating the annual interest rate regardless how it is compounded, i.e. monthly, annually
- `Effective interest rate` is the actual annual interest rate after compounding its sub-compounding periods
  - The more frequent the rate of compounding the higher the interest the investor can get
- `Simple Interest` only uses the original pricipal to calculate interest for the next time period
- `Compound Interest` - Compound interest will include the interest earned from previous time period to calculate the interest for the next time period
  - The interest period used for compounding is called the compounding period
  - When compounding period is a sub-period, convert the interest rate to the sub-period first
    - e.g. If annual interest rate is `12%`, monthly interest rate is `1%`
  - If interest `r` for a certain time period is divided from annual interest `R` by `n`, if there are `n` time periods each year
  - $$I_c=P(1+i)^N-P$$ where `i` is the interest occurs during the time period and `N` is the total number of time periods
  - Effective interest rate - `EAR=((1+r)^N)-1`
- `Continuous Compound` has the compound frequency set to infinite
  - Then, `FV = PV*e^(rN)` and `EAR=e^r-1` where `r` is the stated compound rate and `N` is the stated number of time period for the stated rate
  - Continuous compound yields the highest interest one can get from compounding, given the same interest rate

### Depreciation Calculation

- Book value = Cost basis – Depreciation charges made to date
- Straight-Line Depreciation (SLD)
  - Goods depreciate at a constant rate
  - Annual Depreciation Charge = $$d_t=\frac{(B-S)}{N}$$, where B = cost basis, S = salvage value, N = depreciable life
  - Salvage value is the value of a good when its service life is reached
- Declining-Balance Depreciation (DBD)
  - The declining balance method (DBD) of depreciation models the loss in value of an asset in a period as a constant proportion of the asset’s current value
  - Book Value at the end of period n using DBD equals $$P(1-d)^n$$, where `P` is the initial book value, `d` is the constant depreciation percentage, `n` is the number of periods

### Cash Flow Analysis

- A `Cash Flow` means a certain amount of money disbursed or receipted, usually used when making investment
- A `Cash Flow Diagram` is a graph that summarizes the timing and magnitude of cash flows as they occur over time
  - the graph’s vertical axis is not shown explicitly
    - positive cash flows is represented by arrow pointing upwards and vice versa
  - The horizontal (X) axis represents time
    - Now is time `0`
    - `N` years from now is the end of period `N` and the beginning of period `(N + 1)`
  - When cash flows occur in between time periods, move it to the next period
- To simplify the cash flow analysis, models are created for estimation:
  - `Discrete Models` - model assumes that all cash flows and all compounding of cash flows occur at the ends of conventionally defined periods, such as months or years.
  - `Continuous Models` - models that assume cash flows and their compounding occur continuously over time
- The principle of discrete compounding requires several assumptions:
  1. Compounding periods are of equal length
  2. Each disbursement and receipt occurs at the end of a period. A payment at time 0 can be considered to occur at the end of period minus 1
  3. Annuities and gradients coincide with the ends of sequential periods
- The math function or factor used to convert the mathematical equivalence between the present value and future value of cash flows are referred as the `Compound Interest Factors`
  - Various types of cash flows have different factors, shown as below
  - Since all factors depend on the interest rate for each period and the number of period only, the compound interest factors table can be used as a quick reference for getting the value of each type of factor

#### Types of Cash Flow

- A single cashflow - a lump sum of money, a single disbursement or receipt, it can be measured by:
  - `Compound Amount Factor`, denoted by `(F/P,i,N)`, gives the future amount, `F`, that is equivalent to a present amount, `P`, when the interest rate is `i` and the number of periods is `N`
    - It equals $$(1+i)^N$$
  - `Present Worth Factor`, denoted by `(P/F,i,N)`, gives the present amount, `P`, that is equivalent to a future amount, `F`, when the interest rate is `i` and the number of periods is `N`
    - It is the reciprocal of the compound amount factor
    - It equals $$\frac{1}{(1+i)^N}$$
- Regular cashflows, also known as annuity - continous contribution, same amount every time, it can be measured by:
  - `Sinking Fund Factor`, denoted by `(A/F,i,N)`, gives the size, `A`, of a repeated small receipt or disbursement that is equivalent to a large future amount, `F`, if the interest rate is `i` and the number of periods is `N`
    - It equals $$\frac{i}{(1+i)^N-1}$$
    - A sinking fund is an interest-bearing account into which regular deposits are made in order to accumulate some amount
  - `Uniform Series Compound Amount Factor`, denoted by `(F/A,i,N)`, gives the future value, `F`, that is equivalent to a series of equal-sized receipts or disbursements, `A`, when the interest rate is `i` and the number of periods is `N`
    - It is the reciprocal of the sinking fund factor
    - It equals $$\frac{(1+i)^N-1}{i}$$
  - `Capital Recovery Factor`, denoted by `(A/P,i,N)`, gives the value, `A`, of the equal periodic payments or receipts that are equivalent to a present amount, `P`, when the interest rate is `i` and the number of periods is `N`
    - It can be easily derived from the sinking fund factor and the compound amount factor
    - It equals $$\frac{i(1+i)^N}{(1+i)^N-1}$$
  - `Series Present Worth Factor`, denoted by `(P/A,i,N)`, gives the present amount, `P`, that is equivalent to an annuity with disbursements or receipts in the amount, `A`, where the interest rate is `i` and the number of periods is `N`
    - It is the reciprocal of the capital recovery factor
    - It equals $$\frac{(1+i)^N-1}{i(1+i)^N}$$
    - `Capitalized Value` of a series can be obtained by getting the limit of the number of periods `N` to infinity in the in the series present worth factor calculation
  - Time values of regular cashflows can be calculatd by stacking each individual single cashflow with different number of time period together, the calculation can be simplified using the formula for the sum of a geometric series
    - Regular cashflows calculation can have a end mode(default for most calculators) which means the cashflow is added at the end of each time period
    - Regular cashflows calculation can have a begin mode which means the cashflow is added at the beginning of each time period
    - Begin mode will compound the interest one more time at the end
  - An annuity is a contract between you and an insurance company in which you make a lump-sum payment or series of payments and, in return, receive regular cashflows, beginning either immediately or at some point in the future. it can be further categorized as:
    - Annuity Due - regular cashflows, begin mode
    - Ordinary Annuities - regular cashflows, end mode
    - Perpetuities - regular cashflows, end mode, infinite number of time periods
      - The time value for perpetuities equals payment amount divided by the interest rate for the payment time period
- `Arithmetic Gradient Series` - a series of receipts or disbursements that starts at zero at the end of the first period and then increases by a constant amount from period to period
  - `Arithmetic Gradient to Annuity Conversion Factor`, denoted by `(A/G,i,N)`, gives the value of an annuity, `A`, that is equivalent to an arithmetic gradient series where the constant increase in receipts or disbursements is `G` per period, the interest rate is `i`, and the number of periods is `N`
    - It equals $$\frac{1}{i}-\frac{N}{(1+i)^N-1}$$
    - There is often a base annuity `A'` associated with a gradient. Hence, the total cash flow equals `A'+G(A/G,i,N)`
- `Geometric Gradient Series` - a series of cash flows that increase or decrease by a constant percentage each period
  - `Geometric Gradient to Present Worth Conversion Factor`, denoted by `(P/A,g,i,N)`, gives the present worth, `P`, that is equivalent to a geometric gradient series where the base receipt or disbursement is `A`, and where the rate of growth is `g`, the interest rate is `i`, and the number of periods is `N`
    - It equals $$\frac{(P/A,i^{\circ},N)}{1+g}$$ or $$\left(\frac{(1+i^{\circ})^N-1}{i^{\circ}(1+i^{\circ})^N}\right)\frac{1}{1+g}$$ where $$i^{\circ}=\frac{1+i}{1+g}-1$$
- Uneven Cash Flows (Non-Standard Annuities and Gradients) - continous contribution, uneven amount every time. There are three methods for dealing with this situation:
  1. Treat each cash flow in the annuity or gradient individually. This is most useful when the annuity or gradient series is not large.
  2. Convert the non-standard annuity or gradient to standard form by changing the compounding period
  3. Convert the non-standard annuity to standard form by finding an equivalent standard annuity for the compounding period. This method cannot be used for gradients
- When calculating cashflow it's critical to determine the entity(e.g. bank or investor) and the outflows and inflows of the cashflows for this entity, use negative sign for outflows and positive sign for inflows
- Discounted Cashflow is a method to discount all cashflows from its future value to its present value by compounded the discounted rate(interest rate)
  - Net Present Value(NPV) is the sum of the discounted present value for all inflows and outflows
  - The discounted rate used to make the NPV equals zero is called the Internal Rate of Return(IRR)
  - A investment will generates profit if the NPV is positive, the higher the NPV the more profit a investor can gain from it
  - IRR is a reference for the rate of return, it can be used to see it the rate of return is desirable
  - The Money Weighed Rate of Return(MWRR) of a investment portfolio is used to see the return rate of this investment, the calculation is the same as calculating `IRR`
  - The Holding Period Return(HPR) is a way to evaluate the performance of a portfolio for each holding period(time period), `HPR = EndValue+Cashflows/BeginValue - 1`
    - Begin Values - The balance of the investment account at the beginning of a certain time period
    - End Values - The balance of the investment account at the end of a certain time period including any payouts
    - Cashflows - any payouts from the bank
  - Time Weighted Rate of Return(TWRR) is the preferred way to evaluate the investment performance, calculated by adding all HPR values by 1(change factor) and find `Nth` root of their product where `N` is the number of HPR values or time period, lastly substruct the final result by `1`
    - It is the geometric mean of the change factors of all HPR values
  - For all of the above calculation for return, a nagative HPR means losses, and a positive HPR means gains

# Statistics Concepts

- Types of scales for statistic meaturement
  - Nominal Scale - A property of the data is categorized by name
  - Ordinal Scale - A property of the data is categorized by rank
  - Interval Scale - Data is placed on to a uniformed scale without a true zero on the scale
    - a true zero represent the absent of a measurable property
  - Ratio Scale - Data is placed on to a uniformed scale with a true zero on the scale
- Statistics Terminology
  - `Observation` - Each data entry
  - `Population` - Set of all observation
  - `Sample` - Subset of the population
  - `Parameter` - Measure used to describe a characteristic of a population, e.g. `std. dev.`
  - `Descriptive Statistics` - consolidating a mass of data into useful information
  - `Inferential Statistics` - making estimates about a population from a sample, when the entire population is not available to measure or too big to get
    - `Sample Statistic` - a piece of information one can get from a fraction of a population
- Statistical Analysis Tools
  - `Frequency Distribution`(Histogram) - represents the likelyhood of a data to fall into a certain range
    - Steps to draw a frequency distribution:
      1.  Set the interval by dividing the differece of the max and min into a suitable(from 5 to 10) number of section
          - Use whole numbers for interval boundaries
      2.  Count the number of observation for each interval, and draw the count as bar graph
    - `Frequency Polygon` - connects the top midpoint of the histogram's bar
    - `Absolute Frequency Distribution` - the y-axis is the data count
    - `Relative Frequency Distribution` - the y-axis is the `data count / total data count`
    - `Accumulative Frequency Distribution` - Suming the y value from left to right along the x-axis
      - the right most bar has `100%`

# Economics

## Demand and Supply Analysis

- Target of the demand and supply analysis can be either the market or the firm
- The demand curve of the market is downward sloping and the supply curve is upward sloping and the curve slopes upwards, the intersaction point represent the market price and demand
- The demand curve of the market depends on the types of market it is in, and the supply curve is the `MC` curve above the shutdown level
- One demand or supply curve in a graph can only depict the market condition in a short run, in a long run the curve can shift in all directions accordingly, e.g.:
  - When more firms are joining the market in a long run the supply curve will move down, which is a result of supply increase and price drop, and vice versa
  - when there is an increase in demand, market demand curve shifts upwards and to the right, makes the market price higher and vice versa

### Demand Analysis

- Demand Curve has quantity demanded on the x-axis and the price of the item on the y-axis
  - Quantity demanded represents the comsumer's intention to buy
- The demand function - quantity demanded equals a constant plus the Own-Price coefficient times Own-Price value plus Cross-price elasticity coeffiecient times Cross-price value plus income coeffiecient times income value
  - The quantity demanded is associated with a period, e.g. the demand for 15 apples in a month
  - The quantity demanded is associated wiath a specific group of consumers (e.g. low-income)
- For all the following elasticity, when the absolute value is above 1, it is elastic. When it is less than 1, it is in elastic
  - A high elasticity will greatly effect the demand
- The law of demand - conditional on all else being equal, as the price of a good increases, quantity demanded will decrease; conversely, as the price of a good decreases, quantity demanded will increase

#### Own-Price Elasticity of Demand

- Own-Price Elasticity of Demand is the percentage change in quantity demanded when the price changes by 1 percent
  - it is not equal to the slope of a demand curve
  - it depends on the current price or demand and it is not constant
- Own-price coefficient multiple by the current own-price value and divided by the total quantity demand will get the Own-price elasticity
  - The reciprocal of the elasticity coefficient is the slope of the demand curve
- When the Demand Curve is downward sloping the Own-Price Elasticity is negative, and the law of demand applies
  - There is a region in the demand curve that the quantity demanded is very responsive to a change in price in terms of the changes in percentage, the demand is elastic,
    - the absolute value of elasticity is greater than 1
    - When the demand curve is fully horizontal, it is called perfectly elastic demand where the elasticity is infinite
  - There is a region in the demand curve that the quantity demanded is not very responsive to a change in price in terms of the changes in percentage, the demand is inelastic
    - The absolute value of elasticity is less than 1
    - When the demand curve is fully vertical. it is called perfectly inelastic demand where the elasticity is equal to zero
  - There's this unique point where the elasticity is minus 1, it is called the unitary elasticity point
    - the total revenue is maximized at this point
    - it's the dividing point between the elastic region and inelastic region of the demand curve
      - an increase in price moves us to the elastic region of the curve
      - a decrease in price from this point moves us into the inelastic region
- Factors that effects the slope of the demand and price
  - when goods have many other close substitutes, it will be elastic
  - If the the price of the goods is more expensive compared to the comsumer's income it will be more elastic
  - The elasticity of demand tends to be greater in the long run, as consumers can take time to make adjustments to their consumption habits
  - Essential goods tend to be more inelastic

#### Cross-price Elasticity of Demand

- the percentage change in quantity demanded for every percentage change in price of the related good
- the cross price elasticity is positive when the related good is a substitute
- the cross price elasticity is negative when the related good is a compliment
- Cross-price coefficient multiple by the cross-price value and divided by the total quantity demand will return the cross-price elasticity
- When the price of a goods drops while all its substitutes' price keep the same, the demand for that goods will increase this is called a positive substitute effect

#### Income Elasticity of Demand

- the percentage change in quantity, demanded for every percentage change in income level
- Normal goods are those in which the demand increases with consumer income levels and vice versa, the income elasticity is therefore positive for normal goods
- Inferior goods(goods that save budget) are those for which the demand decreases with consumer income levels, the income elasticity is therefore negative for inferior goods.
- Income coefficient multiple by the income value and divided by the total quantity demand will return the income elasticity
- When there is a positive change in real income (purchasing power) due to prices drop on some goods, the demand for normal goods will increase and it is called a positive income effect, inferior goods will result in a negative income effect
- For an inferior good, when the negative income effect outweights the positive substitute effect, it is called a Giffen good, the demand curve of this good will be an upward sloping straight line
  - It is a exception to the law of demand
  - only in theory, there are some rare instances where this has turned out to be true
  - another exception where the demand curve is upward sloping is the Veblen good for which a higher price makes the goods more desirable. This is usually the case for some luxury goods like Hermes bags where the higher price conveys higher status to the owners. It only applies to a select group of people who can afford it and there has to be a limit to it

### Supply Analysis

#### The Law of Diminishing Marginal Returns

- In order to supply goods the factors of production are required
  - Land - the physical space you own or rent
  - Labour (L) - all workers from unskilled to top management
  - Capital (K) sometimes called plant and equipment
    - this does not include financial capital
  - Materials - refers to the inputs that make the production possible
  - Economists typically concentrate on just two of these, labor (L) and physical capital (K)
- The total product function
  - In a short run, some factors of production are fixed, like capital. The total production should be a function of the labor
  - In the long run however all factors of production are variable. The total production should be a function of the labor and capital input
- Total production is simply the total output in a period
- Average production is the total output per unit of input
- Marginal product is the amount of additional product resulting from using one more unit of input
- The diminishing marginal productivity of labor where in the short run the additional output from each additional worker decreases progressively, it happens in three stages
  - when the labor input is smaller marginal productivity is increasing the slope of the output curve increases at this stage
  - when the labor input gets larger. The marginal productivity is decreasing the slope of the output curve decreases at this stage
  - and for some companies marginal productivity can become zero or even negative, the output curve hits a maximum and starts to dip beyond that

#### Breakeven and Shutdown Analysis

- Fixed costs cannot be changed in the short run, e.g. rental lease
  - average fixed cost (AFC) - total fixed cost devided by the number of output
    - when plot the average fixed cost against the quantity produced, it will show a downward sloping line
- Variable costs vary according to the level of production, e.g. labour cost
  - average variable cost (AVC) - total variable cost devided by the number of output
    - because of diminishing marginal productivity of labor. The average variable cost starts increasing after a certain point
- Total cost equals fixed cost plus variable costs
  - average total cost (ATC) - total cost divide by the number of output
    - The ATC graph looks similar to the AVC, shift up by the AFC
- Marginal cost is the change in total cost per unit change in output quantity
  - it is upward sloping after a certain point due to diminishing marginal productivity
  - marginal cost curve has the actual cost of that additional output on the y-axis
  - marginal cost curve intersects the AVC and ATC curves at their minimum
- Revenue - price times the quantity sold
- The average profit is the difference between the marginal cost and average total cost
- The total economic profit is the average profit multiply by quantity
- The toal economic loss happens when the economic profit is a negative value
- Economic costs are based on opportunity cost which is measured by determining of resources next best opportunity
  - The profit that is gained from this opportunity is called the normal return
  - Not be able to have the full normal return will occur an opportunity cost
  - in economic terms the total economic cost includes the full normal market return on all the resources utilized in the business
  - The actual earnings for a firm is called the accounting profit
  - So when we say a firm does not earn economic profit it doesn't mean that the firm makes no profit (accounting profit) at all. Rather it means that the firm is just making normal profit based on its opportunity costs
- The profit maximizing point will then be the point where the marginal revenue is equal to the marginal cost, because it is the highest point where `MR > MC` is satisfied
- This minimum point where the `ATC` is equal to the `MC` is the breakeven level, when price goes above this level the business makes a profit, when price goes below this level the business will have a loss
- When the price is below the breakeven level and falls in between the lowest point of `ATC` and `AVC` cost, the profit maximizing point is also in between the `ATC` and `AVC` cost, the firm will be running at loss but it still has revenue to cover the `AVC` and part of the `AFC`
  - In this case, continue running the business in short run can minimize loss of the fixed cost, since there is no refund for fixed costs
- This minimum point where the `AVC` is equal to the `MC` is the shutdown level, When price goes below the `AVC` cost, the `AVC` cannot be covered and there is no point to keep the business in both short and long run

#### Economies and Diseconomies of Scale

- In a long run the `AVC` for short run can shift to the right because the output product quantity is increased due the increase in productivity after business growed by investing
- The `AVC` curve might even shift to a lower position due to the the effect called the `Economies of Scale`, Economies of scale occur if the cost per unit of production falls as the firm increases its scale, it results from factors such as:
  - labour specialization
  - mass production
  - investment in more efficient equipment and technology
  - being able to lower input prices with suppliers as its bargaining power increases with scale
- `Economies of Scale` have to hit a limit somewhere. When scaling up does not result in any economies of scale. It is called the `Constant Returns to Scale`
- `Diseconomies of Scale` happens when scaling up even further results in an increase in average cost, due to:
  - inefficiencies from bureaucracy of larger firms
  - problems with motivating a larger workforce
  - greater barriers to innovation and entrepreneurial activity
- if we draw a line that connects all the minimums of the short run `ATC` (`SR ATC`) curves we get the long run `ATC` curve (`LR ATC`) of the firm
  - `Minimum Efficient Scale` - the lowest point on the `LR ATC` corresponds to the scale at which the average total cost of production is minimized

## Market Structures

- Market Structures are determined by examining the following five characteristics of the industry

| Characteristics                 | Perfect Competition   | Monopolistic Competition                  | Oligopoly                                           | Monopoly             |
| ------------------------------- | --------------------- | ----------------------------------------- | --------------------------------------------------- | -------------------- |
| The number and sizes of sellers | Many firms            | Many firms                                | Few firms                                           | Single seller        |
| Barriers to entry or exit       | Very Low              | Very Low                                  | High(economies of scale lead to big size)           | Very high            |
| Products differentiation        | Identical Products    | Different in quality, features, marketing | good substitutes or differentiated                  | No close substitutes |
| The nature of competition       | Compete on price only | Price and product difference              | Price and product difference                        | Little competition   |
| The pricing power of the firms  | None                  | Limited based on perceived differences    | limited if less differentiate or Significant if not | Significant          |

### Perfect Competition

- It is where many firms produce identical products. And competition forces them all to sell at the market price
- This is just in theory, some industry like wheat production industry are close to it, its price depends on the overall market supply and demand
- A perfectly competitive market has a perfectly elastic demand curve for all firms. The marginal revenue is equal to the average revenue which is equal to the market price
  - For the market, the demand curve is still downward sloping
  - For a firm, the marginal revenue is the revenue for each addition product
  - For a firm, the average revenue is the average price of the product
  - A perfectly elastic demand curve, will have the price as a constant, regardless the quantity demanded
  - Under perfect competition firms must operate at minimum efficient scale in the long run, all compititos operate their at this scale in the long run. So this minimum will equal the market price which is the marginal revenue and also the average revenue, anyone operating at a different scale will have a cost that is higher than the market price and have a loss
- Neither economic profit nor economic loss is sustainable in the long run.
  - if existing firms are making economic loss in the short run some of them will eventually shut down or reduce scale thus reducing supply driving prices up and eliminating any economic losses
  - conversely if there are economic profits to be made new firms will enter the industry in the long run. Increasing supply drive in the market price down eliminating any economic profit in essence market price
  - As a result, in a long run the market price will always be at the minimun point of the `ATC` curve, this level is called the `Long-run equilibrium output level` for perfectly competitive firms
  - It goes the same if the economic profit or loss is triggered by a permanent increase/decrease in demand, firm will join or leave the market in long-run due to the changes in the market demand and make the market price back to normal, however the level of overall output will be changed based on the changes in market demand

### Monopolistic Competition

- It is where there are many sellers and differentiated products
- It has a downward sloping elastic demand curve
- It is characterized by a large number of independent sellers, each firm has a relatively small market share
- No individual firm has any significant power over price.
  - Firms need only pay attention to the average price charged in the market, not the price of individual competitors
- Unlike perfectly competitive markets where products are perfect substitutes for each other, firms under monopolistic competition produce slightly different products from each other in terms of quality features and marketing
  - Although there are differences, the competing products are close substitutes for one another as the basic functions are the same
  - Firms compete on price, quality, and features and marketing as a result of product differentiation
  - Marketing is a must to inform the market about such differentiating characteristics
- Firms have downward sloping demand curves, the demand curves for most firms are highly elastic because competing products are close substitutes
  - Firms can make their demand curves less elastic by providing compelling quality and features that consumers are willing to pay a premium for
  - For a firm, the demand curve is also the average revenue curve.
  - The marginal revenue curve is also downward sloping but below and steeper than the average revenue curve
- Monopolistic competition sells at a higher price, higher average cost, and a lower quantity than under perfect competition
  - Higher price is caused by downward sloping AR curve suggests that firm is not producing at the most efficient level. Because, for monopolistic competition, economic cost includes product differentiation costs such as marketing costs and R&D

### Oligopoly

- It is where a few firms compete in a variety of ways
- Firms need to consider other firms'(interdependent firms) strategy
- Demand is also downward sloping but can vary in elasticity, in general firms (Automobile Industry) that are very differentiated from itself to others tend to have more elastic demand than firms with less differentiation (Telco industry)
- An oligopoly market has higher barriers to entry due to economies of scale
- The level of differentiation can vary from good substitutes to high differentiation depending on the industry, this affects the level of pricing power
  - If the level of differentiation is high firms enjoy significant pricing power
- The key distinguishing feature of oligopoly markets is that the firms are interdependent
  - Actions of one company affect not just its own demand curve but also other competitor's, same goes for the price changes
- Oligopoly models has four types of models, each is under a serial of assumption

#### Kinked Demand Curve Model

- Kinked demand curve model is based on the assumption that an increase in a firm's product price will not be followed by its competitors
  - Other firms won't follow because they believe customers will switch to purchase their products and stay away from the product with higher prices, if they keeps the same old price
  - The demand curve for that firm is more elastic above the prevailing price
- The other assumption is that a decrease in price will be followed by its competitors
  - for prices lower than the prevailing price the demand curve is less elastic
- Based on the above assumptions, an oligopoly market has more to lose when it raises prices (high elastic demand curve at higher price) and has less to gain when it lowers prices (low elastic demand curve at lower price). The most profitable price and output combination for the firm is at the kink point where the elasticity is about to change
  - an oligopoly market will maintain its price at this level unless a competitor lowers its price
  - due to the shape of the kinked demand curve the corresponding marginal revenue curve for the firm will have a gap, each line with a difference slope on the two side of the kink point
  - If the `MC` curve fall in between the gap of the `MR` curve, the firm produces at the most profitable price and output combination
  - If the `MC` curve move higher, the price goes up and the firm lose lots of customer, this explain why most oligopoly market price is stable

#### Cournot Model

- The model considers an oligopoly with only two firms competing and both have identical and constant marginal costs of production
- Each firm knows the quantity supplied by the other firm in the previous period and assumes that the supply will not change in the next period
- In this model the combined equilibrium output will return a market price based on the market demand curve
  - this price output combination of the market is known as the Cournot equilibrium
  - This price will be much higher than the market price in a perfect competition market which is the same as the marginal costs
  - This price will be close to but smaller than the max market price in an unregulated monopoly market
  - As more firms join the market the outputs and price equilibrium positions move toward the competitive equilibrium

#### Nash Equilibrium

- It assumes that all firms in an oligopoly will make choices where there is a chance of a better outcome for the firm
  - In other words the Nash equilibrium is reached when the choices of all firms are such that there is no other choice that makes any firm better off
  - According to Nash, collusive agreements to increase profits are seldom successful, if there are no binding agreements
- When collusive agreements are made openly and formally the firms involved are called a `Cartel`, e.g. the `OPEC` oil cartel
  - If there is perfect collusion amongst the firms, the profit can be maximize and the market demand curve can be used to determine the price,
  - In reality, the price is lower and the quantity demanded is higher
- Collusive agreements to increase price in an oligopoly market will be more successful when:
  - There are fewer firms products are less differentiated
  - Cost structures are more similar
  - Purchases are relatively small and frequent
  - retaliation by other firms for cheating is more certain and more severe
  - Less competition from firms outside the cartel
- If we assume that there is perfect collusion amongst the firms the entire market acts like one big monopoly
  - Perfect competition amongst the firms in an oligopoly market is the other exemtre situation, the price output combination will be exactly the same as the perfectly competitive market in the long run
  - In reality the long run price will be in between the above two cases

#### Dominant Firm Model

- This model has a dominant firm in the market
  - It is a single firm that has a significantly large market share because of its greater scale and lower cost structure
  - The market price is essentially determined by the dominant firm and the rest of the firms are price takers
- The demand curve of the dominant firm is slightly below the market demand curve
  - the quantity supplied by the other firms decreases at lower prices, it means the dominant firms demand curve is even closer to the market demand curve when its price is low, and its supply is high
- Based on this demand curve and its associated marginal revenue curve, the firm will maximize profits at the production level where its `MR` is equal to `MC`, this point determines the market price
- The marginal cost curves of other firms are likely higher than that of the dominant firm, the quantity demanded for these firms is determined by the intersaction point between its `MC` curve and the market price

### Monopoly

- It is where only one firm is producing the product
- It has a downward sloping demand curve which is the market demand curve, and firm has the power to choose the price at which it sells its product
- For maximize profit, firms will expand output until its marginal revenue is equal to its marginal cost, the quantity then will determine the market price based on the market demand curve
- Long run positive economic profits can exist, because no other firm can join and change the market supply
- At average cost pricing, a monopolist earns zero economic profit
- At marginal cost pricing, a monopolist makes an economic loss.
- there can be a few reasons for monopolies:
  - Firstly very high barriers to entry protect a monopoly producer from competition
  - copyrights and patents also protect a monopoly from competition
  - sometimes firm has control over a resource specifically needed to produce the product
  - Mostly monopoly power is supported by government in such cases the price the monopoly charges is often regulated by the government as well
- Compared to a perfectly competitive market, the monopoly market will produce less total output and charge a higher price
- Monopoly market will not have consumer surplus and producer surplus both maximized like what perfect competetion market does
  - the consumer surplus is the area below the demand curve and above the price level
  - the supply surplus is the area above the supply curve and below the price level
  - High surplus means taking advantage of the transaction, high consumer surplus means paying to little, high supply surplus means earning too much
  - Monopoly market increases the producer surplus, at the expense of consumer surplus
- A single price model for monopoly market is where monopolist charges all its customers the same price for the product or service
  - This produces a quantity that does not maximize the sum of consumer surplus and produce a surplus from the market perspective
  - It creates a deadweight loss which is a loss of economic efficiency
  - It is an area where marginal benefit is still greater than marginal cost
  - Customers could purchase more goods but give up because of the higher price
- Price discrimination model is can be used to capture more profits by selling at a higher price to those who are willing to pay more, and selling at a lower price to those who will only buy if the price is lower
  - Through price discrimination the consumer surplus is reduced and so is the deadweight, the producer surplus is increased due to higher sales
  - Perfect price discrimination is an extreme case in theory, if it were possible for the supplier to charge each consumer the maximum they're willing to pay for each unit, there would be no deadweight loss because a monopolist would produce the same quantity as under perfect competition, there would also be no consumer surplus as all the surplus would be captured by the monopolist
  - Conditions for price discrimination to work:
    - The seller must face a downward sloping demand curve
    - Have at least two identifiable groups of customers with different price elasticity of demand for the product
    - Be able to prevent the customers paying the lower price from reselling the product to the customers paying the higher price
- Natural monopoly - It is due to the economics of production when there are large economies of scale
  - As firm in a certain industry grows bigger and bigger it become more effeient and other firm become harder to enter the market
  - Governments tend to regulate the price charged by natural monopolies to improve resource allocation, protect consumers, reduce deadweight loss, it can be done through
    - Regulating by average cost pricing - monopolist is required to set its price at its average cost
      - This increases the output and decreases price for consumers
      - The monopolist earns zero economic profit as the price just covers the cost of production it just earns a normal profit to cover opportunity costs
    - Regulating by marginal cost pricing - it forces the monopolies to reduce price to the point where the firms `MC` curve intersects the market demand curve
      - The market demand curve this further increases output and reduces price but causes the monopolies to incur an economic loss
      - Because price is below `ATC`, a government subsidy is provided in order to provide the firm with a normal profit and prevent it from leaving the market entirely
- Market Concentration Measurment - It is done by market regulator, in order to determine whether there is a monopolist in the market who violates any anti-competition laws, The methods are:
  - `Econometric` approaches aims to estimate the elasticity of demand and supply in a market by collecting large dataset and doing regression analysis on average past sales data of the entire market or sales of individual firms in a single period
    - If demand is very elastic the market must be very close to perfect competition, if demand is inelastic companies may have significant market power
  - `N-firm Concentration Ratio` is calculated as the sum of the percentage market shares of the largest and firms in a market, an example result can be 5 firms take up to the 80% of the market share
    - Simple to calculate and understand, but it does not directly quantify market power or elasticity of demand
    - If the barriers to entry are low, the market is still healthy
    - If dominant firms merge, it won't have a big impact on the N-firm concentration ratio, the following improved `HHI` calculation will be able to show the difference
  - `Herfindahl-Hirschman Index` (`HHI`) calculates the sum of the squares of the market shares of the largest N firms in the market
    - It is the most used method
    - Regulator will set a cap for N firms `HHI` and making decision or approval for merging firms based on the `HHI` calculation

## Economic Flows

- A modern economy consists of four major sectors:
  - households
  - businesses
  - government
  - foreign sector - acts like a gateway to the outside world
- The activity centre primarily around four types of markets:
  - goods and services market
  - financial markets
  - factors of production market
- Four sectors interact with four markets, with the following economic flows
  - Services of labor land and capital flow through the factor market to businesses
  - Income from businesses flow back to households in the form of profits and compensation
  - Households spend part of their income on current consumption where the expenditure flows through the goods and services market to the business sector
  - households also save part of their income for future consumption which flows into the financial markets
  - financial markets provides funding for businesses that need to borrow or raise equity capital
  - the amounts raised by businesses are invested in inventory property plant and equipment, so the investment money goes in the goods market
  - businesses also save part of their excess cash in financial markets for future needs
  - The government sector collects taxes from households and businesses
  - The government sector purchases goods and services from the goods and services market which flows back to the businesses
    - For example the government sector hires construction companies to build roads schools and public facilities, there are other spending on government services like the military and postal service
  - The government is also a major employer in the economy, so it has other sources of income and spending on related activities
  - If government spending exceeds net taxes then the government has a fiscal deficit and must borrow in the financial markets to fund its expenditures in our increasingly connected world
  - For the foreign sector, the net exports proceeds flow to businesses.
  - When an economy imports more than it exports, there is a trade deficit. A trade deficit must be funded by borrowing from the rest of the world through the financial markets conversely if the imports are less than exports. There is a trade surplus in this case. There is net foreign lending to the rest of the world

## GDP

- The `Aggregate Output` is the sum of all the goods and services produced in an economy over a certain period of time
- The `Aggregate Income` is defined as the total income earned by individuals and companies in the economy, excluding any adjustment for inflation and taxes
  - The value of the output produced must eventually accrue to the factors of production, so `Aggregate Output` and `Aggregate Income` within an economy must be equal
  - All workers use income to purchase goods and services produced from all factorys
- The `Aggregate Expenditure` is the total amount spent on the goods and services produced in the domestic economy during the period, it is defined as the current value of all the finished goods and services in the economy
  - All income spent on all domestic goods and services
- `Gross Domestic Product` (`GDP`) is formally defined as the total market value of the goods and services produced in an economy within a certain time period
  - By definition the `GDP` is the aggregate output of the economy for the period
  - As a result, in an isolated economy, `GDP`, `Aggregate Output`, `Aggregate Income`, and `Aggregate Expenditure` should all have the same value

### `GDP` Calculation

- `GDP` can be calculated by getting the value of `Aggregate Output`, and `Aggregate Income`

#### Expenditure Approach

- `GDP` is calculated as the total amount spent on the goods and services produced within the economy during a given period
  - It calculates total expenditures in the economy as the `consumption spending by households` plus `business investment` plus `government spending` plus the `net exports`
  - Market analysts generally prefer the expenditure approach because expenditure data is more timely and reliable than data for the income components

#### Income Approach

- `GDP` is calculated as the total amount earned by households and companies in the economy, it uses the sum of:
  - `National Income` - the sum of the income received by all factors of production they go into the creation of final output, which includes:
    - employee compensation
    - interest income
    - business owners incomes
    - rent
    - corporate and government enterprise profits before taxes
    - indirect business taxes less subsidies which include taxes like sales tax, import duties, and property taxes
  - `Capital Consumption Allowance` - measures the wear and tear of physical capital from the production of goods and services over a period, it can be thought of as the profit to be reinvested to maintain the productivity of physical capital
  - `Statistical Discrepancy` - an adjustment for the difference between GDP measured under the income approach and the expenditure approach because they use different data
- Based on the `Expenditure Approach`, `GDP` = `Households Spending` + `Business Investment` + `Government Spending` + `Net Exports`. Based on the economic flow this also equals `Households Spending` + `Net Taxes` + `Households Savings` + `Businesses Savings`
- `Households Savings` + `Businesses Savings` is known as `Domestic Private Saving`
- `Net Exports` + `Government Spending` - `Net Taxes`= `Domestic Private Saving` - `Business Investment`
  - `Government Spending` - `Net Taxes` is the government deficit
  - `Businesses & Households Savings` - `Business Investment` is the excess of private saving over private investment
  - `Net Exports` is the trade deficit
  - In conclusion, government deficit and trade deficit will always be covered by the excess of private saving over private investment

### `GDP` Calculation Criteria

- all goods and services included in the calculation must be produced during the measurement period
  - `GDP` is usually measured in one calendar year but many governments do give annualized quarterly estimates
- The second criteria is not the goods or services value can be determined by being sold in the market, non-market, illege activities or government benefits are excluded
- When using the expenditure approach only the market value of final goods and services should be included, the value of intermediate goods like raw materials and parts should be excluded
  - This type of expenditure approach is called the value of final output method
  - An alternative approach is the sum of value added method which is to sum up all the value added during the production and distribution processes

### Nominal vs Real GDP

- `Nominal GDP` of the economy are calculated using the current market value of the goods and services
  - `Nominal GDP` equals the sum of all the current prices multiplied by the quantity produced for each good in a certain period
  - As the growth in `Nominal GDP` will include the effect of price increase (inflation) for the period, this figure is not representative of the actual production growth
- Real `GDP` is calculated relative to a base year by using base year prices and current year output quantities
  - For base year, `Nominal GDP` is used to represent the `Real GDP`. The current year `Real GDP` equals the sum of each product of price from the base year times its output quantity of current year for all goods and services, then compare the `Real GDP` of the two year to get a relative increases
  - `Real GDP` growth reflects only increases in total output
  - Per capita `Real GDP` is defined as `Real GDP` divided by population
- the `GDP Deflator` is a price index that can be used to convert `Nominal GDP` into `Real GDP`
  - It equals the `Nominal GDP / Real GDP * 100` for a certain year
  - If the `GDP Deflator` index is known the conversion between `Nomial GDP` and `Real GDP` can be done easily

### Personal Income

- `Personal Income` is a measure of the pre-tax income received by households and is one determinant of consumer purchasing power and consumption, compare with the nationl income component, personal income:
  - includes employee compensation
  - includes interest income
  - includes business owner income
  - excludes income indirect business taxes are not considered personal income
    - This portion goes to the government
  - rent
  - includes shareholders distribution of the corporate benefits after tax
    - the taxes goes to the government are excluded
    - the portion retained by the company is excluded
  - includes transfer payments in the form of pay outs like unemployment benefits or indirectly through programs like universal healthcare
    - Transfer payments are excluded from national income, they are not government expenditures
    - Transfer payments are subtracted from government taxes income and reduce the net taxes amount
  - In conclusion, `Personal Income` is equal to transfer payments from the government plus national income minus distributed corporate profits, minus corporate income taxes, minus indirect business taxes
- `Personal Disposable Income` (`PDI`) = `Personal Income` + `Personal Income Taxes`
  - It measures the amount that households have available to either save or spend on goods and services
  - It is an important economic indicator of the ability of consumers to spend and save

## Aggregate Demand & Supply

### The IS (Investment vs Savings) Curve

- it plots the `goods market equilibrium` for real interest rate against real income
  - `goods market equilibrium` is the balance between the excess of private saving over private investment and the sum of government deficit and trade deficit
  - Baed on the economic flows, lower interest rates tend to decrease `Businesses & Households Savings` and increase `Business Investment`, in order to maintain the equilibrium in the goods market. Income must increase. Greater income can increase savings which increases `Businesses & Households Savings` and decrease `Business Investment`
    - Otherwise, tax or imports need to be incresed
- the relationship between real interest rates and real income has to be inverse to maintain equilibrium
- so the `IS` curve is downward sloping

### LM (Liquidity vs Money) Curve

- It plots the `money market equilibrium` for real interest rate against real income
- The demand for money equals to the supply of money
- Higher real interest rates decrease the demand and supply for liquid money because investors are encouraged to shift their assets out of money into higher yielding securities
- to maintain the real money supply at a given level, the income level should be increased such that the demand is kept constant as well
- the relationship between real interest rates and real income has to be direct to maintain equilibrium
- LM is upward sloping
- real money supply equals the nominal money supply (usually a constant) divide by the overall price level of the goods and services
  - If price level increases, real money supply decreases, the `LM` curve shift upwards
  - If price level decreases, real money supply increases, the `LM` curve shift downwards
  - At same interest rate level, high price level results in low real income, real income reflects the real purchasing power
    - Nominal income refers to the actually income amount
- Intersections between the IS and LM curves determine the equilibrium point of both the money and goods market

### Aggregate Demand Curve

- Real output, read GDP or real income of of the economy are refer to the same thing
- It determines the equilibrium levels of price level and real income, it is consisted of a collection of the intersection point between the `IS` and `LM`, when price level moves up and down on the y-axis
  - It is a downward sloping curve
  - It shows that higher price level reduce real income, increase real interest rate and make domestic goods more expensive, and reduce the quantity of demand for domestic goods
- The aggregate demand shows the relationship between the price level and the amount of output demanded at those prices from the consumer's point of view
- When `GDP` increases, this curve move to the right, based on the `Expenditure Approach` increase in `GDP` means:
  - For households, increases in consumer wealth or expect higher future income
  - For businesses, optimistic business outlook or high capacity utilisation
  - For government, expansionary fiscal policy through low tax rate and high government spending
  - For Import/Export
    - weaker currency rate - when a company's currency weakens against its major trading partners exports will increase and imports decrease
    - global economic growth - when global growth is strong foreign economies tend to buy more goods from domestic producers. Exports increase increasing aggregate demand
  - In addition, When the central bank adopts an expansionary monetary policy through lower reserve requirements and target low interest rates, the money supply increases and consumption from the above sectors will increase (can cause real estate boom)

### Aggregate Supply Curve

- It shows the amount of output that all the domestic producers are willing to provide at various prices level
- Similar to the aggregate demand curve, but from the producers's point of view, it also has price level on y-axis and quantity of real output on x-axis
- The very short, short, and long run aggregate supply curves are different because they depend on the how input prices like wages material costs and rent respond to changes in production levels

#### Very Short-Run Aggregate Supply Curve

- It is assumed that the input prices remain fixed regardless of changes in production levels
- Companies can increase or decrease output to some degree without changing price
- It is a horizontal line, a perfectly elastic supply curve
- The following very short term production increasing methods are available without increasing the unit cost of each unit produced
  - increasing overtime hours
  - maximizing the existing plant and equipment
  - depleting existing stockpile of components

#### Short-Run Aggregate Supply Curve

- Only some input prices will change as production is increased or decreased, becasue some input prices can be slow to adjust
  - the cost of certain components or raw materials may increase quickly due to the increased demand
  - wages may not have increased due to union contracts which can be valid for a few years
  - rental costs may not change in the short run
- It has an upward sloping aggregate supply curve
- Changes in costs of production will shift this supply curve
  - decrease input prices like wages rent and raw materials can decrease production costs, lower production costs allow firms to produce more for the same profits, then the SRS curve is shifted to the right.
  - strength of the local currency is a factor when a country's currency appreciates. Domestic firms import foreign goods at cheaper prices and causes the supply curce move to the right
  - decrease in taxes or increase in subsidies also lower the cost and shift the curve to the right
- Changes in expectation of future output prices
  - when businesses expect the price of their output to increase in the future they will expand production increasing SRS
    - Doesn't work if the price level of inputs adjusts according to output prices
    - This effect is more likely to be transient and modest
- Changes in costs of production and expectation of future output prices only have affect on `SRAS` Curve

#### Long-Run Aggregate Supply Curve

- All input prices tend to catch up with the level of their demand
- It has a perfectly inelastic supply curve
- It is vertical at the economy's potential level of real GDP
- `Potential GDP` increases as the economy's resource base grows
  - When the economy is at potential level of the GDP, the economy is at full employment and physical capital are all operating at 100 percent utilization
- Resource base of an economy includes,
  - Quantitative factors:
    - labor
    - natural resources like land and oil
    - physical capital like property, plant and equipment
  - Qualitative improvements:
    - Training and Education that increases the supply of human capital
    - Technology can increase labour productivity
- The curve shifts to the right when `Potential GDP` increases
  - This also holds true for short run supply curves

### Equilibrium

- Long-Run and Short-Run Aggregate Supply Curve intersects with Aggregate Demand Curve at the Long-run Full-employment equilibrium point
  - This is the point where the economy is producing at its full potential where there is no unemployment and all physical capital are operating at full capacity
- When `AD` curve shift to the left, in a short-run the economy produces less at a lower price level, and there is unemployment because `Real GDP` is less than the `Potential GDP`
  - Then gap between the actual `GDP` and the potential `GDP` is called the `Recessionary Gap`
  - Classical economists believe that unemployment would drive wages down which in turn would shift `SRAS` to the right and return the economy to its full employment level of real `GDP` at an even lower price level, so nothing need to be done
  - Keynesian economists believes this is a long and economically painful process, so action should be taken to stimulate `AD` through expansionary fiscal and monetary policy such actions can help to return real GDP to its full employment level and restore prices back to the level before the recession
- When `AD` curve shift to the right, there will be an `Inflationary Gap`
  - The economy can operate at this level in the short run as workers work overtime and maintenance of productive equipment is delayed
  - This is unsustainable in the long run because wages and input prices increase under intense competition thus increasing costs of production shifting the `SRAS` curve to the left, as a result the `Real GDP` is back the the `Potential GDP` level and the price level is higher
    - A Inflationary Loop happens if price keep going up and price levels go up without any increase in real output
    - Contractionary fiscal and monetary policies should be introduced to decrease government spending, increase taxes or slow the growth rate to the money supply through higher interest rates, this will shift `AD` curve back to its original level
- When `SRAS` curve shift to the left due to higher wage or energy cost, it is called a `Stagflation`, it causes a lower `GDP` and higher price level
  - If the country doesn't have control over the energy price, policymaker can only use expansionary policy to stimulate aggregate demand and shift the `AD` to the right, the `GDP` is back to normal, but at a higher price level
    - conversely policymakers can choose to fight inflation by decreasing aggregate demand, this is not ideal either as `GDP` is reduced further
    - If policymakers do nothing and wait for wages to come down due to high unemployment, the costs of production are lowered and the `SRAS` shifts back to the right where price and `GDP` go back to their previous levels. However, this is not a good from a political standpoint if there is high unemployment rate
- When `SRAS` curve shift to the left due to a decrease in the price of important productive inputs, this results in a new short run equilibrium where the GDP is greater than full employment GDP and the price level is lower, the situation may eventually correct itself where the tight labor market pushes wages up increasing production costs shifting `SRAS` back to its original equilibrium

## Economic Growth

### Five Sources of Economic Growth

- `Labor Supply` - the number of people over the age of 16 who are either working or looking for work, it is affected by:
  - population growth
  - immigration
  - labor force participation rate
- `Physical Capital Stock` - plant and equipment built up over the years to produce goods and services
  - Investments by businesses increases a country's stock of physical capital
  - Countries with a higher rate of investment into productive physical capital usually have a higher rate of GDP growth
- `Human Capital` - education and skill level of a country's labor force
  - skilled or well-educated workers are more productive as they are better able to harness advances in technology
  - Many countries invest in human capital either through educating the population or importing talents from overseas
- `Technology`
  - Most important for developed countries
  - As there is diminishing marginal productivity in adding physical capital. Technological advances are important as they allow advanced economies to overcome such limits
  - It requires investments in more advanced equipment and softwareplus a skilled workforce that can develop and harness the benefits of technology
  - Countries typically innovate through expenditures on R&D
- `Natural Resources` - material inputs such as oil and land which are necessary to produce economic output
  - It can be renewable like forests
  - It can be non-renewable like oil
  - Countries with large amounts of productive natural resources like oil and achieve greater rates of economic growth
  - This factor is not mandatory for enconomic growth

### Growth in Potential GDP

- `Production Function` states that the `GDP` equals a function of the size of the labour force and the amount of capital multiply by a total factor productivity
  - the size of the labour force reflects the `Labor Supply` and `Human Capital` factors
  - the amount of capital reflects the `Physical Capital Stock` factor
  - the total factor productivity reflects `Technology` factor
- The `Production Function` can be transformed into a per work basis by using the GDP per work as output, which is a function of the amount of capital per worker, multiply by the total factor productivity
  - The output of this per worker `Production Function` is called the `Labour Productivity`
  - Economists often look at labor productivity as a measure of the health and prosperity of an economy
  - The higher the level of labor productivity the more goods and services the economy can produce with the same number of workers
- `Potential GDP` equals the size of the labor force times the labor productivity
  - The size of the labor force equals the aggregate hours worked among all workers
- Long term `Potential GDP Rate` equals `Labor Force Growth Rate` plus `Labor Productivity Growth Rate`
  - This growth rate is important because long term equity returns are highly dependent on economic growth over time
- The Solow model or Neoclassical model states the growth in potential GDP equates to growth in technology plus the growth in labor times a weight `Wl` plus growth in capital times a weight `Wc`
  - The two weights represent the shares of labour's and capital's percentage shares respectively, and two weights add up to one
  - For most developed economies `Wc` is lower than `Wl`. Investments in physical capital to grow the economy are less effective than growing the workforce
  - The growth in technology represents the change in total factor productivity
- The Neoclassical model can have a per-capita form where the `Growth in per-captita Potential GDP` equals `Growth in Technology` plus `Wc` times `Growth in Capital-to-labour ratio`
  - In developed economies where capital per worker is already relatively high there may be `diminishing marginal productivity` of capital. This means that policymakers cannot continue to grow the economy through capital deepening investments
  - In developed economies, growth in technology should be the primary source of growth in GDP per worker

## Business Cycle

### Phases of Business Cycle

- Business cycles can be thought of as fluctuations around the following trend growth of an economy
- The length of business cycles varies depending on the companies, it can be as short as a year or longer than a decade
- This wave shape business cycles recur, in the long-term it can have an overall uptrend or downtrend
- The recovery (or early expansion) or trough phase - GDP stops decreasing and begins increasing
  - Companies stop layoffs, unemployment rate is still high
  - Consumer and business spending may slowly pick up particularly in housing and consumer durables
  - inflation remains moderate and may continue to fall
- expansion phase - real GDP is increasing
  - businesses increase hiring to meet rising demand and unemployment rate falls
  - consumer and investment spending increase greatly
  - Inflation picks up modestly as price increases with a delay
- peak phase - real GDP stops increasing and begins decreasing
  - Business activity starts to decelerate
  - Businesses slow their rate of hiring adn the unemployment rate continues to fall at a decreasing rate
  - spending is still increasing but the rate of spending starts to slow
  - inflation accelerates at this stage
- contraction or recession phase - real GDP is decreasing
  - Business activity declines
  - Business start laying off, unemployment rate rises
  - Spending by both consumers and businesses falls
  - Inflation decelerates with a lag
- Generally, consider two consecutive quarters of growth in real GDP as the beginning of an expansion and two consecutive quarters of declining real GDP as indicating the beginning of a recession

### Business Cycle Indicator

- Inventory
  - Firms want to keep a balance of having enough inventory for sales and having enough liquidity
  - The ratio of inventory to sales can be used to indicate the business cycle
  - In steady economic growth this ratio is at its normal level
  - During recession as sales pick up the ratio decreases to meet the increase in demand
  - Firms will increase output and the inventory to sales ratio will increase toward normal levels during the expansion phase
  - During peak phases, sales growth begins to slow and unsold inventories accumulate, inventory to sales ratio rises above its normal level
  - Firms respond by reducing production which is one of the causes of the subsequent contraction in the economy, then the ration reaches the normal level
  - A planed increase in this raito means firms are anticipating higher demand, and it is a sign of the expansion phase
  - if the increases unplanned it is a sign of the recession phase
    could be an early sign of a recession forming
- Labor
  - Hiring and retrenchment is not just costly in terms of direct expenses. it can damage employee loyalty and morale
  - Firms prefer adding overtime hours to the current workforce than hiring
  - Firms only hire more when it is necessary which is around the mid to end of the expansion phase and downsize the workforce at the beginning of the contraction phase
- Physical capital
  - It is costly to adjust production levels frequently
  - Similar to the trend of the labor force, firms purchase new equitment at mid to end of the expansion phase
  - At the beginning of the contraction phase, firms reduce their physical capacity by spending less on maintenance or purchase new equipment when it is near the end of its useful life

### Housing Sector in Business Cycle

- The housing section affect the economy with a cyclical swings
- It is affected by the following three factors
- It is sensitive to the `Interest Rate`
  - Interest Rates are usually low during recessions and high during expansion
  - Low interest rates tend to increase home buying and construction while high interest rates tend to reduce home buying and construction
- `Affordability` is a factor measured by household income relative to housing prices, higher affordability can lead to higher sales
  - Household incomes are typically lower in the contraction phase and higher in the expansion phase
  - Household incomes cannot determine the affordability entirely, e.g. in peak phase, the income level is high but the housing price level is also high
- `Speculative Activity` is the expectation that buyer can sell real estate on a higher price in a short period
  - It can be independent from the business cycle
  - Higher prices lead to more construction eventually resulting in oversupply and a subsequent fall in prices
  - When speculative buyers are forced to sale their properties when housing price falls, it will make the price drop further and it can destabilize the financial system as evident in the 2008 financial crisis
- `Demography` is also an important factor
  - It is independent from the business cycle
  - Population in the 25 to 40 year old segment is particularly important because they have the greatest demand for new houses
- `Urbanization` - When governments encourage shifts from rural areas to cities construction activity in cities picks up to accommodate new settlers

### External Trade in Business Cycle

- It depends on domestic GDP growth relative to trading partners GDP growth
  - Increasing growth of domestic GDP leads to increases in imports of foreign goods, decreasing domestic GDP growth reduces imports
  - Increasing foreign incomes increase exports, decreasing economic growth in foreign countries decreases exports
- Relative strength of the country's currency is another factor
  - If a country's currency strengthens against its trading partners its goods are relatively more expensive so exports decrease and imports increase
  - If a foreign currency strengthens the country's domestic goods become relatively cheaper than foreign goods, exports increase and imports decrease

### Theories of Business Cycle

- `Business Cycles` are a result of short term fluctuations in aggregate demand and short-run aggregate supply
  - Aggregate demand and Short-Run aggregate supply are determined by `Market` forces
    - Shifts in `Aggregate Demand` are mainly due to factors such as `Consumer and Business Sentiment`
    - Shifts in `Short-Run Aggregate Supply` are mainly driven by cost factors such as `Input Prices` and `Wage` levels
  - `External Shocks` and changes in `Technology` can also affect demand and supply significantly
  - `Government Policies` also have significant influence
    - `Monetary Policies` affect the rate of increase of `Money Supply` through instruments like the benchmark interest rate, this can shift aggregate demand
    - `Fiscal Policies` is also a factor
      - `Government Spending` which has a direct effect on the aggregate demand
      - changes in `Tax Rates` affect both aggregate demand and short run aggregate supply
- `Neoclassical` economists believe that the economy has a strong tendency toward full employment equilibrium, so in theory business cycles should not exist
  - They do acknowledge that changes in technology can greatly affect certain industries that are displaced by the technology and that can cause limited short term lowering of aggregate demand resulting in a recession
  - They believe that such recessions are short lived, as unemployment will lower wages shifting the `SRAS` curve to the right such that the economy is back to its long run equilibrium
  - No intervention is needed from the government
- `Austrian` School share most of the beliefs of the `Neoclassical school`. The key difference is that the `Austrian` economists argue that business cycles are not a result of changes in technology but misguided interventions by the government
  - When policymakers lower the interest rate, firms invest too much. When these investments turn out poorly, firms must decrease output in those lines which causes a contraction
  - Austrian economists believe that government intervention should be avoided
  - `Neoclassical` and `Austrian` theories both agree that wages will adjust such that the economy will always return to full employment, so recessions should be short lived
- `Keynesian` economists argue that it can take a very long time for the market to adjust wages and go back to full employment this is because wages are inherently `Downward Sticky`
  - `Downward Sticky` means people will choose to remain unemployed rather than to accept a pay cut
  - They believe the business cycle is the result of swings in market sentiment rather than changes in technology or government intervention
  - they argue that for long and deep recessions government intervention particularly in the form of expansionary fiscal policy is necessary to save the economy
- `Monetarist` economists believes government intervention is bad, `Monetary Policies` is good
  - `Monetarists` believe that the `Keynesians` focus on fiscal policy is misplaced
  - They think the `Keynesian` model fails to consider the long term harm that can be caused by sustained government budget deficits and there may be a lag in the stimulative effects of fiscal policy
  - Government intervention may be too slow to prevent an economic crisis from blowing up
  - They believe money supply has the greatest effect on the economy
    - When the money supply grows too fast, the boom is unsustainable
    - When it grows to slow the economy contracts
  - `Monetarists` recommend that the government should follow a policy of steady and predictable increases in the money supply in order to keep aggregate demand stable and growing
- `New Classical` school economists also doen't like government intervention as the predictable loosening and tightening of money supply itself can cause a recession as businesses would just wait for easy money to start investing
  - `New Classical` models consider the changes in technology and external shocks as the main cause of business cycles, such models are called `Real Business Cycle` (RBC) models
  - `New Classical` economists believe that expansions and contractions represent efficient operation of the economy in response to external real shocks and technological changes
  - They believe the government should not intervene in the economy

### Unemployment

- In any economy, employers hire to meet increased demand and fire when demand falls. Workers also quit to look for better jobs and new graduates start looking for jobs.
- Categories of Unemployment
  - `Frictional Unemployment` is due to the time lag necessary to match job seekers with employers
    - This is unavoidable, there will always be some frictional unemployment
  - `Cyclical Unemployment` is caused by short run changes in the general level of economic activity
    - in a recession, the number of available jobs is fewer. So the proportion of unemployed increases
  - `Structural Unemployment` is caused by long run changes in the economy that eliminates some jobs while new jobs for which the unemployed workers are not qualified for
    - This is a structural problem because the unemployed workers do not currently have the skills needed to perform the jobs that are available
- formal definitions of unemployment
  - an `Unemployed` person is one who is not working but is actively searching for work
  - A `Long-term Unemployed` happens when a job seeker has been unsuccessfully looking for a job for several months
  - An `Underemployed` person is someone who is employed part time but would prefer to work full time or is paid far below what his qualifications or skills suggest
    - This is very subjective
  - A `Discouraged Worker` is one who has given up looking for a job perhaps because of a weak economy
  - A `voluntarily unemployed` people choose not to be employed because wages are not up to their expectation or they choose to retire early
- The `labor force` of an economy consists of `Employed`, `Underemployed` and `Unemployed`
  - `Discouraged Workers` are statistically outside the labor force
- the `Participation Ratio` is the size of the labor force as a percentage of the working age population
- The `Unemployment Rate` is the percentage of the labor force that is currently classified as unemployed
- Economy Cycle Indicators
  - the `Unemployment Rates` is a lagging indicator of the health of the economy, it will alway fall behind the movement of the economy as employers trying to minimize hiring and firing as these are costly exercises
    - If a drop in unemployment is accompanied by a drop in participation rate. It may mean that more of the unemployed have given up looking for jobs rather than an actual pickup in hiring
    - It shows that discouraged workers might be hidden inside the unemployed people as it is hard to tell
    - So `Unemployment Rates` might not be a good indicator
  - `Payrolls Growth` can be a better indicator of the economy cycle, it can be a good indication of recovery when they rise number of hours worked especially overtime and the use of temporary workers may also be useful indications of economic activity
  - `Number of Hours Worked` especially overtime and the use of `Temporary Workers` may also be useful indications of economic activity firms tend to increase overtime hours and hire part time workers to cope with initial pickup in demand.
    - these two indicators may be a better signal of economic recovery than the unemployment rate
  - `Productivity` is a measure of output against the number of workers declines early in contractions as firms try to keep workers despite producing less output, in early expansion phase firms trying to produce more output with existing workers, so productivity rises

### Inflation

- Inflation is a sustained increase in the overall price level over time
  - Inflation erodes the purchasing power of a currency meaning that the same dollar can buy less goods over time
  - inflation favors borrowers at the expense of lenders, because when the borrower returns the principal to the lender, the purchasing power of that amount is lower than it was when it was borrowed
- the inflation rate is the percentage increase in the price level typically compared to the prior year
- In general the inflation rate is pro cyclical (a sine wave above 0)
  - It goes up and down with the business cycle but with a lag of a year or more
- `Disinflation` refers to an inflation rate that is decreasing over time but remains greater than zero
- `Deflation` is the phenomenon where the inflation rate is persistently negative over a period of time
  - It is commonly associated with deep recessions
  - Central banks want to avoid at all costs as it is difficult to bring an economy out of deflation
  - When most prices are decreasing consumers delay purchases because they believe they can buy the same goods more cheaply in the future. This depresses aggregate demand causing prices to further decline in a downward spiral
- `Hyperinflation` happens when inflation accelerates out of control
  - It can destroy a country's monetary system and bring about social and political upheavals
- Central banks tend to closely monitor the inflation rate and take monetary actions to keep it within
  a target range
  - Contractionary monetary policies like increasing the benchmark interest rate are used when inflation is too high
  - Expansionary policies are used when the inflation rate is too low

#### Cost Push Inflation

- `Cost Push Inflation` - Inflation happens when the cost of an important factor of production such as labor or energy increases
  - The short run aggregate supply curve of the economy is shifted to the left. Output is lower but price is higher. If the central bank opts to stimulate aggregate demand so output returns to its long run potential, the result would be a further increase in the price level
  - The cost push effect decreases GDP resulting in higher short term unemployment
- The source of cost push inflation is mostly the pressures caused by increase in wages.
  - Lower unemployment rate can generate a higher the pressure on wages
    - The unemployment rate may not be the most effective indicator of wage pressures
    - `Job-skills mismatch`, `Cultural Patterns` that despise certain jobs, and `Inefficiencies` in the labor market can make the unemployment rate misleading
- `NAIRU` (`Non-accelerating inflation rate of unemployment`) or `NARU` (`Natural rate of unemployment`)
  - they can be better indicators of wage pressures which is a major factor of cost push inflation
- `Labor Productivity` can be used to identify signs of potential wage pressure
  - wage increases are not inflationary as long as they remain in line with gains in productivity
  - A useful indicator of wages and benefits in terms of productivity is `Unit Labor Costs`
    - It is the ratio of `Total Labor Compensation per Hour` to `Output Units per Hour`
- `Expected Inflation` can generate wage pressure. If workers expect inflation to increase, they will increase their wage demands accordingly
  - `Expected Inflation` can be determined by using the difference in yields between inflation indexed bonds such as `Treasury Inflation Protected Securities` and otherwise similar non indexed bonds

#### Demand Pull Inflation

- It happens when prices rise as a result of demand pressures.
- the increased demand is usually a result of an increase in the money supply or increased government spending, rising cost of production results in a decrease in short run aggregate supply until real GDP reverts back to full employment GDP
- To measure the potential for demand pull inflation in an economy. Economists often study the capacity utilization rate of key industries
  - High rates of capacity utilization suggest that the economy is producing above potential GDP and may experience inflationary pressure
- The demand pull effect increases GDP above full employment GDP

#### Inflaction Calculation

- Various index can be calculated to determine the inflaction rate
- `Consumer Price Index` (`CPI`) is to determine the change in the overall price of a basket of goods and services that reflect the cost of living of a typical consumer
  - basket of goods and services is a set quanaity of goods and services
  - as the typical consumer can differ vastly between countries, each country has their own definition on basket of goods and services
- The `CPI` is known as the `Laspeyres Index` if it uses the same quantity of goods and services for the base year to calculate the overall expense in the current year, then represent the change in percentage
- The `Laspeyres Index` has shortcomes like:
  - `Quality Bias` the price increase for a product may be partially due to improvements in quality, not just inflation, this creates an upward bias
    - quality bias can be adjusted by a technique known as `Hedonic pricing` where the products in the basket are reviewed and their current prices adjusted for the improvements in quality
  - `New Products Bias` - New products are frequently introduced and priced competitively to gain market share however a fixed basket of goods and services will not include them, this creates an upward bias. It can be fixed by
    - Periodically reviewing consumption habits
    - To adjust the quantities of the current basket of goods
    - Add in new products that consumers are switching to
  - `Substitution Bias` when two goods are substitutes for each other, consumers buy more of the relatively cheaper goods and buy less of the relatively more expensive good. If using outdated consumption figures from the base period, the Laspeyres buyers index can be upwardly biased again
    - A chained price index like the `Fisher Index` can be used to fix this bias
- `Fisher Index` is the geometric mean (root of the product) of a `Laspeyres Index` and a `Paasche Index`
  - `Paasche Index` uses the `Current Consumption Weights` and current prices to compute the cost of the basket
    - This is indicative of the substitution bias in the `Laspeyres Index`
  - This is an adjusted CPI that takes into account that consumers may have substituted relatively more expensive goods with relatively cheaper substitutes
- `Personal Consumption Expenditures` (`PCG`) is based on business surveys
  - `PCG` and `CPI` all measures comsumer price inflation
- `Producer Price Index`(`PPI`) or `Wholesale Price Index` reflects the price changes experienced by producers
  - This is based on items like fuels farm products machinery and equipment transportation equipment and so on
  - Because price increases of these items may eventually pass through to customers. The `PPI` can be a predictor of the future `CPI`
- `Headline Inflation` refers to price indices for all goods
- `Core inflation` refers to price indices that exclude food and energy
  - as food and energy prices are typically more volatile than other goods, core inflation is therefore less volatile and can sometimes be a more useful measure of the underlying trend in prices
- `GDP Deflator` is usually determined by the above price indices

### Economic Indicators

- In the United States, a market research organization called the `Conference Board` compiles leading coincident and lagging indicators for the US and several major economies
- One or more indicator from the same type can be aggregated
- All following three types of indicators need to be reviewed to build a stronger case in determining which phase
  of the business cycle the economy is in
- classifications of the following indicators reflect tendencies in the timing of their turning points, not necessarily true all the time
- Not all changes in direction of leading indicator indices have been followed by corresponding changes in the business cycle, and even when they have the lead time has varied

#### Lagging Indicator

- It doesn't tend to change direction until expansions or contractions are already underway
- It can serve to confirm that the economy is in an actual expansion or contraction phase
- `Conference Board` indicators
  - Average duration of unemployment
  - Inventory-sales ratio - businesses are slow to stock up on inventory
  - Change in unit labor costs
  - Average prime lending rate
  - Commercial and industrial loans - these loans frequently support inventory building
  - Ratio of consumer installment debt to income
  - Change in consumer price index - inflation generally adjusts to the cycle late as producers are slow to adjust prices
- `Aggregate Leading Indicator Index`
  - `Index of Leading Economic Indicators` (`LEI`) - It contains 10 types of `Leading Indicators`
- `OECD` compiles the `Composite Leading Indicators` (`CLI`) for several countries including `EU` or `G7` nations

#### Coincident Indicator

- It changes its direction at roughly the same time as the peaks or troughs
- It can serve to confirm that the economy is in an actual expansion or contraction phase
- `Conference Board` indicators
  - Employees on nonfarm payrolls - businesses adjsut their fulltime payrolls once recession/recovery is clear
  - Aggregate real personal income
  - Index of industrial production
  - Manufacturing and trade sales

#### Leading Indicator

- It is known to change direction before peaks or troughs
- It helps with anticipating cyclical turns and allow strategists and businesses to position themselves to benefit or protect themselves from movements in the business cycle
- `Conference Board` indicators
  - Average weekly hours in manufacturing
  - Initial claims for unemployment insurance - very sensitive indication of initial layoffs and rehiring
  - Manufacturers' new orders for consumer goods
  - Manufacturers' new orders for non-defense goods
  - Institute for Supply Management (ISM) new orders index - decline in new orders can be indication of weekness in demand
  - Building permits for new houses
  - S&P 500 equity price index - stock prices anticipate economic turning points
  - Leading Credit Index
  - 10-year Treasury to Fed funds interest rate spread
  - Consumer expectations

## Monetary and Fiscal Policy

- Money is simply a medium of exchange
- In a `Barter System`, goods and services are exchanged directly
- Money can be:
  - Means of payment - can be used to purchase goods
  - Universal unit of account - can be used to measure the value of goods
  - Store of Value - can be used to save
- Banks in early days start with depositing gold and silver and return a promissory notes
  - Promissory notes then became the early form of money, when people start to exchange them for service and goods
- When banker realize all deposits would never be withdrawn at the same time, it starts to lend a portion of the deposits to earn interest
  - This is called a `Fractional Reserve Banking`
  - `Reserve Requirement` is a minimum percentage of deposits that banks are required to hold
  - Assume the led moeny will end up in another bank, and so on, the total money created by this system equals `New Deposit` divided by the `Reserve Requirement`
  - `Money Multiplier` - The reciprocal of the `Reserve Requirement`
- `Narrow Money` defines the money as notes and `coins in circulation` plus `very liquid assets` such as bank deposits in current accounts
- `Board Money` includes all `Narrow Money` plus `less liquid assets` which can still be used to make purchases
- the definition of what constitutes money differs amongst central banks around the world
- In the U.S. the Federal Reserve produces two measures of money
  - `M1` - Narrow Money
    - notes and coins in circulation
    - traveler's checks of non-bank issuers
    - demand deposits at commercial banks
    - other deposits on which checks can be written
  - `M2` - Board Money
    - includes `M1`
    - savings and money market deposits
    - time deposit accounts have less than one hundred thousand dollars
    - other balances in retail money market and mutual funds
- the European Central Bank produces three measures of euro area money supply
  - `M1` - Narrow Money
    - notes and coins in circulation
    - all overnight deposits
  - `M2` - Board Money
    - includes `M1`
      - deposits redeemable with notes up to three months
      - deposits with maturity up to two years
  - `M3` - Boardest Money
    - includes `M2`
    - repurchase agreements
    - money Market Fund units
    - debt securities with up to two years maturity

### Demand and Supply of Money

- `Demand for Money` - the amount of wealth that households and firms in an economy choose to hold in the form of money
- There are three main reasons for holding money
  - There is transaction demand where the money is needed for undertaking transactions like paying of employee salaries and payment for goods and services
    - As the level of real GDP increases the size and number of transactions will increase and the demand for money to carry out transactions increases
  - There is precautionary demand where money is held for unforeseen future needs
    - The demand for money for precautionary reasons is higher for large firms. The total amount of precautionary demand for money increases with the size of the economy
  - There is speculative demand where money is set aside to take advantage of investment opportunities that may arise in the future, there are three reasons
    - the expected returns of the market. If Bonds and other financial instruments provide higher returns investors would rather invest their money now than hold speculative money balances
    - the perceived risk in the market. If the risk is perceived to be higher. People choose to reduce exposure to risky assets and hold money instead.
    - short term interest rates which referes to the interest rates of risk free bonds. At lower interest rates firms and households choose to hold more money, so money demand is higher
- The money demand curve against nominal (short-term or market) interest rate should be downward sloping
- The supply of money is determined by the central bank, So it is independent of the interest rate this accounts for the perfectly inelastic (vertical line) supply curve
- Market (short term) interest rates are determined by the equilibrium between money supply and money demand
  - If the interest rate is above the equilibrium rate there is excess supply of real money. Firms and households are holding more real money balances than they desire so, they'll purchase short term bonds to reduce their money balances which will decrease the interest rate as bond prices are bid up
  - If interest rates are below equilibrium, There is excess demand for real money balances firms and households will sell securities to increase their money holdings to the desired level. Decreasing bond prices and increasing the interest rate
- A central bank can affect short term interest rates by increasing or decreasing the money supply.
  - For example an increase in the money supply will shift the money supply curve to the right. This causes the equilibrium rate to fall which pressures market interest rate to follow
  - Conversely, if the central bank decreases the money supply. Excess demand for money balances results in sales of securities and an increase in the interest rate
- `Money Neutrality` - Some economists believe that in the long run an increase in the supply of money will increase in the aggregate price level while real output and money velocity remains unchanged
  - The quantity theory of money states that quantity of money is proportional to the total spending in an economy
  - In the quantity equation of exchange, `M * V = P * Y`
    - `M` is the quantity of money or money supply
    - `V` is the velocity of circulation of money which is the average number of times each unit of money (e.g. one dollor) is used for purchases
    - `P` is the average price level
    - `Y` is real output in terms of units sold
  - Assuming that velocity and real output remain constant. Any increase in the money supply will lead to a proportionate increase in the price level
  - For this reason monetarists argue that monetary policy to regulate the supply of money can be used to control inflation
- `Fisher Effect` - it states that the real rate of interest in an economy is stable over time so that changes in nominal interest rates are the result of changes in expected inflation, thus the nominal interest rate in an economy is the sum of the `Real Rate Interest` (Required real return), the `Expected Rate of Inflation` (compensation for expected inflation), and a `Risk Premium` (compensation for uncertainty)
  - This is consistent with money neutrality when nominal interest rate can be seen as the aggregate price level while other factors like real interest rate keep unchanged
- `Expected Inflation` is the level of inflation that the government households and businesses expect in the future
  - Maintaining a stable inflation rate is the primary objective of the central banks
- `Unexpected Inflation` is the level of inflation experienced that's above or below the expected inflation
  - It is much more costly to the economy than expected inflation
- The cost of `Expected Inflation` are:
  - `Menu Costs` - High inflation always means that businesses constantly have to change the advertised prices of their goods and services.
  - `Shoe Leather Costs` - the costs to individuals of making frequent trips to the bank to minimize their holdings of cash which are depreciating in value due to inflation
  - `Cost of Holding Money` - Purchasing power of money decreases at a faster rate than interest-bearing securities, then people will tend to shift more of their money from the bank to interest bearing securities like government bonds. The cost of such transactions can be significant other than these costs
- The cost of `Unexpected Inflation` are:
  - `Inequitable Transfer of Wealth` between borrowers and lenders
    - The cost of high inflation occurs only when it is not perfectly anticipated
    - No cost when everyone increase the price and cost of everything at the same time
    - Otherwise, there will always have someone make profit from it and some others have loss from it
  - `High Cost of Borrowing` - If inflation is very uncertain or very volatile then lenders will ask for a higher risk premium to compensate them for this uncertainty
    - Higher borrowing costs could in turn reduce economic activity
  - `Lower information Content of Market Prices` - This happens when the unexpected inflation makes business owner to make wrong decisions and then it takes more time and adjust
    - unexpected inflation can increase the magnitude or frequency of business cycles
    - Misinformation is a real cost to the economy

### Central Bank

#### Roles of Central Banks

- Central banks have the sole authority to supply money
  - Traditionally such money was backed by gold, the central bank stood ready to convert the money into a pre specified quantity of gold
  - the gold backing was removed and money supplied by the central bank was deemed legal tender by law
    - This refers to the `Fiat Money` - which is money that not backed by any tangible asset
    - `Fiat Money` holds its value over time and is acceptable for transactions, it can continue to serve as a medium of exchange
- Central bank provides banking services to the government and other banks in the economy
  - the central bank also acts as a lender of last resort. It can supply money to banks which are short of money. This role assures depositors that their funds are secure and therefore prevents a run on banks from happening
- The central bank is the regulator and supervisor of the banking and payment systems
  - In many countries, central banks may regulate the banking system by imposing standards of risk taking allowed and reserve requirements of banks under its jurisdiction
  - central banks also oversee the payment system to ensure smooth operations of the domestic clearing system and in conjunction with other central banks for international transactions
- The central bank is also the holder of the nation's gold and reserves of foreign currencies.
- The central bank is the conductor of monetary policy.
  - The central bank controls or influences the quantity of money supplied and the growth of money supply over time.
  - These are done to achieve its stated objectives.

#### Objectives of Central Banks

- The single most important objective of most central banks is to control inflation in order to promote price stability
  - most central banks focus on keeping inflation close to a stated target rate this target rate is usually a range of around 2 to 3 per cent for most developed countries
  - The US Fed and the Bank of Japan do not have an explicit target inflation rate
    - This is because the US Fed has the additional goals of maximum employment and moderate long term interest rates
    - In Japan. It's because deflation rather than inflation has been a persistent problem in recent years
- For most developed nations, monetary policy can be quite effective to regulate the supply of money in their economy.
- Most developing nations may have some difficulty in using monetary policy to control inflation, some common reasons include:
  - The absence of a sufficiently liquid government bond market
  - A rapidly changing economy
  - A poor track record in controlling inflation in the past, making monetary policy intentions less credible
  - An unwillingness of governments to grant genuine independence to the central bank
- Instead of depending solely on monetary policy some central banks rely on pegging their exchange rate against a major currency, primarily the US dollar
  - This involves setting a fixed level or range for the exchange rate against the dollar with the central bank supporting the target by buying and selling the domestic currency in foreign exchange markets
  - The basic idea is that by tying a domestic economy's currency to that of an economy with a good track record on inflation, the domestic economy would effectively import the inflation experience of the low inflation economy
  - The centrel bank of that country sells foreign currency reserves and buys domestic currency to lower domestic money supply and increase short-run interest rate when it experiences high domestic inflation and low exchange rate of their currency, then bring down the inflation

#### Desirable Qualities of Central Banks

- `Independence` - a central bank should be free from political interference for it to be truly effective
  - The political party in power has a preference to boost economic activity and reduce unemployment to create a feel good environment that will increase its popularity
  - The central bank on the other hand has the main objective of maintaining price stability and that may mean taking steps to limit money supply which can hamper economic growth
  - As such it is best that political parties do not interfere with the work of the central bank as they may compromise the central banks ability to manage inflation
  - Independence should be thought of as a spectrum (scale) rather than in absolute terms
  - Independence can be evaluated based on both `Operational Independence` and `Target Independent`
    - `Operational Independence` means that the central bank is allowed to independently determine the policy rate
    - `Target Independence` means that the central bank also defines how inflation is computed, sets the target inflation level, and determines the horizon over which the target is to be achieved
  - Most central banks only have operational independence.
    - European Central Bank has both Target and operational independence
- `Credibility` which affects how businesses and households perceive the central bank's will and ability to follow through on their stated intentions
  - A credible central bank's targets can become self-fulfilling prophecies
  - If the market believes that a central bank is serious about achieving a target inflation rate of 3 percent, wages and other nominal contracts will be based on 3 percent inflation and actual inflation will turn out to be close to 3 percent.
- `Transparency` - transparency means central banks regularly disclose the state of the economy by issuing inflation reports
  - The reports disclose to the public the central bank's views on the range of indicators that they watch, when they come to their monthly interest rate decision
  - By explaining their views on the economy and by being transparent in decision making. The central bank seeks to gain reputation and credibility. This makes it easier for them to influence inflation expectations

### Monetary Policy

#### Monetary Policy Tools

- `Reserve Requirement` is the percentage of deposits, banks are required to retain as reserves
  - An expansionary policy is to decrease the reserve requirement which effectively increases the funds that are available for lending and the money supply which will tend to decrease interest rates
  - An increase in the reserve requirement will decrease the funds available for lending and the money supply which will tend to increase interest rates
  - Most developed economies have not been using reserve requirements as a tool because its banks seldom lend to the extent that the reserve requirement has hit. Adjusting the reserve requirement may have limited impact on lending and market interest rates
  - Reserve requirements are still actively used in many developing countries to control lending as demand for capital is high
- `Policy Rate` also known as the official or benchmark interest rate set by the central bank
  - The purpose of the policy rate is to influence market interest rates and ultimately real economic activity
  - This is the interest rate that the central bank lends money to commercial banks at
    - One common way to lend money to banks is through a repurchase agreement. The central bank purchases securities from banks that in turn agree to repurchase the securities at a higher price that's equal to the principal plus the interest which is the policy rate
    - the Bank of England uses this method and its policy rate is called the two week repo rate
    - For the European Central Bank. It's called the refinancing rate
    - In the US. This rate at which banks can borrow funds from the Fed is termed the discount rate. However the most important interest rate used in U.S. monetary policy is not the discount rate, but the Fed funds rate. This is the rate that banks charge each other on overnight loans of reserves. The Fed sets a target for this market determined rate and uses open market operations to move it to the target rate.
  - The neutral interest rate is the growth rate of the money supply that neither increases nor decreases the economic growth rate
    - It can be estimated by adding the central bank's inflation target to the real trend rate of economic growth trend rate
      - This is the economy's long term sustainable real growth rate
      - the trend rate is not directly observable and must be estimated. It also changes over time as structural conditions of the economy change.
  - When the policy rate is below the neutral rate. The monetary policy is said to be expansionary
  - Contractionary policy is to set a higher policy rate which decreases lending and increases interest rates
- `Open Market Operations` which is the buying and selling of government bonds by the central bank
  - when the central bank buys government bonds from commercial banks. Cash replaces securities So banks have excess cash reserves.This means that more funds are available for lending. The money supply increases and interest rates decrease. This is expansionary monetary policy
  - sales of government bonds by the central bank have the opposite effect. Reducing cash reserves in commercial banks. This reduces the funds available for lending and the money supply which will tend to cause interest rates to increase. This is contractionary monetary policy
  - In the US `Open Market Operations` by the Federal Reserve is the most commonly used monetary tool to achieve the fed funds rate
- Expansionary Policies like reducing reserve requirements lowering the policy rate or open market purchases seek to increase money supply which hopefully increases aggregate demand and helps
  to raise prices when inflation is too low.
- Contractionary Policies like increasing reserve requirements raising the policy rate or open markets selling of bonds seek to decrease money supply which hopefully decreases aggregate demand and helps to moderate price increases when inflation is too high.
- Central banks have to consider the source of inflation before implementing monetary policies
  - The central bank should determine if it is demand pull inflation or cost push inflation
  - If it is cost push due to higher food or energy prices. The economy is already operating below full employment. In such a situation, a contractionary monetary policy may cause even higher unemployment which is harmful to the economy

#### Monetary Transmission System

- The monetary transmission mechanism refers to the ways in which a change in monetary policy, specifically the central bank's policy rate affects the price level and inflation.
- There are four channels through which a change in a policy rate is transmitted to prices. They are transmitted through their effect on
  - market interest rates
  - asset values (Bonds, equity, real estate)
  - consumer and business confidence
  - currency exchange rates.
- For example, when a central bank increases the policy rate. Its intention is to eventually lower the inflation rate.
  - Firstly raising the policy rate increases the costs for commercial banks to borrow from the central bank and from each other. The bank's short term lending rates will therefore increase in line with the increase in the policy rate. The higher rates will decrease aggregate demand as consumers reduce credit purchases and businesses cut back on investment in new projects
  - Secondly bond prices equity prices and asset prices in general will decrease as the discount rates apply to future expected cash flows are increased. These may have a wealth effect because a decrease in the value of households assets may increase the savings rate and decrease consumption
  - Thirdly an increase in policy rate can hurt consumers and business confidence lowering their expectations for future economic growth. As a result they may decrease their expenditures and investments leading to lower domestic demand.
  - Lastly the increase in domestic interest rates may attract foreign investment in debt securities leading to an appreciation of the domestic currency. This increases the foreign currency prices of exports and can reduce the external demand for the country's export goods.
    - besides the stronger currency. Also makes imports of foreign goods cheaper. This also puts downward pressure on the price level resulting in lower inflation

## Currency Exchange Rates

- An exchange rate is simply the price of one currency in terms of another
- The currency on top is known as the price currency, and the one below is the base currency
  - there are alternative conventions for foreign exchange quotes where the base currency is on top
- the exchange rate is the price of one unit of the base currency in terms of the price currency
- A direct quote is from the point of view of an investor in the price currency country
  - Direct qoute directly help investors calculate the price of a foregin goods in their own currency
- An indirect quote is from the point of view of an investor in the base currency country
- the percentage change in one currency relative to another is only in terms of the base currency
  - It represents the percentage change of buying power of the base currency
  - `1.25 CAD/USD -> 1.2 CAD/USD` means the US dollar has depreciated `4%` relative to Canadian dollor
- Nominal exchange rate is discussed in the above, which is the quoted exchange rate at a point in time
- The real exchange rate takes into account the relative price changes between the two countries from a base period
  - `Real Exchange Rate = Nominal Exchange Rate * CPI of the base currency / CPI of the price currency`
- For a pair of relatively less traded currencies, there may not be an active trade in the pair, a third currency which is commonly exchanged between those currencies can be used for a cross rate calculation
- A spot exchange rate is the currency exchange rate for immediate delivery, which for most currencies means the exchange of currencies takes place two days after the trade
- A forward exchange rate is a currency exchange rate for an exchange to be done in the future, which can be 30/60/90/180 days or one year
  - When a firm buys (longs) a currency forward, it's obliged to exchange a specific amount of the base currency for a specific amount of price currency on a future date specified in the contract
  - A forward exchange rate quote can be expressed as an absolute value
  - Or it can be a relative value which is the number of pips relative to the spot exchange rate
    - e.g. `Spot Exchange Rate + 55 pips`, `1 pip or pts = 0.0001` (4th decimal place)
  - When the forward rate is higher than the spot rate, there is a forward premium. When the forward rate is lower than the spot rate, there is a forward discount
    - `Forward Premium/Discount = Forward Rate/Spot Rate - 1`
    - The result can be annualised based on the length of the contract, `90 days formard premium * 4 = Annual Forward Premium`

# Accounting

- Accounting is called an information system since it measures business activities, processes data into reports, and communicates results to decision makers
- Accural accounting is often used in the financial world
  - When a purchase is made by cash the change take effect immediately
  - When a purchase is made on account, an invoice is created and the amount will be paid on a later day.
    - This amount is referred as account receivable. For the purchaser its the account payable
    - Date is important and also associated with a receivable or payable
    - Four different ways the term “on account” is used in transactions:
      1. Performed services on account means Accounts Receivable increases
      2. Collected on account means Accounts Receivable decreases
      3. Purchased on account means Accounts Payable increases
      4. Paid on account means Accounts Payable decreases
- Business transactions that affect the accounting equation (`Assets` = `Liabilities` + `Equity`) are accounting transactions
- Accounting is a double-entry system that reports the dual effects, giving and receiving, of all business transactions. Each transaction affects at least two (or more) accounts
- Transaction Analysis is performed based on the above basic accounting equation
  1. Determine affected accounts, and classify them (at least two accounts should be affected)
     - Revenues and gains affect retained earnings positively
       - Revenues increases net income, then it increases the ending retained earnings, then it increases the shareholder's equity on the balance sheet
     - Expenses, losses, and dividends affect retained earnings negatively
  2. Determine the amount of change on each affected account
  3. Determine the direction of the change for each account
     - The accounting equation must be balanced after analyzing each transaction

## Debit and Credit

- Expand the basic formula and get all the component that can be categorized as debit and credit:
  - `Assets` = `Liabilities` + `Equity`
  - `Assets` = `Liabilities` + (`Share Capital` + `Retained Earnings`)
  - `Assets` = `Liabilities` + (`Share Capital` + (`Beginning Retained Earnings` + `Net Income` - `Dividends`))
  - `Assets` = `Liabilities` + (`Share Capital` + (`Beginning Retained Earnings` + `Revenue/Gain` - `Expense/Loss` - `Dividends`))
    - Dividends are not considered an expense, because they are a distribution of a firm’s accumulated earnings
  - `Assets` + `Expense/Loss` + `Dividends` = `Liabilities` + `Share Capital` + `Beginning Retained Earnings` + `Revenue/Gain`
  - By definition, any positive value on the left side of the above expanded equation is debit and any positive value on the right side is credit
  - A positive debit can be called a normal debit balance, a positive credit is has a normal credit balance
  - A negative debit is a credit and vice versa
- Transactions are recorded first in the journal, a chronological listing of all the entity’s business transactions. When report journal enties for transactions
  - A logical sequence of steps must be followed when recording transactions: analyze (determine the accounts affected and whether the accounts increase or decrease), apply rules of debit and credit, journalize the entry, and include an explanation
  - For each line of record, transcation name is on the left and the amount is on the right
  - Debit records start with `Dr.`
  - Credit records are indented, and start with `Cr.`
  - For transction includes a pair of debit and credit record, the debit line goes first
  - In total, sum of all debit records alway equals the sum of credit records
- T-accounts (an account) - a way to illustrate account's transaction
  - It keeps track on a certain account with two lines in `T` shape
  - The title is the account name, debit transaction on the left and credit transaction on the right
- Ledger – a group of T accounts. All of the accounts of a business grouped together form a book called the ledger (or general ledger). The correct order of accounts is Current Assets, Long-term Assets, Current Liabilities, Long-term Liabilities, Shareholder's Equity, Revenue, Expenses
  - Posting – the process of copying (transferring) data from the journal to accounts in the ledger
  - Businesses need both a chronological record of transactions (the journal) and a record of each account’s activity and its balance (the ledger). Both are necessary to ensure that data are reported accurately
- Trial balance is a list of all accounts and their balances at a given time (typically at the end of the accounting period)
  - For trial balance, the total debit should equals the total credit
  - Usually, the entries in the trial balance has the same order as the accounts in the ledger
- The current ratio is a liquidity ratio that measures a company's ability to pay short-term obligations or those due within one year
  - `Current Ratio` = `Current Assets` / `Current Liabilities`
  - It measures the current liquidity of the firm
- the quick ratio, also known as the acid-test ratio is a type of liquidity ratio, which measures the ability of a company to use its near cash or quick assets to extinguish or retire its current liabilities immediately
  - `Current Ratio` = (`Current Assets` - `Inventory`) / `Current Liabilities`
  - It measures the company's ability to liquidize immediately
- Typical steps of an accounting cycle: Journal Entries, Posting to Ledger, Trial Balance, Adjusting Entries, Adjusted Trial Balance

## Assumptions & Principles

### Assumptions

- Entity assumption - A business is a separate economic unit
- Continuity (going-concern) assumption - Entity will continue to exist indefinitely
- Time period (periodicity) - Reports are prepared for a certain period only
- Historical cost principle - Assets recorded at purchase price, adjusted for any improvements or aging
- Stable monetary unit assumption - Dollar’s purchasing power is stable over time, same currency without inflation

### Principles

- Revenues Recognition Principles - A revenue should be recognized when
  - The service has been performed or the title of the goods have been transferred to the buyer
  - Risk and reward has been transferred to the buyer
  - The amount is known
  - Collection is reasonably assured
- The Matching Principle
  - Resources consumed to earn revenues in an accounting period should be recorded in that period, regardless of when cash is paid
  - Expenses are recognized when incurred, not when paid
- Example scenarios
  - When a service is provided and the cash transaction is completed:
    - For the seller: cash asset increase, revenue, equity increase
    - For the buyer: expenses equity, cash asset decrease
  - When a service has not been provided and the cash transaction is completed: (installment sales)
    - For the seller: Cash asset increases, Unearned Revenue (Liability) increases
    - For the buyer: Expenses asset increases, cash asset decreases
  - When a service is provided and the cash is not received or paid:
    - For the seller: Accounts Receivable or asset increases, service revenue or shareholder's equity increase
    - For teh buyer: Accounts payable or liability increases, expenses or shareholder's equity decreases
  - When a service is provided and the cash transaction is completed:
    - Not a transcation
