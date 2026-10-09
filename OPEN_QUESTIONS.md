# Open Research Questions — Open ULA v0.1

**Status:** Research questions and provisional hypotheses · Not yet validated  
**Scope:** Cognition-Grounded Physical Intelligence / ULA Robot Intelligence System (ULA-RIS)

This document identifies unresolved questions that could support, limit, or challenge the Open ULA hypotheses. It is **not** an implementation specification or a claim that an explicit Cognitive Foundation is necessary or superior. Terms follow [GLOSSARY.md](GLOSSARY.md); causal and intervention claims are defined in [HYPOTHESIS.md](HYPOTHESIS.md). Functional responsibilities are described in [ARCHITECTURE.md](ARCHITECTURE.md); detailed protocols belong in [EXPERIMENTS.md](EXPERIMENTS.md).

## How to read each question

Each question uses six fields:

- **Problem:** What is unresolved?
- **Constraints:** What must a credible solution respect?
- **Acceptable answer:** What evidence or functional behavior would count as an answer, including alternatives to ULA-RIS?
- **Evaluation:** How could the question be tested?
- **Current hypothesis (provisional):** A research direction, **not** a predetermined answer.
- **Failure modes:** What could invalidate, limit, or confound the result?

The questions are grouped by research responsibility rather than implementation module. A positive result for one question does not establish the Root-cause Hypothesis (H-R); evidence for the Intervention Hypothesis (H-I) requires controlled comparison.

## 1. Cognitive Foundation: representation, persistence, and retrieval

### Q1. What information must persist across time to improve action?

- **Problem:** Which task-relevant world, situation, self, and experience information benefits future decisions beyond current observations or matched history?
- **Constraints:** Bounded storage and compute; uncertain, incomplete, and changing observations; no requirement for exhaustive 3D reconstruction or continuous tracking of every object.
- **Acceptable answer:** A measurable criterion for retaining, expiring, or retrieving information that improves decisions relative to strong alternatives, including implicit state and history-based systems.
- **Evaluation:** Compare maintained-state access with (a) equal-length history without explicit maintained state, (b) equal information organized differently, and (c) equal-length history with learned implicit state (e.g., recurrent memory, transformer memory, or learned latent state); vary delay, occlusion, and environmental change. Match information access, training data, capacity, and compute where feasible, and disclose unmatched factors.
- **Current hypothesis (provisional):** Selective, action-relevant persistence may reduce repeated reacquisition and prevent errors caused by stale or missing state.
- **Failure modes:** Memory leakage, larger effective context, hidden additional observations, stale-state errors, retrieval overhead, no gain over matched history, or an apparent advantage over no-memory baselines that disappears against strong learned implicit-state baselines.

### Q2. How should APWM maintain physical-world state without over-modeling?

- **Problem:** What representation and update behavior are sufficient for objects, their states, spatial relationships **between objects**, and changes over time?
- **Constraints:** APWM means **AI Physical World Model**. It supports situation reasoning, planning, and action; it is not itself navigation, task planning, or manipulation. Spatial relationships are physical, not interpersonal or social relationships.
- **Acceptable answer:** A persistent physical-world component that preserves useful state through partial observation, records uncertainty and provenance, and updates when warranted by evidence; an alternative representation may also be acceptable.
- **Evaluation:** Test cross-time state accuracy, occlusion stability, change detection, downstream decision quality, and state maintenance cost against matched baselines.
- **Current hypothesis (provisional):** Spatially grounded, selective state maintenance may be more economical than exhaustive reconstruction for many action decisions.
- **Failure modes:** Hallucinated persistence, treating occlusion as disappearance, erroneous object identity, unbounded update cost, or accurate maps without downstream task benefit.

### Q3. How do World Awareness, Situation Awareness, and Self Awareness interact?

- **Problem:** How can persistent physical state, evolving activities and intentions, and the robot's own capabilities and limitations inform the same decision without collapsing into one undifferentiated state?
- **Constraints:** World Awareness and Situation Awareness are complementary temporal views of the same physical reality. Knowledge & Experience is cross-cutting; these responsibilities need not be separate databases.
- **Acceptable answer:** A functional separation that permits consistent decisions and attribution of information to the appropriate responsibility, or evidence that another decomposition performs better.
- **Evaluation:** Probe tasks where physical configuration is unchanged but situation or robot capability changes; compare decisions and attribution errors.
- **Current hypothesis (provisional):** Distinguishable responsibilities with explicit interfaces may reduce context errors while permitting shared representations.
- **Failure modes:** Duplicated or inconsistent state, missed dependencies, excessive synchronization cost, or unnecessary separation.

## 2. Cognition–Perception interface

### Q4. How should maintained cognition and current multimodal perception jointly ground decisions?

