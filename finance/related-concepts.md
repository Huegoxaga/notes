# Related Concepts

## Time Value of Money

- The time value of money (TVM) is the concept that money you have now is worth more than the identical sum in the future due to its potential earning capacity, the time value can be:
  - Present value(PV) is the current value before making the investment
  - Future value(FV) is the future value after making the investment
- The interest rate is the amount charged, expressed as a percentage of the principal, by a lender to a borrower for the use of assets, it is consisted of the following components:
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
- If the time period of an interest rate is not spcified, it is an annual interest rate
- A cashflow means a certain amount of money, usually used for making investment, it can be:
  - A single cashflow - a lump sum of money
  - Regular cashflows - continous contribution, same amount every time
  - Uneven cashflows - continous contribution, uneven amount every time
- Simple interest only uses the original pricipal to calculate interest for the next time period
- Compound interest will include the interest earned from previous time period to calculate the interest for the next time period
  - `FV=PV(1+r)^N` where `r` is the interest occurs during the time period and `N` is the total number of time periods
  - If interest `r` for a certain time period is divided from annual interest `R` by `n`, if there are `n` time periods each year
  - The more frequent the rate of compounding the higher the interest the investor can get
  - The Effective Annual Rate(EAR) is the total annual interest rate after compounding, `EAR=((1+r)^N)-1`
- Continuous compound has the compound frequency set to infinite
  - Then, `FV = PV*e^(rN)` and `EAR=e^r-1` where `r` is the stated compound rate and `N` is the stated number of time period for the stated rate
  - Continuous compound yields the highest interest one can get from compounding, given the same interest rate
- Time values of regular cashflows can be calculatd by stacking each individual single cashflow with different number of time period together, the calculation can be simplified using the formula for the sum of a geometric series
  - regular cashflows calculation can have a end mode(default for most calculators) which means the cashflow is added at the end of each time period
  - regular cashflows calculation can have a begin mode which means the cashflow is added at the beginning of each time period
  - Begin mode will compound the interest one more time at the end
- For uneven casflows calculation each cashflow separate then add them together
- Annuity - An annuity is a contract between you and an insurance company in which you make a lump-sum payment or series of payments and, in return, receive regular cashflows, beginning either immediately or at some point in the future. it can be further categorized as:
  - Annuity Due - regular cashflows, begin mode
  - Ordinary Annuities - regular cashflows, end mode
  - Perpetuities - regular cashflows, end mode, infinite number of time periods
    - The time value for perpetuities equals payment amount divided by the interest rate for the payment time period
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

## Statistics Concepts

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

## Economics

### Demand and Supply Analysis

- Target of the demand and supply analysis can be either the market or the firm
- The demand curve of the market is downward sloping and the supply curve is upward sloping and the curve slopes upwards, the intersaction point represent the market price and demand
- The demand curve of the market depends on the types of market it is in, and the supply curve is the `MC` curve above the shutdown level
- One demand or supply curve in a graph can only depict the market condition in a short run, in a long run the curve can shift in all directions accordingly, e.g.:
  - When more firms are joining the market in a long run the supply curve will move down, which is a result of supply increase and price drop, and vice versa
  - when there is an increase in demand, market demand curve shifts upwards and to the right, makes the market price higher and vice versa

#### Demand Analysis

- Demand Curve has quantity demanded on the x-axis and the price of the item on the y-axis
  - Quantity demanded represents the comsumer's intention to buy
- The demand function - quantity demanded equals a constant plus the Own-Price coefficient times Own-Price value plus Cross-price elasticity coeffiecient times Cross-price value plus income coeffiecient times income value
  - The quantity demanded is associated with a period, e.g. the demand for 15 apples in a month
  - The quantity demanded is associated wiath a specific group of consumers (e.g. low-income)
- For all the following elasticity, when the absolute value is above 1, it is elastic. When it is less than 1, it is in elastic
  - A high elasticity will greatly effect the demand
- The law of demand - conditional on all else being equal, as the price of a good increases, quantity demanded will decrease; conversely, as the price of a good decreases, quantity demanded will increase

##### Own-Price Elasticity of Demand

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

##### Cross-price Elasticity of Demand

- the percentage change in quantity demanded for every percentage change in price of the related good
- the cross price elasticity is positive when the related good is a substitute
- the cross price elasticity is negative when the related good is a compliment
- Cross-price coefficient multiple by the cross-price value and divided by the total quantity demand will return the cross-price elasticity
- When the price of a goods drops while all its substitutes' price keep the same, the demand for that goods will increase this is called a positive substitute effect

