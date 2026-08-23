# Companion

**Web Companion** — Mobile-friendly dashboard to manage pets away from the desktop overlay.

Part of the [ComputerPets](https://github.com/RicheyWorks/computerpets) ecosystem. Index: [computerpets-ecosystem](https://github.com/RicheyWorks/computerpets-ecosystem).

> Status: **design scaffold**. This repository ships the contract, README, and layout so implementation can start without renaming the organ later.

## Why it exists

The desktop walk is the main quest. Companion is the phone: feed, call-back, medicine, and 'is Rui still on the PC?' when you are on the bus.

The flagship overlay already puts a living sticker on the real desktop (Rui first, 210 kinds). Companion does not replace that. It is one organ.

## Stack

TypeScript · React 19 · Vite · TanStack Query · Spring Boot API client · PWA

GroupId / namespace: `com.enterprisepet.companion`  
Default listen: `8080`

## Talks to

- computerpets Spring backend
- computerpets-quests
- computerpets-visitation
- computerpets-telemetry

## Contract

### Data

`PetCard(id, species, vitals, host) · CareAction(kind, ts) · Presence(machineId, lastSeen)`

### Surface

- GET /me/pets — owned pets + vitals (proxied from flagship)
- POST /me/pets/{id}/care — feed | play | rest | clean | medicine
- GET /me/presence — which machine currently hosts the overlay

### Failure doctrine

Desktop offline → queue care actions, sync on return. Auth missing → local demo Rui only, never another user's pet.

## Layout

```
computerpets-companion/
  README.md           this file
  LICENSE             MIT
  docs/CONTRACT.md    the same contract, frozen for implementers
  src/                implementation lands here
```

## Run (Windows)

PowerShell, from this folder, after the flagship helpers (Git, Node LTS 22+, JDK 21 as needed):

```powershell
cd app; npm install; npm run dev
```

You do not need this service to meet Rui. The [flagship start-here](https://github.com/RicheyWorks/computerpets/blob/main/docs/START-HERE.md) is still the first pet.

## Ecosystem

| Organ | Repo |
| --- | --- |
| Flagship desktop + Spring | [RicheyWorks/computerpets](https://github.com/RicheyWorks/computerpets) |
| This organ | [RicheyWorks/computerpets-companion](https://github.com/RicheyWorks/computerpets-companion) |
| Full map | [RicheyWorks/computerpets-ecosystem](https://github.com/RicheyWorks/computerpets-ecosystem) |

## License

MIT. See [LICENSE](LICENSE).

---

*Two hundred ten living kinds. Keep them so a line does not go quiet.*
