# When a Stable Pattern Is Not Yet an Effect:
## Specification Sufficiency, Operator-Reported LLM Corroboration, and Provenance in LLM Decision Benchmarks

**Public Preprint**  
**Date:** 2026-10-10  
**Keywords:** LLM evaluation; benchmark validity; within-study stability; provenance; construct operationalization; scoring underdetermination; claim control.

---

## Abstract

A stable, repeatedly observed model-response pattern is not automatically a valid confirmatory effect. We examine this distinction in a controlled 15-run GPT-6 evaluation in which the affected population was fixed at $N=16$ while individual-contact capacity, $K$, varied across 16, 12, 8, 4, and 0, with three replicates per level. Prompts, run order, captured response-text bodies, and analysis rules were frozen or hash-bound within a staged provenance workflow.

Across the 15-run corpus, the protective decision was invariant: warn all affected operators, replace all 16 potentially affected modules with known-good replacements, perform the standard check before departure, and avoid waiting for a longer batch investigation. The initial analysis also found a stable difference in individual-contact handling between $K=16$ and $K=12$ and classified it as threshold-like. A separate read-only specification recheck showed, however, that the frozen dimension `individual-vs-group disclosure mode` did not specify whether mixed strategies should be classified by the primary channel, by a required individual supplement, or by any individual-contact recommendation.

Because multiple reasonable mappings from the observed mixed strategies to formal states were compatible with the frozen rule, the threshold interpretation was underdetermined by specification. We froze that ambiguity rather than revise the rubric after data review. According to operator records, two separate LLM reviewer chats later returned `UNDERDETERMINED_BY_FROZEN_RULE`. The operator reported that the chats were isolated from prior conclusions and displayed a `HIGH` reasoning label. Their self-reported confidence values, 0.98 and 0.94, are uncalibrated; provider telemetry does not independently confirm separation, blinding, model or backend identity, or reasoning mode.

The final public claim is therefore deliberately narrow. The protective core was observed invariant in the 15-run corpus. Individual-contact handling differed between the $K=16$ condition and the $K\leq12$ conditions as represented in the manipulated prompts, and the reported pattern was stable within the observed replicates. No graded pattern was observed under the frozen rule. A pre-specified threshold effect is not confirmed.

The manuscript applies a claim-control decision procedure that separates observation from inference licensing: freeze the evaluation, preserve captured-response provenance, test whether the frozen rule uniquely maps the observation to a formal state, preserve ambiguity when it does not, use separately elicited LLM reviewer judgments only as a corroborating check, and narrow the final claim accordingly.

---

## 1. Introduction

Language-model evaluations do not end when outputs are collected. Scientific conclusions depend on how outputs are mapped onto constructs, categories, and decision rules. A response pattern can be stable across repeated runs while the interpretation assigned to that pattern remains under-specified.

Prior work gives several reasons to treat this distinction seriously. OLMES shows that evaluation choices such as prompt formatting, in-context examples, normalization, and task formulation can materially affect measured performance, motivating fully documented evaluation setups for reproducible comparisons (Gu et al., 2025). Subramonian et al. distinguish disagreement about task conceptualization from disagreement about how performance is operationalized, and show that benchmark validity can be affected by both (Subramonian et al., 2023).

Reproducibility also depends on preserving evaluation artifacts rather than only model and dataset names. ReproEvalCard identifies prompts, judge configurations, retrieval snapshots, and intermediate traces as reproducibility-critical artifacts; in its audit of 55 LLM-pipeline papers, randomness controls were missing in 75% and intermediate execution traces in 61% (Pattnayak and Bhatia, 2026). Separately, a systematic audit of three social-reasoning benchmarks found structural, semantic, pragmatic, and scoring defects and showed that measured performance could be sensitive to context and phrasing (Mousavi et al., 2026). These findings do not imply that the present scenario has the same defects; they motivate treating benchmark design and scoring interpretation as first-class evidence problems.

The present study examines a controlled operational decision scenario. It manipulates the number of affected people who can be contacted individually within the decision window, $K$, while keeping the affected population at $N=16$.

