# Example: Huang (1996) and theorem dependency architecture

Version 1.2.0 · Updated 2026-09-09.

**Jian Huang (1996). Efficient Estimation for the Proportional Hazards Model with Interval Censoring. The Annals of Statistics, 24(2), 540–568. DOI: [10.1214/aos/1032894452](https://doi.org/10.1214/aos/1032894452).**

This is an explanatory reconstruction of the proof architecture supplied by the user, not a verbatim transcription of the paper's formulas or theorem numbering. The bibliographic details and headline results were checked against the [author's institutional publication record](https://research.polyu.edu.hk/en/publications/efficient-estimation-for-the-proportional-hazards-model-with-inte/). The score equations below are schematic conditional inputs: an estimator-specific exact or sufficiently accurate approximate relation must be established before use. They are not identities that follow automatically from maximizing a constrained likelihood.

The paper offers a characteristic semiparametric likelihood dependency architecture. It studies the proportional hazards model with case-1 interval censoring. The finite-dimensional target is the regression coefficient \(\beta\), and the infinite-dimensional nuisance is the baseline cumulative hazard \(\Lambda\). Its ultimate aim goes beyond consistency of the joint MLE to establish

\[
\sqrt n(\widehat\beta_n-\beta_0)
\rightsquigarrow N\{0,I_{\mathrm{eff}}^{-1}\},
\]

and attainment of the semiparametric information bound, despite the cube-root rate for the baseline cumulative-hazard estimator.

The example shows why **settling the final theorem target is only the beginning: logically distinct dependency branches must meet to establish asymptotic normality and efficiency**. In the schematic displays, \(P=P_0\), \(\mathbb G_n=\sqrt n(P_n-P_0)\), and \(a^{\otimes2}=aa^\top\). Norms and joint distances must be chosen consistently with the actual rate and expansion being applied; an unspecified norm is not permission to use a stronger one.

## Step 1. Work backward from the final claim

The final statistical claim is

\[
\sqrt n(\widehat\beta_n-\beta_0)
\rightsquigarrow N(0,I_{\mathrm{eff}}^{-1}),
\qquad\widehat\beta_n\text{ is semiparametrically efficient}.
\]

Consistency or a convergence rate alone cannot establish it. Its proof needs at least three distinct chains.

The first provides estimator localization:

\[
\text{model regularity}\longrightarrow\text{consistency}
\longrightarrow\text{joint convergence rate}.
\]

The second describes information geometry:

\[
\text{parametric score}+\text{nuisance tangent directions}
\longrightarrow\text{efficient score}\longrightarrow I_{\mathrm{eff}}.
\]

The third supplies the root-\(n\) expansion:

\[
\begin{gathered}
\text{estimator score relation}+\text{local smoothness}
+\text{stochastic equicontinuity}+\text{nuisance rate}\\
\longrightarrow\text{asymptotic linear expansion}.
\end{gathered}
\]

Efficiency follows only when the third chain's influence-function representation matches the efficient score from the second chain. A fuller graph is

\[
\begin{array}{ccc}
&\text{Primitive regularity conditions}&\\
\swarrow&&\searrow\\
\text{Identification / separation}&&\text{Score and tangent structure}\\
\downarrow&&\downarrow\\
\text{Consistency}&&\text{Efficient score}\\
\downarrow&&\downarrow\\
n^{-1/3}\text{-type joint rate}&&I_{\mathrm{eff}}\\
\searrow&&\swarrow\\
&\begin{array}{c}
\text{Local score expansion}\\
+\text{ stochastic equicontinuity}\\
+\text{ remainder control}
\end{array}&\\
&\downarrow&\\
&\sqrt n(\widehat\beta_n-\beta_0)
=I_{\mathrm{eff}}^{-1}\mathbb G_n\ell_{\mathrm{eff}}+o_p(1)&\\
&\downarrow&\\
&\text{Asymptotic normality and efficiency}&
\end{array}
\]

The branches serve different purposes and cannot replace one another.

## Step 2. Separate efficient information from estimator convergence

The information calculation determines how much information about \(\beta\) is available in the presence of the infinite-dimensional nuisance \(\Lambda\). Project the ordinary score onto the nuisance tangent space to obtain

\[
\ell_\beta^{\mathrm{eff}}
=\dot\ell_\beta-\Pi(\dot\ell_\beta\mid\mathcal T_\Lambda),
\qquad
I_{\mathrm{eff}}=P_0[(\ell_\beta^{\mathrm{eff}})^{\otimes2}],
\]

with the appropriate closed score space understood in the projection.

This branch answers:

> What is the best possible asymptotic variance for estimating \(\beta\) in this semiparametric model?

It does not establish that the MLE attains the bound. Positive-definite \(I_{\mathrm{eff}}\) establishes nondegenerate efficient information, not the estimator's limiting distribution. Keep efficient information and the estimator's asymptotic expansion as separate branches in the graph.

## Step 3. Consistency supplies localization, not a root-\(n\) result

Consistency of the MLE places the random estimator near the truth:

\[
(\widehat\beta_n,\widehat\Lambda_n)
\longrightarrow(\beta_0,\Lambda_0).
\]

Its downstream function is the passage from the global parameter space to a local neighborhood of the truth, allowing subsequent likelihood and score analysis on suitable shrinking neighborhoods. It is not by itself sufficient for asymptotic normality:

\[
\text{Consistency}\not\Longrightarrow\text{Asymptotic normality}.
\]

Quantitative localization and local score control are still required.

## Step 4. The rate supplies the strength needed for remainder control

The cube-root baseline rate and an initial joint rate for the finite- and infinite-dimensional components provide a calculable scale for the later score remainder. Their role is more specific than simply strengthening consistency.

For example, if a nuisance remainder satisfies

\[
R_n=O_p(\|\widehat\Lambda_n-\Lambda_0\|^2),
\qquad
\|\widehat\Lambda_n-\Lambda_0\|=O_p(n^{-1/3}),
\]

then

\[
R_n=O_p(n^{-2/3})=o_p(n^{-1/2}).
\]

The quadratic remainder premise must itself be established. This is the rate's actual dependency role in a root-\(n\) proof. Instead of labeling a node only “convergence-rate theorem”, record the conclusion consumed downstream:

\[
\|\widehat\Lambda_n-\Lambda_0\|=O_p(n^{-1/3})
\Longrightarrow
\|\widehat\Lambda_n-\Lambda_0\|^2=o_p(n^{-1/2}).
\]

This is **dependency strength matching**: the later theorem needs a quantitative rate making the second-order remainder negligible at the required scale, not merely nuisance consistency.

## Step 5. A cube-root nuisance rate need not prevent root-\(n\) estimation of \(\beta\)

An initial joint bound

\[
\widehat\beta_n-\beta_0=O_p(n^{-1/3})
\]

need not be the best achievable rate for \(\beta\). The key to sharpening it is not root-\(n\) nuisance estimation, but elimination of the nuisance's first-order effect along the appropriate efficient direction.

Schematically, suppose the estimator satisfies the score relation

\[
0=P_n\ell_{\mathrm{eff}}(\widehat\beta_n,\widehat\Lambda_n)
\]

and the population expansion is

\[
P_0\ell_{\mathrm{eff}}(\widehat\beta_n,\widehat\Lambda_n)
=-I_{\mathrm{eff}}(\widehat\beta_n-\beta_0)+R_n.
\]

An \(o_p(n^{-1/2})\) score residual also suffices for this schematic argument. The actual estimator-specific relation and the off-truth score construction require justification.

If efficient-score orthogonality removes the first-order nuisance contribution and the nuisance rate yields \(R_n=o_p(n^{-1/2})\), combine this with

\[
\begin{aligned}
(P_n-P_0)\ell_{\mathrm{eff}}(\widehat\beta_n,\widehat\Lambda_n)
={}&(P_n-P_0)\ell_{\mathrm{eff}}(\beta_0,\Lambda_0)
+o_p(n^{-1/2})
\end{aligned}
\]

to obtain

\[
\sqrt n(\widehat\beta_n-\beta_0)
=I_{\mathrm{eff}}^{-1}\mathbb G_n
\ell_{\mathrm{eff}}(\beta_0,\Lambda_0)+o_p(1).
\]

Thus a cube-root nuisance rate alone does not imply a root-\(n\) target rate. The essential structure is

\[
\begin{gathered}
n^{-1/3}\text{ localization}
+\text{efficient-score orthogonality}\\
+\text{smooth local expansion}
+\text{stochastic equicontinuity}\\
\Longrightarrow o_p(n^{-1/2})\text{ nuisance contamination}
\Longrightarrow\text{root-}n\text{ inference}.
\end{gathered}
\]

Preserve this structure in the dependency graph.

## Step 6. A general semiparametric theorem is a reusable shared node

To establish the model-specific main result, Huang also develops a general semiparametric MLE theorem: under appropriate score, smoothness, information, and stochastic conditions, the finite-dimensional MLE can be asymptotically normal and efficient even when the nuisance estimator converges more slowly than root-\(n\).

Architecturally, this separates **a general semiparametric theorem** from **model-specific verification**. The general implication has the form

\[
\left.
\begin{array}{c}
\text{Localization/rate}\\
\text{Positive efficient information}\\
\text{Score relation}\\
\text{Stochastic equicontinuity}\\
\text{Smooth population expansion}
\end{array}
\right\}
\Longrightarrow\text{root-}n\text{ efficient estimation}.
\]

