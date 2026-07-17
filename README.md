# stockwise-hub

Personal homepage for Stockwise Productions / bstockwelldev — a single static page linking out to pinned tools, live apps, GitHub repos, and Vercel projects. Built to be set as a browser homepage/new-tab page, with an optional PWA install.

No build step: `index.html` is self-contained (inline CSS/JS, no external dependencies besides the Google favicon proxy). Deployed as a static site on Vercel.

Design record: [`docs/design/stockwise-hub-v2-plan.md`](docs/design/stockwise-hub-v2-plan.md) (locked SPEC — read this before making structural changes).

## Updating the data

Edit the `ITEMS` array in `index.html`. Each entry:

```js
{
  id: "kebab-case-id",       // stable — pins are stored against this
  type: "app" | "tool" | "project",
  name: "Project Name",
  desc: "One-line description.",  // omit for type "tool"; use `label` instead
  label: "Short label",           // type "tool" only, e.g. "Deployments"
  url: "https://project.vercel.app",
  repo: "https://github.com/bstockwelldev/project",  // omit for type "tool"
  domain: "project.vercel.app",   // drives the favicon
  lang: "TypeScript",
  tags: ["ai", "tabletop", "utility"],
  live: true,
}
```

- `app` — flagship project: shown in both the Tools row (green accent) and the Projects grid.
- `tool` — platform dashboard (GitHub, Vercel, Supabase, ...): Tools row only (blue accent), no repo link.
- `project` — Projects grid only.

Renaming or removing an `id` that's currently pinned in someone's browser is harmless — pins are pruned automatically against the live `ITEMS` list on next load.

## Deploy discipline

**Important:** this Vercel project is not git-linked. Every change requires
two steps, or the live site and the repo will drift:

1. Commit and push to `bstockwelldev/stockwise-hub`.
2. Redeploy to Vercel production (currently done via a one-off file upload,
   not an automatic git-triggered build).

To remove this footgun permanently, import the repo at
[vercel.com/new](https://vercel.com/new) and pick `bstockwelldev/stockwise-hub`
— that enables auto-deploy on push and step 2 goes away. This is a one-time
setup that needs the repo owner's own GitHub OAuth approval in the browser.
