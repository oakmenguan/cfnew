# Deployment

This fork deploys the existing Cloudflare Worker `cfnew` from the `main` branch with GitHub Actions.

## Worker deployment

- Production source: `少年你相信光吗` (generated from `明文源吗`)
- Stable CI entry point: `worker.js` (created only inside the GitHub Actions runner)
- Wrangler configuration: `wrangler.toml`
- Repository secrets: `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID`

When `明文源吗` changes, the existing obfuscation workflow regenerates `少年你相信光吗`, deploys it to Cloudflare, and commits the generated file. Direct production-source or Wrangler changes are deployed by `.github/workflows/deploy-cloudflare.yml`.

## Preferred IP reporting

The preferred-IP report file is:

`cloudflare_ips.txt`

Raw URL:

`https://raw.githubusercontent.com/oakmenguan/cfnew/main/cloudflare_ips.txt`

Example yx-tools upload settings:

`-upload github -repo oakmenguan/cfnew -token <FINE_GRAINED_PAT> -path cloudflare_ips.txt`

Give the fine-grained GitHub token access only to this repository and only the Contents read/write permission needed for updating the file. Do not commit Cloudflare credentials or GitHub tokens to this repository.

Updates to `cloudflare_ips.txt` do not trigger a Worker deployment.
