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
  - in economic terms the total economic cost includes the full normal market return on all the resources utilized in the business.
  - So when we say a firm does not earn economic profit it doesn't mean that the firm makes no profit at all. Rather it means that the firm is just making normal profit based on its opportunity costs
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
- A perfectly competitive market has a perfectly elastic demand curve. The marginal revenue is equal to the average revenue which is equal to the market price
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
  - Through price discrimination the consumer surplus is reduced and so is the deadweight
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
    - Regulating by marginal cost pricing - it forces the monopolies to reduce price to the point where the firms M.S. curve intersects the market demand curve
      - The market demand curve this further increases output and reduces price but causes the monopolies to incur an economic loss
      - Because price is below `ATC`, a government subsidy is provided in order to provide the firm with a normal profit and prevent it from leaving the market entirely
