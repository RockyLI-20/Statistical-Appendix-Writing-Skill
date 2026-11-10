# Section 5 examples: identifying and organizing technical lemmas through appendix revisions

Version 1.5.0 · Updated 2026-09-09.

These examples come from successive revisions of a copula-based semiparametric survival appendix. They illustrate when an assumption becomes a derived result, when a necessary short transition belongs inline, how qualitative and quantitative conclusions differ, and when multiple conclusions legitimately belong in one lemma. The labels refer to the project revisions described here.

## Example 1. A property removed from the assumptions still needs a supplier

The earlier A3 assumed positive uniform lower bounds for the Frank-copula partial derivatives \(K_{1,\alpha}(u,v),K_{2,\alpha}(u,v)\) and boundedness of the required logarithmic derivatives. Section 4's audit identified this as an unsuitable primitive assumption.

Removing it does not remove later proofs' need for the property. Section 5 must answer: **Who now supplies this bound?**

Revised Lemma 1 uses bounded log-baseline hazards, bounded covariate effects, and compact parameter ranges to obtain

\[
s_T,s_C\in[c_s,1].
\]

Regularity of the copula map on this compact range then supplies positive lower bounds for \(K_\alpha,K_{1,\alpha},K_{2,\alpha}\), followed by

\[
|\ell(\pi_1;O)-\ell(\pi_2;O)|\le C\,d_\infty(\pi_1,\pi_2).
\]

The revised architecture is primitive boundedness/compactness \(\rightarrow\) lemma-level copula stability \(\rightarrow\) likelihood Lipschitz control. **Removing an overstrong assumption creates an obligation to prove its needed consequence.** Section 4 determines that the property should not be assumed; Section 5 determines where to prove it.

## Example 2. Component brackets need a likelihood-transfer argument, usually not another lemma

The spline, finite-dimensional, and two neural-network components admit their respective complexity bounds. For example,

\[
\log N_{[]}\{\epsilon,\mathcal F_\delta,L_2(P_X)\},\quad
\log N_{[]}\{\epsilon,\mathcal G_\delta,L_2(P_X)\}
\lesssim s_n\log\frac{CA_n}{\epsilon}.
\]

This does not alone establish

\[
\log N_{[]}\{\epsilon,\mathcal D_\delta,L_2(P)\}
\lesssim s_n\log\frac{C\mathfrak L_n}{\epsilon},
\]

because \(\mathcal D_\delta\) is a likelihood-difference class rather than a component parameter class.

The earlier proof compressed this step into “Combining these componentwise brackets with (2), the product-bracketing rule … gives …”. The revision states the mechanism: “Applying the preceding pointwise Lipschitz bound to the componentwise brackets and then taking products …”.

The chain is component brackets + pointwise likelihood Lipschitz map \(\rightarrow\) induced likelihood brackets \(\rightarrow\) bracketing entropy integral \(\rightarrow\) localized empirical-process modulus. The transfer uses the pointwise bound to enclose each induced likelihood by a representative plus or minus a width envelope; it does not require monotonicity of the likelihood in its components.

Requiring this justification is mathematically substantive, but usually does not justify another standalone lemma. Once the pointwise Lipschitz property is established, one accurate sentence applying it to component brackets can complete the local transition. **A necessary justification does not automatically require standalone lemma status.**

## Example 3. Reuse qualitative identification, but prove the new Gronwall stability bound

The earlier identification argument recovers the two marginal survivals uniquely from a given observed law and copula parameter through an initial-value problem. Population curvature needs more than equality when observed laws coincide: it requires quantitative control of marginal differences.

Revised Lemma 3 reuses the ODE representation

\[
\partial_y s_{T,\pi}
=-\frac{p_{\pi,1}}{K_{1,\alpha}(s_{T,\pi},s_{C,\pi})},
\qquad
\partial_y s_{C,\pi}
=-\frac{p_{\pi,0}}{K_{2,\alpha}(s_{T,\pi},s_{C,\pi})}.
\]

The uniform Lipschitz control from Lemma 1 supports comparison of the two systems and a Gronwall bound. When the association parameter is held fixed, a suitable observed-law distance can yield

\[
\|s_{T,\pi}-s_{T,0}\|_2+\|s_{C,\pi}-s_{C,0}\|_2
\le C\,d_{\mathrm{obs}}(P_\pi,P_{\pi_0}).
\]