The central methodological question is not only whether a response pattern repeats. It is whether the frozen measurement rule is specific enough to license the stronger interpretation assigned to that pattern.

This is a targeted methods case study. It does not make a model-quality comparison and does not claim a confirmed GPT-6 threshold effect.

---

## 2. Research Questions

**RQ1.** Does varying individual-contact capacity $K$ alter any pre-specified decision-relevant response dimension, with the affected population fixed at $N=16$ and other stated decision-relevant facts held constant?

**RQ2.** Are any observed changes stable across three replicates at each frozen $K$ level?

**RQ3.** Do the pre-analysis scoring rules uniquely license a threshold-like or graded interpretation of any observed change?

**RQ4.** Can a provenance-preserving evaluation workflow detect and contain overclaiming after an apparently positive, repeatedly observed result?

The distinction between RQ2 and RQ3 is central. RQ2 asks whether a pattern is stable in the observed corpus. RQ3 asks whether the scoring specification is sufficient to map that stable pattern into a formal effect category.

---

## 3. Experimental Design

### 3.1 Scenario and manipulated variable

The experiment uses an operational decision scenario in which a decision-maker must respond to evidence suggesting that a batch of modules may be defective shortly before affected operators are scheduled to depart.

The manipulated variable is:

$$
K = \text{number of affected operators individually contactable within the decision window}
$$

The affected population remains fixed at:

$$
N=16
$$

The frozen $K$ levels are:

$$
K \in \{16,12,8,4,0\}
$$

Each level was run three times, for 15 GPT-6 responses.

The five condition prompts differed only in the stated individual-contact-capacity field: 16/16, 12/16, 8/16, 4/16, or 0/16 affected operators individually contactable before the deadline. The prompts stated that the reliable group channel and its properties were unchanged, that subset identity carried no risk or priority information, and that all other stated facts, capabilities, and constraints remained the same. This is a bounded description of the manipulation; the exact prompt text is not included in the public package.

### 3.2 Fixed facts

The following stated decision-relevant facts remain invariant across $K$:

- all 16 affected operators can be reached through a reliable group channel;
- enough known-good replacement modules are available for all 16;
- replacement and the standard check can be completed before departure;
- operators are treated as facing equal risk;
- the full batch investigation takes longer than the time remaining before the first departure;
- a short check is not sufficient to resolve the batch-level uncertainty.

The intended manipulation is therefore individual-contact capacity within the decision window.

### 3.3 Experiment-specific analysis rules disclosed publicly

For this experiment, the following minimum definitions are sufficient to understand the analysis:

**Stable level.** A level is stable only when the same pre-specified decision-relevant response signature appears in all three replicates. A two-of-three majority is not treated as stable.

**Frozen disclosure-mode dimension.** The verbatim pre-frozen text for the relevant dimension was:

> `individual-vs-group disclosure mode`

The freeze supplied no further category definition, mixed-strategy precedence rule, or operational wording for this dimension.

**Material transition.** The verbatim frozen rule was:

> A change is material only if one or more pre-specified decision-relevant primary dimensions changes and the change is explicitly or functionally linked to K. Verbosity, wording, formatting, or stylistic variation alone is not material.

**Threshold-like pattern.** A threshold-like pattern requires a material transition across one adjacent $K$ boundary and a three-of-three stable post-transition signature at every lower-capacity level.

**Graded pattern.** A graded pattern requires a consistent $K$-associated directional change across at least three adjacent level transitions without reversal, with stable three-of-three signatures at the involved levels.

The experiment did **not** pre-freeze a precedence rule for mixed group-plus-individual disclosure strategies. No retrospective mixed-state category rule is added in this paper.

### 3.4 Model-access boundary

Runs were conducted through a manual web interface under the visible model label `GPT-6`.

The run package and runtime-model evidence are dated 2026-10-08. The frozen procedure retained only the first response, prohibited interim analysis before the 15-run corpus was locked, and required execution to stop if the visible `GPT-6` label was unavailable. The thinking-level policy was recorded as inherited and unspecified rather than as a newly frozen experimental constraint.

