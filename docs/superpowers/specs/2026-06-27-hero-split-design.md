# NewPhant Homepage Hero Split Design

## Goal

Update the homepage first screen so it reads as a two-column personal/research introduction instead of a centered hero followed by a separate profile card.

## Approved Direction

Use option A: balanced split layout.

- Left side: research identity and action area.
- Right side: personal profile card.
- Keep the existing warm Anthropic-like visual language: white/warm paper background, black ink, clay/accent buttons, rounded profile card.

## Content

### Left column

- Badge: `常州工学院 · 人工智能 · 大一在读`
- Main headline: `I Loved And Did A Little Work`
- Body copy: `研究方向为 Agent 与具身智能。相信 AI 不应只是聊天框，而应成为科研、工程和教育中真正可依赖的生产力工具。`
- CTA buttons:
  - `查看项目` links to `#projects`
  - `取得联系` links to `#contact`
- Tags/stats:
  - `Agent` / `科研智能体方向`
  - `具身智能` / `机器人与物理交互`

### Right column

Profile card content:

- Avatar block: `桥`
- Name: `周仕桥`
- School line: `常州工学院 · 人工智能 · 大一`
- Personal line: `喜欢发呆，擅长睡觉，洗澡唱歌，如厕读书。`
- Status tags:
  - `开放实习机会`
  - `科研远程 RA`
  - `开源交流`
- Email: `3584046379@qq.com`

## Implementation Scope

Edit only `index.html` on the NewPhant GitHub Pages `master` branch:

1. Change document title to `I Loved And Did A Little Work`.
2. Update `.hero` / `.hero-inner` CSS to a responsive two-column layout.
3. Move the existing separate profile card markup into the hero right column.
4. Remove the now-empty standalone profile section.
5. Keep existing navigation, project sections, images, and contact/footer unchanged.

## Responsive Behavior

- Desktop/tablet: two columns, left text first and right profile card second.
- Mobile: stack left column above profile card, keep text readable, preserve CTA and tags.

## Verification

- Local static check: no remaining old headline `让 Agent 智能体真正智能。`.
- Local static check: exactly one profile card area remains in hero.
- Deploy to `master` and verify live page contains the new headline and no old standalone centered profile card section.
