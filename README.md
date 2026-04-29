# Branding5 Agent Skills

Free, open-source AI agent skills from [Branding5](https://www.branding5.com).

---

## Skills

### 📐 social-media-image-sizes

> Check and resize images for every major social media platform.

Validates image dimensions against 60+ specs across Instagram, Facebook, X (Twitter), LinkedIn, TikTok, YouTube, Pinterest, Snapchat, and Threads. Outputs a ranked match list and generates correctly-sized exports via [sharp](https://sharp.pixelplumbing.com/).

**Install:**

```bash
npx skills add Branding5/agent-skills@social-media-image-sizes
```

**Use when a user asks:**
- *"Is this image the right size for Instagram?"*
- *"Resize this photo for a LinkedIn banner"*
- *"What size should my YouTube thumbnail be?"*
- *"Prep these assets for Facebook ads"*
- *"Check if my image fits the TikTok spec"*

**Check an image:**

```bash
node scripts/check.js photo.jpg
```

```
────────────────────────────────────────────────────────────
  📐  photo.jpg
      1200 × 900 px  (1.33:1)  •  842 KB
────────────────────────────────────────────────────────────

  ✅  PERFECT
     Facebook     Feed Posts     Image Post (Landscape)   1200×630    1.91:1

  🟡  CLOSE (scale only)
     LinkedIn     Feed Posts     Image Post (Landscape)   1200×627    1.91:1
     X (Twitter)  Posts          Single Image             1600×900    16:9

  🔄  USABLE (will crop)
     Instagram    Feed Posts     Portrait Post            1080×1350   4:5    → node scripts/resize.js photo.jpg "Instagram Portrait Post"
     Instagram    Feed Posts     Square Post              1080×1080   1:1    → node scripts/resize.js photo.jpg "Instagram Square Post"

  ❌  TOO SMALL
     YouTube      Channel Art    Banner                   2560×1440   16:9

────────────────────────────────────────────────────────────
  ✅ 1 perfect   🟡 2 close   🔄 12 usable   ❌ 8 too small
  Full reference → branding5.com/tools/social-media-cheat-sheet
────────────────────────────────────────────────────────────
```

**Resize to a named spec:**

```bash
node scripts/resize.js photo.jpg "Instagram Portrait Post"
# → photo-instagram-portrait-post.jpg  (1080×1350 px, center-crop)

node scripts/resize.js photo.jpg "LinkedIn Background Photo" --fit contain --bg f0f0f0
# → letterboxed with light grey padding

node scripts/resize.js photo.jpg --list   # show all 60+ spec names
```

**Platforms covered:**

| Platform | Specs |
|----------|-------|
| Instagram | Profile, Feed (portrait/square/landscape), Stories, Reels, Carousel, Ads |
| Facebook | Profile, Cover, Feed, Stories, Reels, Events, Groups, Ads |
| X (Twitter) | Profile, Header, Posts, Cards, Ads |
| LinkedIn | Profile, Background, Company, Feed, Articles, Newsletters, Ads |
| TikTok | Profile, Videos, Ads |
| YouTube | Profile, Banner, Thumbnails, Shorts, Community, Ads |
| Pinterest | Profile, Boards, Standard/Square/Long/Idea Pins, Ads |
| Snapchat | Snaps, Spotlight, Stories, Ads, Filters/Lenses |
| Threads | Profile, Posts |

→ [View skill](./social-media-image-sizes/SKILL.md) · [Full reference](./social-media-image-sizes/AGENTS.md) · [Interactive tool](https://www.branding5.com/tools/social-media-cheat-sheet)

---

## Structure

Each skill lives in its own directory:

```
<skill-name>/
├── SKILL.md          # Frontmatter + agent instructions
├── AGENTS.md         # Full compiled reference (single-file context)
├── scripts/          # Executable tools
├── references/       # Per-platform detail, loaded on demand
└── package.json      # Dependencies (if any)
```

## Installation

Install a single skill:

```bash
npx skills add Branding5/agent-skills@social-media-image-sizes
```

Install globally so it's available in every project:

```bash
npx skills add Branding5/agent-skills@social-media-image-sizes -g
```

## Contributing

Bug reports and pull requests welcome. If a platform updates its specs, open an issue or PR against the relevant file in `social-media-image-sizes/references/` and `scripts/platform-data.js`.

## License

MIT — free to use, fork, and redistribute.

---

*Skills built alongside [Branding5](https://www.branding5.com) — AI brand positioning and marketkng strategy *
