# Admin Tools

A single menu for the browser-based tools the Technical Training admin team use.

**Live site:** https://mbtraininguk.github.io/Admin-dashboard/

Every tool runs entirely client-side. The spreadsheets that get loaded into them
are read in the browser and never uploaded anywhere, which is why this repo can
safely be public — and why no data file should ever be committed to it.

## What is here

| Tool | File | Lives |
|------|------|-------|
| Admin tools menu | `index.html` | here |
| T2397D Recertification | `t2397d.html` | here |
| Weekly Course Numbers | `weekly-numbers.html` | here |
| Technician Qualification Compliance | — | [its own repo](https://github.com/MBTrainingUK/Technician-Qualification-Compliance-Tool) |

The Compliance tool stays in its own repo because a direct link to it has already
been circulated and that link has to keep working. The menu links out to it, and
it has a back link in its app bar that returns here.

## This repo is the live version

`t2397d.html` and `weekly-numbers.html` are what the admin team actually open.
The original project folders on the Desktop keep the data, the old versions and
the working history, but editing them no longer changes what anyone sees.

- `t2397d.html` came from `Desktop/Projects/T2397D tool/T2397D Automation v2 3.html`
- `weekly-numbers.html` came from `Desktop/Projects/Weekly numbers tool/Course_Management_Dashboard.html`

To change a tool, edit it **here** and push. If you would rather keep working in
the Desktop folder, copy the result over afterwards and re-apply the back bar —
it is the small `<!-- Back to the admin tools menu -->` block just inside `<body>`.

## Adding a tool

1. Drop the tool's self-contained HTML file in this folder.
2. Add the back bar just inside its `<body>` — copy the block from `t2397d.html`.
   It points at `index.html`, so it works both locally and on Pages.
3. Add one entry to the `TOOLS` array near the bottom of `index.html`:

```js
{
  icon:  "\u{1F4C8}",              // one emoji for the tile
  title: "Name of the tool",
  desc:  "What it tells you, in a sentence or two.",
  feeds: "What the user has to load into it",
  href:  "your-tool.html"          // or a full URL if hosted elsewhere
}
```

The grid, the card layout and the tool count in the footer all build themselves
from that array — there is no other change to make.

A tool hosted in a different repo needs an absolute `href`, and its own back
link should point at `https://mbtraininguk.github.io/Admin-dashboard/` rather
than `index.html`. The Compliance tool is the worked example.

## Theme

The menu and the Compliance tool share one light/dark preference, stored in
`localStorage` under `mbct-theme`. Both are served from `mbtraininguk.github.io`,
so that is a single origin and the setting carries across. Light is the default.
