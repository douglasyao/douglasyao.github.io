---
layout: post
title: Intuition behind mediated expression score regression
---

This blog post is meant to accompany my paper ["Quantifying genetic effects on disease mediated by assayed gene expression levels"](https://www.nature.com/articles/s41588-020-0625-2) (Yao et al. 2020 Nature Genetics), in which we introduced a method called "mediated expression score regression" (MESC) to estimate a quantity "heritability mediated by gene expression levels." I had originally meant to write it when the paper came out, but better late then never I guess. The paper is unfortunately pretty dense and probably not very accessible to readers not in the field of statistical genetics, so I'm hoping to provide a non-technical overview of the paper, in which I describe the background, motivation, method, and assumptions. I'm assuming that you already have a working knowledge of what GWAS and heritability are. If you're fuzzy about heritability, you can read my other blog post about it. I also included a glossary that defines all the lingo used in this post (terms such as "heritability enrichment" and "Mendelian randomization"). Note that I'll use the terms "trait" and "disease" interchangeably, as well as "SNP" and "variant."

# Background

A while ago, researchers realized that most of the GWAS hits they found fell into _non-coding_ parts of the genome.

[insert figure]

If you think about how a non-coding SNP might exert its effect on a trait, the first thing that comes to mind is via _gene regulation_ (in other words, altering gene expression levels). This was the motivation behind a series of massive efforts to measure _expression quantitative trait loci_ (eQTLs). The most salient of these efforts has been the Genotype-Tissue Expression (GTEx) Consortium, which measured expression levels in ~50 tissues for around ~500 individuals. From these studies, many thousands of significant eQTLs covering almost all genes across many tissues have been detected.

Now, what do we do with these eQTLs after measuring them? In particular, how do we integrate them with GWAS hits to tell us something about how the GWAS hits are acting on the phenotype? Many approaches have been developed to do this on an individual gene level, which include "colocalization tests" and "transcriptome-wide association studies" (TWAS). Long story short, these methods basically look for genes with some sort of "overlap" between their eQTLs and GWAS hits. If a SNP is both a GWAS hit and an eQTL for a given gene, then we would be inclined to think that this gene is somehow important in the SNP's mechanism of action on the trait. In particular, we would like to think that the SNP's effect on the trait is _mediated_ through that gene's expression.

[insert figure]

Although this mediation scenario is what we want to see, there are in fact other less desirable scenarios that are indistinguishable from mediation to colocalization/TWAS. I will discuss some of these scenarios in a bit.

The individual-gene methods are interesting and useful ways to prioritize disease-relevant genes. However, perhaps we'd like to take a step back and understand the _overall_ importance of gene expression in "explaining" a phenotype. Understanding this importance can guide our individual gene analyses and give us an overall idea of how disease-relevant our gene expression measurements are.

With regard to this aim, there had already been some work done before our paper came out. Hormozdiari et al. looked at the overall _heritability enrichment_ of SNPs that we deem to be eQTLs, finding that fine-mapped eQTLs as a whole are enriched for disease heritability. In addition, Chun et al. looked to see what proportion of significant GWAS hits for autoimmune disease "colocalize" with immune cell eQTLs, finding that only 25% of GWAS hits do so. These results give us an idea of how relevant eQTLs as a whole are to disease. We can see the eQTLs are more disease-relevant than random SNPs (as evidenced by their heritability enrichment), but there are signs that some GWAS hits do not overlap with eQTLs, suggesting that perhaps our eQTL data is not capturing disease mechanisms as well as we would hope.

However, there are some important drawbacks to all the previous approaches I've described so far. In particular, these approaches cannot distinguish "mediation" (our desired scenario) from other causality scenarios. Two of these scenarios include "pleiotropy" (in which the same SNP affects gene expression and disease independently of each other) and "linkage" (in which two SNPs separately affect gene expression and disease but are in LD with each other). The colocalization-based methods try to rule out linkage as an explanation for overlap between eQTLs and GWAS hits, but _none_ of the methods can (nor do they attempt to) distinguish pleiotropy from mediation.

This brings us to our paper. In my opinion, the most direct way to understand how "important" eQTLs are to disease is via some sort of quantification of mediation, since mediation is how we tend to conceptualize the involvement of gene expression in disease. How do we measure mediation? We do this by quantifying the _proportion of disease heritability_ that is mediated by gene expression levels. This definition might be a little opaque, so I'll try to break it down.

# Defining "disease heritability mediated by gene expression levels"

Heritability is a natural way to think about the total effect of genetics on a trait. We can imagine that each SNP exerts some causal effect on the disease, which we'll call \\( \omega_k \\) for SNP \\( k \\) (usually people use \\( \beta \\) to refer to this quantity, but I ended up using \\( \beta \\) for eQTL effect sizes in the paper instead - too late to change now.)

[image]

Now, we can think about a model in which each SNP's effect on disease is _mediated_ through the expression of one or more genes.

[image]

Note that each SNP effect size has a mediated component and a non-mediated component. The mediated component can be broken down into the product of eQTL effect sizes and gene effect sizes on trait.

[image]

In this model, we can feel free to interpret these effect sizes in the most intuitive way possible: \\(\beta_{ik}\\) represents the change in expression of gene \\(i\\) in individuals carrying an allele of SNP \\(k\\), \\(\alpha_i\\) is the change in trait per unit change in expression of gene \\(i\\), and \\(\gamma_k\\) is the extra change in the trait in individuals carrying an allele of SNP \\(k\\) that doesn't go through expression. Because we don't want to weigh highly expressed or variable genes more than others, we'll scale gene expression to have the same mean and variance across all genes. Thus, you can think of eQTL effect sizes in terms of expression change proportional to overall expression and variance of the gene.

How do we quantify overall mediation? Well, one way to do it would be to just take all the mediated parts of each effect size and sum them up. Because effect sizes can be positive or negative, we'll square everything. We end up with a quantity that I'll call \\(h_{med}^2\\):

\\[h_{med}^2 = \sum_{i} \alpha_i^2 \sum_{k} \beta_{ik}^2 \\]

Finally, we can divide this quantity by the total SNP effect on disease \\( \sum_k \omega_k^2 \\) to get the _proportion_ of total SNP effect on disease mediated by gene expression.

\\[\frac{h_{med}^2}{h_g^2} = \frac{\sum_{i} \alpha_i^2 \sum_{k} \beta_{ik}^2}{\sum_k \omega_k^2} \\]

We have now defined the quantity we want to estimate (well, not exactly; see below.)

**Technical point 1**: In practice, we don't quite estimate \\(h_{med}^2\\) as defined above. We like to operate in units of _heritability_ (which are comparable across different traits in different populations). When operating in units of heritability, each SNP effect size is scaled by the variance of the SNP's minor allele count, which in turn depends on the SNP's minor allele frequency (MAF) in the population. In other words, SNPs contribute to heritability proportional to both their per-allele effect size (what we intuitively think of as their effect size in an individual) as well as their MAF, which causes common variants to contribute more to heritability than rare variants. Working with scaled effect sizes enables us to write \\(h_g^2 = \sum_k \omega_k^2 \\), without having to think about the variance of individual SNP counts. Scaling effect sizes by MAF may lead us to change our interpretation of these effect sizes, but I'll posit that we don't have to change our interpretation _that_ much (since we are only looking at common variants anyway, for which there isn't a strong relationship between per-allele effect size and MAF). If this point is confusing, it may be helpful to read my other blog post on heritability.

