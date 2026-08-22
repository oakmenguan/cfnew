# Deployment

This fork deploys the `cfnew` Worker from the `main` branch through Cloudflare Workers Builds.

- Worker entry file: `明文源吗`
- Wrangler configuration: `wrangler.toml`
- Preferred IP report file: `cloudflare_ips.txt`
- `cloudflare_ips.txt` is excluded from Cloudflare build watch paths so IP refreshes do not redeploy Worker code.

The Worker can read the latest preferred-IP list from:

`https://raw.githubusercontent.com/oakmenguan/cfnew/main/cloudflare_ips.txt`

Do not commit Cloudflare credentials or GitHub tokens to this repository.
