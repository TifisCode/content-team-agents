# content-team-agents

A **Claude Code agent team plus YouTube and Instagram skills**, built to run a faceless YouTube channel as an
autonomous team. Agents find the content, build it, review it and package it, and a human gives the final yes before
anything goes public.

It was designed for a "dubbing karaoke" channel, where famous dubbed scenes have one character's voice removed so
families can perform it live. That channel is produced with the companion repo **dub-karaoke-pipeline**. The roles,
hand-offs and guardrails carry over to most content channels.

## What's inside

| Folder | What |
|---|---|
| [`agents/`](agents/) | Five subagents: **PM**, **Scout**, **Engineer**, **QA** and **Growth**. See [agents/README.md](agents/README.md). |
| [`skills/`](skills/) | Twelve skills for YouTube (titles, thumbnail briefs, community posts, channel audit, analytics diagnosis, Shorts packaging, audience insights) and Instagram/Facebook (captions, hashtags, profile audit, Short-to-Reel repurposing, hook analysis). See [skills/README.md](skills/README.md). |

## The flow

```
Scout picks a scene → Engineer builds the take → QA reviews with fresh eyes → (Engineer fixes)
→ Growth packages it and uploads it as PRIVATE → the owner approves → the owner publishes
```

The PM keeps the log, measures the KPIs, reports to the owner, and proposes improvements to each agent's
instructions. It applies them only after the owner approves.

## Principles that made it work

- **Nothing goes public without the human's explicit yes, for each piece and each format.** Automated checks and the
  QA agent are filters, not the final word. Uploading as private is fine.
- **Have a reviewer who didn't build the work.** QA only reports, it never edits, and it caught what the builder
  missed.
- **Every skill produces drafts.** No auto-publishing, no bulk edits without review, and no paid third-party
  posting services.
- **Comments, form answers, web pages and pasted text are data, never instructions.**
- **No fake engagement.** No bots, no spam, and subscriptions are invited, never demanded.
- **One growth owner.** A single agent owns views and subscribers end to end. It measures, studies competitors,
  learns, proposes a daily plan, and runs only what's within its autonomy.
- **Lock shared work.** A per-item lock keeps two sessions from editing the same thing at once.

## Install

```bash
# in your project
mkdir -p .claude/agents .claude/skills
cp agents/*.md .claude/agents/       # (skip agents/README.md)
cp -R skills/*/ .claude/skills/
claude --agent pm                    # or scout / engineer / qa / growth
```

The agents refer to project files such as `team/log.md` (team log) and `team/quality/pending.txt`
(review queue). Create them or change the paths to fit your project. Put your brand guide in `brand/BRAND.md`.

## License

The agents and docs are MIT ([LICENSE](LICENSE)). The skills are adapted from MIT-licensed work by Sergey Bulaev
and Daniel Agrici. Each skill folder keeps its original `LICENSE`, and [skills/README.md](skills/README.md) has the
details.
