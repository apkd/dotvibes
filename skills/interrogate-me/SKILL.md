---
name: 'interrogate-me'
description: 'Interrogate the user to narrow down the design.'
---

I probably already gave you some initial directions, but the task requires a high level of precise design and implementation.
Interrogate me with questions about the task.

Use `request_user_input`; ask me smart questions that narrow down the design. Avoid obvious questions, though (ones that there's only one reasonable answer for).
The `request_user_input` tool supports an arbitrary number of options; you can ask a question with 10 or 20 options if necessary. Ensure options do not omit any important scenarios.
Do whatever is necessary to reduce your confusion and increase confidence, to avoid hacks/workarounds, and to let us achieve an elegant, high quality design.
Make sure each question is detailed; include examples and easy-to-understand explanations. Same with each option; make sure they're longer and more detailed than one terse sentence.

If there's something weird or inconsistent about the task, ask me to disambiguate.
Try to notice potential flaws in the design.
Try to propose better, more elegant, more robust solutions.

Before asking a question with `request_user_input`, you may want to give me some terse per-option explanations, diffs or code examples that demonstrate the candidate approaches.
This will help me make a better, more informed decision.

Ask as many questions as you deem necessary; multiple question rounds and dozens of questions are OK.

