---
name: 'csharp-formatting-rules'
description: 'Rules for C# code formatting.'
---

# Prefer pattern matching where possible. Merge patterns.

```diff
-    var source = Units[sourceIndex];
-    if (source.IsInvalid)
+    if (Units[sourceIndex] is not { IsValid: true } source)
         continue;

-    var sourceStats = source.stats;
-    if (sourceStats.IsInvalid || sourceStats.ConditionStats.Health <= 0f)
+    if (source.stats is not { IsValid: true, ConditionStats.Health: > 0f }
sourceStats)
         continue;
```

# Use `var` for most type names

Exceptions:
  - keep explicit names for primitive types and Unity.Mathematics primitives
  - always use `out var ...` for out parameters (e.g., instead of specific `out string ...`)

```diff
-    GameObject go = comp.gameObject;
-    var active = false;
-    var unitPosition = UnitPositions[unitIndex];
-    var nearest = sources[0];
-    var nearestDistanceSq = math.distancesq(unitPosition, nearest);
-    GetPosition(out float3 xyz);
-    for (var i = 1; i < sources.Length; i++)
+    var go = comp.gameObject;
+    bool active = false;
+    float3 unitPosition = UnitPositions[unitIndex];
+    float3 nearest = sources[0];
+    float nearestDistanceSq = math.distancesq(unitPosition, nearest);
+    GetPosition(out var xyz);
+    for (int i = 1, n = sources.Length; i < n; ++i)
```

# Avoid pointlessly huge structs

```
readonly struct AgentAttackPositionMovementSettings
{
    public readonly float FootworkBackstepDistance;
    public readonly float FootworkLeashDistance;
    public readonly float CombatReachDestinationDistance;
    public readonly float CombatSlowDownDistance;
    public readonly float MeleeAttackStartPadding;
    public readonly float FootworkRepositionMinSeconds;
    public readonly float FootworkRepositionMaxSeconds;

    AgentAttackPositionMovementSettings(
        float footworkBackstepDistance,
        float footworkLeashDistance,
        float combatReachDestinationDistance,
        float combatSlowDownDistance,
        float meleeAttackStartPadding,
        float footworkRepositionMinSeconds,
        float footworkRepositionMaxSeconds
    )
    {
        FootworkBackstepDistance = footworkBackstepDistance;
        FootworkLeashDistance = footworkLeashDistance;
        CombatReachDestinationDistance = combatReachDestinationDistance;
        CombatSlowDownDistance = combatSlowDownDistance;
        MeleeAttackStartPadding = meleeAttackStartPadding;
        FootworkRepositionMinSeconds = footworkRepositionMinSeconds;
        FootworkRepositionMaxSeconds = footworkRepositionMaxSeconds;
    }
```

This could be 3x shorter with the use of `{ get; init; }`.

```
readonly struct AgentAttackPositionMovementSettings
{
    public readonly float FootworkBackstepDistance { get; init; }
    public readonly float FootworkLeashDistance { get; init; }
    public readonly float CombatReachDestinationDistance { get; init; }
    public readonly float CombatSlowDownDistance { get; init; }
    public readonly float MeleeAttackStartPadding { get; init; }
    public readonly float FootworkRepositionMinSeconds { get; init; }
    public readonly float FootworkRepositionMaxSeconds { get; init; }
```

# Avoid trivially simple utilities

This kind of code should be inlined:

```
static bool IsSameTarget(Unit.Unmanaged.AccessRO a, Unit.Unmanaged.AccessRO b)
    => a.InstanceIndex == b.InstanceIndex;
```

Single-use utilities should also be inlined. For example, instead of defining a whole method:

```
float GetReactionDelay(Unit.Unmanaged.AccessRW member, in SquadGraphData data)
    => AgentCombatRandom.Range(
        min: MinSeconds,
        max: MaxSeconds,
        unitIndex: member.InstanceIndex,
        ...
     );
```

just use:
```
float delay = AgentCombatRandom.Range(
    min: MinSeconds,
    max: MaxSeconds,
    unitIndex: member.InstanceIndex,
    ...
);
```
