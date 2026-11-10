# Proof patterns and mathematical checks

Use only the patterns needed for the requested result. All displayed implications have hypotheses; they are not generic conclusions for an arbitrary statistical model. The [literature guide](literature-guide.md) supplies source comparisons. The [source decisions](source-decisions.md) distinguish project conventions from general principles.

## 1. Verify the experiment before manipulating its likelihood

Specify the observed random element, its support, and a dominating measure that includes continuous and discrete components. Check normalization for the entire observed distribution. For a conditional likelihood, identify the conditioning event and its normalizing factor.

For example, with continuous latent times and administrative follow-up at a fixed horizon,
\[
Y=T\wedge C\wedge\tau,\qquad
\Delta_T=I(T\le C\wedge\tau),\quad
\Delta_C=I(C<T,\ C<\tau),\quad
\Delta_\tau=I(T>\tau,C>\tau)
\]
hold up to probability-zero ties. Conditional on covariates \(W=w\), write the two subdensities as \(p_{\pi,T}(t\mid w)\), \(p_{\pi,C}(t\mid w)\), and the endpoint mass as \(r_\pi(w)\). Then
\[
\sum_{j\in\{T,C\}}\int_0^\tau p_{\pi,j}(t\mid w)\,dt+r_\pi(w)=1.
\]
The complete log likelihood includes \(\Delta_\tau\log r_\pi(W)\). For a survival copula it is typically \(r_\pi=K_\alpha\{s_T(\tau),s_C(\tau)\}\). A Lebesgue-null endpoint can have positive probability. Bounded log-hazards on a finite interval do not eliminate that probability.

Once this model definition is correct, do not repeatedly explain it in every proof. Carry the atom through score identities, likelihood distances, and entropy arguments. The elementary bound
\[
\|r_\pi-r_0\|_{L_2(P_W)}^2
\le 2\tau\sum_{j\in\{T,C\}}
\|p_{\pi,j}-p_{0,j}\|_{L_2(dt\,dP_W)}^2
\]
follows directly from normalization and Cauchy–Schwarz. It usually belongs within the relevant proof.

Distinguish direct baseline evaluations from integrated baseline effects. Under a bounded event subdensity,
\[
E_0\{\Delta_j h(Y)^2\}
=\int\!\int_0^\tau h(t)^2p_{0,j}(t\mid w)\,dt\,dP_W(w)
\lesssim\|h\|_{L_2(dt)}^2.
\]
This does not assert that unweighted point evaluation is continuous on \(L_2(dt)\). At the administrative atom, both event indicators vanish; cumulative-hazard terms can still contribute there.

## 2. Keep identification, separation, and inverse control distinct

Qualitative identification has the form \(P_\pi=P_{\pi_0}\Rightarrow\pi=\pi_0\), possibly modulo an explicitly defined equivalence. For neural-network estimators, identify the represented statistical function, not necessarily its weight vector.

A consistency proof often needs population separation:
\[
\inf_{d(\pi,\pi_0)\ge\varepsilon}
\{M(\pi_0)-M(\pi)\}>0\qquad(\varepsilon>0).
\]
Uniqueness, compactness in the relevant topology, and continuity can supply this, but identification alone on a noncompact parameter space cannot. For expanding sieves, check separation over the actual union or a suitable common enclosing class.

A rate proof may additionally need a local lower bound such as
\[
M(\pi_0)-M(\pi)\gtrsim d(\pi,\pi_0)^2.
\]
Neither qualitative identification nor strict monotonicity supplies this automatically. The map \(a\mapsto a^3\) is injective while its derivative at zero vanishes. A local nonzero derivative can support local inverse control; it does not exclude distant roots of an identification equation. Retain a separate global uniqueness argument when the chosen theorem uses it.

For ODE-based recovery, reuse the established differential or integral system. If two candidate trajectories already arise from valid model parameters, their existence is already available. A difference inequality and Gronwall can establish uniqueness or stability without repeating an existence theorem. Stability still requires the forcing term to be controlled in the norm used by the statistical argument.

Do not infer derivative convergence from \(L_2\) convergence of functions. Where justified by boundary conditions and regularity, test against a fixed smooth function and integrate by parts to move derivatives onto the test function. State that operation and the resulting bound instead of importing an unnecessary stronger norm.

## 3. Prevent cancellation when recovering model components

Small error in an additive predictor does not by itself make all components small. For the illustrative product-measure predictor difference
\[
q(t,W)=a(t)+D^\top b+v(X),\qquad Ev(X)=0,
\]
set \(R=D-E(D\mid X)\) and assume \(E(RR^\top)\succeq cI\), with the moments needed below. Conditional centering gives
\[
\tau b^\top E(RR^\top)b
\le\|q\|_{L_2(dt\,dP_W)}^2.
\]
Bound \(D^\top b\) using its second moment. Then
\[
\|a+v\|_{L_2(dt\,dP_W)}^2
=\|a\|_{L_2(dt)}^2+\tau\|v\|_{L_2(P_X)}^2
\]
by centering. These displays expose the noncancellation mechanism. Do not replace residual design nondegeneracy with an unrelated positive-definiteness assumption. This is integration under \(dt\,dP_W\), not an assertion that observed time is independent of covariates.

