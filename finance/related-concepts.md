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
