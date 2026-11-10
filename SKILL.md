---
name: how-to-write-appendix-of-a-statistical-paper
description: Draft, revise, and review statistical-paper appendices and supplementary proofs, with disciplined notation, assumption placement and strength, necessary technical lemmas, theorem dependencies, verified citations, and concise statistical prose. Use for asymptotic theory, semiparametric inference, sieve estimation, or comparable methodological proofs; adapt the mathematical workflow to the paper rather than imposing a survival-model template.
metadata:
  version: "1.8.0"
  updated: "2026-09-09"
---

# How to write appendix of a statistical paper

Version 1.8.0 · Updated 2026-09-09.

Write a mathematically valid argument that a statistical reader can reconstruct without unnecessary exposition. Preserve the author's estimand, model, estimator, notation, and requested editing scope. The aim is a coherent proof of the stated statistical result, with every substantive condition visible and every essential inference supported.

## 1. Determine the paper type, theoretical targets, and current task

Before drafting, revising, or reviewing the appendix of a statistical methodology paper, first determine:

1. **What type of statistical methodology the paper develops.**
2. **Which theoretical results that type of paper typically requires, and which results this paper actually intends to claim.**
3. **Whether the current request concerns drafting, proof repair, mathematical explanation, language editing, or theoretical review.**

Do not apply a fixed consistency–rate–asymptotic normality template before identifying the paper type and theorem targets. Different statistical problems require different theoretical objects. Even within one category, the estimand, observation scheme, estimator, inferential target, and actual claims determine the appropriate theorems.

### 1.1 Identify the statistical methodology category

Read the supplied main text, methods section, theorem statements, appendix, supplementary materials, and relevant code or algorithm descriptions. Classify the methodology, first considering these common categories:

| Methodology type | Theoretical results typically requiring attention |
|---|---|
| Parametric estimator | Consistency; asymptotic normality. |
| Semiparametric estimator | Identification; consistency; convergence rate; asymptotic normality. |
| Semiparametric efficiency | The preceding semiparametric estimation results; efficient score; efficient influence function; efficient information or information bound; whether the estimator attains the efficiency bound. |
| Sieve MLE / sieve M-estimation | Consistency; sieve approximation error; convergence rate; root-\(n\) asymptotic normality for finite-dimensional parameters. |
| High-dimensional estimation | Estimation or prediction rates; support recovery or sparsistency where applicable; debiased or desparsified inference; uniform inference when claimed. |
| Causal inference | Identification; estimator consistency; double robustness where applicable; Neyman orthogonality or an influence-function representation; asymptotic normality. |
| DML / ML-assisted nuisance estimation | Nuisance convergence conditions; orthogonality; the role of cross-fitting; remainder control; root-\(n\) inference. |
| Bootstrap methodology | The original statistic's limiting distribution; bootstrap conditional weak convergence or consistency; resulting confidence-interval or test validity. |
| Hypothesis testing | Null distribution; asymptotic size; consistency under fixed alternatives; local power or contiguous alternatives when claimed. |
| Nonparametric estimation | Pointwise or uniform consistency; convergence rate; limiting distribution; minimax lower or upper bounds, or optimality, when claimed. |
| Bayesian methodology | Posterior consistency; posterior contraction rate; a Bernstein–von Mises theorem only when applicable and claimed. |

This table supports **initial classification and a theorem inventory**. It is not a mandatory checklist. Do not add a theorem merely because papers in that category typically establish it.

For example:

- If the model structure or existing literature already establishes identification adequately, do not add another identification theorem for formal completeness.
- An ordinary semiparametric estimator does not automatically warrant an efficiency claim.
- Using a sieve does not require proving minimax optimality.
- Using bootstrap standard errors does not mean that the paper must develop a new bootstrap theorem.
- Estimating nuisance functions by machine learning does not necessarily make the paper a DML contribution.

### 1.2 Build the paper's own theorem target inventory

After classification, extract the intended theoretical conclusions from the paper itself. At a minimum, identify:

- **The estimand or target parameter.**
- **The finite-dimensional and nuisance parameters.**
- **The definition of the estimator.**
- **The observation scheme and sampling regime.**
- **The asymptotic regime.**
- **The theoretical properties already claimed or intended in the main text.**
- **Which results are final statistical claims and which are technical ingredients.**

Build an internal theorem inventory, for example,

\[
\text{Identification}
\rightarrow\text{Consistency}
\rightarrow\text{Rate}
\rightarrow\text{Asymptotic linearity}
\rightarrow\text{Asymptotic normality}
\rightarrow\text{Efficiency},
\]

retaining only the nodes actually needed for this paper.

Distinguish:

- **Main theorem:** a statistical conclusion the paper intends to contribute or use.
- **Corollary:** an inferential result that follows directly from a main theorem.
- **Technical lemma:** an intermediate tool used to establish a main theorem.
- **High-level condition:** a property explicitly taken as a premise rather than derived from primitive assumptions in the paper.

Do not present a technical lemma as a theoretical contribution, or hide an unproved higher-order property in an assumption.

### 1.3 When the paper does not fit a common category

Do not force a classification when the paper cannot reliably be assigned to these categories, or when its estimator or inferential framework is hybrid, emerging, or specific to a field.

In that case:

1. Extract the central statistical object, estimator, data structure, and intended claim.
2. Search for the **five closest high-quality methodology papers**.
3. Prioritize The Annals of Statistics, Biometrika, Journal of the American Statistical Association, and Journal of the Royal Statistical Society: Series B. For a problem with a distinct disciplinary structure, also consider established leading methodology journals in that field.
4. Compare their main theorems, results stated only as lemmas, assumption granularity and strength, logical links between estimators and theorems, and proof architecture.
5. Use that comparison to determine reasonable theorem targets for the current paper.

The purpose is to establish **which theoretical questions this kind of statistical problem typically needs to resolve**, not to copy another paper's number of theorems or proof structure. Match the observation mechanism, estimator, nuisance structure, and inferential target before relying on topical similarity.

### 1.4 Identify the current task after establishing the theorem targets

Classify the request into one or more of five modes:

1. **Manuscript or appendix drafting.**
2. **Proof repair.**
3. **Mathematical explanation.**
4. **Statistical writing or language editing.**
5. **Theoretical review or audit.**

Apply the standards appropriate to the mode. Do not insert teaching explanations directly into manuscript prose or mix reviewer-style criticism into a requested clean revision.

### A. Manuscript drafting

When drafting an appendix from scratch or from an existing main text, identify the paper type and theorem targets, then design the shortest complete proof architecture.

Core rules:

1. **Work backward from the statistical claim.** Determine the target theorem, then the assumptions, technical lemmas, and intermediate results it needs. Do not accumulate unused lemmas to suggest theoretical depth.
2. **Keep the model, estimand, and estimator aligned with the main text.** Do not silently replace an approximate maximizer with an exact maximizer, a penalized estimator with an unpenalized one, or the implemented algorithm with a theoretically convenient estimator.
3. **Prefer recognizable proof routes from statistical methodology.** Examples include M-estimation consistency, sieve rate arguments, empirical-process stochastic equicontinuity, least-favorable submodels, and orthogonal score expansions. Develop new mathematical arguments for the model-specific components.
4. **Keep the hierarchy between main-text theorems and appendix proofs clear.** Main theorems correspond directly to the statistical contribution; technical lemmas serve those theorems.
5. **Prioritize completeness over formal complexity.** Every nontrivial inference must be traceable to a stated assumption, preceding lemma, or verified external theorem. Omit routine algebra that does not affect the conclusion.
6. **Use professional statistical methodology prose.** Enable a reader familiar with the field to recognize the proof strategy, central technical difficulties, and conditions supporting each step, without turning the appendix into a textbook.

### B. Proof repair

When repairing a gap, error, or incomplete argument in an existing proof, use the **minimum necessary repair** principle by default.

Core rules:

1. Identify whether the issue is an incorrect argument, missing premise, insufficient assumption, misuse of an external theorem, circular reasoning, missing uniformity or rate control, notation inconsistency, or merely a short missing justification rather than a substantive proof gap.
2. State the mathematical consequence for the theorem. Instead of a generic label such as “serious gap”, determine whether the conclusion cannot be established, the current route fails while the theorem may remain true, a short bound is sufficient, only a citation needs correction, or the issue is purely expository.
3. Prefer the **least intrusive repair**: preserve the estimator, the author's settled assumptions, the theorem statement when it remains valid, and the existing proof architecture where possible.
4. Do not “prove” the original conclusion by adding unnecessarily strong assumptions. If a new condition is already close to the desired conclusion, identify it as a high-level assumption rather than primitive regularity.
5. Recheck the full dependency chain after repair. A local change can affect later uses in consistency, rates, asymptotic normality, or efficiency; checking only the edited formula is insufficient.

### C. Mathematical explanation

When the user asks to understand a theorem, proof step, lemma, or equation transition, explain the mathematical logic rather than automatically generating manuscript prose.

Core rules:

1. Identify the target conclusion, the available premises, and the missing logical connection.
2. Break complex reasoning into statistically meaningful steps, such as identification, local expansion, curvature, stochastic fluctuation, remainder control, and application of a limit theorem.
3. Distinguish algebraic identities, inequalities, assumptions, lemma consequences, external theorems, and statistical interpretations.
4. Explain why each key term appears and what it controls, rather than only manipulating symbols.
5. Teaching explanations may be more detailed than manuscript prose. If the user subsequently requests an appendix passage, compress the explanation into the proof language of a statistical paper.

### D. Statistical writing and language editing

When polishing an existing theorem, lemma, or proof, **preserve the mathematical content** by default.

Core rules:

1. Preserve the mathematical claim, assumptions, notation, equation numbering, and proof strategy.
2. Give each sentence a clear statistical function: state a condition, cite a result, establish a bound, explain an implication, or give a statistical consequence.
3. Prefer concise mathematical connections such as “By …”, “Since …”, “It follows that …”, “Consequently …”, and “It remains to verify …”.
4. Remove conversational wording, defensive language, repeated explanations of immediate steps, uninformative expressions such as “it is easy to see”, and mathematical digressions unrelated to the current proof.
5. Compression must not alter logical strength. Do not change “may imply” to “implies” without justification, turn an assumption into an established result, or rewrite a pointwise claim as a uniform one.

### E. Theoretical review

When asked to review or score an appendix, assess whether it meets the standards of a high-quality statistical methodology paper. Finding more mathematical objections is not the objective.

Cover at least the following five dimensions.

#### 1. Notation clarity and consistency

Check that:

- Important notation is defined before first use.
- Each symbol retains a single meaning throughout the appendix.
- Truth, deterministic approximation, and estimator are distinguished.
- Finite-dimensional parameters, nuisance functions, score directions, tangent spaces, and sieve spaces are easy to distinguish.
- Norms, metrics, measures, and domains are explicit.
- There is no unnecessary proliferation of notation or multiple aliases for one object.

The purpose of notation is to let the reader reconstruct the argument without repeatedly consulting definitions, rather than to create formal complexity.

#### 2. Assumption rationale, hierarchy, and strength

Assess whether the assumptions are recognizable regularity conditions in the field. Check for:

- Conditions already close to the theorem's conclusion.
- Lemma-level properties imposed as assumptions despite being derivable from primitive conditions.
- Unnecessary global, uniform, or bounded-away-from-zero restrictions introduced for convenience.
- Conditions incompatible with the model, support, observation mechanism, or other assumptions.
- Unnecessary smoothness, compactness, dimension-growth, or tuning restrictions.

When needed, compare related semiparametric inference, sieve estimation, or other methodology papers in The Annals of Statistics, Biometrika, JASA, and JRSS-B. Similar conditions in the literature provide precedent; their necessity for the current model and theorem still requires assessment.

#### 3. Necessity and proof quality of technical lemmas

For each preceding technical lemma, check:

- Its identifiable downstream consumer.
- Its independent and necessary mathematical role.
- Whether a separate lemma is justified or a short calculation inside the theorem proof suffices.
- Correct neighborhood, norm, uniformity, and rate in its statement.
- Accurate use of the relevant assumptions.
- Absence of circular references.
- Applicability of external theorems or inequalities.
- A clear proof strategy.
- Professional, natural statistical proof language.

Check especially whether excessive attention to local mathematical detail reduces readability. Compress or remove steps that a knowledgeable reader can recover from the stated premises and standard tools without affecting validity. Retain essential steps involving a new inverse bound, uniform control, an empirical-process argument, a remainder rate, or an identification mechanism.

#### 4. Logical completeness and proof quality of main theorems

For each main theorem, check:

- Whether its statement captures the statistical claim the paper actually needs.
- Whether its assumptions support the conclusion.
- Correct use of preceding lemmas and intermediate results.
- Any additional conditions that remain unstated.
- Whether consistency, rates, asymptotic linearity, asymptotic normality, and efficiency have been incorrectly conflated.
- The distinction between finite-dimensional and nuisance convergence.
- Remainder control at the scale required by the theorem.
- Satisfaction of the hypotheses of external theorems.
- Whether a statistical reader can readily identify the proof architecture.

