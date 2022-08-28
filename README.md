# Rate Lock Analysis

Rate lock is a derivative on fixed rate and adjustable rate mortgages. Fallout functions are specified for various types of rate locks, and depend on several factors including source of rate lock and mortgage type. Like the prepayment models, these fallout functions are based on analysis of historical data and these have a significant impact on the risk measures of these rate locks.

Rate locks are specified using various categories upon origination. Additionally, there is a current status that may change daily during the course of the rate lock. Depending on the category and status of the rate lock, a fallout function is applied. This fallout function is supposed to be a measure of how many of these loans will close at expiry. Like the prepayment functions, these are based on historical observations.

In theory, one could specify a different fallout function based on the many combination of category and status. In practice, a smaller number of fallout functions is actually specified. 

In order to understand the risk profile of a rate lock, we need to determine a valuation model for them. A rate lock can be viewed as a put option on a mortgage. This is because the borrower has the right but not an obligation to sell the mortgage, and whether or not the mortgagee chooses to sell the loan depends somewhat on mortgage price movements.

There are two reasons not to evaluate these options, such as barrier option (https://finpricing.com/lib/EqBarrier.html) using a traditional Black-Scholes formula:

• The returns of mortgage prices are not normally distributed. Mortgage price movements experience compression (lower volatility) as prices rise and decompression
(higher volatility) as prices fall.

• The exercise of the options by the borrower is not efficient. It is in fact given by the fallout functions discussed earlier. If the exercise was efficient, then all locks would close if the market price decreased (higher rates) and none would close if the market price increased.

Conceptually, the valuation of a rate lock is straightforward. For each rate lock (depending on its status and category), we have a specified fallout function as a function of price changes of the mortgage. 

A model for the forward price distribution of the mortgages is needed in order to compute this expectation. In order to do this, we will need to evaluate the mortgage
forward prices together with their volatilities.

There are forward program related to these mortgage driver types, and specific loans are mapped to these forward programs. This allows flexibility to the user as to how specific loans will be sold in the market. This would mean a specific loan can mapped to more than one forward program, and it also allows the user to specify how these decisions are made. 

In order to do so, one needs to decide what the appropriate settlement date would be for a loan (or a rate lock closing on certain date). At the forward program level, the user specifies the time lag (in days) for closed to ready, ready to pooled and pooled to delivered. The total time lag from closed to delivered is then used, and the next available settlement date is used.

In some cases, the first available date for the delivery of a closed rate lock will be past the last provided settlement date (i.e. in the current example, this would be later than 11/2/2003). In this case, we need to extrapolate the forward prices at the later settlement dates. The settlement dates beyond the dates listed in the market data input section are again user defined, and in the case we examined appeared to be set in monthly interval past the last listed settlement date. 





