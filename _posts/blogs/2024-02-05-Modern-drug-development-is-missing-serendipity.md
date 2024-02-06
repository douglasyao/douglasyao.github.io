---
layout: post
title: Modern drug development is missing serendipity
categories: blogs
---

**TL;DR: In order to improve the productivity of the drug development industry, the number of clinical trials being run needs to greatly increase. The industry should focus on decreasing the cost of running clinical trials.** 

Making a new drug that works in humans is really, really hard. An oft-cited statistic is that only 10% of drugs that enter clinical trials make it through. Another is the existence of Eroom’s law, which notes that the number of new drugs developed per dollar spent on R&D (inflation adjusted) has been dropping exponentially since the 1950s. [Many explanations](https://www.nature.com/articles/nrd3681) have been proposed to explain these trends: clinical trials are more expensive, drugs need to improve on previous drugs, regulations are stricter. 

How does the drug development industry as a whole improve its output, in light of the above challenges? Some propose that [phenotypic screens](https://www.nature.com/articles/s41573-022-00472-w) (aka screens that look at the effects of a drug on a cellular or animal phenotype, rather than binding to a specific target) are the way to go. Others say that using artificial intelligence to design molecules will revolutionize the field. Maybe these approaches can work in some particular cases. However, I think that all approaches that focus on the pre-clinical side of drug development (including the ones mentioned above) ultimately miss the point in several ways: (1) they overestimate how much we know about biology, and (2) they underestimate the role that **serendipity** plays in drug development. 

Pre-clinical studies (including in vitro and in vivo studies) are, at best, weakly predictive of in-human effects of drugs[^1]. This contradicts what you would expect from reading about drug development success stories, where each is accompanied by the sense that it was some sort of deep scientific understanding or ingenuity that led to the drug being effective. The story often looks like this: the drug binds to gene X, and gene X is part of gene pathway Y that causes the disease, so the drug cures the disease. It’s so obvious; how could it possibly not work? 

Undoubtedly some of this scientific understanding is real. Yet, the high clinical trial failure rate is telling. Each of the 90% of drugs that enter clinical trials and fail, which you don’t hear about as much, had an equally convincing-sounding biological mechanism of action as any drug that succeeded[^2]. 

Some would say that the clinical trial success rate will go up in the near future. As a biologist (or at least someone who went through graduate school for it), I’ve been trained to think that it’s possible, through enough effort, ingenuity, and cleverly designed experiments, to gain a deep understanding of any biological mechanism relevant to human disease. I can say now, after digging into many papers and writing several of my own, that this is very far from the case in general. The vast majority (one could even argue “all”) of our understanding of biology is surface-level[^3]. A good fraction of it is probably flat-out wrong[^4]. Our ways of measuring and modeling complex biological systems are embarrassingly crude[^5]. I strongly believe that we are not anywhere close to having predictive models of human disease. 

When we’re working in a system that we poorly understand (and we certainly have a poor understanding of human disease biology as a whole[^6]), our successes are primarily dependent on luck. 

&nbsp;

## Serendipity in drug development

Serendipity plays a massive role in successful drug development. This fact was most obvious during the “historical” era of drug development (from around 1940 to 1980), when molecular biology was in still in its infancy. Nobody understood how any drugs worked. Yet, a great number of highly effective drugs emerged from that era, including most drugs used today in one of the most biologically complicated disease areas (psychiatric disorders). 

How did people make drugs with essentially zero understanding of disease biology? They had to rely on luck. However, they were able to harness luck in the best fashion to maximize their chances of success. When designing something (e.g. a drug) to have some function in a system that we don’t fully understand, the best way to proceed is to **test, modify**, and **iterate** (the so-called “engineering method”), and to do this as fast as possible. 

(1) **Test.** 

Back then, people very rapidly tested new drugs in humans. It was common for a new drug to be synthesized, tested in animals (sometimes this step was skipped), then immediately tested in humans within 1 year. Of course, this is unethical for many reasons, and extensive safety testing in animals is required by the FDA nowadays before human testing, [for good reason](https://en.wikipedia.org/wiki/Thalidomide_scandal). Yet, the frequency of human testing no doubt contributed to the success of drug development during that era. 

A crucial aspect here is that the testing occurred in **humans** - not biochemical assays, cells, or animals. As mentioned above, these are only weakly predictive of in-human effects. In order to guarantee that something has a desired effect in a given complex system, that thing must be tested in that **exact same** system. 

(2) **Modify and iterate**. 

The first drugs to be developed came directly from natural products[^7]. Subsequent drugs were basically small, random modifications of these drugs - adding or replacing a functional group here or there. 

The only way to know, for sure, if a drug works is to test it in humans. Once it’s been established that a drug works, then this serves as a starting point for future cycles of small random modifications and testing. The logic is that small modifications to a drug will most likely preserve its general function, while the randomness provides the possibility for improvement. By retaining the best performing drugs at each cycle, large improvements can occur over time[^8]. 

&nbsp;

In the “modern” era of drug development (where target-based development is the dominant paradigm), we like to think that the “test in human → modify drug → iterate” strategy is no longer as applicable as it was before we knew anything about biology. People have the notion that we can simply design molecules from scratch that will have a desired effect in humans. However, the idea of iterating upon previous drugs certainly has not gone away. [Almost 80% of all approved drugs today are so-called “me-too” drugs](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC534578/) - they make small modifications upon previous drugs. The most effective drug for any given disease is [rarely the first one of its structural class to be developed](https://atelfo.github.io/2023/02/26/pharmaceutical-blockbusters-the-past-present-and-future.html) - they are an iteration of a previous drug. 

Serendipity continues to define the success of drugs. One consistent trend among all the best-selling and/or most effective drugs is that they are that way **by chance:** prior to human testing, there was no way to possibly predict their extraordinary effects. To provide a recent salient example, GLP1 agonists - in particular semaglutide (Ozempic) and tirzepatide (Mounjaro) - have been remarkably effective at treating obesity and obesity-related disorders, such as kidney failure and heart disease. The drugs were not designed to treat obesity; they were designed for type 2 diabetes (a related, but nonetheless different disorder). Their effectiveness towards treating obesity was discovered by accident after clinical trials. Moreover, GLP1 agonists are hardly a new idea - there is a [long history of them](https://en.wikipedia.org/wiki/GLP-1_receptor_agonist), dating back to exenatide approved for clinical use in 2005. People have understood the basic function of GLP1 since the 1980s. As much as we like to think that semaglutide and tirzepatide arose from some scientific breakthrough, they actually came from the tried-and-true strategy of iterating upon previous drugs and getting lucky. 

&nbsp;

## Harnessing serendipity

When success depends on luck, the strategy is clear: take as many shots-on-goal as possible. In drug development, a “shot-on-goal” is a clinical trial. Thus, the way to maximize chances of success is to run as many clinical trials, for as many different drugs, as possible. 

Of course, this is easier said than done. Clinical trials are eye-wateringly expensive - a phase 3 clinical trial can easily cost hundreds of millions of dollars nowadays. This cost is why people try to “de-risk” clinical trials as much as possible - they run tons of pre-clinical experiments in all sorts of cellular and/or animal models, with the hope that repeated validation in non-human models improves the probability of success in a clinical trial. Maybe these non-human models are better than nothing. However, they clearly aren’t very good, as evidenced by the the continued high failure rate of clinical trials. A single data point in a human is worth infinitely more than a thousand mouse studies.

Here’s another way to think about it. Suppose that, with a fixed budget, we would like to double our chance of getting a single drug through clinical trials. One approach is to double the number of drugs we test in clinical trials, which would require us to halve the cost of running each clinical trial. Another approach is to double the chance of success of each individual trial, through better pre-clinical testing or better drug candidates. To me, it seems much easier to reduce the costs of clinical trials, than to increase the chance of success in each individual trial. The latter is impossible to guarantee - at best, you can only claim to *potentially* increase your chance of success in a clinical trial. Even this would require some supernatural biological insight or new technology that nobody in the industry has been able to consistently produce. Meanwhile, running double the number of clinical trials *guarantees* you double the chance of getting at least one success. 

How does one reduce the cost of clinical trials? I’m far from an expert in this area, but [much is written about the myriad  inefficiencies they suffer from](https://aspe.hhs.gov/reports/examination-clinical-trial-costs-barriers-drug-development-0) - lack of electronic data capture, byzantine regulatory practices, disconnect between routine medical care and clinical trials, etc. One revealing statistic is that 90% of patients never get the opportunity participate in a clinical trial due to the lack of clinical trial infrastructure in community hospitals. There are plenty of great startups - [Vial](https://vial.com/) and [Formation Bio](https://www.formation.bio/) (formerly TrialSpark) are two of them - that are trying to tackle this issue. 

&nbsp;

## Final thoughts

There have been some amazing technological advantages in drug discovery in recent years, like mRNA vaccines and CRISPR medicines. I don’t want to downplay the importance of new drug modalities such as them. However, regardless of their potential, all new drugs have to go through clinical trials in order to be used. In order for any type of drug to reach its full potential, it needs to be iteratively tested in humans and modified. Cost-efficient clinical trials, not new biotechnologies, will make the biggest long-term impact on the drug development industry. 

&nbsp;

## Footnotes

[^1]: This is a direct conclusion from the fact that 90% of drugs that enter clinical trials based on pre-clinical evidence fail for one reason or another. Around 50% fail due to simply not having an effect on the disease, while 25% fail due to having toxic effects not predicted by pre-clinical studies. 

[^2]: [Example 1](https://www.pharmavoice.com/news/5-impactful-drug-trial-failures-from-the-last-year/634422/), [Example 2](https://www.fiercebiotech.com/special-reports/2021s-top-10-clinical-trial-flops). People will say, for drugs that fail clinical trials, that our understanding of the biology of the disease was simply incomplete. Does it mean that our biological understanding was “complete” in the cases where the drug succeeded? I don’t believe so. It’s tantalizing to view our successes as resulting from our own volition and our failures as resulting from unavoidable bad luck.

[^3]: One heuristic to determine whether we have a “deep” understanding of a complex system is to see if we can come up with a model, purely based on our knowledge, that makes predictions of how the system behaves, then experimentally verify those predictions. This is how frequently how research in physics works. <br /><br /> No such model exists for anything in biology. The closest thing we have is AlphaFold, but this model was not constructed based on biological knowledge, and it benefitted from a large and, most importantly, high-quality training dataset - rare in biology. The situation is more dire for “simple” biological systems - for example, a whole human cell - which are made up of millions of proteins and are orders of magnitude more complex than single proteins modeled by AlphaFold. I am not aware of any model that is able to make remotely accurate predictions (even absent understanding) of how a single cell responds to arbitrary stimuli. Going from a single cell to a whole organism containing trillions of cells is another inconceivable jump in complexity. 

[^4]: [Over 50% of peer-reviewed cancer biology papers published in top journals don’t replicate](https://elifesciences.org/articles/71601).

[^5]: Anyone who’s run a biology experiment knows how fickle they are. Use a different source of water, stir your test tube a little bit differently, and you can get completely different results from the exact same experiment. The default expectation when running a biology experiment is that it will fail the first few (or more) times - it takes a lot of trial and error to get an experimental system in biology to even show the expected baseline behavior. <br /><br /> Having experimental systems that are so sensitive to environmental conditions/confounders does not instill confidence in their output. No amount of clever AI models can deal with the fact that most biological datasets (particularly from biological systems above a certain level of complexity, say whole cells and up) are extremely noisy and rife with confounders. Imagine trying to train a large language model to output proper English text from a dataset where the words in every sentence are randomly permuted, misspelled, and swapped with other languages - that’s what current biological datasets are like. 

[^6]: I’m willing to exclude rare monogenic diseases from this category, for which the cause can be unambiguously traced to a single mutation in a single gene. In many of these cases, the precise disease mechanisms are still unclear, but at least the cause is known. The same cannot be said of any common disease. 

[^7]: In a way, natural products themselves are already a product of the test → modify → iterate cycle done many times over. The “test” aspect is done by natural selection selecting for products that improve the fitness of the organism, while the “modify” aspect is done by random genetic mutations. Thus, natural products are optimized for some sort of biological activity related to fitness. 

[^8]: One of my favorite essays, “[Understanding is a poor substitute for convexity](https://www.edge.org/conversation/nassim_nicholas_taleb-understanding-is-a-poor-substitute-for-convexity-antifragility)” by Nassim Taleb, describes in more detail the strategies one can take to ensure long-term gains in a poorly-understood system.