Also assess readability and statistical expression. Preserve the mathematical steps that determine validity while avoiding microscopic algebra added only to make every operation explicit.

#### 5. Overall presentation, references, and journal style

Check:

- A clear dependency structure across sections, lemmas, theorems, and proofs.
- Consistent equation numbering, cross-references, theorem environments, and notation layout.
- Logical breaks in long formulas.
- Repeated definitions, redundant remarks, or technical results without consumers.
- Length and density of detail appropriate for a high-quality statistical methodology paper.
- Accurate citations for all substantive borrowed results.
- Correct theorem, lemma, and edition in each pinpoint citation.
- Reference-list coverage of the works actually cited in the appendix and main text.
- When the main text is also supplied, important methodological claims requiring a citation that is missing.

The final score should distinguish **mathematical correctness, assumption quality, proof architecture, statistical writing, notation and presentation, and citation reliability**.

Scoring is neither a count of errors nor a prediction of journal acceptance. For each substantive issue, give its exact location, issue type, effect on theorem validity or readability, and the smallest sufficient correction. Reassess repaired issues using the current version; do not deduct again for defects in an earlier draft.

### 1.5 Establish the authoritative version

After classifying the paper, building its theorem inventory, and identifying the task, establish the authoritative source for the current work.

Read the supplied main manuscript, current appendix, supplementary materials, and algorithms, code, or notation definitions directly relevant to the current theorem in full.

When multiple versions exist, distinguish explicit user decisions, assistant suggestions the user did not accept, superseded drafts, and unresolved mathematical issues.

**Later explicit user decisions take precedence over earlier stylistic suggestions, while mathematical claims still require independent verification.**

Do not determine the version from filenames alone. Inspect internal titles, authors, section and theorem numbering, and content.

If ambiguity changes the estimand, observation scheme, estimator, theorem scope, or required assumptions, ask a focused clarification question while continuing independent work. Resolve ordinary editorial choices from the current manuscript; do not ask the user to supply information already present in the available material.

For a substantial revision, prepare internal working notes recording at least:

- The methodological category.
- Target theorems and their exact conclusions.
- Parameters, metrics, domains, and asymptotic regimes.
- A notation inventory.
- An assumption-to-result dependency map.
- Model, estimator, and version choices that must be preserved.
- Unverified citations.
- Genuinely missing mathematical premises.

Keep these working notes out of manuscript prose unless the user explicitly requests them.

## 2. Build the proof dependency structure around the target theorems

Section 1 has identified the paper type, theoretical targets, and main theorem inventory. This section does not reconsider which conclusions the paper should establish. For each settled target theorem, construct the complete mathematical dependency structure supporting its conclusion.

The two central tasks are:

1. **Build a clear dependency graph for each target theorem.**
2. **Check the proof system for circular dependencies, unsupported dependencies, and invalid references across levels of results.**

Follow the shortest valid route principle. Among valid alternatives, prefer natural conditions, fewer dependencies, and closer alignment with the existing estimator and relevant literature. Do not omit intermediate results necessary for theorem validity merely to simplify the presentation.

### 2.1 Build a dependency graph for each target theorem

For each main theorem identified in Section 1, work backward from its conclusion to the mathematical results required by its proof.

Do not design the appendix by asking which lemmas it would ordinarily contain. Start from

\[
\text{Target theorem}
\]

and ask:

\[
\text{What must already be true for this theorem to follow?}
\]

Construct a structure such as

\[
\text{Primitive assumptions}
\longrightarrow\text{Intermediate mathematical properties}
\longrightarrow\text{Theorem-specific ingredients}
\longrightarrow\text{Target theorem}.
\]

Do not yet decide whether each intermediate result should appear as an assumption, lemma, proposition, or theorem. Later sections address those presentation decisions. Here, identify **the mathematical facts the theorem depends on and their logical order**.

For example, a convergence-rate theorem may have the structure

\[
\begin{gathered}
\text{sieve approximation}+\text{local stochastic modulus}
+\text{criterion curvature}+\text{optimization error control}\\
\Longrightarrow\text{convergence rate}.
\end{gathered}
\]

An asymptotic-normality theorem may require

\[
\begin{gathered}
\text{consistency/rate}+\text{score expansion}
+\text{nuisance contribution control}\\
+\text{remainder }o_p(n^{-1/2})+\text{CLT}\\
\Longrightarrow\sqrt n(\widehat\theta-\theta_0)
\rightsquigarrow N(0,\Sigma).
\end{gathered}
\]

For semiparametric efficiency, the structure may also include

\[
\text{tangent space characterization}
\longrightarrow\text{efficient score}
\longrightarrow\text{efficient information},
\]

and a separate chain,

\[
\text{estimator expansion}
\longrightarrow\text{influence-function representation}.
\]

An efficiency-bound attainment claim requires these two branches to match.

These structures illustrate dependencies; they are not universal proof templates. The actual graph must follow from the model, estimator, and theorem statement established in Section 1.

### 2.2 Connect each mathematical result to an explicit consumer

Every intermediate result should have an identifiable downstream consumer. For each node, record:

- Which theorem or later result uses it.
- Its function in that proof.
- Whether it supplies a qualitative property or a quantitative bound.
- Whether the consumer needs its full conclusion or only part of it.
- Whether an existing result already serves the same purpose.

For example, similar terminology does not make

\[
\text{identifiability}\qquad\text{and}\qquad\text{local inverse inequality}
\]

interchangeable. Identification typically gives

\[
P_\theta=P_{\theta_0}\Longrightarrow\theta=\theta_0,
\]

whereas a rate argument may need a stronger quantitative relation, such as

\[
d(\theta,\theta_0)\lesssim d_P(P_\theta,P_{\theta_0}).
\]

The former does not automatically supply the latter. Similarly,

\[
\widehat\theta_n\to_p\theta_0
\]

does not provide the required convergence rate, and

\[
\widehat\eta_n-\eta_0=O_p(r_n)
\]

does not make a score remainder \(o_p(n^{-1/2})\) unless the relevant expansion and rate calculation have been established.

Record **the actual form of the conclusion needed downstream**, rather than only a broad lemma title.

### 2.3 Distinguish genuine dependencies between theorems

When the appendix contains several main theorems, identify which depend on earlier theorems and which merely share assumptions or technical ingredients. Earlier placement alone does not justify a later theorem's use of a result.

For example,

\[
\text{Consistency}\longrightarrow\text{Rate}
\]

is natural in many problems because a local rate argument first requires the estimator to lie near the truth. In contrast,

\[
\text{Identification}\longrightarrow\text{Rate}
\]

is usually insufficient as a direct implication. Quantitative curvature, local stochastic control, or other ingredients are still needed.

Likewise, existence of efficient information does not imply that an estimator is semiparametrically efficient. The former describes the model's information bound; the latter also requires the corresponding efficient influence-function expansion for the estimator.

For every theorem-to-theorem arrow, ask:

> Which exact conclusion of the earlier theorem does the later proof use?

If this cannot be answered, the dependency usually needs to be decomposed further.

### 2.4 Check for circular dependencies

After constructing the graph, perform a dedicated circularity audit. No result may depend on itself, directly or indirectly. Check both explicit cycles such as

\[
\text{Lemma A}\rightarrow\text{Lemma B}\rightarrow\text{Lemma A}
\]

and less visible cycles such as

\[
\text{Lemma A}\rightarrow\text{Theorem 2}
\rightarrow\text{Theorem 3}\rightarrow\text{Lemma A}.
\]

Pay particular attention to:

- A technical lemma citing a later theorem that itself depends on the lemma.
- A consistency proof using a local-neighborhood property available only after consistency has been established.
- A rate proof using estimator localization obtained only from that same rate theorem.
- An efficient-score construction using a least-favorable-direction approximation rate first established in the asymptotic-normality theorem.
- “By previous arguments” referring to a conclusion not yet independently proved.

Do not conceal circularity by rearranging sections. Determine which facts are primitive, which require independent proof, and whether a mathematical ingredient is missing.

### 2.5 Match the strength of the dependency to its use

Check not only whether a dependency exists but whether its **strength is sufficient**. A later theorem may use more than an earlier result established. Examples include treating:

- Qualitative convergence as a quantitative rate.
- Pointwise convergence as uniform convergence.
- \(L_2\) control as sup-norm control.
- Boundedness of each fixed function as uniform boundedness over an expanding sieve.
- \(O_p(r_n)\) as \(o_p(r_n)\).
- Nuisance-function approximation as approximation of its derivative or score.
- Existence of an information bound as estimator efficiency.

Label the graph with the mathematical form actually needed, for example,

\[
\sup_{\eta\in\mathcal N_n}
|\mathbb G_n(f_\eta-f_{\eta_0})|=o_p(1),
\]

rather than merely “empirical-process lemma”. This exposes

\[
\text{available conclusion}\;\not\Rightarrow\;\text{required conclusion}
\]

before formal proof writing, rather than after substantial algebra has already been developed.

### 2.6 Represent results used by several theorems as shared dependencies

Treat a mathematical result used by several main theorems as a shared node, rather than proving it independently in each theorem proof.

For example, a uniform denominator bound may support likelihood continuity, score Lipschitz control, and a Hessian expansion. The graph may be written as

\[
\text{primitive regularity}\longrightarrow\text{shared bound}
\begin{cases}
\longrightarrow\text{consistency proof},\\
\longrightarrow\text{rate proof},\\
\longrightarrow\text{AN proof}.
\end{cases}
\]

This prevents the same mathematical fact from being proved three times in slightly different forms. Reuse remains limited to the strength actually established. If a new theorem needs a stronger version, such as a uniform rather than pointwise bound, establish that strengthening separately.

### 2.7 Choose the shortest valid proof route

Among valid routes to the same theorem, prefer those that:

- Best match the estimator's definition.
- Require fewer additional assumptions.
- More closely follow established arguments for comparable statistical problems.
- Have shorter, more readily verified dependency chains.

For example, if ordinary consistency follows from uniform criterion convergence and population separation, do not develop local quadratic likelihood equivalence solely to support that consistency proof. Do not force all theorems through the same empirical-process machinery merely to give the appendix a uniform appearance.

The shortest valid route **removes unnecessary dependencies, not necessary proofs**. Retain every ingredient genuinely required downstream, including a new quantitative inverse relation, uniform stochastic control, a model-specific identification mechanism, a non-negligible remainder, operator invertibility, least-favorable approximation, or an estimator-specific score relation.

### 2.8 Produce an internal dependency map

Before writing the assumptions, technical lemmas, and theorem proofs in detail, prepare an internal dependency map. For each target theorem, be able to answer:

\[
\boxed{\text{Which previously established facts are needed, and where do they come from?}}
\]

A useful working record is:

| Target theorem | Required ingredient | Source | Required strength | Used at |
|---|---|---|---|---|
| Theorem \(k\) | Result A | Assumption / earlier result / external theorem | Pointwise / uniform / rate-specific | Proof step |
| Theorem \(k\) | Result B | Earlier theorem | Exact conclusion used | Proof step |
| Theorem \(k\) | Result C | Not yet established | Required bound | Must be proved before the theorem |

Keep this table in working notes by default. It need not appear in the final manuscript.

Every main theorem should now be traceable backward through an acyclic dependency graph to primitive assumptions or verified external results. Later sections determine how to state and place assumptions, which intermediate results warrant separate technical lemmas, and how to prove and write the theorems and lemmas.

### Example

Read [Huang (1996): theorem dependency architecture](references/huang-1996-dependency-example.md) for an extended illustration of the separate localization, information, and estimator-expansion branches.

## 3. Establish and audit a unified notation system

Section 1 identified the statistical objects and target theorems; Section 2 established their mathematical ingredients. Now map every object in the dependency graph to a stable, unambiguous notation system that works throughout the paper.

The aim is neither to redesign the model nor to rename existing symbols extensively for formal uniformity. Ensure that

\[
\boxed{\text{every mathematical object has a unique role and an unambiguous notation}}
\]

and that

\[
\boxed{\text{every theorem symbol is traceable to a defined object, domain, and asymptotic role}.}
\]

For an existing manuscript, the default workflow is

\[
\text{extract}\longrightarrow\text{classify}\longrightarrow\text{audit}\longrightarrow\text{repair},
\]

rather than renaming the entire paper from scratch.

### 3.1 Build a notation inventory from the dependency graph

Before changing any symbols, extract the mathematical objects actually used in theorem statements and proofs from the Section 2 dependency graph. Distinguish at least the following categories.

#### Observed and population objects

Examples are

\[
O_i,\qquad Y_i,\qquad X_i,\qquad P_0,\qquad P_n,\qquad\mathbb G_n.
\]

Specify the observation's components, the state spaces of random variables, and the definitions of empirical and population operators.

#### Finite-dimensional target parameters

Examples are

