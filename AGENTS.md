# Task execution

If the project specifies tests, always run them to validate your work, except in case of changes that are guaranteed to be safe.
In case of a large number of tests, validate using only a subset relevant to the change.
Never re-read files that you already remember reading, unless you suspect that the contents have changed (e.g., when `apply-patch` fails).
Avoid re-validating everything via `git` after completing a task - if the code compiles and works, there's no need.

# Scripting

Avoid writing perl/python/ruby scripts for automation.
Prefer `dotnet run`:

```sh
cat <<'CS' | dotnet run -
using System;
Console.WriteLine("Hello, World!");
CS
```

# Unity MCP tools

Use the Unity MCP tools to prototype solutions, validate code compilation and run tests.
Invoke the `restart` tool in case of instability.
When dealing with assets and GameObjects, `search`, `show`, `to_json`, `from_json_overwrite`, `find_missing_scripts`, `get_dependencies` and `find_references_to` are your friends.
When working with code, you can use `reflect` to browse types and members.
Always use `help` once to get instructions about the common query format used in `search`, `show`, `Search<T>` calls in `execute_code`, etc.

NEVER run the Unity process manually. NEVER kill the Unity process. Use the `restart` command instead.
NEVER build the Unity solution manually. NEVER `dotnet build Assembly-CSharp.csproj`. Call `refresh_asset_database` after making code changes instead.
