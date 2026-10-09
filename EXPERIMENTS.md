# Open ULA — Experimental Framework

**ULA Robot Intelligence System (ULA-RIS)**  
**Research v0.1 · Proposed framework · Not yet validated**

> **Purpose:** Determine whether a maintained, action-relevant Cognitive Foundation, jointly used with current multimodal perception, makes a measurable incremental contribution to **Task Success, Generalization, and Deployment Efficiency**. Architecture is an intervention to test, not evidence that the hypothesis is true.

## 1. Purpose and scope

This document describes a **prioritized, independently testable experimental framework**, not a complete executable protocol or a commitment to run every experiment. It maps to [OPEN_QUESTIONS.md](OPEN_QUESTIONS.md) (Q1–Q12), uses the canonical terms in [GLOSSARY.md](GLOSSARY.md), and applies the distinct evidence standards of [HYPOTHESIS.md](HYPOTHESIS.md). Functional boundaries are described in [ARCHITECTURE.md](ARCHITECTURE.md).

**H-R (Root-cause Hypothesis):** Deficiencies in sufficiently persistent, compositional, action-grounded Cognitive Foundation may contribute meaningfully to observed limitations. **H-I (Intervention Hypothesis):** Making that foundation functionally available and using it jointly with perception may improve measured outcomes under comparable conditions. Neither hypothesis follows automatically from the other.

**Independence rule:** An experiment may be run without completion of earlier tiers. Priority indicates research decision value, not a prerequisite. Component improvements support only the corresponding tested subclaim; they do not establish H-R or overall ULA-RIS superiority.

## 2. Experimental design principles

1. **Strong baselines first.** Include competitive history-based, learned implicit-state, learned-planning, and other relevant approaches; do not deliberately handicap perception-to-action systems.
2. **Predeclare evidence criteria.** Before running, specify outcomes that support, weaken, or leave each tested claim unresolved; register tasks, splits, metrics, exclusions, and analysis decisions.
3. **Account for resources and information.** Report observations/history, training data, model capacity, compute, memory, latency, engineering adaptation, and human support. Record mismatches that cannot be eliminated.
4. **Separate feedback timescales.** Immediate state update and correction are not validated experience consolidation. Define their operational latency and data boundaries for each test.
5. **Report overhead and negative results.** Include regressions, unsafe events, uncertainty, failure cases, and intervention costs; do not selectively report favorable task families.
6. **Do not infer causality from naming.** A component called *cognitive* or *object-centric* has no privileged causal status. Test function and information access, not labels.
7. **Compare efficiency at comparable Task Success.** Report performance–resource trade-offs rather than isolated reductions in data or inference time.
8. **Separate intelligence from embodiment.** Match hardware and action capabilities where possible; distinguish decision errors from sensing, actuation, control, and hardware failures.

## 3. Priority tiers and traceability

| Priority | Experimental focus | Open questions | Evidence role |
|---|---|---|---|
| **Tier 1 — Core validity** | Persistent state, cognition–perception arbitration, predeclared interpretation | Q1, Q4, Q11 | Test central H-I subclaims and discipline H-R inference |
| **Tier 2 — Mechanisms** | Update versus consolidation, workflow composition, object-centric manipulation | Q6, Q9, Q10 | Isolate specific functional contributions |
| **Tier 3 — System and deployment** | APWM efficiency, awareness integration, uncertainty, experience transfer, improvement, deployment value | Q2, Q3, Q5, Q7, Q8, Q12 | Characterize scope, costs, and system-level value |

Q11 is a **cross-experiment evidence protocol**, not a separate robot-performance intervention. Q6's distinction between immediate update and validated consolidation applies from Tier 1 onward even when Q6's own experiment is deferred.

## 4. Tier 1 — Core validity

### EXP-1.1 — Persistent state against strong baselines (Q1)