##### Income Elasticity of Demand

- the percentage change in quantity, demanded for every percentage change in income level
- Normal goods are those in which the demand increases with consumer income levels and vice versa, the income elasticity is therefore positive for normal goods
- Inferior goods(goods that save budget) are those for which the demand decreases with consumer income levels, the income elasticity is therefore negative for inferior goods.
- Income coefficient multiple by the income value and divided by the total quantity demand will return the income elasticity
- When there is a positive change in real income (purchasing power) due to prices drop on some goods, the demand for normal goods will increase and it is called a positive income effect, inferior goods will result in a negative income effect
- For an inferior good, when the negative income effect outweights the positive substitute effect, it is called a Giffen good, the demand curve of this good will be an upward sloping straight line
  - It is a exception to the law of demand
  - only in theory, there are some rare instances where this has turned out to be true
  - another exception where the demand curve is upward sloping is the Veblen good for which a higher price makes the goods more desirable. This is usually the case for some luxury goods like Hermes bags where the higher price conveys higher status to the owners. It only applies to a select group of people who can afford it and there has to be a limit to it

#### Supply Analysis

##### The Law of Diminishing Marginal Returns

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

##### Breakeven and Shutdown Analysis

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

##### Economies and Diseconomies of Scale

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

### Market Structures

- Market Structures are determined by examining the following five characteristics of the industry

| Characteristics                 | Perfect Competition   | Monopolistic Competition                  | Oligopoly                                           | Monopoly             |
| ------------------------------- | --------------------- | ----------------------------------------- | --------------------------------------------------- | -------------------- |
| The number and sizes of sellers | Many firms            | Many firms                                | Few firms                                           | Single seller        |
| Barriers to entry or exit       | Very Low              | Very Low                                  | High(economies of scale lead to big size)           | Very high            |
| Products differentiation        | Identical Products    | Different in quality, features, marketing | good substitutes or differentiated                  | No close substitutes |
| The nature of competition       | Compete on price only | Price and product difference              | Price and product difference                        | Little competition   |
| The pricing power of the firms  | None                  | Limited based on perceived differences    | limited if less differentiate or Significant if not | Significant          |

#### Perfect Competition

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

#### Monopolistic Competition

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

#### Oligopoly

- It is where a few firms compete in a variety of ways
- Firms need to consider other firms'(interdependent firms) strategy
- Demand is also downward sloping but can vary in elasticity, in general firms (Automobile Industry) that are very differentiated from itself to others tend to have more elastic demand than firms with less differentiation (Telco industry)
- An oligopoly market has higher barriers to entry due to economies of scale
- The level of differentiation can vary from good substitutes to high differentiation depending on the industry, this affects the level of pricing power
  - If the level of differentiation is high firms enjoy significant pricing power
- The key distinguishing feature of oligopoly markets is that the firms are interdependent
  - Actions of one company affect not just its own demand curve but also other competitor's, same goes for the price changes
- Oligopoly models has four types of models, each is under a serial of assumption

##### Kinked Demand Curve Model

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

##### Cournot Model

- The model considers an oligopoly with only two firms competing and both have identical and constant marginal costs of production
- Each firm knows the quantity supplied by the other firm in the previous period and assumes that the supply will not change in the next period
- In this model the combined equilibrium output will return a market price based on the market demand curve
  - this price output combination of the market is known as the Cournot equilibrium
  - This price will be much higher than the market price in a perfect competition market which is the same as the marginal costs
  - This price will be close to but smaller than the max market price in an unregulated monopoly market
  - As more firms join the market the outputs and price equilibrium positions move toward the competitive equilibrium

##### Nash Equilibrium

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

##### Dominant Firm Model

- This model has a dominant firm in the market
  - It is a single firm that has a significantly large market share because of its greater scale and lower cost structure
  - The market price is essentially determined by the dominant firm and the rest of the firms are price takers
- The demand curve of the dominant firm is slightly below the market demand curve
  - the quantity supplied by the other firms decreases at lower prices, it means the dominant firms demand curve is even closer to the market demand curve when its price is low, and its supply is high
- Based on this demand curve and its associated marginal revenue curve, the firm will maximize profits at the production level where its `MR` is equal to `MC`, this point determines the market price
- The marginal cost curves of other firms are likely higher than that of the dominant firm, the quantity demanded for these firms is determined by the intersaction point between its `MC` curve and the market price

#### Monopoly

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

### GDP

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
- The `Aggregate Output` of an economy is the value of all the goods and services produced
  in a specified period of time
  - The output from factories
