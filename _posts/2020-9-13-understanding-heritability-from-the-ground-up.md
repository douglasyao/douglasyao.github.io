---
layout: post
title: Introduction to heritability (1/2)
---

"Heritability" is a quantity that is central to human genetics, and there is a huge amount of literature aiming to estimate various forms of it. You've probably seen people define heritability as something like "how well genetics accounts for differences in phenotypes in people" or "the degree of variation in a phenotype that is due to genetic variation" but these definitions are quite vague in my opinion. In a series of blog posts, I'll define heritability and describe how to interpret it in a concise way that is (hopefully) understandable to non-experts, though I think this guide will be most useful to people who already know a bit about GWAS and human genetics.

## Textbook definition of heritability

Heritability is the "proportion of variance" of a phenotype in a population of people that can "be explained" by genetic variants. What do these words actually mean?

## Proportion of variance explained

The notion of "proportion of variance explained" is crucial to understanding heritability. We first start with a group of individuals. For each individual, we measure some phenotype, which we will refer to as \\(y\\). Next, we must define some model that attempts to "explain" \\(y\\) across individuals in some way using other variables, which we'll call \\(x_1, x_2,  \cdots, x_k \\). In our case, \\(x_k\\) represents the minor allele count of a given SNP \\(k\\). Thus, we can write our model for \\(y\\) as something like this:

\\[ y = f(x_1, x_2, \cdots, x_k) + \epsilon \\]

What should this function \\(f\\) look like? In the simplest case, it could be a simple additive function of the variables, where we take some linear combination of the \\(x\\)'s. Or, the function could be much more complicated. For now, we won't specify exactly what this function is. Here, \\(\epsilon\\) refers to whatever part of \\(y\\) that cannot be explained by \\(f\\).

Now, how do we quantify how well \\(f\\) explains \\(y\\) across individuals? We do this by quantifying the "proportion of variance explained" as follows:

\\[\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\]

Here, we are looking at the variance of various quantities from the above model. We can think of \\(Var(y)\\) as the total uncertainty of our phenotype in our population of individuals, which is how much uncertainty in our phenotype we would have if we didn't use any model at all. Meanwhile, we can think of \\(Var(f(x_1, x_2, \cdots, x_k))\\) as how much of the phenotype can be "explained" by \\(x_1, x_2, \cdots, x_k\\). Putting that all together, \\(\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\) represents the total fraction of uncertainty in our phenotype that can be explained by our model. When \\(y\\) represents a given phenotype and \\(x_1, x_2, \cdots, x_k \\) represent SNP minor allele counts, then \\(\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\) is exactly the heritability of the phenotype.

Why do we look at variance? Well, variance is a sensible way to quantify uncertainty. We don't _have_ to quantify uncertainty using variance, but for our purposes it is convenient.

## Different flavors of heritability

We haven't done the most important thing yet: define \\(f\\)! It turns out that we can define \\(f\\) in different ways to give us different flavors of heritability. When we let \\(f\\) represent the best possible _linear_ predictor of our phenotype (in other words, the linear function that will maximize \\(Var(f(x_1, x_2, \cdots, x_k))\\)) then the resulting \\(\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\) will refer to narrow-sense heritability (denoted \\(h^2\\)). When we let \\(f\\) represent the best possible predictor _period_ (which can be nonlinear), then \\(\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\) will refer to broad-sense heritability (denoted \\(H^2\\)). Finally, when we let \\(f\\) represent the best possible _linear_ predictor of our phenotype but restrict the set of SNPs to a subset of all SNPs (often this will be the set of SNPs on a given genotyping chip which are "common" in the population of interest), then \\(\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\) will refer to the SNP heritability (denoted \\(h^2_g)\\). You might think that it's hard to learn the best possible predictor of a phenotype, and you'd be correct - but the cool thing is that statistical geneticists have come up with clever ways to reliably estimate \\(\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\) without actually explicitly estimating \\(f\\) (using methods such as Haseman-Elston regression, variance component analysis, LD score regression, etc.). There are a myriad ways to estimate heritability, and they all come with their own set of assumptions and pros/cons, but I think it would be out of scope to discuss them in this blog post. Just know that statistical geneticists have tried hard to make sure these assumptions are reasonable.

