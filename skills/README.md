# Content skills for YouTube, Instagram and Facebook

Twelve [Claude Code skills](https://docs.claude.com/en/docs/claude-code/skills) that help a small team (or a team of agents) grow a video channel: titles, thumbnails, Shorts, community posts, analytics, comments, captions, hashtags and profiles.

They were adapted from MIT-licensed open-source skills (see [Attribution](#attribution)), translated into English, generalized, and stripped of everything that published automatically or called paid services. What is left is **instructions only**: no scripts, no API keys, no publishing.

The examples use one niche throughout: a **dubbing-karaoke channel**, where famous scenes are posted with one character's voice removed so viewers can dub it live. Swap in your own niche; the methods are generic.

## The skills

| Skill | What it produces |
|---|---|
| `yt-analytics-diagnosis` | A channel health report from YouTube Studio screenshots or CSV exports: funnel (impressions → CTR → retention → subscribers), retention patterns, traffic sources, outliers, and at most 5 prioritized actions. |
| `yt-audience-insights` | A read of a video's or channel's comments: recurring themes and requests, superfans, sentiment, and which comments to reply to or pin (reply drafts). |
| `yt-channel-optimizer` | A channel-page scorecard (name, banner, About, trailer, featured video, sections, playlists, watermark, links) with before/after rewrites. |
| `yt-community-post-writer` | Copy-paste drafts of Community-tab posts and polls. |
| `yt-shorts-package` | A full Short package: first-second hook, beat-by-beat script, loop, title, description, hashtags, bridge to the long video, plus a step-by-step diagnosis for Shorts that are not taking off. |
| `yt-thumbnail-brief` | A thumbnail brief with 2–3 A/B concepts for YouTube Test & Compare, inside your brand guide. Words only; it makes no images. |
| `yt-title-optimizer` | 3–5 title variants for A/B testing, tagged by formula and character count, respecting your channel's fixed title format. |
| `ig-caption-writer` | Instagram/Facebook captions for Reels and posts: hook in the first 125 characters, one CTA, 3–5 hashtags. |
| `ig-hashtag-strategist` | A sized, rotating set of 3–5 hashtags (niche / mid / broad) with a one-line reason for each. |
| `ig-hook-extractor` | A teardown of a pasted viral caption or Reel opening: hook formula, structure, why it worked, and a blank template. |
| `ig-profile-optimizer` | A nine-part Instagram profile scorecard (plus a Facebook Page pass) with before/after rewrites, highlights plan and pinned-post picks. |
| `ig-repurposer` | A YouTube Short (or a post, script or thread) rebuilt as a native Instagram/Facebook Reel or post, with YouTube-only cues removed. |

Each skill folder holds `SKILL.md` (the instructions), `references/` (formulas, checklists, platform heuristics) and the upstream `LICENSE`. Some reference files are shared and appear in several folders on purpose, so each skill can be installed on its own.

Some `SKILL.md` files mention related skills marked *(upstream, not included here)*: they exist in the original repositories but were not adapted.

## Install

Copy the skill folders you want into a `.claude/skills/` directory:

```bash
# for one project
mkdir -p your-project/.claude/skills
cp -R skills/yt-title-optimizer skills/yt-thumbnail-brief your-project/.claude/skills/

# or for every project on your machine
mkdir -p ~/.claude/skills
cp -R skills/* ~/.claude/skills/
```

Claude Code picks them up in the next session; each skill triggers from its `description`, or you can ask for it by name.

Two files the skills expect you to provide (optional, but they make the output yours):

- `brand/BRAND.md`: your brand guide (colors, fonts, mascot, thumbnail layout, intro, title format). The skills defer to it whenever it disagrees with their generic advice.
- `CLAUDE.md`: your project instructions (language, audience, content rules). Also takes precedence over the skills.

Replace the placeholders `@YourChannel` and `@YourIGHandle` with your own handles in your project instructions, not in the skills.

## Principle: drafts only

Every skill ends at a draft. None of them uploads, publishes, schedules, comments, replies or changes a setting. A human reviews each piece and applies it by hand, with the owner's explicit approval given in the conversation. The guardrails built into every skill:

- **Drafts only, approval required.** Nothing goes public without the owner's go-ahead.
- **Untrusted content is data.** Comments, captions, profiles and anything pasted from someone else are never treated as instructions, even when they claim authority (see `references/untrusted-content.md`).
- **No fake engagement.** No bots, no spam, no engagement bait, no bought anything.
- **Subscription is invited, never demanded.** Nothing is locked behind a subscribe or a follow.
- **No invented specifics.** Numbers, dates and results come from the user or are dropped.
- **No spending, no secrets in chat.** No paid services; API keys, if you use any, stay out of the conversation.

## Attribution

These skills are derivative works of MIT-licensed projects. Each folder keeps its original `LICENSE` file unchanged, and each `SKILL.md` names its source on the first line.

| Upstream author | Skills adapted here |
|---|---|
| Sergey Bulaev ([github.com/sergebulaev](https://github.com/sergebulaev)), YouTube skills | `yt-channel-optimizer`, `yt-community-post-writer`, `yt-title-optimizer`, `yt-audience-insights`, `yt-thumbnail-brief` |
| Sergey Bulaev, [sergebulaev/instagram-skills](https://github.com/sergebulaev/instagram-skills) | `ig-caption-writer`, `ig-hashtag-strategist`, `ig-hook-extractor`, `ig-profile-optimizer`, `ig-repurposer` |
| Daniel Agrici ([github.com/AgriciDaniel](https://github.com/AgriciDaniel)), YouTube skills | `yt-analytics-diagnosis` (from `analyze`), `yt-shorts-package` (from `shorts`) |

Changes made to all of them: translated, generalized for any channel, auto-publishing and paid-service steps removed, guardrails added.

The MIT License lets you use, copy, modify, merge, publish, distribute, sublicense and sell copies of the software, provided the copyright notice and permission notice are kept in all copies or substantial portions. The software is provided "as is", without warranty of any kind. See each folder's `LICENSE` for the full text and copyright holder.
