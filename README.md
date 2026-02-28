
# 🌍 3D World

**3D World** is a 3D browser-like platform where users can access user-created worlds through a central 3D HUB using a portal-based system.

Worlds can be:

- 🎮 Games
- 🎬 Walkable 3D Series
- 🖼 Interactive Galleries

The goal is to build a modular ecosystem where each world loads as a package inside the HUB runtime, without launching external executables.

---

# 🏗 Overall Architecture

## 🎮 3D Client (HUB)
- Engine: Unreal Engine 5
- Dynamic world loading via (.pak) packages
- Portal system
- HUB → World → HUB transitions
- Mandatory integration SDK

## 🖥 Backend
- ASP.NET Core (REST API)
- MySQL
- JWT Authentication
- Centralized catalog and metadata system

---

# 📦 World System

Worlds:

- Do not run as external executables
- Are mounted inside the HUB process
- Must comply with a technical contract (World SDK)
- Include a World Manifest

---

# 📄 World Manifest

Each world must include at minimum:

```json
{
  "worldId": "string",
  "version": "string",
  "type": "game | series | gallery",
  "tags": ["string"],
  "entryMap": "string",
  "entrySpawn": "string",
  "thumbnail": "string",
  "contentUrl": "string",
  "hash": "string",
  "capabilities": ["walking", "spectator", "multiplayer"],
  "author": "string",
  "requiredEngineVersion": "string"
}
```

---

# 🧩 World SDK (Mandatory Contract)

## Minimum Required Functions
- Init()
- Shutdown()
- GetSpawnPoints()
- OnEnter()
- OnExit()

## Events Reported to the HUB
- OnWorldLoaded
- OnPlayerEntered
- OnEpisodeStarted
- OnGameStarted
- OnExitRequested
- OnCrashRecovered

---

# 🚀 Initial Roadmap

## Phase 1 – Base MVP

1. Define final architectural model.
2. Design the standard World Manifest.
3. Build HUB MVP with functional portals.
4. Implement Loader (download + cache + hash verification).
5. Implement real HUB → World → HUB transition.

---

# 🔐 Main Technical Challenges

- Security and third-party content sandboxing
- Engine version compatibility
- Package signing and validation
- Backend scalability
- Centralized telemetry and metrics

---

# 🛣 Next Steps

- Full backend catalog
- Search and filtering system
- Official uploader/packager for creators
- Digital signature system
- Accounts and permissions
- Content moderation

---

# 📌 Project Philosophy

3D World is not a game.

It is a foundational platform for community-created 3D experiences, accessible from a unified, modular, and expandable HUB.