## 4. Prove consistency before spending effort on a rate

For a sieve maximizer, identify a feasible deterministic approximation \(\pi_{0n}\), show its population approximation error vanishes, obtain uniform stochastic convergence over the actual criterion class, and apply separation. For an approximate maximizer, retain
\[
P_n\ell_{\widehat\pi_n}\ge P_n\ell_{\pi_{0n}}-\epsilon_n.
\]
The required order of \(\epsilon_n\) depends on the conclusion. Consistency may only need \(\epsilon_n=o_p(1)\); a rate or a root-\(n\) expansion may need more.

Finite covering for each fixed sieve does not itself give a uniform law as \(n\) grows. For a uniformly bounded, measurable criterion class, a sup-norm net with \(\log N(\varepsilon)=o(n)\) for every fixed \(\varepsilon>0\) permits a finite-net concentration argument. Without bounded envelopes or this metric, use the appropriate alternative theorem and verify its conditions.

## 5. Transfer entropy in the metric actually needed

First record the exact architecture, domain, weight bound, sparsity, and output constraint of a neural-network class. Match them to the cited covering theorem. Include finite-dimensional and spline contributions unless they have been validly absorbed. A formula proved for another input domain or weight regime needs a justified rescaling or class comparison.

For a pointwise Lipschitz map of component functions,
\[
|\ell_{u}(o)-\ell_{v}(o)|\le C\sum_{k=1}^m A_k|u_k-v_k|(o),
\]
where the \(A_k\) are positive operators, component brackets of widths \(w_k\) give a likelihood bracket centered at a representative with half-width \(C\sum_k A_kw_k\). Verify its norm width using bounds on the \(A_k\). Nonmonotonicity of the likelihood map causes no difficulty for this construction. Simply substituting lower and upper component endpoints into a nonmonotone map is invalid.

If this pointwise inequality and width bound already appear, one sentence supplies the bracketing transfer. An \(L_2\)-Lipschitz inequality alone does not establish pointwise brackets.

For a local bracketing maximal inequality, state the envelope condition, localization norm, entropy integral, and \(n\)-dependent remainder that the selected version requires. Bounded-envelope \(L_2\) and Bernstein-norm formulations are not interchangeable. Verify the exact book statement before attaching a lemma number; see the source caution in the literature guide.

## 6. Close the rate argument once

Work with the same distance in the local curvature, approximation, and empirical-process bounds, or prove the necessary comparison. A common route combines
\[
M(\pi_0)-M(\pi)\gtrsim d(\pi,\pi_0)^2,
\qquad
E\sup_{d(\pi,\pi_0)\le\delta}
|\sqrt n(P_n-P_0)(\ell_\pi-\ell_{\pi_0})|
\lesssim\phi_n(\delta),
\]
with a rate \(r_n\) satisfying \(\phi_n(r_n)\lesssim\sqrt n\,r_n^2\), the scaling conditions of the chosen rate theorem, consistency, approximation, and the maximization relation. This balance alone is not a complete rate theorem. Verify the remaining hypotheses at the application point.

If \(\pi_0\) is outside the sieve, do not pretend it is the empirical comparator. When
\(d(\pi_{0n},\pi_0)=O(r_n)\) and the local likelihood has a suitable \(L_2\) bound, a deterministic comparator fluctuation can be \(O_p(r_n/\sqrt n)\). It is \(o_p(r_n^2)\) when \(\sqrt n r_n\to\infty\). A quadratic population approximation error needs the corresponding upper bound; the lower curvature bound alone does not supply it.

State the resulting rate, including logarithms and all nuisance contributions. Delete unused derivative or cumulative-function corollaries if the paper does not use them. Keep the approximation construction needed for the proof.

## 7. Construct the efficient score in the correct space

Define population tangent directions with the model's centering and boundary constraints. Map them through the score operator and take the appropriate closure in \(L_2^0(P_0)\). Write the efficient score as
\[
\ell^*=\dot\ell_\psi-\Pi_{\overline{\mathcal T}_\eta}\dot\ell_\psi,
\qquad I_{\mathrm{eff}}=P_0\ell^*\ell^{*\top}.
\]
For vector parameters, project componentwise. A closed-space projection exists and is unique. A particular nuisance-direction tuple attaining the projection need not exist or be unique: the score operator can have a nonclosed range or a nontrivial kernel.