The current-status proportional hazards argument verifies the inputs. The appropriate dependency is therefore

\[
\text{General theorem}
+\text{verification of every required condition}
\longrightarrow\text{model-specific main result},
\]

not merely “general theorem implies main result”. A citation without the required entropy, smoothness, score-residual, information, or rate verification leaves an unsupported dependency.

## Step 7. Use the example to check circularity

The ordering of results must follow real dependencies rather than numbering. An independently established rate can support asymptotic normality. That rate proof cannot, in turn, use root-\(n\) localization available only from the asymptotic-normality theorem.

The following structure is circular:

\[
\text{Rate theorem}
\longleftarrow\sqrt n\text{-localization of }\widehat\beta_n
\longleftarrow\text{AN theorem}
\longleftarrow\text{Rate theorem}.
\]

Instead, first establish the coarser joint localization

\[
d\{(\widehat\beta_n,\widehat\Lambda_n),(\beta_0,\Lambda_0)\}
=O_p(n^{-1/3}),
\]

then use it as an established input to the efficient-score expansion and sharpen the finite-dimensional rate to

\[
|\widehat\beta_n-\beta_0|=O_p(n^{-1/2}).
\]

The same parameter may acquire successively stronger bounds,

\[
O_p(n^{-1/3})\longrightarrow O_p(n^{-1/2}),
\]

