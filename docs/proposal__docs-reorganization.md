# Proposal: Issues-FS__Docs Reorganization

**Document:** proposal__docs-reorganization
**Author:** Librarian Role
**Date:** 2026-02-06
**Status:** Draft -- awaiting review

---

## 1. Analysis of the Current Structure

### Current Directory Layout

```
Issues-FS__Docs/docs/
  development/
    llm-briefs/
      type-safety/
        v3.1.1__for_llms__type_safe__testing_guidance.md
        v3.28.0__for_llms__osbot-utils-safe-primitives.md
        v3.63.4__for_llms__type_safe.md
      v3.63.4__for_llms__python_formatting_guide.md
  issues_fs/
    architecture/
      v0.4.0__issues-fs__architecture-overview.md
    dev-briefs/
      v0.2.14__brief__phases-2-to-5-implementation.md
      v0.2.15__brief__refactor-issues-ui__to-standalone-repo/
        notes.md
        v0.2.15__brief__refactor-issues-ui-to-standalone.md
      v0.2.26__add-git-repo-commit-data/
        v0_2_26__brief-1__git-repo-reader__project-brief.md
      v0.2.32__phase_2__add-mgraph-support__and__issue-pod-architecture/
        v0.2.32__brief-006__gitgraph-issues__phase-2-implementation.md
        v0.2.33__brief-006a__gitgraph-issues__phase-2-backend.md
      v0.2.34__add-type-safe-properties.md/
        draft-brief.md
        v0_2_34__brief-007__gitgraph-issues__type-safe-properties.md
    llm-briefs/
      v0.2.14__briefing__graph-based-issue-tracking.md
      v0.2.25__llm-brief__issues-ui__backend-development-workflow.md
      v0.2.25__llm-brief__issues-ui__frontend-development-workflow.md
      v0.2.32__llm-brief__gitgraph-manual-issues-workflow.md
  to_classify/
    v0.1.0__issues-fs__role-architecture-framework-analysis.md
    v0.1.0__issues-fs__role-based-agent-coordination.md
    v0_4_0__issues-fs__lexicon-architecture-v2.md
    v0_4_0__issues-fs__thinking-in-graphs.md
    already-legacy/
      v0.1.0__issues-fs__lexicon-architecture.md
    6-feb/
      agent-review__component-inventory.md
      agent-review__ecosystem-overview.md
      agent-review__librarian-findings.md
      agent-review__next-steps.md
      v0_4_0__issues-fs__librarian-role-side-capture.md
      v0_4_0__issues-fs__librarian-role.md
      v0_4_0__issues-fs__semantic-graph-code-representation.md
      v0_4_0__issues-fs__semantic-testing-dsl.md
      v0_4_0__issues-fs__semantic-text-architecture.md
      v0_4_0__issues-fs__use-case-pattern.md
      v0_4_0__issues-fs__use-case__github-backup.md
```

### Observations

**What is working well:**
- `development/llm-briefs/type-safety/` is well-organized -- a clear topic with versioned documents.
- `issues_fs/architecture/` exists and contains the architecture overview -- correct placement.
- `issues_fs/dev-briefs/` is well-structured with version-scoped subdirectories for related files.
- `issues_fs/llm-briefs/` contains LLM-focused context documents -- useful category.

**What is problematic:**
- `to_classify/` contains 4 of the most foundational documents in the entire ecosystem: Thinking in Graphs, Lexicon Architecture v2, Role-Based Agent Coordination, and the Role Architecture Framework Analysis. These are not "unclassified" -- they are core architecture documents that belong in `issues_fs/architecture/`.
- `to_classify/6-feb/` is a date-based dump containing 11 documents of vastly different types: architecture specs, agent review findings, side-captures, use case patterns, and exploratory designs. A date-based folder is an anti-pattern for a knowledge system -- it reflects *when* something was created, not *what* it is.
- `already-legacy/` correctly identifies superseded content but has no formal archive structure.
- The `6-feb/` folder name will become meaningless within weeks. It conveys no information about its contents.
- Several foundational documents (Thinking in Graphs, Lexicon v2) are more important than the architecture overview that is already classified, yet they sit in the unclassified pile.

