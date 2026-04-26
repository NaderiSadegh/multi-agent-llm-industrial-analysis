# AI Industrial Decision Support Sample

Public-safe work sample for AI Engineering and Applied AI roles.

This directory is structured so it can be copied into its own GitHub repository if a company requests a project sample. It does not contain proprietary code or internal data from the original thesis environment. Instead, it packages the shareable engineering artifacts: the work-sample PDF, the source used to generate it, and a markdown system overview that explains the architecture and engineering decisions in more detail.

## Repository Purpose

The original project was developed as part of a master's thesis in a large automotive manufacturing environment. The real system focused on AI-supported bottleneck detection and recommendations for industrial processes. Because the original environment involved confidential data, governed systems, and internal implementation details, this repository is intentionally limited to public-safe material.

The goal of this repository is to show:

- how the problem was framed from an engineering perspective
- how the LLM-based system was structured end to end
- how retrieval, orchestration, and structured data access were combined
- how production concerns such as reliability, observability, CI/CD, testing, and cost were handled

## Included Artifacts

- [`docs/work-sample.pdf`](docs/work-sample.pdf): polished 3-page work sample for company review
- [`docs/work-sample-source.tex`](docs/work-sample-source.tex): LaTeX source for the PDF
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

## Why This Works as a GitHub Sample

Most enterprise AI work cannot be published as a complete repository because the valuable parts are tied to private systems, regulated data, and company-specific logic. This sample therefore focuses on the engineering decisions that are still meaningful in a public review:

- system decomposition
- retrieval and grounding strategy
- query-generation constraints
- evaluation logic
- testing and release discipline
- CI/CD and deployment thinking
- production-readiness considerations

That usually gives a hiring team more signal than a toy demo.

## Recommended Use

If a company asks for sample work, this folder can be:

- shared as-is
- copied into a standalone repository
- extended with a private walkthrough, architecture discussion, or interview deep dive

## Notes

- No confidential data, plant names, internal screenshots, or proprietary code are included.
- The repository is intentionally documentation-heavy because the original implementation cannot be published safely.
- If needed, this sample can be adapted into role-specific variants such as `AI Engineer`, `LLM Engineer`, or `Applied AI Engineer`.