**Technical point 2**: Whenever I talk about "heritability," I will be referring specifically to SNP heritability \\(h_g^2\\). When thinking in terms of SNP heritability, it's not quite appropriate to think of \\(\omega_k\\) or \\(\beta_{ik}\\) as representing the _causal_ effect size of SNP \\(k\\). It will actually represent this causal effect size _in addition to_ tagging effects of any SNPs in LD with SNP \\(k\\) that are not included in the set of common GWAS SNPs being studied.

Ok, so we have our quantity that we want to estimate: \\(h_{med}^2\\). Now for the hard part: actually estimating it. In the process of estimating this quantity, we will have to distinguish mediation from the other undesirable scenarios such as pleiotropy and linkage. Let's go into how we do this.

# Estimating \\(h_{med}^2\\)

People have already thought about ways to try to distinguish pleiotropy from mediation, in particular under the umbrella of _Mendelian randomization_ (MR) methods. There are many different types of MR, which all come with their own bag of assumptions and pros/cons. The core idea behind MR is that if a gene's expression is truly mediating genetic effects on disease, then SNP effects on the gene should be proportional to SNP effects on the disease.

This is the core idea behind MESC as well (and is also closely related to TWAS/genetic correlation), so I think it's worth driving home. Let's walk through an example. Suppose that we know in reality that increasing expression of gene \\(i\\) by 1 (in some units) will increase trait by 1 (in some units). Now, suppose that SNP 1 increases the expression of gene \\(i\\) by 2. If the SNP does not affect anything other than the expression of gene \\(i\\), then the SNP should also increase the trait by 2. Note that we cannot measure \\(\alpha\\), but we _can_ measure \\(\beta\\) and \\(\omega\\). We can thus divide \\(\omega\\) by \\(\beta\\) to get an estimate of \\(\alpha\\).

Well, you might think that it's unrealistic that the entire effect of the SNP on trait is going through the gene, and you'd be correct. Perhaps a more realistic model would look like this:



where the SNP has some effect on the trait that isn't going through the gene. Ok, so how do we estimate \\(\alpha\\) now? It's tricky if we just look at one SNP, but if we have _multiple_ SNPs that affect the gene, then we have a way to approach this problem.  




