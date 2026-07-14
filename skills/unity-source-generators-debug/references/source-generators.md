Source generators usually emit code to `obj/Generated/`.
Note that this directory is preview-only. Unity never emits source generated code to files.

The generated source in `obj/Generated/` may be stale.
In order to refresh this preview manually after making changes, you need to build the Unity project's .sln file: `dotnet build <NAME>.sln`
You can also use the `unity.reflect` tool to confirm emitted types/members exist at runtime.
This may be faster if you don't need to read the code, and only want to check the presence of the emitted members.
