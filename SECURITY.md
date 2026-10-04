# Security policy for deskd-spike

deskd-spike is an independent experimental fork. It has no supported production
release, no supported trading deployment, and no claim of verified role isolation.
Its retired launchers do not run the historical desk. Do not provide this spike
with real model or broker credentials.

## Reporting an issue in this fork

Report fork-specific issues to this repository's maintainers, not to OpenAI's
security program. Use this repository's GitHub **Security → Report a
vulnerability** option if it is available. If private reporting is unavailable,
open a minimal issue asking for a private reporting channel; omit exploit details,
personal information, configurations, session traces and credentials from the
public issue. No private reporting channel or response-time guarantee is implied.

A safe initial report contains the source revision, affected component, a short
impact description and, when possible, a reproduction using a fresh directory,
mock service and synthetic data. Never attach authentication files, access keys,
authorization headers, account identifiers, private transcripts or a live account
reproduction. A maintainer does not need your credentials to reproduce a boundary
failure.

If the issue also reproduces on an unmodified OpenAI release, consult the
[upstream security policy](https://github.com/openai/codex/security/policy) for
reporting that upstream issue. OpenAI's program does not cover this fork merely
because it contains upstream code.

## Known boundaries

- Role names, prompts and hooks are not independent authorization identities.
- Legacy provider-proxy and first-party login paths remain in historical source;
  they are unsupported and are not started by the retired launchers.
- A path deny rule alone is not a complete credential or socket boundary. Process
  identity, directory ownership, aliases, environment inheritance and all code
  running outside the sandbox must be accounted for.
- Real role isolation, gateway authorization, restart recovery, credential
  handling and external paper adapters require separate implementation and
  acceptance tests. Mock protocol tests do not establish these properties.

Inherited publishing paths are restricted to upstream, npm packages are
private, and npm staging refuses this private checkout. These restrictions
prevent the documented release paths from
being used as a fork release; they are not a security sandbox for someone who
edits or manually executes source. See [MODIFICATIONS.md](MODIFICATIONS.md).
