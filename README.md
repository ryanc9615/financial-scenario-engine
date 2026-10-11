# Financial Scenario Engine

**Project 2 — Technical Apprenticeship**\
Status: **Documentation/reference setup; Phase 00 in progress**

A deliberately small Python backend for managing B2B SaaS financial scenarios, generating deterministic 12-month forecasts and comparing alternatives. The goal is practical mastery of Python, HTTP, FastAPI, SQL, PostgreSQL, SQLAlchemy, persistence, transactions and testing.

## Read this first

1. `docs/ORIGINAL_SCOPE.md` — full original project brief and boundaries.
2. `docs/ENGINEERING_SPEC.md` — agreed product, financial formulas, ten API endpoints, database and test contract.
3. `docs/PHASE_ROADMAP.md` — staged sequence with completion gates.
4. `docs/TUTOR_PROTOCOL.md` — how AI should tutor and assess, rather than autogenerate the entire system.
5. `docs/PROJECT_STATE.md` — current verified status and handoff between conversations.
6. `docs/DECISIONS.md` — accepted trade-offs and changes.
7. `prompts/` — individual copy-ready prompts for Phases 00–16.

**Start at:** `prompts/phase_00.md` in a new conversation in the existing ChatGPT Project.

## Delivery strategy

| Milestone | Phases | End result |
| --- | --- | --- |
| 1 — Python engine | 00–04 | Independently tested 12-month forecast |
| 2 — HTTP API | 05–06 | Stateless `POST /forecasts` and validation |
| 3 — Relational persistence | 07–08 | PostgreSQL and company API |
| 4 — Scenario CRUD | 09–11 | Persisted scenarios, transactions and integrity |
| 5 — Integrated calculations | 12–13 | Saved forecasts and 2–4-scenario comparisons |
| 6 — Reliability | 14–15 | Migration, error handling and debugging |
| 7 — Final mastery | 16 | Repeatable demonstration and technical examination |

Getting started


## Getting started

### Prerequisites

- **Python 3.12 or later** — tested with Python 3.12.5.
- **Git** — source control.
- **VS Code** — recommended editor.
- **Terminal** — instructions use macOS and Zsh.

### 1. Create a virtual environment

From the project root, run:

```bash
python3 -m venv .venv
```

This creates a project-specific virtual environment named `.venv`.

### 2. Activate the virtual environment

```bash
source .venv/bin/activate
```

This configures the terminal to use the project's Python environment.


### 3. Configure VS Code

Open the project folder in VS Code.

Open the Command Palette using Cmd + Shift + P.

Select Python: Select Interpreter.

Choose the interpreter at .venv/bin/python.

This ensures VS Code uses the same Python environment for running, debugging and analysing the project.

### 4. Run the application

From the project root, with the virtual environment activated, run:

python -m app

How it works:

python starts the selected Python interpreter.

-m instructs Python to locate and execute a module or package by name.

app identifies the project's Python package.

Python executes app/__main__.py, which currently serves as the application's entry point.

Expected output:

Financial Scenario Engine: environment ready

This confirms that the Python environment and application entry point are functioning.

### 5. Dependency management

Project metadata and dependency requirements are declared in pyproject.toml.

The project currently requires no third-party Python packages. Dependencies will be added incrementally as the relevant development phases require them.

.venv/ contains locally installed packages and is excluded from Git.

pyproject.toml declares project requirements and is tracked by Git.

.env.example documents example configuration variables without storing actual credentials.

.env is excluded from Git to prevent accidental disclosure of secrets.

Note: Creating a virtual environment does not automatically install dependencies declared in pyproject.toml. An installation step will be introduced when the project requires external packages.

### 6. Current limitations

The application currently contains only a minimal Python entry point. Financial calculations, HTTP endpoints and PostgreSQL persistence will be introduced in subsequent phases.

Do not expose unauthenticated write-enabled API endpoints publicly. The initial application will run locally for development and learning purposes.

## GitHub remote setup (one time)

For complete extraction, creation, authentication and verification steps, see `docs/GITHUB_SETUP.md`.

If creating a new GitHub repository from this existing local Git history:

1. In GitHub create a **private, empty** repository named `financial-scenario-engine` under your own account. **Do not** initialise it with a README, licence or `.gitignore`, because those files already exist here.
2. From the extracted project directory run:

```bash
git remote add origin https://github.com/ryanc9615/financial-scenario-engine.git
git push -u origin main
```

If you use SSH, substitute the SSH URL. Authenticate with the GitHub CLI, credential manager or your usual Git setup; never put personal access tokens in documents or chats. If your chosen repository name/owner differs, change the remote URL accordingly.

Check publication with `git remote -v` and the GitHub repository website. A local commit alone does **not** mean files have reached GitHub.