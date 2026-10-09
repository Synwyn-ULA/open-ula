# Research Hypotheses — Open ULA v0.1

**Cognition-Grounded Physical Intelligence | ULA Robot Intelligence System (ULA-RIS)**

> **Research status:** Proposed hypotheses and evaluation framework. No performance improvement or causal explanation is claimed to have been validated.

This document distinguishes a **root-cause hypothesis** about limitations in physical-world robotics from an **intervention hypothesis** about the value of an explicit Cognitive Foundation. These propositions require different evidence. Terms follow [GLOSSARY.md](GLOSSARY.md); the system proposal is outlined in [ARCHITECTURE.md](ARCHITECTURE.md).

## 1. Problem and research question

Robots can execute increasingly sophisticated actions, yet useful task completion in unfamiliar and changing physical environments remains difficult. Perception-to-action approaches, including systems that use history, memory, and reasoning, have advanced substantially. Nevertheless, open-world variation in objects, states, environments, task compositions, and unexpected events creates a large space of conditions that is costly to cover through data collection, training, and engineering alone.

Open ULA evaluates three system outcomes:

- **Task Success:** Can a robot complete intended tasks under specified conditions, including recovery when appropriate?
- **Generalization:** Can task capabilities transfer to unseen objects, states, environments, and task combinations?
- **Deployment Efficiency:** What data, training, adaptation, engineering, computation, and human-support resources are needed to achieve and sustain specified performance?

**Central research question:** Can an explicit, persistent Cognitive Foundation—combined with current multimodal perception—improve Task Success, Generalization, and Deployment Efficiency in the physical world?

## 2. Root-cause hypothesis (H-R)

> A significant part of limitations in Task Success, Generalization, and Deployment Efficiency may stem from the lack of a sufficiently **persistent, compositional, and action-grounded Cognitive Foundation**, encompassing **World Awareness, Situation Awareness, Self Awareness**, and reusable **Knowledge & Experience**.

This is a proposed **contributing cause**, not a claim that one missing component explains all failures.

### 2.1 Proposed mechanism

The hypothesis suggests that, in some settings, performance and adaptation costs increase when systems cannot adequately:

1. **Maintain relevant state across time:** preserve and revise knowledge about objects, their states, spatial relationships, and changes rather than reconstructing all relevant context for each decision. **Diagnose by** measuring repeated reacquisition or reconstruction of task-relevant state, and testing recall or update after delays, occlusions, or changes while controlling for observation quality.
2. **Compose understanding across situations and goals:** reuse maintained world, situation, self, and experience information when task conditions or action sequences change. **Diagnose by** testing unseen compositions of previously encountered elements and distinguishing composition failures from failures to recognize or execute those elements.
3. **Ground decisions in physical consequences and constraints:** connect maintained understanding to feasibility, task planning, object-centric interaction, and observed state transitions. **Diagnose by** testing whether failures track neglected feasibility, contact, or other physical constraints after accounting for perception and low-level control quality.
4. **Retain validated experience:** use evaluated outcomes to improve subsequent decisions without treating every observation or failure as a generalizable lesson. **Diagnose by** measuring recurrence of failure modes addressed by previously evaluated experience and whether validated lessons transfer to related tasks without inappropriate overgeneralization.

These are proposed mechanisms for investigation, not evidence that existing systems universally lack them.

### 2.2 Diagnostic predictions

If H-R is materially relevant to a class of tasks, diagnostic studies may find that:

- Failure rates or repeated adaptation effort increase when previously observed, task-relevant state must be recalled or updated across time.
- Errors cluster around stale or missing object states, changed spatial relationships, unrecognized task context, or unavailable reusable experience, after accounting for perception and execution quality.
- Better maintained, task-relevant state reduces repeated information acquisition or unnecessary replanning in some matched conditions.
- Gains are strongest where persistence, compositionality, or action grounding is genuinely required, rather than in fully observable, repetitive tasks.

These predictions are **conditional and non-exclusive**: other mechanisms can generate similar patterns. Observed correlations or a successful intervention alone do not establish H-R.

## 3. Intervention hypothesis (H-I)

> If a sufficiently persistent, compositional, and action-grounded **Cognitive Foundation** is explicitly maintained and jointly used with **current multimodal perception**, **Task Success, Generalization, and Deployment Efficiency** should improve under otherwise comparable conditions.

The proposed intervention is the **functional availability and use** of maintained, action-relevant cognition, not a requirement for a particular database, symbolic formalism, neural architecture, or hardware platform.

