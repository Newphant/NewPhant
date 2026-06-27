# Homepage Hero Split Update Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Update the NewPhant homepage first screen into the approved balanced two-column hero with research intro on the left and personal card on the right.

**Architecture:** This is a single-file static GitHub Pages site. The change should stay inside `index.html`: adjust hero CSS and replace the separate hero/profile markup with one responsive split hero section. Keep project cards, image assets, contact section, and footer unchanged.

**Tech Stack:** Static HTML/CSS/JavaScript, GitHub Pages on `master` branch.

---

### Task 1: Update hero CSS and markup

**Files:**
- Modify: `C:\Users\ZhuanZ\Desktop\NewPhant\index.html`

- [ ] **Step 1: Capture current references**

Run:

```bash
cd "/c/Users/ZhuanZ/Desktop/NewPhant"
grep -n "让 Agent 智能体真正智能\|PROFILE CARD\|hero-inner\|profile-card" index.html
```

Expected: output includes current hero headline, standalone `PROFILE CARD`, `.hero-inner`, and `.profile-card` references.

- [ ] **Step 2: Edit CSS**

In `index.html`, replace the existing `.hero`, `.hero-inner`, `.hero-badge`, `.hero-subtitle`, `.hero-actions`, `.hero-meta`, `.hero-stat`, and `.hero-stat-*` CSS block with a responsive split-hero block. Add small helper classes for `.hero-copy`, `.hero-profile`, `.profile-avatar`, `.profile-tags`, and `.profile-email`.

- [ ] **Step 3: Edit markup**

Replace the current `<!-- ===== HERO ===== -->` section plus the following standalone `<!-- ===== PROFILE CARD ===== -->` section with one `section.hero` containing:

- left `.hero-copy` with badge, `I Loved And Did A Little Work`, existing Agent/具身 copy, CTA buttons, and two stat chips;
- right `.hero-profile` with `桥`, `周仕桥`, school line, personal sentence, three status tags, and email.

- [ ] **Step 4: Static verification before commit**

Run:

```bash
cd "/c/Users/ZhuanZ/Desktop/NewPhant"
grep -n "I Loved And Did A Little Work" index.html
grep -n "让 Agent 智能体真正智能" index.html || true
grep -n "PROFILE CARD" index.html || true
grep -n "hero-profile\|profile-avatar\|喜欢发呆" index.html
```

Expected:

- new headline appears;
- old headline has no output;
- `PROFILE CARD` has no output;
- new hero profile classes/content appear.

- [ ] **Step 5: Commit and push**

Run:

```bash
cd "/c/Users/ZhuanZ/Desktop/NewPhant"
git add index.html .gitignore docs/superpowers/specs/2026-06-27-hero-split-design.md docs/superpowers/plans/2026-06-27-hero-split-update.md
git commit -m "feat: update homepage hero layout"
git push origin master
```

Expected: commit succeeds and pushes to `origin/master`.

### Task 2: Verify deployment

**Files:**
- Read/verify only: live GitHub Pages URL

- [ ] **Step 1: Verify repository content**

Run:

```bash
gh api repos/Newphant/NewPhant/contents/index.html?ref=master --jq '.content' | base64 -d | grep -n "I Loved And Did A Little Work\|hero-profile\|让 Agent 智能体真正智能" || true
```

Expected: new headline and `hero-profile` appear; old headline does not appear.

- [ ] **Step 2: Verify live content**

Run:

```bash
tmp=$(mktemp)
code=$(curl -LfsS -w '%{http_code}' -o "$tmp" "https://newphant.github.io/NewPhant/?verify=$(date +%s)" || true)
printf 'http=%s\n' "$code"
grep -n "I Loved And Did A Little Work\|hero-profile\|让 Agent 智能体真正智能" "$tmp" || true
rm -f "$tmp"
```

Expected: HTTP 200, new headline and `hero-profile` appear, old headline does not appear.
