
# 🌍 3D World

**3D World** es una plataforma tipo navegador tridimensional donde los usuarios pueden acceder a mundos creados por terceros mediante un sistema de portales dentro de un HUB 3D central.

Los mundos pueden ser:

- 🎮 Juegos
- 🎬 Series 3D caminables
- 🖼 Galerías interactivas

El objetivo es crear un ecosistema modular donde cada mundo se carga como un paquete dentro del mismo runtime del HUB, sin ejecutar procesos externos.

---

# 🏗 Arquitectura General

## 🎮 Cliente 3D (HUB)
- Motor: Unreal Engine 5
- Carga dinámica de mundos mediante paquetes (.pak)
- Sistema de portales
- Transición HUB → Mundo → HUB
- SDK obligatorio para integración

## 🖥 Backend
- ASP.NET Core (REST API)
- MySQL
- Autenticación JWT
- Sistema de catálogo y metadatos

---

# 📦 Sistema de Mundos

Los mundos:

- No se ejecutan como .exe externos
- Se montan dentro del mismo proceso del HUB
- Deben cumplir un contrato técnico (World SDK)
- Incluyen un World Manifest

---

# 📄 World Manifest

Cada mundo debe incluir un archivo manifest con al menos:

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

# 🧩 World SDK (Contrato Obligatorio)

## Funciones mínimas
- Init()
- Shutdown()
- GetSpawnPoints()
- OnEnter()
- OnExit()

## Eventos hacia el HUB
- OnWorldLoaded
- OnPlayerEntered
- OnEpisodeStarted
- OnGameStarted
- OnExitRequested
- OnCrashRecovered

---

# 🚀 Roadmap Inicial

## Fase 1 – MVP Base

1. Definir modelo arquitectónico definitivo.
2. Diseñar el World Manifest estándar.
3. Crear HUB MVP con portales funcionales.
4. Implementar Loader (descarga + caché + verificación hash).
5. Implementar transición real HUB → Mundo → HUB.

---

# 🔐 Principales Desafíos Técnicos

- Seguridad y sandbox de contenido de terceros
- Compatibilidad de versiones del engine
- Firma y validación de paquetes
- Escalabilidad del backend
- Telemetría y métricas centralizadas

---

# 🛣 Próximos Pasos

- Backend de catálogo completo
- Sistema de búsqueda y filtrado
- Uploader/Packager oficial para creadores
- Firma digital y verificación
- Sistema de cuentas y permisos
- Moderación y validación de contenido

---

# 📌 Filosofía del Proyecto

3D World no es un juego.
Es una plataforma base para experiencias 3D creadas por la comunidad, accesibles desde un HUB unificado, modular y expansible.
