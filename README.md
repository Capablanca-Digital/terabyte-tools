# terabyte.tools

Free, client-side calculators for people who run infrastructure. Live at **[terabyte.tools](https://terabyte.tools)**.

Built by a working backup and infrastructure engineer who got tired of two things: vendor sizing tools that are lead capture forms in disguise, and independent calculators that were last updated in 2010.

## The tools

| Tool | What it answers |
|------|-----------------|
| [Backup retention & sizing](https://terabyte.tools/backup-retention-calculator/) | How much backend storage a GFS retention scheme really needs over 5 years, with three dedup models: global, per copy, raw |
| [Subnet calculator](https://terabyte.tools/subnet-calculator/) | Network, broadcast, host range and wildcard for any IPv4 CIDR, with the binary laid out bit by bit, plus VLSM splitting |
| [RAID & ZFS capacity](https://terabyte.tools/raid-calculator/) | Usable space, fault tolerance and the probability of hitting a URE during rebuild, for RAID 0/1/5/6/10 and RAIDZ1/2/3 |
| [Backup window & bandwidth](https://terabyte.tools/backup-window-calculator/) | How long a transfer takes on a real link, and what bandwidth fits your window |
| [Kubernetes sizing](https://terabyte.tools/kubernetes-sizing-calculator/) | Worker nodes needed from pod requests, system reserves and N+1 failover |
| [VM consolidation](https://terabyte.tools/vm-consolidation-calculator/) | Hosts needed for a VM fleet at any vCPU overcommit ratio. RAM is never overcommitted on purpose |
| [Cloud vs on-prem TCO](https://terabyte.tools/cloud-vs-onprem-calculator/) | Monthly and 5-year cost comparison where every rate is editable, because hardcoded prices go stale |

## Principles

- **Everything runs in your browser.** No accounts, no tracking, no cookies of our own. The numbers you type never leave your machine.
- **Every result is a shareable URL.** Drop an exact scenario into a ticket, a design doc or a forum answer.
- **The models are honest about their limits.** Each page has a "How it's calculated" section that documents the formula and, just as important, what it deliberately ignores.
- **No build step.** Plain HTML and vanilla JavaScript. View source and you see everything.

## Run it yourself

There is nothing to build. Clone and open any `public/*/index.html` in a browser, or serve the `public/` folder with anything that serves static files:

```bash
git clone https://github.com/Capablanca-Digital/terabyte-tools.git
cd terabyte-tools
python3 -m http.server -d public 8080
```

The production site runs on Cloudflare Workers static assets. With your own Cloudflare account and `wrangler.jsonc` adjusted to your domain, `npx wrangler deploy` publishes the whole thing.

## Found a problem with the math?

That is the most valuable issue you can open. Each model is a simplification and some simplifications are wrong in ways only practitioners notice. Open an issue with the scenario and the number you expected, and it gets fixed.

## License

MIT. See [LICENSE](LICENSE).
