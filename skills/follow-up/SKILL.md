---
name: 'follow-up'
description: 'Propose next actions based on the recent work.'
---

Goal: infer the next development actions the user is most likely to want after the current task.

Output a short list of actionable next steps.
Always include at least one next action.
Add more only when they are high-confidence and useful.
Prefer concrete developer instructions over vague suggestions.
Base predictions on the repo state, your recent changes, current task, and likely workflow.
