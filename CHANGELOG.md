# Changelog

This repo improves continuously from real use and from your feedback.

## 2026-10-21
- **The creative loop** ([docs/CREATIVE-LOOP.md](docs/CREATIVE-LOOP.md)): agents draft, humans decide taste. It
  covers the split between checks (measurable) and taste (human), the brief → options → checks → human call → taste
  log flow, and a real three-round example.
- **QA logs every check, not only failures:** one row per check in `team/quality/checks.tsv`, with PASS/FAIL and
  the measured value. Passing checks are logged too, so a check that silently stops running shows up in the PM's
  weekly drift check. *Thanks to the replies on X for this one.*
- **Hand-off contracts** ([docs/HANDOFFS.md](docs/HANDOFFS.md)): fixed formats for every file agents pass to each
  other, a validation rule, `BLOCKED:` logging and a troubleshooting table. *Prompted by "the one in the middle is
  the one that breaks".*
- **The agents are niche-neutral:** the five agents no longer assume a specific kind of channel.
- **Skills follow the creative loop:** 2–3 deliberately different options, references first, the taste log read
  before every brief, and the human makes the call.
- **[QUICKSTART.md](QUICKSTART.md) and [examples/](examples/):** templates for every file the agents use, plus a
  first-day walkthrough.
- Issue templates (bug, idea, "how I used it") and [CONTRIBUTING.md](CONTRIBUTING.md).

## 2026-10-20
- First release: 5 Claude Code subagents (PM, Scout, Engineer, QA, Growth) and 12 YouTube/Instagram skills adapted
  from MIT-licensed work by Sergey Bulaev and Daniel Agrici.
