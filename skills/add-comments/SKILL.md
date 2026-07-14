---
name: 'add-comments'
description: 'Rules for writing comments in code.'
---

When writing or modifying code, make sure code contains comments that explain its purpose.
- Do not include comments that re-state what the code is doing.
- Comments must explain why the code exists, why a particular approach was chosen, or what constraint it satisfies—not how the code works.
- Comment non-obvious business rules, domain assumptions, and edge cases that are not apparent from the code itself.
- Include blocks of lowercase single-line comments above a block of unobvious code.
- Document unusual tradeoffs, performance optimizations, workarounds, and compatibility hacks, including the reason they are necessary.
- If a comment becomes inaccurate, update or remove it in the same change that modifies the code.
- Prefer improving names, structure, and decomposition before adding explanatory comments. Comments are not a substitute for readable code.
- Comments should add information that cannot be easily inferred from the code. Redundant comments should be removed.
- For complex algorithms, describe the high-level strategy, invariants, or correctness assumptions rather than individual implementation steps.
- Prefer comments that explain intent, constraints, and rationale over comments that narrate execution flow.
- (C#) Include XML comments on top of reusable public APIs. Prefer single-line XML comments when the <summary> is short.
- (C#) Include lowercase single-line comments (//) at the end of a particularly important line that needs explaining.

Examples:

---

Data.PrefabID = saveable.PrefabID;             // for pooled objects
Data.SceneLocalID = saveable.LocalID;          // for in-scene objects
Data.InstanceID = gameObject.GetInstanceID();  // for object reference remapping

---

// regular MonoBehaviours need editor query support without pretending their lifecycle callbacks ran.
// [ExecuteAlways] and runtime objects use the callback-backed storage directly.

---

// ensure duplicate updatables are not added
// (this happens when updatables are toggled on/off frequently)
for (int i = 0, n = updatables.Count; i < n; ++i)
    updatablesToAdd.Remove(array[i]);
