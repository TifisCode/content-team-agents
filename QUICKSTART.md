# Quickstart

From zero to your first reviewed piece in about 30 minutes. You need [Claude Code](https://claude.com/claude-code)
and a project folder for your channel.

## 1. Install the agents and skills

```bash
cd your-channel-project
git clone https://github.com/TifisCode/content-team-agents /tmp/cta
mkdir -p .claude/agents .claude/skills
cp /tmp/cta/agents/{pm,scout,engineer,qa,growth}.md .claude/agents/
cp -R /tmp/cta/skills/*/ .claude/skills/
cp -R /tmp/cta/examples/team /tmp/cta/examples/brand .
```

## 2. Make it yours (10 minutes, the important part)

1. **`brand/BRAND.md`:** fill in your palette, fonts, thumbnail formula, voice and the measurable rules QA should
   enforce. This is the file that keeps the team from producing generic content.
2. **Clear out the example rows** in `team/` (queue, log, pending, approved, checks, owner_signoff, taste). Keep
   the headers.
3. **Production tools:** the Engineer builds with whatever lives in `scripts/` (render scripts, an editor CLI,
   templates). Write one paragraph in your `CLAUDE.md` saying how a piece gets built and how to check it.
4. **Your references:** drop 2–3 examples of thumbnails or posts you love into `brand/references/`. Growth asks
   for these before any new creative format.

## 3. Your first day, step by step

```bash
claude --agent scout      # "Fill team/queue.md with 10 ideas for <your niche>, best first, with reasons"
claude --agent engineer   # "Build the top item of the queue and add it to team/quality/pending.txt"
claude --agent growth     # "Write the thumbnail and title brief for <id> with 3 options"
claude --agent qa         # "Review everything in pending.txt and the brief options"
claude --agent pm         # "Show me what's ready for my sign-off"
```

At this point **you** make the creative call: pick an option, say why in one sentence, and approve or ask for
changes. The PM logs your verdict in `team/quality/owner_signoff.tsv` and your reasoning in
`team/creative/taste.md`. Growth uploads as **private**, and you publish.

That's the loop. [docs/CREATIVE-LOOP.md](docs/CREATIVE-LOOP.md) explains why the taste decision stays with you.

## 4. Make it daily (optional)

When the manual day works, schedule one routine per agent. There's an example schedule in
[agents/README.md](agents/README.md#example-daily-routine). Leave publishing out of every routine: it stays your
click.

## When something breaks

Check [docs/HANDOFFS.md](docs/HANDOFFS.md#troubleshooting). Most failures come from a hand-off file that one agent
wrote in a format the next one didn't expect. Agents log those as `BLOCKED:` lines in `team/log.md`.

If it still doesn't work, [open an issue](../../issues/new/choose). Reports of how you used it help as much as bug
reports.
