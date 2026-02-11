# Contributing

## How to Contribute

### Suggest via Issue

The quickest way to contribute — no git knowledge needed. [Open an issue](https://github.com/jarmolkowicz/modern-mind-knowledge-base/issues) to:

- Suggest a source or paper
- Flag an error or misinterpretation
- Propose a new concept or practice

### Add an Entry Directly

To write and submit a KB entry:

1. **Fork** the repository
2. **Create** your entry using templates in `_guide/templates/`
3. **Submit** a pull request

All contributions require human review before merging.

### AI-Assisted Workflows

For processing sources into KB entries, use the workflow prompts in `_workflows/`. These are structured prompts designed for AI agents — not scripts, not fully automated pipelines.

**Why semi-automated?** AI handles discovery and extraction. Humans make every editorial decision — what gets in, how it's framed, what it connects to.

**3-stage pipeline:**

1. **Scout** (`_workflows/scout.md`) — Discover new sources relevant to the KB domain. Outputs go to `_workspace/inbox/`.
2. **Screener** (`_workflows/screener.md`) — Assess a source for relevance and quality. Recommends include, partial, skip, or defer.
3. **Processor** (`_workflows/processor.md`) — Extract concepts, frameworks, practices, and source entries from approved sources.

**Guardrail:** All workflow outputs go to `_workspace/` — never directly to KB folders (`concepts/`, `frameworks/`, `practices/`, `sources/`). A human reviews and approves every entry before it moves into the KB.

Each stage hands off to the next after human review. The prompts are open so you can see exactly how content is processed. See the individual workflow files for detailed instructions.

## Templates

Use the appropriate template:

- `concept.md` — Ideas, phenomena, terms
- `framework.md` — Coherent systems
- `practice.md` — Actionable guidance
- `source.md` — Evidence (papers, books, articles)

## Required Metadata

Every entry needs YAML frontmatter:

```yaml
---
status: solid | emerging | speculative
area: [risk, erosion, preservation]
sources:
  - "Citation or reference"
reviewed_by:
reviewed_date:
---
```

Leave `reviewed_by` and `reviewed_date` empty — whoever reviews the entry fills these.

## Quality Standards

- **One concept per entry** — Keep entries focused
- **Plain language** — Accessible to non-academics
- **Source everything** — No unsourced claims
- **Connect entries** — Use `[[wikilinks]]` to relate concepts

## Naming Conventions

- Lowercase with hyphens: `cognitive-offloading.md`
- Sources: `author-keyword-year.md`
- Descriptive but concise

## What to Contribute

Good contributions:
- Research papers with clear implications
- Frameworks from domain experts
- Practices with evidence or strong reasoning
- Corrections or clarifications to existing entries

Not a fit:
- Opinion without evidence
- Content outside the "human thinking with AI" domain
- Duplicates of existing concepts
