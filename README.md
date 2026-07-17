# stockwise-hub

Personal homepage for Stockwise Productions / bstockwelldev — a single static page linking out to live apps, GitHub repos, and Vercel projects. Built to be set as a browser homepage/new-tab page.

No build step: `index.html` is self-contained (inline CSS/JS, no external dependencies). Deployed as a static site on Vercel.

## Updating the project list

Edit the `PROJECTS` array in `index.html`. Each entry:

```js
{
  name: "Project Name",
  desc: "One-line description.",
  url: "https://project.vercel.app",
  repo: "https://github.com/bstockwelldev/project",
  lang: "TypeScript",
  tags: ["ai", "tabletop", "tools"],
  live: true,
}
```
