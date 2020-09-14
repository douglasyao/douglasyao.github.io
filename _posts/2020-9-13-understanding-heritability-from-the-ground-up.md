---
layout: post
title: Explaining heritability from the ground up
---

"Heritability" is a quantity that is central to human genetics, and there is a huge amount of literature aiming to estimate various forms of it. Despite its ubiquity, there also seems to be a dearth of resources that explain what it actually is, and in particular how to interpret it, in a way that is understandable to non-experts. I'm hoping that this blog post can address this. I'll assume that the reader has at least a basic understanding of genetics (for example, you should know what a SNP, or genetic variant, is).

## Textbook definition of heritability

Heritability is the "proportion of variance" of a phenotype in a population of people that can "be explained" by genetic variants. What do these words actually mean?

## Proportion of variance explained

The notion of "proportion of variance explained" is crucial to understanding heritability. We first start with some variable, which we'll call \\(y\\). In our case, this variable will represent some phenotype such as an individual's height. Next, we must define some model that attempts to "explain" \\(y\\) in some way using other variables, which we'll call \\(x_1, x_2,  \cdots, x_k \\). In our case, \\(x_k\\) represents the minor allele count of a given SNP \\(k\\). Thus, we can write our model for \\(y\\) as something like this:

\\[ y = f(x_1, x_2, \cdots, x_k) + \epsilon \\]

What should this function \\(f\\) look like? In the simplest case, it could be a simple additive function of the variables, where we take some linear combination of the \\(x\\)'s. Or, the function could be much more complicated. For now, we won't specify exactly what this function is. Here, \\(\epsilon\\) refers to whatever part of \\(y\\) that cannot be explained by \\(f\\).

Now, how do we quantify how well \\(f\\) explains \\(y\\)?
We do this by quantifying the "proportion of variance explained" as follows:

\\[\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\]

What exactly is going into the numerator and denominator here? We are looking at the variance of various quantities from the above model. Why variance? Well, variance is a sensible way to quantify uncertainty. We can think of \\(Var(y)\\) as the total uncertainty in our phenotype, which is how much uncertainty in our phenotype we would have if we didn't use any model at all. Meanwhile, we can think of \\(Var(f(x_1, x_2, \cdots, x_k))\\) as how much of the phenotype can be "explained" by \\(x_1, x_2, \cdots, x_k\\). Putting that all together, when \\(y\\) represents a given phenotype and \\(x_1, x_2, \cdots, x_k \\) represent SNP minor allele counts, then \\(\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\) is exactly the heritability of the phenotype.

## Narrow sense vs broad sense heritability

We can define \\(f\\) in different ways to give us different flavors of heritability. When we let \\(f\\) represent the best possible _linear_ predictor of our phenotype (in other words, the \\(f\\) that will maximize \\(Var(f(x_1, x_2, \cdots, x_k))\\)) then the resulting \\(\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\) will refer to narrow-sense heritability (denoted \\(h^2\\)). When we let \\(f\\) represent the best possible predictor _period_ (which can be nonlinear), then \\(\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\) will refer to broad-sense heritability (denoted \\(H^2\\)). Finally, when we let \\(f\\) represent the best possible _linear_ predictor of our phenotype but restrict the set of SNPs to a subset of all SNPs (oftentimes this will be a set of SNPs that are "common" in the population of interest), then \\(\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\) will refer to the SNP heritability (denoted \\(h^2_g)\\). You might think that it's hard to learn the best possible predictor of a phenotype, and you'd be correct - but the cool thing is that statistical geneticists have developed methods to reliably estimate \\(\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\) without explicitly estimating \\(f\\).

In practice (particularly in the GWAS era), people tend to work more with \\(h_g^2\\) than \\(h^2\\) or \\(H^2\\). There are a couple reasons why this is the case. Typically, SNP chips used in GWAS measure a small set of common SNPs, which are chosen to be correlated with as many other common SNPs as possible (rare SNPs do not come into the picture since the correlation between rare and common SNPs is guaranteed to be small). From this data, only \\(h_g^2\\) can be estimated, whereas estimation of \\(h^2\\) and \\(H^2\\) requires family or twin data that can be challenging to obtain at large scale. Moreover, given that our goal is often to explicitly estimate \\(f\\) from GWAS data, \\(h_g^2\\) gives us an upper bound on the best possible prediction accuracy (in terms of proportion of variance explained) of our predictor learned from the GWAS data.

Note that it will be the case that \\(h_g^2 \leq h^2 \leq H^2\\). For an example with some concrete numbers, the \\(h_g^2\\) of height (one of the most well-studied human phenotypes) was initially estimated to be around 0.45 ([Yang et al. 2010 Nature Genetics](https://www.nature.com/articles/ng.608)) when including ~300,000 SNPs found on GWAS SNP chips at the time (out of ~10,000,000 total common SNPs), while \\(h^2\\) and \\(H^2\\) have both been shown to be around 0.8 (from twin studies). One interesting phenomenon is that for many phenotypes, \\(h^2\\) is close to \\(H^2\\), implying that the relationship between genotype and phenotype in human populations is quite close to linear. This might contradict our 


## Important things to know about heritability

Although the definition of heritability is pretty straightforward, there are a lot of extra things that should be kept in mind when interpreting heritability.

**(1) Heritability comes very close to causality (much closer than what you might think at first glance)**. Oftentimes when people perform a regression analysis, where they learn some relationship between a dependent variable and one or more independent variables, there is no guarantee of the existence of any causal relationship between the dependent and independent variables (even if the proportion of variance explained by the independent variables is high). This is the classic "correlation does not imply causation" argument. Thus, you might reasonably think that heritability cannot be interpreted as reflecting any sort of causal effect of SNPs on a phenotype.

However, when we specifically have our independent variables represent SNP minor allele count and our dependent variable represent a phenotype in a population of humans, then correlation _DOES_ imply causation (with a few caveats, see below). This fact is quite surprising (at least it was to me when I first learned it), but it makes sense when you think about where our genetics comes from.

First, it's important to understand what exactly leads to correlation \\(\neq\\) causation. The two main


This is probably the single biggest misunderstanding I



(1) Heritabilty is a function of the  Note that in order to have
