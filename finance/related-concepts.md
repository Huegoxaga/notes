# Quantitative Analysis

- The time value of money (TVM) is the concept that money you have now is worth more than the identical sum in the future due to its potential earning capacity, the time value can be:
  - `Present Value (PV)` is the current value before making the investment
  - `Future Value (FV)` is the future value after making the investment
- `Interest` is the difference between the amount of money lent and the amount of money later repaid
- The `Interest Rate` is the amount charged, expressed as a percentage of the principal, by a lender to a borrower for the use of assets

## Components of Interest Rate

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

## Interest Calculation

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
- When `i` is the market interest rate, i' refers to the real interest rate (inflation-free rate) excluding the effect of inflation rate
  - Given the inflation rate `f` and the market interest rate `i`, `i' = (1+i)/(1+f) - 1`
    - Optionally, `i = i' + f + i'f`
  - the real dollars is the inflation-free dollars and the actual dollar is the cash flow amount used in daily calculation when inflation is not considered

## Depreciation Calculation

- Book value = Cost basis – Depreciation charges made to date
- Straight-Line Depreciation (SLD)
  - Goods depreciate at a constant rate
  - Annual Depreciation Charge = $$d_t=\frac{(B-S)}{N}$$, where B = cost basis, S = salvage value, N = depreciable life
    - Service charges like installation fee should be included in the cost basis
  - Salvage value is the value of a good when its service life is reached
- Declining-Balance Depreciation (DBD)
  - The declining balance method (DBD) of depreciation models the loss in value of an asset in a period as a constant proportion of the asset’s current value
  - Book Value at the end of period n using DBD equals $$P(1-d)^n$$, where `P` is the initial book value, `d` is the constant depreciation percentage, `n` is the number of periods
- The depreciation expense for tax purpose can be referred as the Capital Cost Allowance (CCA)
  - Depreciation charge referred to as capital allowance
  - The maximum capital cost allowance a company can take in one year is what would be sufficient to reduce taxable income to zero
  - the remaining value for all assets under the same CAA class after depreciation is called the Undepreciated Capital Cost (`UCC`)
    - `Opening UCC + additions – disposals – CCA = Ending UCC`
  - Generally, only 50% of a given rate is allowed in the first year of aquiring asset additions
  - Recaptured CCA occurs when an asset is sold for more than the book value, where the market value is higher than the book value estimated by using CCA
    - The difference is taxable income
    - When the market price is higher than original price, that portion is captial gain
  - Loss on disposal occurs when the market value is less than the book value
    - The loss can be a tax benifit
  - When taxation is considered tax rate also applies on loss, tax benefit generated by CCA multiply tax rate
- Net salvage value (`NSV`) - It is the salvage value of the property retired, after deducting the cost of removal
  - `NSV` = $$S(1 – t) + B_dt$$, where `t` is the marginal tax rate, $$B_d$$= book value at disposal
  - If there is a recapture of funds, taxes must be paid
  - If there is a loss, a tax credit is received

## Cash Flow

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
  - The table is uesful when trying to find the interest rate given the factor and the number of period, since `i` can't be solved easily
    - When the interest rate can't be find in the table, or for a more accurate estimation, linear interpolation is often used
    - It makes the assumption that given the same number of periods, the factor and the interest rate has a linear relationship

### Single Cash Flow

- A single cash flow - a lump sum of money, a single disbursement or receipt, it can be measured by:
  - `Compound Amount Factor`, denoted by `(F/P,i,N)`, gives the future amount, `F`, that is equivalent to a present amount, `P`, when the interest rate is `i` and the number of periods is `N`
    - It equals $$(1+i)^N$$
  - `Present Worth Factor`, denoted by `(P/F,i,N)`, gives the present amount, `P`, that is equivalent to a future amount, `F`, when the interest rate is `i` and the number of periods is `N`
    - It is the reciprocal of the compound amount factor
    - It equals $$\frac{1}{(1+i)^N}$$

### Regular Cash Flows

- Regular cash flows, also known as annuity - continous contribution, same amount every time, it can be measured by:
  - `Sinking Fund Factor`, denoted by `(A/F,i,N)`, gives the size, `A`, of a repeated small receipt or disbursement that is equivalent to a large future amount, `F`, if the interest rate is `i` and the number of periods is `N`
    - It equals $$\frac{i}{(1+i)^N-1}$$
    - A sinking fund is an interest-bearing account into which regular deposits are made in order to accumulate some amount
    - To calculate the amount owe after repay the mortgage after a certain period, calculate the future value of the total amount minus the future value of all the repayment at the end of that period
  - `Uniform Series Compound Amount Factor`, denoted by `(F/A,i,N)`, gives the future value, `F`, that is equivalent to a series of equal-sized receipts or disbursements, `A`, when the interest rate is `i` and the number of periods is `N`
    - It is the reciprocal of the sinking fund factor
    - It equals $$\frac{(1+i)^N-1}{i}$$
  - `Capital Recovery Factor`, denoted by `(A/P,i,N)`, gives the value, `A`, of the equal periodic payments or receipts that are equivalent to a present amount, `P`, when the interest rate is `i` and the number of periods is `N`
    - It can be easily derived from the sinking fund factor and the compound amount factor
    - It equals $$\frac{i(1+i)^N}{(1+i)^N-1}$$
    - It is used to find the equivalent regular income required after investing in an asset when the asset loss its value over time
      - `A = (P-S)(A/P,i,N)+S*i`, when `P` is the cost of the equipment and `S` is its salvage value
      - `i` in this scenario is called `cost of capital`
      - Alternativly, Equivalent Uniform Annual Cost can be `EUAC = P(A/P,i,n) – S(A/F,i,n)` or `EUAC = (P – S)(A/F,i,n) + Pi`
  - `Series Present Worth Factor`, denoted by `(P/A,i,N)`, gives the present amount, `P`, that is equivalent to an annuity with disbursements or receipts in the amount, `A`, where the interest rate is `i` and the number of periods is `N`
    - It is the reciprocal of the capital recovery factor
    - It equals $$\frac{(1+i)^N-1}{i(1+i)^N}$$
    - `Capitalized Value` of a series can be obtained by getting the limit of the number of periods `N` to infinity in the in the series present worth factor calculation
  - Time values of regular cash flows can be calculatd by stacking each individual single cash flow with different number of time period together, the calculation can be simplified using the formula for the sum of a geometric series
    - Regular cash flows calculation can have a end mode(default for most calculators) which means the cash flow is added at the end of each time period
    - Regular cash flows calculation can have a begin mode which means the cash flow is added at the beginning of each time period
    - Begin mode will compound the interest one more time at the end
  - An annuity is a contract between you and an insurance company in which you make a lump-sum payment or series of payments and, in return, receive regular cash flows, beginning either immediately or at some point in the future. it can be further categorized as:
    - Annuity Due - regular cash flows, begin mode
      - It can be treated as ordinary annuities which has one less period and count the first payment directly as a present worth. e.g. `P = P1 + A(P/A,i,N-1)`
      - Optionally, Determine the present worth of a standard annuity at time −1 and then find its worth at time 0 (now).
    - Ordinary Annuities - regular cash flows, end mode
    - Perpetuities - regular cash flows, end mode, infinite number of time periods
      - `P = A/i` is known as the capitalized value formula
      - The time value for perpetuities equals payment amount `A` divided by the interest rate `i` for the payment time period
      - For infinite number of time periods the present worth can be: $$P=\lim_{N\to \infty}A(P/A,i,N)=\frac{A}{i}$$
      - `P` in this case called the capitalized value
- For continuous compounding at nominal rate `r` per period
  - Continuous Compounding Sinking Fund: $$[A/F,r,n]=\frac{e^r-1}{e^{rn}-1}$$
  - Continuous Compounding Capital Recovery: $$[A/P,r,n]=\frac{e^{rn}(e^r-1)}{e^{rn}-1}$$
  - Continuous Compounding Series Compound Amount: $$[F/A,r,n]=\frac{e^{rn}-1}{e^{r}-1}$$
  - Continuous Compounding Series Present Worth: $$[P/A,r,n]=\frac{e^{rn}-1}{e^{rn}(e^r-1)}$$
- `Arithmetic Gradient Series` - a series of receipts or disbursements that starts at zero at the end of the first period and then increases by a constant amount from period to period
  - `Arithmetic Gradient to Annuity Conversion Factor`, denoted by `(A/G,i,N)`, gives the uniform annuity equivalent value of gradient component of each cash flow in terms of a equal amount `A`, where `G` is the constant increase in receipts or disbursements per period, the interest rate is `i`, and the number of periods is `N`
    - It has `A` at the end of first period, `A+G` at the end of the second period, `A+2G` at the end of the third period...
    - It equals $$\frac{1}{i}-\frac{N}{(1+i)^N-1}$$
    - There is often a base annuity `A'` associated with a gradient. Hence, the total cash flow equals `A'+G(A/G,i,N)`
      - `A'` equals to the cash flow amount at the end of the first period since there is no G component at that time
      - `A'-G(A/G,i,N)` if `G` is a constant decrease
  - `Arithmetic Gradient to Present Worth Conversion Factor`, denoted by `(P/G,i,N)`
    - It equals $$\left[\frac{(1+i)^N-i\cdot N-1}{i^2(1+i)^N}\right]$$
    - The total present value `P` = `Series Component (A)` + `Gradient Component (G)` = `A(P/A,i,N)` + `G(P/G,i,n)`