- **Research question:** Does explicitly maintained, action-relevant physical-world state improve cross-time decisions beyond access to equivalent observations or learned implicit memory?
- **Hypothesis:** H-I persistence subclaim; diagnostic failure patterns may inform H-R but cannot establish it alone.
- **Baselines:** (a) no explicit maintained state with equal-length history; (b) equal information arranged in another accessible format; (c) learned implicit state, such as RNN memory, transformer memory, or learned latent state. Baselines must be competent and tuned fairly.
- **Intervention / perturbation:** Provide maintained task-relevant world state; vary delays, occlusions, object relocations, state changes, and unfamiliar environments while holding available action capabilities fixed.
- **Metrics:** Task Success and first-attempt success; cross-time state accuracy; unnecessary reacquisition/re-observation; human intervention; retrieval latency, memory, compute, and adaptation cost.
- **Confounders:** Different effective information, context length, training exposure, model capacity, compute, retrieval effort, and leakage from evaluation scenes.
- **Interpretation:** Improvement over (a) alone shows value beyond that baseline, **not** superiority to implicit memory. If benefits disappear against (c), the necessity or incremental value of this explicit representation is weakened in the tested regime. Comparable gains with lower total cost may support deployment efficiency. Failure attribution for H-R needs additional controlled diagnostic evidence.

### EXP-1.2 — Cognition–perception conflict arbitration (Q4)

- **Research question:** When maintained state and current perception disagree, does an explicit, testable arbitration behavior improve decisions?
- **Hypothesis:** H-I joint-grounding subclaim.
- **Baselines:** Perception-priority, maintained-state-priority, and a strong fusion policy without the proposed explicit arbitration; where appropriate compare confidence-based and learned arbitration alternatives. **Oracle arbitration** may be reported as a hindsight upper bound, never as a deployable or information-matched baseline.
- **Intervention / perturbation:** Arbitration using **recency, provenance, confidence, and task relevance**; introduce stale state, occlusion, noisy observations, and conflicting evidence. Predefine when the system should re-observe, ask, defer, or act.
- **Metrics:** Task-relevant decision accuracy, calibration, unsafe decisions, unnecessary interventions, Task Success, **arbitration attribution accuracy** (stale cognition, noisy perception, or both, where ground truth permits), and latency/compute overhead.
- **Confounders:** Observation quality, access to extra evidence, model/fusion capacity, task distribution, confidence calibration, and unequal fallback opportunities.
- **Interpretation:** Benefits with matched information and resources support the tested arbitration mechanism. Benefits attributable only to additional observations or capacity do not isolate joint grounding. A universal rule that fails under identifiable conflict conditions weakens that rule, not all cognition–perception integration. Oracle gaps indicate headroom, not the deployable benefit of a particular arbitration strategy.
- **Dependency:** This experiment presumes some form of maintained cognition. If EXP-1.1 finds no measurable value in explicit persistent state, arbitration may instead be tested against learned implicit-state alternatives.
- **Boundary:** Basic uncertainty thresholds may be predefined here; adaptive uncertainty-management policies are evaluated separately in EXP-3.3.

### EXP-1.3 — Predeclared H-R / H-I evidence protocol (Q11)

- **Research question:** Can each experiment distinguish evidence about a proposed root cause from evidence about an intervention?
- **Hypotheses:** H-R and H-I are assessed **separately**.
- **Baseline:** Not applicable: this is an evidence-governance protocol, not a performance comparison.
- **Procedure:** Before data collection, specify the intervention contrast, diagnostic perturbations, plausible alternative causes, positive/negative/inconclusive patterns, minimum meaningful effects, statistical uncertainty, and allowed conclusions. Freeze the analysis plan or record deviations transparently.
- **Metrics:** Completeness of preregistered contrasts, reproducibility, uncertainty reporting, alternative-explanation coverage, and adherence to declared interpretation rules.
- **Confounders:** Post-hoc threshold changes, selective task selection, unbalanced baselines, unreported resource differences, and circular causal explanations.
- **Interpretation:** An intervention gain supports H-I under tested conditions but does not prove H-R. Controlled mechanism perturbation or convergent diagnostics that weaken alternatives can strengthen H-R. A missing preregistration limits confirmatory interpretation; it does not make exploratory findings worthless if labeled accordingly.

## 5. Tier 2 — Mechanism experiments

### EXP-2.1 — Immediate update versus validated consolidation (Q6)

