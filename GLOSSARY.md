# Glossary — Open ULA v0.1

**Canonical terminology for Cognition-Grounded Physical Intelligence and the ULA Robot Intelligence System (ULA-RIS).**

This document defines the concepts used across Open ULA. Definitions describe a **proposed research architecture**, not validated capabilities or mandatory implementation choices. Related documents should preserve these meanings even when using shorter descriptions.

## 1. Research positioning and architecture

### Open ULA
The public research initiative investigating whether an explicit, persistent Cognitive Foundation, used together with current multimodal perception, can improve **Task Success, Generalization, and Deployment Efficiency** in physical-world robotics. *Open ULA is a project name, not an acronym expanded as “Unified Learning Architecture.”*

### Cognition-Grounded Physical Intelligence
A research direction in which maintained cognition and current multimodal perception jointly ground situation reasoning, planning, and physical action. **Not a claim** that existing perception-to-action systems lack internal representations, memory, or reasoning.

### ULA-RIS — ULA Robot Intelligence System
The proposed robot intelligence architecture connecting a Cognitive Foundation, current multimodal perception, task understanding, situation reasoning and planning, object-centric action execution, and feedback-driven improvement. **Not** a foundation model, a finished robot product, or a claim of validated performance.

### Perception-to-Action
A family of approaches that learns or implements mappings from sensory observations (often with history and other context) to actions. It is a major research paradigm and a **comparison point**, not a claim that all such systems are memoryless or incapable of reasoning.

## 2. Cognitive Foundation and awareness

### Cognition
The robot's accumulated or maintained understanding, together with the processes that acquire, transform, store, retrieve, update, and use that understanding. **Not synonymous with** the reasoning, planning, or action-execution modules alone.

### Cognitive Foundation
The maintained, action-relevant cognitive basis supporting task understanding and decisions. It encompasses **World Awareness, Situation Awareness, and Self Awareness**, with **Knowledge & Experience** as a cross-cutting resource. These are functional responsibilities, **not** a requirement for four independent models or databases. In ULA-RIS, Cognitive Foundation refers to the maintained, action-relevant subset of cognition that supports task understanding and decisions. It is not the whole of cognition, and it is not equivalent to a reasoning or planning module.

### World Awareness
Persistent understanding of the physical environment: spaces, physical entities and objects, their relevant states and properties, **spatial relationships**, and changes over time. It is more than a static navigation or semantic map. Its persistent physical-world representation is explored through **APWM**. World Awareness and Situation Awareness are complementary temporal views of the same physical reality. APWM is one proposed mechanism for maintaining the persistent physical-world component of World Awareness.

### Situation Awareness
Understanding of temporally active events, activities, interactions, and task-relevant conditions in the current situation. World Awareness and Situation Awareness are complementary perspectives on the **same physical reality**, not separate worlds.

### Self Awareness
Maintained understanding of the robot's embodiment, available capabilities, operating constraints, and limitations. **Not equivalent to** raw real-time proprioception, although proprioception can update it.

### Knowledge & Experience
Reusable knowledge, priors, and appropriately validated experience that support World, Situation, and Self Awareness and subsequent decisions. This is a **cross-cutting cognitive resource**, not necessarily a fourth independent world-state store. Raw event logs are not automatically validated experience.

### Current Multimodal Perception
Observations and estimates from available sensory modalities, with temporal context and uncertainty, used to ground and update decisions. It complements maintained cognition; neither is assumed to replace the other. **Not equivalent to** a complete persistent world model.

## 3. Four core technologies

### APWM — AI Physical World Model
**Canonical definition:**

> Represents and maintains a persistent understanding of the physical world, including objects, their states, spatial relationships between objects, and changes over time, to support situation reasoning, planning, and action.

**Scope and boundaries:**
- *Spatial relationships* refers to physical spatial relationships between objects (for example, *on*, *inside*, *beside*, or *left of*), **not interpersonal or social relationships**.
- People may be represented as physical entities for relevant spatial reasoning; human activities and interactions are addressed through Situation Awareness and related cognitive responsibilities.
- The model may represent uncertainty and update its understanding as observations change, including when objects are occluded; these are research properties, not alternative expansions of **APWM**.
- APWM does **not** itself perform navigation, task planning, or manipulation, and does not require exhaustive 3D reconstruction or continuous tracking of every object.

### Experience Intelligence
The processes that evaluate outcomes, corrections, and interactions and turn suitable findings into **validated, reusable experience** for future decisions and capability improvement. **Not** automatic promotion of every observation, failure, or local success into long-term knowledge.

### Workflow Composition
Goal- and situation-conditioned organization of task steps and **semantic actions**, using cognition, perception, and available robot capabilities. It is part of task reasoning and planning; **not** a separate compulsory serial stage after planning or a library of fixed physical trajectories.

### Manipulation Intelligence
**Object-centric** grounding and execution of intended semantic actions in physical interaction. It considers the current target object's state, relevant physical/material properties, affordances, relative geometry, contact and force constraints, embodiment, and observed outcomes. **Not** merely grasp detection or the replay of a predefined trajectory.

