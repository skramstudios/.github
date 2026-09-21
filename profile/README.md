# Skram Studios

Small command-line tools for working on one machine alongside coding agents.
Each one stands alone: install only the one you came for.

| Tool | What it is for |
| --- | --- |
| [skram-vault](https://github.com/skramstudios/skram-vault) | A git-backed folder of markdown you and your agents share: lore (what you learned the hard way), specs, and tickets. It lives outside every repo it serves, so it follows you across repos and machines and never enters anyone else's git history. CLI + MCP server. |
| skram *(release coming)* | One job queue for the things your agents cannot each have a copy of: the Docker VM, the local Kubernetes cluster, a shared build host. One job at a time per resource, with who asked, a human `hold`, `wait`, and `explain`. CLI + MCP server. |
| skram-tunnel *(release coming)* | Share a local app *and the identity provider it logs in against* on one public URL, so a reviewer on a phone can get past the login page. |

The tools are free to use. Binaries for macOS and Linux are on each
repository's releases page; the source is not published at the moment.
Issues are welcome on each repository.

They share one optional config file, `~/.config/skram/config.yaml`. Each tool
reads its own block and ignores the rest: see [config.md](https://github.com/skramstudios/.github/blob/main/config.md).
