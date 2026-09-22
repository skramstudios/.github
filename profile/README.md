# Skram Studios

Small command-line tools for working on one machine alongside coding agents.
Each one stands alone: install only the one you came for.

| Product | What it does |
| --- | --- |
| [Skram](https://github.com/skramstudios/skram) | One job queue you and your coding agents share: one job at a time per shared resource, every run logged. |
| [Skram Vault](https://github.com/skramstudios/skram-vault) | A git-backed folder of markdown you and your agents share: lore (what you learned the hard way), specs, and tickets. |
| [Skram Tunnel](https://github.com/skramstudios/skram-tunnel) | Shares a local app and the identity provider in front of it on one public URL, so a reviewer on a phone can get past the login page. |

The products are free to use. Binaries for macOS and Linux are on each
repository's releases page; the source is not published at the moment.
Questions and bugs go to Issues on the product's own repository; see
[SUPPORT.md](https://github.com/skramstudios/.github/blob/main/SUPPORT.md).

They share one optional config file, `~/.config/skram/config.yaml`. Each product
reads its own block and ignores the rest: see [config.md](https://github.com/skramstudios/.github/blob/main/config.md).
