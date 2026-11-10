# Section 7 examples

Version 1.7.0 · Updated 2026-09-09.

These eleven examples come from successive audits of the same statistical appendix. They span material requiring derivation, material needing only a short bridge, and material to omit from the manuscript. The original example numbers are retained, including gaps.

## Example 1. Component brackets to likelihood brackets: retain the minimal transfer mechanism

The earlier argument controlled parameter-component covering or bracketing complexity, but the induced likelihood class is a different object. Component brackets require a mapping before they yield likelihood brackets.

The existing pointwise Lipschitz control supplies the mechanism. A bound such as

\[
|\ell(\pi_1;O)-\ell(\pi_2;O)|\le C\,d_\infty(\pi_1,\pi_2)
\]

supports a sup-norm transfer. For \(L_2\) component brackets, use the established pointwise width-envelope bound and verify its \(L_2\) width; the sup-norm display alone does not supply that conclusion. Form products of component brackets and use the likelihood map to enclose the induced functions.

No additional “likelihood bracket lemma” is needed when this mechanism is already available. The minimum sufficient transition is component brackets + compatible pointwise likelihood control \(\Rightarrow\) likelihood brackets. **Repair a missing bridge without maximizing its exposition.**

## Example 2. Identification to a quantitative inverse bound: a stronger claim needs new mathematics

Point identification establishes

\[
P_\pi=P_{\pi_0}\Rightarrow\pi=\pi_0,
\]

whereas the rate proof needs

\[
d(\pi,\pi_0)\le C\,d_{\mathrm{obs}}(P_\pi,P_{\pi_0}).
\]

The historical audit distinguished completed point identification from the stronger inverse bound needed for local quadratic criterion control. It also noted that the observable identification equation involved derivatives not controlled by \(L_2\) convergence.

“By identifiability, the parameters are close” does not fill this gap. **Qualitative uniqueness does not imply quantitative stability.** Treat the stronger conclusion as new mathematical content.

## Example 3. ODE uniqueness to Gronwall stability: reuse the structure, show the new estimate

Identification already represented the marginal survivals as unique solutions of an initial-value problem. The curvature proof need not reprove existence and uniqueness, but must compare the systems at \(\pi\) and \(\pi_0\).

Retain the ODE representation, uniform Lipschitz control of its right-hand side, comparison of the systems, and application of Gronwall and Cauchy–Schwarz. At fixed copula parameter, the resulting bound has the form

\[
\|s_{T,\pi}-s_{T,0}\|_2+\|s_{C,\pi}-s_{C,0}\|_2
\le C\|(p_{\pi,1}-p_{0,1},p_{\pi,0}-p_{0,0})\|_2.
\]

If the copula parameter varies, include its difference in the forcing bound and establish separate control before absorbing that term. **Reuse the established representation; show the genuinely new stability argument.** Gronwall itself needs no new proof; the model-specific comparison must be visible.

## Example 4. The calculation \(s_n\Gamma_n=O(n\tau_n^2)\): short does not mean dispensable

Rate-theorem applicability depends on this bound. Merely citing growth conditions hides whether polynomial and logarithmic factors match. Retain the decisive arithmetic:

\[
\log A_n=O\{(\log n)^2\},\qquad
\Gamma_n=O\{(\log n)^2\},
\]

\[
s_n=O(na_n^2\log n),\qquad\tau_n\ge a_n\log^2n,
\]

and hence

\[
s_n\Gamma_n=O\{na_n^2(\log n)^3\}=O(n\tau_n^2).
\]

**Short does not imply dispensable.** Show dominant orders when they determine whether a named theorem applies.

## Example 5. Deriving \(B_T[a_T]\): show the origin of a model-specific object

Defining \(B_T[a_T](y)=\int_0^yh_{0T}(s)a_T(s)\,ds\) without motivation makes it appear arbitrary. Instead, introduce

\[
\zeta_{T,\varepsilon}=\zeta_{T0}+\varepsilon a_T,
\qquad
H_{0T,\varepsilon}(y)=\int_0^y
e^{\zeta_{T0}(s)+\varepsilon a_T(s)}\,ds.
\]

Using \(e^{\zeta_{T0}(s)}=h_{0T}(s)\) yields the directional derivative

\[
B_T[a_T](y)=\int_0^yh_{0T}(s)a_T(s)\,ds,
\]

followed by the nuisance score. The sufficient exposition is **path → non-obvious intermediate functional → score**, without every routine chain-rule term.

## Example 8. \(L_2\) convergence does not control derivatives or point evaluations

The audit noted that \(\|S_\pi-S_0\|_2\to0\) does not establish convergence of \(S_{V_T},S_{V_C},S_{V_TV_C}\). Consequently, the derivative-based observable identification equation cannot be imported into the rate argument on the basis of \(L_2\) convergence alone.

The revision instead used a weak integrated identification functional to obtain the required local bound

\[
|\alpha-\alpha_0|\le C\|S_\pi-S_0\|_2
\]

under the relevant identification and nondegeneracy conditions. Do not hide transitions from \(L_2\) to \(L_\infty\), functions to derivatives, almost-everywhere to pointwise control, or integrated control to point evaluation behind “clearly”. Readability cannot replace the required topology.

