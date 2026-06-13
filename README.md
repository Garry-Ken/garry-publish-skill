# md2wechat — WeChat Article Formatting Skill

Markdown → WeChat Official Account HTML converter, installable as a skill for Claude Code, Codex, WorkBuddy, and other AI agent tools.

11 built-in themes, syntax highlighting with macOS traffic light dots, tables/lists/images fully compatible with WeChat's editor.

## Install

```bash
npx skills add Garry-Ken/garry-publish-skill -g
```

## Usage

In Claude Code (or any compatible agent):

```
/md2wechat path/to/article.md
/md2wechat path/to/article.md claude
```

The converted HTML is copied to your clipboard — paste directly into the WeChat Official Account editor.

## Themes

| ID | Name | Style |
|---|---|---|
| `apple` | Mac Minimal (default) | Clean, modern, generous whitespace |
| `claude` | Claude Oat | Warm oat background, great for long reads |
| `wechat` | WeChat Native | Official account default style |
| `media` | NYT | Classic news typography |
| `stripe` | Stripe | Tech-minimal |
| `linear` | Linear Dark | Dark theme for developers |
| `notion` | Notion | Clean note-taking style |
| `github` | GitHub Docs | Developer documentation style |
| `dracula` | Dracula | Classic dark color scheme |
| `sakura` | Sakura Pink | Soft pink palette |
| `cyberpunk` | Cyberpunk | Neon futuristic |

## Web Version

A full UI version with live preview is available at [garry-publish.vercel.app](https://garry-publish.vercel.app).

## License

MIT