- **Research question:** Which observations may safely update maintained world state immediately, and which interaction lessons require validation before reuse?
- **Hypothesis:** Separating world-state maintenance from experience consolidation reduces erroneous carryover without sacrificing timely task correction.
- **Baselines:** Unrestricted direct reuse of interaction outcomes; no long-term consolidation; alternative validation/gating policies with comparable memory and data.
- **Intervention / perturbation:** Route observed state changes to maintained world state; route candidate generalizable lessons through evaluation, validation, and controlled consolidation. Inject ambiguous observations, one-off failures, spurious success, and distribution shifts. Declare latency bounds for *immediate* and *validated* updates.
- **Metrics:** State freshness, repeated-error rate, false lesson adoption, harmful transfer, recovery success, Task Success, human review time, and latency.
- **Confounders:** Different update frequencies, extra supervision, retained data, validation compute, and delayed availability of correct state.
- **Interpretation:** Lower harmful reuse at acceptable recovery latency supports separation. If benefits are explained solely by extra human review or training, report that limitation. Neither a single failure nor a single success is automatically a validated lesson.

### EXP-2.2 — Workflow Composition incremental value (Q9)

- **Research question:** Does goal- and situation-conditioned workflow composition add value beyond strong alternatives?
- **Hypothesis:** Composing and adapting semantic actions may improve success on unseen task combinations and reduce per-task engineering.
- **Baselines:** (a) fixed workflow library; (b) capacity-matched learned planner; (c) strong LLM-based planner with matched information and compute, when applicable.
- **Intervention / perturbation:** Explicitly distinguish disabling **composition itself**, **goal-conditioned composition**, and **situation-conditioned recomposition**. Test novel combinations, changed preconditions, and recoverable interruptions.
- **Metrics:** Task Success, generalization gap, recovery success, plan revisions, task time, human intervention, engineering time, and compute.
- **Confounders:** Planner/model capacity, access to action descriptions, demonstrations, prompt engineering, available tools, and training-task overlap.
- **Interpretation:** Report which ablation and baseline generated each effect. Gains from extra information or compute do not independently establish a composition advantage; success on a narrow library does not establish open-world generalization.

### EXP-2.3 — Object-state information versus object-centric organization (Q10)

- **Research question:** Is manipulation improved by access to object state, by organizing reasoning around the operated object, or both?
- **Hypothesis:** Object-centric grounding may improve adaptive physical interaction beyond merely supplying object-state features.
- **Baselines / factorial contrast:** Compare **object-state information present/absent** and **object-centric versus alternative reasoning organization** wherever both factors can be varied without changing action capabilities. A robot-centric system receiving the same object-state information is a critical control.
- **Intervention / perturbation:** Ground semantic actions in target-object state, affordances, relevant physical properties, relative pose, contact constraints, and observed outcomes; vary object identity, pose, materials, and interaction conditions.
- **Metrics:** Task/first-attempt success, recovery, completion time, intervention minutes, damage/drop/spill/collision rates, contact reliability, and adaptation effort.
- **Confounders:** Unequal object information, perception accuracy, controller quality, robot morphology, tactile sensing, training exposure, and action budgets.
- **Interpretation:** A main effect of object information is **not** evidence that object-centric organization adds value. The latter requires a controlled comparison with the same information and capabilities. Physical safety and task performance must both be reported.
- **Precondition:** Object-state estimates must be of sufficient quality for both object-centric and alternative reasoning organizations. If object-state estimation is unreliable, report that limitation separately; it does not isolate the contribution of object-centric organization.

## 6. Tier 3 — System and deployment experiments

Each experiment below is independently runnable; detailed task lists, thresholds, and statistical plans belong in study-specific protocols.

### EXP-3.1 — APWM representation and maintenance (Q2)

- **Hypothesis:** Selective persistent physical-world state can preserve action-relevant accuracy without exhaustive reconstruction.
- **Baselines:** Re-observe-on-demand, matched history, **structured spatial maps, relational graphs, and learned latent-state representations**, with information and compute matched where feasible and mismatches reported.
- **Intervention / perturbation:** Compare selective updates under occlusion, relocation, delayed observation, and environmental change.
- **Metrics:** Cross-time state consistency, Task Success, re-observation burden, memory, compute, initialization/adaptation effort.
- **Confounders:** Scene complexity, sensor coverage, prior maps, and update frequency.
- **Interpretation:** Representation efficiency matters only when action-relevant accuracy and performance remain comparable. **APWM — AI Physical World Model** is not itself navigation, planning, or manipulation.

