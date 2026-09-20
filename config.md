# One config file, three tools

Every Skram tool reads `~/.config/skram/config.yaml` (or the file `--config`
names). Each reads the top-level keys it owns, plus `repos:`, and ignores
everything else, so a file written for one tool never breaks another, and a
file holding only one tool's block is a complete config for that tool.

| Top-level key | Read by | What it says |
| --- | --- | --- |
| `repos:` | all three | which git checkouts are which repo on this machine |
| `vault:` | skram-vault | where the vault is, and whether specs and tickets are on |
| `projects:`, `workflows:`, `reaper:`, `guard:` | skram | what can be queued, and against which shared resource |
| `tunnel:` | skram-tunnel | named targets worth sharing |

## `repos:`

The one block the tools have in common. It answers "which repo am I standing
in?" from the checkout's git origin, falling back to its path, so the answer
is the same in every clone and worktree.

```yaml
repos:
  my-app:
    remote: my-org/my-app        # owner/name or any git URL; every checkout with this origin matches
    paths: [~/Dev/my-app]        # checkouts on this machine (~ and globs); the fallback when there is no origin
    namespaces: [my-app]         # skram-vault: vault namespaces in scope here
    projects: [my-app]           # skram: what `skram run <target>` means here
```

A tool ignores the lines that belong to another: skram-vault never reads
`projects`, skram passes `namespaces` through untouched.

## A file for skram-vault alone

```yaml
repos:
  my-app:
    remote: my-org/my-app
    namespaces: [my-app]
vault:
  path: ~/vault
  specs: {}
  tickets: {}
```

`skram-vault init` writes this for you.

## What the tools write into a checkout

Only machine-local files, never anything you would commit: a section of
`AGENTS.local.md` per tool, a one-line `CLAUDE.local.md` that imports it, and
their entries in the checkout's `.git/info/exclude`, so none of it shows in
`git status`. Each tool replaces only the section under its own heading, so
they can run in any order.
