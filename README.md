# AI Industrial Decision Support Sample

Production-oriented multi-agent LLM system for industrial bottleneck analysis.

This repository presents a public work sample based on a master's thesis project in a large automotive manufacturing environment, focusing on AI-driven decision support for complex operational workflows.

It is structured so it can be shared if a company requests a project sample. It does not contain proprietary code or internal data from the original thesis environment. Instead, it packages the shareable engineering artifacts: the work-sample PDF and a markdown system overview that explains the architecture and engineering decisions in more detail.

## Repository Purpose

The original project was developed as part of a master's thesis in a large automotive manufacturing environment. The real system focused on AI-supported bottleneck detection and recommendations for industrial processes. Because the original environment involved confidential data, governed systems, and internal implementation details, this repository is intentionally limited to public-safe material.

The goal of this repository is to show:

- how the problem was framed from an engineering perspective
- how the LLM-based system was structured end to end
- how retrieval, orchestration, and structured data access were combined
- how production concerns such as reliability, observability, CI/CD, testing, and cost were handled

## Included Artifacts

- [`docs/work-sample.pdf`](docs/work-sample.pdf): polished 3-page work sample for company review
- [`docs/system-overview.md`](docs/system-overview.md): expanded technical summary for GitHub readers
- [`PUBLIC_SCOPE.md`](PUBLIC_SCOPE.md): what is intentionally shareable and what is excluded

## Project Summary

The underlying system was an AI-based decision-support layer for bottleneck analysis in manufacturing operations. The challenge was not simply querying data. The harder problem was to connect structured operational signals, supporting context, and multi-step reasoning in a way that remained traceable and safe for business use.

At a high level, the design combined:

- curated SQL-accessible analytical views
- embeddings and vector search for contextual retrieval
- LLM-driven reasoning and response generation
- agent-style orchestration for multi-step workflows
- API boundaries for integration into user-facing applications

## Impact

- Reduced analysis time by up to 60% through automated root-cause detection and AI-driven recommendations
- Standardized investigation workflows across heterogeneous data sources
- Improved traceability and consistency of decision support in industrial analysis

## Engineering Focus

This repository highlights the engineering decisions behind building a production-oriented AI system:

- system decomposition and modular architecture
- retrieval and grounding strategies (RAG)
- structured query generation and constraints
- evaluation, testing, and failure handling
- CI/CD and deployment considerations
- cost, latency, and reliability trade-offs

## Recommended Use

If a company asks for sample work, this folder can be:

- shared as-is
- copied into a standalone repository
- extended with a private walkthrough, architecture discussion, or interview deep dive

## Notes

- No confidential data, plant names, internal screenshots, or proprietary code are included.
- The repository is intentionally documentation-heavy because the original implementation cannot be published safely.
- If needed, this sample can be adapted into role-specific variants such as `AI Engineer`, `LLM Engineer`, or `Applied AI Engineer`.