\[
\beta\in\mathbb R^p,\qquad\alpha\in\mathbb R,
\qquad\theta\in\Theta\subset\mathbb R^q.
\]

State dimensions when they affect derivatives, projections, information matrices, or limiting distributions.

#### Infinite-dimensional nuisance parameters

Examples are

\[
\Lambda\in\mathcal H,\qquad f\in\mathcal F,\qquad g\in\mathcal G.
\]

For a multicomponent nuisance parameter, make the block structure explicit, for example,

\[
\eta=(\Lambda,f,g)\in\mathcal H\times\mathcal F\times\mathcal G.
\]

#### Population and sieve spaces

Distinguish the population parameter space \(\mathcal H\) from the sample-size-dependent sieve space \(\mathcal H_n\). Likewise, distinguish parameter spaces, function classes, score classes, tangent spaces, and empirical-process classes. Their common description as collections of functions does not justify confusing notation.

#### Score, derivative, and tangent objects

Examples are

\[
\dot\ell_\beta,\qquad\dot\ell_\eta[h_\eta],\qquad
\mathcal T_\eta,\qquad\ell_{\mathrm{eff}},\qquad I_{\mathrm{eff}}.
\]

The notation should identify the perturbed parameter block, the perturbation direction, whether the score is scalar, vector-valued, or a linear operator, and the \(L_2(P_0)\) space containing the tangent space.

#### Rates and tuning sequences

Examples are \(a_n,r_n,\delta_n,\lambda_n\). Give each sequence a single explicit asymptotic role, such as sieve approximation error, estimator convergence rate, localization radius, penalty level, or optimization tolerance. Do not use the same sequence to represent different error sources.

An internal inventory should record at least:

| Symbol | Mathematical object | Type | Domain / dimension | Statistical role | First substantive use |
|---|---|---|---|---|---|
| \(\beta\) | Regression parameter | Vector | \(\mathbb R^p\) | Target parameter | Model |
| \(\eta\) | Nuisance parameter | Function/block | \(\mathcal H\) | Nuisance | Model |
| \(\eta_0\) | True nuisance parameter | Function/block | \(\mathcal H\) | Truth | Assumptions |
| \(\eta_{0n}\) | Deterministic sieve approximation | Function/block | \(\mathcal H_n\) | Approximation | Rate argument |
| \(\widehat\eta_n\) | Nuisance estimator | Random function/block | \(\mathcal H_n\) | Estimator | Estimator definition |

Keep this inventory as an internal worksheet by default, outside the final manuscript.

### 3.2 Distinguish truth, approximation, and estimator

Whenever population truth, deterministic approximation, and random estimation coexist, make their asymptotic roles explicit in the notation. A typical family is

\[
\eta_0\in\mathcal H,\qquad
\eta_{0n}\in\mathcal H_n,\qquad
\widehat\eta_n\in\mathcal H_n,
\]

representing three distinct roles:

\[
\boxed{\text{truth}\neq\text{deterministic approximation}\neq\text{random estimator}.}
\]

Bootstrap, perturbed, or one-step versions should form recognizable extensions, such as \(\widehat\eta_n^*\) or \(\widetilde\eta_n\).

Do not silently turn

\[
d(\eta_{0n},\eta_0)=O(a_n)
\]

into a conclusion about \(d(\widehat\eta_n,\eta_0)\). The former is deterministic approximation error; the latter also includes stochastic estimation error. The notation must identify which error a formula controls.

### 3.3 Give each exact notation one mathematical role

Within the same argument scope, follow

\[
\boxed{\text{one exact notation}\longleftrightarrow\text{one mathematical object}.}
\]

This does not mean that a letter can be used only once. Related objects can share coherent families, such as \(\eta,\eta_0,\eta_{0n},\widehat\eta_n\), or \(P_0,P_n,\mathbb G_n\). The problem is the same exact symbol serving different mathematical roles at different locations.

If \(\eta\) denotes the nuisance parameter, do not reuse that exact symbol for a linear predictor. If \(h_T\) denotes a hazard function, do not also use it for a perturbation direction.

For multicomponent nuisance parameters, identify the perturbed block in the direction notation, for example,

\[
h_{\zeta_T},\qquad h_{\zeta_C},\qquad h_f,\qquad h_g,
\]

rather than ambiguous directions \(h_1,h_2,\ldots\).

### 3.4 Form coherent notation families for related objects

Notation should reveal structural relationships as well as avoid collisions. Prefer the recognizable family

\[
\eta,\quad\eta_0,\quad\eta_{0n},\quad\widehat\eta_n
\]

over visually unrelated symbols such as \(\eta,h_0,g_n^*,\widetilde f\) for versions of the same underlying object.

Likewise,

\[
\dot\ell_\beta,\qquad\ell_\beta^{\mathrm{eff}},\qquad I_\beta^{\mathrm{eff}}
\]

should immediately identify the shared target parameter. For component-indexed models, use a consistent convention such as

\[
\zeta_j,\qquad h_{\zeta_j},\qquad
\dot\ell_{\zeta_j}[h_{\zeta_j}],
\]

rather than inventing a naming rule for each component. The purpose is recognizable structure, not formal symmetry.

### 3.5 Specify each norm's or metric's measure and domain

Define the measure and domain of every nonstandard norm, semimetric, or product distance at first use. Do not treat the following as equivalent by default:

\[
\|f\|_{L_2(P_0)},\qquad\|f\|_{L_2(P_X)},\qquad
\|f\|_{L_2([0,\tau],dt)},\qquad\|f\|_{L_2(dt\,dP_W)}.
\]

For a product metric \(d(\pi,\pi_0)\), specify whether it means

\[
|\beta-\beta_0|+\|f-f_0\|+\|g-g_0\|
\]

or

\[
\{|\beta-\beta_0|^2+\|f-f_0\|^2+\|g-g_0\|^2\}^{1/2}.
\]

Define a different or stronger metric separately when needed; do not switch implicitly under the same symbol. Check that each convergence statement uses the metric required by its downstream consumer. For example,

\[
\|\widehat f-f_0\|_{L_2(P_X)}=O_p(r_n)
\]

cannot silently be used as \(\|\widehat f-f_0\|_\infty=O_p(r_n)\).

The notation audit therefore also checks dependency strength: a convergence symbol must not conceal a change of measure, domain, or topology.

### 3.6 Specify the dimensions and types of vectors, matrices, operators, and functions

State the dimension or mathematical type of objects used in differentiation, projection, matrix inversion, covariance calculations, or tensor products. If \(\beta\in\mathbb R^p\), readers should be able to determine that

\[
\dot\ell_\beta(O)\in\mathbb R^p,\qquad
I_{\mathrm{eff}}=P_0[\ell_{\mathrm{eff}}\ell_{\mathrm{eff}}^\top]
\in\mathbb R^{p\times p}.
\]

For a nuisance direction \(h=(h_1,\ldots,h_K)\), specify

\[
h\in\mathcal H_1\times\cdots\times\mathcal H_K.
\]

When a derivative is an operator, distinguish its evaluation \(\dot\ell_\eta[h]\) from ordinary scalar multiplication. In particular, check that:

- Score and target parameter dimensions agree.
- Hessian and information matrix shapes are correct.
- Projection domains and codomains match.
- Block nuisance directions belong to the appropriate product tangent space.

Dimension mismatches can reveal hidden proof errors before further work.

### 3.7 Distinguish parameter spaces, sieve spaces, and stochastic function classes

Objects such as \(\Theta,\Theta_n,\mathcal F_n\) may have entirely different roles in the same proof. Distinguish population parameter spaces, sieve parameter spaces, likelihood-difference classes, score classes, entropy classes, and tangent spaces.

For example, \(\eta\in\mathcal H_n\) describes an admissible parameter, whereas

\[
\mathcal F_n=\{\ell(\pi)-\ell(\pi_0):\pi\in\Pi_n\}
\]

may be the function class used in empirical-process analysis. Their common dependence on \(n\) does not justify notation that obscures the distinction. When the dependency graph calls for entropy, bracketing, or maximal inequalities, the notation must identify the class whose complexity is controlled.

### 3.8 Introduce notation only when it has a real consumer

A new symbol should satisfy at least one of these criteria:

- It is used repeatedly.
- It substantially shortens an important formula.
- It represents an object with an independent mathematical role in the dependency graph.
- It distinguishes otherwise confusable asymptotic roles.

Do not introduce notation for a simple one-use expression merely to make the appendix look formal. Avoid multiple aliases for one score, repeated component definitions that admit a single indexed definition, temporary symbols for one routine calculation, and decorative notation without a theorem dependency. Match notation complexity to proof complexity.

### 3.9 Preserve manuscript notation that already works

The default goal is repair rather than wholesale redesign. Retain notation that is established in the main text, unambiguous, compatible with field conventions, and free of role collisions.

Suggest renaming only when:

1. One exact symbol represents several mathematical objects.
2. Several unrelated symbols represent the same object.
3. Truth, approximation, and estimator cannot be distinguished.
4. A nuisance direction conflicts with a model quantity.
5. Norm or metric notation conceals different measures or domains.
6. A notation family substantially impedes understanding of theorem dependencies.

Do not rename an entire appendix to impose a personal stylistic preference. Once a change is accepted, update every theorem statement, assumption, proof, and cross-reference using that object. Leave the concrete TeX searches, rendering, and typesetting verification to the final-format audit.

### 3.10 Perform three notation audits

Once the system is settled, conduct three separate checks.

#### A. Collision audit

Find symbols representing multiple objects, such as \(\eta\) denoting the nuisance parameter and later the linear predictor. Record genuine collisions and the smallest adequate repair.

#### B. Undefined-object audit

Look for notation introduced in theorems, lemmas, or proofs without a clear definition, such as \(d_\infty,\mathcal T,r_n,\pi_{0n}\). Even a familiar object needs a definition when its specific meaning depends on the model.

#### C. Role-ambiguity audit

Find formally defined symbols whose asymptotic roles remain unclear. Examples include \(r_n\) denoting both sieve approximation error and estimation rate, or \(\pi_n\) not distinguishing a deterministic approximation from a random estimator. Such ambiguity need not be a literal symbol collision to damage readability and dependency verification.

### 3.11 Produce an authoritative notation ledger

Before writing assumptions and technical lemmas in detail, produce an internal authoritative notation ledger containing at least:

| Symbol | Meaning | Mathematical type | Domain / dimension | Asymptotic role | Related family |
|---|---|---|---|---|---|
| \(O_i\) | Observed datum | Random element | \(\mathcal O\) | Observation | \(P_0,P_n\) |
| \(\beta\) | Target parameter | Vector | \(\mathbb R^p\) | Parameter | \(\beta_0,\widehat\beta_n\) |
| \(\eta\) | Nuisance parameter | Function/block | \(\mathcal H\) | Nuisance | \(\eta_0,\eta_{0n},\widehat\eta_n\) |
| \(\eta_{0n}\) | Sieve approximation | Function/block | \(\mathcal H_n\) | Deterministic approximation | \(\eta_0\) |
| \(a_n\) | Approximation error | Scalar sequence | \(\mathbb R_+\) | Deterministic rate | — |
| \(r_n\) | Estimation rate | Scalar sequence | \(\mathbb R_+\) | Stochastic rate | — |
| \(d\) | Parameter metric | Metric | Specified product space | Convergence metric | — |
| \(\ell_{\mathrm{eff}}\) | Efficient score | Vector function | \(L_2^0(P_0)^p\) | Inferential object | \(I_{\mathrm{eff}}\) |

Retain three internal issue lists: **symbol collisions**, **undefined objects**, and **ambiguous asymptotic roles**.

On completion, every node in the Section 2 dependency graph should have a stable mathematical representation, and every later notation should be traceable to one object, one domain, and one statistical role. From Section 4 onward, use this ledger for assumptions, lemmas, and theorem proofs rather than introducing conflicting symbols ad hoc.

### Example

Read [Huang (1996): notation architecture](references/huang-1996-notation-example.md) for a worked illustration of object types, notation families, convergence metrics, and the three notation audits.

## 4. Build and audit the assumption system from proof dependencies

Section 1 established the target theorems, Section 2 their mathematical ingredients, and Section 3 the notation that expresses those objects unambiguously. Now translate the dependency graph into an assumption system consistent with that notation.

The aim is not to mechanically assemble \(A1,A2,\ldots\), but to find **the weakest coherent set of assumptions sufficient for the stated theoretical claims**. Follow

\[
\begin{gathered}
\text{dependency graph}\longrightarrow\text{required mathematical conditions}\\
\longrightarrow\text{functional classification}\\
\longrightarrow\text{primitive / derived / high-level classification}\\
\longrightarrow\text{minimal assumption list}.
\end{gathered}
\]

Ensure that every assumption has an identifiable function and consumer, every required dependency has sufficient support, and no advertised theorem is implicitly assumed through the assumption list.

### 4.1 Work backward from the dependency graph

