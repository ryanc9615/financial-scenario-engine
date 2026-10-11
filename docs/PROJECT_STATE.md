# Financial Scenario Engine — Project State

> Update at the end of each phase. Keep factual; planned features are not implemented features. This file is the handoff between tutor conversations.

## Current position

- **Phase:** 00 — Project Setup and Development Workflow
- **Status:** IN PROGRESS
- **Last completed phase:** None
- **Last handoff update:** 2026-10-11 (environment and package verified; commit published to GitHub; final understanding check pending)

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
- **Git evidence:** `git rev-parse --show-toplevel` returned the project root; `git remote -v` showed `origin`; `git log -1 --oneline` showed `d8896cb` on local `main` and local `origin/main` tracking reference. `git check-ignore -v .venv/pyvenv.cfg` confirmed the `.gitignore` rule.
- **Commands actually run successfully:** `python -m app`; direct execution of `app/__main__.py` from VS Code; `importlib.util.find_spec('app.__main__').origin`; `tomllib` parsing of `pyproject.toml`; environment and Git inspection commands.
- **Manual smoke checks observed passing:** package entry point printed the expected message; VS Code ran the same entry point; module lookup resolved to `app/__main__.py`; TOML parser returned the intended project metadata.
- **Automated tests observed passing:** None; an automated test suite has not been created.
- **Git commit evidence:** local commit `c794a99` (`Initialize Python development environment and entry point`) recorded five files. `git log -1 --oneline` confirmed the commit. `git status --short --branch` returned `## main...origin/main [ahead 1]` with no working-tree changes. Connected GitHub inspection later confirmed remote `main` at that same commit.
- **Staged review:** `git diff --cached --check` produced no output before commit. **Not yet verified:** local Git status after remote synchronization; full README Markdown cleanup; automated tests (not expected in Phase 00).

## Learning outcomes

- **Concepts demonstrated:** Python version/interpreter inspection; virtual environment activation and package isolation; dependency declaration versus installation; Git ignore/stage/commit/status; package invocation and module lookup; secrets handling. Five-question review attempted 2026-10-11; answers on dependencies, Git and secrets were broadly correct.
- **Concepts needing reinforcement:** base Python is also local to the machine; `sys.prefix` points to the active environment while `sys.base_prefix` points to the base Python installation. `python -m app` executes `app/__main__.py`, not every script in the folder. `git commit` is local; `git push` publishes to the remote.

## Known issues / blockers

- **Phase 00 remains IN PROGRESS** until the user can clearly explain interpreter isolation and package execution in their own words. All required setup operations were demonstrated.
- The GitHub README includes a duplicate plain-text `Getting started` heading and some unformatted shell commands; a minor documentation follow-up.
- The connected GitHub repository is **public**, although original setup instructions proposed private visibility. Confirm whether this is intentional and never commit secrets.
- The connected GitHub integration could read but could **not write** the updated state file (403 forbidden); apply this handoff locally and commit/push through the terminal.

## Next phase

- **Phase:** Finish Phase 00; then Phase 01 — Financial Domain Modelling in Python.
- **Prerequisites:** Answer two targeted follow-up questions about the base/virtual Python environment and `python -m app`. No new implementation is required.
- **First action:** Save this file to `docs/PROJECT_STATE.md`, check its diff, complete the two explanations, update the status to COMPLETE once demonstrated, then commit and push the final handoff. Begin Phase 01 only after this gate.

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