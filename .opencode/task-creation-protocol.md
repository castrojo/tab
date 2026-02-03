# Task Creation Protocol

## Behavior: "Create all the tasks but do not execute"

When a user requests task creation without immediate execution, follow this protocol:

### 1. Planning Phase
- Analyze requirements comprehensively
- Break down work into logical tasks with clear dependencies
- Document task structure, descriptions, and relationships
- Get user approval on structure before creating

### 2. Creation Phase
- Create beads issues with complete descriptions
- Establish all dependencies between tasks
- Link tasks to parent epic if applicable
- Close/merge any superseded tasks
- Sync beads and commit changes to git

### 3. Do NOT Execute Phase
**CRITICAL:** Do NOT start work on the tasks after creation. Stop after:
- ✅ All beads issues created
- ✅ All dependencies established
- ✅ Changes committed and pushed to git
- ❌ Do NOT mark any task as in_progress
- ❌ Do NOT begin implementation work
- ❌ Do NOT make changes to target files

### 4. Handoff
After task creation is complete:
- Provide summary of what was created
- Show task IDs and structure
- Indicate which tasks are ready to work (no blockers)
- Wait for user to select which task to work on

## Example Workflow

```bash
# User says: "create all the tasks but do not execute"

# 1. Create epic
bd create --title "Epic name" --type epic --priority 1 --description "..."

# 2. Create all child tasks
bd create --title "Task 1" --type task --priority 1 --description "..."
bd create --title "Task 2" --type task --priority 1 --description "..."
# ... etc

# 3. Establish dependencies
bd dep add <task-id> <epic-id>
bd dep add <task-2-id> <task-1-id>
# ... etc

# 4. Sync and commit
bd sync
git add .beads/issues.jsonl
git commit -s -m "Create epic with tasks..."
git push origin main

# 5. STOP HERE - provide summary, wait for user direction
```

## When to Use This Protocol

Use this protocol when user explicitly says:
- "create all the tasks but do not execute"
- "plan the work but don't start yet"
- "set up the beads issues"
- Similar requests for planning without execution

## When NOT to Use This Protocol

Do NOT use this protocol when user says:
- "let's work on [task]" - implies execution
- "start with [task]" - implies execution
- "do [task]" - implies execution
- No explicit request to defer execution

## Benefits

This protocol enables:
- **Parallel execution:** Multiple agents can work on independent tasks
- **User control:** User chooses which task to prioritize
- **Clean planning:** Separate planning from execution
- **Flexibility:** Easy to adjust plan before starting work
