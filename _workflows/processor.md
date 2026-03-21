# Processor Workflow

## CRITICAL: Output Location

**NEVER write directly to KB folders (concepts/, sources/, practices/, frameworks/).**

All outputs go to `_workspace/processing/[source-slug]/`. Human approval required before any entry enters the KB.

**Do NOT:**
- Write to KB folders directly
- Edit existing KB entries
- Fill in `reviewed_by` or `reviewed_date` fields

---

## Purpose

Extract KB elements from approved source. Create new entries or draft updates to existing entries.

## Input

- Approved source from `_workspace/inbox/`
- Current KB state (all entries in concepts/, frameworks/, practices/, sources/)

## Process

### 1. Deep Read
Thoroughly read/analyze the source. Identify:
- All concepts mentioned or introduced
- Any frameworks or systems
- Actionable practices
- Key claims with evidence

**Entry type distinctions:**
- **Concept** — Names a phenomenon, mechanism, or idea. Explains *what* something is. Descriptive.
- **Framework** — A coherent system of related concepts with an author. Explains how things relate. Structural.
- **Practice** — Tells someone what to *do*. Actionable (specific steps), teachable (can be explained), repeatable (applies across situations). Prescriptive.
- **Source** — Every processed source gets a source entry. This is automatic.

Boundary cases:
- A concept that implies an action (e.g., "cognitive offloading") stays a concept. A specific protocol for when/how to offload (e.g., "cognitive portion control — stop AI before the polished end") is a practice.
- A principle that justifies practices (e.g., "partial automation principle") is a concept. The actionable method it supports (e.g., "strategic alternation") is a practice.
- If a source introduces both a concept AND a practice derived from it, create both with cross-links.

### 2. Match Against Existing KB

For each extracted element:

**Check existing entries:**
- Search by name/title
- Search by aliases/synonyms
- Search by description similarity

**Classify as:**
- **NEW**: Doesn't exist in KB → create entry
- **UPDATE**: Exists, source adds new insight → draft addition
- **DUPLICATE**: Exists, source adds nothing new → skip

### 3. Create Outputs

#### For NEW items
Create draft entries in `_workspace/processing/[source-slug]/new/`

Follow the structure in `_guide/templates/` for each entry type. Fill all fields. Set `status: emerging` unless source is highly authoritative.

**Concept** (template: `_guide/templates/concept.md`):
- Frontmatter: `status`, `area`, `sources`, `reviewed_by`, `reviewed_date`
- Sections: `What It Is`, `Why It Matters`, `Key Insight`, `Related`

**Framework** (template: `_guide/templates/framework.md`):
- Frontmatter: `status`, `area`, `sources`, `reviewed_by`, `reviewed_date`
- Sections: `Overview`, `Author`, `Core Idea`, `Key Components`, `Strengths`, `Limitations`, `Related`

**Practice** (template: `_guide/templates/practice.md`):
- Frontmatter: `status`, `area`, `sources`, `reviewed_by`, `reviewed_date`
- Sections: `What To Do`, `How To Do It` (numbered steps), `Why It Works`, `Related`

**Source** (template: `_guide/templates/source.md`):
- Frontmatter: `status`, `area`, `type` (paper|book|article|video|talk), `sources`, `reviewed_by`, `reviewed_date`
- Sections: `Citation`, `Type`, `Key Insight`, `Relevance`, `Supports`

#### For UPDATE items
Create update drafts in `_workspace/processing/[source-slug]/updates/`

Format:
```markdown
# Update: [Existing Entry Name]

## Source
[New source being processed]

## Proposed Additions

### To "[Section Name]" section:
[New content to add]

### To "Related" section:
- [[new-link]] - [relationship]

## New Source to Add
- "[Citation]"
```

#### For source entry itself
Create `_workspace/processing/[source-slug]/new/source-[slug].md`

Every processed source gets a sources/ entry.

### 4. Create Summary

Create `_workspace/processing/[source-slug]/SUMMARY.md`:

```markdown
# Processing Summary: [Source Title]

## Extraction Ledger

For each entry type, list what was extracted or explain why nothing was found.

### Concepts
- [NEW: name / UPDATE: name / NONE — rationale]

### Frameworks
- [NEW: name / UPDATE: name / NONE — rationale]

### Practices
- [NEW: name / UPDATE: name / NONE — rationale]

### Source Entry
- [filename]

## New Entries Created
- [type]/[name].md

## Updates to Existing
- [type]/[existing].md — [what's added]

## Skipped (duplicates)
- [element] — already covered by [[existing]]

## Ready for Review
- [ ] New entries
- [ ] Updates
- [ ] Source entry
```

## Output Structure

```
_workspace/processing/[source-slug]/
├── SUMMARY.md
├── new/
│   ├── concept-name.md
│   ├── practice-name.md
│   └── source-[slug].md
└── updates/
    ├── existing-concept.md
    └── existing-framework.md
```

## Handoff

Human reviews:
1. SUMMARY.md for overview
2. Each new entry → approve, edit, or reject
3. Each update → merge into existing entry or reject

Approved new entries move to KB folders.
Approved updates get manually merged.
Source moves to `_workspace/archive/`.
