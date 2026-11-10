# Literature guide: assumption strength and proof architecture

Bibliographic and source checks were made on 8 September 2026. Recheck later publication versions when using this guide. These sources support specific comparisons; they do not certify a new manuscript. The examples were selected for proximity to the supplied survival, sieve, and semiparametric discussions.

## How to compare a proposed assumption

Search an academic database with the statistical object and proof task, for example `dependent censoring copula identifiability sieve consistency`, `partially linear Cox neural network efficient score`, or `current status sieve asymptotic normality`. Prioritize The Annals of Statistics, Journal of the American Statistical Association, Journal of the Royal Statistical Society Series B, and Biometrika; include closer papers elsewhere when they answer the mathematical question better.

For each candidate, record the observation scheme, target, estimator, nuisance structure, assumption location, exact proof use, and derived conclusions. Read the proof or supplement containing the relevant step. Compare fixed versus estimated dependence parameters, partial versus full likelihood, censoring versus current status, and a finite parameter versus a functional target.

Classify the proposed condition as one of:

- directly implied by existing premises;
- a primitive restriction comparable to the source;
- stronger than the source because the new model needs additional control;
- stronger than necessary for the current proof;
- an explicit high-level condition whose primitive sufficient conditions remain unproved.

Explain strength using an implication, counterexample, or proof requirement. “Used in a top journal” and “common in the literature” are insufficient explanations. Do not report a conditional theorem as unconditional, or interpret a source's compressed proof as permission to omit a substantive premise.

## Comparators from the four journals

### A. The Annals of Statistics: neural partially linear Cox estimation