### 3.1 What the intervention changes

ULA-RIS proposes to connect:

- A **Cognitive Foundation** comprising World Awareness, Situation Awareness, Self Awareness, and cross-cutting Knowledge & Experience;
- **Current Multimodal Perception**, which supplies observations, detects changes, and helps resolve uncertainty;
- **Cognitive Task Understanding** and **Situation Reasoning & Planning**, including Workflow Composition;
- **Object-Centric Action Execution**, supported by Manipulation Intelligence;
- **Feedback**, with immediate state update/correction/recovery distinguished from evaluated experience validation and consolidation.

**APWM — AI Physical World Model** is a proposed mechanism for the persistent physical-world component of World Awareness. It does not itself perform navigation, task planning, or manipulation. The four core technologies and their boundaries are defined in [GLOSSARY.md](GLOSSARY.md).

### 3.2 Intervention predictions

Relative to a carefully matched comparison system, a useful intervention should demonstrate one or more of the following **without unacceptable regressions elsewhere**:

- Higher Task Success on tasks that require remembering or updating relevant physical-world state.
- Better Generalization to held-out objects, states, layouts, environments, task compositions, or changes over time.
- Lower deployment resources to achieve **comparable Task Success**, including reduced per-environment adaptation, repeated data acquisition, retraining, engineering work, or human intervention.
- Improved recovery or reduced recurrence of previously evaluated failure modes.

These predictions are **separable, conditional subclaims**, not an all-or-nothing test of H-I:

| Observation in matched tests | Interpretation for the intervention |
|---|---|
| Improved Task Success where relevant state must persist across time | Supports the persistence-related subclaim under tested conditions |
| Improved performance on unseen compositions of known elements | Supports the compositionality-related subclaim under tested conditions |
| Lower data, adaptation, engineering, compute, or human-support cost at comparable Task Success | Supports the deployment-efficiency subclaim, subject to total overhead |
| Reduced recurrence of evaluated failure modes, without unsafe transfer | Supports the experience-consolidation subclaim under tested conditions |
| Benefits limited to particular tasks, embodiments, or resource budgets | Conditional support only; identify the boundary of applicability |
| No measurable gains, or gains outweighed by added cost or regressions | Does not support the tested intervention under those conditions |

No single positive subclaim establishes H-I across all three outcomes. Report trade-offs and negative effects alongside gains.

The hypothesis is not confirmed merely because a system with more components achieves higher raw performance. Additional model capacity, information, training, or computation must be accounted for.

## 4. Competing explanations and alternatives

The proposed cognitive bottleneck must be tested against credible alternatives:

| Alternative explanation | What to examine |
|---|---|
| Insufficient or unrepresentative training data | Whether better coverage or data quality explains the observed gap |
| Model capacity or training methodology | Whether scaling or optimization closes the gap without an explicit Cognitive Foundation |
| Perception or state-estimation errors | Whether failures arise primarily from missing, noisy, or misinterpreted observations |
| Planning or action-policy limitations | Whether better planning, policies, or action representations explain improvements |
| Manipulation and low-level control limitations | Whether contact, force, motion, and control failures dominate outcomes |
| Embodiment, sensing, and hardware reliability | Whether physical constraints prevent success regardless of cognitive design |
| Extra compute, latency, or engineering effort | Whether apparent benefits reflect additional resources rather than the proposed mechanism |

These explanations are not mutually exclusive. Explicit maintained cognition may complement, overlap with, or be approximated by other architectures, including learned implicit state or memory. Experiments should compare **functional capabilities**, not merely labels such as “cognitive” versus “end-to-end.”

## 5. Evidence standards and experimental logic

### 5.1 Root-cause diagnosis

H-R requires evidence that specific deficiencies in persistent, compositional, action-grounded cognition **contribute causally** to relevant failures or costs. Useful methods include:

- Failure attribution with traceable task context, observations, state estimates, action choices, and physical outcomes;
- Controlled perturbations of state persistence, state freshness, composition, or action grounding;
- Tests of competing explanations and relevant interactions among causes;
- Replication across task families and environments where the proposed mechanisms should matter.

Causal attribution for H-R requires more than correlation between state availability and success. It requires controlled perturbation of the proposed mechanism or convergent evidence from multiple independent diagnostic methods that jointly weaken plausible alternatives.

A diagnostic study should identify **where and why** a cognitive deficiency matters, not merely report a system-level score difference.

### 5.2 Intervention evaluation

H-I requires controlled comparisons or ablations of the proposed cognitive mechanisms. Wherever feasible, comparisons should match or report:

