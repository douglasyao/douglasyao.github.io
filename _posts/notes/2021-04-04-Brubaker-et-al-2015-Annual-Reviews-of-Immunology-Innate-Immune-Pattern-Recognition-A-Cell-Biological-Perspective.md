---
layout: post
date: '2020-10-25 20:23:32 +0000'
updated_at: '2021-04-04 22:59:35 +0000'
title: Brubaker et al. 2015 Annual Reviews of Immunology - Innate Immune Pattern Recognition - A Cell Biological Perspective
tags: [ 'immune' ]
latitude: 42.365234375
longitude: -71.1221407587489
altitude: 9.64645004272461
source: desktop.mac
categories: ['notes', 'genomics']
---

**Authors**: Sky W. Brubaker, Kevin S. Bonham, Ivan Zanoni, and Jonathan C. Kagan

[Link to paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5146691/)

## Synopsis

This review paper describes the molecular pathways involved in the innate immune response. I will focus specifically on the TLR4 pathway response to lipopolysaccharide (LPS), as this pathway is one that I am studying in my own research.

## Summary

![109635d4-eb82-4b76-8532-6b93b5684278.png](/assets/Brubaker-et-al-2015-Annual-Reviews-of-Immunology-Innate-Immune-Pattern-Recognition-A-Cell-Biological-Perspective-109635d4-eb82-4b76-8532-6b93b5684278.png){:width="450px"}

This figure summarizes the entire TLR4 pathway, which includes signaling from both the cell surface and from endosomes. Here is an alternate figure of the same pathway from [Wikipedia](https://en.wikipedia.org/wiki/TLR4):

![1e572216-a0f0-4509-9a66-2a1d9f12fb04.png](/assets/Brubaker-et-al-2015-Annual-Reviews-of-Immunology-Innate-Immune-Pattern-Recognition-A-Cell-Biological-Perspective-1e572216-a0f0-4509-9a66-2a1d9f12fb04.png){:width="450px"}

### LPS multireceptor complex

The LPS multireceptor complex is the first thing that binds to LPS and activates the TLR4 signaling pathway. It is made up of 4 genes:

1. **TLR4** (Toll-like receptor 4)
2. **MD-2** (Myeloid differentiation factor 2) aka **LY96** (Lymphocyte antigen 96)
3. **CD14** (Cluster of differentiation 14)
4. **LBP** (LPS binding protein)

LBP binds to LPS and facilitates the transfer of LPS to CD14. CD14 then transfers LPS to TLR4-bound MD-2, which dimerizes TLR4 leading to signal transduction. CD14 also helps traffic TLR4 from the plasma membrane into the endosomes, resulting in additional signal transduction.

### TIRAP/MyD88 pathway

This pathway occurs immediately following the previous one and occurs from the cell surface. It comprises the following steps:

1. TLR4 moves to lipid rafts and interacts with **TIRAP** (TIR Domain-Containing Adaptor Protein)
2. TIRAP oligomerizes with **MyD88** (Myeloid Differentiation Primary Response Gene 88) and **IRAK1/2/4** (IL-1 Receptor Associated Kinases) to form a myddosome
3. IRAKs recruit **TRAF6** (TNF Receptor-Associated Factor 6)
4. TRAF6 recruits kinase complexes containing **TAK1** (Transforming growth factor-beta-Activated Kinase 1, aka **MAP3K7**) and **TAB1/2/3** (TAK1-Binding protein)
5. **IKKa/b/g** (IkB Kinase aka **CHUK**, **IKBKB** and **IKBKG**) gets recruited and activates **NF-kB**. NF-kB leads to downstream effects including production of proinflammatory cytokines such as **IL-12** and **TNF**.
6. **TAK1** (aka **MAP3K7**) gets released into the cytoplasm and acts as a MAPKKK (mitogen-activation protein kinase kinase kinase). The MAPK cascade leads to activation of **AP-1** (activator protein 1), involved in expression of proinflammatory cytokines.

### TRIF/TRAM pathway

In addition to the TIRAP/MyD88 pathway (which occurs from the cell surface), TLR4 signaling also continues from endosomes.

1. TLR4 engages **TRAM** (TRIF-related Adaptor Molecule aka **TICAM2**)
2. TRAM  interacts with **TRIF** (TIR-domain-containing adaptor inducing interferon-beta aka **TICAM1**) 
3. TRIF interacts with **RIPK1** (Receptor Interacting Serine/Threonine Kinase 1), **TRADD** (TNFRSF1A Associated via Death Domain), **CASP8** (Caspase 8), **FADD** (Fas-associated protein with death domain aka **MORT1**), and **IKKa/b/g** to start **NF-kB** signaling
4. TRIF also recruits **TRAF3**
5. TRAF3 interacts with **TANK** (TRAF family member-associated NF-kB activator) to recruit **IKKg/e** and **TBK1** (TANK binding kinase 1), which activates **IRF3** (Interferon regulatory factor 3)
6. IRF3 is a key transcriptional regulator of type 1 interferon response. The type 1 IFN response involves 6. **IFN-a** and **IFN-b**.

### TLR4-independent CD14 signaling

CD14 can also signal in response to LPS independently of TLR4. One pathway induces calcium influx via NFAT activation. Another pathway controls endocytosis and moves TLR4 from the plasma membrane into endosomes. The second pathway depends on **ITAM** (immunoreceptor tyrosine-based activation motif), **Syk** (a tyrosine-protein kinase), and **PLCg2** (phospholipase C gamma 2).
