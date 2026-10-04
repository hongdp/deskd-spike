# Modification record

This is **deskd-spike**, an independently modified fork of
[OpenAI Codex](https://github.com/openai/codex). It is not an official OpenAI
distribution. Upstream and third-party notices remain in [NOTICE](NOTICE), and
the source license remains [Apache-2.0](LICENSE).

## Historical experiment

The desk spike was recorded at source revision `10c2ba0423`, with upstream base
`b0659c5386`. These identify source history, not the provenance of any binary that
may have been built separately.

The fork added historical desk configuration, role cards and hooks under `desk/`,
a provider wire adapter under `codex-rs/desk-shim/`, CLI adapter startup, and Linux
sandbox integration changes. The adapter included forwarding to a first-party
ChatGPT backend and Gemini translation. These are research artifacts, not the
supported authentication or isolation design for the replacement.

Role-card permission declarations and prompt labels must not be treated as
independent role identities. No production safety guarantee is derived from this
historical experiment.

The inherited changes relative to that upstream base are:

- `codex-rs/desk-shim/`, `codex-rs/cli/src/main.rs`, the workspace and CLI
  `Cargo.toml` files, and `Cargo.lock`: add and start the historical adapter.
- `codex-rs/linux-sandbox/src/daemon_mounts.rs`: skip mount entries whose root or
  destination cannot be decoded as an absolute mount path. The source comment
  mentions namespace mounts, but the actual skip is broader; this revision does
  not validate or endorse that isolation change.
- `.github/scripts/verify_cargo_workspace_manifests.py`: remove the `code-mode`
  workspace feature exception. Two upstream comment-only placeholder files,
  `codex-rs/core/tests/suite/scenarios_read_only_mcp.rs` and
  `codex-rs/login/src/internal_identity.rs`, were deleted.
- `.codespellignore` and `.gitignore`: add a spelling exception and exclusions
  for local sensitive/runtime material.
- `desk/`: add role/configuration material, launch and trust helpers, hooks,
  rules, a Python provider adapter, a host-policy example and a watch prototype.
  These are retained historical experiments, not deployment instructions.

## 2026-10-03: independent identity and retirement of unsafe defaults

Files changed in this hygiene revision:

- `README.md` and `SECURITY.md`: replace inherited product and reporting claims
  with the independent project identity, actual support limits and reporting
  guidance.
- `NOTICE`: preserve the upstream and third-party notices and add this fork's
  modification attribution.
- `MODIFICATIONS.md` and `desk/README.md`: document provenance, retained source
  and the replacement's migration boundaries.
- `desk/bin/deskd-spike`: provide a neutral, non-running retirement entry point.
- `desk/bin/codex-desk`: retire automatic use of the repository's desk home and
  fork binary. Neither entry point runs models, opens a login flow or starts the
  old proxy, including when called with `exec`, `login` or `app-server`.
- `codex-cli/package.json`, `sdk/typescript/package.json` and
  `codex-rs/responses-api-proxy/npm/package.json`: mark inherited npm packages
  private to prevent publishing this checkout under upstream package identities.
- `codex-cli/scripts/build_npm_package.py` and `scripts/stage_npm_packages.py`:
  refuse packaging while the CLI manifest is private, including generated
  platform packages, before creating staging output or downloading artifacts.
  Direct source-staging calls apply the same check.
- `.github/workflows/rust-release.yml`, `r2-release.yml`,
  `rust-release-zsh.yml` and `rusty-v8-release.yml`: restrict inherited release
  entry jobs to `openai/codex`. Existing upstream-only Python publishing guards
  remain in place. This change does not run or publish a release.
- Add file-level modification notices to the retained modified Rust sources,
  Cargo manifests/lockfile, workspace verification script,
  ignore file and desk TOML configuration. These comments change no configuration
  or Rust behavior. JSON and spelling-list provenance is recorded here because
  those formats do not support ordinary source comments.
- `desk/config.toml`, `desk/desk_shim.toml` and
  `desk/system/apparmor-codex-desk`: replace personal absolute paths with
  `/path/to/` placeholders and mark them as retired source examples. They must
  not be deployed or loaded as host policy. No active host profile is changed.

This revision does not change any running checkout, process, credential store,
hosted repository name, existing release, installed binary or remote setting.
Repository naming and any removal of previously published artifacts are separate
maintainer operations.

## Retained upstream UI and integrations

The Rust source still contains upstream titles such as “OpenAI Codex”, onboarding,
first-party login, updater, telemetry and service integration code. This revision
does not perform a global replacement of those strings or rewrite protocol names.
Source attribution and third-party notices must remain intact.

**Do not publish a modified runnable binary from this tree.** A future decision
to distribute one requires its own UI/login/update/service identity review,
dependency notices and behavioral tests. Merely changing the visible header would
not fix the inherited authentication or distribution identity. Existing manual
builds are outside the retired launchers' protection.

The planned deskd overlay instead installs the unmodified official harness
separately; its genuine upstream UI and notices should remain unchanged. BYOK is
the planned default, and supported third-party subscription authentication is a
separate optional capability. No compatibility with that capability is established
by this hygiene change.
