# Companion

**Keep an eye on your pet away from the desktop.**

A planned mobile-friendly care dashboard showing pet vitals, care actions, and the machine hosting the overlay.

**Stage: design scaffold.** This checkout contains a design document and a source placeholder. The experience below is planned; there is no runnable app or integrated service yet.

[Status](#status) · [Planned experience](#planned-experience) · [Contributor quickstart](#contributor-quickstart) · [Service contract](docs/CONTRACT.md) · [Ecosystem map](https://github.com/RicheyWorks/computerpets-ecosystem)

## Status

| Available today | What you can inspect |
| --- | --- |
| [Service contract](docs/CONTRACT.md) | Intended behavior, boundaries, and planned dependencies. |
| [Source placeholder](src/companion/index.ts) | Name metadata only; no package.json, app, or runtime is checked in. |
| [MIT license](LICENSE) | Licensing terms for the repository. |

Gameplay, endpoints, integration arrows, and failure handling on this page describe implementation targets. No build/test harness, CI workflow, or product screenshots are included in this scaffold.

## Planned experience

- GET /me/pets — owned pets + vitals (proxied from flagship)
- POST /me/pets/{id}/care — feed | play | rest | clean | medicine
- GET /me/presence — which machine currently hosts the overlay

### Planned technology

TypeScript · React 19 · Vite · TanStack Query · Spring Boot API client · PWA

### Planned connections

These arrows show intended dependencies, rather than working integrations.

```mermaid
flowchart LR
  phone --> companion
  companion --> spring
  companion --> quests
  companion -->|recall| visitation
```

## Contributor quickstart

With access to this private repository, Git and PowerShell are enough to review the scaffold:

```powershell
git clone https://github.com/RicheyWorks/computerpets-companion.git
Set-Location computerpets-companion
Get-Content docs/CONTRACT.md
Get-Content src/companion/index.ts
```

Read [Service contract](docs/CONTRACT.md) before choosing implementation details. The commands above inspect the checked-in files; app installation, editor launch, and server startup become possible after a buildable project and entry point are added.

### First implementation target

**Pet card for Rui: vitals, feed/play/rest/clean/medicine, presence of the host machine.**

You know it works when: Backend down: queue care, do not pretend it landed. No auth: local demo Rui only.

Treat this as an acceptance target for a future implementation. Start with the documented slice, add the required project setup and focused tests, and update these instructions with commands that work from a fresh clone.

## Design boundaries

- Stay canon with 210 species. No illegal hybrids. No swapped voices.
- Treat the desktop overlay as the main quest. This organ is optional until wired.
- Fail soft: the overlay keeps walking if this service is down, unless this *is* the overlay.
- No PII in public artifacts (Steam id, wallet, home path, webcam frames).

**Required failure behavior:**

Desktop offline → queue care actions, sync on return. Auth missing → local demo Rui only, never another user's pet.

## Ecosystem

- [computerpets](https://github.com/RicheyWorks/computerpets) Spring backend
- [computerpets-quests](https://github.com/RicheyWorks/computerpets-quests)
- [computerpets-visitation](https://github.com/RicheyWorks/computerpets-visitation)
- [computerpets-telemetry](https://github.com/RicheyWorks/computerpets-telemetry)

Start with the [ComputerPets flagship](https://github.com/RicheyWorks/computerpets) for the desktop pet. This repository describes an optional extension; the [ecosystem map](https://github.com/RicheyWorks/computerpets-ecosystem) explains the broader plan.

## License

MIT. See [LICENSE](LICENSE).