---

## 2. Proposed Folder Structure

```
Issues-FS__Docs/docs/
  foundations/                              # Core philosophy and principles
    v0_4_0__issues-fs__thinking-in-graphs.md

  architecture/                            # System-level architecture documents
    v0.4.0__issues-fs__architecture-overview.md
    v0_4_0__issues-fs__lexicon-architecture-v2.md

  roles/                                   # Role-based agent coordination
    v0.1.0__issues-fs__role-based-agent-coordination.md
    v0.1.0__issues-fs__role-architecture-framework-analysis.md
    v0_4_0__issues-fs__librarian-role.md
    v0_4_0__issues-fs__librarian-role-side-capture.md

  semantic/                                # Semantic text/graph architecture
    v0_4_0__issues-fs__semantic-text-architecture.md
    v0_4_0__issues-fs__semantic-graph-code-representation.md
    v0_4_0__issues-fs__semantic-testing-dsl.md

  use-cases/                               # Use case pattern and instances
    v0_4_0__issues-fs__use-case-pattern.md
    github-backup/
      v0_4_0__issues-fs__use-case__github-backup.md

  reviews/                                 # Agent review outputs and findings
    2026-02-06/
      agent-review__ecosystem-overview.md
      agent-review__component-inventory.md
      agent-review__librarian-findings.md
      agent-review__next-steps.md

  development/                             # Development guides and briefs
    llm-briefs/
      type-safety/
        v3.1.1__for_llms__type_safe__testing_guidance.md
        v3.28.0__for_llms__osbot-utils-safe-primitives.md
        v3.63.4__for_llms__type_safe.md
      v3.63.4__for_llms__python_formatting_guide.md
    dev-briefs/
      v0.2.14__brief__phases-2-to-5-implementation.md
      v0.2.15__brief__refactor-issues-ui__to-standalone-repo/
        notes.md
        v0.2.15__brief__refactor-issues-ui-to-standalone.md
      v0.2.26__add-git-repo-commit-data/
        v0_2_26__brief-1__git-repo-reader__project-brief.md
      v0.2.32__phase_2__add-mgraph-support__and__issue-pod-architecture/
        v0.2.32__brief-006__gitgraph-issues__phase-2-implementation.md
        v0.2.33__brief-006a__gitgraph-issues__phase-2-backend.md
      v0.2.34__add-type-safe-properties.md/
        draft-brief.md
        v0_2_34__brief-007__gitgraph-issues__type-safe-properties.md
    llm-briefs/
      v0.2.14__briefing__graph-based-issue-tracking.md
      v0.2.25__llm-brief__issues-ui__backend-development-workflow.md
      v0.2.25__llm-brief__issues-ui__frontend-development-workflow.md
      v0.2.32__llm-brief__gitgraph-manual-issues-workflow.md

  archive/                                 # Superseded or legacy documents
    v0.1.0__issues-fs__lexicon-architecture.md
```

---

## 3. File-by-File Recommendations

### Files Currently in `to_classify/`

| Current Location | Recommended Location | Classification | Rationale |
|-----------------|---------------------|---------------|-----------|
| `to_classify/v0_4_0__issues-fs__thinking-in-graphs.md` | `foundations/` | **Foundational** | This is the single most important document in the ecosystem. Every other architecture document depends on it. It defines the core philosophy. It should be the first thing anyone reads. |
| `to_classify/v0_4_0__issues-fs__lexicon-architecture-v2.md` | `architecture/` | **Architecture** | Defines the root graph of the ecosystem. A system-level architecture document that describes a core component (the Lexicon). |
| `to_classify/v0.1.0__issues-fs__role-based-agent-coordination.md` | `roles/` | **Architecture (Role-specific)** | Defines the six-role model, coordination protocols, issue types, handoff schemas. The governing document for all role repos. |
| `to_classify/v0.1.0__issues-fs__role-architecture-framework-analysis.md` | `roles/` | **Reference/Analysis** | Supporting analysis that stress-tests the role architecture against five frameworks. Companion to the role coordination doc. |