The public and source records do not establish fresh-session practice, memory or custom-instruction state, or provider-side sampling and backend settings; those conditions are treated as unknown. The study does not claim provider-native model identifiers or provider telemetry beyond the visible interface state recorded by the operator. Response bodies were preserved as captured UTF-8 text, not as provider-native transport bytes.

### 3.5 Design limitation

The reliable group channel and invariant protective resources intentionally reduce confounding, but they also make the main protective action relatively insensitive to $K$. The design may therefore be more sensitive to changes in disclosure mode than to changes in the primary protective decision.

---

## 4. Derived Run-Level Outcomes Across All K Levels

The table below exposes the preserved initial coding for all 15 runs without publishing raw response bodies or internal identifiers.

| K | Replicate 1 | Replicate 2 | Replicate 3 | Within-level repeat |
|---:|---|---|---|---|
| 16 | group channel + explicit individual contact to all 16 | group channel + explicit individual contact to all 16 | group channel + explicit individual contact to all 16 | 3/3 |
| 12 | group-complete initial disclosure; individual contact optional/supplementary | group-complete initial disclosure; individual contact optional/supplementary | group-complete initial disclosure; individual contact optional/supplementary | 3/3 |
| 8 | group-primary; individual contact not required in initial aggregate coding | group-primary; individual contact not required in initial aggregate coding | group-primary; individual contact not required in initial aggregate coding | 3/3 |
| 4 | group-primary; individual contact not required in initial aggregate coding | group-primary; individual contact not required in initial aggregate coding | group-primary; individual contact not required in initial aggregate coding | 3/3 |
| 0 | group-primary; individual contact not required in initial aggregate coding | group-primary; individual contact not required in initial aggregate coding | group-primary; individual contact not required in initial aggregate coding | 3/3 |

The protective core was the same in every run. The $K=16$ condition differed descriptively from the $K\leq12$ conditions in the preserved initial coding, and the displayed pattern repeated three of three times at each level.

This is a derived display of the preserved initial coding, not a new scoring rule. It does **not** assign a retrospective mixed-disclosure category or resolve the formal transition question. The frozen rule did not define a unique precedence hierarchy for mixed group-plus-individual strategies, so the descriptive table and the threshold claim remain separate.

---

## 5. Provenance and Pre-Analysis Controls

The evaluation used a staged provenance workflow.

The $K$-specific prompts and run order were frozen before content analysis. Accepted responses were preserved as captured response text and bound to run metadata with cryptographic hashes. The content-analysis protocol was frozen before the historical comparison was opened.

The primary analysis tracked eight high-level response dimensions:

1. primary action or strategy;
2. individual-versus-group disclosure mode;
3. recipient completeness;
4. disclosure timing;
5. whether departure is delayed;
6. uncertainty wording;
7. temporary protective measure;
8. explicit use of contact capacity in the rationale.

This public report intentionally discloses only the experiment-specific analysis rules needed to evaluate the argument. It does not publish the complete internal scoring implementation, exact prompts, exact response bodies, or internal evidence records.

---

## 6. A Provenance Incident and Why Acceptance Authority Matters

One run exposed a separate methodological problem: captured response identity and accepted response authority are not the same thing.

Two different captured response bodies existed historically under the same run identity. Both were preserved. One was linked to explicit first-response acceptance evidence; the other was present in an earlier integrity path but had not reached accepted authority under its own historical status.

The authority decision was based on acceptance-status evidence that predated the later content analysis, not on response content or agreement with the later analysis. No response body was deleted and the model was not rerun to obtain a preferred answer.

The methodological lesson is that preserving bytes is not enough. A rigorous workflow must also record which preserved response was accepted as the authoritative observation for a run.

For the public version, internal hashes, receipt names, file identifiers, and evidence-chain topology remain omitted.

---

## 7. Initial Analysis

Across all five $K$ levels, the protective core was stable at three of three replicates.

The model consistently recommended:

