# Agent Instructions

## Repository Purpose

🎯 **This is a WORKING FORK of cncf/tab**

This repository serves as a prototyping and development workspace:
- Track ALL work with bd (beads) issue tracking
- Make iterative commits with bd metadata tracked in git
- Prototype, test, and refine changes locally
- Squash and clean up commits before submitting PRs upstream
- Keep upstream (cncf/tab) history clean and professional

**Why this pattern?**
- Preserves detailed work history and bd tracking in fork
- Submits polished, single-commit PRs to upstream
- Enables AI agents to track complex work without polluting upstream
- Maintains clean contribution history in cncf/tab

---

## Workflow Overview

### Work in Fork (Detailed Commits)
- Create bd issues for all work
- Make frequent, descriptive commits
- Push branches with .beads/ metadata tracked
- Iterate and refine with full history preserved

### Submit to Upstream (Single Squashed Commit)
- Branch from `upstream/main`
- Squash all work into ONE commit
- Exclude `.beads/` directory from PR
- Write professional commit message
- Submit clean PR to cncf/tab

---

## bd (Beads) Issue Tracking

This project uses **bd** for issue tracking. Run `bd prime` for full workflow context.

### Core Principles

- **ALL state lives in bd** - No TODO files, no markdown task lists
- **Create issues BEFORE coding** - Track work from conception
- **bd metadata STAYS in fork** - Never include .beads/ in upstream PRs
- **Track upstream issues** - Create bd issues for cncf/tab work
- **Link everything** - Reference upstream issue numbers in bd

### Quick Reference

```bash
bd ready              # Find available work
bd create "Title" --type task --priority 2  # Create issue (0-4, 0=critical, 2=medium)
bd show <id>          # View issue details
bd update <id> --status in_progress  # Claim work
bd close <id>         # Complete work
bd sync               # Sync with git
```

### Tracking Upstream Work

```bash
# Create bd issue for upstream work
bd create "Implement cncf/tab#95: Reviewer guidelines" \
  --type feature \
  --priority 1 \
  --description "Upstream: https://github.com/cncf/tab/issues/95"
```

---

## Essential Commands

### Git Configuration
```bash
# Add upstream remote (one-time setup)
git remote add upstream git@github.com:cncf/tab.git
git fetch upstream

# Configure bd role
git config beads.role contributor

# Install bd hooks for AI integration
bd hooks install
```

### Workflow: Fork (Detailed)
```bash
# Start work
bd create "Your work description" --type task --priority 2
bd update <id> --status in_progress
git checkout -b feature/your-work

# Make iterative commits (detailed history is GOOD here)
git add .
git commit -m "WIP: Initial implementation"
git commit -m "WIP: Add tests"
git commit -m "WIP: Update docs"

# Push to your fork (includes .beads/)
git push origin feature/your-work
```

### Workflow: Upstream PR (Squashed)

**IMPORTANT**: The user should write the PR description, not the AI. The AI prepares the branch and opens a browser for the user to complete the PR submission.

```bash
# 1. Fetch latest upstream
git fetch upstream

# 2. Create clean branch from upstream/main
git checkout -b upstream-your-work upstream/main

# 3. Copy specific files from your work (avoid squash merge which includes .beads/)
# Option A: Copy specific files manually
git show main:file1.md > file1.md
git show main:file2.md > file2.md
git add file1.md file2.md

# Option B: If using merge --squash, MUST exclude .beads/
git merge --squash main
git reset .beads/              # CRITICAL: Remove .beads/ from staging
rm -rf .beads/                 # Remove from working tree
git status                     # Verify only intended files are staged

# 4. Create single professional commit with AI attribution
git commit --no-verify -m "Your PR title

Detailed description of changes and motivation.

Addresses cncf/tab#<number>

Assisted-by: Claude 3.5 Sonnet via GitHub Copilot"

# 5. Verify commit contents (MUST show only intended files, no .beads/)
git log --oneline -1 --stat

# 6. Push branch to your fork
git push origin upstream-your-work

# 7. Open browser for user to create PR (USER FILLS IN PR DESCRIPTION)
xdg-open "https://github.com/cncf/tab/compare/main...castrojo:tab:upstream-your-work?expand=1"

# The user will:
# - Review the commit and file changes
# - Write the PR title and description
# - Submit the PR
# - Copy the PR URL

# 8. After user submits PR, close bd issue
bd close <id> --reason "PR submitted: <url>"

# 9. Switch back to main
git checkout main
```

