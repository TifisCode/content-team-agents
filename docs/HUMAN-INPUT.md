# Giving creative input: a guide for the human

The agents can only be as good as your direction. This page is for **you**, the person who makes the creative calls.
Growth links to it whenever it asks for your input, and the `copy-review` skill applies it to any copy you write.

## The feedback card (30 seconds per option)

When you review options, answer in this shape. Loose feedback works too: Growth converts it into this format and reads
it back to you before acting on it.

```
KEEP 2 · DROP 1 (generic: any channel could post it) · COMBINE 2's hook + 3's ending
On 2, "Ultimate guide" → off-voice: we never promise "ultimate". Direction: name the actual number of steps.
```

1. **Name the option** (1, 2, 3). Options are always numbered.
2. **Point at the exact line, word or area.** "The title" is too broad. "'Ultimate guide' in the title" is actionable.
3. **Name the problem in one word:** *unclear · off-voice · generic · too long · too slow · wrong promise ·
   false · flat*.
4. **Say why, for this viewer.** "Beginners don't know that term" teaches the team something. "I don't like it"
   doesn't.
5. **Give a direction, not a rewrite**, unless you want your exact words used. In that case, write them. Your
   edits are the strongest feedback there is (see below).

## Useless vs. useful feedback

| Instead of… | Say… |
|---|---|
| "Make it pop" | "The title has no number or outcome. Lead with the result." |
| "It doesn't feel right" | "Off-voice: too formal. We talk like a friend, not a manual." |
| "Make it shorter" | "Cut to under 40 characters so it survives on mobile." |
| "Something more creative" | "All three options use curiosity. Give me one that states the benefit plainly." |
| "I don't like the colors" | "Too dark to read at phone size. Use the high-contrast palette from BRAND.md." |

Vague feedback isn't wrong, it's just slow: Growth will come back with a clarifying question that has a recommended
answer ("I read 'make it pop' as 'add a concrete number'. Confirm or override?").

## References: show, don't describe

Before any new format, Growth asks for **3–5 references**. Pick varied ones, not five of the same, and for each
one say:

- **What to take** ("the bold two-word title", "the first line is a question").
- **What not to take** ("not the clickbait arrow", "not the color").

They're kept in `team/creative/references/` so the next brief starts from them instead of from zero.

## Your kill list

When you delete a word or pattern, it goes on the kill list in `brand/BRAND.md`, always with a reason and a
replacement:

| Never | Why | Instead |
|---|---|---|
| "Ultimate", "game-changer" | Overpromise; our viewers distrust hype | The specific result ("in 3 steps") |
| Starting with "Did you know…" | Every channel opens like this | Open with the surprising fact itself |

Build it from what *you* actually cut, not from a generic list of "AI words" (those lists are mostly English and
miss your language's tells).

## Writing copy yourself

When you write the copy (a title, a caption, a post), the team's job changes: it **protects your voice** and only
checks it. The `copy-review` skill:

1. **Diagnoses** what you gave: a blank (build it), a full draft with your voice (keep your words), or a one-line
   change (touch only that line).
2. **Runs the measurable checks:** length, the swap test, missing facts, voice rules, required credits.
3. **Gives you the guidelines that apply**, with at most two optional suggestions, each labeled with the rule
   behind it.
4. **Never rewrites your copy unasked.** Any suggested change it can't justify with a rule gets dropped.

Before you write, the short version of [COPY-GUIDE.md](COPY-GUIDE.md):

- **One viewer, one idea.** Write to one person about one thing.
- **Specific beats clever.** Use a number, a name or a concrete result.
- **The swap test:** if any other channel could post your line unchanged, it's too generic.
- **Lead with the payoff.** The first 40 characters (titles) or 125 (captions) do the work.
- **Read it aloud.** If you stumble, the viewer will too.
- **Don't invent facts.** Leave `[NEED: number of viewers]` and fill it in later.

## Your edits are feedback

When you rewrite something an agent drafted, Growth compares your version with its draft, and the PM logs the
difference in the taste log ("owner replaced 'Ultimate' with '3 steps' → prefers concrete over hype"). You never
have to explain the same preference twice.

---
*Adapted in our own words from: the option/feedback structure in Anthropic's `doc-coauthoring` skill idea;
"confirm or override" questions from TribeAI's brand-voice plugin (MIT); kill lists and copy diagnosis from
coreyhaines31/marketingskills (MIT); and Anthropic's prompting guidance ("explain why"; say what to do, not only what
to avoid).*