provided the weaker bound is independently established before it supports the stronger argument. This is legitimate rate refinement, not circularity.

## Step 8. The central lesson

The architecture can be summarized as two branches:

\[
\boxed{\begin{array}{c}
\text{Model regularity}\\\downarrow\\
\text{Consistency}\\\downarrow\\
\text{Initial }n^{-1/3}\text{ localization}
\end{array}}
\quad+\quad
\boxed{\begin{array}{c}
\text{Score/tangent structure}\\\downarrow\\
\text{Efficient score}\\\downarrow\\I_{\mathrm{eff}}
\end{array}}
\]

feeding into

\[
\boxed{\begin{array}{c}
\text{Estimator score relation}\\
+\text{ stochastic equicontinuity}\\
+\text{ local smoothness}\\
+\text{ rate-based remainder control}
\end{array}}
\]

and then

\[
\sqrt n(\widehat\beta_n-\beta_0)
=I_{\mathrm{eff}}^{-1}\mathbb G_n\ell_{\mathrm{eff}}+o_p(1)
\quad\Longrightarrow\quad
\text{asymptotic normality and semiparametric efficiency}.
\]

When writing or reviewing another appendix, adopt this **dependency discipline**, rather than copying Huang's formulas:

1. Work backward from the final theorem to the mathematical ingredients it actually consumes.
2. Separate information calculations from estimator convergence.
3. Use consistency for localization.
4. Use rates to check the asymptotic scale of remainders.
5. Do not mistake a slow nuisance rate for the final rate of the finite-dimensional target.
6. Verify the hypotheses of a general theorem when applying it.
7. Establish weaker preliminary results independently before using them to sharpen later conclusions.
8. Make every main claim traceable to primitive assumptions or verified external results through the dependency graph.

Return to [Section 2 of the skill](../SKILL.md#2-build-the-proof-dependency-structure-around-the-target-theorems).
