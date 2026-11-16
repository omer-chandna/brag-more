---
name: brag-more
description: Turn the current project's GitHub README into a polished, show-off front page — an animated SVG hero in the project's own colors, fonts, and UI, designed feature cards, the brag video or a live demo loop, honest badges, a one-line pitch, real features, a quickstart that actually runs, and light/dark-aware visuals. Use when someone says "/brag-more", "make my README look nice", "brag in the README", "pretty up the GitHub repo", or wants the repository page to look as good as the project.
---

# /brag-more

You built it. Now make the repo brag too. The README is the first thing anyone sees on GitHub; turn it into a front page that sells the project in five seconds and gets a stranger from zero to running it in one minute.

Whatever the project, the result should feel like a README from a well-loved open-source project: confident, scannable, visual, and true. Nothing on the page that doesn't earn its place.

Usage: `/brag-more [options]`. Options (flags or plain language):

| Option | Default |
|---|---|
| `--style clean\|bold\|minimal\|showcase` | inferred from the project (see Styles) |
| `--preview` | off: write `README.md` in place. With it, write only to `brag-output/repo/` and leave `README.md` alone |
| `--no-banner` | banner on |
| `--no-demo` | demo on when there is something to show |

Work files go in `brag-output/repo/` (timestamped `brag-output-YYYY-MM-DD-HHmmss/repo/` if `brag-output/` already exists and isn't from this run). Assets the README references go in the repo, in `.github/readme/`, so they ship with it.

## 1. Inspect

Read the project, not just the old README:

- **The existing README**, every line. It's the user's writing. Keep whatever is true and useful (install steps, config tables, credits, license notes, sponsor links, acknowledgements); restyle it, don't throw it away.
- **Identity:** exact brand colors and fonts from the stylesheets or theme config, the logo or favicon, any existing hero image or OG image.
- **What it is:** package manifests (`package.json`, `pyproject.toml`, `Cargo.toml`, `go.mod`, …) for the name, description, version, license, binaries and scripts; the entry point and main routes or commands for the real features.
- **How to run it:** the actual install and start commands from the manifest scripts, `Makefile`, `justfile`, Dockerfile, or CI workflow. Note the runtime versions the project pins.
- **Signals for badges:** `LICENSE`, `.github/workflows/*`, whether the package is published (npm, PyPI, crates.io — check the manifest's name and `private` flag), the git remote (`git remote get-url origin`) for `owner/repo`.
- **Existing brag output:** if `brag-output*/brag.mp4` and `brag.jpg` exist, they're the best demo material on the machine. Use the newest.

Skip build output, lock files, `.git/`, env and secret files (`.env`, `.env.*`), key and credential material, and anything `.gitignore` excludes for those reasons.

Before writing, answer: What is it (one sentence a stranger gets)? Who is it for? What's the one thing it does better than the alternative? What's the visual hook — the screenshot, GIF, or banner that makes someone stop scrolling? What are the 3–5 real features? What's the shortest path from clone to running?

The README is public. Never carry secrets, tokens, internal hostnames, real customer or user names, email addresses, or other personal data into it or its images. If a screenshot shows such data, swap in plausible fictional stand-ins.

## 2. Plan

Write `brag-output/repo/readme-plan.md`: the one-liner, the chosen style, the section order, which visuals you'll make and what each shows, which badges are justified (and the evidence for each), and what you're keeping from the old README.

**Shape:** a starting shape, not a template. Drop any section that would be empty or padding.

1. **Hero** — the animated SVG hero (see Build), then centered: the one-liner, a short badge row, and a nav line of links (Demo · Install · Docs · …).
2. **Demo** — the product in use, right under the hero, framed: the brag video loop, a GIF of the real UI, or a terminal recording. One visual, big.
3. **Why** — 2–4 sentences: what it does for the user and what sets it apart, in the project's own words. For a developer tool, a 3–5 line code block that *is* the pitch beats a paragraph (`bun run index.tsx  # TS and JSX out of the box`).
4. **Feature showcase** — 3–6 real features, each with its own small visual: a cropped screenshot of the real UI, a per-command terminal GIF, or a code snippet and its output. Lay visual ones out as side-by-side cards (see Build). Text-only features get a bold lead-in and one line.
5. **Quickstart** — copy-pasteable, in order, every command verified against the project. Prerequisites first.
6. **Usage** — one or two real examples: a command and its output, a code snippet, or a config block.
7. **How it works** — optional. A short paragraph or a Mermaid diagram when the architecture is the interesting part.
8. **Everything else from the old README** — configuration, FAQ, roadmap, contributing, credits — tidied, folded into `<details>` when long.
9. **Footer** — license line, plus the closing art strip (see Build).

## README laws

- **True.** Every claim, number, feature, and badge must be backed by the project. No invented stars, downloads, benchmarks, testimonials, or "used by" logos. A badge appears only if what it points to exists (a published package, a real workflow, a license file).
- **Runs.** Every command in Quickstart and Usage exists in the project as written. If you can run it safely (install, build, `--help`, tests), do. If a step needs secrets or a paid service, say so plainly instead of hiding it.
- **Five-second test.** Someone who lands on the repo from a tweet knows what it is, sees it working, and finds the install command without scrolling past the first screen.
- **Show the thing.** The demo shows the real product in use, not a logo animation or abstract art. Reuse real UI, real CSS, real copy.
- **Say what the repo is.** If the repo is the website, landing page, or demo for a product, say so in the one-liner; don't imply people can download an app or install a package that the repo doesn't ship.
- **Specific.** It must feel written for this exact project. "Blazing fast", "seamless", "next-generation", "streamline your workflow" are banned unless the project measurably earns them.
- **Scannable.** Short paragraphs, headings that say something, one idea per bullet. Emoji in headings only if the project's own voice uses them, and then sparingly (the `showcase` style is the exception: one emoji per section heading, by design).
- **Both themes.** GitHub readers use light and dark mode. Every image looks right on `#ffffff` and on `#0d1117`: transparent PNGs with a visible edge, or `<picture>` with a `prefers-color-scheme` source per theme.
- **Fits the column.** The README column is about 830px wide on desktop and much narrower on phones. Banner text stays legible when scaled to phone width; tables have few columns; no wide raw HTML layouts that break on mobile.
- **Every link resolves.** Relative links point at files that exist; anchors match real headings.

## Styles

| Style | Feel | Use when |
|---|---|---|
| `clean` | Animated hero with restrained motion, framed demo, tidy cards | Most projects; the default |
| `bold` | Full-bleed hero in brand colors with a bigger animated moment, punchy one-liner, demo front and center | Consumer apps, playful projects, launches |
| `minimal` | Small animated logo lockup + name + one-liner, plain sections | Libraries, CLIs, infrastructure, serious tools |
| `showcase` | The dense, emoji-sectioned technical README (think a winning hackathon or research project): a real screenshot of the product at the top, an award or status line, then one emoji-led section per topic | Hackathon, research, ML, data, or science projects; anything with real depth to show off. Pick it when the user asks for "something like Find My Shark" or a detailed, documentation-style README |

### The `showcase` recipe

Modeled on the owner's Find-My-Shark README. Keep what makes it work, and fix what doesn't:

- **Title with one emoji and the achievement line** under it ("NASA Space Apps 2025, Galactic Impact Winner"), only if the project really earned it. Ask or read it from the old README; never invent one.
- **A real screenshot or the demo GIF straight under the title**, framed (see Demo, framed). Keep the animated hero only if it adds something; here the real product is the star.
- **A 2-3 line pitch and the "why it matters" line**, then sections each led by one emoji: Features, Region/Scope or Inputs, Data Sources (table), How it works or Mathematical Model, Quick Start (install, basic usage, API usage), Project Structure (annotated tree), Configuration (the real config), Output Files, Command-Line Options, Background, Future Extensions, Testing, Logging, closing tagline.
- Include only sections the project has real content for. Hackathon-grade depth is the point, so keep the specifics: parameters, formulas, thresholds, dataset names, and the project tree.
- **Fix the usual slips:** use the real clone URL (never `your-username`), replace the project-tree code block's stale entries with what exists, add a table of contents or quick-links row once there are more than six sections, wrap long reference sections (CLI options, full config, scientific background) in `<details>`, add badges for the real stack (Python version, license, key libraries) and a `<picture>` or framed screenshot for both themes, and set the repo description and topics at delivery.
- **Anchors with emoji:** GitHub drops the emoji from a heading's slug but keeps the hyphen, so `## 🚀 Quick Start` is `#-quick-start`, not `#quick-start`. Write every nav link and badge link that way and check each one against its heading. The `<details>` summary is not a heading and has no anchor.
- Still follow every README law (True, Runs, Both themes) and the Check step.

## 3. Build

The best READMEs on GitHub (Excalidraw, Scalar, Supabase, Charm, Rich, Bun) share a few moves. Use them all; that's what makes this one stop a scroll.

### The hero: an animated SVG

This is the signature. A static banner reads as a template; a hero that moves — in the project's own colors, fonts, and UI — reads as made for this project. GitHub renders an SVG in an `<img>` tag with its CSS `@keyframes` running, so the hero can animate without a GIF's banding or weight.

Build `.github/readme/hero.svg` (viewBox about 1600×800, rendered at `width="100%"`):

- **The scene is the product.** Recreate the project's real hero or key screen as SVG shapes: its background image, its headline in its own font, and one real UI element doing its job (a card swiping, a command typing, a chart drawing, a toast landing). One idea, one loop.
- **Motion:** CSS `@keyframes` in a `<style>` block inside the SVG, on `transform` and `opacity` only, with `transform-box: fill-box; transform-origin: center` on anything that scales or rotates. A 6–10 s loop that comes back to its start frame seamlessly, entrances staggered, every text line settled long enough to read. Add a slow drift on the background (a 1.0 → 1.05 scale over the loop) so the frame never feels frozen. A CSS `transform` replaces an element's SVG `transform` attribute, so position things with an outer `<g transform=…>` and animate an inner element.
- **Reduced motion:** wrap the keyframes in `@media (prefers-reduced-motion: no-preference)` so readers who opt out see the finished, settled frame. The settled frame must be postable on its own and show the product, so anything that only appears mid-loop (a match overlay, a toast) starts hidden with an `opacity="0"` attribute and is revealed only by its keyframes.
- **Self-contained.** An SVG loaded through `<img>` can't fetch anything: no web fonts by URL, no external images, no scripts. Embed fonts as base64 `@font-face` (Google Fonts' `latin` files are already ~20 KB and can be embedded whole; subset other fonts with `pyftsubset … --text="…" --flavor=woff2`, which needs a recent fontTools), or convert the text to paths. Embed photos as base64 JPEG, resized to what the hero needs. Avoid `<foreignObject>` (Safari won't render it inside `<img>`). Keep the file under ~1.5 MB.
- **Both themes.** If the hero is full-bleed and opaque it works on both; otherwise make `hero-dark.svg` too and swap with `<picture>` or `#gh-dark-mode-only` / `#gh-light-mode-only` URL fragments.
- **Text:** the project name and the one-liner, big (the hero shrinks to ~40% on phones). Nothing else.

```html
<p align="center">
  <a href="<site or demo link>"><img src=".github/readme/hero.svg" alt="<Project> — <one-liner>" width="100%"></a>
</p>
```

Also capture the settled frame at 1280×640 to `.github/readme/social-preview.png` (opaque) for the repo's social card; render the SVG in a headless browser with reduced motion on.

If the project has no visual identity worth animating (a library with no UI), make an animated wordmark instead: the name in a fitting font, one motion that says what it does (a value flowing through a pipe, text being formatted, a test turning green).

### Demo, framed

In order of preference:

1. **The brag video.** If a `brag.mp4` exists, make a looping preview GIF or animated WebP from its strongest 4–8 seconds. Start the clip on a settled, strong frame, not a fade or a dark intro card: the first frame is what shows while the GIF loads (`ffmpeg` with a generated palette: `fps=15,scale=800:-1:flags=lanczos,split[a][b];[a]palettegen[p];[b][p]paletteuse`). Keep it under 5 MB. Save to `.github/readme/demo.gif` and link it to the full video. `brag-output*/` is usually gitignored, so copy the video to `.github/readme/brag.mp4` and link that copy (if it's over ~25 MB, re-encode it smaller; GitHub rejects files over 100 MB). GitHub won't play a repo-relative `.mp4` inline; tell the user they can drag `brag.mp4` into the GitHub README editor to get a playable `user-attachments` URL, and leave a commented placeholder where it goes.
2. **A capture of the real UI.** Run the project locally and record the core flow (entry → key action → result) with a headless browser.
3. **A terminal recording** for CLIs: a scripted session rendered to GIF or SVG with whatever tool is installed (`vhs`, `asciinema` + `agg`, `svg-term`). Script it so it never shows real paths, usernames, or tokens.

Frame it so it sits on the page like a product shot, not a pasted file: bake a device or window frame into the GIF (browser chrome for web apps, a terminal title bar for CLIs) on a brand-colored backdrop, or at least wrap it in `<kbd>` for GitHub's subtle border. Keep the GIF fully opaque, edge to edge: a transparent backdrop or rounded transparent corners stop the encoder from reusing unchanged pixels, and the file grows 20× or more. If none is possible, skip the demo rather than fake one, and suggest running `/brag` first.

### Feature cards

Visual features go side by side, two per row, as images at `width="49%"`. They stay two across on phones, so each card renders about 175px wide there: design for that.

```html
<p align="center">
  <img src=".github/readme/feature-matching.png" alt="Pasture-based matching: …" width="49%">
  <img src=".github/readme/feature-filters.png" alt="Hay preference filters: …" width="49%">
</p>
```

Make each card a designed image, not a raw screenshot: crop the real UI for that feature, set it on a soft brand-colored panel with rounded corners and padding, and put the feature name and one line of copy on the card in the project's font. Same size, same layout, same type for every card so the grid reads as a set. On an 800×600 card, the title is at least 56px and the line of copy at least 30px, or they're unreadable on a phone; keep the visual in the top ~45% so a two-line title never collides with it. An even number of cards fills the grid; with an odd number of features, the project's own testimonial or tagline makes a good last card. Build them as HTML with the project's own CSS, capture on a transparent background, and slice.

### Branded details

Small things that make the page feel designed end to end:

- **Divider:** a thin `.github/readme/divider.svg` (1600×4, a gradient in the brand colors) between major sections instead of the default `<hr>`.
- **Badges in brand colors:** shields.io with `color=<brand hex>`, `labelColor=<dark brand hex>`, and a `logo=` where one exists, `style=flat-square` (or `for-the-badge` for `bold`). At most 5, and only the justified ones from the plan: license, CI status (`github/actions/workflow/status/<owner>/<repo>/<workflow-file>`), published version, runtime requirement, docs or site link. No "made with love", "PRs welcome", or vanity-count badges unless the user asks. Zero is fine when nothing justifies one.
- **Footer strip:** a short closing SVG (`.github/readme/footer.svg`, about 1600×200) that echoes the hero — the brand gradient or background, the tagline, a gentle loop — so the page ends instead of trailing off.
- **Quick links / back to top:** for READMEs longer than about three screens, a nav line under the hero and a `<a href="#readme-top">↑ back to top</a>` after long sections.
- **Community proof only if it's real:** for a public repo with real activity, a contributors grid (`contrib.rocks/image?repo=<owner>/<repo>`) or a star-history chart. Never for a new or private repo.

### GitHub-flavored extras

Use them where they help, not everywhere: `> [!NOTE]` / `> [!TIP]` / `> [!WARNING]` alerts for the one thing people get wrong, `<details>` for long reference material, Mermaid for an architecture diagram, `<kbd>` for keyboard shortcuts, tables for options.

### Write it

Copy the original to `brag-output/repo/README.before.md` before touching anything. Write the new README to `README.md` (or only to `brag-output/repo/README.md` with `--preview`). Match the project's existing Markdown conventions (heading style, list markers, line wrapping).

## 4. Check

- **Links and images:** every relative `src`, `href`, `srcset`, and Markdown link resolves to a file in the repo; every `#anchor` matches a heading's GitHub slug.
- **Commands:** re-read Quickstart against the manifest one more time. Run what's safe to run.
- **Look at it:** render the README the way GitHub does and screenshot it at 830px and 390px wide, in light and in dark (`prefers-color-scheme`). A local renderer is enough: convert it with any GFM-capable Markdown library and wrap it in the `github-markdown-css` stylesheet, or use `gh markdown-preview` if it's installed. Don't send the README to a remote rendering API unless the repo is already public or the user says so. Chrome's `--headless --window-size` won't go narrower than about 500px, so take the phone shot with real device emulation (a Playwright `viewport`, or DevTools device mode) and confirm the page doesn't scroll sideways. Local renderers don't draw GitHub's `> [!NOTE]` alerts, so check those by eye. Fix anything that overflows, collides, or loses contrast on either theme.
- **The hero and footer animate:** open each SVG through an `<img>` tag in a real browser (not directly, where it gets privileges `<img>` doesn't), watch a full loop in real time, and screenshot the settled frame with reduced motion on. Headless Chrome's `--virtual-time-budget` doesn't reliably advance animations inside an `<img>` SVG, so don't judge timing from it. Confirm fonts are the embedded ones, not a fallback, and that the loop has no jump.
- **Weight:** the files in `.github/readme/` together stay under ~10 MB.

## 5. Deliver

- **Tell the user** what changed: the new section order, the visuals you made and where they live, what you kept from the old README, and where the backup is. Show the first screen (hero + demo) as a screenshot if the client can display images. Remind them the animated hero only looks right on GitHub itself, not in editors that preview Markdown without SVG animation.
- **Don't commit or push.** Leave the changes in the working tree for the user to review.
- **Repo metadata** (outward-facing, so offer and wait for a yes): the description, topics, and homepage, as a ready-to-run command:

  ```bash
  gh repo edit <owner>/<repo> --description "<one-liner>" --homepage "<site>" --add-topic <topic> --add-topic <topic>
  ```

  GitHub has no API for the social preview image; tell the user to upload `.github/readme/social-preview.png` under **Settings → General → Social preview**.
- Offer to re-roll the banner, try another style, or run `/brag` to make a demo video if there wasn't one.