- **Problem:** How should reasoning use both prior maintained state and new observations, especially when they disagree?
- **Constraints:** Support **relevance retrieval, temporal alignment, conflict detection, uncertainty handling, and grounded composition**. Neither source is automatically authoritative; different modalities may update at different rates.
- **Acceptable answer:** A testable fusion or arbitration behavior when maintained cognition and current perception disagree, with explicit criteria for recency, provenance, confidence, and task relevance; it should be evaluated against strong perception-only, history-based, and implicit-state alternatives.
- **Evaluation:** Introduce controlled changes, delayed observations, occlusion, and contradictory evidence; measure task decisions, calibration, intervention, and resource overhead.
- **Current hypothesis (provisional):** Explicitly handling temporal relevance and disagreement may improve decisions compared with unqualified use of either source.
- **Failure modes:** Confirmation bias toward stored state, overreaction to noisy perception, hidden information advantages, added latency, or no incremental value.

### Q5. When should the system observe again, ask, or act?

- **Problem:** What level of uncertainty warrants further sensing, clarification, conservative action, or stopping?
- **Constraints:** Safety and embodiment limits; action cost and time; confidence estimates may be imperfect; no guarantee of perfect observation.
- **Acceptable answer:** A decision policy with calibrated trade-offs among task success, risk, intervention, and latency, not necessarily an explicit symbolic policy.
- **Evaluation:** Compare alternative uncertainty thresholds and information-gathering strategies under matched task conditions and safety constraints.
- **Current hypothesis (provisional):** Action-relevant uncertainty management may reduce avoidable failures and unnecessary perception cycles.
- **Failure modes:** Excessive hesitation, unsafe overconfidence, costly repeated observation, or apparent gains caused by more information rather than better cognition.

## 3. Feedback, experience, and improvement

### Q6. What can be updated immediately, and what requires validation?

- **Problem:** How can execution feedback correct maintained world state without allowing a single outcome to contaminate reusable Knowledge & Experience?
- **Constraints:** **State update is not experience consolidation.** Observed object changes may revise maintained world state; generalized lessons require evaluation, validation, and controlled consolidation. The latency boundary between “immediate” and “validated” updates must be explicitly defined for the tested system rather than assumed.
- **Acceptable answer:** Explicit behavioral criteria distinguishing immediate state correction and recovery from promotion of reusable experience, with safeguards against erroneous promotion.
- **Evaluation:** Inject incorrect observations, one-off successes and failures, and repeated outcomes; test recovery, false lesson promotion, and later-task regressions.
- **Current hypothesis (provisional):** Separating the two feedback paths may reduce persistent error propagation without slowing necessary world-state updates.
- **Failure modes:** Premature consolidation, frozen stale state, validation bottlenecks, or costly safeguards without measurable benefit.

### Q7. When is experience reusable, and across which contexts?

- **Problem:** Which evaluated outcomes can improve future decisions across objects, tasks, environments, or embodiments?
- **Constraints:** Experience must retain relevant context, constraints, uncertainty, and applicability limits; improvement is not assumed after every interaction.
- **Acceptable answer:** A validated transfer criterion that predicts when experience helps, has no effect, or should not be reused.
- **Evaluation:** Compare recurrence of evaluated failure modes and task performance on related and unrelated held-out conditions; check negative transfer and leakage.
- **Current hypothesis (provisional):** Context-conditioned, validated experience reuse may reduce repeated human correction and repeated failures.
- **Failure modes:** Overgeneralization, memorization of test tasks, hidden retraining advantages, catastrophic forgetting, or negligible net benefit.

### Q8. What constitutes measurable Cognitive & Capability Improvement?

- **Problem:** How can a system distinguish genuine, sustained improvement from task memorization, added resources, or favorable evaluation conditions?
- **Constraints:** Controlled updates and rollback; safety evaluation; comparable hardware and action capabilities; explicit accounting of data, computation, and human effort.
- **Acceptable answer:** Repeated, reproducible improvements on held-out conditions without unacceptable regressions or unreported costs.
- **Evaluation:** Longitudinal before/after and matched-control tests, including regression suites, failure recurrence, intervention minutes, and adaptation cost.
- **Current hypothesis (provisional):** Validated consolidation may enable improvement across interactions, but only in identifiable task families and conditions.
- **Failure modes:** Benchmark contamination, drift, unsafe updates, regression elsewhere, or benefits outweighed by consolidation cost.

## 4. Planning, physical grounding, and evaluation

### Q9. When does Workflow Composition add value beyond strong planners?

- **Problem:** Does goal-conditioned composition of task workflows and semantic actions improve novel task combinations without requiring predefined physical trajectories for every situation?
- **Constraints:** Workflow Composition belongs within Situation Reasoning & Planning. It does not replace low-level control, and comparison planners must receive matched information and appropriate compute budgets.
- **Acceptable answer:** Evidence of incremental value—or evidence that fixed workflows, learned end-to-end planners, or strong LLM-based planners achieve equivalent or better results.
- **Evaluation:** Compare candidate baselines: (a) fixed workflow libraries, (b) capacity-matched learned planners, and (c) information- and compute-matched LLM-based planners; report which are used and why. Specify whether the ablation disables composition itself, goal-conditioned composition, or situation-conditioned composition, and keep other available capabilities comparable.
- **Current hypothesis (provisional):** Composition may improve transfer to unseen combinations of familiar elements.
- **Failure modes:** Weak baselines, hidden extra planning time, brittle decomposition, infeasible plans, or no advantage over learned planning.