### EXP-3.2 — Awareness interaction (Q3)

- **Hypothesis:** Coordinating World, Situation, and Self Awareness improves context-sensitive decisions.
- **Baselines:** Individual awareness sources; pairwise combinations of World, Situation, and Self Awareness; and a **single undifferentiated state representation with matched information**. Match model capacity and compute where feasible.
- **Intervention / perturbation:** Vary situation changes, robot capability constraints, and physical-world state.
- **Metrics:** Decision feasibility, Task Success, recovery, intervention, and compute.
- **Confounders:** Extra state features, planning capacity, and unequal task context.
- **Interpretation:** Identify which interaction adds value; do not assume three awareness functions require three databases.

### EXP-3.3 — Observe, ask, defer, or act (Q5)

- **Hypothesis:** Uncertainty-aware decision policies reduce unsafe or wasteful actions at acceptable interaction cost.
- **Baselines:** Always-act, fixed re-observation, and strong learned uncertainty policies.
- **Intervention / perturbation:** Manipulate ambiguity, occlusion, and risk; allow re-observation, clarification, deferral, or action.
- **Metrics:** Task Success, unsafe events, calibration, unnecessary questions, delay, and human intervention.
- **Confounders:** Different observation budgets, risk thresholds, and human assistance.
- **Interpretation:** Lower risk alone is insufficient if the system simply refuses useful tasks; report safety–completion trade-offs.

### EXP-3.4 — Validated experience transfer (Q7)

- **Hypothesis:** Evaluated experience transfers to related tasks without harmful overgeneralization.
- **Baselines:** No transfer, raw episodic retrieval, and matched fine-tuning/retraining alternatives.
- **Intervention / perturbation:** Reuse validated lessons across controlled changes in object, task, and environment.
- **Metrics:** Repeat-error reduction, transfer Task Success, negative transfer, correction effort, and compute/data cost.
- **Confounders:** Shared training examples, hidden task overlap, validation supervision, and retrieval budget.
- **Interpretation:** Gains restricted to near-duplicate tasks do not demonstrate broad transfer.

### EXP-3.5 — Measurable cognitive and capability improvement (Q8)

- **Hypothesis:** Controlled learning and consolidation produce durable, safe improvements across repeated use.
- **Baselines:** Frozen system, equal-data retraining, and alternative memory/learning updates.
- **Intervention / perturbation:** Evaluate held-out tasks before and after validated updates, including delayed retests and distribution shifts.
- **Metrics:** Task Success change, retained improvement, repeated-error rate, regressions, safety events, and update cost.
- **Confounders:** Additional training data, practice exposure, human corrections, and test contamination.
- **Interpretation:** Improvement after use is not automatically evidence of self-improving cognition; identify the causal update and its cost.

### EXP-3.6 — System-level and deployment value (Q12)

- **Hypothesis:** Integrated functionality can improve Task Success and Generalization while lowering total adaptation and support cost at comparable performance.
- **Baselines:** Strong end-to-end, hybrid, and other competitive systems with matched embodiment and reported resource budgets.
- **Intervention / perturbation:** Evaluate new environments, task mixes, long-duration use, and repeated deployments.
- **Metrics:** Task Success, Generalization, deployment engineering hours, data and training needs, human intervention minutes, compute, memory, latency, safety events, and total support cost.
- **Confounders:** Hardware quality, task selection, site difficulty, staffing, data reuse, and unequal operational support.
- **Interpretation:** A system-level win supports H-I only under the tested conditions and budgets. Higher complexity without commensurate value weakens the deployment case; H-R requires separate causal diagnostics.

## 7. Cross-experiment discipline and reporting template

Every study should publish or archive, to the extent permitted by safety, privacy, and intellectual-property constraints:

