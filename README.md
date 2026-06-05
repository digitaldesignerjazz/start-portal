# Start Portal

**The Unified Entry Point & Dashboard for NexusSpace**

Start Portal is the central web interface for discovering, starting, monitoring, and interacting with every component of the NexusSpace ecosystem:

- Mesh Networking (xMesh, NovaNet, QNET)
- AI Agent Swarms & Emotional AI
- Hardware Prototypes (Grok Launcher, Soilnova, Vista Nova, etc.)
- Blockchain Layer (XCoin / QCoin + integrations)
- Monitoring & Observability
- Creative & Immersive Tools

It serves as both a **practical launcher** and a **beautiful overview dashboard** — the single place you (and eventually collaborators or agents) go to bring the nexus to life.

## Vision

Instead of juggling multiple terminals, Docker Compose files, config directories, and browser tabs, Start Portal gives you:

- At-a-glance status of all running services and prototypes
- One-click or guided "Start" actions for complex setups (mesh node + agents + monitoring in one flow)
- Deep links into the detailed documentation and code in the main [NexusSpace](https://github.com/digitaldesignerjazz/nexusspace) repository
- Extensible architecture so new prototypes and agent swarms can be added with minimal effort
- Future: Real-time updates via WebSockets or polling, authentication, multi-user / agent access

Start Portal is the **front door** to the Nexus.

## Current Status (June 2026)

- Just initialized
- Static HTML + Tailwind prototype dashboard available immediately (open `index.html` in a browser)
- Full architecture and tech decisions documented below
- Ready for rapid evolution into a dynamic web application

## Proposed Architecture

### Tech Stack Options (to be decided / iterated)

**Recommended Path (High Performance + Native Feel):**
- **Backend**: Rust + Axum (or Actix) — high performance, safe, great async story for long-running connections
- **Frontend**: Leptos (or Dioxus) for full-stack Rust, or SvelteKit / HTMX + Tailwind for faster iteration
- **Real-time**: WebSockets or Server-Sent Events for live status updates
- **State**: In-memory + optional SQLite / Redis for persistence
- **Deployment**: Docker, easily runnable alongside mesh nodes and agents

**Simpler / Faster Iteration Path:**
- Python (FastAPI) + HTMX + Tailwind (very quick to build rich interactive UIs)
- Or even a static site + lightweight backend for status

The static prototype in this repo uses **Tailwind CSS via CDN** so you can open `index.html` directly with zero setup.

## Folder Structure (Planned)

```
start-portal/
├── README.md
├── LICENSE
├── .gitignore
├── index.html                 # Current beautiful static prototype
├── public/                    # Static assets (icons, themes)
├── src/                       # Future backend/frontend source
│   ├── backend/              # Rust Axum or Python FastAPI
│   └── frontend/             # Leptos / Svelte / HTMX components
├── docs/
│   ├── architecture.md
│   └── integration-guide.md   # How to add new Nexus components
└── docker/
    └── Dockerfile
    └── docker-compose.yml
```

## How to Use Right Now (Static Prototype)

1. Clone or download this repo
2. Open `index.html` in any modern browser
3. Explore the dashboard cards for Mesh, AI Agents, Prototypes, Blockchain, Creative, and Monitoring
4. Click the "Start" buttons (currently visual only — will be wired to real actions)

This already gives a strong sense of the intended experience.

## Integration with NexusSpace

Start Portal is designed to work hand-in-hand with the main [NexusSpace](https://github.com/digitaldesignerjazz/nexusspace) monorepo:

- Links to detailed READMEs and docs in each subdirectory
- Will eventually read status from monitoring tools living in `tools/monitoring/`
- Can trigger Docker Compose profiles or scripts from `mesh-networking/configs/` and `prototypes/`
- Future agent swarms can interact with the portal via API

## Next Steps & Priorities

- [ ] Decide on final tech stack (Rust full-stack vs Python + HTMX vs other)
- [ ] Turn the static prototype into a real dynamic dashboard (live status, actual start/stop actions)
- [ ] Add authentication / local-only mode
- [ ] Create first real integration (e.g., start a mesh node + basic monitoring)
- [ ] Dockerize the portal so it can run as part of the overall Nexus stack
- [ ] Add WebSocket / SSE support for real-time updates

See the main NexusSpace repository for the broader vision and current state of all components.

---

**Start Portal is the place where the Nexus becomes accessible.**

Let's build the front door.