- `Geometric Gradient Series` - a series of cash flows that increase or decrease by a constant percentage each period
  - `Geometric Gradient to Present Worth Conversion Factor`, denoted by `(P/A,g,i,N)`, gives the present worth, `P`, that is equivalent to a geometric gradient series where the base receipt or disbursement is `A`, and where the rate of growth is `g`, the interest rate is `i`, and the number of periods is `N`
    - It has cash flows A, A(1 + g), A(1 + g)^2,...A(1 + g)^(N–1) are at the end of periods 1, 2, 3, ..., N respectively
    - The factor equals $$\frac{(P/A,i^{\circ},N)}{1+g}$$ or $$\left(\frac{(1+i^{\circ})^N-1}{i^{\circ}(1+i^{\circ})^N}\right)\frac{1}{1+g}$$ where $$i^{\circ}=\frac{1+i}{1+g}-1$$
      - Demoninator is the series present worth factor using $$i^{\circ}$$
    - $$i^{\circ}$$ is known as the growth adjusted interest rate
    - When $$i^{\circ}$$ is a negative value, the factor table can't be used
    - When `i = g > 0` or $$i^{\circ}$$ is zero, the formula can be simplified as `P = N(A/(1+g))`
    - The cash flow amount at period `i` is $$A_i=A_1(1+g)^{i-1}$$
- When inflation is considered multiply all future cash flow amount by `(1+f)^N` where f is the inflation rate

### Uneven Cash Flows

- Uneven Cash Flows (Non-Standard Annuities and Gradients) - continous contribution, uneven amount every time. There are three methods for dealing with this situation:
  1. Treat each cash flow in the annuity or gradient individually. This is most useful when the annuity or gradient series is not large.
  2. Convert the non-standard annuity or gradient to standard form by changing the compounding period
  3. Convert the non-standard annuity to standard form by finding an equivalent standard annuity for the compounding period. This method cannot be used for gradients
- When calculating cash flow it's critical to determine the entity(e.g. bank or investor) and the outflows and inflows of the cash flows for this entity, use negative sign for outflows and positive sign for inflows

### Cash Flow Analysis

- Discounted Cash Flow is a method to discount all cash flows from its future value to its present value by compounded the discounted rate(interest rate)
- Net Present Value(NPV) is the sum of the discounted present value for all inflows and outflows
- A investment will generates profit if the NPV is positive, the higher the NPV the more profit a investor can gain from it
  - For an independent project, do it when NPV is greater than 0, it means one can make money from it
  - For mutually exclusive projects, select one with the highest NPV
  - For related but not mutually exclusive, combine them into an exhaustive list of `2^n` mutually exclusive sets, then pick one from the set
- Present worth analysis - Net Present Worth = Present worth benefits – Present worth of costs
  - Present worth requires that the analysis is made between equal time periods
  - When the project length is different
    - Repeated Lives Approach - one can find the least common multiple (LCM) of the project length and repeat the projects until they have the same total length
    - Study Period Approach - Adopt specified study period for comparison, realizing need of salvage value at end of period and repeat the project with shorter length once
      - e.g. comparing a 7-year and 13-year project, repeat first project after 7 years and stop it in 3 years for a total of 10 years vs stopping the 13-year project at the end of 10th year
    - For infinite analysis period use the perpetuities formula for the capitalized value or the present worth `P`, it equals `A/i` where `i` is the interest for each period
  - Use annual worth analysis by converting present values and one-time values on the timeline to equivalent uniform values
    - For projects with infinite length, use `A = Pi`
    - For irregular cash disbursements over the analysis period it is convenient to convert them to a present worth cost, rather than using the annual worth cost approach
    - The following factors are useful when calculating the the PW of assets involve infinite tax savings from depreciation, applied with half year rules
      - For non-depreciable costs and revenues simply multiply (1 – tax rate) by itself
      - The PW of capital investment add the tax savings from depreciation equals Capital Tax Factor (`CTF`) multiply by itself
        - `CTF` = `1 – [tax rate * CCA Rate(1 + Interest Rate/2)]/[(Interest Rate + CCA Rate)(1 + Interest Rate)]`
      - The PW of salvaged aseet adding the loss of tax saving by multiply proceeds from disposal by Capital Salvage Factor (`CSF`)
        - `CSF` = `1 – Tax Rate * CCA Rate/(Interest Rate + CCA Rate)`
      - Use after-tax interest rate for the above formulas

#### Rate of Return

- All below comparsions are refer to the investor model where a large initial cost and regular cash inflow (similar to deposit money into saving accounts)
  - For a borrower model, there is a large initial gain and regular cash outflow
  - For the borrower model every comparsion conclusion is opposite from the investor model
- Minimum Acceptable Rate of Return (MARR) uses a interest rate to represent the actual equivalent opportunity cost of an investment
  - It is the minimum rate of return required for any project to be accepted. Other wise, just save the cash in a bank and earn the interest
  - When using `MARR` for present worth analysis, pick the project that yields highest PW value
  - MARR represent the basic rate of return from other invest opportunities
  - When tax is considered during calculation
    - the exact method use the after-tax amount for all cash flows in the `MARR` calculations
    - the approximated method multiply (1 - tax rate) by the `MARR` (before-tax `MARR`) result to get the after tax `MARR`
  - When inflation is considered, `actual MARR = real MARR + f + real MARR * f` where `f` is the inflation rate
    - `actual MARR` is the `MARR` before calculating inflation
    - `real MARR` is the `MARR` after calculating inflation
    - For real projects, perform sensitivity analysis on the profitability of each project with different inflation rates
  - The logic for calculating before/after tax `IRR` and real/actual `IRR`
- Internal Rate of Return (`IRR`) is the interest rate at which the benefits are equivalent to the costs
  - Under present worth analysis, `IRR` makes the `PW` of all cash inflow/outflows equals to zero
  - Under annual worth analysis, `IRR` makes equivalent annual worth of all cash flows equal to zero
  - From an investor perspective, if the IRR exceeds the MARR, the investment is economic. If it is less than the MARR, the investment is uneconomic
  - `PW of benefits – PW of costs = 0` or `PW of benefits/PW of costs = 1` or finding the zero net cash flows by using the annual worth analysis, or compare the future worth at the end of the project
  - $$PW=0=\sum_{t=0}^{T}\frac{R_t-D_t}{(1+i^*)^t}$$, It means the IRR rate $$i^*$$ is a rate that make the sum of the present worth of all net cash flow has a net value of zero
  - `IRR` is usually positive. (otherwise project is losing money)
  - The equation for the `IRR` is solved by trial and error along with linear interpolation or using built-in `IRR` function in Excel or other programs
  - Comparing mutually exclusive alternatives with incremental analysis
    1. Remove all projects with overall IRR lower than the target, sort remaining the projects from the lowest first cost to the highest. Call this lowest first cost the current best
       - Rank by highest first deposit for the borrower model
    2. Challenge the current best with the next most expensive project. During investment, if the incremental investment `IRR` (known as `ΔIRR`) is greater or equal than `MARR`, then make the challenger the current best. If not, calculate the `ΔIRR` with the next challenger
       - `ΔIRR` is the rate of return that will make two project has the same net present worth
    3. Repeat Step 2 until there are no further challengers
  - For independent investment projects, all of them can be chosen if their `IRR`s are greater or equal than the `MARR`s
  - The major advantage of the internal rate of return comparison method is that it facilitates the comparison of projects of different size. It is commonly used
    - Disadvantage is it has multiple solutions sometimes and it is hard to calculate
- The Money Weighed Rate of Return(MWRR) of a investment portfolio is used to see the return rate of this investment, the calculation is the same as calculating `IRR`
- External rate of return (ERR), denoted by $$i^*_e$$ , is rate of return when "excess" cash earns interest at an explicit rate — usually the MARR
  - "excess" cash is not used in the following investment
  - It assumes all unused excess cash uses `MARR` and all investment related cash flow uses `ERR`
    - From an investor perspective, outflow uses `ERR`, inflow uses `MARR`
  - It simplify the cash flows by picking out the "excess" cash flow and combine its future value with other cash flow, so there will be only one sign change in cash flow diagram and it yields only one solution
  - To estimate `ERR`, take net receipts forward at the `MARR` and equating to net disbursements taken forward at the `ERR` rate
    - calculate the interest rate when the future value of each inflows equals the future value of each outflows
    - For investor model, all inflows uses `MARR`, all outflows use `approx ERR`
  - When solving for `IRR`, multiple solutions might happen, then it's a good time to use `ERR`
    - Simple investment often have one solution, it is characterized by one or more periods of cash outflows, followed by one or more periods of cash inflows, because based on the Descartes' rule, there is only one solution
  - `IRR` doesn't differentiate cash flow types and all cash flow uses the same `IRR` for time value conversion
  - `ΔERR` can be used to compare mutually exclusive projects, when `IRR` has multiple solutions
- The Holding Period Return(HPR) is a way to evaluate the performance of a portfolio for each holding period(time period), `HPR = (EndValue+CashFlows)/BeginValue - 1`
  - Begin Values - The balance of the investment account at the beginning of a certain time period
  - End Values - The balance of the investment account at the end of a certain time period including any payouts
  - cash flows - any payouts from the bank
- Time Weighted Rate of Return(TWRR) is the preferred way to evaluate the investment performance, calculated by adding all HPR values by 1(change factor) and find `Nth` root of their product where `N` is the number of HPR values or time period, lastly substruct the final result by `1`
  - It is the geometric mean of the change factors of all HPR values
