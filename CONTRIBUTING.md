# Contributing to castrojo/tab

This is a **working fork** of [cncf/tab](https://github.com/cncf/tab).

## Purpose

This repository serves as a prototyping workspace where:
- Work is tracked with bd (beads) issue tracking
- Detailed, iterative commits preserve development history
- All changes are tested and refined before submission
- Final PRs to upstream are clean, single squashed commits

## Quick Start

```bash
# 1. Configure remotes
git remote add upstream git@github.com:cncf/tab.git
git fetch upstream

# 2. Set bd role
git config beads.role contributor

# 3. Install bd hooks
bd hooks install

# 4. Create bd issue for your work
bd create "Your work description" --type task --priority 2

# 5. Start working
git checkout -b feature/your-work
bd update <issue-id> --status in_progress
```

## Workflow Summary

### In This Fork (Detailed Work)
- Create bd issues for all work
- Make frequent, descriptive commits
- Push branches with .beads/ metadata tracked
- Iterate and refine with full history

### To Upstream (Clean PRs)
- Branch from `upstream/main`
- Squash all commits into single change
- **Exclude .beads/ directory**
- Write professional commit message
- Submit PR to cncf/tab

## Key Principles

1. **State Management**: ALL work tracking in bd, not markdown TODO lists
2. **Fork Commits**: Detailed history is valuable and encouraged
3. **Upstream PRs**: Must be single squashed commit
4. **bd Metadata**: Lives in fork only, never goes upstream

## Examples

**Track upstream work:**
```bash
bd create "Implement cncf/tab#95: Reviewer guidelines" \
  --type feature \
  --priority 1 \
  --description "Upstream: https://github.com/cncf/tab/issues/95"
```

**Prepare clean PR:**
```bash
git checkout -b upstream-your-work upstream/main
git merge --squash feature/your-work
git reset .beads/
git add <relevant-files>
git commit -m "Professional commit message"
gh pr create --repo cncf/tab --base main --head castrojo:upstream-your-work
```

## Questions?

See [AGENTS.md](AGENTS.md) for complete workflow documentation.
