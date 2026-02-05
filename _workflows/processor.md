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

Use templates from `_guide/templates/`. Fill all fields.

Set `status: emerging` unless source is highly authoritative.

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

## New Entries Created
- concepts/[name].md
- practices/[name].md

## Updates to Existing
- concepts/[existing].md - [what's added]
- frameworks/[existing].md - [what's added]

## Skipped (duplicates)
- [concept] - already covered by [[existing]]

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