- For all of the above calculation for return, a nagative HPR means losses, and a positive HPR means gains

#### Payback Period

- It is the number of years it takes for an investment to be recouped
- It equals `First cost / Annual savings`, and disregard all other factors including scrap value
- If annual savings not constant, payback period is computed by deducting each year of savings from the first cost until the first cost is recovered
- the project with the shorter payback period wins
- Payback period of two years is often acceptable
- More than four years is usually unacceptable
- The payback period should not be used as a the sole criterion for evaluating projects

### Asset Replacement Analysis

- Reasons for Replacement
  - Obsolescence - Technology of an asset is surpassed by newer and/or different technologies
  - Depletion - Loss of market value due to consumption or exhaustion of resource
  - Deterioration due to aging - Loss of functionality or efficiency due to the aging process
- Purchasing asset is decision to acquire capacity
  - A capacity cost is incurred when a business or other organization spends money in order to expand operations or increase production capacity
- In asset replacement analysis
  - The existing physical asset is called the defender
  - The potential replacement is called the challenger
- An asset should be replaced by a new one when it reaches its economic life
- Economic life is the number of years that minimizes: EAC(total) = EAC(capital) + EAC(O&M)
  - Generally, the equivalent annual cost (EAC total) is the annual cost of owning, operating, and maintaining an asset over its entire life while the whole life cost is the total cost of the asset over its entire life
  - EAC(capital) is the equivilent annual cost (`EAC`) of depreciation of an asset, `A = (P+I–S)(A/P, i, N) + S*i`
    - `I` is the installations costs
    - `(P-S)` or `(P+I-S)` is known as the capital cost
  - EAC(O&M) is the equivilent annual cost of operating and maintaining, it is usually an increasing arithmetic or gradient series
- Economic life is considering replacing the existing asset with an identical one and this sequence continues indefinitely in the future (the same asset will be used forever), some useful assumptions:
  - The defender /challenger are technologically identical
  - Lives of these identical assets are assumed to be short
  - Relative prices/interest rates are assumed constant
- When challenger is different from defender, challenger repeats and will be continuously used indefinitely
  1. Determine the Economic Life of the challenger and its associated EAC
  2. Determine the remaining Economic Life of the defender and its associated EAC
  3. If the EAC(defender) > EAC(challenger), replace now. Otherwise, do not replace now.
  - For old asset only the EAC of the next year should be checked becuase it will also increase, and the economic life is always the next year
    - This is known as the `One Year Principle`: when annual capital costs will be low in comparison to O&M costs and EAC(total) will be increasing each N, and the yearly operating costs are monotonically increasing, the economic life of the defender is one year and total EAC is the cost of using the defender for one more year
- If the operating costs are not smoothly increasing, a detailed year-to-year comparison has to be conducted

### Benefit-cost Analysis (BCA)

- Mostly used by public sectors
- `Benefit-Cost Ratio` = `Equivalent Worth of Net Benefits` / `Equivalent Worth of Net Costs`
  - `PW Benefits / PW Costs`, `FW Benefits/ FW Costs`, `AW Benefits / AW Costs` all work
  - Only work on the project when the ratio is greater than one
- `Conventional B/C Ratio` = `EW net benefits` / (`EW initial costs` + `EW O&M costs`)
- `Modified B/C Ratio` = (`EW net benefits` - `EW O&M costs`) / `EW initial costs`
- `Net Benefits` = `Expected Benefits` - `Disbenefits`
  - Disbenefits are negatives effects on individuals or groups
- For mutually exclusive project rank project by initial cost, from low to high and eliminate projects that has incremental Benefit-Cost Ratio being less than 1
  - Incremental benefit-cost ratio calculates the ratio between benefit difference over cost difference of two projects
  - Incremental benefit-cost ratio is undefined when the cost different ratio is zero, in those cases choose project with greatest benefits first
  - When cost difference is zero, pick project with lowest costs

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

#### Inflation Calculation

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

## Standards Setting Bodies

- Standards setting bodies are professional not for profit organizations that establish financial reporting standards
- Desirable attributes of standard setting bodies:
  - all parties involved in the standard settings process should observe high professional standards
    - including standards of ethics and confidentiality
  - have adequate authority resources and competencies to fulfill its responsibilities
  - Have clear and consistent standard-setting processes
  - Guided by a well-articulated framework with a clearly stated objective
  - operate independently seeking and considering input from stakeholders but making decisions that are consistent with the stated objective of the framework
  - The decision setting process should not be compromised by pressure from external forces. It should also not be influenced self or special interests.
  - Decisions and resulting standards should be made in the public interest.
- the `International Accounting Standards Board (IASB)` sets Financial Reporting Standards that have been adopted in many countries
  - Widely adopted outside the U.S.
  - It it adopted in Canada by Chartered Professional Accountants of Canada (CPAC) (previously CICA)
    - They publish the CPAC Handbook as Canada's official GAAP
    - Publicly accountable enterprises (PAEs) must apply International Financial Reporting Standards (IFRS) which are standards set by the International Accounting Standards Board (IASB) to enhance the comparability of financial information reported by public enterprises around the world. IFRS was effective January 1, 2011 for Canadian public companies.
    - Private enterprises apply the Accounting Standards for Private Enterprises (ASPE). However, private enterprises have the option of using IFRS or ASPE.
    - Other sets of GAAP are applicable to not-for-profit organizations, pension plans and government entitie
  - The `IASB` establishes the `International Financial Reporting Standards (IFRS)`
  - `IASB` replaced `International Accounting Standards Committee (IASC)` in 2001
    - `IASC` issued the `International Accounting Standard (IAS)`. While some rules from `IAS` is still in use, `IASB` replace some of `IAS` by `IFRS`
- `Financial Accounting Standards Board (FASB)`
  - Widely adopted in the U.S
  - `FASB` establishes the generally accepted accounting principles, known as `US GAAP`

## Financial Reporting Standards

- Standard setters are working to achieve convergence of financial reporting standards
- To keep up to date on the evolving standards an analyst can monitor professional journals and the `IASB` and `FASB` websites, or position papers on financial reporting issues through the CFA Institute Center for Financial marketing integrity
- A financial reporting standard that a country follows is usually called a GAAP(generally accepted accounting principles), each country has its own GAAP or under different names

### IFRS

- Most countries are adopting or planning to adopt `IFRS`

#### Conceptual Framework

- `IASB` set its standards in the `Conceptual Framework (2010) for Financial Reporting`
- The framework is designed to assist:
  - standard setters in developing and reviewing standards
  - preparers of financial statements in applying standards and in dealing with issues not specifically covered by standards
  - auditors in forming an opinion on financial statements
  - users in interpreting financial statement information
- The core of the conceptual framework is the objective to provide financial information about the reporting entity that is useful to existing and potential investors, lenders and other creditors, in making decisions about providing resources to the entity includes:
  - the entities financial position
  - financial performance
  - company's cash flow
- States the overall objective of financial reporting is to provide useful information to users to make investing and lending decisions.
- The framework defines usefulness, the information is useful if:
  - it is Relevant - information should have timely, predictive, value confirmatory value or both
    - Materiality is an aspect of relevance.
    - Note: Consider the conflict between information that is timely (based on estimates) and reliable that may require additional time to ensure accuracy that may render the statements irrelevant.
  - it has been faithfully represented. Such information is complete neutral and free from error.
- There are four characteristics that enhance relevance and faithful representation
  - compatibility - the financial statement presentation is consistent among firms and across time periods
  - verifiability - independent observers will arrive at similar conclusions if they use the same methods
  - timeliness - the information is available to decision makers before it becomes stale
  - understandability - users should be able to readily understand the information the statements present
- The framework defines the reporting elements that should be included
  - financial position mearsuring elements
    - assets
      - resources controlled as a result of past transactions.
      - expected to provide future economic benefits
    - liabilities
      - a result of past events
      - expected to require an outflow of economic resources in the future
    - owners equity
      - Equity is the owner's residual interest in the assets After deducting the liabilities
  - performance measuring elements
    - income
      - an increase in economic benefits, either increasing assets or decreasing liabilities in a way that increases owners equity, includes `comprehensive income`, `revenues`, and `gains`
    - expenses
      - decreasing assets or increasing liabilities in a way that decreases owners equity
      - `losses` are to be included in expenses
- the framework also states that an item should be recognized in the balance sheet or income statement if a future economic benefit from the item is probable and the items value or cost can be measured reliably
  - the amounts at which such items are to be reported depend on the measurement base
    - measurement bases include historical cost a motorized cost current cost realizable value present value and fair value
- the framework states two important underlying assumptions in financial statements
  - accrual accounting - financial statements should reflect transactions at the time they actually occur not necessarily when cash is paid
  - growing concern - assumes the company will continue to exist for the forseeable future
    - If this is not the case then presenting the company's financial position fairly requires a number of adjustments. For example it's inventory or other assets may only be worth their liquidation values
- The framework defines constraint
  - the cost of providing the information
    - optimally benefits derived from the information should exceed the costs.
    - The aim is to achieve a balance between costs and benefits
  - non quantifiable information like reputation brand loyalty and innovation cannot be captured directly in financial statements
- The framework does not address the contents of the financial statements, `IAS No.1` does

#### IAS 1

