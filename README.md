# deskd-spike

An independent, retired architecture experiment for **deskd**: a self-hosted
workspace with distinct agent seats and an auditable authorization ledger.
This repository is a modified fork of [OpenAI Codex](https://github.com/openai/codex).
It is not an OpenAI product and is not endorsed or supported by OpenAI.

The historical repository address and internal `codex-*` source identifiers
remain for provenance. The project's public name is **deskd-spike**; changing
documentation does not rename the hosted repository or an existing installation.

## Status

This spike is source material for the next deskd architecture, **not a supported
agent runtime or a trading system**. Its role cards and hooks do not establish
independent security identities. The planned replacement uses an unmodified,
separately installed Codex release, independent role roots, a credential gateway,
and a persistent coordination ledger. That replacement is not implemented here.

The old launcher is retired. `desk/bin/deskd-spike --help` explains the migration;
it does not start a model, load a desk home, or start the legacy provider proxy.
`desk/bin/codex-desk` is a retired compatibility entry point that refuses execution.
There is no supported run or login command in this repository.

Do not use the historical desk configuration with personal credentials, broker
accounts, or a production workspace. No real-money trading is supported. Future
examples start with a local paper ledger; external paper adapters require their
own authorization and isolation review.

## Authentication and distribution

The replacement's default is a user-supplied API key. Optional subscription
authentication must use a supported third-party application registration and
public API route under the application's own identity. The old first-party login
and ChatGPT backend proxy are not a supported deskd authentication path.

This fork does not publish runnable binaries or packages. The inherited npm CLI,
SDK and proxy packages are marked private, npm staging refuses this private
checkout, and inherited publishing paths are restricted to the upstream
repository. Historical Rust source still contains upstream UI,
login, update and service integrations; a manual source build does **not** make
those integrations supported for deskd. Do not distribute that build as an
official Codex release or as a completed deskd runtime.

For the unmodified upstream product, use the
[official Codex documentation](https://developers.openai.com/codex). Those
instructions describe OpenAI's distribution, not this fork.

## Repository guide

- [Historical desk material and migration boundaries](desk/README.md)
- [Modification and distribution record](MODIFICATIONS.md)
- [Security reporting and current limits](SECURITY.md)
- [License](LICENSE) and [required notices](NOTICE)

The existing upstream source, tests and contributor guidance are retained for
research and attribution. Retained upstream documentation is not a promise that
this fork supports all upstream product features.

## License and attribution

This fork remains under Apache-2.0; see [LICENSE](LICENSE). Preserve the original
copyright and third-party notices when redistributing permitted source material.
New files in this change are also Apache-2.0. This repository does not change the
license of the separate deskd project. Product names used to identify upstream
components do not imply affiliation or grant trademark rights.