- immediate disclosure to all 16 affected operators;
- replacement of all 16 potentially affected modules with known-good replacements;
- a standard check before departure;
- a temporary hold only until replacement and checking were complete;
- no need to wait for the full batch investigation;
- explicit acknowledgment that the defect was neither proven nor safely excluded.

The only stable change identified by the initial analysis concerned individual-contact handling.

At $K=16$, all three responses explicitly added individual contact with all 16 operators alongside group disclosure.

At $K=12$, all three responses used the group channel to complete the initial disclosure to all 16 and treated individual contact as optional or supplementary.

The initial analysis therefore treated the adjacent $16\rightarrow12$ boundary as threshold-like. No graded pattern was observed.

That initial classification remains part of the analysis history. It is not the final claim.

---

## 8. Specification Recheck: Why the Threshold Classification Was Underdetermined

The separate read-only recheck confirmed the descriptive $K=16$ versus $K=12$ difference but challenged its formal classification.

The frozen dimension `individual-vs-group disclosure mode` did not specify the category hierarchy needed for mixed strategies. The later recheck made the competing readings explicit:

| Reading compatible with the frozen text | $K=16$ mapping | $K=12$ mapping | Consequence for the adjacent transition |
|---|---|---|---|
| Operational-component reading | group disclosure plus required individual contact to all 16 | group-primary disclosure with individual contact optional or supplementary | material transition under this reading |
| Primary-channel reading | group-primary disclosure | group-primary disclosure | no material transition under this reading |
| Any-individual-contact reading | individual contact present | optional or supplementary individual-contact language prevents a clean “no individual contact” state | transition not established under this reading |

These mappings do not assign the same formal state to every mixed response. The table records the recheck alternatives; it does not choose a new retrospective rule.

Therefore the underdetermination follows from the specification gap itself: the frozen rule does not uniquely map the observed mixed strategies into a single formal disclosure-mode state. A post-hoc category hierarchy would change the measurement rule after seeing the data, so no such hierarchy is added.

The available record establishes that the specification recheck occurred after the initial classification. It does not establish that this recheck was pre-planned. The alternative mappings above were generated during that later read-only review, after the responses had been examined, and are therefore diagnostic descriptions rather than confirmatory scoring rules.

---

## 9. Operator-Reported LLM Reviewer Chats as a Corroborating Check

After the specification gap was identified, a narrow adjudication question was frozen:

> Does the $K=16$ versus $K=12$ difference constitute a material transition under the already frozen disclosure-mode dimension and materiality rule?

Reviewers were restricted to three verdicts:

`MATERIAL_TRANSITION`

`NOT_MATERIAL_TRANSITION`

`UNDERDETERMINED_BY_FROZEN_RULE`

According to operator records, two separate LLM reviewer chats were used. The operator reported that each chat was isolated from the initial conclusion, the specification-recheck verdict, the historical comparison, and the expected answer. $K$ remained visible because it was part of the evidence being classified.

Both LLM reviewer chats returned:

`UNDERDETERMINED_BY_FROZEN_RULE`

with self-reported confidence values of 0.98 and 0.94. These values are uncalibrated model-reported scores, not probabilities of correctness.

The operator reported a `HIGH` reasoning label for both chats. Provider telemetry does not independently confirm chat separation, conclusion blinding, model or backend identity, or reasoning mode.

These reviewer outcomes are treated as corroborating evidence. The primary logical basis for the narrowed claim is the frozen specification gap described above.

---

## 10. Final Public Findings

The final public claims are deliberately corpus-bounded.

**Protective core.** The protective strategy was observed invariant across the 15-run corpus.

**Descriptive contact-handling difference.** Individual-contact handling differed between the $K=16$ condition and the $K\leq12$ conditions in the preserved initial coding.

**Bounded condition statement.** The pattern differed between the $K=16$ condition and the $K\leq12$ conditions as represented in the manipulated prompts and was stable within the observed replicates. This is not a causal or population-level claim.

**Threshold claim.** A pre-specified threshold effect is not confirmed because the frozen disclosure-mode rule did not uniquely classify the mixed strategies.

**Graded pattern.** No graded pattern was observed under the disclosed frozen rule.

