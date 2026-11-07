<!-- ourostack:brand:start -->
<p align="center">
  <a href="https://github.com/ourostack"><img src="https://raw.githubusercontent.com/ourostack/.github/main/brand/headers/homebrew-tap.webp" alt="Ouro beside a copper brewing kettle and a barrel whose brass tap pours glowing green light into a mug" width="100%"></a>
</p>
<!-- ourostack:brand:end -->

# Ouro Homebrew tap

**Homebrew casks for our command-line tools.**

[Tools](#tools) · [m365crawl](https://github.com/ourostack/m365crawl) · [Add a tool](#for-maintainers) · [More from Ouro](https://github.com/ourostack)

```sh
brew install ourostack/tap/m365crawl
```

## Tools

| Tool | Install | Description |
| --- | --- | --- |
| [m365crawl](https://github.com/ourostack/m365crawl) | `brew install ourostack/tap/m365crawl` | Microsoft 365 for agents: offline search across Teams, Outlook and OneNote indexed notes, with source-qualified people observations and explicit transcript fetch. |

## For maintainers

<details>
<summary>Registering a new ourostack CLI</summary>

1. Add `owner/repo` as a line in `tools.txt`.
2. In the tool's release workflow, attach the goreleaser-rendered cask (`homebrew_casks` with `skip_upload: true`) to the release as `<tool>.rb`.

### How casks get here

Each tool publishes its own cask as part of its release. A stable release attaches its rendered cask as an asset named `<tool>.rb`, and once the release's artifacts verify, the tool's release workflow pushes that file to `Casks/<tool>.rb` on `main` as `<tool> <version>`. It pushes with a deploy key that can write to this repository and nothing else, held as the `HOMEBREW_TAP_DEPLOY_KEY` secret in the tool's repository. The push starts `Verify casks`, which installs every cask on a clean Mac. As a safety net, the `Update casks` workflow runs once a day (and on manual or `repository_dispatch` triggers): it reads `tools.txt`, downloads the `<tool>.rb` asset of each tool's newest release and commits it if the tap is behind. Do not edit casks by hand.

</details>
