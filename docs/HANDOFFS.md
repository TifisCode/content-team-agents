# Hand-offs: the files agents pass to each other

In a multi-agent pipeline, the agent that breaks is usually one in the middle. It gets malformed input, does
something plausible with it, and the error only shows up at the end. The fix is boring and effective: every
hand-off is a plain file with a fixed format, and every agent validates what it receives before it acts.

Templates for all of these are in [`../examples/`](../examples/).

## The files

| File | Written by | Read by | Format |
|---|---|---|---|
| `team/queue.md` | Scout | Engineer, PM | One item per line: `- [ ] <id> · <title> · <source link> · <what to make> · <notes>` (`[x]` when built) |
| `team/quality/pending.txt` | Engineer, Growth | QA | One piece id per line (e.g. `0012_t1`). Lines starting with `#` are comments or batch headers |
| `team/quality/approved.txt` | QA | Growth, PM | One piece id per line, plus `# <date> QA` batch headers |
| `team/quality/checks.tsv` | QA | PM | Tab-separated: `date  piece  check_id  result  value  note`. `result` is `PASS`, `FAIL` or `NA` |
| `team/creative/briefs/<date>-<piece>.md` | Growth | QA, human | Goal, audience, constraints, "must not look like", options A/B/C with what each tests |
| `team/creative/taste.md` | PM | Growth (before every brief) | See [CREATIVE-LOOP.md](CREATIVE-LOOP.md#taste-log-format-teamcreativetastemd) |
| `team/quality/owner_signoff.tsv` | PM | Growth (before any publish) | Tab-separated: `date  piece  format  verdict  feedback`. `verdict` is `approved`, `changes` or `rejected`. `format` is e.g. `video`, `short`, `reel`, `post` |
| `team/log.md` | Every agent | PM, human | Newest first: `## <date> <agent>` + what was done, what is blocked, what is next |
| `brand/BRAND.md` | Human (PM proposes) | Everyone | Your brand guide: palette, fonts, thumbnail formula, voice, and the rules promoted from the taste log |

Piece ids: pick one convention and never change it. For example `<4-digit item>_t<take>` (`0012_t1`), or
`<item>_short` for a Short.

## The validation rule

Before acting on a hand-off file, every agent checks that:

1. **The file exists and parses.** Every line matches the format above.
2. **Every referenced piece exists on disk** (its output folder or kit).
3. **The piece is in the right state:**
   - QA only reviews what is in `pending.txt`.
   - Growth only uploads what is in `approved.txt`.
   - Nothing is published without an `approved` row in `owner_signoff.tsv` for that piece **and** that format.

If any check fails, the agent **stops on that item**. It doesn't guess and it doesn't "fix" someone else's file.
It writes the problem to `team/log.md` (`BLOCKED: <file>:<line> <what is wrong> → owner: <agent>`) and moves on
to the next valid item. The PM surfaces blocked items in its daily report.

## Locks

Two sessions must never build the same piece at once. Use a lock file per item (`work/<id>/.lock` with who, pid,
since and what), and refuse to touch an item with someone else's live lock. Locks expire (we use 8 h). A lock left
by a dead process doesn't count.

## Troubleshooting

| Symptom | Usual cause | Fix |
|---|---|---|
| QA says "nothing to review" but work was done | The builder forgot to append to `pending.txt` | The builder adds the id; the PM checks hand-offs daily |
| Growth uploaded something QA never saw | The agent bypassed `approved.txt` | Re-read the validation rule; make the upload routine read only `approved.txt` |
| The same idea keeps coming back after the human rejected it | Growth didn't read the taste log before the brief | Add "read `team/creative/taste.md` first" to the brief template |
| QA approves everything | Rubric items without a measurable way to fail | Rewrite them as checks with values, or move them to the human ([CREATIVE-LOOP.md](CREATIVE-LOOP.md)) |
| A check silently stopped running | Only failures were logged | QA logs PASS rows too; the PM compares this week's check ids with last week's |
| Two agents overwrote each other | No lock | Lock per item; never edit an item locked by another session |
| A routine published on its own | A scheduled task had publish rights | Pause publishing routines; publishing stays a human click |