- Robot hardware, sensing, action space, actuation and low-level control;
- Task specifications, observations, available history, and environmental conditions;
- Training data, model capacity, training procedures, and access to external information;
- Inference and storage costs, latency, adaptation time, and human assistance;
- Safety constraints and intervention/recovery policies.

Ablations may isolate persistent state, state updating, experience consolidation, or their integration with reasoning and action. Comparisons against strong baselines that already have memory or implicit world-state capabilities are particularly important.

### 5.3 Evaluation principles

1. **Report all three outcomes:** Task Success, Generalization, and Deployment Efficiency, with task-specific submetrics and uncertainty where appropriate.
2. **Compare efficiency at comparable performance:** resource savings are not an efficiency improvement if achieved through an unacceptable loss of Task Success; report performance–cost trade-offs when exact matching is infeasible.
3. **Distinguish intelligence and embodiment:** Task Success is a system outcome; classify intelligence-related and physical execution failures where possible.
4. **Avoid leakage:** specify held-out objects, layouts, environments, temporal changes, and task combinations; prevent test information from entering adaptation or experience stores improperly.
5. **Separate immediate state update from long-term learning:** current-state correction is not validated experience consolidation; a single attempt is not automatically a reusable lesson.
6. **Report negative results and overhead:** added latency, compute, memory, integration complexity, and new failure modes count against the intervention.
7. **Do not infer causality from naming:** an “explicit” component is not inherently superior to an implicit learned representation; its contribution must be measured.

Detailed experimental protocols, datasets, task definitions, and statistical decision criteria belong in [EXPERIMENTS.md](EXPERIMENTS.md).

## 6. How results should be interpreted

| Finding | Supported interpretation | Not justified by that finding alone |
|---|---|---|
| Cognitive intervention improves matched outcomes | Evidence for H-I under tested conditions | Proof that H-R is the unique or primary root cause |
| Intervention shows no measurable gain | H-I is not supported for that implementation and setting | Proof that persistent cognition cannot help or that H-R is false |
| Failures are causally linked to deficient maintained state | Evidence strengthening H-R for the tested task class | Proof that the proposed ULA-RIS implementation is optimal |
| Alternative approaches match or outperform the intervention | The proposed explicit mechanism may offer no advantage under tested conditions | Proof that persistent state or cognition is unnecessary in all systems |
| Benefits appear only for particular tasks or conditions | A bounded, conditional result | A universal claim of generalization or deployment advantage |

A negative result under one implementation, task family, or resource budget does not generalize to all implementations, task families, or budgets. Likewise, a positive result does not generalize beyond tested conditions without replication.

Evidence can support, weaken, constrain, or motivate revision of either hypothesis independently. Neither hypothesis is protected from rejection by architectural complexity or by redefining success after observing results.

## 7. What We Are NOT Claiming

Open ULA does **not** claim that:

1. **VLA, end-to-end, or perception-to-action systems lack cognition, memory, or reasoning.** Many such systems incorporate history, learned representations, and other mechanisms for context-sensitive decisions.
2. **Data scaling is ineffective.** Better data, model capacity, and training methods remain important competing or complementary explanations. An explicit Cognitive Foundation is not proposed as a replacement for data scaling; the two may be complementary.
3. **Trajectory planning, motion planning, or low-level control are unnecessary.** Workflow Composition and semantic actions do not eliminate the need for physically valid execution, feedback, or safety constraints.
4. **ULA-RIS v0.1 is the only correct architecture, or an empirically validated solution.** It is a falsifiable research proposal; its components, interfaces, and mechanisms may be revised or rejected.

Nor does this document claim unrestricted online self-improvement, guaranteed learning from every interaction, or independence from physical embodiment.

## 8. Research status and next steps

**v0.1 status:** Conceptual hypotheses and proposed evidence standards; **not yet validated**.

Next steps are to define discriminating task families, strong baselines, failure taxonomies, ablations, matched resource budgets, and predeclared success/failure criteria. The experimental program should prioritize tests that can meaningfully distinguish H-R from competing explanations and H-I from improvements caused by extra resources.

**Publish thinking, not promises. Let evidence decide.**

---

**Related documents:** [README.md](README.md) · [GLOSSARY.md](GLOSSARY.md) · [ARCHITECTURE.md](ARCHITECTURE.md) · [OPEN_QUESTIONS.md](OPEN_QUESTIONS.md) · [EXPERIMENTS.md](EXPERIMENTS.md)