### Files Currently in `to_classify/6-feb/`

| Current Location | Recommended Location | Classification | Rationale |
|-----------------|---------------------|---------------|-----------|
| `6-feb/v0_4_0__issues-fs__librarian-role.md` | `roles/` | **Architecture (Role-specific)** | The Librarian's full architecture document. Defines the role in depth -- its principles, workflows, graph operations, and integration points. Belongs with other role docs. |
| `6-feb/v0_4_0__issues-fs__librarian-role-side-capture.md` | `roles/` | **Side-capture (Role-specific)** | Raw ideas captured during the Librarian role design. Belongs alongside the main Librarian doc as supporting material. |
| `6-feb/v0_4_0__issues-fs__semantic-text-architecture.md` | `semantic/` | **Architecture (Exploratory)** | Defines text-as-graph architecture. A distinct architectural domain from the core issue tracking -- deserves its own category. |
| `6-feb/v0_4_0__issues-fs__semantic-graph-code-representation.md` | `semantic/` | **Architecture (Exploratory)** | Defines how semantic graphs compile to code. Companion to the semantic text architecture doc. |
| `6-feb/v0_4_0__issues-fs__semantic-testing-dsl.md` | `semantic/` | **Architecture (Exploratory)** | Defines the testing DSL for semantic content. Companion to the other two semantic docs. Explicitly marked as exploratory. |
| `6-feb/v0_4_0__issues-fs__use-case-pattern.md` | `use-cases/` | **Architecture (Pattern)** | Meta-pattern for creating focused solutions. Defines a repeatable pattern -- belongs in its own category. |
| `6-feb/v0_4_0__issues-fs__use-case__github-backup.md` | `use-cases/github-backup/` | **Use Case Spec** | A specific instance of the use case pattern. Grouped under the use-cases category, in its own subdirectory because future use cases will follow. |
| `6-feb/agent-review__ecosystem-overview.md` | `reviews/2026-02-06/` | **Review Output** | Output from an agent review session. Date-scoping makes sense for review outputs (unlike architecture docs) because reviews are point-in-time assessments. |
| `6-feb/agent-review__component-inventory.md` | `reviews/2026-02-06/` | **Review Output** | Component inventory from the same review session. |
| `6-feb/agent-review__librarian-findings.md` | `reviews/2026-02-06/` | **Review Output** | Self-review findings from the Librarian subagent. |
| `6-feb/agent-review__next-steps.md` | `reviews/2026-02-06/` | **Review Output** | Synthesised recommendations from the review session. |

### Files Currently in `to_classify/already-legacy/`

| Current Location | Recommended Location | Classification | Rationale |
|-----------------|---------------------|---------------|-----------|
| `already-legacy/v0.1.0__issues-fs__lexicon-architecture.md` | `archive/` | **Superseded** | Lexicon Architecture v1.0, explicitly superseded by v2.0. Should be in a proper archive with a `superseded_by` reference to v2.0. |

### Files Already Classified (No Change Needed)

| Current Location | Status | Notes |
|-----------------|--------|-------|
| `issues_fs/architecture/v0.4.0__issues-fs__architecture-overview.md` | **Correctly placed** | Moves to `architecture/` in the new structure (the `issues_fs/` prefix is dropped as redundant -- all docs in this repo are about Issues-FS). |
| `issues_fs/dev-briefs/*` | **Correctly placed** | Moves to `development/dev-briefs/` |
| `issues_fs/llm-briefs/*` | **Correctly placed** | Moves to `development/llm-briefs/` |
| `development/llm-briefs/type-safety/*` | **Correctly placed** | Stays in `development/llm-briefs/type-safety/` |
| `development/llm-briefs/v3.63.4__for_llms__python_formatting_guide.md` | **Correctly placed** | Stays in `development/llm-briefs/` |

---

## 4. Classification Rationale

### The Five Document Categories

The proposed structure uses five top-level categories, each serving a distinct purpose:

