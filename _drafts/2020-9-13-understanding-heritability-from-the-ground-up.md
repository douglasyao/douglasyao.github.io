---
layout: post
title: Explaining heritability from the ground up
---

"Heritability" is a quantity that is central to human genetics, and there is a huge amount of literature aiming to estimate various forms of it. Despite its ubiquity, there also seems to be a dearth of resources that explain what it actually is, and in particular how to interpret it, in a way that is understandable to non-experts. I'm hoping that this blog post can address this. I'll try to omit as many technical details as possible. I'll assume that the reader has at least a basic understanding of genetics (for example, you should know what a SNP, or genetic variant, is).

## Textbook definition of heritability

Heritability is the "proportion of variance" of a phenotype in a population of people that can "be explained" by genetic variants. What do these words actually mean?

## Proportion of variance explained

The notion of "proportion of variance explained" is crucial to understanding heritability. We first start with a group of individuals. For each individual, we measure some phenotype, which we will refer to as \\(y\\). Next, we must define some model that attempts to "explain" \\(y\\) across individuals in some way using other variables, which we'll call \\(x_1, x_2,  \cdots, x_k \\). In our case, \\(x_k\\) represents the minor allele count of a given SNP \\(k\\). Thus, we can write our model for \\(y\\) as something like this:

\\[ y = f(x_1, x_2, \cdots, x_k) + \epsilon \\]

What should this function \\(f\\) look like? In the simplest case, it could be a simple additive function of the variables, where we take some linear combination of the \\(x\\)'s. Or, the function could be much more complicated. For now, we won't specify exactly what this function is. Here, \\(\epsilon\\) refers to whatever part of \\(y\\) that cannot be explained by \\(f\\).

Now, how do we quantify how well \\(f\\) explains \\(y\\) across individuals? We do this by quantifying the "proportion of variance explained" as follows:

\\[\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\]

What exactly is going into the numerator and denominator here? We are looking at the variance of various quantities from the above model. Why variance? Well, variance is a sensible way to quantify uncertainty. We can think of \\(Var(y)\\) as the total uncertainty of our phenotype in our population of individuals, which is how much uncertainty in our phenotype we would have if we didn't use any model at all. Meanwhile, we can think of \\(Var(f(x_1, x_2, \cdots, x_k))\\) as how much of the phenotype can be "explained" by \\(x_1, x_2, \cdots, x_k\\). Putting that all together, when \\(y\\) represents a given phenotype and \\(x_1, x_2, \cdots, x_k \\) represent SNP minor allele counts, then \\(\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\) is exactly the heritability of the phenotype.

## Different flavors of heritability

We can define \\(f\\) in different ways to give us different flavors of heritability. When we let \\(f\\) represent the best possible _linear_ predictor of our phenotype (in other words, the linear function that will maximize \\(Var(f(x_1, x_2, \cdots, x_k))\\)) then the resulting \\(\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\) will refer to narrow-sense heritability (denoted \\(h^2\\)). When we let \\(f\\) represent the best possible predictor _period_ (which can be nonlinear), then \\(\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\) will refer to broad-sense heritability (denoted \\(H^2\\)). Finally, when we let \\(f\\) represent the best possible _linear_ predictor of our phenotype but restrict the set of SNPs to a subset of all SNPs (oftentimes this will be a set of SNPs that are "common" in the population of interest), then \\(\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\) will refer to the SNP heritability (denoted \\(h^2_g)\\). You might think that it's hard to learn the best possible predictor of a phenotype, and you'd be correct - but the cool thing is that statistical geneticists have come up with ways to reliably estimate \\(\frac{Var(f(x_1, x_2, \cdots, x_k))}{Var(y)}\\) without explicitly estimating \\(f\\) (using methods such as Haseman-Elston regression, variance component analysis, LD score regression, etc.).

One benefit of restricting \\(f\\) to be linear is that heritability becomes exactly equivalent to a quantity that many people are familiar with, namely \\(R^2\\). Many of us can picture what an \\(R^2\\) of 0, 0.5, or 1 look like in a simple linear regression setting (one independent variable). Now, just imagine that we have a linear model where the dependent variable is our phenotype and the independent variables are minor allele counts for each SNP respectively. When this linear model is the best possible out of all other linear models, then the \\(R^2\\) from this model will equal \\(h^2\\).


## \\(h_g^2\\) in the GWAS era

When people talk about heritability as the total contribution of genetics to a phenotype, they will usually be referring to \\(h^2\\) or \\(H^2\\). However, in the GWAS era, people tend to work more with \\(h_g^2\\) than \\(h^2\\) or \\(H^2\\). This is the case because only \\(h_g^2\\) can be estimated from GWAS data, whereas \\(h^2\\) and \\(H^2\\) need family or twin data to be estimated. To elaborate a bit, SNP chips used in GWAS measure a small set of common SNPs, which are chosen to be correlated with as many other common SNPs as possible (rare SNPs do not come into the picture since the correlation between rare and common SNPs is guaranteed to be small). A SNP chip might contain around ~500,000 common SNPs, out of ~10,000,000 total common SNPs and >100,000,000 total SNPs (including rare SNPs). Thus, estimates of \\(h_g^2\\) will often refer to the phenotypic variance that can be explained by just the 500,000 genotyped SNPs. Note however that due to correlations between SNPs, these 500,000 SNPs can often capture a large fraction of the total phenotypic variance.

