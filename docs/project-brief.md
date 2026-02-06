# Issues-FS Project Brief

**Purpose:** General briefing document for any AI subagent working within the Issues-FS ecosystem.
**Date:** 2026-02-06
**Status:** Active

---

## What Issues-FS Is

Issues-FS is a **file-system-based, graph-native issue tracking system** designed to live inside Git repositories. Issues are stored as JSON files in a `.issues/` directory structure, committed and versioned alongside code. No external services, databases, or API tokens are required for basic operation.

The project is authored by Dinis Cruz (OWASP SBOT) and lives within the broader MGraph-AI ecosystem (~27 repositories).

## Core Design Principles

1. **Git-native:** Issues branch and merge with code, appear in `git diff`, and are versioned by Git.
2. **Graph data model:** Everything is a node. Relationships (blocks, depends-on, assigned-to) are first-class bidirectional links.
3. **Pluggable storage:** Memory-FS abstraction with backends for memory (tests), local disk (Git), SQLite, ZIP, S3/GCS.
4. **Type-safe:** All Python code uses osbot-utils `Type_Safe` with `Safe_*` primitives for runtime validation.
5. **AI-agent first:** Designed for AI agents to create, manage, and query issues without external auth.
6. **Fractal structure:** Issues nest inside other issues via `issues/` subdirectories.

## Graph-First Philosophy

The foundational philosophy, documented in "Thinking in Graphs: Meaning Through Connectivity", rests on ten principles. The most important for day-to-day work:

- **Everything is a node.** Nodes carry local properties but have no obligation to declare what they are.
- **Meaning comes from edges.** What a node "is" emerges from graph relationships traceable from it.
- **Confidence is proportional to connectivity.** More edges to well-defined reference points = higher confidence.
- **Honest uncertainty is the default.** Report what the graph supports, never assume.
- **Enrichment, not enforcement.** Low confidence is remedied by adding edges, not validation rules.

## Key Components

| Component | Package | Purpose | Status |
|-----------|---------|---------|--------|
| **Issues-FS** | `issues-fs` | Core library: Graph__Repository, Node__Service, Link__Service, MGraph integration, schemas, storage | Active |
| **Issues-FS__CLI** | `issues-fs-cli` | CLI tool: init, create, show, list, update, delete, link, comment, types | Active |
| **Issues-FS__Service** | `issues-fs-service` | FastAPI REST server with routes for Nodes, Links, Comments, Types, Graph | Active |
| **Issues-FS__Service__Client__Python** | `issues-fs-service-client` | Python API client + all request/response schemas (schema foundation) | Active |
| **Issues-FS__Service__UI** | `issues-fs-service-ui` | Web UI: FastAPI backend serving the web interface | Active |
| **Issues-FS__Docs** | `issues-fs-docs` | Documentation: architecture docs, dev briefs, LLM briefs | Active |
| **Issues-FS__Lexicon** | `issues-fs-lexicon` | Root graph with anchor nodes, analysis tools, bootstrap definitions | Designed, not built |

All Python schemas live in `Issues-FS__Service__Client__Python`. Both the core library and the service depend on it.

## Role-Based Agent Coordination

The ecosystem uses six specialised AI agent roles, each encoded as a Role Repo (submodule of `Issues-FS__Dev`):

| Role | Responsibility | Status |
|------|---------------|--------|
| **Conductor** | Orchestration, priorities, blockers | Designed, not built |
| **Architect** | Technical decisions, API design, ADRs | Designed, not built |
| **Dev** | Implementation, bug fixes, unit tests | Designed, not built |
| **QA** | Test strategy, quality gates | Designed, not built |
| **DevOps** | CI/CD, deployment, releases | Implemented |
| **Librarian** | Documentation curation, knowledge coherence | Bootstrapping |

Roles coordinate via **typed issues as a state machine**: Decision, Handoff, Review_Request, Approval, Blocker, Task, Defect, Release, Knowledge_Request, ADR.

## Key Technologies

| Technology | Purpose |
|-----------|---------|
| **Python 3.12+** | All repos |
| **Poetry** | Build system and dependency management |
| **osbot-utils / Type_Safe** | Runtime type validation, `Safe_*` primitives |
| **Memory-FS** | Pluggable storage abstraction |
| **MGraph-DB** | Graph database for traversal and visualization |
| **FastAPI** | REST API service layer |
| **osbot-fast-api** | FastAPI helpers |

## Repository Structure

```
Issues-FS__Dev/                          (development hub)
  modules/
    Issues-FS/                           (core library)
    Issues-FS__CLI/                      (command-line interface)
    Issues-FS__Service/                  (FastAPI server)
    Issues-FS__Service__Client__Python/  (schemas + Python client)
    Issues-FS__Service__UI/             (web UI)
    Issues-FS__Docs/                    (documentation)
  roles/
    Issues-FS__Dev__Role__DevOps/       (implemented)
    Issues-FS__Dev__Role__Librarian/    (bootstrapping)
```

## Important Conventions

- **Naming:** Repos use `Issues-FS__<Component>` naming. Packages use `issues-fs-<component>` (PyPI) or `issues_fs_<component>` (Python).
- **Type Safety:** All Python code uses osbot-utils `Type_Safe` as base class. Use `Safe_*` primitives (`Safe_Str`, `Safe_Id`, `Safe_UInt`, etc.) instead of raw Python types.
- **Testing:** Tests use pytest. Test files mirror source structure with `test__` prefix. Use `Type_Safe` patterns in tests.
- **Document headers:** Title, Document identifier, Version, Date, Status, Depends On.
- **Document status values:** Draft, Active, Superseded, Archived.
- **CI/CD:** GitHub Actions workflows. Repos have `ci-pipeline.yml`, `ci-pipeline__dev.yml`, `ci-pipeline__main.yml`.

## Current State

**What is built and working:**
- Core library with full CRUD, graph operations, and MGraph integration
- CLI tool with all basic commands
- FastAPI service with REST endpoints
- Python API client with all schemas
- Web UI with issue management views
- DevOps role repo with runbooks and CI

**What is extensively designed but not yet built:**
- Issues-FS__Lexicon (v2.0 architecture doc, 5-phase migration plan)
- Conductor, Architect, Dev, QA role repos (fully specified in docs)
- GitHub sync service (architecture documented)
- Use case pattern with GitHub Backup as first instance
- Semantic text architecture (text-as-graph)

**What is actively being bootstrapped:**
- Librarian role repo (this repo)
- Documentation classification and organization

## Dogfooding

Issues-FS manages itself using Issues-FS. Both the HTML Transformation Workbench and the Service UI have active `.issues/` directories tracking their own bugs, features, tasks, projects, and releases.

---

*Issues-FS Project Brief v1.0*
*Date: 2026-02-06*
