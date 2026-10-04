# Historical desk material

This directory belongs to **deskd-spike**, the retired experiment described in the
[repository README](../README.md). Its configuration, role cards, hooks and watcher
are source references. They are not an installation template for the replacement.
Personal absolute paths have been replaced with `/path/to/` placeholders.
Do not load the historical AppArmor example or deploy these configuration files.

## Retired entry points

```text
desk/bin/deskd-spike --help
```

This command only explains retirement. It does not launch a harness, read a desk
home, start a provider proxy or contact any service. The former `codex-desk`
entry point reports retirement and rejects all calls. Existing external scripts
that used it must be explicitly migrated; there is no silent fallback to the
historical binary.

Do not copy an existing home, authentication state, provider secret or broker
authorization into a new installation. Do not enable the old first-party login
proxy as a compatibility default. The replacement begins with fresh configuration,
synthetic paper data and separately validated boundaries.

## Replacement boundaries

- Official Codex is a separately installed, pinned dependency, not a required
  modified binary from this fork.
- Each accountable seat is a root thread; a child named after another seat does
  not acquire that seat's authority.
- A separate gateway owns credentials, deterministic policy and transaction
  records. Prompts and hooks alone do not establish this boundary.
- A trader may propose an entry, but another authorized principal must issue the
  grant before execution. The trader still reviews each exact order.
- Start with offline paper fixtures. Real-money trading is not a supported path.

These are migration requirements, not completed features of this directory.
See [MODIFICATIONS.md](../MODIFICATIONS.md) for the source and distribution scope.