One benefit of restricting \\(f\\) to be linear is that heritability becomes exactly equivalent to a quantity that many people are familiar with, namely \\(R^2\\). Many of us can picture what an \\(R^2\\) of 0, 0.5, or 1 look like in a simple linear regression setting (one independent variable). Now, just imagine that we have a linear model where the dependent variable is our phenotype and the independent variables are minor allele counts for each SNP respectively. When this linear model is the best possible out of all other linear models, then the \\(R^2\\) from this model will equal \\(h^2\\).


## \\(h_g^2\\) in the GWAS era

When people talk about heritability as the total contribution of genetics to a phenotype, they will usually be referring to \\(h^2\\) or \\(H^2\\). However, in the GWAS era, \\(h_g^2\\) often comes up more than \\(h^2\\) or \\(H^2\\). This is probably in part because \\(h_g^2\\) can be estimated from GWAS data, whereas \\(h^2\\) and \\(H^2\\) can only be estimated from family or twin data (of which there is not a great amount). To elaborate a bit on why we can only estimate \\(h_g^2\\) from GWAS data: SNP chips used in GWAS only measure a small set of common SNPs, which are chosen to be correlated with as many other common SNPs as possible (rare SNPs do not come into the picture since the correlation between rare and common SNPs is guaranteed to be small). A SNP chip might contain around ~500,000 common SNPs, out of ~10,000,000 total common SNPs and >100,000,000 total SNPs (including rare SNPs). Thus, from this data, we can only estimate the proportion of phenotypic variance that can be explained by the 500,000 genotyped SNPs. I won't go into _how_ we estimate \\(h_g^2\\) (turns out these methods tend to differ from those used to estimate \\(h^2\\) or \\(H^2\\)), but you should at least know what it is.

It will always be the case that \\(h_g^2 \leq h^2 \leq H^2\\). To provide some concrete numbers, the \\(h_g^2\\) of height (one of the most well-studied human phenotypes) was initially estimated to be around 0.45 ([Yang et al. 2010 Nature Genetics](https://www.nature.com/articles/ng.608)) when including ~300,000 SNPs found on GWAS SNP chips at the time, while \\(h^2\\) and \\(H^2\\) have both been shown to be around 0.8 (from twin studies).

It is perhaps surprising to see that \\(h_g^2\\) is such a sizable fraction of \\(h^2\\), given that \\(h_g^2\\) includes so many fewer SNPs than \\(h^2\\) (~300,000 vs many millions). Another interesting observation is that \\(h^2\\) is very close to \\(H^2\\), implying that the true relationship between genotype and height in human populations is quite close to linear (which seems paradoxical given that biology is generally very nonlinear). These two facts hold true for many phenotypes beyond just height. Although these facts seem surprising, they both have very reasonable explanations, which I'm hoping to discuss in future blog posts.

## Purpose of estimating heritability

Why do we care about heritability in the first place? One classical goal of statistical genetics has been to quantify the contribution of genetics to phenotypes (related to the nature vs nurture discussion). \\(h^2\\) or \\(H^2\\) are sensible ways to quantify this contribution.

In the GWAS era, \\(h_g^2\\) finds its main utility in providing an upper bound on the prediction accuracy of a linear predictor learned from GWAS data. A big part of statistical genetics is learning how to predict phenotype from genotype using GWAS data (this is the idea behind [polygenic risk scores](https://www.genome.gov/Health/Genomics-and-Medicine/Polygenic-risk-scores)), so it's useful to know how well we can possibly predict. If a phenotype has a \\(h_g^2\\) close to 0, then this also means it's probably not worth performing any GWAS-related analyses on it. Another very useful but  indirect use of \\(h_g^2\\) is in _partitioning heritability_, in which we "partition" \\(h_g^2\\) across different subsets of SNPs with different biological functions in order to gain some understanding of the biological mechanisms by which genetic variants affect phenotypes.

In the next post, I'll talk about some more useful things to know about heritability.
