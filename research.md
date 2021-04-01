---
layout: page
title:
permalink: /research/
---

# Research interests

I am broadly interested in anything to do with statistics/machine learning, genetics/genomics, and biotechnology. As an undergraduate, I conducted research in computational cancer genomics. I conceived and led a project aiming to identify associations between gene expression levels and a cancer phenotype known as "genomic instability" (which is a metric of how quickly tumors mutate) in large databases of tumor sequencing data. The project culminated in a manuscript I wrote that was published in Scientific Reports.

As a graduate student, my research has been in statistical genetics, a field dating back to Ronald Fisher in the 1920s which aims to study the statistical relationship between genetics and phenotype in human or animal populations. In this venue, I worked on a project that involved defining a quantity known as "heritability mediated by gene expression levels," which quantifies how much total genetic effect on a phenotype "flows through" separately measured gene expression levels. I derived a novel method of moments estimator of this quantity, established its properties (including bias, consistency, and calibration under the null) via derivations and simulations, and applied it to real human disease genetics data. The project culminated in a manuscript I wrote that was published in Nature Genetics.

For more info on my past work, see below.

# Current research

I am currently working on general experimental and computational strategies to learn combinatorial effects of multiple treatments on any biological model system _at scale_. Normally, if one wants to study all pairs of _n_ distinct treatments on some model system, one needs to conduct at least _n_ choose 2 experiments (which exhaustively enumerates all pairs of the _n_ treatments). I am investigating an alternative framework inspired by compressed sensing in signal processing, which involves conducting a relatively small number of _random composite experiments_ (i.e. experiments that involve applying random combinations of many treatments), then recovering all information from this set of experiments. This approach can in theory learn the effects of all individual pairs of treatments with comparable accuracy to the exhaustive enumeration approach, while requiring 1-3 orders of magnitude less experiments. I am currently testing this approach in the context of CRISPR gene knockouts to study genetic interaction effects, and hope that it can eventually be used to efficiently screen drug combinations at much larger scales than currently done.

# Past research

## Statistical genetics

<img src="/assets/mesc_screenshot.png" width="180" align="right" style="margin: -30px 0px 10px 40px;border:1px solid lightgrey;border-radius:90px">

**Douglas Yao**, Luke O'Connor, Alkes Price, Alexander Gusev.
[Quantifying genetic effects on disease mediated by assayed gene expression levels](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7276299/).
_Nature Genetics_, 2020.

See [here](/blogs/2021/03/22/General-overview-of-Yao-et-al-2020.html) for a summary of the work aimed at a general audience, and [here](/blogs/2020/09/16/intuition-behind-mediated-expression-score-regression.html) for a summary of the work aimed at a technical audience.

<br>

## Computational cancer genomics

<img src="/assets/lmm_screenshot.png" width="180" align="right" style="margin: -55px 0px 10px 40px;border:1px solid lightgrey;border-radius:90px">

**Douglas Yao**, Nikolas Balanis, Eleazar Eskin, Thomas Graeber.
[A linear mixed model approach to gene expression-tumor aneuploidy association studies](https://www.nature.com/articles/s41598-019-48302-1).
_Scientific Reports_, 2019.

<br>

## Other publications
Igor Mandric, Harry Taegyun Yang, Nicolas Strauli, Dennis Montoya, ... , **Douglas Yao**, ... , et al.
[Profiling immunoglobulin repertoires across multiple human tissues by RNA sequencing](https://www.nature.com/articles/s41467-020-16857-7).
_Nature Communications_, 2020.

Keith Mitchell, Jaqueline Brito, Igor Mandric, Qiaozhen Wu, ... , **Douglas Yao**, ... , et al.
[Benchmarking of computational error-correction methods for next-generation sequencing data](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-020-01988-3).
_Genome Biology_, 2020.
