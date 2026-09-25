# SENTIALA AI

**A completely free, local-first, ethical OSINT username investigation platform.**

Sentiala researches a username across **117 public sources** and **publicly indexed
web pages**, collects structured evidence and public metadata, identifies
*possible* correlations, computes a transparent public-footprint exposure score,
and presents everything through an animated, dark intelligence-style dashboard.

---

## Core principles

- **Completely free.** No subscriptions, no credits, no scan limits, no locked
  features, no payment wall. Install locally and investigate as much as you want.
- **Ethical OSINT.** Publicly accessible pages only. Sentiala never attempts to
  crack or guess passwords, bypass authentication or CAPTCHA, access private
  accounts, or exploit websites.
- **No fake results.** `SCANNING` means the backend is really scanning, `FOUND`
  requires supporting evidence, and an HTTP error is *never* reported as
  "profile not found". Animations reflect real backend state only.
- **Correlation ≠ identity.** Sentiala distinguishes four layers:

  ```
  OBSERVED PUBLIC DATA  →  VERIFIED EVIDENCE  →  POSSIBLE CORRELATION  →  AI INTERPRETATION
  ```

  A correlation is always presented as a possible signal — for example
  *"Both public pages reference the same public domain"* — and never as
  "these accounts definitely belong to the same person".

---

## Quick start

### Kali Linux / Linux / macOS

```bash
git clone <your-repo-url> sentiala-ai
cd sentiala-ai
./start.sh          # or: bash start.sh
```

`start.sh` will create a virtual environment, install dependencies, start the
backend, and open the interface in your browser at `http://127.0.0.1:8765`.

Requirements: Python 3.10+ (`sudo apt install python3 python3-venv` on Kali) and
a desktop browser. Nothing else — no Node.js, no build step, no API keys.

### Windows

```bat
start.bat
```

The launcher creates a `.venv`, installs dependencies and opens the browser.

### Manual start (any OS)

```bash
python3 -m venv .venv
source .venv/bin/activate         # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python -m uvicorn backend.app.main:app --host 127.0.0.1 --port 8765
```

### Run the test suite

```bash
pytest -q
```

79 automated tests cover username validation, the 100+ source registry, URL
generation, evidence parsing and enrichment, discovery deduplication and
variant handling, correlation, geographic signals, evidence classification,
exposure scoring and groups, the AI fallback, the deep-scan stage pipeline,
and every API endpoint (all offline — no network needed).

---

## Developing in VS Code

The project ships with a ready-made `.vscode/` workspace:

1. **Open the folder**: `File → Open Folder... → sentiala-ai`
   (VS Code will prompt you to install the recommended Python extensions —
   accept them.)
2. **Create the virtual environment**: `Ctrl+Shift+P` →
   **Python: Create Environment...** → Venv → pick your Python 3.10+.
   (Or just run `bash start.sh` once — it creates `.venv` for you and VS Code
   will pick it up automatically via `.vscode/settings.json`.)
3. **Install dependencies**: `Ctrl+Shift+P` → **Tasks: Run Task** →
   `install dependencies` (or the terminal: `pip install -r requirements.txt`).

Then use the built-in workflows:

| Action | How |
|---|---|
| Run + debug with hot reload | **F5** (or the Run panel → "Sentiala: run + debug") — breakpoints in backend code work, and the server auto-restarts when you save a file |
| Run all tests | Testing sidebar (flask icon) → Run Tests, or `Ctrl+Shift+P` → `Tasks: Run Task` → `run tests (pytest)` |
| Debug the test file you're editing | Run panel → "Sentiala: debug current test file (pytest)" |
| Start the server (no debugger) | `Tasks: Run Task` → `start server (dev, hot reload)` |

Frontend edits need nothing special: the browser at `http://127.0.0.1:8765`
serves `frontend/` straight from disk, so a refresh picks up your changes
(with `--reload`, backend changes too).

Handy entry points when you start changing things:

- `backend/app/osint/sources.py` — add a source (one line, no engine changes)
- `backend/app/osint/engine.py` — investigation pipeline
- `frontend/src/components/` — one file per dashboard panel
- `frontend/src/styles/main.css` — the whole dark theme

---

## Publishing to GitHub

A GitHub Actions workflow (`.github/workflows/tests.yml`) runs the full offline
test suite on Python 3.10/3.11/3.12 for every push and pull request — it will
show up automatically under the *Actions* tab of your repo.

From VS Code or a terminal:

```bash
git init
git add .
git commit -m "Sentiala AI: free, ethical OSINT username investigation"
git branch -M main
git remote add origin https://github.com/<your-username>/sentiala-ai.git
git push -u origin main
```

Or use VS Code's built-in **Source Control** panel (`Ctrl+Shift+G`):
*Initialize Repository* → stage, commit, then **Publish Branch**, and VS Code
creates the remote repository for you if you're signed in to GitHub.

Already covered for you:

- `.gitignore` — keeps `.venv/`, caches, `.env` (secrets!) and the SQLite DB
  out of git
- `LICENSE` — MIT
- `.github/workflows/tests.yml` — CI on every push/PR

Never commit a real `SENTIALA_AI_API_KEY`: keep it only in your local `.env`
(see `.env.example`).

