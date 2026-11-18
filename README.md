# UK-State-Pension-Simulator
Comparison of the current UK Triple Lock Pension policy with a new recently announced policy proposal 


[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jak3rzz/UK-State-Pension-Simulator/blob/main/UKPensionProjectV7.ipynb)

## Project Overview
This is a simulation built using Python to compare the long-term evolution of the UK State Pension under two different policies: the current Triple Lock policy, and an alternative 'New Triple Lock' mechanism. This mechanism is my interpretation of how the pension policy change recently announced by the UK Prime Minister could operate.

The model began as a simple deterministic model and progressed into a Monte Carlo simulation incorporating autoregressive inflation dynamics, inflation-dependent earnings growth, and probabilistic economic shocks.

## Pension Policies
Currently, the UK State Pension rises each year by the largest of the following values: 2.5%, inflation, or average earnings growth.
Because the increase in the pension always takes the highest of these values, the current mechanism can cause the State Pension to grow relative to average earnings over time. This is the 'ratchet' effect, where the value of the pension compounds upwards over time, because increases in the pension's relative value can never be reversed.

The alternative policy involves removing annual earnings growth as a determining factor in pension uprating, but maintains a long-run link to earnings. Therefore, the pension rises each year by the largest of 2.5% or inflation, whilst also not being allowed to fall below a predetermined benchmark relative to earnings.

We simulate both policies under identical economic conditions to compare them.

## Simulation Methodology
The final version of the model uses a Monte Carlo simulation to generate multiple economic outcomes.

The model incorporates:
- **Stochastic inflation:** inflation varies annually around a long-run target of 2%.
- **Inflation persistence:** use of an AR(1) model allows current inflation to be influenced by previous inflation levels.
- **Inflation shocks:** inflation shocks can occur according to a user-defined probability, mean magnitude, and standard deviation.
- **Stochastic earnings growth:** nominal earnings growth varies around a user-defined long-run rate.
- **Earnings response to inflation:** earnings growth also responds to the level of inflation in the previous year.
- **User-defined parameters:** users can adjust the simulation horizon, starting pension index, economic assumptions, and the number of simulations run.

The model records the evolution of pension and average earnings indices, and measures the relative value of each pension policy to earnings.

## Model Output
The final simulator produces: summary statistics for the final pension values, including means, medians, and percentiles; a comparative histogram showing the distribution of final outcomes under both policies; a fan chart displaying the median path and 5th-95th percentile range of relative pension values over time.


## Development History
Earlier versions of the model are available in the previous_versions folder.

Below are the developments made for each version:
- **V1:** simple one period deterministic model to build the foundational code for calculating pension value
- **V2:** introduction of two economic periods to allow the user to vary inflation and earnings over time
- **V3:** inflation and earnings growth are now randomly calculated according to a normal distribution
- **V4:** introduction of random inflation shocks at a fixed probability
- **V4.5:** allowing user to vary the probability at which inflation shocks occur
- **V5:** introduction of inflation persistence so the effect of economic shocks is seen over multiple periods
- **V6:** introducing a relationship between earnings growth and previous-year inflation
- **V6.5:** allowing the user much greater freedom to vary the economic parameters used in the model
- **V7:** introducing a Monte Carlo simulation to analyse the distribution of outcomes under both policies

## Limitations
- This is an illustrative model that allows the user to see potential outcomes, rather than accurately forecast future State Pension payments
- The economic processes used have been simplified, and results depend on user-defined parameters that have not been calibrated to historical data
- The model compares indexed values for pensions and earnings, and not their actual values and true fiscal cost over time