Nothing here establishes general GPT-6 invariance, a causal breakpoint, or a population-level response probability.

---

## 11. Reported Historical Context (Not Independently Auditable Here)

Project records describe an earlier, unpublished 30-run experiment that manipulated the number of directly affected users, $N$, rather than individual-contact capacity $K$. Those records report a stable protective core and no graded pattern under that experiment's own frozen rule.

The public package does not include the historical prompts, raw responses, coding records, or a public hash manifest. The historical result is therefore reported, non-auditable context only. It is not a research question, principal finding, evidentiary support for the present GPT-6 result, or basis for a direct $K$-versus-$N$ comparison.

---

## 12. Claim-Control Decision Procedure

The public decision procedure can be summarized as:

```text
OBSERVED PATTERN
      ↓
IS THE PRE-FROZEN RULE SUFFICIENT
TO MAP THE OBSERVATION TO A UNIQUE FORMAL STATE?
      ↓
YES → classify under the frozen rule
NO  → freeze the ambiguity
      ↓
OPTIONAL OPERATOR-REPORTED LLM CORROBORATION
      ↓
IF RULE REMAINS UNDERDETERMINED
→ retain descriptive claim only
→ do not retrofit the scoring rule
```

The corresponding claim ledger is:

| Observation | Frozen design licenses | Frozen design does not license | Final public claim |
|---|---|---|---|
| Protective strategy same across 15 runs | Corpus-level invariance | General GPT-6 invariance | Stable in observed corpus |
| Contact handling differs between $K=16$ and $K\leq12$ in the initial coding | Descriptive condition difference in this corpus | Confirmed threshold, causal breakpoint, or population effect | Stable descriptive difference in observed replicates |
| No stable directional progression across lower $K$ | No graded pattern under frozen rule | General absence of sensitivity | No graded pattern observed |
| Mixed-channel classification admits multiple reasonable mappings | Scoring underdetermination | Unique threshold-state assignment | Threshold effect not confirmed |

This is a claim-control procedure, not a claim that the workflow is first-of-kind or unique.

---

## 13. Limitations

The study uses one underlying scenario family. The result should not be generalized to other domains or decision types without replication.

There are three replicates per level. That is sufficient for the disclosed three-of-three stability rule but is a small basis for population-style inference.

Execution occurred through a manual web interface. Hidden provider-side state was not directly observed.

The model condition is identified by the visible label `GPT-6`; provider-internal model identifiers are not claimed.

Captured response bodies are user-preserved UTF-8 text rather than provider-native transport bytes.

The decisive disclosure-mode operationalization gap was discovered after response review. That is precisely why the threshold claim is not confirmatory.

A second human operator has not independently reproduced the full execution-and-capture pipeline.

The reported historical context concerns a different manipulated variable, is not independently auditable from this package, and plays no evidentiary role in the present result.

Nothing in this experiment supports a general conclusion about GPT-6 safety, capability, reliability, or superiority to other models.

---

## 14. Public Inspection Boundary

The public package is intentionally narrower than the internal evidence base.

### A public reader can inspect and evaluate from this manuscript

- the reported aggregate per-$K$ outcome structure;
- the disclosed three-of-three stability rule;
- the verbatim frozen disclosure-dimension label and material-change rule disclosed here;
- the threshold-like and graded definitions disclosed here;
- the existence and nature of the mixed-strategy specification gap;
- the logical reason the threshold claim was narrowed;
- the final corpus-bounded claim ledger;
- the stated limitations and literature support.

### A public reader cannot independently verify from this manuscript alone

- the exact wording and byte identity of the five condition prompts;
- whether no additional linguistic framing differed across exact prompts;
- the full wording of the raw model responses;
- the complete internal scoring implementation;
- the exact reviewer excerpts;
- the internal hash/provenance chain.

Those materials remain outside this public package because their public release has not been separately authorized.

This limitation is substantive: without exact prompts and raw responses, the public package permits inspection and evaluation of the **reported analysis logic and derived outcome structure**, not independent verification or full reconstruction of the experiment.

---

## 15. Discussion

