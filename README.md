# Unity Commons — Pooling

Object pooling for Unity Commons: `GenericObjectPool<T>` for reusing instances without per-frame allocation, plus `PoolSettings` for sharing pool sizing as an asset.

## Dependency

This package is **not standalone**. Its `Runtime/` carries a `.asmref` pointing at the `Commons` assembly, so its code compiles **into** Commons rather than into an assembly of its own. It therefore requires [Unity Commons](https://github.com/pzagora/Unity-Commons) to be present, and consumers reach these types through the `Commons` assembly (namespace `Commons`) — no separate assembly reference is needed.

## Installation

Add both packages to `Packages/manifest.json`:

```json
"com.zagoradev.unity.commons": "https://github.com/pzagora/Unity-Commons.git",
"com.zagoradev.unity.commons.pooling": "https://github.com/pzagora/Unity-Commons.Pooling.git"
```

Requires Unity `6000.0+`.

## Usage

```csharp
using Commons;

var pool = new GenericObjectPool<Projectile>(prefab, timeToLive: 10, initial: 8, max: 64);
var projectile = pool.Get();
pool.Release(projectile);
```