If a least-favorable tuple representation is available, state its extra conditions or introduce it conditionally. Otherwise use the abstract projection and approximations to its score. Express orthogonality against each actual nuisance score operator. Integral baseline operators and centered covariate directions generally do not yield the same conditional-mean equation. Derive any conditional characterization from the tangent class; do not copy it from a current-status model with another operator.

Nonsingularity of \(I_{\mathrm{eff}}\) is required to invert it. An efficient-score formula and information bound describe the experiment. Attainment by a particular sieve estimator requires the additional argument below.

## 8. Organize an asymptotic-linearity proof by its remainders

Let \(\pi=(\psi,\eta)\), let \(\ell_n^\dagger(\pi)\) be an approximate efficient score constructed with deterministic directions, and write
\(\|\ell_n^\dagger(\pi_0)-\ell^*\|_{P_0}=r_{\mathrm{LF},n}\).
For a rate \(d(\widehat\pi_n,\pi_0)=O_p(r_n)\), a useful sufficient set of ingredients is:

- an approximate score equation \(P_n\ell_n^\dagger(\widehat\pi_n)=o_p(n^{-1/2})\);
- stochastic equicontinuity of \(\ell_n^\dagger\) on the estimator's neighborhood;
- a population expansion with parameter coefficient \(-I_n\), \(I_n\to I_{\mathrm{eff}}\);
- an orthogonality error of order \(O_p(r_{\mathrm{LF},n}r_n)\) and a quadratic remainder \(O_p(r_n^2)\);
- \(\sqrt n r_{\mathrm{LF},n}r_n\to0\), \(\sqrt n r_n^2\to0\), and score convergence sufficient for the central term.

Prove these from the stated model or retain the relevant ones as explicit high-level conditions. Smoothness of the true nuisance does not by itself imply approximability of least-favorable directions. An arbitrary population perturbation need not be a feasible path in a constrained finite neural-network sieve. A numerical optimum alone does not establish the displayed score equation.

The essential decomposition is
\[
\begin{aligned}
P_n\ell_n^\dagger(\widehat\pi_n)
={}&P_n\ell_n^\dagger(\pi_0)
 +(P_n-P_0)\{\ell_n^\dagger(\widehat\pi_n)-\ell_n^\dagger(\pi_0)\}\\
&+P_0\{\ell_n^\dagger(\widehat\pi_n)-\ell_n^\dagger(\pi_0)\}.
\end{aligned}
\]
Explain each remainder once. Under score differentiation justified by the model, the identity
\[
D_\eta P_0\ell_n^\dagger(\pi_0)[h]
=-P_0\{\ell_n^\dagger(\pi_0)\dot\ell_\eta[h]\}
\]
combined with orthogonality of \(\ell^*\) and a bounded score operator yields the product error by Cauchy–Schwarz. The identity concerns the fixed-law expectation derivative of a model score; verify its regularity and normalization hypotheses.

For likelihoods with exponential functional predictors, prove the population Taylor remainder using derivatives along function paths and integrated bounds. Smoothness of ReLU weights is a different question. A common bounded-envelope argument may need directions uniformly bounded in \(n\), not merely bounded separately for every \(n\).

For deterministic \(g_n\) with \(\|g_n\|_{P_0}\to0\),
\(\sqrt n(P_n-P_0)g_n=o_p(1)\) follows by a variance bound in an iid experiment. This does not automatically apply to directions fitted on the same data. For random directions, supply the appropriate empirical-process or conditional argument without silently changing the estimator.

If the approximate scores have mean zero at the truth, the preceding controls yield
\[
\sqrt n(\widehat\psi_n-\psi_0)
=I_{\mathrm{eff}}^{-1}\frac1{\sqrt n}
\sum_{i=1}^n\ell^*(O_i)+o_p(1).
\]
Apply the relevant central limit theorem and state its covariance. Reserve a semiparametric efficiency claim for the relevant regularity framework as well as the efficient influence-function representation.

## 9. Check that the rate conditions can hold together

In the project-specific form \(\tau_n=a_n\log^2n+n^{-u\nu}\), the sufficient undersmoothing restrictions are
\[
\sqrt n\,a_n^2\log^4n\to0,\qquad u\nu>1/4.
\]
If \(a_n\asymp n^{-\kappa}\), the first holds for \(\kappa>1/4\). If also \(\kappa<1/2\), then \(\sqrt n\tau_n\to\infty\). Check all architecture and approximation restrictions in addition; these inequalities alone do not prove that a proposed architecture is feasible.

Given \(\sqrt n\tau_n\to\infty\), the product condition
\(\sqrt n r_{\mathrm{LF},n}\tau_n\to0\) implies \(r_{\mathrm{LF},n}\to0\); there is no need to impose the latter twice. By contrast, the product condition itself needs proof or an explicit premise.

Write a small rate ledger in working notes: each remainder, its bound, the required limit, and the source of that limit. Transfer only the substantive conditions and shortest implications into the manuscript.