- The `IAS No.1` defines details like which financial statements are required, Their general features and their structure and content, as:
- Required financial statements
  - balance sheet
  - statement of comprehensive income
    - It can be presented as a single statements or separately as an income statement and a statement of comprehensive income
  - statement of changes in owners equity
  - statement of cash flows
  - notes, summarising accounting policies and disclosing other items
- General features
  - fair presentation - faithfully representing the effects of the entity's transactions and events
  - going concern basis - the financial statements are based on the assumption that the firm will continue to exist
  - accrual basis - it is used to prepare the financial statements other than the statement of cash flows
  - materiality - the financial statements should be free of misstatements or omissions like good influence the decisions of relevant parties, aggregation of similar items and separation of dissimilar items
    - It refers to the relative size of an amount. Relatively large amounts are material, while relatively small amounts are not material
    - When it is material it can depreciate over time. For non material matters, it can be treated as an one time expense
  - No offsetting - No offsetting of assets against liabilities or income against expenses unless a specific standard permits or requires it.
  - Frequency of Reporting - frequency must be at least annually
  - comparative information for prior periods should be included unless a specified standard states otherwise
  - consistency - between periods in how items are presented and classified with prior period amounts disclosed for comparison
- Structure and Content
  - classified balance sheet showing current and non-current assets and liabilities
  - Minimum information is required on the face of each financial statement
    - For example the face of the balance sheet must show specific items such as cash and cash equivalents, plant property and equipment and inventories
  - Minimum specified no disclosures - The standard specifies disclosures about information to be presented in the footnotes
  - This information must be provided in a systematic manner and cross referenced from the face of the financial statements
  - Comparative information for prior period should be included unless a specified standard states otherwise

### US GAAP

- Many aspects of `IFRS` and `US GAAP` have converged over the past decade
- Compare to `IFRS`, `US GAAP` has the following difference:
  - only revenue and expenses are listed as elements related to performance
  - `US GAAP` defines an asset as a resource for which a future economic benefit is expected to flow.
    - The `FASB` defines it simply as a future economic benefit(probable)
  - `US GAAP` allow the upward valuation of most assets, but `FASB` doesn't
  - still disagree on the best treatment of certain items or issues
    - certain business groups place pressures to block any changes in accounting practices that may not be in their best interest
- In many cases however a company will present a reconciliation statement showing what its financial results would have been under an alternative reporting system

## General Assumptions

- Entity assumption - A business is a separate economic unit
- Continuity (going-concern) assumption - Entity will continue to exist indefinitely
- Time period (periodicity) - Reports are prepared for a certain period only
- Historical cost principle - Assets recorded at purchase price, adjusted for any improvements or aging
- Stable monetary unit assumption - Dollar’s purchasing power is stable over time, same currency without inflation

## General Principles

- Financial Reports are prepared based on accural accounting, which recognizes the impact of revenue generating activities on financial statements in the time periods when revenues and expenses accrue
  - Revenue accrues when service is provided and invoice is given regardless whether the payment has been received
  - Different from cash accounting, that recognizes revenues and expenses when cash is either received or paid
  - Required by IFRS and ASPE
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
- Revenues Recognition Principles - A revenue should be recognized when
  - The service has been performed or the title of the goods have been transferred to the buyer
  - Amount to record is the cash value of goods or services transferred to customer
  - Risk and reward has been transferred to the buyer
  - The amount is known
  - Collection is reasonably assured
- The Matching Principle
  - Resources consumed to earn revenues in an accounting period should be recorded in that period, regardless of when cash is paid
  - Expenses are recognized when incurred, not when paid
  - Example scenarios for a transaction
    - When a service is provided and the cash transaction is completed:
      - For the seller: cash asset increase, revenue, equity increase
      - For the buyer: expenses equity, cash asset decrease
    - When a service has not been provided and the cash transaction is completed: (installment sales)
      - For the seller: Cash asset increases, Unearned Revenue (Liability) increases
      - For the buyer: Expenses asset increases, cash asset decreases
    - When a service is provided and the cash is not received or paid:
      - For the seller: Accounts Receivable or asset increases, service revenue or shareholder's equity increase
      - For the buyer: Accounts payable or liability increases, expenses or shareholder's equity decreases
    - When a service is provided and the cash transaction is completed:
      - Not a transcation

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
- Typical steps of an accounting cycle: Journal Entries, Posting to Ledger, Trial Balance, Adjusting Entries, Adjusted Trial Balance

### Adjusting Entries

- Adjustments are additional end-of-period journal entries to update account balances, it involves adding a new entry that reduce part of the normal balance of a previous transcation and add the normal balance of a third account. There are three types of adjustments
  - Prepayments/Deferral
    - `Prepaid Expense` - Recorded as an asset when purchased. Expensed when used or expired
    - `Unearned Revenue` - Recorded as a liability when payment is received. Recorded as revenue when earned
  - Depreciation - Allocates cost of plant assets to expense over useful lives. Represents wear-and-tear and obsolescence
  - Accruals
    - `Accrued Expenses` (unrecorded expenses) - Record expense before paying cash. e.g. Salaries, interest, and income taxes
    - `Accrued Revenues` (unrecorded revenues) - Record revenue before collecting cash. Earned and will collect next period
- It happens for accrual basis accounting, for cash basis there is no need
- The adjusting entry to record depreciation expense is: Debit Depreciation Expense and Credit Accumulated Depreciation
- The next step after adjusting entries is closing the Books
  - Prepares the accounts for next period
  - Sets revenues, expenses, and dividends to zero
- Two types of account are dealt differently during closing:
  - `Temporary Accounts` - They should be closed (e.g. Revenues, expenses, and dividends)
  - `Permanent Accounts` - They shouldn't be closed (e.g. Assets, liabilities, and equity)
- Accounts for closing
  - Close Revenues - Debit each revenue account and Credit retained earnings
  - Close Expenses - Debit retained earnings and Credit each expense account
  - Close Dividends - Debit retained earnings and Credit dividends

## Ratios

### Valuation Ratios

- Price to Earnings(P/E) is the ratio for valuing a company that measures its current share price relative to its per-share earnings (EPS)
  - A lower `P/E` ratio means the stock price is undervalued, which is good
  - `P/E` = `Price of Shares` / `EPS`
    - Earnings per share (EPS) = `Net Income Available to Common Shareholders` / `# of Outshanding Shares`
- The price/earnings to growth ratio (PEG ratio) is a stock's price-to-earnings (P/E) ratio divided by the annual EPS growth rate
  - Any PEG ratio that is smaller than 1.0 is good
- The price-to-sales (P/S) ratio is a ratio that compares a company market cap to its revenue over the past 12 months
- The price-to-book ratio compares a company's market value to its book value, the book value is the total book value of all the shareholders determined when they buy the shares
- Dividend yield is a financial ratio that shows how much a company pays out in dividends each year relative to its stock price
  - this ratio can go up when the stock price drops, since the the pay out amound keeps the same
- The dividend payout ratio is the ratio of the total amount of dividends paid out to shareholders relative to the net income of the company

### Profitability Ratios

- Return on Assets (ROA) an indicator of how profitable a company is relative to its total assets
  - `ROA` = `Net Income` / `Avg. Total Assets`
  - The higher the better
- Return on equity (ROE) is a measure of financial performance calculated by dividing net income by shareholders' equity
  - `ROE` = `Net Income` / `Avg. Total Equity`
- Profit margin is the percentage of sales has turned into profits

### Efficiency Ratios

- Inventory turnover is a ratio showing how many times a company has sold and replaced inventory during a given period
  - It shows how fast the company is selling, important ratio for retail companies
  - `Inventory-turnover Ratio` = `Sales` / `Inventories`
- Asset turnover ratio measures the value of a company's sales or revenues relative to the value of its assets

### Liquidity Ratios

- The current ratio is a liquidity ratio that measures a company's ability to pay short-term obligations or those due within one year
  - The current ratio is the proportion of the amount of current assets which only can be sold in one year divided by the amount of current liabilities
  - The higher the better, should be at least great than 1.0
  - `Current Ratio` = `Current Assets` / `Current Liabilities`
  - It measures the current liquidity of the firm
  - It is greater than one most of the time, so when both `CA`, `CL` decrease for the same amount the ratio increase
- Working Capital - Similar to current ratio but calculate in dollar amount
  - `Wokring Capital` = `Current Assets` - `Current Liabilities`
- the quick ratio, also known as the acid-test ratio is a type of liquidity ratio, which measures the ability of a company to use its near cash or quick assets to extinguish or retire its current liabilities immediately
  - The quick ratio is the proportion of the amount of current assets which only can be sold quickly exclude all the inventory divided by the amount of current liabilities
  - This calculation is more conservative than the current ratio
  - `Quick Ratio` = `Quick Assets` / `Current Liabilities`
    - `Quick Assets` = `Current Assets` - `Inventories` - `Prepaid Items`
  - `Quick Ratio` = (`Cash` + `Account Receivables` + `Marketable Securities`) / `Current Liabilities`
  - It measures the company's ability to liquidize immediately

### Solvency Ratios

- The debt-to-equity (D/E) ratio is calculated by dividing a company’s total liabilities by its shareholder equity
  - `D/E` = `Total Liabilities` / `Avg Total Equity`
  - Better to be less than 1
- The debt-to-asset (D/A) ratio measures ability to pay all liabilities
  - Better to be less than 1
  - Low debt ratio is safer than high debt ratio
  - `D/A` = `Total Liabilities` / `Total Assets`
  - Since it normally less than one, when both terms increase for the same amount the ratio increase