Do not copy standard assumptions from another paper and then attempt to fit them to the current model. For each dependency in Section 2, ask:

> What mathematical condition is actually required for this implication to hold?

If consistency uses uniform stochastic convergence and population separation, trace the former to the required measurable-envelope, complexity, or Glivenko–Cantelli conditions, and the latter to identification, continuity, or compactness conditions.

If a rate theorem uses local curvature, a stochastic modulus, and sieve approximation, identify the conditions providing each: sufficient criterion curvature near the truth, empirical-process fluctuation control, and the smoothness and sieve architecture delivering the approximation rate.

Construct the chain

\[
\text{Theorem}\leftarrow\text{dependency}\leftarrow
\text{required property}\leftarrow\text{primitive condition}.
\]

Reconsider any assumption that cannot be connected to a theorem through this chain.

### 4.2 Give every assumption an explicit functional role

Beyond its mathematical statement, every assumption must answer **what it controls**. Determine this independently of numbering and physical placement. Common roles include the following.

#### A. Parameter-space control

Compactness, interiority, bounded parameter ranges, monotonicity, normalization, and identifiability constraints restrict admissible parameters. They may support existence, compactness arguments, separation, or avoidance of nonidentifiability. Although both concern the parameter space, \(\theta_0\in\operatorname{int}(\Theta)\) primarily supports local expansions, whereas compactness of \(\Theta\) may support consistency or existence.

#### B. Boundedness and envelope control

These conditions ensure finite likelihood values, stable denominators, integrable score or derivative envelopes, applicability of empirical-process tools, and uniform Taylor-remainder control. Examples include \(\|X\|_\infty\le C\), \(0<c\le p_\pi(O)\le C\), and common-envelope conditions.

Their function is to **control the magnitude of likelihoods, scores, or stochastic classes**. Do not merely state “bounded covariates” without identifying what boundedness controls in the proof.

#### C. Support and positivity control

Conditions such as \(P(X\in\mathcal X)=1\), compact support, or \(P(A=a\mid X)\ge c>0\) can have different purposes. Compact support may control approximation or envelopes; positivity may make inverse weighting well-defined; support overlap may support identification; a time-domain restriction may control hazards or cumulative hazards uniformly. Record the downstream function rather than classifying these solely by their form as support assumptions.

#### D. Smoothness and approximation control

These conditions permit approximation of nuisance functions by splines, series, kernels, neural-network sieves, or other classes at a specified rate. For example, \(f_0\in C^s(\mathcal X)\) may support

\[
\inf_{f\in\mathcal F_n}\|f-f_0\|\le a_n.
\]

Its role is **deterministic approximation-error control**, rather than a final statistical conclusion. Reconsider smoothness not used by an approximation, derivative, or entropy argument.

#### E. Design and nondegeneracy control

Positive definiteness of \(E(XX^\top)\), or residual covariance bounded away from singularity, can support identifiability, curvature, information invertibility, identification of least-favorable directions, or nonsingular asymptotic covariance. Their function is to **prevent degeneracy of the statistical problem**. Identify whether global nonsingularity is needed or local nonsingularity near the truth suffices. Distinguish uniqueness of a closed-space score projection from uniqueness of a direction representing it.

#### F. Observation-mechanism control

Independent censoring, dependent-censoring structure, missing at random, conditional independence, exclusion restrictions, interval-censoring mechanisms, and treatment assignment specify how data are observed. These are often part of the model or identification structure rather than ordinary regularity assumptions. Their function is to **connect the observed-data distribution to the target statistical model**. Do not mix them indiscriminately with boundedness conditions in an undifferentiated list.

#### G. Complexity and stochastic-process control

These conditions support Glivenko–Cantelli or Donsker properties, bracketing entropy, stochastic equicontinuity, maximal inequalities, or local empirical-process moduli. An illustrative entropy bound is

\[
\log N_{[]}(\varepsilon,\mathcal F_n,L_2(P))
\lesssim s_n\log(1/\varepsilon).
\]

Check whether this conclusion should be assumed or derived from the primitive sieve architecture and a Lipschitz mapping. When derivable, establish it as a technical result rather than a top-level assumption.

#### H. Curvature and local identification control

A rate argument may need quantitative separation near the truth, for example,

\[
P\{\ell(\pi)-\ell(\pi_0)\}\le-c\,d^2(\pi,\pi_0).
\]

This is generally stronger than qualitative identification. Determine whether the model structure and information nondegeneracy imply it, whether it needs a separate lemma, or whether it is retained as a high-level condition. Do not silently place an unproved local inverse inequality among routine regularity assumptions.

#### I. Information and operator control

These conditions may ensure nonsingular efficient information, an invertible score operator, a well-defined unique projection, a finite information bound, or positive-definite covariance. For example,

\[
0<\lambda_{\min}(I_{\mathrm{eff}})
\le\lambda_{\max}(I_{\mathrm{eff}})<\infty.
\]

Specify whether the required property is a primitive assumption or follows from more basic design nondegeneracy and tangent-space structure.

#### J. Tuning and sieve-growth control

Conditions such as \(K_n\to\infty\), \(K_n/n\to0\), or \(s_n\log n=o(n^\gamma)\) **balance approximation error and stochastic complexity**. Match growth restrictions to the actual rate calculation. Do not impose unnecessary balance or dominance conditions such as \(K_{1n}\asymp K_{2n}\) merely to obtain a tidier rate.

#### K. Moment and tail control

Finite moments \(E|X|^q<\infty\), sub-Gaussian tails, or bounded higher moments may support a CLT, maximal inequality, covariance existence, concentration, or uniform integrability. Determine whether second moments, \(2+\delta\) moments, or exponential tails are needed. Do not habitually impose stronger tails than the argument requires.

#### L. Theorem-specific inferential control

Some conditions are needed only for asymptotic normality, efficiency, bootstrap validity, or higher-order results. Examples include

\[
P_n\ell_n^\dagger(\widehat\pi_n)=o_p(n^{-1/2}),
\]

least-favorable-direction approximation, or another score-residual requirement. Their role is to **control the inferential expansion at its target scale**. Later use alone does not justify adding them to the common assumptions of every theorem.

### 4.3 Allow multiple functions while identifying the primary role

One primitive condition can serve several downstream results. Bounded covariates may control a likelihood envelope, scores, and Hessians; do not state the same assumption three times. Record its primary role and secondary consumers in the internal ledger:

| Assumption | Primary role | Secondary uses |
|---|---|---|
| Bounded covariates | Score/envelope control | Hessian control, empirical-process envelope |
| Smooth \(f_0\) | Sieve approximation | Derivative approximation |
| Information nonsingularity | Invertibility | Asymptotic covariance |

This avoids repackaging the same condition, repeatedly citing an entire assumption block, and obscuring why a condition exists.

### 4.4 Distinguish primitive assumptions, derived properties, and high-level conditions

After functional classification, determine logical status.

**Primitive assumptions** concern the data-generating process, parameter space, or underlying functions: bounded or compact support, finite moments, smoothness, positivity, model structure, design nondegeneracy, and parameter interiority. They may be stated directly as assumptions.

**Derived technical properties** are to be established from primitives and model structure. Examples include likelihood Lipschitzness, uniform envelopes, entropy bounds, local curvature, score equicontinuity, operator bounds, denominator stability, and approximation of transformed likelihood classes. A distinct consumer or substantial proof may justify a technical lemma. **Do not assume a model-specific property that should reasonably be proved.**

**High-level conditions** support an explicitly conditional theorem when the author does not derive the property fully from primitives. Examples include an approximate score equation or least-favorable approximation condition. Retain these only with an explicit high-level or additional-condition designation. Do not use “By definition of the estimator” to disguise an unproved property as automatic.

### 4.5 Separate shared assumptions from theorem-specific assumptions

Do not collect every condition into a large \((A1)\)–\((A12)\) list for uniform appearance. Following the theorem structure, distinguish:

- Model and identification conditions supporting the experiment and identification.
- Shared regularity used across consistency, rate, and asymptotic-normality results.
- Sieve and approximation conditions supporting approximation and rates.
- Additional asymptotic-normality conditions for the root-\(n\) expansion.
- Additional efficiency or bootstrap conditions only when those conclusions are claimed.

Make scope visible in statements such as “Under (A1)–(A5), the estimator is consistent”, followed by a rate theorem under (A1)–(A7), and an inferential theorem under those conditions plus an additional score condition (A8). Do not attach an unused asymptotic-normality premise to consistency.

### 4.6 Apply a minimality test to every assumption

Ask:

> What exact dependency fails if this assumption is removed or weakened?

If no consumer can be identified, the condition may be unused, mechanically inherited, redundant, or stronger than necessary. In particular, ask whether:

1. A local condition suffices instead of a global one.
2. A finite moment suffices instead of bounded support.
3. Positive definiteness at the truth suffices instead of uniform positive definiteness over the parameter space.
4. \(C^s\) smoothness suffices instead of analyticity.
5. An \(o(1)\) conclusion suffices instead of an unnecessarily fast specified rate.

Prefer **the weakest transparent condition supporting the intended theorem**. Weaker does not mean more technical at any cost. A standard, interpretable condition can be preferable to an opaque near-minimal one, provided it does not materially restrict the model's applicability.

### 4.7 Keep theorem conclusions out of the assumption list

An assumption must not effectively restate the advertised main conclusion. To prove \(d(\widehat\pi_n,\pi_0)=O_p(r_n)\), do not assume localization in an \(O_p(r_n)\) neighborhood. To prove asymptotic normality, do not silently assume the full representation

\[
\sqrt n(\widehat\theta_n-\theta_0)=\mathbb G_n\phi+o_p(1).
\]

If identification is a contribution, do not assume a condition already containing the required unique inverse map. Conditional theorems are allowed, but state that the result depends on a high-level property instead of disguising it as ordinary regularity.

### 4.8 Audit quantifiers and uniformity

Condition strength often lies in quantifier order. Distinguish a finite bound for each function,

\[
\forall f\in\mathcal F_n,\quad\exists C_f<\infty,
\]

from a common bound

\[
\exists C<\infty\quad\text{such that}\quad
\sup_{f\in\mathcal F_n}\|f\|\le C.
\]

These are generally different for expanding sieves. Check whether constants are independent of \(n\), bounds are uniform over parameter neighborhoods, neighborhoods are fixed or shrinking, conclusions are pointwise or uniform, probabilities concern data alone or also bootstrap/random-sieve variation, and \(o(1)\) is uniform in parameters.

Support every uniform conclusion with the corresponding conditions. Finite \(C_\eta\) for each \(\eta\) does not imply \(\sup_{\eta\in\mathcal H_n}C_\eta<\infty\).

### 4.9 Check compatibility across the assumption system

Individually plausible conditions need not be jointly feasible. Check at least:

**Model compatibility:** agreement between observation support and likelihood, between censoring and hazard specifications, and whether boundary conditions admit a valid true distribution.

