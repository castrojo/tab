# Template Modification Rule

## Codified Behavior: Do NOT Modify Review Templates During Guideline Updates

### Rule

When updating review guidelines, rating systems, or assessment frameworks:

**DO NOT** modify template sections that are used for future reviews.

Templates should be updated:
- ✅ When conducting actual reviews (by reviewers using the template)
- ✅ When explicitly requested by user to update templates
- ❌ NOT during guideline tone/framework updates

### Rationale

1. **Templates are tools, not guidelines:** Templates demonstrate how to apply guidelines, they don't define them
2. **Updated during use:** Reviewers naturally adopt new rating systems when conducting reviews
3. **Avoids confusion:** Mixing old and new rating systems in templates creates inconsistency
4. **Separation of concerns:** Guideline updates ≠ template updates

### Example: Reference Architecture Review Guidelines

**File:** `process/reference-architecture-review-guidelines.md`

**Guideline Sections (UPDATE these):**
- Lines 5-37: Review Principles, Rating Scale, Overall Assessment
- Lines 40-552: Individual criteria sections with ratings
- Lines 652-763: Agent instructions for conducting reviews

**Template Sections (DO NOT UPDATE these):**
- Lines 553-651: Review Deliverable Format (GitHub issue template)
  - Contains example titles, rating formats, section structure
  - Used by reviewers to create review issues
  - Will naturally adopt new rating system when used

### How to Identify Templates

Templates typically include:
- Example formats with placeholders (`[PLACEHOLDER]`)
- Markdown code blocks showing structure
- "Issue Body Template" or similar headings
- Demonstration of how to format outputs
- Empty fields to be filled in during use

### When User Requests Template Updates

If user explicitly says:
- "Update the template too"
- "Change the template format"
- "Update lines 553-651"

Then proceed with template updates. Otherwise, default to NOT modifying templates.

### Implementation in Tasks

When creating tasks that involve guideline updates:

```markdown
IMPORTANT: Do NOT modify Review Deliverable Format template section 
(lines 553-651) - that template is for future use and should not be 
updated as part of this reframe.
```

## Related Documents

- `.opencode/task-creation-protocol.md` - Task planning without execution
- This rule applies during both planning and execution phases