- Interest coverage ratio can be calculated by dividing a company's earnings before interest and taxes (`EBIT`) by its interest expense
  - Lower than `1.0` is not good
- Equity Ratio - extent firm relies on debt
  - smaller the ratio, the more dependent a firm is on debt and the higher the risk of not being able to manage debt
  - `Equity Ratio` = `Total Equity` / `Total Assets`

### Leverage Ratios

## List of Common Accounts

### Assets

#### Current Assets (debit normal balances)

- Cash
- Accounts receivable or A/R
- Notes receivable
- Marketable securities
- Inventory
- Office Supplies or Supplies Inventory
- Prepaid rent
- Prepaid insurance

#### Property, Plant, and Equipment (PPE) (debit normal balances)

- Land
- Building
- Equipment
- Machinery
- Furniture
- Laptops or computer
- Car

#### Long Term Investments (LTI) (debit normal balances)

- Equity investments
- Debt investments
- Bonds receivable

#### Intangibles (debit normal balances)

- Trademark
- Copyright
- Goodwill
- Patent

### Liabilities

#### Current Liabilities (credit normal balances)

- Accounts payable
- Unearned Revenues
- Note payable
- Dividend payable
- Utilities payable
- Rent payable
- Insurance payable
- Advertising payable
- Salaries payable
- Wages payable
- Income tax payable

#### Long Term Liabilities (credit normal balances)

- Bonds payable
- Note payable
- Loan payable

### Equity (credit normal balances)

- Common shares
- Retained earnings
- Accumulated Other Comprehensive Income (AOCI)
- Contributed Surplus

#### Contra Asset (credit normal balances)

- Accumulated Depreciation
- Allowance for doubtful accounts

#### Contra Liabilities (debit normal balances)

- Discount on bonds payable

#### Adjunct Liabilities (credit normal balances)

- Premium on bonds payable

#### Contra Revenue (debit normal balances)

- Sales returns
- Sales allowances
- Sales discounts

#### Contra Expense (credit normal balances)

- Purchase returns
- Purchase allowances
- Purchase discounts

#### Adjunct Revenues (credit normal balances)

- Sales discounts forfeited

#### Contra Equity (debit normal balances)

- Dividends declared
- Cash dividends

### Income Related

#### Revenues (credit normal balances)

- Revenue
- Sales
- Service Revenue
- Dividend Revenue
- Rent Revenue

#### Expenses (debit normal balances)

- COGS (Cost of Goods Sold)
- Rent expense
- Insurance expense
- Utilities expense
- Advertising expense
- Salaries expense
- Wages expense
- Income tax expense
- Interest expense
- Supplies expense
- Depreciation expense
- Amortization expense
- Bad debt expense

## Financial Reports

- Financial reports are published at a regular intervals based on the applicable regulatory requirements
  - financial report are generated by making the use of financial accounting for matters which external to business
  - Parties like investors, creditors, government, customers, asuppliers, employee all can gain valuable info from financial reports
- The reports should be prepared in the following order
  - Income Statement, the net income is calculated first
  - Changes in Equity, the net income from the income statement is required here
  - Balance Sheet, The retained earnings from changes in equity will be used here as a part of the onwers' equity
  - Statement of cash flows, The changes in cash between two balance sheets can be elaborated here
    - The indirect method also needs the net income

### Income Statement

- It accounts the net income of a company for a certain period
  - It has net income or loss of the company at the bottom line of the statement
- `Net Income = Revenue - Expenses + Other Income`
  - `Revenue` - inflows from delivering or producing goods and services and other activities
  - `Expenses` - outflows in the processes of running operations that generates revenue including depreciation of assets and concurrence of liabilities
  - `Other Income` - inflows that is not from the ordinary course of the business
- `Revenue/Expenses` are expected and related to the daily operation of a business
- It shows records of gross profit, tax expenses, interest expenses, or income from operations (EBITDA, Earnings Before Interest, Taxes, Depreciation, and Amortization)
- Income from operations is also called E.B.I.T. (earnings before interest and taxes) or Operating Income (OI)
  - The next line is usually the income tax expense. It is the second last line, right before the bottom line (net income)
- Net income is an estimate. True income can be measured only when business is liquidated
  - Investors cannot wait for business liquidation to learn about true income
- Income Statement Formats
  - Single-step
    - All revenues grouped together
    - All expenses grouped together
  - Multi-step
    - Shows subtotals to emphasize relationships
    - Includes
      - Gross profit
      - Income from operations
      - Income before taxes
      - Net income

#### Comprehensive Income Statement

- It accounts the gains and losses that are excluded from the income statement, e.g.
  - Unrealized gains on losses on investments that are classified as available for sale
  - Foreign currency translation gains or losses
  - Pension plan gains or losses
- `Gain/Losses` are from peripheral activities, and they are unpredictable
- Optionally, comprehensive income statement can combine with net income statement as a `Total Comprehensive Income Statement`

### Changes in Equity

- `Net Changes in Equity` is the amount of the changes in Owner's Equity between two balance sheet from one period to its next
  - It uses an accumulated calculation
- The `Statement of Changes in Equity` is also known as `Statement of Retained Earnings` in U.S. GAAP
  - Retained earnings is portion of net income company has kept over a period of years
- `Net Changes in Equity = Total Comprehensive Income - Changes in Equity(Compare to last period)`
  - `Beginning Retained Earnings + Net Income - Dividends = Ending Retained Earnings`
- It explains the changes in equity
  - e.g. the shareholder transactions like dividend payout, and issurance of common shares

### Balance Sheet

- a snapshot of the firm's financial position on a certain date
  - Also called the `Statement of Financial Position`
- It measures the financial health of a company
- It has three components:
  - Assets - resources owned by the company(e.g. Equipment, Cash)
  - Liability - amount borrowed from others
  - Owner's Equity - it equals `Assets - Liability`
  - Or `Assets` on the left side, `Owner's Equity` and `Liabilities` on the right side
    - The total of these portions must equal
- The owners' equity portion represents the stockholders' ownership of the business assets and residual interest in assets after all liabilities are settled, it consists of:
  - Common stock
  - Contributed surplus
  - Retained earnings
  - Accumulated other comprehensive income (loss)
- Shareholder's Equity is a form of `Net Assets` = `Assets` – `Liabilities`
- Asset must have a certain future benefit, company must have rights to access the future benefits, and they should be quantifiable. Assets include
  - Current assets - Cash and cash equivalents(Accounts receivable), Merchandise inventory, Prepaid expenses
    - Generally, assets are divided into two categories: current and noncurrent assets
  - Long-term assets - Net Property and Equipment (which equals Property and Equipment - Accumulated Depreciation) whose future benefits exceed one year or operating cycle whichever is longer
  - Intangible assets - patent and trademarks
  - Contract assets - negative assets
- Liabilities include
  - Current liabilities: Accounts payable, Taxes payable
  - Long-term liabilities: Long-term debt
- Balance Sheet record asset's book values and changes of value including depreciation
- Current assets can be expected to be converted to cash, sold or consumed in the next year or within the business’s operating cycle (whichever is longer), anything that will be held longer than one year would be considered as long-term assets
- A liability must meet the following four criteria:
  - Past Transactions
  - Promise of Payment
  - Quantifiable
  - Known Date
- Liabilities can be non-monetary, they are the expected cost of goods and services for the money received
  - e.g. Warranty
- Similarily, liabilities have current liabilities and long-term liabilities (anything longer than one year)
- Balance Sheet Formats
  - Report format
    - Assets listed at the top
    - Start with current assets and within current assets list in order of liquidity
    - Liabilities and equity beneath
  - Account Format
    - Assets on the left
    - Start with current assets and within current assets list in order of liquidity
    - Liabilities and equity on the right

### Statement of Cash Flows

- It focuses on the cash
- A disclosure of the use of cash including cash receipts, cash payments, and the net change in cash resulting from the operating, investing, and financing activities of a company during a specific period
  - the net cash flow should matches the changes in balance cash between two balance sheets
  - it evaluates company's liquidity
- It has the purpose of:
  - determines the ability of the company to pay dividends and interest
  - provides information about the cash receipts and cash payments during a period
  - predicts future cash flows
- It reports the difference of liabilities, assets, equity in cash as shown between balance sheets
- The accrual concept is not used in the preparation of a cash flow statement
  - It is the only report that is calculated on a cash basis
- Net cash flows are consisted of three sections: operating, investing, financing (in strict order)
- Exchanges between asset and equity are not cash flows, they are `NIF` (Non-cash Investing and Financing Activities)
  - e.g. borrow cash to purchase, exchange common shares to buildings
  - This info can be included in the footnotes

#### Operation Cash Flows

- Mainly related income statement items, depreciation, gain/loss, changes in current assets, and current liabilities
- Cash from operating activities results from converting net income from the accrual basis to the cash basis
- Cash from operating activities can be calculated using one of two methods and both methods give the same result
  - The indirect method
  - The direct method

##### Direct Method

