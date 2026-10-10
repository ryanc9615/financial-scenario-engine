# Publish this starter repository to GitHub

The archive distributed with this plan contains a **local Git repository and initial commit**. The GitHub remote repository is **not yet created**. Publish to your own account rather than adding this project to an unrelated repository.

## 1. Download and extract

Download `financial-scenario-engine-starter.zip` from the ChatGPT conversation and extract it. You should have a folder named `financial-scenario-engine` containing `README.md`, `docs/`, `prompts/` and a hidden `.git/` directory.

On macOS open **Terminal**, then change into the extracted folder (adjust path if you moved it):

```bash
cd ~/Downloads/financial-scenario-engine
git status
git log -1 --oneline
```

Expected: branch `main`, clean working tree and a first documentation/setup commit. If the directory isn't under Downloads, drag the extracted folder into the Terminal window after `cd ` to use its full path.

## 2. Create a private empty repository

1. Sign in to your personal GitHub account (`ryanc9615`, as identified by your connected account).
2. Visit https://github.com/new.
3. **Owner:** your own GitHub account; **Repository name:** `financial-scenario-engine`.
4. **Visibility:** Private (recommended for a learning project).
5. **Do not** select *Add a README*, `.gitignore` or a licence: these exist in the initial commit.
6. Select **Create repository**.

If you prefer a different name or owner, adapt the remote below. Do **not** publish secrets or `.env` files.

## 3. Connect local Git history and push

```bash
git remote add origin https://github.com/ryanc9615/financial-scenario-engine.git
git push -u origin main
```

If `origin` already exists, inspect with `git remote -v` and change it deliberately with `git remote set-url origin <correct-url>` rather than blindly overwriting.

GitHub HTTPS pushes require a supported credential manager/token or equivalent authentication, not a GitHub account password. You may instead use your existing SSH GitHub authentication and `git@github.com:ryanc9615/financial-scenario-engine.git`. Never paste tokens or secrets into ChatGPT.

## 4. Verify

```bash
git status
git remote -v
git branch -vv
```

Open the new GitHub repository page. Confirm `README.md`, `docs/` and `prompts/` are visible and the latest commit appears on `main`. The project is **not remotely published** until this verification succeeds.

## 5. Work with the repository throughout the apprenticeship

In each phase: work on a small change → run relevant tests → update `docs/PROJECT_STATE.md` → commit → push to GitHub. Branches are optional for solo work.

Example future workflow:

```bash
git status
git add -A
git commit -m "feat: implement customer movement forecast"
git push
```

Before committing, review `git diff --staged` and ensure you didn't stage passwords, `.env`, large data or irrelevant generated files.

## 6. ChatGPT Project references

You already uploaded the original scope. Add the following Markdown files **as Project reference files** using the Project's file-add control:

- `docs/ENGINEERING_SPEC.md`
- `docs/PHASE_ROADMAP.md`
- `docs/TUTOR_PROTOCOL.md`
- `docs/PHASE_PROMPTS.md`

Then paste the content of `docs/TUTOR_PROTOCOL.md` from the section under the divider into the Project's **Instructions** section. Keep repository `docs/PROJECT_STATE.md` as the up-to-date implementation handoff; don't treat an old Project-file copy of it as authoritative.

Start a new chat inside the same Project with `prompts/phase_00.md`. The tutor will guide Phase 00; the repository currently intentionally has no application code.

> The archive and files in the ChatGPT conversation do not automatically attach to your ChatGPT Project or publish to GitHub. Both actions above are explicitly required.
