# Source decisions and project-specific conventions

This record explains how the skill was synthesized. It preserves decisions that would otherwise be lost when a later assistant reads only an early draft. General writing instructions are in [SKILL.md](../SKILL.md); mathematical patterns and external-source comparisons are in the other references. The skill can be used without access to the original private workspace.

## Source coverage and limits

The four shared discussions were retrieved through their corresponding ChatGPT conversation records, with pagination exhausted. The accessible records contained 70 user/assistant turns in total; the local proof task added 6 turns. These are retrieval counts, not counts of independent mathematical arguments. The connector does not expose attachment contents, and one long historical assistant message reached its per-message retrieval limit. Accordingly, this record does not claim that every original attachment or every original character was available.

| Source | Accessible turns | Main use |
|---|---:|---|
| [Shared discussion 1](https://chatgpt.com/share/6a9fdfcf-5b08-83e8-9ff4-a832f522614a) | 30 | Later mathematical repairs, score expansion, rate implications, and final scope choices. |
| [Shared discussion 2](https://chatgpt.com/share/6a9fdff7-1014-83ee-99f1-a8e63cc42c73) | 8 | Appendix review, separation of defects from exposition, and administrative-endpoint repair. |
| [Shared discussion 3](https://chatgpt.com/share/6a9fe010-8980-83ee-abb0-d49415c71e3e) | 9 | Lemma organization, notation, tangent-space presentation, and concise proofs. |
| [Shared discussion 4](https://chatgpt.com/share/6a9fe021-0188-83ee-aa47-13c326fc3b61) | 23 | Earlier extensive notation, assumption, entropy, and rate discussions. |
| Local proof task and project proof drafts | 6 task turns, plus files | Earlier identification arguments, implementation context, and version reconciliation. |

The available current appendix `D:/Project_1/proof_revised.pdf` was read as an 18-page document. Relevant local proof text and primary paper/supplement files were also examined. The project file `theory_proofs_0_4.md` concerns an earlier model before the later exclusion restrictions; its nonidentification discussion must not automatically be applied to the current identified model.

The local research cache contained a concrete labeling error: `tmp/pdfs/sources/wu_supp.txt` contained the Liu supplement, whereas `tmp/pdfs/sources/liu_supp.txt` contained the Wu supplement. Titles and authors inside the files were used to identify them. Preserve this correction in future source use; filenames are not bibliographic evidence.

The source discussions contain disagreement, corrections, and superseded assistant suggestions. A claim's presence in a conversation is not proof that the user accepted it or that it is mathematically true. The entries below distinguish reusable principles, project conventions, and corrected claims.

## Accepted principles that generalize

### Statistical reasoning and proof organization

- Organize a proof around the conclusion actually needed. Consistency can use separation without first developing quantitative quadratic equivalence.
- Keep qualitative identification, global uniqueness, local stability, and local quadratic bounds distinct. Reuse earlier results while proving the genuinely new inequality.
- Show the few equations that prevent hidden component cancellation; remove extended instructional algebra once the mechanism is clear.
- A technical lemma needs a real consumer. A short local modulus used only by a bracketing argument belongs with that argument. A one-use result can remain a separate lemma when its proof is substantial.
- Remove unused baseline-derivative and cumulative-function consequences when they add no needed result. Keep the spline approximation and other ingredients actually used.
- Match the empirical comparator to the sieve estimator. Verify approximation, entropy, drift, and optimization error at their required scales.

### Assumptions and citations

- A structural identification restriction can be stated in the main text and invoked in the appendix. Its absence from a repeated appendix list does not make it an unstated premise.
- Derive copula bounds from actual compact ranges, positivity, and uniform regularity when those premises suffice. Do not add a second assumption merely to restate the consequence.
- A high-level condition is acceptable in a deliberately conditional theorem when it is explicit and the advertised conclusion has the same scope. It must not be represented as a consequence of maximization unless proved.
- Identify the exact version and statement of a borrowed result. Avoid invented pinpoint citations, including a proposed elementary-covering citation that was subsequently removed.
- Compare source models before judging condition strength. An independent/current-status/known-association result cannot resolve all conditions of a joint unknown-association likelihood.

### Professional prose and level of detail

- The user may request a step-by-step explanation to understand a proof. That explanation is not automatically the preferred manuscript version.
- Express the claim and its reason directly. Remove repeated disclaimers, imagined reviewer objections, and explanations of what the proof is not doing.
- Preserve necessary mathematical qualifiers. Concision cannot replace a missing hypothesis, justify a false claim, or erase conditional scope.
- An omitted routine sentence is not always a major gap. Distinguish a logical error, a missing substantive premise, a short justification, a citation problem, and an optional editorial improvement.
- After an accepted repair, assess the current text. Do not repeat a criticism of a superseded version.

## Local notation choices: preserve unless the user changes them

| Object | Project choice and reason |
|---|---|
| Full observation and time | Use \(O\) for the observation and \(Y\) for observed time. An earlier proposed global renaming was not the final choice. |
| Administrative observation | Use \(Y=T\wedge C\wedge\tau\), with event, censoring, and administrative indicators \(\Delta_T,\Delta_C,\Delta_\tau\), consistently with the latest model. |
| Finite and nuisance parameters | Retain \(\psi\) and \(\eta\). Existing \(\eta_T,\eta_C\) linear predictors are intentional and need not trigger a wholesale renaming. |
| Log-baseline directions | Use explicit component subscripts such as \(h_{\zeta_T},h_{\zeta_C}\), alongside \(h_f,h_g\); distinguish these from hazard symbols and from specific directions \(a_T,a_C,b_f,b_g\). |
| Copula arguments | Use \(s_T,s_C\) to avoid colliding with smoothness notation. Distinguish \(\Phi_\alpha\), generator notation, and a censoring coefficient \(\phi\). |
| Network classes | \(\mathcal F_n\) and \(\mathcal G_n\) denote centered function classes. Shared raw architecture is allowed. Different typefaces can distinguish unrelated objects. |
| Empirical process | The user preferred explicit \(\sqrt n(P_n-P)\) to introducing another \(G_n\) symbol. |
| Rate and normalization | Define \(\tau_n=a_n\log^2n+n^{-u\nu}\) before repeated use and \(\rho_n=\tau_n^{-1}\) where needed. This supersedes an earlier preference to expand the rate everywhere. |
| Spline notation | Preserve a clear distinction among a basis vector \(b_n(t)\), its components \(B_{j,n}\), and a likelihood-approximation quantity such as \(\delta_{b_n}\). |
| Standard definitions | Refer to main-text definitions and conventional entropy notation when sufficient; do not manufacture redundancy findings. |
| Labels | Retaining labels such as A1, A2, A5–A8 can preserve manuscript compatibility after relocation. Gaps in labels alone are not a mathematical defect. |
| Equation numbering | Number cross-referenced displays in one sequence for standalone appendices unless the existing journal style dictates otherwise. |

These conventions describe this project. A new manuscript should retain its own coherent system.

## Mathematical corrections that supersede earlier suggestions

### Administrative endpoint

With finite cumulative hazards and a positive survival copula at the study horizon, a terminal probability mass remains. The current observation scheme and likelihood include that mass. Omitting it invalidates normalization and the mean-zero score argument. Merely deleting a support sentence does not repair a likelihood whose functions are only defined to the horizon. This repair is substantive and was accepted; repeated defensive commentary about it is unnecessary once incorporated.

Direct terms multiplied by event indicators vanish at the administrative atom. Their \(L_2\) bounds can be justified using continuous subdensities. This does not license unweighted point evaluation under a Lebesgue \(L_2\) norm.

### Inverse bounds and identifiability

Strict monotonicity need not imply a nonzero derivative. A local nondegeneracy argument does not eliminate distant roots. An earlier global uniqueness condition for the identification equation must be retained if the selected global separation proof uses it. Conversely, do not repeat that global argument when only a local estimate is needed.

ODE uniqueness and ODE stability have different conclusions. Reusing the established ODE is efficient; the new difference inequality must still be shown. The user's request to avoid expanding the ODE discussion is a presentation choice, not a claim that every stability bound follows without hypotheses.

### Entropy

The established pointwise Lipschitz envelope makes bracketing transfer short even when the likelihood map is nonmonotone. Earlier criticism overstated the size of this missing explanation. Retain the correct bracket construction, not the inaccurate criticism. An \(L_2\)-only comparison remains insufficient for that construction.

A restriction such as one sieve dimension dominating another is not automatically implied by separate big-O bounds. Retain both terms if dominance is unnecessary. Check every logarithmic factor before inferring an undersmoothing limit.

### Source interpretations

The Liu supplement explicitly imposes boundedness in the relevant baseline/sieve construction. Earlier statements that it only imposed Lipschitz continuity were inaccurate. Its sample-extrema interval should not be confused with a fixed population support endpoint, and its consistency theorem in the checked version does not supply estimation of an additional unknown copula coordinate.

Existence of a closed-space projection does not guarantee existence or uniqueness of a least-favorable parameter tuple. An earlier suggestion to cite a general projection reference for that stronger claim should not be revived.

Conditional orthogonality equations from Wu's current-status model must not replace the actual unconditional operator equations of the joint model. Centered direction classes may yield a constant conditional expectation rather than zero; derive the implication for the actual class.

## Latest accepted scope for the asymptotic-normality proof

The current project retains an explicit approximate efficient-score equation as a high-level condition. The user chose not to expand the question of arbitrary population directions versus feasible finite-network perturbations in that revision. Preserve this conditional scope. Do not reopen it solely because it remains conditional; reopen only if a new claim treats the condition as proved or new evidence changes validity.

The proof also retains deterministic least-favorable approximating directions and a substantive product-rate requirement. When using uniform envelopes, their boundedness must be uniform in the sequence. Smoothness or approximation of the true nuisance functions alone does not establish the required direction approximation.

The final argument derives consequences that follow from existing restrictions: convergence of the least-favorable score approximation follows from its product rate together with \(\sqrt n\tau_n\to\infty\); an already established entropy-growth bound need not become a new assumption. Undersmoothing \(\sqrt n\tau_n^2\to0\) is an additional restriction and must remain explicit.

The accepted expansion controls empirical fluctuations, a population Taylor remainder, and approximate orthogonality separately. It derives functional smoothness bounds from the actual likelihood, uses the score identity for the nuisance remainder, and replaces deterministic score sequences by a variance argument. These details justify concise final prose; they should not be replaced by a generic appeal to semiparametric theory.

The latest review treated the endpoint repair and expanded remainder argument as incorporated. Remaining conditional scope should be reported as scope, not repeatedly scored as a newly discovered logical defect. No historical numerical review score should be encoded as a mathematical guarantee.