**Qixian Zhong, Jonas Mueller, and Jane-Ling Wang (2022). Deep learning for the partially linear Cox model. The Annals of Statistics, 50(3), 1348–1375. DOI: [10.1214/21-AOS2153](https://doi.org/10.1214/21-AOS2153).** Supplement DOI: [10.1214/21-AOS2153SUPP](https://doi.org/10.1214/21-AOS2153SUPP).

Consult the main paper's assumptions and Section 6.5 and the supplement's technical lemmas and Section S2. Design and follow-up restrictions are distinguished from additional regularity for asymptotic normality; model-specific bounds are developed in the proofs. The supplement helps assess how much score algebra and entropy work warrants a separate lemma. Its partially linear Cox setting differs from a joint likelihood with an estimated copula parameter. A regularity condition used for asymptotic normality does not, by itself, establish a new model's least-favorable sieve approximation rate. [Author manuscript](https://par.nsf.gov/servlets/purl/10344993); [publisher issue](https://www.imstat.org/publications/aos/aos_50_3/aos_50_3.pdf).

### B. JASA: dependent censoring with an unknown copula parameter

**Negera Wakgari Deresa and Ingrid Van Keilegom (2024). Copula Based Cox Proportional Hazards Models for Dependent Censoring. Journal of the American Statistical Association, 119(546), 1044–1054. DOI: [10.1080/01621459.2022.2161387](https://doi.org/10.1080/01621459.2022.2161387).**

Compare identification conditions C1–C6, asymptotic conditions D1–D8, Lemma 5.1, and Theorem 5.1. The paper uses a semiparametric event margin and a parametric censoring margin. Its conditions include compactness, bounded covariates, baseline regularity, matrix nonsingularity, and separation of the estimating equation. Lemma 5.1 supplies substantial intermediate estimator properties. This is evidence that explicit high-level separation conditions can have a legitimate role; it is not a justification for imposing every bound as a primitive assumption in a richer nuisance model. [Author publication page](https://negerawd.netlify.app/publication/journal-article/).

### C. JRSS-B: neural likelihood estimation and functional inference

**Wen Su, Qiang Wu, Kin-Yat Liu, Guosheng Yin, Jian Huang, and Xingqiu Zhao (2026). Nonparametric inference for censored data using deep neural networks. Journal of the Royal Statistical Society Series B: Statistical Methodology, advance article qkag060. DOI: [10.1093/jrsssb/qkag060](https://doi.org/10.1093/jrsssb/qkag060).** Published online 2 April 2026; no final issue pagination was shown in the checked version.

Read Conditions C1–C3 and Theorem 3.1 in Section 3, then Theorem 4.1 in Section 4.1. The paper separates truth/design/follow-up conditions, network choices for estimation error, and further rate requirements for functional asymptotic inference. This is a useful organizational comparator. Its nonparametric conditional-hazard target and right-censoring experiment differ from joint unknown-copula semiparametric inference. Do not transplant its functional expansion without checking the new score operator and approximation terms. [Publisher full text](https://academic.oup.com/jrsssb/advance-article/doi/10.1093/jrsssb/qkag060/8572589).

### D. Biometrika: sieve assumptions allocated by statistical conclusion

**Shuwei Li, Tao Hu, Lianming Wang, Christopher S. McMahan, and Joshua M. Tebbs (2024). Regression analysis of group-tested current status data. Biometrika, 111(3), 1047–1061. DOI: [10.1093/biomet/asae006](https://doi.org/10.1093/biomet/asae006).**

Section 4 gives Conditions 1–5 and Theorems 1–3. Smoothness and compactness, design restrictions, and nondegeneracy are stated separately; the consistency, rate, and asymptotic-normality theorems invoke specified subsets and tuning restrictions. This provides a concrete example of matching assumptions to conclusions rather than attaching the complete list to every lemma. The observation mechanism is group-tested current status, so the information and likelihood calculations are not interchangeable with ordinary dependent right censoring. [Publisher article](https://academic.oup.com/biomet/article/111/3/1047/7606770).

## Closely related sources discussed in the project

### E. Neural partially linear current-status inference

**Qiang Wu, Xingwei Tong, and Xingqiu Zhao (2024). Deep partially linear Cox model for current status data. Biometrics, 80(2), ujae024. DOI: [10.1093/biomtc/ujae024](https://doi.org/10.1093/biomtc/ujae024).**

The checked supplement states C1–C10 in Appendix A and gives the Theorem 3 expansion in Appendix C, including its score-equation and stochastic terms. It is useful for concise proof organization and for checking what regularity is explicitly imposed. Its current-status nuisance score has a different form from a baseline operator containing hazard integrals. Do not copy conditional orthogonality equations or infer existence of a deterministic least-favorable approximation sequence merely from a smoothness condition. [Publisher full text](https://academic.oup.com/biometrics/article/80/2/ujae024/7638948).

### F. Informative censoring with spline components

**Zili Liu, Hong Wang, Chunjie Wang, and Xinyuan Song (2026). Simultaneous Variable Selection and Estimation of Survival Model with Informative Censoring. Statistica Sinica, 36(2), 999–1022. DOI: [10.5705/ss.202023.0227](https://doi.org/10.5705/ss.202023.0227).**

The checked supplementary Section S1.1 explicitly bounds the baseline hazards and their sieve approximants. It should not be described as assuming only Lipschitz continuity. Sample-extrema support notation does not establish that a fixed population endpoint has no probability mass. The consistency parameter vector in the checked version does not include an estimated copula association parameter, so its result cannot establish consistency for that additional coordinate without further work. [Publisher record](https://www3.stat.sinica.edu.tw/statistica/J36N2/J36N223/J36N223.html); [publisher preprint](https://www3.stat.sinica.edu.tw/preprint/SS-2023-0227_Preprint.pdf).

## Covering-number reference

**Weigutian Ou and Helmut Bölcskei (2026 revision). Covering Numbers for Deep ReLU Networks with Applications to Function Approximation and Nonparametric Regression. arXiv:2410.06378v2, revised 2 March 2026; listed as to appear in Foundations of Computational Mathematics. Preprint DOI: [10.48550/arXiv.2410.06378](https://doi.org/10.48550/arXiv.2410.06378).** A journal DOI was not verified in this review. [Version and manuscript](https://arxiv.org/abs/2410.06378).

The project cites a covering bound from this work. Before reusing its theorem number or rate formula, inspect the selected version and map depth, widths, sparsity, input domain, and parameter bounds to the actual sieve. A reference for network coverings does not directly establish brackets for a composed likelihood; prove that transfer separately, usually in one short argument.

## Empirical-process reference and citation cautions

**Aad W. van der Vaart and Jon A. Wellner (1996). Weak Convergence and Empirical Processes: With Applications to Statistics. Springer, first edition. DOI: [10.1007/978-1-4757-2545-2](https://doi.org/10.1007/978-1-4757-2545-2).** The publisher also lists a later electronic publication date for this edition; retain the edition used for theorem numbering. [Publisher record](https://link.springer.com/book/10.1007/978-1-4757-2545-2).

The project discussions distinguish the rate theorem numbered 3.4.1 and the bounded-envelope versus Bernstein-norm maximal-inequality formulations around Lemmas 3.4.2–3.4.3 in this edition. This guide does not reproduce their full hypotheses. Read the actual statement before citing a particular lemma and match envelope, metric, entropy integral, and scaling conditions. A correct-looking final inequality does not validate an incorrect pinpoint citation.

The earlier proposed “Pollard (1984), Lemma 4.1” pinpoint for an elementary Euclidean covering estimate was not established and should not be restored. Name a standard volumetric argument or locate a verified source. Likewise, a Hilbert-space projection result does not by itself establish existence and uniqueness of a parameter tuple representing that projection.

## What this comparison supports

The compared articles support a disciplined division among model restrictions, shared primitive regularity, theorem-specific tuning or nondegeneracy, and derived technical work. Which category applies still depends on the new argument. In particular:

- prove a model-specific bound when the stated compactness, positivity, and smoothness already imply it;
- retain a substantive global separation or approximate score condition explicitly if it is the chosen premise of a conditional theorem;
- give stronger conclusions their actual additional hypotheses;
- identify the exact theorem served by a lemma and keep simple one-use calculations within that theorem;
- treat normalization, approximation error, and operator structure as mathematical requirements of the particular experiment.

These are inferences from the comparisons and the supplied proof discussions, not verbatim recommendations issued by the cited journals.
