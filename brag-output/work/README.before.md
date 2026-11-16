# brag-more

**Make your project's GitHub README brag.**

`brag-more` is an agent skill that rebuilds a project's README into a front page worth landing on: an animated SVG hero in the project's own colors and fonts, a looping demo, designed feature cards, honest badges, a one-line pitch, and a quickstart that actually runs. Light and dark mode both look right.

It is a companion to [brag](https://github.com/latent-spaces/brag), which makes the launch video. If you ran `/brag` first, the README uses your video as its demo.

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

## Install

```bash
npx skills add https://github.com/omer-chandna/brag-more --skill brag-more
```

Or copy it by hand:

```bash
rsync -a skills/brag-more/ ~/.claude/skills/brag-more/
```

Restart your agent after copying.

## Credits

Built on [brag](https://github.com/latent-spaces/brag) by Shunit Haviv Hakimi (MIT). See [LICENSE](LICENSE).
