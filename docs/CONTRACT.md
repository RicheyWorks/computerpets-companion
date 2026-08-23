# Companion contract

Do not implement against folklore. Implement against this file.

## Identity

- Product: **Companion**
- Repo: `computerpets-companion`
- Category: Web & Client
- Idea: Web Companion
- Port / surface: `8080`

## Must

- Stay canon with 210 species. No illegal hybrids. No swapped voices.
- Treat the desktop overlay as the main quest. This organ is optional until wired.
- Fail soft: the overlay keeps walking if this service is down, unless this *is* the overlay.
- No PII in public artifacts (Steam id, wallet, home path, webcam frames).

## Data

PetCard(id, species, vitals, host) · CareAction(kind, ts) · Presence(machineId, lastSeen)

## Surface

- GET /me/pets — owned pets + vitals (proxied from flagship)
- POST /me/pets/{id}/care — feed | play | rest | clean | medicine
- GET /me/presence — which machine currently hosts the overlay

## Neighbors

- computerpets Spring backend
- computerpets-quests
- computerpets-visitation
- computerpets-telemetry

## Failure doctrine

Desktop offline → queue care actions, sync on return. Auth missing → local demo Rui only, never another user's pet.

## Stack

TypeScript · React 19 · Vite · TanStack Query · Spring Boot API client · PWA
