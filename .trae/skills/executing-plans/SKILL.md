---
name: executing-plans
description: Use when you have a written implementation plan to execute in a separate session with review checkpoints
---

# Executing Plans

## Overview

Load plan, review critically, execute tasks in batches, report for review between batches.

**Core principle:** Batch execution with checkpoints for architect review.

**Mandatory tracking rule:** Every single step must be tracked using the `planning-with-files` skill. No step may be executed without updating its status.

**Announce at start:** "I'm using the executing-plans skill to implement this plan."

## The Process

### Step 1: Load and Review Plan
1. Read plan file  
   - Record status in `planning-with-files` as: `In Progress`
   - After reading, update to: `Completed`

2. Review critically  
   - Record status as: `In Progress`
   - Identify questions, risks, inconsistencies, or missing details
   - If review complete, update to: `Completed`
   - If blocked, update to: `Blocked` (include reason)

3. If concerns exist:
   - Record clarification task as `Blocked`
   - Raise issues with human partner before starting
   - Do NOT proceed until resolved

4. If no concerns:
   - Create TodoWrite
   - Record creation as `Completed`
   - Proceed to execution

### Step 2: Execute Batch
**Default: First 3 tasks**

For each task:
1. Mark task as `In Progress` using `planning-with-files`
2. Execute each step exactly as written (bite-sized steps)
   - Before starting each step → mark step `In Progress`
   - After finishing → mark step `Completed`
   - If failure → mark `Blocked` with reason
3. Run verifications exactly as specified
   - Mark verification step `In Progress`
   - After execution:
     - If success → `Completed`
     - If failure → `Blocked` and STOP execution
4. When entire task is done → mark task `Completed`

⚠️ No task or sub-step may be executed without status tracking.

### Step 3: Report
When batch complete:
- Ensure all related steps are marked appropriately in `planning-with-files`
- Show what was implemented
- Show verification output
- Say:  
  "Ready for feedback."

Wait for feedback before continuing.

### Step 4: Continue
Based on feedback:
- If changes required:
  - Add/update steps in `planning-with-files`
  - Mark modified steps appropriately
- Execute next batch
- Track every single step status
- Repeat until complete

### Step 5: Complete Development

After all tasks complete and verified:

1. Verify all plan steps are marked `Completed`
2. Announce:
   "I'm using the finishing-a-development-branch skill to complete this work."
3. **REQUIRED SUB-SKILL:** Use `superpowers:finishing-a-development-branch`
4. Track each finishing step using `planning-with-files`
5. Follow the skill to:
   - Verify tests
   - Present options
   - Execute selected option
6. Mark final state as `Completed`

## When to Stop and Ask for Help

**STOP executing immediately when:**
- Hit a blocker mid-batch (missing dependency, test fails, instruction unclear)
- Plan has critical gaps preventing starting
- You don't understand an instruction
- Verification fails repeatedly

**Ask for clarification rather than guessing.**

## When to Revisit Earlier Steps

**Return to Review (Step 1) when:**
- Partner updates the plan based on your feedback
- Fundamental approach needs rethinking

**Don't force through blockers** - stop and ask.

## Remember
- Review plan critically first
- Follow plan steps exactly
- Don't skip verifications
- Reference skills when plan says to
- Track EVERY step in `planning-with-files`
- Between batches: just report and wait
- Stop when blocked, don't guess
- Never start implementation on main/master branch without explicit user consent

## Integration

**Required workflow skills:**
- **planning-with-files**  
  REQUIRED: Must be used for every single step, sub-step, verification, clarification, and completion state update. No exceptions.
- **superpowers:writing-plans** - Creates the plan this skill executes
- **superpowers:finishing-a-development-branch** - Complete development after all tasks
