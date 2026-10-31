# Tjikup recipes

Tjikup is a Rust recipe runner in tjikOS. This repository supplies declarative
recipes and application commands. The runner has no Python library API.

The root workflow is Dotjik's `tjikup.json`. It declares prerequisites, exact
capture/autocommit files, repository synchronization, and explicit home/system
configuration managers. It includes each repository's `tjikup/recipes.json`.
The graph preserves shared resource exclusion and final service/network/release
ordering across both repositories.

Regular maintenance templates now live in `.chezmoitemplates/tjikup` under the
managed source root. They are not Chezmoi hooks. Tjikup renders and syntax-checks
them, then executes recipes. Plain `chezmoi apply` / `chezetc apply` no longer runs
these maintenance tasks. Native initial bootstrap/once/onchange hooks remain for
explicit bootstrap; Tjikup's file actions exclude scripts entirely. Recurring
Bitwarden CLI and font preparation are explicit Tjikup recipes.

Install both repository changes and the Rust runner together. From Dotjik:

```sh
bash scripts/install-tjikup.sh
tjikup --check
tjikup --plan
```

The installer validates the full graph before replacing the executable. Cargo
is required to build from source. Initial provisioning still follows the existing
bootstrap guides; install prerequisites and initialize Chezmoi/Chezetc before
running the fleet workflow. Tjikup does not silently bootstrap missing managers,
passwordless sudo, secrets or upstream branches.

`--dry-run` is now a strictly nonexecuting plan. `--upgrade` retains the package
upgrade policy. `--skip-conflicts` preserves conflicting files. `--skip-repo-sync` bypasses
repository pulls/pushes and their clean-worktree checks while retaining capture
and its scoped commit; both switches are declarative workflow policy. Missing checkouts,
detached branches and absent upstreams now fail explicitly before file apply.
If a pull changes recipe configuration, rerun Tjikup to use the new graph.

Capture remains a standalone Python command with the existing template-aware
propagators and private backups. It has no dependency on the runner's internals.
Autocommit and Git orchestration are native Rust actions, and only the explicitly
listed tracked files may be automatically committed. Unrelated work is preserved.

Logs and timing receipts are private under `~/.local/state/tjikup/logs`. No live
apply is part of tests. Test recipe rendering for fi/li/si, then perform a
supervised update before treating the migration as live acceptance.

The complete schema and execution contract are documented in
[tjikOS](https://github.com/tijptjik/tjikos/tree/main/apps/tjikup).
