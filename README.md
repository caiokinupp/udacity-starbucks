# Udacity Starbucks project

## Table of Contents
1. [Overview](#overview)
	1. [Background Information](#bg-info)
	2. [Optimization Strategy](#optmization)
	3. [How To Test Strategy?](#strategy)

2. [Authors](#authors)
3. [License](#license)

<a name="overview"></a>
## Overview

This Project is part of Data Science Nanodegree Program by Udacity.

<a name="bg-info"></a>
### Background Information

The dataset in this portfolio exercise was originally used as a take-home assignment provided by Starbucks for their job candidates. The data for this exercise consists of about 120,000 data points split in a 2:1 ratio among training and test files. In the experiment simulated by the data, an advertising promotion was tested to see if it would bring more customers to purchase a specific product priced at $10. Since it costs the company 0.15 to send out each promotion, it would be best to limit that promotion only to those that are most receptive to the promotion. Each data point includes one column indicating whether or not an individual was sent a promotion for the product, and one column indicating whether or not that individual eventually purchased that product. Each individual also has seven additional features associated with them, which are provided abstractly as V1-V7.

<a name="optmization"></a>
### Optimization Strategy

My task is to use the training data to understand what patterns in V1-V7 to indicate that a promotion should be provided to a user. Specifically, my goal is to maximize the following metrics:

  **Incremental Response Rate (IRR)**
 
IRR depicts how many more customers purchased the product with the promotion, as compared to if they didn't receive the promotion. Mathematically, it's the ratio of the number of purchasers in the promotion group to the total number of customers in the purchasers group (treatment) minus the ratio of the number of purchasers in the non-promotional group to the total number of customers in the non-promotional group (control).

$$IRR = \frac{purch_{treat}}{cust_{treat}} - \frac{purch_{ctrl}}{cust_{ctrl}}$$

  **Net Incremental Revenue (NIR)**

NIR depicts how much is made (or lost) by sending out the promotion. Mathematically, this is 10 times the total number of purchasers that received the promotion minus 0.15 times the number of promotions sent out, minus 10 times the number of purchasers who were not given the promotion.

$$NIR= (10 \times purch_{treat} - 0.15 \times cust_{treat}) - (10 \times purch_{ctrl})$$

For a full description of what Starbucks provides to candidates see the [instructions available here](https://drive.google.com/open?id=18klca9Sef1Rs6q8DW4l7o349r8B70qXM).

<a name="strategy"></a>
### How To Test Strategy?:

After I have an optimization strategy, I have completed the `promotion_strategy` function to pass to the `test_results` function. There are four possible outomes:

Table of actual promotion vs. predicted promotion customers:

|             |Actual |Actual|
|-------------|-------|------|
|**Predicted**|Yes    |No    |
|Yes          |**I**  |**II**|
|No           |**III**|**IV**|

The metrics are only being compared for the individuals we predict should obtain the promotion – that is, quadrants I and II. Since the first set of individuals that receive the promotion (in the training set) receive it randomly, I expected that quadrants I and II will have approximately equivalent participants.

Comparing quadrant I to II then gives an idea of how well my promotion strategy will work in the future.

My IRR and NIR with my developed strategy were 0.0187 and 358.05 respectively, while the original solution (which was provided from the course designer) was with a IRR of 0.0188 and an NIR of 189.45 on the test set.

<a name="authors"></a>
## Authors

* [Caio Kinupp](https://github.com/caiokinupp)

<a name="license"></a>
## License
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)


