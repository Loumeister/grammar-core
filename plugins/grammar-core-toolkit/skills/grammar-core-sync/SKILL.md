---
name: grammar-core-sync
description: Safely synchronize a product repository's shared/grammar-core subtree with the canonical grammar-core repository and route portable fixes upstream first. Use for subtree pulls, sync-conflict handling, scope verification, product validation, and draft-PR handoff; do not use for ordinary content adapters or direct local edits inside the shared subtree.
---

# Grammar Core Sync

Canonical repository: `https://github.com/Loumeister/grammar-core.git`

Required subtree prefix: `shared/grammar-core`

Repository paths in prose begin with `/`; Git pathspecs and `--prefix` values omit that leading slash.

## 1. Preflight

1. Read the product repository's `/AGENTS.md`, `/docs/product-contract.md` or equivalent local contract, and validation instructions.
2. Confirm repository root, current branch, remotes, subtree presence, and worktree state:

   ```sh
   git rev-parse --show-toplevel
   git branch --show-current
   git remote -v
   git status --short
   git log -1 -- shared/grammar-core
   ```

3. Stop if the worktree is dirty. Do not stash, discard, or absorb unrelated user changes.
4. Identify the product remote and its default branch without assuming a branch name:

   ```sh
   git remote show <product-remote>
   git symbolic-ref refs/remotes/<product-remote>/HEAD
   ```

5. Identify the canonical default branch without assuming a branch name:

   ```sh
   git ls-remote --symref https://github.com/Loumeister/grammar-core.git HEAD
   ```

6. Fetch the product remote. Switch to its default branch, fast-forward it to the fetched remote-tracking ref, and prove that `HEAD` is exactly that fetched commit before creating a dedicated sync branch:

   ```sh
   git fetch <product-remote> --prune
   git switch <product-default-branch>
   git merge --ff-only <product-remote>/<product-default-branch>
   git rev-parse HEAD
   git rev-parse <product-remote>/<product-default-branch>
   git switch -c <sync-branch>
   ```

   The two `rev-parse` results must be identical. Stop if they differ; do not branch from an unverified local default branch.

7. Record the pre-sync commit as `<sync-base>` with `git rev-parse HEAD` after creating the sync branch.

Stop and ask for direction when the remote, default branch, prefix history, or clean baseline cannot be established.

## 2. Pull canonical history

Run the subtree pull with the detected canonical branch:

```sh
git subtree pull \
  --prefix=shared/grammar-core \
  https://github.com/Loumeister/grammar-core.git \
  <canonical-default-branch> \
  --squash
```

Do not modify files outside the prefix while the pull or merge is unresolved.

## 3. Resolve conflicts safely

1. Inspect the exact conflicts:

   ```sh
   git status --short
   git ls-files --unmerged
   git diff --name-only --diff-filter=U
   git diff --cc -- <conflicted-file>
   git diff --cached
   ```

2. Resolve each file from its actual intent. Canonical files normally follow upstream, but preserve product-local behavior outside the subtree through local wrappers, adapters, or contracts.
3. Never run blanket `checkout --theirs`, `checkout --ours`, or equivalent across `shared/grammar-core/`.
4. If a conflict exposes a local edit inside the shared subtree, stop and decide whether to:
   - upstream the portable improvement to `grammar-core` first;
   - move product-specific behavior into a local wrapper or contract; or
   - abort with `git merge --abort`.
5. After resolving each file, stage only that reviewed file. Re-run `git ls-files --unmerged` and review `git diff --cached` after every staged resolution.
6. When `git ls-files --unmerged` is empty, review the complete staged resolution, run `git diff --cached --check`, and complete the existing subtree merge with `git commit --no-edit`. Do not add unrelated changes to that merge commit.

## 4. Verify sync scope

Before changing local references, confirm that the subtree merge is complete. `git rev-parse -q --verify MERGE_HEAD` must produce no SHA, and `git status --short` must show no unresolved entries. Only then compare the committed sync result with `<sync-base>`:

```sh
git diff --name-status <sync-base>..HEAD
git diff --stat <sync-base>..HEAD
git diff --check <sync-base>..HEAD
```

The range must contain at least one committed path. Empty output from `git diff --name-status <sync-base>..HEAD` is not scope evidence: stop and report a no-op or investigate an unfinished merge. At this point, committed sync changes must be limited to `/shared/grammar-core/`. Stop and investigate any other path.

Review the canonical changes that may affect the product:

- shared/local scope contracts;
- adopted schemas and taxonomy;
- wrapper paths under `/.agents/skills/`;
- renamed or removed canonical files;
- product adapters and documented adoption boundaries.

## 5. Update local references explicitly

Only after the subtree scope is clean:

1. Update product-local wrappers, `/AGENTS.md`, contracts, README references, or recorded sync metadata made stale by the canonical change.
2. Keep these local edits separate and reviewable; do not rewrite canonical subtree content.
3. Search for stale canonical paths or removed skill names.
4. Re-run `git diff --check`.

## 6. Validate the consuming product

Run the checks required by the product repository, including:

- shared-content or schema validation;
- relevant unit and integration tests;
- lint and type checks;
- relevant end-to-end tests;
- skill discovery and frontmatter validation when skill paths changed.

Record pre-existing failures separately. Treat new failures as sync incompatibilities; do not mask them by changing canonical files locally.

## 7. Draft-PR handoff

Before any push, report:

- product and canonical branches used;
- `<sync-base>`, the non-empty committed sync range, and pulled canonical revision;
- subtree paths changed;
- local wrapper or reference changes;
- conflicts and their per-file resolutions;
- validations with pass/fail status;
- remaining risks.

Commit only intentional local follow-up changes. Push and create a draft pull request only when authorized. The draft PR must describe the canonical range, compatibility changes, validation evidence, and rollback plan.

## Reverse flow

For a portable improvement discovered in a product repository:

1. leave `/shared/grammar-core/` unchanged;
2. create and merge a focused change in `grammar-core`;
3. run this sync procedure after merge;
4. adapt the new canon locally through explicit product code or contracts.

Keep product-specific UI, evaluator logic, labels, progression, data shapes, and feedback flows local.

## Recovery

- During an unresolved subtree merge, use `git merge --abort`.
- After a completed sync commit has been shared, prefer a normal revert PR.
- Never use destructive reset or blanket file replacement to recover a sync.

## Completion criteria

Complete only when the worktree contains the intended subtree update plus explicit local compatibility changes, no unresolved conflicts or stale path references remain, required product checks pass or have documented pre-existing failures, and the draft-PR handoff is complete.
