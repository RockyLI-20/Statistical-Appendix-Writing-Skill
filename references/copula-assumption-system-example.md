# Example: assumption-system audit in a copula-based semiparametric survival model

Version 1.4.0 · Updated 2026-09-09.

This example records an assumption-system audit of a semiparametric survival model with copula dependence, partially linear hazards for both margins, B-spline baseline sieves, and DNN nuisance components. The focus is how one appendix revision assigned different logical statuses to superficially similar regularity conditions:

- An assumption became a derived technical property.
- An assumption became a model or identification condition.
- A theorem-local condition became a shared assumption.
- Vague regularity wording became a functionally interpretable condition.

The purpose is neither mechanically reducing nor increasing the assumption count. Assign each condition the correct functional role, logical status, physical location, and downstream consumer. Assumption and theorem numbers below refer to the project revisions described in the supplied example, not universal numbering conventions.

## Step 1. An important model-specific property need not be primitive

An earlier appendix stated (A3): on the compact set induced by other parameter restrictions, \(K_{1,\alpha}(u,v)\) and \(K_{2,\alpha}(u,v)\) are uniformly bounded away from zero, and the required first and second derivatives of their logarithms are uniformly bounded. It described this condition as preventing singularities in the Frank-copula likelihood.

The condition has important consumers: denominator stability, logarithmic-likelihood boundedness, likelihood Lipschitz control, ODE uniqueness, and local empirical-process bounds. But **importance does not imply primitive status**.

Reexamining the dependencies shows that these bounds follow from more basic conditions. The revised common block retains A1, A2, and A5–A8 rather than the old A3. In the technical argument, bounded parameter and sieve ranges first give

\[
s_T,s_C\in[c_s,1]
\]

uniformly over the sieve. The compact association-parameter range and the Frank copula's regularity then give positive lower bounds for \(K_\alpha,K_{1,\alpha},K_{2,\alpha}\) and bounds for the required derivatives. These yield

\[
|\ell(\pi_1;O)-\ell(\pi_2;O)|\le C\,d_\infty(\pi_1,\pi_2).
\]

The revised Lemma 1 establishes this chain explicitly:

\[
\begin{gathered}
\text{bounded sieve / parameter ranges}
+\text{compact }\alpha\text{-space}
+\text{copula regularity}\\
\Downarrow\\
\text{positive lower bounds for }K_{1,\alpha},K_{2,\alpha}
+\text{derivative bounds}\\
\Downarrow\\
\text{likelihood stability and Lipschitz control}.
\end{gathered}
\]

This replaces a blanket assumption of all required copula bounds. For each model-specific condition, ask whether simpler primitives imply it. If so, prefer primitives \(\rightarrow\) technical result \(\rightarrow\) theorem, rather than presenting a lemma-level property as routine regularity.

## Step 2. Separate model and identification structure from generic regularity

The earlier A4 combined double exclusion restrictions, relevance, common support, a positive conditional-density lower bound, centering, and linear–nonlinear nonconcurvity or positive-definite residual covariance. It included

\[
\begin{aligned}
h_T(t\mid Z,X,V_T,V_C)&=h_T(t\mid Z,X,V_T),\\
h_C(t\mid Z,X,V_T,V_C)&=h_C(t\mid Z,X,V_C),
\end{aligned}
\qquad\theta_{T0}\ne0,\quad\theta_{C0}\ne0.
\]

The primary consumer was joint identification rather than approximation or empirical-process theory. The earlier identification theorem asserted unique identification under (A1)–(A4). Its proof used exclusions to separate marginal structures, relevance and common support to identify the copula parameter, residual covariance nondegeneracy to identify the partially linear decomposition, and centering to remove additive normalization ambiguity.

These are primarily **identification structure**. The revised common assumption block removes A4 and refers to the double-exclusion, relevance, common-support, centering, and nonconcurvity conditions stated in the main text. The identification theorem invokes “(A1)–(A2) and the identification conditions stated in the main text”; consistency and rate results add the identification conditions where needed.

A necessary logical premise need not belong to the common regularity list. Consider placing observation mechanisms, exclusion restrictions, normalization, structural independence, and identification-specific support conditions in the model or identification setup. Ask **whether the condition is regularity or part of the model itself**. Relocation preserves its logical force.

## Step 3. Multiple consumers can justify a shared assumption

An audit does not only remove assumptions. Reconstructing dependencies may reveal that a condition previously introduced late should be stated formally as shared input.

The earlier asymptotic-normality section imposed

\[
\lambda_{\min}\{I_{\mathrm{eff}}(\psi_0)\}>0,
\qquad\sqrt n\,\tau_n^2\to0.
\]

Information nonsingularity has two distinct consumers. The efficient-information theorem needs it to express the finite inverse-information bound for regular estimation as \(I_{\mathrm{eff}}^{-1}(\psi_0)\); the revised Theorem 4 invokes A8 for this step. The asymptotic-normality theorem also needs it after \(I_n\to I_{\mathrm{eff}}(\psi_0)\), to obtain

