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

Each tool publishes its own cask as part of its release. A stable release attaches its rendered cask as an asset named `<tool>.rb`, and once the release's artifacts verify, the tool's release workflow pushes that file to `Casks/<tool>.rb` on `main` as `<tool> <version>`. It pushes with a deploy key that can write to this repository and nothing else, held as the `HOMEBREW_TAP_DEPLOY_KEY` secret in the tool's repository. The push starts `Verify casks`, which installs every cask on a clean Mac. As a safety net, the `Update casks` workflow runs once a day (and on manual or `repository_dispatch` triggers): it reads `tools.txt`, downloads the `<tool>.rb` asset of each tool's newest release and commits it if the tap is behind. Do not edit casks by hand.

## Registering a new ourostack CLI

1. Add `owner/repo` as a line in `tools.txt`.
2. In the tool's release workflow, attach the goreleaser-rendered cask (`homebrew_casks` with `skip_upload: true`) to the release as `<tool>.rb`.
