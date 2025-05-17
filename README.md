# Asset pricing

This project aims to price different types of derivative products: European and Asian options, straddles, and interest rate swaps.

We consistently use the Black-Scholes equation. European options are priced using closed-form formulas, while Asian options are priced using Monte Carlo simulations.

We used Dash Plotly to create our application.

## Page 1: Pricing European Options

**Inputs:**

- Underlying: The underlying asset;  
- Type: Call or Put;  
- Maturity: Maturity date. We consider the pricing date as the data retrieval date, i.e., 08/12/2023;  
- S0: Price of the underlying on the pricing date. By default, we use the price on 08/12/2023;  
- Strike: The strike price;  
- Interest rate: The interest rate.

**Outputs:**

- Implied volatility: The implied volatility of the option based on the given inputs;  
- Option price: The price of the option based on the given inputs;  
- Option Greeks: The Greeks of the option based on the given inputs;  
- Greek graphs vs. underlying price: **This graph may take a few seconds to load or update after changing input values. Please be patient.**  
    - Additional inputs: Greek (delta, gamma, vega, theta, or rho), the desired Greek / Min and Max: lower and upper bounds of the price range to consider  
    - Output: Graph of the specified Greek of the option over the selected price range  
- Greek graphs vs. strike: **This graph may take a few seconds to load or update after changing input values. Please be patient.**  
    - Additional inputs: Greek (delta, gamma, vega, theta, or rho), the desired Greek / Min and Max: lower and upper bounds of the strike range to consider  
    - Output: Graph of the specified Greek of the option over the selected strike range  
- Implied volatility: In our approach, we calculated and stored the implied volatilities for each underlying, each strike, and each maturity. This graph represents implied volatility as a function of strike and maturity for the selected underlying.

## Page 2: Pricing Straddles

On this page, we price a straddle, a structured product composed of a call and a put on the same underlying. We assume that the call and put share a common S0 and maturity, but have different strikes.

**Inputs:**

- Underlying: The underlying asset;  
- Maturity: Maturity date. We consider the pricing date as the data retrieval date, i.e., 08/12/2023;  
- S0: Price of the underlying on the pricing date. By default, we use the price on 08/12/2023;  
- Call strike: The strike of the associated call;  
- Put strike: The strike of the associated put;  
- Interest rate: The interest rate.

**Outputs:**

- Implied volatilities: The implied volatilities of the call and put based on the given inputs;  
- Straddle price: The price of the straddle based on the given inputs;  
- Straddle Greeks: The Greeks of the straddle based on the given inputs;  
- Greek graphs vs. underlying price: **This graph may take a few seconds to load or update after changing input values, especially when the price range is wide. Please be patient.**  
    - Additional inputs: Greek (delta, gamma, vega, theta, or rho), the desired Greek / Min and Max: lower and upper bounds of the price range to consider  
    - Output: Graph of the specified Greek of the straddle as the underlying price varies over the selected range  
- Greek graphs vs. Call strike: **This graph may take a few seconds to load or update after changing input values, especially when the strike range is wide. Please be patient.**  
    - Additional inputs: Greek (delta, gamma, vega, theta, or rho), the desired Greek / Min and Max: lower and upper bounds of the strike range to consider for the call  
    - Output: Graph of the specified Greek of the straddle as the call strike varies over the selected range  
- Greek graphs vs. Put strike: **This graph may take a few seconds to load or update after changing input values, especially when the strike range is wide. Please be patient.**  
    - Additional inputs: Greek (delta, gamma, vega, theta, or rho), the desired Greek / Min and Max: lower and upper bounds of the strike range to consider for the put  
    - Output: Graph of the specified Greek of the straddle as the put strike varies over the selected range  
- Implied volatility: In our approach, we calculated and stored the implied volatilities for each underlying, each strike, and each maturity. This graph represents implied volatility as a function of strike and maturity for the selected underlying.

# Page 3: Pricing Interest Rate Swaps

**Inputs:**

- Direction: Pay or Receive.  
  *Pay* when the client buys the fixed rate. The absolute value of the price is then what they must pay in exchange for the contract.  
  *Receive* when the client sells the fixed rate. The absolute value of the price is then what they receive in exchange for the contract.  
- Notional: The notional amount of the contract;  
- Pricing date: The date considered as the pricing moment;  
- Rate index: The index chosen for risk-free rates when using historical rates. The forward rate index is SOFR;  
- Value date: The contract start date;  
- Maturity: The contract's maturity or end date;  
- Fixed leg frequency: We chose to differentiate payment frequencies for fixed and floating legs. This is the fixed leg frequency expressed in months;  
- Floating leg frequency: Frequency of the floating leg payments, in months;  
- Fixed rate: The fixed interest rate.

**Outputs:**

- Bond rates B(t,T) with *t* as the pricing date and *T* as either the value date T1 or maturity date Tn. We distinguish calculations for the fixed and floating legs due to potentially different payment frequencies;  
- Leg values: The values of the fixed and floating legs;  
- Swap price: The difference between the two leg values, with the sign determined by the direction.

## Page 4: Pricing Asian Options

**Inputs:**

- Underlying: The underlying asset;  
- Type: Call or Put;  
- Maturity: Maturity date. We consider the pricing date as the data retrieval date, i.e., 08/12/2023;  
- S0: Price of the underlying on the pricing date. By default, we use the price on 08/12/2023;  
- Strike: The strike price;  
- Interest rate: The interest rate;  
- Simulations: The number of Monte Carlo simulations;  
- Window: The number of business days to consider for calculating the average price. By default, 20 business days correspond approximately to one month.

**Outputs:**

- Historical volatility: The historical volatility obtained using the underlying's price history;  
- Option price: The price of the option based on the given inputs. **This output may take a few seconds to load or update after changing input values, especially with a high number of Monte Carlo simulations. Please be patient.**  
- Option Greeks: The Greeks (delta, gamma, vega) of the option based on the given inputs. Greeks are calculated using the finite difference method. **This output may take a few seconds to load or update after changing input values, especially with a high number of Monte Carlo simulations. Please be patient.** The Greeks are relatively unstable and reflect the limitations of the estimation method, such as convergence issues and significant approximation errors.
