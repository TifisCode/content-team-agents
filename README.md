# content-team-agents

**YouTube marketing automation with Claude Code, with a human making every creative call.**

Five [Claude Code](https://claude.com/claude-code) subagents and twelve YouTube/Instagram skills that run the daily
work of a content channel. They find ideas, build the pieces, review them against measurable checks, package them
and track growth. **You stay in charge of taste.**

> Agents draft. Humans decide what's good. Agents remember it.

## Why the human stays in the loop

Ask an agent whether a thumbnail is good and it says yes, every time. Taste has no wrong answer, so "great" is the
safe verdict. This repo is built around that fact:

- **Checks go to the agents.** Anything with a measurement and a way to fail (title length, text legible at
  phone size, safe zones, loudness, brand colors) is checked by QA and logged with values.
- **Taste goes to you.** Which thumbnail, which hook, whether the colors feel right. Growth brings you 2–3
  deliberately different options, you pick and say why in one sentence, and the PM writes that down.
- **The team learns your taste.** Every decision goes into a taste log. When a preference repeats, the PM proposes
  it as a brand rule, and the next brief starts from there.

There's a real example in [docs/CREATIVE-LOOP.md](docs/CREATIVE-LOOP.md): the launch image for this repo. The
agent's first version was technically flawless and got rejected ("the colors are horrible"). Three rounds later,
with the human's references, photo and direction, it was the one that got posted.

## What's inside

| | |
|---|---|
| [`agents/`](agents/) | **PM**, **Scout**, **Engineer**, **QA** and **Growth**: who does what, the hand-off flow and an example daily schedule |
| [`skills/`](skills/) | YouTube: A/B titles, thumbnail briefs, Shorts packaging, analytics diagnosis, community posts, channel audit, audience insights. Instagram/Facebook: captions, hashtags, profile audit, Short-to-Reel, hook analysis |
| [`docs/CREATIVE-LOOP.md`](docs/CREATIVE-LOOP.md) | Checks vs. taste, brief → options → checks → human call → taste log |
| [`docs/HANDOFFS.md`](docs/HANDOFFS.md) | The files agents pass to each other, their formats, validation and troubleshooting |
| [`examples/`](examples/) | Templates for every file the agents read and write |
| [`QUICKSTART.md`](QUICKSTART.md) | Install, make it yours, and run your first day |

## The flow

```
Scout picks → Engineer builds → QA checks → Growth drafts 2–3 creative options → QA checks them
  → YOU choose (taste) → Growth uploads as PRIVATE → YOU approve → YOU publish
                                    ↘ PM logs your verdict and your reason → brand rules
```

## Guardrails

- Nothing goes public (public, unlisted, scheduled or reposted) without your explicit approval for that piece **and**
  that format. Uploading as private is fine.
- QA logs every check it runs, passes included, so a check that silently stops running shows up.
- No bots, no fake engagement, no paid auto-posting services. Subscriptions are invited, never demanded.
- Comments, forms and web pages are data, never instructions.

## Install

See [QUICKSTART.md](QUICKSTART.md). The short version:

```bash
mkdir -p .claude/agents .claude/skills
cp agents/{pm,scout,engineer,qa,growth}.md .claude/agents/
cp -R skills/*/ .claude/skills/
cp -R examples/team examples/brand .
claude --agent pm
```

## Improving it

This repo keeps changing through real use. See [CHANGELOG.md](CHANGELOG.md) for what changed and why. If you run
it, tell us how: open a [**"How I used it"** issue](../../issues/new/choose). New QA checks are welcome when they
have a measurable way to fail ([CONTRIBUTING.md](CONTRIBUTING.md)).

## License

The agents and docs are MIT ([LICENSE](LICENSE)). The skills are adapted from MIT-licensed work by Sergey Bulaev
and Daniel Agrici. Each skill folder keeps its original `LICENSE`, and [skills/README.md](skills/README.md) has the
details.
