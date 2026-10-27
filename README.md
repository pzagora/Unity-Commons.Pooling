# Unity Commons — Pooling

Object pooling for Unity Commons: `GenericObjectPool<T>` for reusing instances without per-frame allocation, plus `PoolSettings` for sharing pool sizing as an asset.

## Dependency

This package is **not standalone**. Its `Runtime/` carries a `.asmref` pointing at the `Commons` assembly, so its code compiles **into** Commons rather than into an assembly of its own. It therefore requires [Unity Commons](https://github.com/pzagora/Unity-Commons) to be present, and consumers reach these types through the `Commons` assembly (namespace `Commons`) — no separate assembly reference is needed.

## Installation

Install from the zagora.dev UPM registry — add the scoped registry (and OpenUPM, for UniTask) to `Packages/manifest.json`, then the package; its dependencies install automatically:

```json
"scopedRegistries": [
    { "name": "zagora.dev", "url": "https://upm.zagora.dev", "scopes": [ "com.zagoradev" ] },
    { "name": "OpenUPM", "url": "https://package.openupm.com", "scopes": [ "com.cysharp" ] }
],
"dependencies": {
  "com.zagoradev.unity.commons.pooling": "1.0.3"
}
```

Requires Unity `6000.0+`.

## Usage

```csharp
using Commons;

var pool = new GenericObjectPool<Projectile>(prefab, timeToLive: 10, initial: 8, max: 64);
var projectile = pool.Get();
pool.Release(projectile);
```