### Q10. What incremental value does object-centric Manipulation Intelligence provide?

- **Problem:** When does grounding semantic actions in the operated object's current state, affordances, physical properties, contact conditions, and observed outcomes improve execution?
- **Constraints:** The operated object remains the center of manipulation reasoning; robot embodiment and surrounding space are necessary constraints, not competing centers. Do not assume fixed trajectories can cover every physical situation.
- **Acceptable answer:** Measurable gains in first-attempt success, recovery, safe contact, adaptation, or intervention cost over strong matched execution approaches. An acceptable answer must distinguish gains from access to object-state information from gains attributable to organizing manipulation reasoning around the object.
- **Evaluation:** Vary object pose, properties, contact, and task conditions while matching robot hardware, sensing, and control; measure execution errors separately from planning errors. Where feasible, compare object-centric and alternative reasoning organizations with the same object-state information and comparable compute.
- **Current hypothesis (provisional):** Object-centric grounding may improve adaptation when interaction conditions differ from training or prior examples.
- **Failure modes:** Control or sensor bottlenecks, object-state estimation errors, slower execution, unsafe contact, or gains attributable to extra sensing.

### Q11. How can experiments distinguish the Root-cause Hypothesis from the Intervention Hypothesis?

- **Problem:** A successful architecture ablation may show useful intervention without establishing that missing Cognitive Foundation was the principal cause of earlier failures.
- **Constraints:** H-R and H-I require distinct evidence; include competing explanations such as data scale, model capacity, perception, planning, compute, and physical execution.
- **Acceptable answer:** A research design with independent root-cause diagnostics and matched intervention tests, explicit alternative explanations, and limits on causal interpretation. Before running experiments, predeclare which patterns of results would weaken H-R, weaken H-I, or leave either or both unresolved.
- **Evaluation:** Combine controlled perturbations, failure attribution, alternative mechanisms, strong baselines, replication, and predeclared analysis where feasible.
- **Current hypothesis (provisional):** Convergent diagnostic evidence and controlled interventions may clarify where persistent cognition contributes, without proving it is universally necessary.
- **Failure modes:** Correlation treated as causation, component naming treated as evidence, unbalanced baselines, or conclusions beyond tested conditions.

### Q12. What makes gains meaningful at system and deployment level?

- **Problem:** How should Task Success, Generalization, and Deployment Efficiency be jointly evaluated rather than optimized in isolation?
- **Constraints:** **Compare Deployment Efficiency at comparable Task Success levels**; report performance–cost trade-offs, and distinguish intelligence-related failures from embodiment and hardware failures.
- **Acceptable answer:** Reproducible improvements in defined task families with transparent accounting for training data, adaptation, compute, engineering effort, human intervention, and failure modes.
- **Evaluation:** Use held-out tasks and environments, matched hardware and capability, resource budgets, failure taxonomy, and repeated trials; report positive and negative results.
- **Current hypothesis (provisional):** The value of maintained cognition, if any, will depend on task structure, environmental change, and deployment constraints rather than appear uniformly.
- **Failure modes:** Success on narrow demos, inflated generalization claims, hidden deployment labor, added cognitive overhead, or improvements below practical significance.

## 5. Cross-cutting research discipline

1. **Alternatives remain valid candidates.** An implicit-state or perception-to-action system may satisfy the same functional requirements without an explicit Cognitive Foundation.
2. **No predetermined winner.** An acceptable answer may reject a proposed ULA-RIS mechanism or reveal that it helps only under specific conditions.
3. **Functional concepts are not implementation prescriptions.** This document does not publish or require particular state schemas, storage formats, algorithms, model weights, datasets, training recipes, or hardware platforms.
4. **Safety and failure costs matter.** Report harmful regressions, unsafe actions, and intervention burden alongside success metrics.
5. **Evidence is conditional.** Neither a positive nor a negative result should be generalized beyond tested implementations, tasks, and budgets without replication.
6. **Maintain the three outcomes.** **Task Success · Generalization · Deployment Efficiency** remain the top-level evaluation dimensions; submetrics are diagnostic instruments, not replacements.

## 6. Research status and participation

**Open ULA v0.1 is a hypothesis and conceptual architecture, not a validated robot intelligence system.** These questions are intended to invite falsifiable proposals, counterexamples, stronger baselines, and reproducible evaluations.

Contributions are most useful when they specify: the question addressed, the proposed mechanism or alternative, the controlled comparison, measurable outcomes, likely confounders, and conditions under which the proposal would fail.

See [EXPERIMENTS.md](EXPERIMENTS.md) for the evaluation framework and [HYPOTHESIS.md](HYPOTHESIS.md) for interpretation standards.
