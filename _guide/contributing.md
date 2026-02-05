# Contributing

## How to Contribute

1. **Fork** the repository
2. **Create** your entry using templates in `_guide/templates/`
3. **Submit** a pull request

All contributions require human review before merging.

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

Leave `reviewed_by` and `reviewed_date` empty—reviewers fill these.

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