**`foundations/`** -- Documents that define the core philosophy and principles underpinning the entire ecosystem. These are read-first, rarely-changing documents. Currently there is one: Thinking in Graphs. If additional foundational documents are written (e.g., "On Fractal Scopes" or "The Role of Honest Uncertainty"), they belong here.

**`architecture/`** -- System-level architecture documents that describe how the ecosystem is structured, what its components are, and how they interact. The architecture overview and the Lexicon design live here. These documents describe *what the system is*.

**`roles/`** -- Documents about the role-based agent coordination model. The six-role definition, the framework analysis, and role-specific architecture documents (like the Librarian role doc) live here. These describe *how the system is operated*.

**`semantic/`** -- Documents about the semantic text/graph architecture. This is a distinct domain from core issue tracking -- it describes how text content can be represented as graphs, compiled to code, and tested. These three documents form a coherent cluster and are all marked as exploratory.

**`use-cases/`** -- The use case pattern and specific use case specifications. These describe *focused solutions built on top of the ecosystem*. Each use case gets its own subdirectory.

Two additional categories handle supporting material:

**`reviews/`** -- Agent review outputs. These are point-in-time assessments, so date-scoping is appropriate (unlike architecture docs, which should be found by topic). Reviews age differently from architecture -- they are historical records of what was observed on a particular date.

**`development/`** -- Practical development guides, dev briefs for specific implementation tasks, and LLM context briefs. These are operational documents that support day-to-day work.

**`archive/`** -- Superseded or retired documents. These are kept for historical reference but clearly separated from active documents.

### Why This Hierarchy

The hierarchy reflects the Librarian's classification principles:

1. **Topic over time.** Documents are organized by what they are about, not when they were created. The `6-feb/` folder is eliminated because "February 6th" tells you nothing about content. The exception is `reviews/`, where date-scoping is meaningful because reviews are inherently temporal.

2. **Discoverable from the top.** A newcomer can scan the top-level folders and immediately understand the shape of the knowledge: there are foundations, architecture, roles, semantic extensions, use cases, reviews, development guides, and an archive. Each folder name is self-describing.

3. **Depth where needed, flatness where not.** `use-cases/` has subdirectories because use cases are independent units with potentially multiple files each. `foundations/` is flat because there are few foundational documents and each stands alone. Depth is added only when it aids navigation.

4. **No `to_classify/` in steady state.** The `to_classify/` directory is an admission of backlog. The goal of this reorganization is to empty it entirely. Going forward, new documents should be classified on accession -- the Librarian's Workflow 1 (New Document Accession) ensures every artifact gets placed immediately.

5. **Dropping the `issues_fs/` prefix.** The current structure has `issues_fs/architecture/` and `issues_fs/dev-briefs/`. Since the entire `Issues-FS__Docs` repository is about Issues-FS, the `issues_fs/` prefix is redundant. Documents about the broader development environment (osbot-utils, Type_Safe) live in `development/` without needing an `issues_fs/` qualifier.

---

## 5. Document Classification by Type

### Foundational Documents

These define the core philosophy. They rarely change and everything else depends on them:

| Document | Version | Status |
|----------|---------|--------|
| Thinking in Graphs: Meaning Through Connectivity | v1.0 | Draft (should be promoted to Active) |

### Architecture Documents

These define system structure. They evolve as the system grows:

| Document | Version | Status |
|----------|---------|--------|
| Issues-FS Architecture Overview | v1.0 | Active |
| Lexicon Architecture v2.0 | v2.0 | Draft |

### Role-Specific Documents

These define how AI agents operate within the system:

| Document | Version | Status |
|----------|---------|--------|
| Role-Based Agent Coordination | v1.0 | Draft |
| Role Architecture Framework Analysis | v1.0 | Draft |
| Librarian Role Architecture | v1.0 | Draft |
| Librarian Role Side-Capture | n/a | Raw (needs triage) |

### Exploratory Documents

These describe future capabilities that are designed but not built:

| Document | Version | Status |
|----------|---------|--------|
| Semantic Text Architecture | v1.0 | Draft (Exploratory) |
| Semantic Graph Code Representation | v1.0 | Draft (Exploratory) |
| Semantic Testing DSL | v1.0 | Draft (Exploratory) |

