Formative Assessment 4
================

## Item A:

### A geospatial analysis systems has four sensors supplying images. The percentage of images supplied by each sensor and the percentage of images relevant to a query are shown in the following table:

``` r
sensor <- c(1, 2, 3, 4)
supplied_images <- c(15, 20, 25, 40)
relevant_images<- c(50, 60, 80, 85)
```

``` r
data <- data.frame(sensor, supplied_images, relevant_images)
print(data)
```

    ##   sensor supplied_images relevant_images
    ## 1      1              15              50
    ## 2      2              20              60
    ## 3      3              25              80
    ## 4      4              40              85

### What is the overall percentage of relevant images?

``` r
# Solution 1

weighted_contribution <- data$supplied_images * data$relevant_images / 100

op_relevant <- sum(weighted_contribution) / sum(data$supplied_images)

cat("The overall percentage of relevant images:", op_relevant, "or", round(op_relevant* 100, 2), "%\n")
```

    ## The overall percentage of relevant images: 0.735 or 73.5 %

``` r
## The overall percentage of relevant images: 0.735 or 73.5 %
```

``` r
# Solution 2

# using the conditional probability and independent probability:
# let s = supplied_images and r = relevant_images

prob_s <- c(0.15, 0.20, 0.25, 0.40)
prob_r_given_s <- c(0.50, 0.60, 0.80, 0.85)

prob_s_and_r <- sum(prob_r_given_s * prob_s)

cat("The overall percentage of relevant images:",prob_s_and_r, "or", round(prob_s_and_r* 100, 2),"%\n")
```

    ## The overall percentage of relevant images: 0.735 or 73.5 %

``` r
## The overall percentage of relevant images: 0.735 or 73.5 %
```

## Explanation:

Consider the given sensors labeled as S₁ S₂ S₃ and S₄ each has own
percentage of supplied images such that:

$$ P(S_1) = 0.15 $$

$$ P(S_2) = 0.20 $$

$$ P(S_3) = 0.25 $$

$$ P(S_4) = 0.40 $$

In each sensors, each holds the percentages of which images is relevant

$$ p(R_1|S_1) = 0.50 $$

$$ p(R_2|S_2) = 0.60 $$

$$ p(R_3|S_3) = 0.80 $$

$$ p(R_4|S_4) = 0.85 $$

Through the Conditional Probability Theorem, we can determine the
intersection of events between the individual sensors and to its
relevant images it holds;

$$ \text{If } P(B | A) = \frac{P(A \cap B)}{P(A)}$$

$$ \text{Then } P(A \cap B) = P(B | A) * P(A) $$

To determine the total probability of relevant images

$$ \text{Denoting as } P(R) $$

$$ P(R) = P(S_1 \cap R_1) + P(S_2 \cap R_2) + P(S_3 \cap R_3) + P(S_4 \cap R_4)$$

Derive each of the probability of the intersection of events according to
the law of conditional probability:

$$ P(R) = (P(R_1 | S_1)* P(S_1)) + (P(R_2 | S_2)* P(S_2)) + (P(R_3 | S_3)* P(S_3)) + (P(R_4 | S_4)* P(S_4)) $$

Subsitute every values known

$$ P(R) = (0.50 × 0.15) + (0.60 × 0.20) +(0.80 × 0.25) + (0.85 × 0.40) = 0.735 $$

### A geospatial analysis systems has four sensors supplying images. Nevertheless, the relevant images in the overall system would be about 73.5%

## Item B:

<img src="MONFERO_PATAYON - FA4 ITEM 2-1.png" width="100%" /><img src="MONFERO_PATAYON - FA4 ITEM 2-2.png" width="100%" /><img src="MONFERO_PATAYON - FA4 ITEM 2-3.png" width="100%" /><img src="MONFERO_PATAYON - FA4 ITEM 2-4.png" width="100%" /><img src="MONFERO_PATAYON - FA4 ITEM 2-5.png" width="100%" /><img src="MONFERO_PATAYON - FA4 ITEM 2-6.png" width="100%" />
