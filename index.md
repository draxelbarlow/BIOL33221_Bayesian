---
title       : "Bayesian phylogenetics"
subtitle    : "BIOL33221: Bioinformatics"
author      : Dr Axel Barlow
job         : "email: axel.barlow@ntu.ac.uk, office: IBRC115"
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : zenburn      # {zenburn, tomorrow, solarized-dark, ...}
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
logo        : ntu-shield.png
biglogo     : NTU_open-graph.png
assets      : {assets: ../../assets}
license     : by-nc-sa
---



<!-- adding bold and italic options -->
<style>
em {
  font-style: italic
}
strong {
  font-weight: bold;
}
</style>

## Bayesian phylogenetics

- Bayesian statistics
- Phylogenetic models
- Prior and posterior distributions
- MCMC sampling
- Interpreting results

--- &vcenter

## Introductory video 1

https://www.youtube.com/watch?v=IqMzYTOf6H0&ab_channel=DataCamp

--- &vcenter

## Introductory video 2

https://www.youtube.com/watch?v=FmzgKXV53-w&ab_channel=DataCamp

--- .class #id

## The key points

- Bayesian statistics provide a way of describing our prior knowledge of a system as a probability
- We can then update this `prior probability` by observing some data
- The updated probability is called the `posterior probability`
- Prior and posterior probabilities can also take the form of `probability distributions`
- These allow us to describe a range of probabilites for different values
- More flexible than a single fixed probability value

--- &twocol bg:white

## Probability distributions

- Imagine you want to predict the number of patients arriving at a hospital in the next week
- You have information from previous weeks that allow you to make an estimate
- **But on the Monday...**

*** =left

<img src="assets/fig/unnamed-chunk-1-1.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="100%" style="display: block; margin: auto;" />

--- &twocol bg:white

## Probability distributions

- Imagine you want to predict the number of patients arriving at a hospital in the next week
- You have information from previous weeks that allow you to make an estimate
- **But on the Monday, more patients arrive that you were expecting!**

*** =left

<img src="assets/fig/unnamed-chunk-2-1.png" title="plot of chunk unnamed-chunk-2" alt="plot of chunk unnamed-chunk-2" width="100%" style="display: block; margin: auto;" />

*** =right

<img src="assets/fig/unnamed-chunk-3-1.png" title="plot of chunk unnamed-chunk-3" alt="plot of chunk unnamed-chunk-3" width="100%" style="display: block; margin: auto;" />

--- .segue .dark 

## How does this work with phylogenetics?

--- .class #id

## Bayesian phylogenetic analysis

- The phylogeny is the evolutionary history of the sequences
- We need a `model` of how the sequences evolve
- The model has `parameters` that we can assign prior probabilites to
- The tree `topology`, for example, is a parameter
- We can then observe some data, in the form of a `sequence alignment`
- And calculate the `posterior probabilities` of our model parameters

--- .class #id

## An example phylogenetic model

Parameter|Prior
---------|------
Substitution rate|estimated rate
Tr/Tv ratio|estimated ratio
Base frequencies|estimated frequencies A,T,G,C
Topology|A set of tree topologies
Branch lengths|A set of branch lengths
Population size|A number of individuals

--- .segue .dark 

## Can you compute all those possibilities?

--- .class #id

## Example: tree topology

- We would like to calculate posterior probabilities for all possible tree topologies
- Then select the ones with highest probability

>- How many rooted tree topologies are there?
  + 3 sequences = 3 trees
  + 4 sequences = 15 trees
  + 5 sequences = 105 trees
  + 10 sequences = 34,459,425 trees
  + 53 sequences = 2.7E+80 (> total atoms in universe)

>- **Computing all possible topologies for modest number of sequences is computationally impossible**

--- &twocol

## Markov chain Monte Carlo (MCMC) sampling

*** =left

1. Start at a tree
2. Jump to a nearby tree
3. Compare posterior probabilities
4. New tree > previous tree
  + accept
5. New tree < previous tree
  + accept proportional to difference
6. Repeat (x millions)

*** =right

<img src="./assets/img/uni_trees.svg" title="plot of chunk unnamed-chunk-4" alt="plot of chunk unnamed-chunk-4" width="100%" style="display: block; margin: auto auto auto 0;" />

--- .class #id

## MCMC sampling in practise

>- The initial moves are likely to have low probability
>- This is called `burn in`
>- We rapidly move to a set of parameter values with similarly high probability
>- This is called `convergence` or `stationarity`
>- Sampling the chain at convergence approximates the true posterior distribution
>- This is called the `posterior sample`
>- Since the MCMC steps are not independent, we take 1,000s between every sample
>- And we can verify sufficient sampling using the `effective sample size`

--- &twocol bg:white

## MCMC sampling in practise

Graphically it looks like this

*** =left

<img src="assets/fig/unnamed-chunk-5-1.png" title="plot of chunk unnamed-chunk-5" alt="plot of chunk unnamed-chunk-5" width="100%" style="display: block; margin: auto;" />

*** =right

<img src="assets/fig/unnamed-chunk-6-1.png" title="plot of chunk unnamed-chunk-6" alt="plot of chunk unnamed-chunk-6" width="100%" style="display: block; margin: auto;" />

--- .segue .dark 

## But aren't we also collecting thousands of trees?

--- &twocol bg:white

## Summarising the posterior sample of trees

*** =right

- The *actual* result of the analysis is thousands of trees
- Typically pick one good one, and annotate with clade posterior probabilities
- Other parameters like branch lengths are averaged across posterior sample

*** =left

<img src="./assets/img/panda.svg" title="plot of chunk unnamed-chunk-7" alt="plot of chunk unnamed-chunk-7" width="95%" style="display: block; margin: auto auto auto 0;" />


--- .class #id

## Bayesian phylogenetics

- Bayesian statistics
- Phylogenetic models
- Prior and posterior distributions
- MCMC sampling
- Interpreting results

--- &thankyou

## Next time

**Molecular dating**