### Use Case Documents

These describe focused solutions:

| Document | Version | Status |
|----------|---------|--------|
| Use Case Pattern | v1.0 | Draft |
| GitHub Backup Use Case | v1.0 | Draft |

### Review Outputs

These are point-in-time assessments:

| Document | Date | Status |
|----------|------|--------|
| Ecosystem Overview | 2026-02-06 | Raw findings |
| Component Inventory | 2026-02-06 | Raw findings |
| Librarian Findings | 2026-02-06 | Raw findings |
| Next Steps | 2026-02-06 | Recommendations |

### Legacy/Superseded Documents

| Document | Superseded By |
|----------|--------------|
| Lexicon Architecture v1.0 | Lexicon Architecture v2.0 |

---

## 6. Status Observations

Several documents are marked as "Draft" that appear stable and well-reviewed enough to be promoted to "Active":

- **Thinking in Graphs** -- This is the foundational document. Everything depends on it. It should be marked Active.
- **Architecture Overview** -- Already marked Active. Correct.
- **Role-Based Agent Coordination** -- Stable design, actively being implemented (DevOps and Librarian role repos exist). Consider promoting to Active.

The semantic architecture documents (text, code representation, testing DSL) are correctly marked as Draft/Exploratory -- they describe future capabilities that have not been implemented.

The Librarian Role Side-Capture has a status of "Raw -- needs triage and routing." This is accurate. The four ideas in the side-capture should be processed through the Librarian's Draft-to-Document Processing workflow (Workflow 3): each idea should become either a Decision issue for the Architect, a Task, or be documented as a rejected proposal.

---

## 7. Cross-Reference Integrity

Several documents contain internal cross-references (relative links in their References sections) that will break if files are moved. When executing this reorganization:

1. Update all relative links within moved documents to reflect their new locations.
2. Update any documents outside `Issues-FS__Docs` that reference these files (e.g., ROLE.md files in role repos).
3. Consider adding a `_redirects.md` or mapping file during the transition period so that anyone looking for a document at its old path can find its new location.

---

## 8. Recommended Execution Order

1. **Create the new directory structure** (`foundations/`, `architecture/`, `roles/`, `semantic/`, `use-cases/`, `reviews/2026-02-06/`, `archive/`).
2. **Move foundational and architecture documents first** (Thinking in Graphs, Lexicon v2, Architecture Overview) -- these are the most referenced and their new locations need to be established early.
3. **Move role documents** (role coordination, framework analysis, Librarian role, Librarian side-capture).
4. **Move semantic documents** (the three semantic architecture docs).
5. **Move use case documents** (use case pattern, GitHub backup).
6. **Move review outputs** (the four agent-review docs).
7. **Move legacy document** to archive.
8. **Reorganize development docs** (move from `issues_fs/dev-briefs/` and `issues_fs/llm-briefs/` to `development/dev-briefs/` and `development/llm-briefs/`).
9. **Update all cross-references** in all moved documents.
10. **Delete empty directories** (`to_classify/`, `to_classify/6-feb/`, `to_classify/already-legacy/`, `issues_fs/`).
11. **Verify** -- run a scan for broken internal links.

---

## 9. Note on the Librarian Side-Capture

The file `v0_4_0__issues-fs__librarian-role-side-capture.md` contains four un-triaged ideas from the Librarian role design session:

1. Document Abstraction as Layered Semantic Graphs
2. Context Management for LLM Interactions
3. Storing Document Relationships in MGraph-DB
4. Every Published Artifact Gets Its Own Ontology

These should be processed as a separate task using the Draft-to-Document Processing workflow (Workflow 3 from the ROLE.md). Each idea should be evaluated and routed to either:
- A **Decision issue** for the Architect (ideas 1, 2, 3 are architectural proposals)
- An **extension** to an existing document (idea 4 may already be implicit in Thinking in Graphs)
- A **rejection** with documented rationale

This triage is itself a Librarian task and should not block the reorganization.

---

*Proposal by the Librarian Role*
*Date: 2026-02-06*