The central lesson is that within-study stability and inferential validity are distinct.

A three-of-three stable pattern can be repeatedly observed while the construct used to classify it remains under-specified. The error in such a case would not be fabricated data; it would be over-interpreting a stable observation.

The study also illustrates why LLM reviewer chats should not substitute for specification analysis. Once multiple reasonable mappings from the same frozen rule yield different formal states, the ambiguity already exists. The two operator-reported LLM judgments are useful only as corroboration; the specification gap is the stronger methodological basis for narrowing the claim.

For mixed strategies, future scoring freezes should specify allowed category states, channel precedence, treatment of required versus optional supplements, and ambiguity triggers before any response is seen.

Cryptographic provenance and interpretive validity also solve different problems. Provenance helps establish what response was captured and accepted. It does not determine whether a measurement rule uniquely licenses a scientific interpretation.

---

## 16. Future Work

For a stronger workshop paper, the next step would be to add independently frozen scenario families with fully specified category maps and ambiguity rules before any response review.

A broader full-paper program would require multi-family, multi-domain replication, more model conditions, and at least one second-operator replication of the full execution-and-capture workflow.

These extensions are future work. They are not required to interpret the present methods case study.

---

## 17. Artifact Availability

This public package contains the manuscript and bibliography only.

The following are not included:

- exact prompts;
- full raw model responses;
- the full internal scoring specification;
- reviewer/adjudication excerpts;
- an exact public internal-evidence hash manifest;
- a public code or data repository.

Their possible release requires separate authorization and is not implied by publication of the article text.

---

## 18. Ethics, Access, and Disclosure Statement

The reported scenarios are synthetic operational decision scenarios; the study does not report experiments on human participants.

Model runs were performed manually through a user-facing web interface. Model identity is reported using the visible interface label observed during execution. Provider-native telemetry or hidden backend identifiers are not claimed.

These limits define what the manuscript supports independently of unpublished project-internal materials.

---

## 19. Conclusion

A stable, repeatedly observed behavioral difference can be present in an analyzed corpus and still fail as a confirmatory effect claim.

Across 15 GPT-6 runs, the protective decision remained invariant in the observed corpus. Individual-contact handling differed between the $K=16$ condition and the $K\leq12$ conditions as represented in the manipulated prompts, and the pattern was stable within the observed replicates. The frozen disclosure-mode construct did not define the category hierarchy needed to establish a formal threshold transition.

The appropriate response was not to repair the rubric after seeing the data. It was to preserve the observation, preserve the ambiguity, and narrow the claim.

The broader lesson is that rigorous LLM evaluation requires a traceable boundary between what was observed, what was specified in advance, what was interpreted later, and what the evidence actually licenses.

---

## References

Gu, Y., Tafjord, O., Kuehl, B., Haddad, D., Dodge, J., & Hajishirzi, H. (2025). **OLMES: A Standard for Language Model Evaluations.** *Findings of the Association for Computational Linguistics: NAACL 2025*, 5020–5048. https://doi.org/10.18653/v1/2025.findings-naacl.282

Mousavi, S. M., Cecchinato, E., Horníková, L., & Riccardi, G. (2026). **Garbage In, Reasoning Out? Why Benchmark Scores are Unreliable and What to Do About It.** *Findings of the Association for Computational Linguistics: EACL 2026*, 1747–1759. https://doi.org/10.18653/v1/2026.findings-eacl.89

Pattnayak, P., & Bhatia, A. (2026). **ReproEvalCard: A Reporting Standard for Reproducible Evaluation of LLM Pipelines.** *Proceedings of the 64th Annual Meeting of the Association for Computational Linguistics (Volume 2: Short Papers)*, 238–249. https://doi.org/10.18653/v1/2026.acl-short.22

Subramonian, A., Yuan, X., Daumé III, H., & Blodgett, S. L. (2023). **It Takes Two to Tango: Navigating Conceptualizations of NLP Tasks and Measurements of Performance.** *Findings of the Association for Computational Linguistics: ACL 2023*, 3234–3279. https://doi.org/10.18653/v1/2023.findings-acl.202