---

## Optional external AI (never required)

Sentiala works fully without any AI provider: the analysis falls back to a
local, deterministic, evidence-based analyzer.

To plug in an **OpenAI-compatible** endpoint, copy `.env.example` to `.env` and
set `SENTIALA_AI_API_KEY`, `SENTIALA_AI_BASE_URL` and `SENTIALA_AI_MODEL`.

A completely free local option that stays 100% offline:

```bash
ollama serve
ollama pull llama3
```

```ini
SENTIALA_AI_BASE_URL=http://localhost:11434/v1
SENTIALA_AI_MODEL=llama3
SENTIALA_AI_API_KEY=ollama
```

The AI only ever receives aggregated evidence statistics and can never invent
data; any failure degrades gracefully to the local fallback.

---

## Architecture

```
Browser
   │
   ▼
Frontend (dependency-free ES modules, served by the backend)
   │  polls GET /api/investigations/{id}  (clean polling; SSE-upgradeable)
   ▼
FastAPI Backend
   ├── Deep-Scan Pipeline        10 real stages, from initializing to report
   ├── Investigation Engine      controlled concurrency, per-source timeouts
   ├── Source Registry           117 sources, data-driven, one-line additions
   ├── Discovery Engine          public search index + username variants
   ├── Evidence Engine           honest state classification + metadata
   │                             enrichment (display name, bio, avatar, timing)
   ├── Evidence Items            DIRECT / CORRELATED / WEAK / UNCONFIRMED
   ├── Correlation Engine        possible signals, never identity claims
   ├── Geo Signals               ccTLD references only - never owner location
   ├── Scoring                   7 components + 5 presentation groups
   ├── AI Analysis               external-optional → local fallback
   └── SQLite Database           zero-setup local persistence
```

```
.vscode/                 ready-made workspace (debug, tests, tasks)
.github/workflows/       CI: runs the test suite on every push/PR
LICENSE                  MIT
backend/
    app/
        main.py            FastAPI app, static serving, lifespan
        config.py          env-driven settings (no hardcoded secrets)
        database.py        SQLite persistence
        api/routes.py      REST endpoints
        models/            dataclasses: sources, evidence, investigation
        schemas/           pydantic request/response models
        osint/
            sources.py     the 117-source registry (add one tuple = new source)
            registry.py    read-only registry view
            engine.py      investigation orchestrator
            evidence.py    response → honest evidence
            discovery.py   public web discovery
            correlation.py signal detection
            scoring.py     transparent 0-100 exposure score
            analysis.py    AI layer + local fallback
        services/report.py printable HTML report
        utils/             validation, HTML parsing
    tests/                 66 offline tests

frontend/
    index.html
    src/
        main.js            application controller (scroll-first dashboard)
        components/        landing, target header, deep-scan stepper, platform
                           intelligence cards, world map, live feed, correlation
                           graph, evidence board, AI panel, timeline, report
        visualizations/    custom canvas force-directed graph (no deps)
        animations/        ambient particles (paused when tab hidden)
        services/api.js    API client
        assets/world-110m.json   vendored TopoJSON (offline world map)
        styles/main.css    dark intelligence theme (custom scrollbars,
                           responsive, reduced-motion support)
```

### Adding a source

Append one line to `backend/app/osint/sources.py`:

```python
("Example", "Social", "https://example.com/@{u}", "high", ("page not found",), False),
```

No engine changes needed. The dashboard source count updates automatically.

---

## What each status means

| Status | Meaning |
|---|---|
| `SCANNING` | the source is being checked right now |
| `FOUND` | page loaded **and** the username is visible on it |
| `NOT_FOUND` | 404/410 or a known "no such profile" page |
| `UNCERTAIN` | page reachable but username not visible (JS-rendered etc.) |
| `BLOCKED` | site declined the request or redirected to a login wall |
| `ERROR` | server/network error — **never** treated as "not found" |
| `TIMEOUT` | source did not answer in time |

---

## Exposure score

A 0-100 score describing the *breadth of publicly discoverable information*
(not personality, morality or danger). It is fully transparent — the UI shows
every component:

| Component | Weight |
|---|---|
| Profile breadth | 30% |
| Category breadth | 15% |
| Public links | 15% |
| Metadata availability | 10% |
| Username reuse | 15% |
| Web discovery | 10% |
| Domain diversity | 5% |

---

## API

```
GET  /health                          service status, source count
GET  /api/sources                      registry summary
POST /api/investigations               start an investigation { "username": "..." }
GET  /api/investigations               list investigations
GET  /api/investigations/{id}          full live state (poll this)
GET  /api/investigations/{id}/report   standalone printable HTML report
```

Interactive API docs: `http://127.0.0.1:8765/docs`

---

## Security & ethics notes

- All secrets live in environment variables (`.env.example` provided; never
  commit real keys).
- Usernames are strictly validated (safe character set) before any URL is built.
- Every request has a timeout; concurrency is capped to stay polite.
- Sentiala only distinguishes observed public data from AI interpretation, and
  every report says so explicitly.

## License

Free to use, study, modify and share (MIT-style, do whatever you want, no
warranty). Use it responsibly and lawfully.
