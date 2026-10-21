# Changelog

This repo improves continuously from real use and from your feedback.

## 2026-10-21 (2): guidance for the human
We looked at the best open-source work on creative AI agents and copy, and adopted what beats ours, in our own
words and with credit.

- **[docs/HUMAN-INPUT.md](docs/HUMAN-INPUT.md), a guide for the person making the calls:** a 30-second feedback
  card (keep / drop / combine, the exact words, a one-word problem, why, a direction), useless vs. useful feedback,
  how to give references, and your own kill list (Never / Why / Instead).
- **[docs/COPY-GUIDE.md](docs/COPY-GUIDE.md):** diagnose before writing (build / polish / point edit), the swap
  test, `[NEED: …]` instead of invented facts, hooks in three non-redundant pieces, titles and thumbnails as a
  pair, a reader test by a fresh agent, seven editing passes. Every rule is marked [check] or [taste].
- **New skill [`copy-review`](skills/copy-review/SKILL.md):** when you write copy, the team checks it and gives you
  the guidelines that apply, with at most two optional changes, each backed by a rule. It never rewrites your
  voice and never scores.
- **The creative loop:** numbered options that differ in their promise; "confirm or override?" questions with a
  recommended answer; your direct edits count as feedback; a reference library in `team/creative/references/`; a
  taste log with evidence (owner verdict vs. A/B result) and status (active / watch / retired).
- **QA:** new measurable copy checks (concrete element, swap test, no `[NEED:` left, kill list, per-surface voice
  rules, the reader test).
- **Fixes:** consistent thresholds (thumbnail text ≤ 4 words, legible at 168 px); removed references to tools we
  don't ship.

**Sources and credit:**
- [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) (MIT): copy diagnosis, swap
  test, `[NEED]`, hook system, editing passes.
- [anthropics/skills](https://github.com/anthropics/skills): the option/feedback structure and reader test of
  `doc-coauthoring` (idea only).
- [TribeAI/claude-cowork-brand-voice-plugin](https://github.com/TribeAI/claude-cowork-brand-voice-plugin) (MIT):
  "We are / We are not" and "confirm or override".
- [efeoncepro/voice.md](https://github.com/efeoncepro/voice.md) (Apache-2.0): per-surface voice rules as checks.
- [blader/humanizer](https://github.com/blader/humanizer) (MIT): AI writing tells.
- Anthropic's prompting best practices.
- YouTube Help on title and thumbnail A/B tests.

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