- It records all records of cash transactions from operating activities
- The following items are calculated
  - Cash collections from customers
    - `Ending A/R = Beg. A/R + Revenues - Collections`
  - Cash payments to suppliers
    - `Ending Inventory = Beg. Inventory + Purchases – COGS`
    - `Ending A/P = Beg. A/P + Purchases – Payments`
  - Cash payments for operating expenses, it equals
    - add increases or substract decreases in prepaid expenses
      - `Ending P/E = Beginning P/E + Payments for P/E – Operating Expenses`
      - `Change in P/E = Payments for P/E – Operating Expenses`
      - `Payments for Operating Expenses = Operating Expenses + Changes in P/E`
    - substract increases or add decreases in accrued liabilities
      - `Ending A/L = Beginning A/L + Operating Expenses – Payments for A/L`
      - `Change in A/L = Operating Expenses – Payments for A/L`
      - `Payments for A/L = Operating Expenses – Change in A/L`
  - Cash payments for interest and income taxes
    - For income taxes - `Ending IT Payable = Beg. IT Payable + IT Expense – Payments for IT`
    - For interest - `Ending Interest Payable = Beg. Interest Payable + Interest Expense – Interest Payments`

##### Indirect Method

- The indirect method begins with net income, then adjusts that number to calculate operating cash flows
  - Its all about remove non-cash elements or items not affecting cash from the net income amount
  - For records (on most revenue and expenses accounts) that are embedded in the calculation of net income, ignore all of them
- Most companies prefer this method because it:
  - is easier to prepare
  - focuses on the differences between net earnings and net cash flow from operating activities
  - reveals less company information to competitors
- Net cash provided by (used for) operating activities equals net income:
  - add Depreciation/depletion/amortization expense (They are expenses not in cash, and they decreased the net income, should be added)
  - substract Gain or add Loss on sale of long-term assets (This gain exists only when comparing with book value, gain increased net income, need to be removed)
  - substract Increases or add Decreases in current assets other than cash (Account receivable does not affect cash, and it increased the net income, so its normal value needs to be substracted)
  - add Increases or substract Decreases in current liabilities (Acount Payables does not affect cash, and it decreased the net income, so its normal value needs to be added)

#### Investments Cash Flows

- mainly related to cash transactions in long-term assets and investments, it equals the sum of:
  - `+` Sales of long-term assets
  - `-` Purchases of long-term assets
  - `+` Sale of investments
  - `-` Purchase of investments
  - `+` Collections of notes receivable
  - `-` Loans to others

#### Financing Cash Flows

- mainly related to cash transactions in long-term liabilities and owners' equity
  - Repurchase stock (cash outflow)
  - Proceeds from long-term debt (cash inflow)
  - Payments to long-term debt (cash outflow)
  - Payments of dividends (cash outflow)
  - Issuing equity or debt (cash inflow)
- It equals the sum of:
  - `+` Issuance of shares
  - `-` Repurchase of shares
  - `+` Borrowing
  - `-` Payment of notes and bonds payable
  - `-` Payment of dividends

### Footnotes

- Footnotes are required for any type of financial reports, it provides additional information about the items presented, for example:
- Basis of preparation
  - Clarification of the fiscal period covered
  - The inclusion of consolidated entities
  - The accounting methods
  - The significant accounting standards and estimates
  - Assumptions and estimates used
- Additional material information
  - Business acquisitions or disposals
  - Legal actions
  - Employee benefit plans
  - Contingencies and commitments
  - Significant customers
  - Sales to related parties
  - Segments of the firm

### MD&A

- Managements Discussion and Analysis(MD&A) can also be an addition section
- It can includes discussion about
  - The nature of the business
  - Past performance
  - Future outlook
  - Effects of inflation and changing prices
  - Off-balance sheet obligations and contractual obligations, such as purchase commitments
  - Accounting policies that require significant management judgment
  - the likely impact of implementing recently issued accounting standards that includes
    - discussion about whether the new standards are applied
    - The material effects on the financial statements or state that they are still evaluating the effects of the new standards
  - Forward-looking expenditures and divestitures
- In the United States, The FCC requires that the management discuss trends and identify significant events and uncertainties for publicly traded companies

## Managerial Accounting

- Managerial Accounting focuses on internal matters for management
- It is an internal process of collecting accounting data for business purposes
- There is no necessity to follow any commonly defined accounting principles. The principles and systems used are entirely at the discretion of the organization
  - The accounting principles from `IASB` and `FASB` only apply to financial accounting
- The internal managerial accounting reports are useful to make the decisions that affect the organization’s daily operations
- It focuses on the relevance while financial accounting focuses on reliance

### Cost Function

- Cost object - it is anything in which a cost can be captured
  - Assignment - the act of applying the cost to the cost object
    - Tracing - A way to assign cost directly
    - Allocation - Any assignment that can't be done by tracing, then cost driver can be used to calculate the cost
- There are constant unit cost, true variable total cost, total fixed cost, fixed cost per unit, step-variable cost, and mixed cost
- Cost Function - it reflects the relationship between production quantity (level of activity) and the cost, each type of cost can have a function to approximate the cost
  - The total mixed cost line can be expressed as an equation: `Y = a + bX` where `a` is the total fixed cost portion and `bX` is the total variable cost portion
- Cost Driver - the conditions that will affect the cost
  - The allocation requires a cost driver
  - The X-axis of cost function
- In most cases, economist's curvilinear cost function can be treated as a linear function within the relevant range by using the accountant's straight-line approximation (constant unit variable cost)
  - Managers use cost estimation to measure a relationship based on data from past costs and the related level of an activity
- Linear methods of cost estimation has two assumptions:
  - Changes in total costs can be explained by changes in the level of a single cost driver
  - Cost behavior can adequately be approximated by a linear function of the activity level within the relevant range
- High Low Method - Use the highest and lowest point on the X-axis to do a linear approximation
  - The limitations are: The highest and lowest points could be outliers, only two data points are considered, only one cost driver, no statistical quality measures
- Least-Squares Regression Method - fit a straight line to the data that minimizes the sum of the squared errors
  - Least-squares regression also provides a statistic, called the `R^2`, which is a measure of the `goodness of fit` of the regression line to the data points
    - `R^2` is the percentage of the variation in total cost explained by the activity
    - `R^2` varies from `0%` to `100%`, and the higher the percentage the better
    - assume an acceptable R-Square is greater than `0.60` or `60%`
    - the selection of model is based on the `R^2` value
  - T-value measures whether the cost and cost driver are related by coincidence
    - A higher T-value means that the relationship is not a coincidence
    - The T-value should be greater than 2
    - There is T-value for the estimated coefficient (slope), and another T-value for the constant portion. If the associated T-value is less than 2 then the estimation for that portion should excluded in the formula
      - e.g. when T-value for coefficient is `1`, the cost function only equals to a constant
    - Use standard error of coefficient or constant if T-value is not given, its the plus or minus range of the coefficient or constant

#### Common Types of Costs

- Unit Variable Cost (`UVC`) - A fixed unit cost
- Total Variable Cost (`TVC`) - The variable total cost calculated from the UVC
- Total Fixed Cost (`TFC`) - A fixed total cost
- Unit Fixed Cost (`UFC`) - A variable unit cost calculated from the TFC, the average unit cost
- Direct materials (`DM`): These are materials that end up in the final product. E.g. wood, glass, iron, plastic.
- Direct labour (`DL`) - also known as touch labour...the labour that produces the product.
  Usually paid per hour or per unit produced. Usually, assembly line workers. Idle Time vs Overtime
  Complication covered later.
- Variable Manufacturing Overhead (`VMOH`) - these are indirect costs that are not part of the final product or
  cannot be economically traced to it e.g. electricity, utilities, indirect labour (see overtime and idle time
  discussion later), indirect material (e.g. glue, paint, nails, lubrication for machine, cleaning supplies)
- Fixed Manufacturing Overhead (`FMOH`) - these are fixed and do not vary based on level of activity e.g. rent,
  property taxes, insurance, manufacturing or production supervisor salaries; deprecation on production
  equipment, etc.
- Variable Selling and Admin costs (`VS&A`) - e.g. sales commissions, packaging, delivery
- Fixed Selling and Admin costs (`FS&A`) - e.g. advertising, sales supervisor salaries, and rent insurance and
  property taxes for the selling function or their portion
- Average cost (or Unit Cost) = `Total Cost / Total Units = [TFC + TVC] / Total Units = UVC + UFC`
- Manufacturing Overhead (`MOH`) - equals `VMOH + FMOH`
- Prime Cost or Direct Manufacturing Cost - equals `DM used + DL`
- Conversion Cost - equals `DL + MOH` or `DL + VMOH + FMOH`
- Total (Manufacturing) Cost - equals `DM + DL + MOH` or `DM + DL + VMOH + FMOH`

#### Categorization of Costs

- Behaviour - Variable/Fixed
  - Variable costs are `TVC`, `UFC`, `DM`, `DL`, `VMOH`, `VS&A`, it changes when the level of production changes
  - Fixed costs are `UVC`, `TFC`, `FS&A`, `FMOH`, it won't change with the production activity
  - Sometimes a cost can be mixed, it has both variable and fixed components in the cost
