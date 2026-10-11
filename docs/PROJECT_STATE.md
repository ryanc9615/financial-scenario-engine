# Financial Scenario Engine — Project State

> Update at the end of each phase. Keep factual; planned features are not implemented features. This file is the handoff between tutor conversations.

## Current position

- **Phase:** 00 — Project Setup and Development Workflow
- **Status:** COMPLETE
- **Last completed phase:** 00 — Project Setup and Development Workflow
- **Last handoff update:** 2026-10-11 (Phase 00 functionality, Git workflow and understanding check verified; final handoff update awaiting local commit)

## Working functionality

- A minimal Python package exists in `app/`, with `app/__init__.py` and `app/__main__.py`.
- Running `python -m app` from the repository root in the active virtual environment produced: `Financial Scenario Engine: environment ready`.
- VS Code also successfully executed `app/__main__.py` using the project's `.venv/bin/python` interpreter.
- No financial calculations, API routes, database operations or automated tests have been implemented.

## Repository / important files

- `app/__init__.py`: package marker; created during Phase 00.
- `app/__main__.py`: minimal runnable entry point; created during Phase 00.
- `pyproject.toml`: project metadata (`financial-scenario-engine`, version `0.1.0`, Python `>=3.12`) and an empty dependency list; parsed successfully using `tomllib`.
- `README.md`: existing project overview; getting-started instructions updated during Phase 00; GitHub inspection identified a duplicated plain-text heading and some unformatted commands to tidy later.
- `.gitignore`: excludes `.venv/`, local `.env` secrets, caches and generated files.
- `.env.example`: existing placeholder configuration; no database credentials introduced.
- `docs/ORIGINAL_SCOPE.md`: original project brief.
- `docs/ENGINEERING_SPEC.md`: agreed V1 technical contract.
- `docs/PHASE_ROADMAP.md`: phase index, dependencies and acceptance gates.
- `docs/TUTOR_PROTOCOL.md`: tutoring and phase-closure protocol.
- `docs/DECISIONS.md`: approved design decisions.
- `prompts/phase_00.md` through `prompts/phase_16.md`: phase conversation prompts.

## Decisions / architecture

- Retained the existing repository, documentation, `.gitignore` and `.env.example` instead of regenerating a scaffold.
- Used Python's built-in `venv` to create a local `.venv`; no third-party application dependencies installed during Phase 00.
- Created only a minimal `app` package and entry point. FastAPI, SQLAlchemy, PostgreSQL and financial calculations remain out of scope for this phase.
- The local Git repository is on `main`, with `origin` configured at `https://github.com/ryanc9615/financial-scenario-engine.git`.
- The earlier note that a GitHub remote still needed to be created is outdated. GitHub was checked directly: remote `main` points to `c794a9924684156cd0547253ae57b1f83742e5bb`. GitHub reports repository visibility as public.
- See `docs/DECISIONS.md` for existing agreed architectural decisions; no new deviation from the engineering specification was approved.

## Verification

- **Environment observed:** macOS (`Darwin`), Zsh (`/bin/zsh`), VS Code, Python 3.12.5 and Apple Git 2.39.3.
- **Base interpreter:** `/Library/Frameworks/Python.framework/Versions/3.12/bin/python3`.
- **Virtual environment interpreter:** `/Users/ryangael/Documents/Projects/LearningAI/financial-scenario-engine/.venv/bin/python`.
- **Environment evidence:** `sys.prefix` points to `.venv`; `sys.base_prefix` points to the base Python 3.12 installation. `python -m pip --version` returned pip 24.2 within `.venv`; `python -m pip list` showed only pip.
- **Git evidence:** `git rev-parse --show-toplevel` returned the project root; `git remote -v` showed `origin`; `git check-ignore -v .venv/pyvenv.cfg` confirmed the `.gitignore` rule. Initial reference commit was `d8896cb`; Phase 00 application commit is `c794a99` (see below).
- **Commands actually run successfully:** `python -m app`; direct execution of `app/__main__.py` from VS Code; `importlib.util.find_spec('app.__main__').origin`; `tomllib` parsing of `pyproject.toml`; environment and Git inspection commands.
- **Manual smoke checks observed passing:** package entry point printed the expected message; VS Code ran the same entry point; module lookup resolved to `app/__main__.py`; TOML parser returned the intended project metadata.
- **Automated tests observed passing:** None; an automated test suite has not been created.
- **Git commit evidence:** local commit `c794a99` (`Initialize Python development environment and entry point`) recorded five files. `git log -1 --oneline` confirmed the commit. `git status --short --branch` returned `## main...origin/main [ahead 1]` with no working-tree changes. Connected GitHub inspection later confirmed remote `main` at that same commit.
- **Staged review:** `git diff --cached --check` produced no output before commit. **Final interpreter verification:** after deactivation, running base `python3` produced equal `sys.prefix` and `sys.base_prefix`, both `/Library/Frameworks/Python.framework/Versions/3.12`. **Not yet verified:** local Git status after remote synchronization; complete README Markdown cleanup. No automated tests were required or run during Phase 00.

## Learning outcomes

- **Concepts demonstrated:** Python version and interpreter inspection; virtual environment activation, deactivation and package isolation; dependency declaration versus installation; Git ignore/stage/commit/status; package invocation and module lookup; secrets handling. The five-question review and two targeted follow-ups were completed on 2026-10-11. The user correctly identified that `python -m app` targets `app/__main__.py`, and observed equal prefixes when using base Python after deactivation.
- **Concepts to revisit during later phases:** confidently explain `sys.prefix` versus `sys.base_prefix` without prompting; distinguish direct file execution from package execution and imports; explain Git local commits versus remote publication. These are reinforcement goals, not blockers to advancing.

## Known issues / blockers

- No blocking Phase 00 implementation or understanding gaps remain. Functional and learning acceptance criteria have been met with observed evidence. The final handoff document still needs to be copied into the local repository and committed/pushed.
- The GitHub README includes a duplicate plain-text `Getting started` heading and some unformatted shell commands; a minor documentation follow-up.
- The connected GitHub repository is **public**, although original setup instructions proposed private visibility. Confirm whether this is intentional and never commit secrets.
- The connected GitHub integration could read but could **not write** the updated state file (403 forbidden); apply this handoff locally and commit/push through the terminal.

## Next phase

- **Phase:** 01 — Financial Domain Modelling in Python.
- **Prerequisites:** Copy this final handoff into local `docs/PROJECT_STATE.md`, review it, commit and push it; confirm local branch is synchronized. Preserve the completed Phase 00 files and working environment.
- **First action:** Review current repository files and this handoff. Compare a Python dictionary versus a dataclass for the V1 financial assumptions before choosing a domain representation. Do not begin financial calculations or add API/database code.

## End-of-phase handoff template

Copy and replace the sections above at each completion review:

```markdown
## Current position
- Phase:
- Status: NOT STARTED / IN PROGRESS / COMPLETE
- Last completed phase:

## Working functionality
- ...

## Repository / important files
- ...

## Decisions / architecture
- ...

## Verification
- Commands actually run:
- Tests observed passing:
- Tests failing or not run:

## Learning outcomes
- Concepts demonstrated:
- Concepts needing reinforcement:

## Known issues / blockers
- ...

## Next phase
- Phase:
- Prerequisites:
- First action:
```