## 4. Reasoning, action, and learning

### Cognitive Task Understanding
Interpretation of a goal or instruction using maintained cognition and available context to establish the intended task, constraints, and relevant information needs. **Not** a claim that perception occurs only after task understanding.

### Situation Reasoning & Planning
Reasoning over the goal, Cognitive Foundation, and current perception to interpret the situation, assess feasibility and constraints, and organize action—including Workflow Composition. **Not** a substitute for low-level control or physical execution.

### Semantic Action
A meaningful action type such as *grasp*, *hold*, *release*, *push*, *pull*, *press*, *lift*, or *rotate*, specified by its intent and relevant object/state constraints rather than a fixed trajectory. It must be grounded in current physical conditions for execution.

### Object-Centric Action Execution
Physical execution organized around the **object being operated on**, its actionable state, affordances, relative pose, contact conditions, and observed state transitions. The robot's body and surrounding space remain essential constraints, but do not displace the target object as the center of manipulation reasoning.

### Persistent State for Action
Using maintained physical-world state **together with current observations** to support the next decision or action, rather than relying only on the present observation. **Not** ignoring contradictory or fresher sensory evidence.

### Immediate State Update / Correction / Recovery
Short-horizon processing of new observations and execution feedback to revise current state estimates, correct an ongoing action, or recover from failure. This can happen during a task. **State update is not experience consolidation.**

### Experience Validation & Consolidation
Evaluation of candidate lessons for correctness, safety, relevance, and reusability before incorporating them into longer-term experience or capabilities. A single successful or failed attempt is not automatically a generalizable lesson.

### Cognitive & Capability Improvement
Changes to maintained cognition and/or robot capabilities that follow appropriate evaluation and validation. **Not** an assumption of continuous, unrestricted online self-training or guaranteed improvement after every interaction.

## 5. Hypotheses and evaluation

### Root-cause Hypothesis
The testable proposition that an insufficiently persistent, compositional, and action-grounded **Cognitive Foundation** contributes materially to limitations in task success, generalization, and deployment efficiency. Requires **diagnostic evidence** and examination of competing explanations, not only a successful architecture ablation.

### Intervention Hypothesis
The testable proposition that explicitly maintaining and jointly using such a Cognitive Foundation with current multimodal perception produces measurable benefits under otherwise comparable conditions. Evaluated through **controlled comparisons and ablations**.

**Evidence boundary:** A successful intervention does not by itself establish the proposed root cause; an unsuccessful intervention does not automatically disprove it.

### Task Success
The degree to which the robot completes intended tasks under specified conditions. Operational measures may include **task completion rate**, first-attempt success, successful recovery, manipulation-specific success, and human intervention. It is a **system outcome**, influenced by both intelligence and physical embodiment; not synonymous with hardware reliability.

### Generalization
The extent to which task capabilities transfer to **unseen objects, states, layouts, environments, task compositions, and temporal changes**, without disproportionate task-specific retraining or re-engineering. Must be measured on clearly specified held-out conditions.

### Deployment Efficiency
The data, training, engineering, adaptation, computation, and human-support resources needed to reach and sustain **specified task performance** in deployment. Compare efficiency **at comparable Task Success levels**, reporting relevant performance–cost trade-offs; not merely inference speed or reduced training data in isolation.

### Controlled Comparison / Ablation
An experiment isolating the contribution of a proposed cognitive component or mechanism while matching hardware, observations, action capabilities, and relevant data/model/compute budgets as closely as feasible. Remaining differences and confounders should be reported.

### Embodiment and Physical Execution Constraints
The sensing, actuation, kinematics, control precision, contact dynamics, safety limits, and hardware reliability that affect physical task outcomes. Open ULA studies the **incremental contribution of robot intelligence** while controlling for and reporting these constraints; it does not treat hardware as irrelevant.

## 6. Cross-document consistency rules

1. Always expand **APWM** as **AI Physical World Model**; never *Adaptive* or *Actionable Physical World Model*.
2. Use **Cognitive Foundation** for the architectural concept; do not casually replace it with generic *cognition* when naming the component.
3. Treat **Cognitive Foundation + Current Multimodal Perception** as joint grounding for reasoning and planning, not a strictly sequential pipeline.
4. Treat **Workflow Composition** as part of reasoning and planning, and **Manipulation Intelligence** as object-centric physical grounding.
5. Keep **immediate state updates** distinct from **validated experience consolidation**.
6. Keep **Root-cause** and **Intervention** hypotheses separate, with different evidence standards.
7. Use **Task Success · Generalization · Deployment Efficiency** as the three top-level evaluation dimensions.
8. These definitions specify **research concepts and boundaries**, not a commitment to one implementation, dataset, model, or hardware platform.

For the research thesis, see [README.md](README.md) and [HYPOTHESIS.md](HYPOTHESIS.md). For system responsibilities and experiments, see [ARCHITECTURE.md](ARCHITECTURE.md) and [EXPERIMENTS.md](EXPERIMENTS.md).
