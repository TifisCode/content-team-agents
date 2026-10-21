# Copy guide: titles, hooks, captions and posts

Best practices the agents follow when they draft copy, and that the `copy-review` skill shows you when you write it
yourself. Every rule is marked **[check]** (QA can measure it: pass or fail) or **[taste]** (your call).

## 1. Diagnose before writing

| What came in | Mode | What the agent does |
|---|---|---|
| Nothing, or a topic | **A · Build** | Draft 2–3 deliberately different options |
| A full draft in the owner's voice | **B · Polish** | Keep the owner's words. Fix only what fails a check, and suggest at most two changes |
| "Change this one line" | **C · Point edit** | Touch that line only |

**Leave-it-alone test:** any change the agent can't tie to a rule in this guide or in `BRAND.md` gets undone.

## 2. Principles

1. **One viewer, one idea.** Picture one specific person. Each piece makes one promise. **[taste]**
2. **Specific beats clever.** Use a number, a name, a result or a time. "3 lighting mistakes" beats "Lighting tips
   you need". **[check]:** the line contains at least one concrete element (number, name, result).
3. **Swap test.** If a rival channel could post the line unchanged, it fails. **[check]:** a fresh agent is asked
   "could a different channel in this niche post this as is?"
4. **Lead with the payoff.** The key phrase goes in the first ~40 characters of a title and the first 125 of a
   caption. **[check]**
5. **Use the viewer's words.** Take phrases from comments and questions (voice of the customer), not marketing
   language. **[taste]**, informed by the comments the team collected.
6. **Never invent facts.** Mark gaps as `[NEED: …]`. **[check]:** no `[NEED:` remains in anything sent for
   approval.
7. **Voice comes from BRAND.md**, including "We are / We are not" and the kill list. **[check]:** no kill-list item
   appears.
8. **Read it aloud.** **[taste]**: the owner's ear decides.

## 3. Hooks (Shorts, Reels, first seconds)

Write the hook as **three separate pieces** that don't repeat each other:

| Piece | Job | Example |
|---|---|---|
| **Picture** (first frame) | Show the payoff or the problem | The finished result, on screen at 0:00 |
| **Spoken line** | Make the claim | "Most people light from the wrong side." |
| **On-screen text** | Add what the voice doesn't say | "Fix it in 10 seconds ↓" |

**[check]:** the on-screen text isn't a transcript of the spoken line.

## 4. Titles and thumbnails work as a pair

- The thumbnail text and the title **don't repeat each other**. Together they tell one story. **[check]**
- Thumbnail text: **4 words or fewer**, legible at **168 px** wide. **[check]**
- Title ≤ 100 UTF-16 units (emoji count as 2). Key phrase in the first ~40 characters. **[check]**
- **Reader test:** a fresh agent with no context reads only the title and thumbnail text and describes the video
  it expects. A mismatch with the brief fails. **[check]**
- When A/B testing, options should differ on purpose (different promise, not different wording). YouTube's Test &
  Compare picks winners by **watch-time share**, not CTR, so judge and log results that way.

## 5. Editing passes

Before copy goes to QA, the drafting agent re-reads it once per pass:

1. **Clarity:** could a new viewer understand it in one read?
2. **Voice:** does it sound like BRAND.md, and is nothing from the kill list in it?
3. **So what?** Does every line give the viewer a reason to care?
4. **Proof:** is every claim backed up, or marked `[NEED: …]`?
5. **Specificity:** replace one vague word with a concrete one.
6. **Rhythm:** read it aloud and cut what you stumble on.
7. **Zero risk:** no misleading promise, no clickbait the video doesn't deliver.

## 6. What QA never does

QA never scores copy ("8/10", "strong hook"). It runs the **[check]** items and logs each one in
`team/quality/checks.tsv`. Everything marked **[taste]** goes to the owner, using the feedback card in
[HUMAN-INPUT.md](HUMAN-INPUT.md).

---
*Adapted in our own words from coreyhaines31/marketingskills (MIT: copy diagnosis, the swap test, `[NEED]`
markers, the hook system and editing passes inspired by "Seven Sweeps"); efeoncepro/voice.md (Apache-2.0:
per-surface voice rules as lintable tokens); blader/humanizer (MIT: removing AI writing tells); YouTube Help on title
and thumbnail A/B tests; and Anthropic's prompting best practices.*
