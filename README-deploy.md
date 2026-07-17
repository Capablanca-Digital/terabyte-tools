# terabyte.tools

Static calculators hub, served by Cloudflare Workers (Static Assets). First tool: Backup Retention & Storage Sizing Calculator.

## Deploy

Prerequisites: Node 18+, the `terabyte.tools` zone active in your Cloudflare account.

```bash
npm install -g wrangler        # or: npx wrangler ...
wrangler login
wrangler deploy
```

That's it. `wrangler deploy` uploads `public/` as static assets and binds the custom domains defined in `wrangler.jsonc` (terabyte.tools and www). First deploy may take a minute to provision the domain certificate.

To preview locally before deploying:

```bash
wrangler dev
```

If you prefer to attach the domain from the dashboard instead, remove the `routes` block and use: Workers & Pages → terabyte-tools → Settings → Domains & Routes → Add custom domain.

## Structure

```
public/
  index.html    # self-contained tool: HTML + CSS + vanilla JS, no build step
wrangler.jsonc  # Workers config
```

No framework, no build step, no backend. Each future tool is another folder under `public/` (e.g. `public/subnet-calculator/index.html`), which keeps URLs clean: terabyte.tools/subnet-calculator/.

## Notes

- Everything computes client-side; no analytics or external calls except Google Fonts. Consider self-hosting the fonts later to remove the last external dependency.
- Share links encode inputs in the query string, so results are linkable — useful for forums/Reddit answers, which is free distribution.
- When adding tools, keep one `<h1>` per page with the exact search phrase you target, plus the "How it's calculated" prose section — that text is what ranks, the tool is what retains.
