# Example: Huang (1996) and notation architecture

Version 1.3.0 · Updated 2026-09-09.

**Jian Huang (1996). Efficient Estimation for the Proportional Hazards Model with Interval Censoring. The Annals of Statistics, 24(2), 540–568. DOI: [10.1214/aos/1032894452](https://doi.org/10.1214/aos/1032894452).**

Huang (1996) illustrates the notation architecture of a semiparametric paper. The case-1 interval-censored proportional hazards model requires simultaneous estimation of a finite-dimensional regression parameter and an infinite-dimensional baseline cumulative hazard. The regression estimator achieves root-\(n\) asymptotic normality and the information bound while the baseline estimator has a cube-root convergence rate.

Rather than repeating the theorem dependencies, this example examines how notation distinguishes observations, finite-dimensional targets, infinite-dimensional nuisances, truths, estimators, and efficient-score objects. The ledgers below organize the supplied example using this skill's audit framework; they are not tables reproduced from Huang's paper.

## Step 1. Establish an object taxonomy from the model

For case-1 interval censoring, Huang writes an observation as

\[
X=(\delta,U,Z),\qquad\delta=1\{T\le U\},
\]

where \(U\) is the examination time, \(Z\) the covariate vector, and \(\delta\) indicates whether the event has occurred by examination.

The principal model parameters are \(\theta\), the finite-dimensional regression parameter, and \(\Lambda\), the infinite-dimensional baseline cumulative hazard. Before reading a proof, the model notation should already identify these different types:

\[
\boxed{\text{finite-dimensional target: }\theta},
\qquad\boxed{\text{infinite-dimensional nuisance: }\Lambda}.
\]

The first audit step is to **identify mathematical types before judging symbol choices**. An initial ledger is:

| Symbol | Meaning | Mathematical type | Statistical role |
|---|---|---|---|
| \(X\) | Observed datum | Random vector | Observation |
| \(\delta\) | Current-status indicator | Binary variable | Observed response |
| \(U\) | Examination time | Scalar random variable | Observation mechanism |
| \(Z\) | Covariate | Vector | Observed covariate |
| \(\theta\) | Regression coefficient | Finite-dimensional vector | Target parameter |
| \(\Lambda\) | Baseline cumulative hazard | Monotone function | Nuisance parameter |

The important feature is not the literal choice of \(\theta\) and \(\Lambda\), but the visual and mathematical distinction between the parameter types. Preserve the principle in a new paper without mechanically copying the letters.

## Step 2. Build truth–estimator notation families

The true parameters are \(\theta_0,\Lambda_0\), and their MLEs are \(\widehat\theta_n,\widehat\Lambda_n\). The consistency result distinguishes these objects, giving two coherent families:

\[
\theta\longrightarrow\theta_0\longrightarrow\widehat\theta_n,
\qquad
\Lambda\longrightarrow\Lambda_0\longrightarrow\widehat\Lambda_n.
\]

Each family encodes both **parameter identity** and **asymptotic role**. The objects \(\theta_0\) and \(\widehat\theta_n\) visibly belong to the same parameter family. The subscript zero identifies population truth, while the hat and sample-size index identify a sample-dependent estimator.

Readers can therefore recognize \(\widehat\theta_n-\theta_0\) as finite-dimensional estimation error and \(\widehat\Lambda_n-\Lambda_0\) as infinite-dimensional nuisance estimation error without revisiting their definitions. This is the main benefit of a coherent notation family.

## Step 3. Keep derived objects connected to their primitive objects

The baseline survival function \(S_0(t)\) and its estimator

\[
\widehat S_n(t)=\exp\{-\widehat\Lambda_n(t)\}
\]

retain the same truth and estimator conventions as the cumulative hazards:

\[
\Lambda_0\longleftrightarrow S_0,
\qquad\widehat\Lambda_n\longleftrightarrow\widehat S_n.
\]

The consistency theorem states convergence of \(\widehat\theta_n\) to \(\theta_0\) and of \(\widehat S_n(t)\) to \(S_0(t)\). A derived object need not acquire elaborate notation merely to signal that it is a transformation.

More generally, for \(\psi=T(\eta)\), use

\[
\eta_0\longrightarrow\psi_0=T(\eta_0),
\qquad
\widehat\eta_n\longrightarrow\widehat\psi_n=T(\widehat\eta_n),
\]

rather than symbols for the derived truth and estimator disconnected from their original parameter family.

## Step 4. Give distribution notation a fixed role

Huang uses \(G\) for the distribution function of the examination time \(U\). It also supplies the integrating measure in the nuisance convergence metric. The baseline rate takes the form

\[
\left\{\int_{\tau_0}^{\tau_1}
[\widehat\Lambda_n(u)-\Lambda_0(u)]^2\,dG(u)\right\}^{1/2}
=O_p(n^{-1/3}).
\]

The shorter expression \(\|\widehat\Lambda_n-\Lambda_0\|_2=O_p(n^{-1/3})\) omits important information unless that norm has already been defined. The actual object has a particular measure and integration domain:

\[
\|\widehat\Lambda_n-\Lambda_0\|_{L_2(G;[\tau_0,\tau_1])}.
\]

If a new appendix abbreviates this as \(d(\widehat\Lambda_n,\Lambda_0)\), first verify that

\[
d^2(\Lambda_1,\Lambda_2)
=\int_{\tau_0}^{\tau_1}\{\Lambda_1(u)-\Lambda_2(u)\}^2\,dG(u),
\]

or the exact applicable definition, is stated. **A convergence rate is incomplete unless its topology is identifiable.**

## Step 5. Encode the target parameter in score notation

For semiparametric efficiency of \(\theta\), the paper introduces the efficient score \(\ell_\theta^*(X)\) and information \(I(\theta)\). Theorem 3.1 supplies their explicit expressions.

The subscript in \(\ell_\theta^*\) identifies the efficient score for the finite-dimensional target \(\theta\), rather than a nuisance score or the full likelihood score. The corresponding information supplies the limiting covariance \(I(\theta_0)^{-1}\), giving another family:

\[
\theta\longrightarrow\ell_\theta^*\longrightarrow I(\theta).
\]

This principle is particularly useful in modern models with several nuisance blocks. For \(\eta=(\eta_1,\eta_2,\eta_3)\), prefer

\[
\dot\ell_{\eta_1}[h_{\eta_1}],\qquad
\dot\ell_{\eta_2}[h_{\eta_2}],\qquad
\dot\ell_{\eta_3}[h_{\eta_3}],
\]

so both the parameter block and its perturbation direction are visible.

## Step 6. Give auxiliary functions identifiable consumers

In the efficient-information calculation, auxiliary functions such as \(Q(u,\delta,z)\) and \(O(u\mid z)\) simplify the efficient score; \(R(u,z)\) compresses the information formula. The paper also defines \(a^{\otimes2}=aa^\prime\) for a column vector \(a\in\mathbb R^d\).

These symbols have explicit consumers:

\[
Q,O\longrightarrow\ell_\theta^*,\qquad
R\longrightarrow I(\theta).
\]

This suggests a practical test. If removing a definition merely requires restoring a short expression at one location without reducing readability, the symbol may be unnecessary. Conversely, auxiliary notation is justified when an expression recurs, is long, has independent statistical meaning, or participates directly in an important theorem.

Judge notation by asking **whether it has a clear mathematical consumer**, not simply by counting symbols.

## Step 7. Align parameter, score, and information dimensions

With \(a^{\otimes2}=aa^\prime\) for a column vector in \(\mathbb R^d\), a target \(\theta\in\mathbb R^d\) has an efficient score in \(\mathbb R^d\) and information

\[
I(\theta)=E[\{\ell_\theta^*(X)\}^{\otimes2}]
\in\mathbb R^{d\times d}.
\]

Thus \(I(\theta_0)^{-1}\) has the correct shape to be the covariance of \(\sqrt n(\widehat\theta_n-\theta_0)\). The asymptotic-normality result is stated as

\[
\sqrt n(\widehat\theta_n-\theta_0)
\rightsquigarrow N\{0,I(\theta_0)^{-1}\}.
\]

A dimension audit therefore checks the mathematical compatibility of

\[
\text{parameter}\rightarrow\text{score}\rightarrow
\text{information}\rightarrow\text{limiting covariance},
\]

not merely its typography.

## Step 8. Preserve different convergence scales for different parameters

Both \(\widehat\theta_n-\theta_0\) and \(\widehat\Lambda_n-\Lambda_0\) are estimation errors, but their asymptotic behavior differs: the former is root-\(n\), while the baseline nuisance has a cube-root rate. Having hats and arising from joint maximum likelihood does not imply a common component rate.

An aggregate statement \(d(\widehat\pi_n,\pi_0)=O_p(r_n)\), without the component structure of \(d\), can conceal the difference between

\[
|\widehat\theta_n-\theta_0|=O_p(n^{-1/2}),
\qquad
\|\widehat\Lambda_n-\Lambda_0\|=O_p(n^{-1/3}).
\]

For a product parameter \(\pi=(\theta,\eta)\), check whether an aggregate metric hides different component rates. When needed, retain separate \(r_{\theta,n}\) and \(r_{\eta,n}\), or state which component determines the overall rate.

## Step 9. Construct an authoritative notation ledger

Organizing Huang's current-status proportional hazards setting using this section's framework gives:

| Symbol | Meaning | Mathematical type | Domain / dimension | Role | Notation family |
|---|---|---|---|---|---|
| \(X=(\delta,U,Z)\) | Observed datum | Random vector | Observation space | Observation | \(X_i\) |
| \(\delta\) | Current-status indicator | Binary | \(\{0,1\}\) | Observed outcome | — |
| \(U\) | Examination time | Scalar random variable | Time domain | Observation mechanism | \(G\) |
| \(G\) | Distribution of \(U\) | Distribution function / measure | Time domain | Integration measure | \(U\) |
| \(Z\) | Covariate vector | Vector | \(\mathbb R^d\) | Covariate | \(\theta\) |
| \(\theta\) | Regression parameter | Vector | \(\Theta\subseteq\mathbb R^d\) | Finite-dimensional target | \(\theta_0,\widehat\theta_n\) |
| \(\theta_0\) | True regression parameter | Vector | \(\Theta\) | Truth | \(\theta\) |
| \(\widehat\theta_n\) | MLE of \(\theta_0\) | Random vector | \(\Theta\) | Estimator | \(\theta\) |
| \(\Lambda\) | Baseline cumulative hazard | Monotone function | Function space | Nuisance parameter | \(\Lambda_0,\widehat\Lambda_n\) |
| \(\Lambda_0\) | True baseline cumulative hazard | Function | Function space | Truth | \(\Lambda\) |
| \(\widehat\Lambda_n\) | MLE of \(\Lambda_0\) | Random function | Estimated function space | Nuisance estimator | \(\Lambda\) |
| \(S_0\) | Baseline survival function | Function | Time domain | Derived truth | \(\Lambda_0\) |
| \(\widehat S_n\) | Estimated baseline survival | Random function | Time domain | Derived estimator | \(\widehat\Lambda_n\) |
| \(Q,O,R\) | Auxiliary functions | Scalar functions | Specified arguments | Efficient-information calculation | \(\ell_\theta^*,I(\theta)\) |
| \(\ell_\theta^*\) | Efficient score for \(\theta\) | Vector-valued function | Values in \(\mathbb R^d\) | Inferential object | \(I(\theta)\) |
| \(I(\theta)\) | Efficient information | Matrix | \(\mathbb R^{d\times d}\) | Information | \(\ell_\theta^*\) |

This internal reconstruction checks that every important symbol has one identifiable mathematical role; it is not an original table from the paper.

## Step 10. Apply the three notation audits

The example illustrates the three audits.

**Collision audit.** The families \(\theta,\Lambda,S,G\) have distinct roles. Regression parameters, baseline functions, survival functions, and the examination-time distribution are not collapsed into one symbol.

**Undefined-object audit.** Auxiliary notation such as \(Q,O,R,a^{\otimes2}\) is defined before the main conclusions using it. The relation between efficient score and information is recognizable.

**Role-ambiguity audit.** The objects \(\theta_0,\Lambda_0\) are truths, whereas \(\widehat\theta_n,\widehat\Lambda_n\) are estimators. The fixed role of \(G\) as the examination-time distribution carries through to the nuisance metric's integrating measure.

There is no need to rename the system merely to make it look more modern. **Good notation should usually be preserved, not redesigned.**

## Step 11. Do not copy the notation mechanically

This architecture is an example rather than a universal template. Its principal nuisance is a baseline cumulative hazard \(\Lambda\); the example does not use the three-layer truth–sieve-approximation–estimator system common in modern sieve arguments.

If a new estimator requires a deterministic sieve approximation, explicitly distinguish

\[
\eta_0\in\mathcal H,\qquad
\eta_{0n}\in\mathcal H_n,\qquad
\widehat\eta_n\in\mathcal H_n.
\]

The use of \(\Lambda_0,\widehat\Lambda_n\) in the example does not justify omitting an approximation with an independent mathematical role in a new paper.

Similarly, for \(\eta=(\Lambda,f,g)\), expand the family to reflect the actual component structure rather than forcing every infinite-dimensional object into one \(\Lambda\). Adopt **role-based notation discipline**, not the literal symbol choices.

## Step 12. Extract the general lesson for Section 3

The architecture has four layers:

\[
\begin{aligned}
\text{Data:}&\quad X=(\delta,U,Z),\\
\text{Parameters:}&\quad(\theta,\Lambda),\\
\text{Asymptotic roles:}&\quad(\theta_0,\Lambda_0)
\quad\text{versus}\quad(\widehat\theta_n,\widehat\Lambda_n),\\
\text{Inference:}&\quad\theta\longrightarrow\ell_\theta^*
\longrightarrow I(\theta)\longrightarrow I(\theta_0)^{-1}.
\end{aligned}
\]

Nuisance convergence retains its own metric structure,

\[
\left\{\int(\widehat\Lambda_n-\Lambda_0)^2\,dG\right\}^{1/2}.
\]

After Section 3, a new methodology paper should offer the same readable progression from data objects to parameters, truth/approximation/estimator roles, and score/information/inferential objects.

Every convergence statement should answer: **Which object? Relative to which truth? Under which metric? On which domain? At which asymptotic scale?** This is the notation system's substantive function in a theoretical appendix.

Return to [Section 3 of the skill](../SKILL.md#3-establish-and-audit-a-unified-notation-system).
