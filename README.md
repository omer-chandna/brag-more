<a id="readme-top"></a>

<p align="center">
  <a href="#demo"><img src=".github/readme/hero.svg" alt="brag-more. Make your README brag. A plain README card turns into a polished one with a hero, badges and feature cards." width="100%"></a>
</p>

<p align="center">
  <strong>An agent skill that rebuilds your GitHub README into a front page worth landing on.</strong><br>
  Animated hero in your project's colors, a framed demo, feature cards, honest badges, a quickstart that runs.
</p>

<p align="center">
  <img alt="MIT license" src="https://img.shields.io/badge/license-MIT-f5a524?style=flat-square&labelColor=0b0f14">
</p>

<p align="center">
  <a href="#demo">Demo</a> ·
  <a href="#features">Features</a> ·
  <a href="#use-it">Use it</a> ·
  <a href="#install">Install</a> ·
  <a href="#credits">Credits</a>
</p>

<img src=".github/readme/divider.svg" width="100%" height="4" alt="">

## Demo

<p align="center">
  <a href="brag-output/brag.mp4"><img src=".github/readme/demo.gif" alt="A plain README for coffeeCart gets one command, /brag-more, and turns into a README with an animated hero, a demo and feature cards. The same skill then rebuilds horse-tinder in two styles." width="100%"></a>
  <br>
  <sub>▶ Click for the full 22-second video with sound. It was made with <a href="https://github.com/latent-spaces/brag">brag</a>, and the README you're reading was made by brag-more.</sub>
</p>

## Features

<p align="center">
  <img src=".github/readme/feature-hero.png" alt="A hero in your colors: an animated SVG with your palette, fonts and UI." width="49%">
  <img src=".github/readme/feature-demo.png" alt="Your video as the demo: run /brag first and the README plays it." width="49%">
  <img src=".github/readme/feature-styles.png" alt="Four styles: clean, bold, minimal, or showcase." width="49%">
  <img src=".github/readme/feature-checked.png" alt="Checked before it ships: links resolve, commands run, nothing invented." width="49%">
</p>

<img src=".github/readme/divider.svg" width="100%" height="4" alt="">

## Use it

```text
/brag-more
/brag-more --style bold
/brag-more --style showcase
/brag-more --preview
```

| Style | Feel |
|---|---|
| `clean` | Animated hero, framed demo, tidy cards. The default. |
| `bold` | Full-bleed hero in brand colors, punchy one-liner. |
| `minimal` | Small animated logo lockup and plain sections. |
| `showcase` | Dense, emoji-sectioned, screenshot-first. Good for hackathon, research and ML projects. |

Your existing README text is kept and restyled. Nothing is committed or pushed. With `--preview` it writes to `brag-output/repo/` and leaves `README.md` alone.

If you ran `/brag` first, the README uses your launch video as its demo. brag-more is a companion to [brag](https://github.com/latent-spaces/brag), which makes the video.

## Install

```bash
npx skills add https://github.com/omer-chandna/brag-more --skill brag-more
```

Or copy it by hand:

```bash
rsync -a skills/brag-more/ ~/.claude/skills/brag-more/
```

Restart your agent after copying.

> [!NOTE]
> The animated hero only plays on GitHub itself. Elsewhere you'll see its first frame.

## What's here

| Path | What it is |
|---|---|
| `skills/brag-more/SKILL.md` | The skill |
| `brag-output/` | This repo's own launch video, plan and share copy |
| `.github/readme/` | The images this README uses, made by the skill |

<p align="center">
  <img src=".github/readme/footer.svg" alt="brag-more. Make your README brag." width="100%">
</p>

## Credits

Built on [brag](https://github.com/latent-spaces/brag) by Shunit Haviv Hakimi (MIT). See [LICENSE](LICENSE).

<p align="right"><a href="#readme-top">↑ back to top</a></p>