| Required record | Minimum content |
|---|---|
| **Question / claim** | Q-number, H-R diagnostic or H-I subclaim, and exact tested contrast |
| **Protocol** | Task family, inclusion/exclusion criteria, conditions, randomization, stopping rules |
| **Baselines** | Versions, tuning budgets, information access, and rationale for strength |
| **Intervention / perturbation** | What function changes; what is held constant; which ablation is disabled |
| **Outcomes** | Primary/secondary metrics, meaningful-effect threshold, uncertainty estimates |
| **Resources** | Data, training, inference, memory, latency, engineering, and human effort |
| **Confounders** | Known mismatches, leakage checks, embodiment constraints, safety conditions |
| **Interpretation** | Support / weaken / unresolved for each claim; alternatives and scope limits |
| **Reproducibility** | Task/environment specifications, hardware and software versions, seeds, and available artifacts |

**Predeclared outcome categories:**

- **Supports the tested H-I subclaim:** A meaningful, reproducible benefit over strong matched alternatives, with disclosed resource trade-offs and no unacceptable regressions.
- **Weakens the tested H-I subclaim:** No meaningful incremental benefit, or benefits erased by fair baselines or disproportionate cost, within the tested regime.
- **Strengthens H-R:** Controlled mechanism perturbations and/or convergent independent diagnostics implicate the proposed cognitive limitation while weakening plausible alternatives.
- **Weakens H-R:** Failures are better explained by alternatives, or targeted mechanism changes do not affect predicted failure patterns under adequately sensitive tests.
- **Unresolved:** Inconclusive uncertainty, confounding, insufficient sensitivity, contradictory findings, or untested alternatives.

**Predeclared research-direction decision rules (candidate triggers, not automatic verdicts):**

| Evidence pattern under adequate, replicated, fairly controlled tests | Research decision to consider |
|---|---|
| EXP-1.1: explicit persistent state shows no meaningful gain against strong implicit-state baselines | Reduce investment in this explicit representation; investigate implicit or hybrid alternatives |
| EXP-1.2: arbitration adds no benefit at matched information and compute | Reconsider the proposed cognition–perception arbitration mechanism, not joint grounding in general |
| EXP-1.3: support/weaken/unresolved criteria cannot be stated in advance | Pause confirmatory claims until an evidence protocol is defined; exploratory work may continue |
| EXP-2.1: separating state updates and experience consolidation shows no net benefit | Reassess the tested separation mechanism, while preserving safety and validation requirements |
| EXP-2.2: Workflow Composition does not outperform strong matched planners | Reassess its status as a distinct incremental contribution |
| EXP-2.3: gains are explained by object-state information alone | Reassess object-centric reasoning organization as an independent architectural claim |
| EXP-3.4: experience transfer works only for near-duplicate tasks | Narrow claims about cross-task reuse and redirect effort to transfer boundaries |
| EXP-3.5: improvements cannot be separated from additional data or compute | Withhold claims of incremental cognitive improvement; redesign the comparison |
| EXP-3.6: system benefits are outweighed by integration and deployment costs | Reassess the deployment case and scope of integrated ULA-RIS |

These are **candidate predeclared decision triggers**, not universal stopping thresholds. Each study must define minimum meaningful effects, uncertainty, replication, safety constraints, and a review decision (continue, revise, narrow, pause, or stop) **before** confirmatory evaluation. A single negative result does not establish universal impossibility.

A successful intervention **does not prove H-R**. An unsuccessful implementation **does not disprove H-R**. Neither positive nor negative findings generalize beyond tested conditions without replication.

Safety-related failures, human interventions, and the costs of obtaining performance are part of the result, not optional footnotes. Exploratory studies may be useful, but must be labeled separately from confirmatory tests.

## 8. Research status and next decisions

**Status:** Proposed experimental framework, **not yet empirically validated**. Specific protocols, benchmark choices, sample sizes, effect thresholds, and implementation details remain open.

**Suggested first decision:** Run a focused Q1 study on cross-time physical-world changes, with matched history and a strong learned implicit-state baseline. If no meaningful incremental benefit remains after fair controls, revisit the representation, intervention, or scope before scaling the full architecture. This does not automatically refute H-R; it challenges the tested explicit-state intervention under the evaluated conditions. In parallel, establish Q11 evidence criteria and use Q6's update/consolidation separation as a control in every study.

The purpose is not to prove Open ULA correct. It is to discover **which functions, under which conditions, change which system outcomes—and at what cost**.
