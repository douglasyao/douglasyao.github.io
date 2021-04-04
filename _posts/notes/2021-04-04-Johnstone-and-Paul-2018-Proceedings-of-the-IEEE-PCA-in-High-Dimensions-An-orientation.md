---
layout: post
date: '2020-11-05 02:36:40 +0000'
updated_at: '2021-04-04 16:04:35 +0000'
title: Johnstone and Paul 2018 Proceedings of the IEEE - PCA in High Dimensions - An orientation
tags: [ 'PCA', 'stats' ]
latitude: 42.330104002368884
longitude: -71.1166558973225
altitude: 15.05522632598877
source: desktop.mac
categories: ['notes', 'stats']
---

**Authors**: Iain M. Johnstone and Debashis Paul

[Link to paper](https://ieeexplore.ieee.org/document/8412585)

## Synopsis

This paper provides a review of the properties of eigenvalues and eigenvectors of the _random covariance matrices_ in which the data is "high dimensional" (or the number of features is comparable to the number of samples). It turns out that the eigenvalues of such matrices exhibit some really interesting properties. This information is pertinent for answering questions like: "which eigenvectors/eigenvalues of a matrix are _significant_?" or "what proportion of variance in a matrix can be explained by low-rank signal vs. independent noise?"

## Summary

### Background

When performing PCA, we start with a \\(p \times n\\) matrix \\(X\\), where \\(n\\) is the number of samples and \\(p\\) is the number of features. We then find the eigenvalues and eigenvectors of the \\(p \times p \\) sample covariance matrix \\(\frac{1}{n} X X^T \\). Although PCA is simply a procedure applied to a matrix of fixed values, it can also be conceptualized in terms of _random matrices_, in which each sample is drawn from a multivariate distribution with some mean vector and covariance matrix.

As \\(n\\) goes to infinity and \\(p\\) is fixed, the sample covariance matrix will converge to the population covariance matrix (a.k.a \\(E[XX^T]\\)), and the sample eigenvalues will also converge to the population eigenvalues. However, what happens if \\(n\\) and \\(p\\) _both _go to infinity and the ratio \\(\frac{p}{n}\\) stays constant? What will the eigenvalues of the sample covariance matrix look like? This is the boundary case in which the paper focuses on.

### Figure 2

![f92ae920-30cd-466a-b866-68460e56bc7f.png](/assets/Johnstone-and-Paul-2018-Proceedings-of-the-IEEE-PCA-in-High-Dimensions-An-orientation-f92ae920-30cd-466a-b866-68460e56bc7f.png)

This figure illustrates the phenomenon known as "eigenvalue spreading," in which sample eigenvalues are more spread out than population eigenvalues. Both figures denote a scenario in which the matrix has \\(p\\) = 100 features. On the left, all 100 eigenvalues of the population covariance matrix are equal to 1, while the eigenvalues of the sample covariance matrix (where \\(n\\) = 200) are spread out. The same phenomenon is observed when the eigenvalues of the population covariance matrix are spread evenly between 5 and 25 (on the right).

### Figure 3

![93e201a5-d7cc-4f5a-8a3c-500ae225f985.png](/assets/Johnstone-and-Paul-2018-Proceedings-of-the-IEEE-PCA-in-High-Dimensions-An-orientation-93e201a5-d7cc-4f5a-8a3c-500ae225f985.png){:width="300px"}

Given a random matrix (features mean centered and variance standardized, samples iid), when \\(n\\) and \\(p\\) go to infinity and their ratio stays constant, the distribution of eigenvalues of the sample covariance matrix will converge to a [Marchenko-Pastur distribution](https://en.wikipedia.org/wiki/Marchenko%E2%80%93Pastur_distribution) (which depends _only_ on the ratio between \\(n\\) and \\(p\\)). This figures shows what this distribution looks like for two values \\(\frac{n}{p} = 1\\) and \\(\frac{n}{p} = 4\\).

### Figure 4

![fca751c1-774b-4de5-92ad-1d75192d394a.png](/assets/Johnstone-and-Paul-2018-Proceedings-of-the-IEEE-PCA-in-High-Dimensions-An-orientation-fca751c1-774b-4de5-92ad-1d75192d394a.png){:width="500px"}

This figure describes the distribution of the largest eigenvalue in random covariance matrices. A very interesting fact is that even if the population covariance matrix has eigenvalues that are larger than 1, if these eigenvalues are smaller than some critical point indicated in the figure, then the distribution of sample eigenvalues will be _indistinguishable_ from that arising from a population covariance matrix in which _all_ eigenvalues are equal to 1.

First, the way we model this is through the "spiked covariance" model, which is a way to model noise on top of low-rank structure. The model involves a "base" covariance matrix \\(\Sigma_0\\) and a low-rank perturbation:

\\[ \Sigma = \Sigma_0 + \sum_k^K h_k \mathbf{u}_k \mathbf{u}_k^T \\]

In the simplest case, \\(\Sigma_0\\) is the identity matrix, while \\(h_k\\) and \\(\mathbf{u}_k\\) are the eigenvalues and eigenvectors respectively of some low-rank structure in the covariance matrix. This model is called the “spiked” covariance model because it results in a population eigenvalue distribution with many points at 1 (corresponding to noise) and spikes at each \\(h_k\\) (corresponding to signal). This can also be conceptualized in terms of the probabilistic PCA model \\(\mathbf{x = Wz + e}\\), where \\(\mathbf{x}\\) is our sample, \\(\mathbf{W}\\) are all the eigenvectors of the sample covariance matrix, \\(\mathbf{z}\\) are the projected points in PC space (assumed to be randomly drawn from \\(N(\mathbf{0}, \mathbf{I})\\)), and \\(\mathbf{e}\\) is isotropic noise (drawn from \\(N(\mathbf{0}, \mathbf{I})\\)). The covariance matrix of \\(\mathbf{x}\\) is defined as \\(\mathbf{W W}^T + \mathbf{I}\\).

Continuing on: let \\(l_1\\) represent an eigenvalue of our matrix greater than 1, with the remaining eigenvalues equal to 1. If \\(l_1\\) is smaller than \\(1 + \sqrt{\gamma}\\) (where \\(\gamma\\) is \\(\frac{p}{n}\\)), then the distribution of eigenvalues will be _exactly_ the same as if \\(l_1 = 1\\) (a.k.a. it will look as if the matrix has no low-rank structure at all. This fact is pretty cool). Moreover, the corresponding eigenvector for \\(l_1\\) will be _completely uncorrelated_ with the true eigenvector. The top eigenvalue will be distributed according to a [Tracy-Widom distribution](https://en.wikipedia.org/wiki/Tracy%E2%80%93Widom_distribution) around the value \\((1 + \sqrt{\gamma})^2\\).

### Figure 5

![ba8070e7-8234-497b-bc43-cbbe05cfc0ec.png](/assets/Johnstone-and-Paul-2018-Proceedings-of-the-IEEE-PCA-in-High-Dimensions-An-orientation-ba8070e7-8234-497b-bc43-cbbe05cfc0ec.png){:width="500px"}

This figure describes the scenario in which the population covariance matrix has eigenvalues that are larger than the critical point. If \\(l_1\\) is greater than \\(1 + \sqrt{\gamma}\\), then the top eigenvalue will now be distributed according to a _Gaussian distribution_ while being _significantly upwardly biased_ relative to \\(l_1\\) (interesting!). Meanwhile, the corresponding eigenvector will now be correlated with the true eigenvector, where the degree of correlation will depend on \\(l_1\\) and \\(\gamma\\):

![7ce288b5-7945-4e92-b5f1-0d6c4b11efd0.png](/assets/Johnstone-and-Paul-2018-Proceedings-of-the-IEEE-PCA-in-High-Dimensions-An-orientation-7ce288b5-7945-4e92-b5f1-0d6c4b11efd0.png){:width="400px"}

### Figure 6

![237cd688-a8db-4334-9a4e-e70f5380f6f4.png](/assets/Johnstone-and-Paul-2018-Proceedings-of-the-IEEE-PCA-in-High-Dimensions-An-orientation-237cd688-a8db-4334-9a4e-e70f5380f6f4.png){:width="400px"}

This figure shows the relationship between upward bias of \\(\lambda(l_1)\\) (a.k.a. the sample value of \\(l_1\\)) relative to its population value. The upward bias will converge to \\(\gamma\\) as \\(l_1\\) increases. More precisely, we have the following relationship between \\(\lambda(l_1)\\) and \\(l_1\\):

\\[ \lambda(l_1) - l_1 = \gamma \frac{l_1}{l_1 - 1} \\]
