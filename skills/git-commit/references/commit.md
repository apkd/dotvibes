Put together a short, descriptive commit message, followed by two newlines, then a longer commit description.
You should be able to recognize these changes from your last actions; check `git status --short` for a summary of changed files.
DO NOT re-read the diffs and files. You already remember what you worked on. No need to waste time like this.

---

Example message: Add .roslynqueryignore-based project filtering
Example description:
Implemented solution-level project filtering by reading `.roslynqueryignore`
and removing matching projects before the workspace is indexed.

Example message: Restrict CI push trigger
Example description:
CI only triggers on pushes to `master`, removing broad branch execution.

Example message: Add build-and-release workflow
Example description:
Implemented a release-driven CI workflow.
Commit flow now publishes linux binaries and artifacts, and manages
a rolling `release` tag plus generated release notes.

---

Do not overspecify. Avoid redundant information, repetitiveness and wordiness. For example, this description:
  Added three extra shader assets to the project preloaded shader list so they are loaded during startup.
  This keeps the required shader variants available at startup and avoids late loading during scene activation.

This should be simply stated as:
  Added three shader assets to preloaded shaders.

Another example:
  Update waybar cloud icon glyph
  Replaced the network usage widget's cloud icon constant with the networked cloud symbol.
  The widget now renders the updated icon from the configured Tabler font in status output.

Simplify this to:
  Update waybar cloud icon
  Replaced the cloud icon with the networked cloud symbol.

Complex changes deserve long descriptions, but simple changes shouldn't be overdescribed.
Small-scope, single file changes can usually be described in just a few words.

Describe the intent of the commit rather than just what changed.
Focus on the primary relevant change only.
Only describe what the commit actually does.

---

The description can be multiline.
Use past tense when describing what change was DONE, and present tense when describing what the code DOES.
Write without a subject; do not use "I", "we", etc.

Use terse language and avoid repetition.
Use simple, readable language; avoid wordiness and complicated phrasing.
Keep descriptions short and casual, especially for small granular commits.
Skip low-importance changes.
Do not list every modified file.
When a refactor touches many systems, only describe the refactor.

Do not describe changes to tests, artifacts, documentation, comments, XML docs, or other documentation.
Ignore consistency adjustments to serialization, tests, documentation, comments, and similar side effects.
Do not mention doc changes. These are less important than code changes.
Do not mention aligning other code. We are interested in the core change, not side refactors.
Do not mention keeping existing behavior. We are only interested in the new/modified behavior, not what we're keeping unchanged.
Avoid unnecessary adjectives; words like "safe" and "efficient" are usually redundant.

---

Write the commit message and description to a temporary file.
Commit the changes with `git commit -F <commit_message_path>`.
Retry with an elevated call in case of a sandbox issue.

Do not commit files that were not staged in the first place; leave those be.
Try to split the staged changes into separate commits if they naturally have several different areas of concern.
If there are no files to commit, or any other issue occurs, stop and respond.
Do not look for workarounds in case of problems; inform the user instead.
Ensure no data loss.