If \(\alpha\) also varies, the ODE comparison generally includes \(|\alpha-\alpha_0|\) in the forcing bound. Establish separate control of that difference before absorbing it into the observed-law distance. Use the norms and regularity actually established for the model.

Thus **ODE uniqueness is different from ODE perturbation stability**, just as identification is different from quantitative inverse control. Reuse the established identity and prove the new estimate. Neither repeat the entire identification proof nor replace the stability argument by “By identifiability, the parameters are close”.

## Example 4. A lemma may have multiple conclusions if each has a consumer

Revised Lemma 3 establishes local quadratic behavior,

\[
c_1d^2(\pi,\pi_0)\le P\ell(\pi_0)-P\ell(\pi)
\le c_2d^2(\pi,\pi_0),\qquad d(\pi,\pi_0)<\epsilon_0,
\]

and global separation,

\[
\sup_{\pi\in\cup_n\Pi_n:\,d(\pi,\pi_0)\ge\epsilon}
P\ell(\pi)<P\ell(\pi_0).
\]

Why retain both? The consumer audit distinguishes their uses.

**Global separation supports consistency.** The consistency proof uses

\[
c_\epsilon=P\ell(\pi_0)
-\sup_{d(\pi,\pi_0)\ge\epsilon}P\ell(\pi)>0
\]

to turn empirical near-maximization into \(d(\widehat\pi_n,\pi_0)\to_p0\). Local curvature does not make this global input dispensable.

**Local quadratic bounds support the rate theorem.** The rate proof needs the quadratic scale of criterion loss and a localized modulus. It uses Lemma 2 to construct the rate function, Lemma 3 for criterion control, and then the van der Vaart–Wellner rate theorem.

The two conclusions share a coherent role—population criterion behavior—and each has a consumer. Their number alone does not make the lemma oversized. If there were no consistency theorem or other global consumer, the global conclusion would need a new deletion test.

## Example 5. Why the localized empirical-process result deserves its own lemma

The localized result is not included merely to display an entropy calculation. Its output is the modulus directly required by the rate proof:

\[
\begin{aligned}
E^*\sup_{\pi\in B_\delta}
|\mathbb G_n\{\ell(\pi)-\ell(\pi_{0n})\}|
\le C\left[
\delta\sqrt{s_n\log\frac{C\mathfrak L_n}{\delta}}
+\frac{s_n}{\sqrt n}\log\frac{C\mathfrak L_n}{\delta}
\right].
\end{aligned}
\]

The proof develops component bracketing bounds, transfers them to the likelihood class through its Lipschitz control, and applies an entropy integral and maximal inequality. The rate proof then explicitly invokes Lemma 2 and uses the bound to construct \(\varphi_n(\delta)\), verifying the rate theorem's modulus condition.

Its contract is clear: **input:** component complexity and likelihood modulus; **output:** localized empirical-process rate; **consumer:** convergence-rate theorem. Its independent, describable, verifiable role in the dependency graph justifies the lemma, not proof length alone.

## Example 6. Construct the technical lemma ledger

The technical layer can be organized as follows:

| Technical result | Functional role | Main output | Main consumer |
|---|---|---|---|
| Lemma 1 | Approximation + global likelihood complexity | \(\pi_{0n}\) approximation; covering/ULLN; compact-range likelihood regularity | Consistency; later local bounds |
| Lemma 2 | Localized stochastic control | Localized bracketing / empirical-process modulus | Convergence rate |
| Lemma 3 | Population criterion behavior | Local quadratic curvature + global separation | Rate + consistency |
| Gronwall calculation within Lemma 3 | Quantitative inverse stability | Observed-law control, with required association-parameter control, gives marginal/parameter control | Lemma 3 curvature/separation |
| Component-bracket transfer within Lemma 2 | Likelihood-class entropy transfer | Component brackets yield likelihood brackets | Lemma 2 |
| Calculation \(s_n\Gamma_n=O(n\tau_n^2)\) | Rate-function verification | Required scale comparison | Rate theorem; inline |

The last row illustrates that a necessary calculation need not become a lemma. Section 5 seeks the **shortest complete mathematical infrastructure**, rather than the largest number of technical lemmas: assumptions \(\rightarrow\) necessary technical results \(\rightarrow\) main-theorem proofs.

Return to [Section 5 of the skill](../SKILL.md#5-construct-and-verify-the-technical-lemma-layer).
