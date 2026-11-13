# portolan-spec-site

This repo deploys the rendered Portolan specification to <https://spec.portolan-sdi.org/>. It contains a deploy workflow and no content.

The specification text and the build code live in [portolan-spec](https://github.com/portolan-sdi/portolan-spec), under `site/`. Change the site there, not here.

## Deploy workflow

[`deploy.yml`](.github/workflows/deploy.yml) checks out `main` of portolan-spec and builds every release from v0.2.0 on, plus the `next` draft from `main`. Each version gets a PDF and an electronic publication (EPUB) download. The workflow checks the output and deploys it to GitHub Pages. It then waits until every version and download returns HTTP 200 on the live domain.

A deploy starts on any of these events:

- A `spec-updated` dispatch, which portolan-spec sends after a push to `main` or a published release.
- A weekly schedule, which catches a dispatch that never arrived.
- A manual run from the Actions tab.

## Repo settings

GitHub stores these settings outside the repo files. Set them once, when you create the repo.

| Setting | Value |
|---|---|
| Pages source | GitHub Actions |
| Pages custom domain | `spec.portolan-sdi.org` |
| Enforce HTTPS | On |
| DNS record | `CNAME spec` → `portolan-sdi.github.io` |
| `github-pages` environment | Deployment branch policy allows `main` |

The dispatch from portolan-spec uses the `portolan-ops-sync` app. The org installs that app on all of its repos, so this repo needs no extra step.

## Contributing

See the org [contributing guide](https://github.com/portolan-sdi/.github/blob/main/CONTRIBUTING.md), including the AI policy.

## License

[Apache-2.0](LICENSE), like every Portolan repo.
