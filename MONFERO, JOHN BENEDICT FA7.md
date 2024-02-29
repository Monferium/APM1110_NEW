
# Formative Assessment 7
The project contains three items, nonetheless, the first item shows that given λ = 4 minutes, how to find the Poisson Distribution if we need λ = 15 seconds. Therefore, the representation of discrete values have been turn into more intervals of data distribution;

## Poisson and Exponential Distributions in R

To comprehend the situation, we will firstly establish the relationship between Poisson and exponential distributions is key to calculating event probabilities over time given the lambda in minutes into lambda in seconds. Here's a detailed breakdown of how they relate and their implementation in R coding.

## Poisson Distribution

The Poisson distribution models the number of events in discrete fixed interval of time or space, with the formula:

$$ P(X = k) = e^{-\lambda} \frac{\lambda^k} {k!}$$

where * λ * is the rate of events.

## Exponential Distribution

Derived from the Poisson process, the exponential distribution describes the time between events, with the cumulative distribution function:

$$ P(T \leq t) = 1 - e^{-\lambda t} $$

## R Implementation

### Task 1: λ = 4 per minute


1. Probability that the time between submissions is at most 15 seconds (0.25 minutes):

Since,

$$ λ_{minutes} = 4 $$

Meaningfully,

$$ λ_{seconds} = 4 * 60 = 240 $$

Consequently,

$$ λ_{15seconds} = 240/16 = 15 $$

Therefore the time *t*
$$t = 15s/(60s/min) = 0.25min $$

Likewise,

$$ λ * t = 4 * 0.25 $$

Then apply the given in the exponential distribution:

$$ P(T \leq t) = 1 - e^{-\lambda t} $$

```r
p_less_15second <- 1 - exp(-4 * 0.25)
p_less_15second
```
p_less_15second = 0.632120558829

---
---
---
2. Probability that the time between submissions is greater than 30 seconds (0.5 minutes):

Reconsider the case of λ = 30 seconds

$$ λ_{30seconds} = 240/8 = 30 $$

Therefore the time *t*
$$t = 30s/(60s/min) = 0.50min $$

Likewise,

$$ λ * t = 4 * 0.50 $$

Then apply the given in the exponential distribution:

$$ P(T > t) = e^{-\lambda t} $$

```r
p_greater_30 <- exp(-4 * 0.5)
p_greater_30
```
p_greater_30 = 0.864664716763

---
---
---
3. Probability that the time between submissions is between 15 seconds and 1 minute:

Notice the case for both λ = 15 seconds and λ = 1 minute

$$ λ_{15seconds} = 240/16 = 15 \hspace{20pt} λ_{60seconds} = 240/4 = 60 $$

Therefore their time in terms of *t_{A} and t_{B}*
$$t_{A} = 15s/(60s/min) = 0.25min \hspace{20pt} t_{A} = 60s/(60s/min) = 1min $$

Finally their possion distribution can be expressed in terms of the difference between two exponential distributions

$$ P(0.25 < T < 1) = e^{-λ * 0.25} - e^{-λ * 1} $$

```r
p_between_15_60 <- exp(-4 * 0.25) - exp(-4 * 1)
p_between_15_60
```
p_between_15_60 = 0.349563802283

---
---
---
### Task 3: λ = 2 per minute

1. Probability of more than two jobs arriving in a minute:

Since no manipulation in time needed, unlike the example Task 1; we may utilize the ppois() function
```r
p_more_than_2 <- 1 - ppois(2, lambda = 2)
p_more_than_2
```
p_more_than_2 = 0.3233236

---
---
---
2. Probability at least 30 seconds will elapse:

```r
p_at_least_30 <- exp(-2 * 0.5)
```
p_at_least_30 = 0.3678794

---
---
---
3. Probability less than 30 seconds will elapse:

```r
p_less_30 <- 1 - exp(-2 * 0.5)
p_less_30
```
p_less_30 = 0.6321206

---
---
---
4. Probability a job will arrive in the next 30 seconds, given none have arrived in the last 30:

```r
p_next_30 <- 1 - exp(-2 * 0.5)
p_next_30
```
p_next_30 = 0.6321206

---
---
---
### Task 7: λ = 15 visits per hour

1. Probability that at least 10 minutes will elapse without a visit:

Since,

$$ P(T <= t) = 1 - e^{λt} $$

If and only if the given would want a visit at least 10 minutes

$$ 1 - P(T <= t) = 1 - (1 - e^λt) = e^λt $$

If we do not want to have visit

```r
p_at_least_10 <- exp(-0.25 * 10)
p_at_least_10
```
p_at_least_10 = 0.082085

---
---
---
2. Probability that less than eight visits will occur in any hour

Since no time manipulation must be done in the lambda expression in terms of hours, we may utilize the ppois() function

```r
# Given lambda for task 7 is 15 visits per hour
lambda_per_hour <- 15

# Probability that in any hour, there will be less than eight visits
# We use the CDF of the Poisson distribution up to 7 visits (since we want less than 8)
probability_less_than_eight <- ppois(7, lambda_per_hour)

probability_less_than_eight
```
probability_less_than_eight = 0.01800219
