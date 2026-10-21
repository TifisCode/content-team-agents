# The creative loop: agents draft, humans decide taste

This team automates the parts of a channel that can be measured: the queue, renders, loudness, leak checks, title
length, safe zones and upload hygiene. It deliberately does **not** automate taste. Creative work, like titles,
thumbnails, hooks, social copy and promo art, needs a human every time.

That isn't a limitation we're working around. It's the design.

## Why agents can't own taste

Ask a model "is this thumbnail good?" and it almost always says yes. A taste question has no wrong answer, so the
safe verdict is "great". Hand the same model a rule with a way to fail, like "the speech bubble must be readable at
168 px wide" or "nothing in the bottom-right corner", and it starts reporting real failures.

So the work splits cleanly:

| Kind of question | Example | Who answers |
|---|---|---|
| **Check:** it has a measurement and a pass/fail | Title ≤ 100 UTF-16 units, text inside the Shorts safe zone, face larger than 30 % of the frame, −15 LUFS ±1 | **QA agent**, logged in `team/quality/checks.tsv` |
| **Taste:** it has no wrong answer | Which of three thumbnails is more clickable, whether a color palette feels right, whether a joke lands | **The human**, logged in `team/creative/taste.md` |

The rule: **if a check has no measurable way to fail, it isn't a check. It's a taste question, and it goes to the
human.**

## The loop

```
1. BRIEF      Growth writes a brief: goal, one viewer, one idea, constraints, what it must NOT look like.
              New format? Ask the human for 3–5 varied references, each with "take this / not this",
              and store them in team/creative/references/.
2. OPTIONS    Growth drafts 2–3 NUMBERED options that differ on purpose (a different promise, not
              different wording), each with one line on what it tests. Copy follows COPY-GUIDE.md.
3. CHECKS     QA runs the measurable checks on every option (legibility at phone size, safe zones,
              length, swap test, kill list, reader test by a fresh agent). Failures go back before
              the human sees anything.
4. TASTE      The human answers with the feedback card (HUMAN-INPUT.md): keep / drop (why) / combine,
              pointing at exact words. Loose feedback is fine: Growth restates it in that shape and
              asks "confirm or override?" with a recommended answer.
5. ITERATE    Growth applies the feedback. Repeat 2–5 until the human says yes. If the human rewrites
              something, that edit is the feedback: Growth diffs it against its draft.
6. REMEMBER   The PM appends the decision, the reason and the evidence to team/creative/taste.md.
              When the same preference shows up twice, the PM proposes it as a rule in brand/BRAND.md
              (the human approves the rule).
```

Every new brief starts by reading `team/creative/taste.md`, `team/creative/references/` and `brand/BRAND.md`, so
the team doesn't repeat a rejected idea.

**When the human writes the copy**, the loop flips: the agents protect the human's voice and only check it. The
[`copy-review`](../skills/copy-review/SKILL.md) skill diagnoses the input (build, polish or point edit), runs the
measurable checks, shows the 3–5 guidelines that apply and suggests at most two optional, rule-backed changes. It
never rewrites unasked and never scores. Two guides, one for each side:

- [HUMAN-INPUT.md](HUMAN-INPUT.md): for **you**. The feedback card, how to give references, your kill list, and
  writing copy yourself.
- [COPY-GUIDE.md](COPY-GUIDE.md): for **everyone**. The copy principles, each marked [check] or [taste].

## A real example: one promo image, three rounds

This is how the launch image for this repo was made.

**Round 1 (rejected).** The agent generated a polished infographic with an AI image tool: a navy-and-amber palette,
robot avatars and six feature cards. The checks passed (the text was spelled right and readable), but the human's
verdict was *"absolutely horrible, the colors are horrible."* No rubric could have caught that. It was taste.

**What the human added.** Three reference images of posts that work in that space (a dark background, bold title
blocks, a person presenting, tool logos), their own photo, and one creative direction: *"a catchy title about what
the repo is for, technical and specific."*

**Round 2 (approved).** The agent switched tools. It composed the image with code, so the text came out exact and
crisp. It used a black background, a white condensed title with the key phrase in a red band, a warm glow, and the
human's photo cut out on-device. The title was concrete: *"YouTube Marketing Automation with Claude Code"*, plus
real numbers (5 subagents, 12 skills).

**Round 3 (polish).** The human flagged that the photo looked bad (it had been upscaled from a 460 px avatar) and
supplied a high-resolution one. The agent re-cut it, reframed it waist-up and removed a color halo left by the
background.

The launch copy followed the same pattern. The agent drafted the LinkedIn post, the X post and a thread. The human
set the framing, then narrowed the scope: neutral, about the agent team only, nothing about the original niche.

**Who did what:**

| The human brought | The agents brought |
|---|---|
| References, taste, the "no", the final "yes" | Speed, several options, exact text, measurable checks, the edge cleanup nobody wants to do by hand |

The decision went into the taste log, and the style became a reusable rule: *"Repo/LinkedIn art: dark background,
bold technical title, the owner's photo; never a generic AI palette."* The next image starts from there.

## Taste log format (`team/creative/taste.md`)

```markdown
## 2026-10-20 · promo image for LinkedIn/X
- Options: 1 AI infographic (navy/amber) · 2 composed thumbnail-style (black/red/orange + owner photo)
- Verdict: KEEP 2 after one change (HD photo) · DROP 1 (off-brand: "the colors are horrible")
- Why: 2 reads technical and specific
- Applies to: repo and LinkedIn/X art
- Evidence: owner verdict          (or: A/B test, watch-time share 58/42, n = 3,100 impressions)
- Status: active                    (active · watch · retired)
- Rule proposed: repo art = dark background, bold technical title, owner photo → added to BRAND.md (approved)
```

- **Evidence** separates the owner's taste from a measured result. Both count, but a measured result can retire a
  taste rule, and the other way around needs the owner.
- **Status** keeps the log useful: about 20 **active** entries at most. Entries that stop applying move to
  **retired**, they're never deleted. **Watch** is for a preference seen only once.
- **The human's direct edits** are logged too: "owner replaced 'Ultimate' with '3 steps' → prefers concrete over
  hype".

## What this means for each agent

- **Growth** never sends a single creative option to the human, and never sends one that hasn't passed QA's checks.
  It never "improves" copy the human wrote: it runs `copy-review` and suggests at most two changes.
- **QA** grades only what can fail. QA never writes "looks good" about creative work. It writes which checks
  passed, with values.
- **PM** owns the memory: it logs every verdict (and every human edit) with its evidence and status, curates
  `team/creative/references/`, and turns repeated preferences into brand rules once the human approves them. When
  the brand guide is silent or contradicts itself, it asks the human "confirm or override?" with a recommended
  answer.
- **The human** gives direction and the final yes. Nothing creative goes public on the agents' judgment alone.