There is another reason to care about \\(h_g^2\\), namely that our goal is often to explicitly estimate \\(f\\) from GWAS data (this is the whole idea behind genetic prediction of disease and polygenic risk scores). \\(h_g^2\\) thus gives us an upper bound on the best possible prediction accuracy (in terms of proportion of variance explained) of our predictor learned from the GWAS data.

Note that it will be the case that \\(h_g^2 \leq h^2 \leq H^2\\). For an example with some concrete numbers, the \\(h_g^2\\) of height (one of the most well-studied human phenotypes) was initially estimated to be around 0.45 ([Yang et al. 2010 Nature Genetics](https://www.nature.com/articles/ng.608)) when including ~300,000 SNPs found on GWAS SNP chips at the time, while \\(h^2\\) and \\(H^2\\) have both been shown to be around 0.8 (from twin studies).

As an aside, one interesting phenomenon is that for many phenotypes, \\(h^2\\) is close to \\(H^2\\), implying that the relationship between genotype and phenotype for most phenotypes in human populations is quite close to linear (which seems paradoxical given that biology is generally very nonlinear). It turns out that this becomes a little less of a paradox when you realize that heritability is intrinsically a population-level parameter while biological nonlinearity operates on the individual level, but this is a topic for another discussion.

# "Folk knowledge" about heritability

Although the definition of heritability is pretty straightforward, there are a lot of extra things that should be kept in mind when interpreting heritability. These facts are common knowledge to statistical geneticists but are often not obvious to people not working in the field.

## (1) Heritability comes much closer to causality than you might think at first glance.

Oftentimes when think about the proportion of variance in an arbitrary dependent variable that can be explained by arbitrary independent variables, we cannot guarantee the existence of any causal relationship between the two (even if the proportion of variance explained is high). This is the classic "correlation does not imply causation" argument. You may be familiar with plots such as the following, which show almost perfect correlations between two clearly unrelated variables:

<img src="/assets/spurious_correlation.png" width="800">

Thus, you might reasonably think that heritability cannot be interpreted as reflecting any sort of causal effect of SNPs on a phenotype.

However, when we specifically have our independent variables represent SNP minor allele counts and our dependent variable represent a phenotype in a population of humans, then correlation _DOES_ imply causation (with a few caveats of course; see below). This fact is quite surprising (at least it was to me when I first learned it), but it makes sense when you think about where our genetics comes from.

First, we need to understand what leads to correlation \\(\neq\\) causation. This phenomenon only really applies to observational (rather than experimental) data, in which we cannot control external factors from influencing our variables of interest. The main boogeymen in observational studies (which include GWAS) are _confounders_, which are potentially unknown factors that influence both our dependent and independent variables. Confounders can make it look as if there is a relationship between our dependent variable and independent variable even when there is none, leading us to make spurious scientific conclusions. Another problem is _reverse causality_, in which our dependent variable actually influences our independent variable(s) rather than the other way around.

It is serendipitous that genetic variants are basically immune to both these problems in most human populations.  In terms of reverse causality, our germline genotype cannot by altered by any factors, so reverse causality is not an issue. In terms of confounders, we normally aim to address them via _randomization_, in which we delegate our independent variable to samples in a random manner that is (hopefully) independent of all possible confounders. Well, it turns out that nature has already done this randomization for us. The mechanism of this randomization is _meiosis_ followed by _random mating_. I won't go into detail about how these processes work, but you can sort of imagine each individual inheriting each SNP in their genome by pooling all SNPs in the population together and then randomly selecting two SNPs to act as their genotype - a perfect randomized experiment.

Of course, in reality there _are_ factors that can cause this process to be non-random. Individuals in a homogenous population mate mostly, but not entirely, randomly. People tend to mate with others in close geographic proximity ("population stratification") or with more similar phenotypes ("assortative mating") as themselves. In addition, people don't actually inherit each SNP independently of one another; people inherit them in contiguous sections of chromosomes, which causes SNPs physically near each other to be correlated across individuals in a population ("linkage disequilibrium"). However, these sources of confounding are minor compared to the sort of confounders you see in other types of  observational studies, and they are in fact quite well understood, enabling us to mostly account for them in our analyses.

Finally, let's relate this back to heritability. The above discussion implies that when we see a correlation between a SNP and a phenotype in a population, this basically means that the SNP (or at least some other SNP correlated with that SNP) is _causally_ influencing the trait. We can thus think about the heritability of a phenotype as something close to the total _causal_ effect of genetic variants on a phenotype.