\[
\sqrt n(\widehat\psi_n-\psi_0)
=I_{\mathrm{eff}}^{-1}(\psi_0)
\frac1{\sqrt n}\sum_{i=1}^n\ell_\psi^*(O_i;\pi_0)+o_p(1).
\]

The revision therefore introduces the shared assumption

\[
\text{(A8)}\qquad I_{\mathrm{eff}}(\psi_0)\text{ is nonsingular}.
\]

It supports both the finite inverse-information bound and inversion in the asymptotic expansion. Its placement follows its consumer structure. A condition used only by one stronger theorem can remain local; shared use across distinct claims can justify a shared block. Do not label a condition “AN-only” without checking all consumers. The undersmoothing condition remains a separate requirement with its own role.

## Step 4. Make the functional role visible in the statement

Earlier baseline regularity said that \(\zeta_{T0}\) and \(\zeta_{C0}\) were “\(u\)-smooth” on \([0,\tau]\), while the spline condition specified quasi-uniform knots and \(q_n\asymp n^\nu\). The wording did not explicitly identify the function space or connect readily to a spline approximation theorem.

The revised conditions state

\[
\zeta_{T0},\zeta_{C0}\in C^u[0,\tau],
\]

and specify fixed spline order \(r>u\), quasi-uniform knots, and \(q_n\asymp n^\nu\). Their function becomes recognizable:

\[
C^u\text{ smoothness}+r>u+\text{quasi-uniform knots}
\Longrightarrow\text{deterministic B-spline approximation control}.
\]

This supplies sieve approximations \(\zeta_{T0,n},\zeta_{C0,n}\) with the required approximation property. Revised Lemma 1 uses these inputs to construct them.

A condition should do more than sound like regularity. Its wording should expose condition \(\rightarrow\) mathematical mechanism \(\rightarrow\) consumer. For example, \(f_0\in C^s\) connects more directly to approximation theory than “sufficiently smooth”, and \(\lambda_{\min}\{I_{\mathrm{eff}}(\psi_0)\}>0\) connects more directly to inversion than “the model is nondegenerate”.

## Step 5. Record the revised assumption ledger

| Condition | Functional role | Logical status after audit | Main consumer |
|---|---|---|---|
| Bounded supports / covariate effects | Likelihood-envelope control | Primitive assumption | ULLN, empirical-process control |
| Compact finite-dimensional parameter space | Compactness / interiority | Primitive assumption | Consistency, local expansion |
| Positive lower bounds for \(K_{1,\alpha},K_{2,\alpha}\) and derivative bounds | Likelihood stability | Derived technical property | Likelihood Lipschitzness, local bounds |
| Double exclusion / relevance / common support | Identification | Model / identification structure | Identifiability, local inverse relation |
| Centering / nonconcurvity | Uniqueness of partially linear decomposition | Identification structure | Identifiability |
| \(\zeta_{T0},\zeta_{C0}\in C^u\) | Baseline approximation | Primitive assumption | Spline approximation |
| Spline order \(r>u\), quasi-uniform knots, \(q_n\) growth | Approximation–complexity balance | Sieve condition | Rate theorem |
| DNN compositional Hölder and architecture conditions | Nonlinear approximation–estimation trade-off | Sieve / primitive condition | Entropy and rate |
| Nonsingular \(I_{\mathrm{eff}}(\psi_0)\) | Inferential nondegeneracy | Shared primitive assumption | Information bound and asymptotic normality |

This is an internal ledger, not a mandatory manuscript table. It answers both “Why is this condition here?” and “Why is it an assumption rather than a lemma or model restriction?”

## Step 6. Extract the general audit rule

The lesson is not that the earlier draft simply had “wrong assumptions”. Reconstructing the dependencies changed their classification:

- **A3: primitive assumption to derived technical property**, because boundedness, compactness, and copula regularity supply the bounds.
- **A4: common assumption to model / identification structure**, because its primary purpose is identification.
- **Information nonsingularity: theorem-local condition to shared A8**, because both information-bound and asymptotic-normality results consume it.
- **Informal smoothness to an explicit function-space condition**, because the statement should connect directly to its mathematical consumer.

Before choosing assumption numbers, ask in order:

1. What does this condition control?
2. Which dependency requires it?
3. Is it primitive or derivable?
4. Is it model structure or regularity?
5. Is it shared or theorem-specific?
6. Can its statement be weakened or made more explicit?

Only then decide whether it belongs as a model condition, assumption, technical lemma, high-level condition, or theorem-specific premise. **Every condition should occupy the weakest and most natural logical position that still supports all its consumers.**

Return to [Section 4 of the skill](../SKILL.md#4-build-and-audit-the-assumption-system-from-proof-dependencies).
