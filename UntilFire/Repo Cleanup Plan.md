# Repo Cleanup Plan

Goal: make Obsidian the UntilFire information layer, and keep the GitHub repo focused on code.

## Already migrated

All Markdown files found in `/home/adminuser/projects/UntilFire` were copied into `UntilFire/` in the Obsidian vault.

Start here: [[UntilFire/UntilFire Knowledge Base]]

## Safe next repo cleanup

Do this only after confirming the vault migration looks right:

1. Keep a small `README.md` in the repo with:
   - what UntilFire is
   - how to install/run/test/build
   - pointer: “product docs live in Obsidian: `UntilFire/UntilFire Knowledge Base`”
2. Keep `AGENTS.md` only if agents need it before touching code.
3. Consider keeping `AUTH_SETUP.md` only if it is required for local setup; otherwise replace it with a short pointer.
4. Move or delete repo-only docs after confirmation:
   - `docs/`
   - `TODOS.md`
   - `CHANGELOG.md` if changelog is no longer code-release-facing
   - `CLAUDE.md` if not used by active tooling
   - `instructionsBundle/` if stale

## Do not delete yet

Repo files were not deleted in this pass. Deleting repo docs should be a separate git commit after review.

## Secret handling

Credential-like migrated lines were conservatively redacted where detected. Keep real tokens, keys, passwords, webhook secrets, and connection strings out of both the repo and the vault.