If you're familiar with TWAS, this sounds quite similar to the genetic correlation betwen; and it is! There is an important difference though.

To summarize:





# "Mediated heritability" vs. "explained heritability"

This section is somewhat technical, so feel free to skip if you want. There is a subtle but important difference between




# Glossary
* **eQTL**: An eQTL is a GWAS hit in which we have our trait of interest be the expression levels of some gene.
* **Linkage disequilibrium**: You can think of LD as correlations between nearby SNPs across individuals in a population.
* **Heritability**: If you're not comfortable with thinking about heritability, please see my other blog post(s) on it. Briefly, you can think of heritability as the "total effect of genetics on a phenotype." This quantity is often more straightforward to estimate than individual SNP effects on a phenotype, which are complicated by LD.
* **Heritability enrichment**: is related to the idea of "partitioning heritability," in which we quantify how much total effect is coming from a _particular set of SNPs_ (rather than the set of all SNPs). We are free to define this set of SNPs in any way that we want; for example, these SNPs can be located on a given chromosome, or be located in genomic regions annotated as carrying a particular histone mark, etc. The "heritability enrichment" of this set of SNPs is simply how much more heritability is coming from those SNPs than expected (a.k.a. if genetic effect was uniformly distributed across all SNPs). Enrichment for heritability means that more genetic effect on disease is coming from these SNPs than average, so we can interpret these SNPs as being more disease-relevant than average.
* **Marginal vs causal**: Sometimes I will refer to a GWAS or eQTL effect size as "marginal" or "causal." A SNP's "marginal" effect size is one that comes straight out of a GWAS. Due to correlations between SNPs, these effect sizes will "tag" the effects of nearby SNPs. A SNP's "causal" effect size is its _actual_ effect on the trait, which does not include these tagging effects. We typically cannot directly measure the causal effect size of a given SNP from GWAS, but there are some ways to get at SNPs with nonzero causal effects.
* **Fine-mapping**: is a way to try to identify causal GWAS hits or eQTLs in a region of marginal GWAS hits or eQTLs. Without going into detail, fine-mapping methods take into account the LD structure of a region of associated SNPs and give you a probability that a particular SNP truly has a causal effect on the trait.
* **Colocalization**: This concept is closely related to fine-mapping. One early way that people have tried to integrate eQTLs with GWAS was to simply intersect marginal GWAS hits with marginal eQTLs, but as you can imagine this is complicated by tagging effects of nearby SNPs. Colocalization involves jointly fine-mapping both the eQTL and GWAS hit in order to produce a probability that the exact same SNP is causal for both expression and trait.
* **Transcriptome-wide association study (TWAS)**: TWAS was developed as an alternative approach to colocalization. Rather than looking for genes with one or more eQTLs that have a high probability of also being GWAS hits (as colocalization does), TWAS looks for genes with _significant genetic correlation_ between their expression and trait. You can think of genetic correlation between two traits as the _correlation_ between the SNP effect sizes for those traits. In other words, in TWAS, we want to see that when eQTL effect sizes for a given gene go up, then the GWAS effect sizes of those SNPs also go up.
* **Mendelian randomization**: Mendelian randomization (MR) is an approach that was developed a long time ago, but when applied to gene expression is very similar to TWAS. Whereas TWAS looks for _correlation_ between eQTL effect sizes and GWAS effect sizes, MR looks at the _slope_ when regressing GWAS effect sizes on eQTL effect sizes.
* **TWAS vs MR**: The conceptual difference between TWAS and MR basically boils down to the difference between correlation and slope (which as you can imagine are two very similar things). In particular, . In practice, different methods have different ways of handling LD and other various implementation details.

due to the fact that in a regression, the _correlation_ between the two variables is equivalent

First, let's define some terms.
Let \\(r_i\\) represent the _genetic correlation_ between the expression of gene \\(i\\) and a trait (TWAS will look for genes where this is significantly nonzero). Let \\(\alpha_i\\) represent the _slope_ from regressing GWAS effect sizes on a eQTL effect sizes for gene \\(i\\) (MR will look for genes where this is significantly nonzero). \\(r_i\\) and \\(\alpha_i\\) are related by the simple formula:
\\[\alpha_i = r_i \frac{Var(\omega_k)}{Var(\beta_{ik})}\\]
If we let \\(\beta\\) represent eQTL effect sizes and
In what scenario will MR outperform TWAS? Suppose that we have . In the end, it's probably fine to think to TWAS and MR as basically the same thing, where the primary differences come down to implementation details.
* **Colocalization vs TWAS/MR**: TWAS/MR has various pros and cons relative to colocalization. For example, colocalization can eliminate scenarios where eQTLs and GWAS hits overlap due to "linkage," whereas TWAS/MR cannot (in fact, colocalization was specifically designed for this task). On the other hand, TWAS/MR is more powerful than colocalization when a gene has multiple eQTLs that all overlap with GWAS hits.