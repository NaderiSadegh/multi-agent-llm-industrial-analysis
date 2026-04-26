# System Overview

## Problem

Industrial bottleneck analysis is difficult even in data-rich environments. Relevant evidence is usually distributed across several sources: KPI views, downtime records, event logs, operational messages, cycle-time signals, and analyst documentation. The operational challenge is not only to retrieve facts, but to connect those facts into a reliable explanation of where throughput is constrained and what should be investigated next.

That makes the problem a poor fit for a single dashboard and also a poor fit for an unconstrained chatbot. A useful system needs structured data access, contextual retrieval, workflow control, and guardrails around output quality.

## High-Level Design

The project was structured as a modular AI application with four main layers:

1. Data layer
   Curated analytical views over structured operational data, exposed with stable semantics and consistent naming.
2. Retrieval layer
   Embeddings and vector search used to retrieve supporting context such as definitions, playbooks, and investigation guidance.
3. LLM layer
   Reasoning, synthesis, and structured query generation for complex user questions.
4. Orchestration layer
   Multi-step workflow control, tool routing, retries, and API-oriented delivery.

This separation was important because each layer had different quality criteria. Data access needed correctness and schema clarity. Retrieval needed relevance. Reasoning needed bounded workflow behavior. Delivery needed reliability and integration readiness.

## Data Engineering Considerations

The project relied on curated views rather than exposing raw operational sources directly. That reduced ambiguity for both users and models.

Key data-engineering considerations included:

- standardized naming and documented semantics
- reusable time-grain logic for comparable analysis windows
- structured interfaces for downstream query generation
- read-only access boundaries
- resilience to empty results, timeouts, or incomplete inputs

This part of the system matters for AI Engineering because LLM behavior is heavily shaped by the quality of the surrounding data contracts.

## Retrieval and Grounding

Retrieval-augmented generation was used to connect the model to relevant context instead of relying on model memory.

The retrieval layer supported:

- semantic lookup of analytical guidance
- mapping user questions to the right investigation context
- grounding answers in retrieved evidence
- reducing hallucination risk in explanation steps

The practical trade-off was that better retrieval quality required work on chunking, metadata, ranking, and scope control. Richer retrieval improved answers, but it also added latency and tuning complexity.

## Structured Query Generation

Some user questions were well suited to structured data access rather than free-form reasoning. For those cases, the system used Text2SQL-style concepts to translate KPI and time-window questions into SQL under constrained conditions.

Important design points were:

- schema-aware prompting
- restricted query scope
- documented column semantics
- explicit error and fallback behavior when a query path was weak

This design treated query generation as an engineering problem, not just a prompting problem.

## Orchestration

The system did not rely on one prompt to do everything at once. It used stepwise orchestration to break down complex analysis tasks into smaller operations such as:

- question interpretation
- retrieval of supporting context
- structured data access
- comparison across time windows or evidence sources
- final synthesis into a readable answer

That orchestration approach improved traceability and made failure modes easier to observe than in a single-prompt setup.

## Evaluation

Evaluation focused on workflow usefulness rather than only language fluency.

Representative dimensions included:

- retrieval relevance
- answer usefulness
- workflow traceability
- handling of ambiguous or incomplete inputs
- stability across prompt and configuration changes

MLflow was used for experiment and configuration tracking so prompt variants, retrieval settings, and workflow versions could be compared in a reproducible way.

## Testing and Validation

For AI Engineering roles, testing matters as much as prompting. In this project context, the important testing surface was broader than traditional unit tests because failures could come from retrieval quality, schema drift, prompt changes, tool routing, or degraded query behavior.

The relevant validation layers included:

- regression-style question sets for representative user scenarios
- checks on retrieval relevance and grounding quality
- validation of structured query behavior under realistic inputs
- workflow-level handling of empty results, timeouts, and ambiguous requests
- comparison of configuration and prompt variants through tracked evaluation runs

This is one of the main differences between an AI system and a small demo application: useful testing has to cover data access, orchestration behavior, and model-driven outputs together.

## Delivery and CI/CD Thinking

The original project cannot be published with its internal delivery setup, but the engineering scope did include the kind of lifecycle concerns that matter for AI Engineering roles.

Those concerns included:

- version-controlled prompts, workflow definitions, and retrieval settings
- repeatable packaging of application and configuration changes
- deployment discipline around API and orchestration updates
- promotion of changes through controlled environments rather than ad-hoc edits
- rollback capability when a prompt, retrieval setting, or workflow change regressed behavior

In practice, AI Engineering work benefits from treating prompt and workflow changes like software changes: tested, versioned, reviewed, and deployed through a controlled pipeline rather than modified directly in production.

## Production Readiness

The system was designed with production-oriented constraints in mind:

- observability through logs of retrieval hits, tool paths, latency, and query outcomes
- CI/CD thinking around controlled rollout of prompt, workflow, and API changes
- cost control through bounded steps and selective model usage
- reliability through fallbacks, retries, and human-readable failure messages
- scalability through modular APIs and reusable data contracts
- safety through read-only access, auditable outputs, and explicit system boundaries

These concerns were part of the design from the start rather than a later packaging step.

## What This Repository Shows

This repository does not claim to be a full public release of the original system. It is a sanitized engineering sample that demonstrates:

- AI system decomposition
- RAG application design
- orchestration of LLM workflows
- integration with structured data systems
- evaluation, testing, and release-oriented thinking
- production-oriented AI engineering judgment