**Parameter-space compatibility:** the admissible set must be nonempty. Conditions such as \(f\in C^s\), \(\|f\|_\infty\le M\), \(f'\ge c>0\), and \(f(0)=f(1)\) require a joint feasibility check; the derivative and endpoint restrictions in this example conflict.

**Rate compatibility:** tuning sequences \(K_n,s_n,\lambda_n,a_n\) must admit a common growth regime. Do not simultaneously require \(K_n\gg n^{1/2}\) and \(K_n^2/n=o(1)\).

**Cross-theorem compatibility:** added asymptotic-normality conditions must be compatible with the earlier consistency and rate regimes.

### 4.10 Do not strengthen assumptions merely to simplify the proof

Writing convenience should not automatically become a statistical restriction. If the argument contains \(K_{1n}\) and \(K_{2n}\), retain the actual contribution

\[
K_{1n}\log n+K_{2n}\log n
\]

rather than assuming \(K_{1n}\asymp K_{2n}\) merely to combine terms. Likewise, use local positivity when sufficient, neighborhood smoothness rather than global smoothness, \(L_2\) rather than sup-norm approximation when adequate, and bounded second moments rather than bounded support when that is all the proof needs. Every additional restriction needs a statistical consumer.

### 4.11 Separate logical status from physical location

Whether a condition is an assumption is distinct from where it appears. Preferred placements are:

| Condition type | Preferred location |
|---|---|
| Observation mechanism / model restriction | Model or identification setup |
| Parameter normalization | Model definition |
| Shared primitive regularity | Common assumption block |
| Sieve architecture | Estimator / sieve definition |
| Approximation smoothness | Common or sieve-specific block |
| Model-specific derived inequality | Lemma or proof |
| AN-only condition | Asymptotic-normality theorem or additional-condition block |
| High-level score condition | Explicitly labeled with the theorem requiring it |

Do not move every condition to the front merely for tidiness. Let readers distinguish conditions defining the model from additional conditions needed for stronger asymptotic claims.

### 4.12 Compare mathematical problems rather than paper topics

When internal proof analysis cannot resolve whether an assumption is too strong, compare high-quality methodology literature. Match observation mechanism, estimator type, nuisance structure, asymptotic target, and proof technique.

For example, compare sieve-MLE smoothness to other sieve-likelihood arguments rather than treating assumptions as interchangeable because both papers concern survival analysis. Precedent establishes that a similar condition has been used, not that it is necessary or appropriate here. Follow the later citation section for literature searches and source verification.

### 4.13 Expose assumption use in the proof dependencies

Show conditions' actual roles rather than repeatedly citing the whole block. Avoid “By (A1)–(A8)” unless all are genuinely involved. Prefer, when justified:

- “By the bounded-support condition in (A2), the score class admits a common envelope.”
- “The smoothness condition in (A4), together with the sieve approximation result, yields …”

The aim is not additional prose, but a recoverable chain from assumption to mathematical property to theorem step. This also makes actual assumption use auditable.

### 4.14 Build an assumption ledger

Before writing technical lemmas, produce an internal authoritative ledger, for example:

| ID | Exact condition | Functional role | Logical status | Supports dependency | Used by |
|---|---|---|---|---|---|
| A1 | Model / observation restriction | Identification | Primitive | Observed model to target model | Thm 1 |
| A2 | Bounded covariate support | Envelope control | Primitive | Bounded likelihood/score | Thm 2–4 |
| A3 | \(f_0\in C^s\) | Approximation control | Primitive | Sieve approximation | Thm 3 |
| A4 | Design nondegeneracy | Curvature/information | Primitive | Local curvature | Thm 3–4 |
| L1 | Entropy bound | Stochastic-process control | Derived | Local modulus | Thm 3 |
| A5 | Approximate score equation | Inferential expansion | High-level | Score expansion | Thm 4 |

Derived properties may appear in the ledger without belonging to the final top-level assumption list.

### 4.15 Build the dependency–assumption map

Trace each key Section 2 dependency to its mathematical support. A schematic map may connect (A2)+(A3) to sieve approximation, (A2)+Lemma L1 to an empirical-process modulus, and (A4) to local curvature, then combine these ingredients in a rate theorem. For asymptotic linearity, combine the rate theorem, (A5), score smoothness, and information nonsingularity.

These arrows require model-specific verification; labels alone do not establish the implications. If a dependency lacks sufficient support, the assumption system is incomplete.

### 4.16 Audit the assumption system

Conduct at least five checks:

**A. Missing-assumption audit:** does a dependency require a property supplied by no assumption or lemma?

**B. Unused-assumption audit:** does any assumption have no consumer in a theorem, lemma, or derived property?

**C. Overstrong-assumption audit:** is a global or uniform condition imposed where a local or pointwise one suffices?

**D. Misclassified-property audit:** have derivable entropy bounds, curvature, Lipschitz properties, inverse inequalities, or operator bounds been stated as regularity assumptions?

**E. Compatibility audit:** can all assumptions, sieve regimes, and theorem-specific conditions hold together?

### 4.17 Produce the authoritative internal outputs

Complete three internal objects:

1. **An assumption ledger:** each entry contains its statement, functional role, logical status, and consumer. It should answer “Why is this assumption here?”, not merely identify a label such as (A4).
2. **A dependency–assumption map:** each key dependency traces to primitive assumptions, derived technical properties, and theorem-specific conditions through the chain dependency \(\leftarrow\) property \(\leftarrow\) assumption.
3. **An assumption issue list:** record missing assumptions, unused assumptions, overstrong assumptions, derived properties incorrectly assumed, and incompatible conditions.

The completed system gives every assumption a function and consumer, every required dependency sufficient support, and no hidden version of the theorem conclusion. From Section 5 onward, technical lemmas derive the identified properties from these primitives rather than inventing proof conditions again.

### Example

Read [Assumption-system audit in a copula-based semiparametric survival model](references/copula-assumption-system-example.md) for a worked example of deriving copula bounds, relocating identification restrictions, sharing information nondegeneracy, and clarifying spline regularity.

## 5. Construct and verify the technical lemma layer

Section 1 established the target theorems; Section 2 their dependency graphs; Section 3 the authoritative notation; and Section 4 the distinction among primitive assumptions, model/identification conditions, derived properties, and high-level conditions.

Now address the **derived mathematical properties** not yet directly established in Sections 2–4. Determine which warrant standalone technical lemmas and which belong as local arguments in main-theorem proofs.

The objective is

\[
\text{primitive assumptions}\longrightarrow\text{verified technical results}
\longrightarrow\text{main theorems}.
\]

A technical lemma is not an additional layer intended to display mathematical complexity. It supplies a verifiable mathematical result for a theorem dependency. A sound lemma has **inputs, an exact output, a functional role, and a downstream consumer**. Every nonprimitive dependency needs a mathematical supplier, and every standalone lemma needs a genuine consumer.

### 5.1 Start with unresolved dependency edges in Section 2

Do not begin by asking how many lemmas papers of this type usually contain. For each edge \(A\longrightarrow B\), determine whether primitive assumptions, model structure, an established theorem, or a verified external theorem already supplies the implication. If not, identify the missing derived property.

For example, sieve smoothness does not directly imply a rate theorem. Intermediate ingredients typically include sieve approximation, localized empirical-process control, and population curvature. A schematic chain is

\[
\begin{aligned}
(A5)\text{–}(A7)&\longrightarrow\text{sieve approximation lemma},\\
(A1),(A2),(A5)\text{–}(A7)&\longrightarrow\text{empirical-process lemma},\\
\text{identification structure}+\text{regularity}
&\longrightarrow\text{curvature/separation lemma},
\end{aligned}
\]

followed by approximation + stochastic modulus + curvature \(\longrightarrow\) rate theorem. Section 5 establishes these intermediate suppliers rather than redesigning the theorem dependencies.

### 5.2 Give every technical result an explicit functional role

For each proposed lemma, ask **what mathematical obstacle it removes**. Common roles include the following.

#### A. Approximation / construction

A conclusion such as

\[
\exists\pi_{0n}\in\Pi_n,\qquad d(\pi_{0n},\pi_0)\le a_n
\]

controls deterministic sieve approximation.

#### B. Envelope / Lipschitz / stability

For example,

\[
|\ell(\pi_1;O)-\ell(\pi_2;O)|\le C\,d_\infty(\pi_1,\pi_2)
\]

transfers parameter-space control to a likelihood or score class. These are often the model-specific properties that Section 4 requires deriving from primitives rather than assuming.

#### C. Complexity / empirical-process control

For example, a bracketing bound

\[
\log N_{[]}\{\epsilon,\mathcal D_\delta,L_2(P)\}
\le Cs_n\log\frac{CA_n}{\epsilon}
\]

may lead to

\[
E^*\sup_{\pi\in B_\delta}
|\mathbb G_n\{\ell(\pi)-\ell(\pi_{0n})\}|
\le\phi_n(\delta).
\]

The role is uniform control of stochastic fluctuations over a local parameter class.

#### D. Identification strengthening / inverse control

Qualitative identification,

\[
P_\pi=P_{\pi_0}\Longrightarrow\pi=\pi_0,
\]

does not substitute for the quantitative relation a rate argument may require:

\[
d(\pi,\pi_0)\le C\,d_{\mathrm{obs}}(P_\pi,P_{\pi_0}).
\]

The latter converts closeness of observed distributions into quantitative parameter closeness.

#### E. Curvature / separation

A local bound

\[
c_1d^2(\pi,\pi_0)\le P\ell(\pi_0)-P\ell(\pi)
\le c_2d^2(\pi,\pi_0)
\]

and a global separation statement

\[
\sup_{d(\pi,\pi_0)\ge\epsilon}P\ell(\pi)<P\ell(\pi_0)
\]

serve different roles: local quantitative curvature and global population separation.

#### F. Score / tangent / operator control

Nuisance-score operator continuity, existence of least-favorable directions, projection characterizations, information convergence, and operator invertibility prepare the semiparametric inferential expansion.

#### G. Localized remainder / inferential control

For example,

\[
\sup_{d(\pi,\pi_0)\le\delta_n}
|\mathbb G_n\{\ell_{\psi,n}^{\dagger}(\pi)
-\ell_{\psi,n}^{\dagger}(\pi_0)\}|=o_p(1)
\]

establishes negligibility of the corresponding nuisance perturbation at the target root-\(n\) scale.

These categories are not a checklist. Establish only the technical results the dependency graph needs.

### 5.3 Treat each lemma as an input–output–consumer contract

Before proving a lemma, specify its **inputs**: assumptions, model conditions, previous lemmas, and verified external results it may use. Specify its **output**: the exact conclusion needed downstream. Identify its **consumer**: the theorem or later lemma using that conclusion.

If a rate theorem needs

\[
E^*\sup_{d(\pi,\pi_{0n})\le\delta}
|\mathbb G_n\{\ell(\pi)-\ell(\pi_{0n})\}|
\le C\phi_n(\delta),
\]

establish that quantitative modulus. Merely stating that the likelihood class is “sufficiently regular” or “Donsker” does not automatically meet the requirement. **State the weakest exact output sufficient for the consumer.**

### 5.4 Decide between a standalone lemma and a theorem-local argument

A standalone lemma is usually justified when the result is reused downstream, contains a substantial independent argument, establishes a meaningful reusable property, would obscure a main theorem's architecture if proved there, or forms a clear shared node. A localized empirical-process modulus, population curvature result, or least-favorable approximation can meet these criteria.

Keep a single Cauchy–Schwarz application, direct substitution, routine finite-dimensional calculation, simple Taylor remainder, immediate rate consequence such as \(r_n^2=o(n^{-1/2})\), or short one-use bound without independent content inside the theorem proof. Do not create a numbered lemma for a rate implication requiring only one line in the asymptotic-normality proof.

Length alone is not decisive. Ask whether the result has an independent mathematical role or a reusable consumer.

### 5.5 Match the statement precisely to the required strength

Specify the neighborhood, parameter or function class, norm or metric, underlying measure, pointwise or uniform scope, deterministic or stochastic status, rate, independence of constants from \(n\), and exact quantifiers.

For example,

\[
P\{\ell(\pi_1)-\ell(\pi_2)\}^2
\le Cd^2(\pi_1,\pi_2),\qquad
\pi_1,\pi_2\in B_{\epsilon_0}(\pi_0),
\]

is different from a bound holding uniformly for all pairs in \(\Pi_n\). In a quotient formulation of the latter, restrict to pairs with positive distance to avoid an undefined zero denominator. Do not prove an unnecessary global bound when a local one suffices. Conversely, local curvature does not supply the global separation a consistency proof needs.

### 5.6 Give each essential proof transition a provenance

Every nontrivial step must follow from a primitive assumption, an established result, a verified external theorem, or an elementary mathematical argument. Avoid a generic “By the regularity conditions”. Identify the mathematical function, for example:

- “By the bounded-support condition in (A1), the score class admits a common envelope.”
- “The smoothness and quasi-uniform-knot conditions in (A5)–(A6) give the stated spline approximation rate.”
- “By the compact-range result of Lemma 1, the logarithmic copula map is uniformly Lipschitz.”

The reader should be able to recover assumption \(\rightarrow\) derived bound \(\rightarrow\) lemma conclusion.

### 5.7 Order technical lemmas topologically

Follow mathematical dependencies rather than proof length, aesthetic appeal, or the order in which results were conceived. If

\[
L_1\longrightarrow L_2\longrightarrow L_3\longrightarrow T_2,
\]

use that reading order where possible. A lemma may use authoritative assumptions, model conditions, verified external results, and established predecessors in the graph. It cannot form a cycle such as \(L_1\rightarrow T_2\rightarrow L_1\). Section 2 audits global circularity; this section enforces the lemma-level order.

### 5.8 Reuse qualitative results while proving new quantitative conclusions

An established unique-recovery theorem can supply its representation or structure. A new stable-recovery conclusion such as

\[
\|\eta-\eta_0\|\le C\|P_\eta-P_{\eta_0}\|
\]

still needs a quantitative argument. Identification does not automatically give an inverse inequality; ODE uniqueness does not automatically give perturbation stability; score orthogonality does not automatically give second-order remainder control. **Reuse the established identity; prove the genuinely new estimate.**

### 5.9 Combine related results without creating oversized lemmas

An entropy bound used only to obtain a localized modulus through an entropy integral and maximal inequality can usually be developed within the same lemma. Do not collect approximation, entropy, consistency, curvature, score differentiability, and information convergence into one lemma merely because they eventually support the same theorem.

Merge according to **the same mathematical purpose and consumer chain**, not merely a shared final theorem. Sieve approximation and population curvature usually remain distinct technical nodes even when both support a rate result.

### 5.10 Treat external-theorem applicability as part of the proof

For covering, spline approximation, empirical-process maximal inequalities, neural-network entropy, or operator results, verify the actual hypotheses. Check the function class, metric, boundedness conditions, depth/width/sparsity conventions, distinction between bracketing and ordinary covering, theorem version or edition, and conclusion normalization.

A similar-looking conclusion is insufficient. The later citation section handles bibliographic authenticity and citation auditing, but applicability must be established at the point of use in the lemma proof.

### 5.11 Feed proof failures back into the architecture

If the proposed output cannot be proved, distinguish an overstrong lemma statement, a genuinely missing primitive assumption, and an incorrect dependency route. Return respectively to the lemma contract in Section 5, the assumption system in Section 4, or the dependency architecture in Section 2.

Do not finish the proof by silently introducing a condition, changing \(O_p\) to \(o_p\), promoting pointwise to uniform control, switching to a stronger metric, or invoking an inapplicable theorem. **A lemma proof may reveal a missing assumption, but it may not silently create one.**

### 5.12 Audit the technical lemma layer systematically

Check at least:

- **Consumers:** every standalone lemma has a real downstream use.
- **Strength:** its conclusion meets the required strength.
- **Statement–proof agreement:** the proof establishes every stated uniformity, neighborhood, metric, rate, and quantifier.
- **Redundancy:** two lemmas do not merely establish the same property.
- **Inline versus standalone placement:** trivial lemmas belong inline, while repeatedly proved shared arguments may warrant extraction.
- **Circularity:** no indirect lemma–lemma or lemma–theorem cycle exists.
- **External results:** applicability of every substantive borrowed result has been checked.

### 5.13 Produce a technical lemma ledger

Before entering the main-theorem proofs, prepare an authoritative internal ledger, for example:

| Result | Functional role | Exact output | Inputs | Consumer | Presentation |
|---|---|---|---|---|---|
| L1 | Sieve approximation | \(d(\pi_{0n},\pi_0)\le a_n\) | A5–A7 | T2, T3 | Standalone/shared |
| L2 | Stochastic control | Local empirical-process modulus | A1,A2,A5–A7 + L1 | T3 | Standalone |
| L3 | Population behavior | Curvature + separation | Identification + regularity | T2,T3 | Standalone |
| C1 | Remainder calculation | \(r_n^2=o(n^{-1/2})\) | Rate result | T4 | Inline |

Also prepare a lemma-to-consumer map and a technical-issue list. Record missing technical results, unused or overstrong lemmas, trivial standalone lemmas, repeated proof-local arguments, circular dependencies, statement/proof mismatches, and unverified external-theorem applications.

On completion, every nonprimitive dependency in Section 2 should have a verified supplier, every standalone lemma a necessary consumer, and every conclusion the exact strength needed downstream. From Section 6 onward, main-theorem proofs should primarily **assemble established ingredients** rather than rebuild the technical infrastructure.

### Examples

Read [Organizing technical lemmas through actual appendix revisions](references/technical-lemma-layer-examples.md) for six examples covering derived bounds, bracket transfer, ODE stability, multiple conclusions, localized moduli, and the technical lemma ledger.

## 6. Assemble verified ingredients into complete main-theorem proofs

Section 1 established the theorem list; Section 2 the dependency graphs; Section 3 the authoritative notation; Section 4 the assumption system; and Section 5 the technical lemmas and proof-local derived properties.

Now assemble these verified ingredients into **logically closed, statistically interpretable, and reproducible main-theorem proofs**, rather than redesigning the theoretical structure. The central task is

\[
\text{statement}\longrightarrow\text{verified inputs}
\longrightarrow\text{logical bridges}\longrightarrow\text{exact theorem conclusion}.
\]

A main-theorem proof completes the path established in Sections 2–5 for each Section 1 target; it does not rebuild the technical infrastructure.

### 6.1 State each theorem as a complete statistical contract

Before proving a main theorem, make its statement independently interpretable. Specify the target parameter or estimand, estimator, required assumptions and model conditions, metric or normalization, asymptotic regime, convergence mode, limiting object, and scope.

Instead of merely saying that an estimator is asymptotically normal, state, for example,

\[
\sqrt n(\widehat\theta_n-\theta_0)\rightsquigarrow N(0,\Sigma_0).
\]

A rate theorem should state \(d(\widehat\pi_n,\pi_0)=O_p(r_n)\), with \(d\) defined in the Section 3 ledger, \(r_n\) assigned a unique asymptotic role, and assumptions matching the Section 4 ledger. **A theorem statement should be interpretable without reading its proof.**

### 6.2 Execute the established dependency graph

Section 2 determined which results are needed and in what order. Follow that architecture rather than inventing a new route. If consistency depends on sieve approximation, a ULLN, global population separation, and near-maximization, organize the proof around those four ingredients.

If a rate theorem depends on consistency, a localized stochastic modulus, local curvature, and approximation error, do not suddenly introduce a global argument or additional assumption. Main-theorem proofs assemble established ingredients; they must not silently rebuild the technical layer.

When a substantial new requirement emerges, return to Section 5 for a technical result, Section 4 for a condition, or Section 2 for a revised route. Do not conceal a new two-page technical argument inside the main proof.

### 6.3 Use a dependency-based roadmap for long proofs

A short roadmap is useful only when a proof has several substantive mathematical stages. Describe functions, for example:

> The proof proceeds in three steps: localization, control of the nuisance remainder, and the asymptotic score expansion.

Or:

> We first establish near-maximization of the population criterion, then use global separation to obtain consistency.

Avoid equation-by-equation narration such as “Step 1 proves (14), Step 2 proves (15), Step 3 proves (16)”. Routine algebra needs no additional numbering. **Proof stages should correspond to mathematical roles, not equation numbers.**

### 6.4 Reuse lemmas, but show the logical bridges

Do not reprove Section 5 lemmas. Explain why their outputs imply the theorem. A consistency proof needs more than “By Lemmas 1 and 3, consistency follows”.

Suppose Lemma 1 supplies

\[
\sup_{\pi\in\Pi_n}|(P_n-P)\ell(\pi)|=o_p(1),
\qquad\pi_{0n}\in\Pi_n,\qquad d(\pi_{0n},\pi_0)\to0,
\]

and Lemma 3 supplies

\[
\sup_{d(\pi,\pi_0)\ge\epsilon}P\ell(\pi)<P\ell(\pi_0).
\]

Connect these to the estimator's maximization relation

\[
P_n\ell(\widehat\pi_n)\ge P_n\ell(\pi_{0n}).
\]

The bridge also requires the established criterion continuity or approximation bound ensuring \(P\ell(\pi_{0n})\to P\ell(\pi_0)\). Together, these give population near-maximization and hence

\[
P\{d(\widehat\pi_n,\pi_0)\ge\epsilon\}\to0.
\]

These bridge steps are the main theorem proof's central work: reuse the supplied lemmas while showing how their outputs yield the target conclusion.

### 6.5 Give each substantive transition an explicit source

Every substantive transition must trace to an assumption, model condition, technical lemma, earlier theorem, verified external theorem, or elementary mathematical operation. Avoid “By standard arguments” or “By the regularity conditions” when the step needs a particular result.

Prefer, when justified:

- “By Lemma 2, the localized empirical-process modulus satisfies …”
- “By Theorem 2, \(\widehat\pi_n\) lies in the required neighborhood with probability tending to one.”
- “By the nonsingularity condition in (A8), \(I_{\mathrm{eff}}(\psi_0)\) is invertible.”

Readers should be able to trace the provenance of every transition.

### 6.6 Analyze exactly the estimator defined in the manuscript

A global maximizer, approximate maximizer, penalized estimator, numerical stationary point, one-step estimator, and profile estimator are not interchangeable.

If the estimator satisfies only

\[
P_n\ell(\widehat\pi_n)
\ge\sup_{\pi\in\Pi_n}P_n\ell(\pi)-\epsilon_n,
\]

retain the optimization error \(\epsilon_n\). Do not replace this with exact maximization over every \(\pi\in\Pi_n\).

Likewise, if asymptotic normality uses

\[
P_n\ell_{\psi,n}^{\dagger}(\widehat\pi_n)=o_p(n^{-1/2}),
\]

do not silently replace the right-hand side by zero. **The proof must analyze the estimator actually defined in the paper.**

### 6.7 Invoke cross-theorem dependencies explicitly without reproving them

For an established chain \(T_2\longrightarrow T_3\longrightarrow T_4\), use the exact earlier conclusion. For example:

> By Theorem 2, \(d(\widehat\pi_n,\pi_0)=o_p(1)\), so with probability tending to one the estimator lies in the neighborhood on which Lemma 3 provides quadratic curvature.

Proceed to the new rate argument without proving consistency again. An asymptotic-normality proof may similarly use \(d(\widehat\pi_n,\pi_0)=O_p(r_n)\) to control remainders without repeating the rate proof. Reuse conclusions at exactly the strength already established.

### 6.8 End with the object required by the theorem type

#### Identification

Reach \(P_\pi=P_{\pi_0}\Longrightarrow\pi=\pi_0\), rather than stopping after identifying only an intermediate margin.

#### Consistency

Reach \(d(\widehat\pi_n,\pi_0)\to_p0\). Criterion convergence alone is insufficient unless its implication for parameter convergence is supplied.

#### Convergence rate

Reach \(d(\widehat\pi_n,\pi_0)=O_p(r_n)\), not merely \(o_p(1)\).

#### Asymptotic normality

Prefer first obtaining an asymptotic linear representation,

\[
\sqrt n(\widehat\psi_n-\psi_0)
=\frac1{\sqrt n}\sum_{i=1}^n\phi_0(O_i)+o_p(1),
\]

then applying a CLT to reach \(N(0,\Sigma_0)\).

#### Semiparametric efficiency

An efficient score or information bound alone is insufficient. Establish that the estimator's influence function is the efficient influence function,

\[
\phi_0=I_{\mathrm{eff}}^{-1}\ell_{\mathrm{eff}},
\]

and hence that its asymptotic covariance is \(I_{\mathrm{eff}}^{-1}\). Retain the regularity framework needed for the efficiency claim. The proof must end at exactly the statistical claim in the theorem.

### 6.9 Close the argument at the stated scale, norm, and uniformity

Check that the final result has the statement's mathematical strength:

- **Scale:** \(o_p(1)\) does not satisfy a required \(o_p(n^{-1/2})\) bound.
- **Norm:** an \(L_2(P_X)\) rate does not establish the claimed sup-norm rate without another argument.
- **Uniformity:** convergence for each fixed \(\eta\) does not establish \(\sup_{\eta\in\mathcal N_n}|R_n(\eta)|=o_p(1)\).
- **Probability mode:** distinguish \(O_p\), \(o_p\), convergence in probability, and convergence in distribution.

Match the statement in rate, norm, domain, and mode of convergence.

### 6.10 Separate principal results from ancillary consequences

Highlight the paper's actual statistical claim rather than collecting every natural consequence in one theorem. If asymptotic normality is primary and \(\widehat\Sigma\to_p\Sigma\) only supports Wald confidence intervals, the latter can appear as a corollary, a consequence after the theorem, or in an inference subsection.

Do not mechanically combine consistency, rates, asymptotic normality, variance estimation, confidence-interval validity, and Wald-test validity unless they form an inseparable principal result.

### 6.11 Apply external theorems accurately at the point of use

Identify the theorem, map the current objects to its notation, state which earlier results establish its hypotheses, and specify the normalization or rate parameter. For example, after verifying applicability:

> Applying Theorem 3.4.1 of van der Vaart and Wellner (1996) with \(R_n=r_n^{-1}\), using the quadratic drift from Lemma 3, the localized modulus from Lemma 2, and the near-maximization relation, yields …

This is more reproducible than a generic appeal to empirical-process theory. The later citation section handles bibliographic verification; applicability must be logically complete here.

### 6.12 Return new gaps to the appropriate layer

A main-theorem proof should not become a place for improvised repairs. Return missing primitive conditions to Section 4, missing derived properties to Section 5, invalid dependency routes to Section 2, ambiguous notation to Section 3, and changes to theorem targets to Section 1.

Do not force completion by adding an undeclared assumption, silently defining a new norm, compressing a substantial new lemma into “it follows”, weakening the conclusion without revising the statement, or replacing the estimator with an easier one. **Section 6 assembles the architecture; it does not silently rewrite it.**

### 6.13 Audit closure for every theorem

Check the following after completing the proof:

**A. Statement closure:** does the proof reach the exact stated conclusion?

**B. Dependency closure:** is each required Section 2 dependency used, replaced by an earlier theorem, or shown unnecessary after re-audit?

**C. Assumption closure:** are all conditions drawn from the established Section 4 ledger, with no hidden assumptions?

**D. Lemma closure:** are invoked conclusions identical to their Section 5 statements, without promoting local results to global ones?

**E. Estimator closure:** does the proof analyze the estimator in the theorem statement?

**F. Scale closure:** do all remainders attain the required scale?

**G. Norm and domain closure:** do proof and statement agree on norm, metric, domain, measure, and parameter component?

**H. Limit closure:** for a distributional claim, has the proof established the stochastic expansion, controlled its remainder, checked the limit theorem's hypotheses, and identified the correct covariance?

The proof must close at exactly the claimed mathematical object and strength.

### 6.14 Build a theorem closure ledger

After completing the main proofs, prepare an authoritative internal ledger, for example:

| Theorem | Statement | Dependencies | Assumptions | Technical suppliers | Exact closure | Status |
|---|---|---|---|---|---|---|
| T1 | Identification | ID1–ID3 | Model + ID conditions | — | \(\pi=\pi_0\) | Closed |
| T2 | Consistency | Approximation + ULLN + separation | Shared assumptions | L1, L3 | \(d\to_p0\) | Closed |
| T3 | Rate | T2 + modulus + curvature | Shared + sieve conditions | L2, L3 | \(d=O_p(r_n)\) | Closed |
| T4 | AN | T3 + score expansion + remainder + CLT | AN conditions | Inferential lemmas | ALR + normal limit | Closed |
| T5 | Efficiency | T4 + efficient score/information | Information condition | Tangent/projection results | \(I_{\mathrm{eff}}^{-1}\) attained | Closed |

Also record missing bridges, statement–proof mismatches, hidden assumptions, estimator mismatches, wrong norms or domains, insufficient rates, unused dependencies, conclusions stronger than proved, and incompletely closed theorems.

### 6.15 The intended completed state

Every Section 1 theorem should be mathematically closed, and every proof reconstructible by tracing its steps through Sections 2–5. The appendix should connect theorem targets, dependency graphs, notation, assumptions, technical lemmas, main-theorem assembly, and exact statistical conclusions.

Evaluate main proofs by **logical closure, statistical interpretability, and reproducibility**, rather than the number of mathematical steps. Section 7 then addresses the detail, readability, and editorial quality of these completed arguments.

## 7. Control proof detail: choose the minimum sufficient exposition for validity and readability

Section 6 has closed each target theorem mathematically. Section 7 does not strengthen the theorem or seek maximal mathematical elaboration. It turns the verified argument into a manuscript proof that is **correct, recoverable, proportionate, and readable**.

Distinguish the **internal verification proof** from the **manuscript proof**. Internal verification can be more extensive: it may examine edge cases, exact parameter-space compatibility, closure properties, external-theorem hypotheses, alternative sufficient constructions, and pathological representations. Include these in the manuscript only when essential to the final theorem's validity, recoverability, or interpretation.

\[
\text{internal verification depth}\ge\text{manuscript exposition depth}.
\]

Mathematical correctness is a prerequisite; **maximum expansion is not the objective**.

### 7.1 Decide whether a step is necessary before deciding its detail

Do not immediately ask whether a candidate step needs more explanation. Apply two tests.

**Stage 1: necessity.** If the step is removed, can readers legitimately reach the next conclusion from the stated premises without inventing an assumption, proving a new theorem, changing a norm/topology/convergence mode, upgrading qualitative to quantitative control, or guessing a model-specific transformation? If not, retain the step. Otherwise, determine whether it is routine algebra, a standard consequence, an auxiliary representation, a sufficient but nonessential mechanism, or a redundant consequence.

**Stage 2: granularity.** Even when necessary, show only the mathematical information a professional reader needs to recover the argument. **Necessity determines whether to retain a step; recoverability determines how much to show.**

### 7.2 Use a proof-detail ladder rather than a write/omit dichotomy

#### Level 0 — Internal only

Omit from the final manuscript. Appropriate examples include verified routine closure, pathological representation cases, nonessential sufficient constructions for high-level premises, and auxiliary machinery with no downstream consumer.

#### Level 1 — Phrase or citation

Examples include “by Cauchy–Schwarz”, “by the projection theorem”, and “by the standard B-spline approximation result”. Use when the result is standard and model-specific applicability is evident or already established.

#### Level 2 — One sentence or one display

Use for a necessary short bridge, such as componentwise control plus a Lipschitz map yielding likelihood-class control, or a short rate calculation whose powers and logarithms must be visible.

#### Level 3 — Short derivation

Use for a model-specific score, quantitative stability argument, non-obvious change of mathematical object, or derivation of a new functional. Usually several equations and explicit transitions suffice; do not reprove a standard general theorem.

#### Level 4 — Standalone technical result

Use only when Section 5's criteria identify an independent technical node. Section 7 must not create additional lemmas merely to explain more.

### 7.3 Match minimum exposition to the transition type

**A. Routine algebra** can be compressed: substitution, finite-dimensional matrix algebra, direct Cauchy–Schwarz, and a stochastic-order calculation under explicit rates, provided no new asymptotic requirement is hidden.

**B. A necessary short bridge** must name its mechanism, usually in one sentence or display. Component brackets do not automatically become likelihood brackets, but the transfer need not repeat all of covering theory.

**C. A new model-specific quantitative argument** needs its core derivation. Identification does not imply a quantitative inverse bound, and ODE uniqueness does not imply stability. These are new mathematical content, not routine details.

**D. A change of mathematical strength or topology** cannot be skipped. Transitions from \(L_2\) to \(L_\infty\), functions to derivatives, almost-everywhere to pointwise statements, qualitative uniqueness to rates, or \(O_p\) to \(o_p\) require explicit support. Prose cannot conceal a change in topology, norm, derivative order, quantifier, or asymptotic strength.

### 7.4 Show the origin of model-specific constructions, not every mechanical derivative

When a new object such as \(B_T[a_T](y)\) cannot be recovered naturally from the notation, do not introduce it as an apparently arbitrary functional. Show the path from perturbation through the intermediate object to the score or derivative. Do not expand every routine chain-rule term. **Show where a non-obvious object comes from, not every mechanical differentiation step.**

### 7.5 Show the arithmetic that determines asymptotic order

If an external theorem requires

\[
R_n^2\varphi_n(R_n^{-1})\lesssim\sqrt n,
\]

“by the growth conditions” is insufficient when polynomial powers, logarithms, sieve complexity, and approximation rates interact. Display the decisive order relations. Once the dominant orders are explicit, omit routine simplification. Show the arithmetic that determines applicability.

### 7.6 Verify external theorems fully; report non-obvious applicability selectively

Internally check the object, function class, metric, parameter range, dimension, entropy notion, tuning regime, and theorem version. In the manuscript, identify the mapping to the external theorem, the non-obvious hypotheses already met, and the resulting conclusion.

Do not reprove the external theorem, copy all architecture bookkeeping into the proof, or import an auxiliary object merely because the reference uses it. **Citation verification should be exhaustive internally, but selective in manuscript exposition.**

### 7.7 Do not prove every sufficient mechanism for an explicit high-level premise

If the theorem explicitly assumes

\[
P_n\ell^\dagger_{\psi,n}(\widehat\pi_n)=o_p(n^{-1/2}),
\]

check that the premise is coherent, weaker than the theorem conclusion, sufficient for the subsequent proof, and clearly reflected in the scope. Once this holds, there is no need to establish every finite-sieve construction that could guarantee it.

Omit a nonessential construction especially when it introduces tangent spaces, entropy classes, rate sequences, or assumptions with no other consumer. **Do not prove every sufficient mechanism for an explicitly stated high-level premise.**

### 7.8 Do not solve irrelevant representation pathologies for a well-defined canonical object

For example, define the efficient score canonically as

\[
\ell_\psi^*=\dot\ell_\psi-\Pi_{\mathcal T_\eta}\dot\ell_\psi.
\]

When the appropriate closed-space projection is well-defined and unique, the principal statistical object exists. A particular least-favorable tuple may be nonunique, its infimum may not be attained, or only a minimizing-sequence representation may be available. Such issues need not be elaborated when they do not affect the projection or theorem conclusion. **Do not solve representation pathologies that do not alter the canonical theorem object.**

### 7.9 Verify routine closure properties without automatically displaying their proofs

Internally check that centered approximations remain admissible, output restrictions only reduce a class, constant shifts can be represented by the network, and bounded subsets inherit the relevant complexity control.

If the mechanism is elementary, does not change rates or substantive class structure, and has no separate downstream use, one sentence or omission usually suffices. This decision follows verification, not an assumption that closure is automatic.

### 7.10 Avoid repeating consequences recoverable from the principal theorem

If \(d(\widehat\pi_n,\pi_0)=O_p(\tau_n)\) directly yields a componentwise result, do not repeat that result in the theorem, proof, and closing discussion. Retain a consequence when it is a substantive claim, has an independent interpretation, or is used later. **Mathematical truth does not imply manuscript necessity.**

### 7.11 Base deletion on dependencies rather than visual complexity

Before deleting a display, conclusion, or paragraph, ask which downstream dependency consumes it. Do not remove needed material because it resembles another result, the proof is long, or the formula is unattractive. Prefer deletion when there is no consumer and the material is not needed to understand the main mechanism.

Delete a detail only if the dependency graph remains valid and the intended inference remains recoverable.

### 7.12 Do not retain details merely because a leading-journal reference used them

References can inform the proof route, conventional abstraction level, and use of standard results. Do not mechanically copy auxiliary variables, tangent objects, local parameters, decompositions, or intermediate lemmas. Borrow their proof function, not every part of their presentation.

### 7.13 Classify severity before choosing the size of a revision

Distinguish five cases:

- **Substantive mathematical gap:** a new theorem-level or quantitative argument is missing; return to Section 5 or 6.
- **Necessary short bridge:** the route is sound but an essential transition is unstated; add the shortest bridge.
- **Rate or applicability verification gap:** supply the local order calculation or hypothesis mapping.
- **Optional exposition improvement:** explanation would be more pedagogical, but a professional reader can recover the argument; usually do not add it.
- **Mathematical maximalism:** correct material has no consumer, treats only a pathology or a sufficient mechanism for a high-level condition, or introduces disproportionate notation; remove it or keep it in internal notes.

Do not describe all five as an incomplete proof.

### 7.14 Use recoverability rather than maximal explicitness as the final standard

A knowledgeable statistical reader should be able to reconstruct the intended inference from the stated premises, established results, and identifiable standard theorems **without inventing a missing assumption or proving a genuinely new result**. The reader need not be able to reproduce every algebraic line without doing any work. Recoverable does not mean fully expanded.

### 7.15 Produce a proof-detail audit

Keep an internal record for each fragment:

| Step | Mathematical role | Necessary? | Novel? | Standard? | Consumer | Exposition level |
|---|---|---|---|---|---|---|
| Component-to-likelihood bracket transfer | Bridge | Yes | Low | Partly | EP bound | Level 2 |
| Gronwall stability | Quantitative stability | Yes | High | Standard theorem, model-specific application | Curvature | Level 3 |
| Centering closure of DNN sieve | Class closure | Internally | Low | Routine | Approximation | Level 0–1 |
| Minimizing-sequence representation | Edge case | Not for main claim | Technically involved | Functional analytic | None | Level 0 |
| \(s_n\Gamma_n\) calculation | Rate verification | Yes | Low | Model-specific arithmetic | Rate theorem | Level 2 |

Record omitted but verified details, manuscript-required bridges, overexpanded paragraphs, repeated consequences, and unresolved gaps. On completion, no required bridge is missing, and no substantial mathematical block remains solely because more can be proved.

Seek **the shortest proof preserving mathematical validity and professional recoverability**, rather than either the shortest or longest proof in isolation.

### Examples

Read [Proof-detail control across appendix revisions](references/proof-detail-control-examples.md) for eleven examples spanning necessary derivations, short bridges, and material best retained only in internal verification.

## 8. Express mathematically complete proofs in direct, accurate statistical prose

Sections 1–7 determined what to prove, how to organize dependencies, notation, assumptions, technical lemmas, and theorem closure, and which details belong in the manuscript. Section 8 converts the completed argument at its chosen exposition level into **precise, direct, non-defensive, statistically professional prose** without changing its mathematical structure.

**Language may compress mathematics, but must never change mathematical strength.** The purpose is not ornamental writing: each sentence should faithfully express a mathematical function.

### 8.1 Give every sentence a mathematical function

Proof sentences usually serve one of five roles:

- **State a premise:** “By Theorem 3, \(d(\widehat\pi_n,\pi_0)=O_p(\tau_n)\).”
- **Invoke a result:** “Lemma 2 gives the localized empirical-process bound.”
- **Make a transition:** “Hence the estimator lies in the neighborhood where the quadratic curvature bound applies with probability tending to one.”
- **State a conclusion:** “Therefore \(R_nd(\widehat\pi_n,\pi_0)=O_p(1)\).”
- **Explain statistical meaning:** “Thus \(I_{\mathrm{eff}}^{-1}(\psi_0)\) is the asymptotic covariance and the estimator attains the semiparametric information bound.”

Use these statements only when the corresponding inference is established. Split sentences that obscure their function by combining premises, citations, qualifications, defensive explanations, and conclusions.

### 8.2 Use connectives to express actual mathematical relationships

Use **By** to invoke a result, **Since** to supply a premise, **Hence / Therefore / Consequently** for deduction, **It remains to show** to identify unfinished work, and **Combining … yields** to join established ingredients.

Do not apply these mechanically. “Hence, by regularity, the result follows” adds little without an identifiable implication. Connectives should expose premise → operation → conclusion.

### 8.3 Prefer precise mathematics to vague prose

Instead of “The estimator converges sufficiently fast”, state \(d(\widehat\pi_n,\pi_0)=O_p(\tau_n)\). Instead of merely describing quadratic likelihood behavior, display the applicable bound:

\[
c_1d^2(\pi,\pi_0)\le P\ell(\pi_0)-P\ell(\pi)
\le c_2d^2(\pi,\pi_0).
\]

Precision takes priority over elegance when prose would obscure mathematical content.

### 8.4 Never use prose to conceal a gap

“Clearly”, “immediately”, “by standard arguments”, “it is easy to see”, and “by regularity” do not replace missing mathematics. Do not edit away a transition Section 7 identified as a topology change, quantitative strengthening, rate verification, or model-specific transformation. **Prose compression cannot repair a mathematical gap.**

### 8.5 Remove conversational and defensive wording

The appendix need not repeatedly reassure readers, anticipate reviewers, or explain what the author does not claim.

| Weak or defensive wording | Preferred form |
|---|---|
| “It should be noted that we do not claim the score equation always holds.” | “Assume that the estimator satisfies the approximate score equation …” |
| “This is not a proof of identification again, but rather …” | “We establish the inverse bound required for the quadratic lower bound.” |
| “It is easy to see that the remainder is small.” | “By the operator bound and Cauchy–Schwarz, \(\|R_n\|=O_p(r_n^2)=o_p(n^{-1/2})\).” |
| “Although this assumption may seem restrictive …” | State the assumption and its role; compare literature if needed. |
| “For completeness, we once again spell out …” | Cite the earlier identity and give only the new bound. |

State scope mathematically rather than defending it rhetorically.

### 8.6 Preserve mathematical qualifiers

Qualifiers such as “uniformly in \(n\)”, “for deterministic approximating directions”, “in a neighborhood of the truth”, “under the additional score condition”, “for regular estimators”, “with probability tending to one”, “for sufficiently large \(n\)”, and “for every fixed \(\epsilon>0\)” can determine validity.

Removing them can turn a local result into a global one or a conditional result into an unconditional theorem. Necessary qualifiers are mathematical content, not stylistic hedges. Retain them where needed without repeated reminders.

### 8.7 State conditional scope once

If the theorem explicitly invokes an additional score condition, do not repeatedly announce its conditional nature in the proof. An explicitly designated high-level assumption does not require recurrent warnings that it is not automatic from the estimator definition. State scope where it controls the theorem, then use it.

### 8.8 Separate manuscript prose from reviewer-facing prose

Revision history, anticipated objections, reasons for deferring an expansion, impressions that an assumption looks strong, and abandoned proof routes generally belong in a response letter or internal notes. The manuscript presents the current claim, current conditions, and current proof.

### 8.9 Avoid unnecessary meta-language

Minimize “We now proceed to show”, “We next turn our attention to”, and “It is worth mentioning that” unless they clarify the architecture. Usually proceed directly: “By Lemma 3”, “Define”, “Consider”, or “Applying Gronwall's inequality yields”.

### 8.10 Use informative displays instead of repetitive explanations

A display such as

\[
d(\pi,\pi_0)\le C\left[
|\alpha-\alpha_0|
+\|(p_{\pi,1}-p_{0,1},p_{\pi,0}-p_{0,0})\|_2
\right]
\]

already states the comparison precisely. Prose should explain why it holds and what comes next, rather than restating the formula in words before and after it.

### 8.11 Audit the final prose

Check mathematical strength: no assumption becomes a conclusion, sufficient condition becomes necessary, local result becomes global, numerical improvement becomes a proved guarantee, or approximate equation becomes exact.

Check sentence functions, repeated scope statements, definitions or conclusions, response-letter remnants, and defensive wording that can be replaced by direct mathematics. Finally confirm recoverability after compression. Every sentence should advance the statistical argument without changing its scope.

## 9. Typeset for reading and mathematical verification

Make theorems, assumptions, equations, references, and proof boundaries easy to read and check. **Typesetting should expose mathematical structure, not compete with it.**

### 9.1 Preserve the manuscript's journal style

Retain the supplied class, theorem environments, fonts, spacing, macros, and bibliography style. Do not shrink the entire document, force narrow margins, compress line spacing manually, or redesign the document for a local appendix edit. Address excessive length through Sections 7–8 before sacrificing readability.

### 9.2 Use equation numbering for cross-references

Number displays that are referenced later; routine unreferenced displays can remain unnumbered. Prefer `\label{...}` and `\eqref{...}` over manually maintained `\tag{S.17}`, unless manual numbering is an explicit manuscript convention. Preserve the established scheme unless the user requests renumbering.

### 9.3 Break long equations at logical operations

Use `aligned`, `split`, or `multline`. Break at equalities, inequalities, major additive terms, or logical decompositions. Do not force one-line formulas through scaling, unreadable negative spacing, or compressed notation.

### 9.4 Treat displays as parts of sentences

Punctuate displays according to the sentence, for example: “Therefore,” followed by \(d(\widehat\pi_n,\pi_0)=O_p(\tau_n),\) and “which proves the claim.” Displays are not graphics disconnected from prose.

### 9.5 Make theorem and proof boundaries clear

Avoid orphaned proof headings, awkward separation of a theorem from its proof, detached lemma titles, crowded proof endings and following headings, and matrices exceeding the text width. Repair disruptive page breaks locally without changing theorem content.

### 9.6 Synchronize notation and equation labels globally

After renaming or moving equations, check every `\ref` and `\eqref`, theorem and appendix references, citation keys, duplicated labels, and undefined labels. Remove stale notation, obsolete theorem numbers, and references to deleted lemmas left by copying passages.

### 9.7 Compile and inspect

For TeX artifacts, preserve macros and packages, define new macros, compile in the full manuscript or a faithful minimal wrapper, resolve errors, check references, and inspect affected rendered pages. Focus on long displays, theorem boundaries, matrices, bibliography, page breaks, and equation references.

Report unavailable compilation or missing fonts/packages accurately. Do not claim compilation or visual inspection without performing it.

### 9.8 Keep layout decisions from changing mathematics

Do not remove qualifiers, merge distinct assumptions, obscure logical steps, or change mathematical grouping to shorten an equation or improve a page break. **Layout may change presentation, never mathematical meaning.**

## 10. Verify citations and compare literature responsibly

Sections 5–7 address mathematical applicability of external results. Section 10 addresses **bibliographic authenticity, result–citation correspondence, validity of literature comparisons, and citation–reference agreement**, rather than repeating that applicability proof.

### 10.1 Verify bibliographic identity

Use academic search engines for discovery, then prioritize publisher or journal pages, official supplements, author manuscripts, and cited books or monographs. For each important reference reported or retained, verify title, authors, journal/book, year, relevant volume and issue, pages/article number, and DOI.

If no DOI is found, say so; never invent one. Distinguish preprint and journal DOIs, corrections or errata, accepted manuscripts, and final versions.

### 10.2 Match the citation to the proposition actually borrowed

Topic similarity is insufficient. Function approximation does not automatically supply least-favorable-direction approximation; partial-likelihood results do not automatically establish joint dependent-censoring likelihood results; ordinary covering numbers do not automatically give bracketing entropy.

Every substantive citation should answer: **What exact mathematical ingredient is being borrowed?** Otherwise it may be topical rather than evidentiary.

### 10.3 Compare matched mathematical structures

Before calling a condition standard, check comparable estimator types, nuisance structures, observation mechanisms, and asymptotic targets. Before claiming weaker assumptions, compare exact conditions rather than impressions.

If a proof “follows Huang (1996)”, identify whether the borrowed element is the route, tangent-space argument, rate-theorem structure, or information calculation. Do not imply that all assumptions and model details coincide. Compare mathematical roles rather than topics alone.

### 10.4 Do not replace proof with precedent

A condition's appearance in a leading journal does not establish necessity, sufficiency, minimality, or applicability here. Precedent establishes only that a comparable condition appeared in a comparable problem. Sections 4–7 determine its role in the present theorem.

### 10.5 Check theorem numbering and versions

For pinpoint citations such as Theorem 3.4.1 of van der Vaart and Wellner (1996), or a proposed lemma citation to Pollard (1984), verify the edition, numbering, exact statement, notation, and hypotheses. Do not guess from secondary citations. Use the numbering of the version actually consulted.

### 10.6 Ensure citation–reference agreement

Check that every citation has an entry, every entry is used, author–year spelling agrees, duplicates are removed, DOIs identify the right versions, and supplements are distinguishable from main articles. Follow the manuscript's shared or separate bibliography arrangement. Do not claim a full-manuscript audit from a partial appendix alone.

### 10.7 Separate research notes from the manuscript bibliography

Papers consulted to assess assumptions, theorem targets, or style need not all enter the bibliography. Include works actually cited, supporting a statement, supplying a borrowed result, or providing a necessary comparison.

### 10.8 Preserve the boundary between applicability and source verification

Sections 5–7 ask whether the external theorem is mathematically applicable. Section 10 asks whether the source is correctly identified and accurately represented. Perform both checks without producing duplicate audits of the same issue.

## 11. Perform the final gatekeeping audit and deliver

This is the final gate, not another proof-writing stage. Confirm that requested claims are closed, no high-impact unresolved issue is hidden, the artifact is internally consistent, and the user receives an accurate account of changes and remaining issues.

### 11.1 Review in order of impact

Prioritize model/observation compatibility, theorem validity, assumption dependencies and feasible rates, technical-lemma sufficiency, citation accuracy, notation, prose, and layout, in that order. Do not polish punctuation, spacing, or fonts while a major mathematical gap remains unresolved.

### 11.2 Revisit the theorem inventory

Mark every Section 1 target as complete, conditional but complete, incomplete, or intentionally omitted. A long proof must not obscure the original inventory.

### 11.3 Classify unresolved issues by severity

**Mathematical error:** an error invalidating the claimed theorem must be repaired or reported as unresolved. If only the current argument fails, distinguish that from a false theorem.

**Missing premise:** decide whether to add a condition, reduce scope, or retain a conditional result.

**Citation uncertainty:** an argument may be valid while its source remains unverified; do not report source uncertainty as proof certainty.

**Editorial issue:** wording, redundancy, or layout may leave validity unaffected. Keep these separate from mathematical errors.

### 11.4 Reconcile authoritative ledgers

Check agreement among the theorem inventory, dependency map, notation ledger, assumption ledger, technical lemma ledger, theorem closure ledger, and proof-detail audit. Every final object, assumption, or lemma should have an identifiable source in these structures.

### 11.5 Check scope consistency

Confirm agreement between main text and appendix on estimand, model restrictions, estimator, theorem scope, and notation. Simulation and implementation descriptions must not suggest guarantees stronger than the theory. In particular, do not present a conditional theorem as an unconditional guarantee in the abstract or discussion.

### 11.6 Perform mechanical artifact QA

Check labels, theorem numbering, cross-references, bibliography, undefined notation, duplicate definitions, stale comments, tracked-change remnants, compilation errors, and rendering. When a compilable artifact is requested, compile it or accurately explain why compilation was unavailable.

### 11.7 Distinguish issue levels in reviews

A finding should give its location, type, mathematical consequence, and smallest adequate correction. Do not label every issue major or describe an optional stylistic preference as a proof defect.

### 11.8 Report actual changes for narrow edits

For a single lemma repair, assumption change, or section rewrite, focus the final report on what changed, why, and any unresolved issue affecting validity. Do not automatically audit the whole paper unless the change affects downstream mathematics.

### 11.9 Treat scores as assessments, not certification

Score only when explicitly requested, using clear dimensions such as correctness, assumption quality, proof architecture, notation, exposition, and citation reliability. State that a score is neither proof certification nor a journal-acceptance prediction.

### 11.10 Stop when the requested claim holds at the intended detail level

Once the theorem is closed, bridges are supplied, conditions are explicit, citations verified, and Section 7's recoverability standard met, stop expanding. Do not add edge cases, stronger theorems, unsolicited efficiency results, or new sufficient mechanisms for already explicit high-level conditions merely because more rigor could be displayed.

Reopen an accepted issue only when new evidence changes validity, the model or estimator changes, a source reveals an incorrect application, or the user requests a stronger result. **Stop when the requested claims follow correctly at the intended level of detail.**

### 11.11 Deliver according to the task

- **Draft/revision:** the final passage or artifact, a concise account of substantive changes, and remaining material issues.
- **Proof repair:** the corrected proof, the exact gap repaired, and any new condition or scope change.
- **Review:** prioritized findings with locations, consequences, and minimal corrections.
- **Artifact delivery:** an accessible file and accurate compilation/rendering status, without claiming unperformed checks.

The intended outcome is closed mathematics, proportionate exposition, verified sources, and an artifact matching the requested scope.
