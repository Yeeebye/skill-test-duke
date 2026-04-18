---
name: skill-test-duke
description: "A demonstration skill that shows how to structure a Claude Code skill — covers overview, workflow, commands, and expected output. Use this as a template when creating new skills for Claude Code agents."
---

# Skill Test Duke

## Overview
This is a reference skill demonstrating the standard structure for Claude Code skills.
It does not perform real actions — it serves as a copyable template for building new skills.

## When to Use
- When you need a starting point for a new Claude Code skill
- When onboarding contributors who are unfamiliar with skill authoring conventions
- As a smoke-test to verify the skill-loading pipeline works end-to-end

## Workflow
1. Define the skill's trigger condition (what user request should invoke it).
2. Describe the steps the agent should follow, in order.
3. Specify any scripts, tools, or APIs the skill depends on.
4. Document expected outputs so the agent can verify success.

## Command
```bash
# Example command a skill might invoke
python scripts/skill_runner.py --skill skill-test-duke --env production
```

Example with dry-run flag:
```bash
python scripts/skill_runner.py --skill skill-test-duke --env production --dry-run
```

## Expected Output
On success:
- `[SKILL_OK] skill-test-duke executed successfully`
- A summary of actions taken

On failure:
- `[SKILL_ERROR] <reason>`
- Steps to remediate printed to stderr

## Parameters
| Parameter | Type   | Required | Description                        |
|-----------|--------|----------|------------------------------------|
| `--skill` | string | yes      | Name of the skill to run           |
| `--env`   | string | yes      | Target environment (dev/staging/production) |
| `--dry-run` | flag | no       | Simulate execution without side effects |

## Integration Notes
- Place this file at the repo root or inside `.claude/skills/`.
- The skill loader reads the YAML frontmatter (`name`, `description`) for indexing.
- Keep each skill focused on a single responsibility — compose complex flows from multiple skills.

## scripts/
- `scripts/skill_runner.py`: entry-point that dispatches to individual skill handlers.