## Example 9. Baseline-rate consequences: reduce correct but repeated mathematics

After obtaining the full-parameter rate, an earlier proof also derived baseline-hazard and cumulative-hazard consequences, including

\[
\|\widehat h_{0j}-h_{0j}\|_{L_2}=O_p(\tau_n).
\]

These may be correct. But when they follow directly from the principal statement \(d(\widehat\pi_n,\pi_0)=O_p(\tau_n)\), repeating them in the theorem, proof, and conclusion is unnecessary. **A correct consequence need not be principal-theorem material.** Preserve the hierarchy of information rather than listing everything derivable.

## Four central boundaries against mathematical maximalism

## Example 10. Population versus finite-sieve directions: an explicit high-level premise can suffice

The population efficient score uses nuisance directions in \(\mathcal T_\eta\), while a finite-sieve estimator's feasible first-order directions need not coincide with them.

An earlier construction introduced a finite-sieve direction space \(\mathbb T_{\eta,n}(\pi)\), feasible directions

\[
\widehat h_n\in\mathbb T_{\eta,n}(\widehat\pi_n)^{d_\psi},
\]

and a relation \(h_n-\widehat h_n=r_nu_n\), with \(u_n\in\mathcal U_n\) and additional entropy, boundedness, and Lipschitz conditions. Such a route aims to derive the approximate score equation from sieve first-order optimality, provided all required feasibility and rate conditions are established.

The final manuscript instead explicitly assumed

\[
P_n\ell_{\psi,n}^{\dagger}(\widehat\pi_n)=o_p(n^{-1/2})
\]

and proved the subsequent asymptotic linearity and efficiency. The extra spaces and directions then had no remaining manuscript role.

**A foundational subtlety can remain outside the exposition when it only supplies one sufficient mechanism for an explicit, coherent high-level premise.** Internal verification may explore that mechanism; the appendix need not develop it in full.

## Example 11. Nonattainment of a least-favorable minimum: the canonical projection may be enough

An expanded treatment considered an unattained infimum by introducing tuples \((a_{T,m},a_{C,m},b_{f,m},b_{g,m})\) whose nuisance-score sums converge in \(L_2(P_0)\) to

\[
\Pi_{\mathcal T_\eta}\dot\ell_\psi(\pi_0).
\]

It interpreted the efficient score through this minimizing-sequence limit when no exact representing tuple exists. Yet the theorem's canonical object is the closed-space projection, which is already uniquely defined.

The final treatment says that, if the projection admits a least-favorable representation, any such representation may be used; nonunique tuples give the same projected score. **Do not add pathological representation branches when they do not change the canonical theorem object.**

## Example 12. Centered DNN approximants: verify elementary class closure internally

The model requires \(Ef(X)=Eg(X)=0\). After constructing DNN approximants, internally verify whether centering preserves the defined sieve. This can involve the output layer's constant-shift representation, connectivity, depth, width, and weight bounds.

When that check confirms admissibility without changing rates, complexity, or substantive model structure, the manuscript can simply state that the approximation construction followed by centering gives \(f_{0,n}\in\mathcal F_n\) and \(g_{0,n}\in\mathcal G_n\). **Routine closure should be verified, not automatically promoted into additional manuscript mathematics.**

## Example 14. Ou–Bölcskei entropy: verify applicability without copying architecture bookkeeping

The internal source audit examined input dimension, depth, width, connectivity, weight bounds, a restriction of the form \(s\ge\max\{W,L\}\), pruning, constant networks, output bounds, and centering. Which restrictions apply depends on the actual cited theorem and version.

The manuscript need not reproduce this entire notebook. Make clear the justified inclusion of the sieve in the theorem's realization class and the non-obvious architecture bounds needed for application. **Verify hypotheses exhaustively; report non-obvious applicability selectively.** This preserves citation rigor without allowing the audit to overwhelm the proof.

## The detail spectrum

| Detail type | Default treatment | Examples |
|---|---|---|
| Change of mathematical strength or topology | Supply the necessary argument | 2, 8 |
| New model-specific quantitative argument | Show the core mechanism | 3 |
| Necessary short bridge | One sentence or display | 1 |
| Rate arithmetic deciding applicability | Show dominant orders | 4 |
| Nonstandard model-specific functional | Show its origin | 5 |
| Direct consequence of the principal theorem | Compress or remove repetition | 9 |
| Sufficient construction for a high-level premise | Verify internally; may omit | 10 |
| Pathological representation of a canonical object | Usually omit | 11 |
| Elementary sieve/class closure | Verify internally | 12 |
| Full external-theorem bookkeeping | Complete internal check; selective reporting | 14 |

Show every genuinely new mathematical bridge, but not every part of the argument that could be made more elaborate. Include the minimum mathematics a knowledgeable reader needs to reconstruct the intended proof without inventing a missing premise or genuinely new argument.

Return to [Section 7 of the skill](../SKILL.md#7-control-proof-detail-choose-the-minimum-sufficient-exposition-for-validity-and-readability).
