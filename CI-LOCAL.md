# Local verification and hosted exceptions

Follow the household [GitHub Actions and local-first CI policy](https://github.com/norma-cat/housecat/blob/main/common-room/standards/GITHUB-ACTIONS-AND-CI.md).
Automatic hosted CI is disabled by default. Retained manual hosted workflows
require concrete justification and explicit authorization before execution;
paid Actions usage requires Cailea's approval. Keep feature branches, committed
exact-SHA local tests, strict documented final review and all required acceptance,
release, security and independent-review gates. No gate is waived by this change.

On a suitable local Nix development target, run:

```fish
nix flake check -L --keep-going
```

The retained manual workflow calls the existing reusable Nix build workflow.
That upstream recipe also runs `nix flake update`; perform dependency updates only
on a dedicated branch, review the lockfile diff and repeat checks. This CI-only
change does not update dependencies, build or install plugins. Preserve all
upstream build and compatibility requirements.
