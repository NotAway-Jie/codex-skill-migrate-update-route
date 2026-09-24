# Optional Cross-Computer Migration Package

Read this reference only when the user requests a restore-ready backup, a new-computer migration, or a package spanning multiple agent runtimes. Do not load it for a normal skill inventory, update check, route audit, or single-skill move.

## Scope and contents

1. Confirm the source roots and target agent/runtime from current official documentation or runtime configuration. Separate active user skills from workbench copies, project skills, plugin-managed content, and caches. Include a category only when the user requests it or it is required by the selected workflow.
2. Create one dated package folder in the user's chosen destination. Include a concise `README.md`, restore-oriented `INSTALL.md`, machine-readable skill manifests (`.csv` and `.json`), a routing summary, and only the selected skill folders plus their required relative resources. Record each item's source, version or commit when verified, and expected target root. Do not turn an inventory archive into a full backup.
3. Keep the package reproducible: record file counts and hashes for included skill payloads, preserve relative references, and note excluded dependencies or unavailable roots. Do not package plugin caches as though they were portable installations.

## Privacy and validation

- Never copy raw authentication settings, tokens, credentials, private keys, shell histories, or unrelated machine configuration. Use redacted templates only when the user specifically needs configuration examples.
- For a public destination, omit private repository URLs, usernames, absolute paths, machine identifiers beyond the explicitly requested host label, and private project names unless the user specifically asks to include them.
- Scan the staging folder for secrets and review the actual ZIP entries before delivery. Do not delete an unsafe intermediate package until the corrected package passes validation.
- Verify the folder and archive exist, the archive opens, required manifest and restore files are present, every referenced skill file exists, counts and hashes match, and edited/synced skills pass the available `quick_validate.py`. If the validator cannot run because a dependency is missing, report that instead of claiming validation passed.
- Before restoring, compare each target against the package. Back up same-name targets before replacing anything; preserve local-only files and stop for a decision when changes conflict.

## Provenance

The package workflow is adapted from the inventory and validation ideas in [Fable-Forge/agent-skill-migration's migration checklist](https://github.com/Fable-Forge/agent-skill-migration/blob/main/references/migration-pack-checklist.md), an MIT-licensed project. This reference is a local workflow adaptation; it does not copy that project's files or scripts.
