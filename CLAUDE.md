# CLAUDE.md - Modern Mind Knowledge Base

## Project Overview

**What**: Curated knowledge base for the "human thinking with AI" domain—maintaining cognitive sovereignty while using AI productively.

**Purpose**: Research, practice, and professional insight translated into concepts you can teach from, apply, and verify. For anyone teaching about or navigating AI use.

**Audience — two personas:**
- **Educator** — Corporate trainers, L&D professionals, workshop facilitators, professors, and content creators who build learning experiences about AI and human thinking.
- **Practitioner** — Professionals who use AI daily — consultants, strategists, designers, developers, leaders, and anyone navigating AI in their work — who want to preserve their thinking, judgment, and expertise.

**Researcher = Collaborator, not audience.** Academics and scientists who review entries, validate claims, and contribute sources. We translate their work for practitioners. They don't need us to explain their own field.

## Repository Structure

```
Modern Mind Knowledge Base/
│
├── concepts/          # Ideas, phenomena, terms
├── frameworks/        # Coherent systems from authors
├── practices/         # Actionable guidance
├── sources/           # Evidence base (papers, books, articles)
│
├── _guide/
│   ├── contributing.md
│   └── templates/
│
├── _workflows/        # Agent processing prompts
│   ├── scout.md
│   ├── screener.md
│   └── processor.md
│
└── _workspace/        # Working area (not curated content)
    ├── inbox/
    ├── processing/
    └── archive/
```

## Metadata Schema

Every entry requires YAML frontmatter:

```yaml
---
status: solid | emerging | speculative
area: [risk, erosion, preservation]
sources:
  - "Citation"
reviewed_by:
reviewed_date:
---
```

### Status Levels
- **solid** — Peer-reviewed support, teach with confidence
- **emerging** — Supported but developing, or from thought leaders
- **speculative** — Hypothesis, needs evidence

### Area Tags
- **risk** — What capabilities are threatened
- **erosion** — Why and how capacity degrades
- **preservation** — What to do about it

## Naming Conventions

- Files: lowercase with hyphens (`cognitive-offloading.md`)
- Sources: `author-keyword-year.md` (`bjork-desirable-difficulties-2011.md`)
- Use `[[wikilinks]]` for internal references

## Workflow

All content goes through human review:

```
Source → Screener → Processor → Human Review → KB
```

### Guardrails

- **Never** write directly to `concepts/`, `frameworks/`, `practices/`, `sources/`
- **Always** output to `_workspace/processing/[source-slug]/` for review
- **Leave** `reviewed_by` and `reviewed_date` empty—reviewer fills these

## Templates

Use templates in `_guide/templates/` for new entries:
- `concept.md`
- `framework.md`
- `practice.md`
- `source.md`

## Contributing

See `_guide/contributing.md` for full guidelines.