- Traceability - Direct/Indirect
  - When a cost has a known unit cost and traceable, it is a direct (prime) cost. Otherwise it is an indirect cost
  - Direct costs are `DM`, `DL`
  - Indirect costs are `VMOH`, `FMOH`, `VS&A`, `FS&A`
  - Manufacturing overhead is an indirect cost and it can't be traced directly by the unit number produced, they include:
    - Materials used to support the production process like lubricants
    - Wages paid to employees who are not directly involved in production like maintenance workers or security guards
  - For direct labour cost when there is:
    - Idle time
      - If it is the fault of the company, then it's a indirect labour cost
      - If it's the fault of the client, then it's a direct labour cost
    - Overtime
      - Total overtime pay rate = Regular pay rate + Overtime pay rate
      - If it is the fault of the company: Regular rate portion is direct Labour, overtime rate is indirect labour
      - If it's the fault of the client, then it's a direct labour cost
    - When both idle and overtime happens - Idle time is penalized first for the OT Rate becuase idle is usually the cause of overtime
  - Traceability can be changed based on the cost object
    - For the factory the janitor is direct
    - For the prodect the janitor is indirect
  - Traceability can be changed depends on materiality
    - Some unit cost can be defined but it is just too small and the owner doesn't bother to trace it. Instead a total indirect cost is evaluated
- Function - Product/Period
  - Product(Inventoriable) cost - anythine related to make the product
    - These costs go into the balance sheet as inventory, after shipment the cost of good sold is transferred into income statement as expenses
    - They are `DM`, `DL`, `VMOH`, `FMOH`
  - Period cost - the costs including all selling and administrative costs
    - These costs go directly into income statement as expenses
    - They are `VS&A`, `FS&A`, including any marketing expense and customer service expense

### Costs in Reports

- Cost vs Expense - Cost is an asset on balance sheet, expense reduces net income in income statements

#### Costs in Balance Sheet

- Costs consists of three accounts in the inventory section of the balance sheet
- Raw Materials (`RM`) - Unprocessed goods, this account is managed by the purchase department
  - `Beginning Balance + Purchase of RM – Ending Balance = RM Used`
  - `RM` is blend of `DM` (Direct Material) + `IM` (Indirect Material)
    - `IM` is not calculated here
- Work in Progress (`WIP`) - Goods that is under processes, this account is managed by the factory
  - `Beginning Balance + DM used + DL + MOH – Ending Balance = Cost of Goods Manufactured (COGM)`
  - `Ending Balance - Beginning Balance = Change in WIP`, so `COGM = DM used + DL + MOH – Change in WIP`
  - Keep in mind that `DM Used` comes from the `RM` account
  - `IM used` from the `RM` account is part of the `MOH` in the `WIP` account.
  - `MOH` uses the applied `MOH` if normal costing is used
  - Only accounts for orders that are still in production and has not been moved to the `FG` account
  - For each order in the `WIP` account the total cost is the order's `WIP` + `DM` + `DL`
- Finished Goods (`FG`) - Goods that is ready to be shipped, this account is managed by the marketing department
  - `Beginning Balance + COGM – Ending Balance = Cost of Goods Sold (COGS)`
  - `Ending Balance - Beginning Balance = Change in Finished Goods Inventory`, so `COGS = COGM - Change in FG`
  - `COGM` from `WIP` comes into `FG` account
  - `Cost of goods available for sale (COGAS) = Beginning Balance of Finished Goods + COGM`
  - `COGS` is realized only after the goods is sold and shipped to the customers

#### Expenses in Income Statement

- When shipped the total costs will be shown as `COGS` in the income statement
  - `Gross Profit` or `Gross Margin` (`GM`) equals `Sales Revenue - COGS`
  - `Operating Income (OI) = GM – Period (or Selling & Advertisement) Expenses`
    - Income Tax is calculated based on the `Operating Income`

### Costing Systems

#### Job Order Costing

- Also known as Normal Costing, Direct Costing, Traditional Costing, Absorption Costing, Plant-Wide Rate Costing, Single Rate Costing
- It is required by `GAAP` for external reporting purpose
- Different from average costing, job order costing trace the actual and direct material/labour cost, while average costing evaluates the average cost of a unit using the sum of all direct and indirect costs
- Different from actual costing, cctual costing is a calculation of all accurate costs associated with a project including materials, labor and overhead costs
- Applied on estimatie
- For overhead cost (which is indirect), find a cost driver to allocate overhead
  - e.g. hours in shop for auto repairs
  - `Estimated Overhead Costs` / `Total Estimated Level of Activity (Size of the Cost Driver)` = `Cost Allocation Rate`
  - `Cost Allocation Rate` is also known as `Predetermined Overhead Rate` (`POHR`) or `Overhead Application Rate`
- The allocated cost for each task equals the actual size of the cost driver for each task multiply by `POHR`
  - This allocated cost is known as the `Applied/Charged/Allocated/Assigned Overhead`
  - The calculation of `POHR` is based on the estimation from previous data, the actual activity is based on the end of period data
- By the end of the period, adjustment needs to be made when the actual level of activity and actual overhead cost is ready to use
  - The adjustment happens after transaction is completed, that's why revenue is not certain before period ends
  - When applied overhead is lower than actual overhead, it's called underapplied, adjust it by debiting (increasing) `COGS`, then crediting the same amount on `Manufacturing Overhead`
  - When applied overhead is higher than actual overhead, it's called overapplied, adjust it by crediting (reducing) `COGS`, then debiting the same amount on `Manufacturing Overhead`
  - Adjusting the `COGS` account is the direct method, the proration method split the different into `COGS`, `WIP`, `FG` accounts based on their ending balance of the three accounts
    - Split by the percentage of the end balance of one account out of the sum of the end balance of all three accounts
    - proration method increase all three accounts when underapplied and decrease all three accounts when overapplied
- Job Order Costing is good for:
  - High direct costs, low indirect costs (MOH)
  - Small number of products consuming similar amounts of indirect costs
  - Low non-manufacturing costs (not assigned to cost objects)

#### Activity Based Coasting (ABC)

- All indirect costs including period costs are allocated
- It adpots multiple cost pools and drivers
- ABC is good for:
  - Capital intensive instead of labour intensive, higher indirect costs
  - Increased S&A costs (sales commission, shipping, warranty, etc) that can be traced to individual product or service with better technology
  - Product diversity and customization by customer, utilizing `MOH` at different degrees
  - traditional costing relys heavily on the volumn of units produces, and for above cases it will make high volume over-costed, Low volume complex products under-costed
- ABC is a good supplement to our traditional cost system
- ABC is designed to provide managers with cost information for strategic and other decisions that potentially affect capacity, it is generally more accurate than job order costing
- Firms prefers `ABC` for internal use as a decision making tool
- ABC defines an activity which is an event that causes the consumption of overhead resources
- One activity is related to a group of cost driver, a collection of the cost from the cost drivers forms an activity pool, the size or quantity of the activities in the activity pool is known
- A certain cost driver for an activity cost pool is represented by a percentage
- For each cost driver is shared by one or more activity pool and make up to a total of `100%`
  - Usually the total cost of one cost driver is known, so cost of one activity pool is known, the total cost of all cost driver for a activity pool will be the total cost of that activity pool, then the unit cost of an activity pool (activity rate) equals the total cost for the activity pool divided by the size of the activity
- If the activity rate for each pool is known the total cost for a given scenario is calculated by the sum of the product of the pool volumn involved and their rates
- ABC defines four levels of activity that largely do not relate to the volume of units produced
  - Unit-Level Activity - Activities that are performed each time a unit is produced
    - Examples: DM, DL, sales commission, packaging, shipping
  - Batch-Level Activity - Activities that are performed each time a batch of goods is processed
    - Examples: Placing Purchase Orders, Production Setup Costs, Inspection
  - Product-Level Activity - Activities that are related to a specific product regardless of how many units produced or batches run
    - Examples: Designing & Developing a product, R&D, Licensing, Advertising for a product
  - Facility-Level Activity - Activities that are carried out regardless of which products are produced, how many batches are run, or how many units are produced
    - Examples: Janitorial, Rent, Insurance

#### Process Costing

- It is used for high volumn production for identical products

#### Departmental Costing

- It is used for different departments

#### Joint Product

- It is used for multiple products come out from a single input

#### Dual

- It breaks down the single rate from the job order costing into a fixed rate and a variable rate component

### Cost-Volume-Profit Analysis

- Cost-volume-profit (CVP) analysis is a powerful tool that managers use to help them understand the inter-relationship amongst cost, volume and profit in an organization by focusing on interactions among the following five elements:
  - prices of products
  - volume or level of activity
  - per unit variable costs
  - total fixed costs
  - mix of products sold
- The contribution income statement is helpful to managers in judging the impact on profits of changes in selling price, cost, or volume. The emphasis is on cost behaviour
  - It lists total sales, total variable cost, contribution margin (`CM`), total fix total, and has net operating income as the bottom line
  - Sales, variable expenses, and contribution margin can also be expressed on a per unit basis in the above statement
  - Contribution refers to the amount contributes toward covering the fixed costs
- The relationship among revenue, cost, profit and volume can be expressed graphically by preparing a CVP graph
  - Number of unit sold is on the x-axis, and dollors is on the y-axis. Lines are draw for total expenses and total sales
- Cost structure refers to the relative proportion of fixed and variable costs in an organization
- There are advantages and disadvantages to high fixed cost (or low variable cost) and low fixed cost (or high variable cost) structures
  - An advantage of a high fixed cost structure is that income will be higher in good years compared to companies with lower proportion of fixed costs
  - A disadvantage of a high fixed cost structure is that income will be lower in bad years compared to companies with lower proportion of fixed costs
  - Companies with low fixed cost structures enjoy greater stability in income across good and bad years
