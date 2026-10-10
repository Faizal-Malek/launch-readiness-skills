# Launch Readiness Skills

Go-live agent skills for **production security/performance** and **SEO / discoverability**—separate from UI/UX de-AI taste skills.

**Owner:** [Faizal-Malek](https://github.com/Faizal-Malek) · **License:** MIT

## When to use

| Skill | Invoke | Use when |
| --- | --- | --- |
| [production-readiness](skills/production-readiness/SKILL.md) | `/production-readiness` | Final-phase reviews, PRs, schema migrations, or whole-app go-live (AppSec + performance). **Not** for UI taste or de-AI styling. |
| [seo-audit](skills/seo-audit/SKILL.md) | `/seo-audit` | Before launch, after marketing site changes, or when organic search / social previews matter. **Not** for AppSec or de-AI restyles. |

Complementary UI/UX skills live in [ui-ux-agent-skills](https://github.com/Faizal-Malek/ui-ux-agent-skills) (`/ux-improve`, `/ux-audit`, `/restyle`, …).

## Skills

| Skill | Invoke | Purpose |
| --- | --- | --- |
| [production-readiness](skills/production-readiness/SKILL.md) | `/production-readiness` | Dual-axis security hardening + performance audit (Node, ASP.NET, Python, React, Three.js/R3F, Supabase/Postgres, MongoDB) |
| [seo-audit](skills/seo-audit/SKILL.md) | `/seo-audit` | 20-point SEO / discoverability checklist (sitemap, robots, meta, schema, CWV, OG, Search Console, llms.txt) |

Optional reference media: [media/seo-20-checks.jpg](media/seo-20-checks.jpg).

## Repo layout

```text
.
├── skills/
│   ├── production-readiness/SKILL.md
│   └── seo-audit/SKILL.md
├── media/
│   └── seo-20-checks.jpg
├── LICENSE
└── README.md
```

## Install

### Cursor (user / global)

```bash
git clone git@github.com:Faizal-Malek/launch-readiness-skills.git ~/launch-readiness-skills
mkdir -p ~/.agents/skills ~/.cursor/skills
for s in production-readiness seo-audit; do
  ln -sfn ~/launch-readiness-skills/skills/$s ~/.agents/skills/$s
  ln -sfn ~/launch-readiness-skills/skills/$s ~/.cursor/skills/$s
done
```

### Antigravity (global)

```bash
mkdir -p ~/.gemini/config/skills ~/.gemini/antigravity/skills
for s in production-readiness seo-audit; do
  ln -sfn ~/launch-readiness-skills/skills/$s ~/.gemini/config/skills/$s
  ln -sfn ~/launch-readiness-skills/skills/$s ~/.gemini/antigravity/skills/$s
done
```

### Cursor (project skills)

```bash
REPO=~/launch-readiness-skills
mkdir -p .agents/skills .cursor/skills
for s in production-readiness seo-audit; do
  ln -sfn "$REPO/skills/$s" .agents/skills/$s
  ln -sfn "$REPO/skills/$s" .cursor/skills/$s
done
```

## Clone

```bash
git clone git@github.com:Faizal-Malek/launch-readiness-skills.git
# or
git clone https://github.com/Faizal-Malek/launch-readiness-skills.git
```

## Invoke

In Cursor or Antigravity, ask for the skill by name or slash:

- `/production-readiness` — security + performance go-live audit
- `/seo-audit` — 20-point SEO checklist
