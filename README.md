# ourostack Homebrew tap

Homebrew casks for ourostack command-line tools.

```sh
brew install ourostack/tap/<tool>
```

## Tools

| Tool | Install | Description |
| --- | --- | --- |
| [teamscrawl](https://github.com/ourostack/teamscrawl) | `brew install ourostack/tap/teamscrawl` | Mirror the Microsoft Teams desktop cache into local SQLite for agents. Read-only, offline, no tokens. |

## How casks get here

The tap pulls; no tool repo holds a credential for it. Each tool's release attaches its rendered cask as an asset named `<tool>.rb`. The `Update casks` workflow runs hourly (and on manual or `repository_dispatch` triggers), reads `tools.txt`, downloads the `<tool>.rb` asset of each tool's newest release (prereleases included), and commits `Casks/<tool>.rb` to `main` as `<tool> <version>` when it changed. Do not edit casks by hand.

## Registering a new ourostack CLI

1. Add `owner/repo` as a line in `tools.txt`.
2. In the tool's release workflow, attach the goreleaser-rendered cask (`homebrew_casks` with `skip_upload: true`) to the release as `<tool>.rb`.