### Troubleshooting Upstream PR Creation

**Problem: "branches are identical" when creating PR**
- The commit wasn't created or pushed
- Solution: Check `git log upstream/main..upstream-your-work` shows your commit
- If empty, you need to commit and push

**Problem: .beads/ directory included in commit**
- Solution: Reset and exclude it
```bash
git reset HEAD~1                 # Undo commit
git reset .beads/                # Unstage .beads/
rm -rf .beads/                   # Remove from working tree
git add <intended-files>         # Stage only what you want
git commit --no-verify -m "..."  # Commit without beads hook
```

**Problem: beads hook preventing commit**
- If beads database is missing (e.g., on clean branch), use `--no-verify`
- The hook is important for fork work, but PRs to upstream don't need beads validation
```bash
git commit --no-verify -m "Your commit message"
```

### Sync with Upstream
```bash
# Regular sync (do this often!)
git checkout main
git fetch upstream
git merge upstream/main
git push origin main
```

---

## Landing the Plane (Session Completion)

**When ending a work session**, you MUST complete ALL steps below. Work is NOT complete until `git push` succeeds.

### Mandatory Checklist

```bash
# 1. Check what changed
git status

# 2. Stage ALL changes (including .beads/)
git add .

# 3. Sync bd with git
bd sync

# 4. Commit to your fork
git commit -m "Session end: <description of work>"

# 5. PUSH to fork (MANDATORY)
git push origin <branch-name>

# 6. Verify push succeeded
git status  # MUST show "up to date with origin"

# 7. Update bd issues
bd list --status in_progress
bd update <id> --notes "Session paused at: <state>"
```

### Critical Rules

- Work is NOT complete until `git push` succeeds
- NEVER stop before pushing - that leaves work stranded locally
- NEVER say "ready to push when you are" - YOU must push
- If push fails, resolve and retry until it succeeds
- ALWAYS push to origin (your fork) before ending session
- NEVER push .beads/ to upstream (cncf/tab)

---

## Critical Requirements

### For Work in Fork
✅ **Detailed commits are ENCOURAGED**
✅ **Track .beads/ in git**
✅ **Push frequently to origin**
✅ **Preserve full iteration history**

### For Upstream PRs
🚨 **MUST be single squashed commit**
🚨 **MUST exclude .beads/ directory**
🚨 **MUST have professional commit message**
🚨 **MUST link to upstream issue**

---

## Configuration Verification

```bash
# Verify setup
git remote -v                  # Should show origin + upstream
git config --get beads.role    # Should show "contributor"
bd doctor                      # Should pass all checks
ls -la .git/hooks/             # Should show bd hooks
```

---

## Quick Reference

**Find work:**
- `bd ready` - Available work in bd
- `gh issue list --repo cncf/tab --state open` - Upstream issues

**Start work:**
- Create bd issue → Start work → Make commits → Push to fork

**Submit upstream:**
- Branch from upstream/main → Squash → Exclude .beads/ → Single commit → PR

**Session end:**
- Stage all → bd sync → Commit → Push → Verify

For full workflow context: `bd prime`

---

## AI Attribution Requirements

AI agents must disclose what tool and model they are using in the "Assisted-by" commit footer:

```text
Assisted-by: [Model Name] via [Tool Name]
```

Example:

```text
Assisted-by: Claude 3.5 Sonnet via GitHub Copilot
```

This attribution should be included in all commits made by AI agents, whether working in the fork or submitting upstream PRs. This helps maintain transparency about AI contributions to the project.
