# Johann Moreno

**Frontend engineer.** I built an autonomous AI pipeline so I can focus on what I care about — the UI.

I send a voice note or a text to Telegram. Minutes later, there's a React app running in Kubernetes. The infrastructure, the CI/CD, the boilerplate — all handled by agents I built. I just write frontend.

---

## The Pipeline

Every app I ship goes through this system. Each component is a standalone TypeScript service running as a pod in my K8s cluster.

```
 Voice / Text
      │
      ▼
┌─────────────┐    ┌──────────────────┐    ┌─────────────┐    ┌──────────┐
│   Alisios   │───▶│     ForgeBot     │───▶│     R2D2    │───▶│  ArgoCD  │──▶ Live App
│  Telegram   │    │  Agent Civiliz.  │    │   DevOps    │    │  GitOps  │
└─────────────┘    └──────────────────┘    └─────────────┘    └──────────┘
```

### `alisios-bot` — Telegram → GitHub

The entry point. A Telegram bot that accepts text and **voice notes** (transcribed via OpenAI Whisper), detects deployment intent using GPT-4o mini, and triggers the pipeline with interactive confirmation.

```
You (voice): "Hazme una app para gestionar el inventario de comida"
      │
      ▼
 [Whisper] → transcription → [GPT-4o mini] → intent extraction → deployment API call
```

### `forge-bot` + `forge-agents` + `forge-comms` + `forge-memory` — Agent Civilization

Before any code is written, AI agents with distinct roles **discuss the problem**:

| Agent | Role | What it does |
|-------|------|-------------|
| **Product Owner** | Orchestrator | Runs first. Cites other agents, reviews their output, decides when specs are ready |
| **Functional Analyst** | Requirements | Breaks down user stories, acceptance criteria, edge cases |
| **UX Designer** | Interface | Proposes component structure, interaction patterns, responsive behavior |
| **Senior React Dev** | Architecture | Defines technical approach, component tree, state management, data flow |

The agents are **not GitHub Copilot agents** — they're custom prompts executed via OpenAI API, orchestrated by ForgeBot through GitHub Discussions. ForgeBot auto-approves and squash-merges PRs from `copilot/*` branches, cleans up, and logs everything.

The civilization has **persistent memory** (`forge-memory`) and **inter-agent messaging** (`forge-comms`) — agents can reference past decisions across projects.

### `devops-agent-r2d2` — One API Call → Running App

R2D2 automates the full GitOps lifecycle with a single API call:

```
POST /deploy
{
  "name": "my-app",
  "type": "remix"    ← front | back | remix
}
```

What happens behind the scenes:

1. **Creates GitHub repo** from the right template
2. **Injects CI/CD** — GitHub Actions workflow that builds Docker image → pushes to GHCR
3. **Generates K8s manifests** — Deployment, Service, Ingress with TLS
4. **Registers in ArgoCD** — app syncs automatically on every push
5. **Configures secrets** — GitHub secrets + imagePullSecrets, all wired
6. **Streams logs** via Server-Sent Events so Alisios can report progress back to Telegram

Three deployment types:
- **`front`** — Static HTML + nginx
- **`back`** — Node.js Express API with health checks
- **`remix`** — Full-stack React Router v7 app cloned from `remix-pod-starter`

Production endpoint: `devops-agent-r2d2.johannmoreno.dev`

### `infra-live` — GitOps Source of Truth

All Kubernetes manifests live here. ArgoCD watches this repo — any commit triggers automatic deployment. Structured by environment (`staging/`, `production/`) with shared base resources.

---

## The Platform Layer

The agents don't generate code from scratch every time. They build on top of standardized foundations:

### `tajao-design-system`

Production-grade React component library. Not a wrapper around MUI — built from primitives:

- **vanilla-extract** — Zero-runtime CSS, fully type-safe tokens and themes
- **Radix UI** — Accessible, unstyled primitives (Dialog, Popover, Select, etc.)
- **CVA** — Class variance authority for composable component variants
- **SSR-first** — No flash of unstyled content, works with React Router v7 streaming
- **Agent-friendly** — Every export has JSDoc with `@example` blocks so AI agents can use it correctly

### `remix-pod-starter`

The template R2D2 clones for every `remix` deployment:

- React Router v7 (Remix) with SSR
- TypeScript strict mode
- Tailwind CSS v4 + shadcn/ui components
- i18n (i18next, `es`/`en` by default)
- WCAG 2.1 AA accessibility defaults
- Light/dark theme with CSS custom properties
- Vitest + Testing Library
- Docker multi-stage build → K8s ready

### `open-claw-generator`

API to deploy and manage dockerized OpenClaw instances on a remote VPS via SSH. Each instance is an autonomous Telegram bot with Whisper transcription. Runs as a K8s pod, persists state in SQLite on a PVC.

### `bbdd-agent`

Database management API — handles schema creation, migrations, and data access for apps that need persistence beyond the frontend.

---

## What gets shipped

The output of the pipeline. These are the frontend applications — all TypeScript, all built in 2025–2026:

| App | What it is | Stack |
|-----|-----------|-------|
| **Mente Digital** | Obsidian-like knowledge base with Telegram integration for capturing ideas on the go | `TypeScript` `React Router v7` `Telegram API` |
| **Envite Canario** | Online multiplayer card game — the traditional Canarian "envite" with animations | `TypeScript` `React` `WebSockets` |
| **Dive Computer** | Nitrox calculator and dive planning tool for scuba diving | `TypeScript` `React` |
| **Healthy Habits** | Micro-exercise routine app with reminders and movement tracking | `TypeScript` `Remix` |
| **OVNI Tenerife** | Interactive map of UFO sightings in Tenerife — report and explore | `TypeScript` `React` `Maps API` |
| **Silbo Training** | Learn Silbo Gomero, the whistled language of the Canary Islands | `TypeScript` `React` `Web Audio` |
| **Inventario Comida** | Home food inventory tracker with expiry alerts | `TypeScript` `Remix` |
| **Inventario Ropa** | Wardrobe manager with categories and seasonal tracking | `TypeScript` `Remix` |
| **Gestión Tareas Hogar** | Household chore management with assignment and scheduling | `TypeScript` `Remix` |
| **Mama Fit** | Exercise routines with tagging, filtering, and progress tracking | `TypeScript` `React` |
| **Juego de las Sillas** | Musical chairs game for kids with audio and animations | `TypeScript` `React` |
| **App de Bienestar** | Office wellness — sends stretch/movement reminders throughout the day | `TypeScript` `Remix` |

---

## Stack

**Frontend** — where I spend my time:

`TypeScript` · `React` · `React Router v7 / Remix` · `vanilla-extract` · `Tailwind CSS` · `Radix UI` · `styled-components` · `Storybook` · `Vitest` · `Testing Library` · `GraphQL`

**Platform** — what the agents manage:

`Node.js` · `Express` · `Docker` · `Kubernetes` · `ArgoCD` · `GitHub Actions` · `GHCR` · `nginx`

**AI/Agents** — the glue:

`OpenAI API (GPT-4o)` · `Whisper` · `GitHub Copilot` · `Telegram Bot API` · `Server-Sent Events`

---

<div align="center">
<sub>Based in the Canary Islands · Open to opportunities in Barcelona & Madrid</sub>
<br/><br/>
<a href="https://www.linkedin.com/in/johannmoreno"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white"/></a>
</div>