- The `Aggregate Income` of an economy is the value of all the payments earned by the suppliers of factors used in the production of goods and services
  - The income of factory workers
- The value of the output produced must eventually accrue to the factors of production, so `Aggregate Output` and `Aggregate Income` within an economy must be equal
  - All workers use income to purchase goods and services produced from all factorys
- The `Aggregate Expenditure` is the total amount spent on the goods and services produced in the domestic economy during the period
  - The workers income spent on all domestic goods and services
- `Gross Domestic Product` (`GDP`) is formally defined as the total market value of the goods and services produced in an economy within a certain time period
  - By definition the `GDP` is the aggregate output of the economy for the period
  - As a result, in an isolated economy, `GDP`, `Aggregate Output`, `Aggregate Income`, and `Aggregate Expenditure` should all have the same value
- GPD can be calculated by getting the value of `Aggregate Output`, and `Aggregate Income`
  - `Expenditure Approach` - `GDP` is calculated as the total amount spent on the goods and services produced within the economy during a given period
    - It calculates total expenditures in the economy as the `consumption spending by households` plus `business investment` plus `government spending` plus the `net exports`
    - Market analysts generally prefer the expenditure approach because expenditure data is more timely and reliable than data for the income components
  - `Income Approach` - `GDP` is calculated as the total amount earned by households and companies in the economy, it uses the sum of:
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
- `GDP` calculation criteria
  - all goods and services included in the calculation must be produced during the measurement period
    - `GDP` is usually measured in one calendar year but many governments do give annualized quarterly estimates
  - The second criteria is not the goods or services value can be determined by being sold in the market, non-market, illege activities or government benefits are excluded
  - When using the expenditure approach only the market value of final goods and services should be included, the value of intermediate goods like raw materials and parts should be excluded
    - This type of expenditure approach is called the value of final output method
    - An alternative approach is the sum of value added method which is to sum up all the value added during the production and distribution processes
- `Nominal GDP` of the economy are calculated using the current market value of the goods and services
  - `Nominal GDP` equals the sum of all the current prices multiplied by the quantity produced for each good in a certain period
  - As the growth in `Nominal GDP` will include the effect of price increase (inflation) for the period, this figure is not representative of the actual production growth
- Real GPD is calculated relative to a base year by using base year prices and current year output quantities
  - For base year, `Real GDP` is the `Nominal GDP`, the current year `Real GDP` is the sum of the product of prices from the base year and output quantities of this year for all goods and services, then compare the `Real GDP` of the two year to get a relative increases
  - `Real GDP` growth reflects only increases in total output
  - Per capita `Real GDP` is defined as `Real GDP` divided by population
- the `GDP Deflator` is a price index that can be used to convert `Nominal GDP` into `Real GDP`
  - It equals the `Nominal GDP / Real GDP * 100` for a certain year
  - If the `GDP Deflator` index is known the conversion between `Nomial GDP` and `Real GDP` can be done easily
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

#### The IS (Investment vs Savings) Curve

- it plots the `goods market equilibrium` for real interest rate against real income
  - Baed on the economic flows, lower interest rates tend to decrease `Businesses & Households Savings` and increase `Business Investment`, in order to maintain the equilibrium in the goods market. Income must increase. Greater income can increase savings which increases `Businesses & Households Savings` and decrease `Business Investment`
    - Otherwise, tax or imports need to be incresed
- the relationship between real interest rates and real income has to be inverse to maintain equilibrium
- so the `IS` curve is downward sloping

#### LM (Liquidity vs Money) Curve

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

#### Aggregate Demand Curve

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

#### Aggregate Supply Curve

- It shows the amount of output that all the domestic producers are willing to provide at various prices level
- Similar to the aggregate demand curve, but from the producers's point of view, it also has price level on y-axis and quantity of real output on x-axis
- The very short, short, and long run aggregate supply curves are different because they depend on the how input prices like wages material costs and rent respond to changes in production levels

##### Very Short-Run Aggregate Supply Curve

- It is assumed that the input prices remain fixed regardless of changes in production levels
- Companies can increase or decrease output to some degree without changing price
- It is a horizontal line, a perfectly elastic supply curve
- The following very short term production increasing methods are available without increasing the unit cost of each unit produced
  - increasing overtime hours
  - maximizing the existing plant and equipment
  - depleting existing stockpile of components

##### Short-Run Aggregate Supply Curve

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

##### Long-Run Aggregate Supply Curve

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

#### Equilibrium

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

#### Economic Growth

##### Five Sources of Economic Growth

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

##### Growth in Potential GDP

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