- The Basic Assumptions of CVP Model: The CVP model is simplified by the following assumptions:
  - All costs can be resolved into fixed and variable elments
    - CVP analysis requires that all the company's costs, including manufacturing, selling, and administrative costs, be identified as variable or fixed
  - Over the activity range being considered costs and revenues behave in linear fashion
  - The selling prices, total fixed costs, and unit variable costs are known with certainty in advance and will remain unchanged during the period
  - The technology, production methods and efficiency remain unchanged
  - The number of units produced equals the number of units sold. This suggests that there no changes in the level of inventory during the period
    - There are no stock level changes or that stocks are valued at marginal cost only
  - The productivity of workers is constant.
  - For multiple-product analysis, the sales mix is assumed to be known in advance and remains constant during the period
  - The only factor affecting costs and revenues is volume

#### Related Formulas

- `CM` = `Total Sales` - `Variable Costs`
  - This will be used to cover fixed expenses and profit, in the line followed in the contribution income statement
  - Break even happens when CM equals the total fixed costs
  - On a per unit basis, `CM per unit` = `SP per unit` - `Unit Variable Cost`
    - `SP` is selling price
- `CM Ratio` = `CM per unit` / `SP per unit` or `Total CM` / `Total Sales`
  - the unit variable cost ratio equals one minus `CM Ratio`
  - `Increase in CM` = `Increase in SP` × `CM Ratio`
  - `Breakeven Point in sales dollar` = `Fixed Costs` / `CM Ratio`
- `# of unit sold` = (`Fixed Expenses` + `Target Profit`)/`CM per unit`
  - Add tax into consideration, `# of unit sold` = (`Fixed Expenses` + `After Tax Profit`/(`1` - `Tax Rate`))/`CM per unit`
- `Net Income` = `CM per unit` × `# of unit sold above break-even`
- `Sales` = `Variable expenses` + `Fixed expenses` + `Profits`
- `Margin of safety` = `Total sales` – `Break-even sales`
  - The margin of safety is the excess of budgeted (or actual) sales over the break-even volume of sales
  - It can be expressed as a ratio as (`Total sales` – `Break-even sales`) / `Total sales`
  - It can be expressed as a number of unit sold (`Total sales` – `Break-even sales`) / `SP per unit`
- `Degree of operating leverage` = `Contribution margin` / `Net operating income`
  - `% change in Net Operating Income`= `% Changes in Sales` × `Degree of operating leverage`
  - Only works when fixed expenses are unchanged

### Decision Making

#### Cost Terms

- `Relevant Cost` - also called differential cost. It is a cost that differs between alternatives, so it can be relevant in the decision making process, it can be one of the following cost:
  - `Avoidable Cost` - a cost that can be eliminated, in whole or in part, by choosing one alternative over another
  - `Idle Capacity: If Exceeding Capacity` - it is responsible for the increases in the total fixed cost
  - `Opportunity Cost` is the benefit that is foregone as a result of pursuing some course of action
- `Irrelevant Cost` - the opposite of relevant cost, it includes:
  - `Unavoidable Cost` - a fixed cost portion that still incur no matter what decision is made
  - `Sunk Cost or Historical` - Cost incurred in the past can cannot be recovered
  - `Future Cost`- Cost occurs in the future which has no impact on decision making
  - `Accounting or Booking-keeping` - allocated fixed costs including depreciation
  - `Idle Capacity: If Not Exceeding Capacity` - the existing fixed cost already covered this cost
- `Total Cost Analysis` compares the sum all related cost in the business
- `Differential Cost Approaches` only considers the impact on the existing costs after a change is made

#### Non-Routine Decision Making

- Special Orders - A special order on top of existing business model, a decision is required on whether or not to accept it
  - The special order should be accepted if the incremental revenue from the order exceeds its incremental costs
  - `Incremental Revenue` = `Special Order units` x `Special Order price`
  - `Incremental Costs` = `Variable Costs` + `Extra Fixed Overheads` + `Opportunity Cost`
    - `Opportunity Cost` = `# of units exceeding capacity` x `CM per Unit at Regular SP`
  - The extra fixed overheads refers to the `Idle Capacity: If Exceeding Capacity` case of the relevant cost
  - Only consider the `opportunity cost` when max capacity is reached
- Make or Buy (Outsourcing) - When a company is involved in more than one activity in the entire value chain, it is vertically integrated. A decision to carry out one of the activities in the value chain internally, rather than to buy externally from a supplier is called a "make or buy" decision.
  - Only making the product instead of buying when the relevant cost of making is less than the relevant cost of buying
  - RELEVANT COSTS OF MAKING = Variable Cost of Manufacturing (DM, DL and VFOH) + Any increase in specific fixed costs + Any Opportunity cost involved from utilizing the released facilities
  - RELEVANT COSTS OF BUYING = Purchase price + Any direct costs relating to purchasing - Any avoidable Fixed Costs resulting from not making
- Retain or Replace an old asset - Decide if it's time to sale the old asset and buy a better one for production
  - Replace the asset if the total cost of replacing is negative
  - The cost of replacing is calculated as (adding costs and substrcting savings):
    - `+` Purchase cost of new equipment
    - `-` Current Salvage Value of Old Equipment
    - `+` Opportunity cost of lost Terminal Salvage Value of old equipment
    - `-` Terminal Salvage value of New Machine
    - `-` Savings in annual operating costs for remaining life of new machine
    - `+/-` Any other differential costs or benefits
- Keeping or Dropping a Product Line - It involves making changes on an underperformed product line
  - Use differential method to compare total oppertunity costs with the total savings from closing the old production line and then utilzing that line for other purpose
    - Costs of closing includes loss of the revenue from old production lines and additional variable cost of the new production line
    - Savings includes the variable cost of the old produnction line the avoidable fixed costs and the increased revenue of the new prodcution line
  - Make sure only relevant costs are considered, they usually includes variable costs, avoidable fixed costs, opportunity costs
- Utilization of a Constrained Resource - Given a limited resource a decision need to be made to maximize the production of certain goods, so the profit can be maximized, steps for making such decision are as follows:
  1. Calculate the contribution per unit of limiting factor for each product
  2. Rank the products by contribution per unit of limiting factor
     - For example, when time is the limiting factor, then calculate the unit CM per hour and maximize the production of the highest
  3. Produce the maximum that can be sold of the product with the highest contribution per unit of limiting factor.
  4. Repeat for the next best product and so on until the scarce resource is used up

### Budgeting

- A budget is a detailed quantitative plan for acquiring and using financial and other resources over a specified forthcoming time period
  - e.g. set rules to maintain inventory level at end of month based on a percentage of the estimated production amount of the next month
- The act of preparing a budget is called budgeting
- The use of budgets to control an organization's activity is known as budgetary control
- An estimate is done by experts for an area, a forcast is based on certain estimates, and some forcast become the budget
- Controllability - The degree of influence that a manager has over costs, revenues, or related items for which he is being held responsible
- The budgeting process may be abused both by superiors and subordinates, leading to negative outcomes
  - Superiors may dominate the budget process or hold subordinates accountable for events they have no control over
  - Subordinates may build "budgetary slack" into their budgets - set budget on theirs flavor to maximize performance
- Advantages of Budgets
  - Promotes planning, including the implementation of plans
    - Link the budget with strategic analysis for the organization including overall objectives, trends, risks, alternative strategies
    - Promotes coordination and communication among subunits within the company
  - Motivates managers and other employees
  - Apply and influence control
    - Assign responsibilities by allocating resources to managers
    - Set targets and goals
- Provide performance evaluation and feedback criteria
  - Comparing actual performance against a budget is better than comparing this year’s achievements to last year’s results including corrective action
- Short-Term Budgets (1 year or less) deals with Quantities to produce, Quantities to sell, Supplies acquisitions, Financial resources needed
- Long-Term Budgets (more than one year) deals with Forecasts of large asset acquisitions, Financing plans, Research and development plans
- Master Budget (Short-Term Budget Application)
  - Coordinates and summarizes all the financial projections of all the organization’s individual budgets in a single document for a set period of time
  - Includes operating estimates, a cash budget, and pro forma financial statements (balance sheet, income statement, and statement of cash flows)
  - Embraces operating and financing activities and decisions
- Operating Budget - The set of budgets leading to the pro-forma (budgeted) income statement, it involves the following steps:
  1. Prepare the Revenues Budget
  2. Prepare the Production Budget (in Units)
  3. Prepare the Direct Materials Usage Budget and Direct Materials Purchases Budget
  4. Prepare the Direct Manufacturing Labour Budget
  5. Prepare the Manufacturing Overhead Costs Budget
  6. Prepare the Ending Inventories Budget
  7. Prepare the Cost of Goods Sold Budget
  8. Prepare the Operating Expense (Period Cost) Budget
  9. Prepare the Budgeted Income Statement
- Financial Budget - The set of budgets that comprise and lead to the capital budget, cash budget, pro-forma balance sheet and the pro-forma statement of cash flows, it involves the following steps:
  1. Prepare the capital expenditures budget
  2. Prepare the cash budget
  3. Prepare the budgeted balance sheet
  4. Prepare the budgeted statement of cash flows
- Production Budget = Sales budget + Ending Inventory - Beginning Inventory = Total Expected Asset - Total Existing Asset

#### Responsibility Accounting

- Responsibility Accounting - Focuses on information sharing, not in laying blame on a particular manager
- Types of Responsibility Centers
  - Cost - Accountable for costs only
  - Revenue - Accountable for revenues only
  - Profit - Accountable for revenues and costs
  - Investment - Accountable for investments, revenues, and costs
