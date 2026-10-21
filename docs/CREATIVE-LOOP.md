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
1. BRIEF      Growth writes a brief: goal, audience, constraints, what it must NOT look like.
              New format? Ask the human for 2–3 reference examples first.
2. OPTIONS    Growth drafts 2–3 options that differ on purpose (not three variations of one idea), each with
              one line on what it is testing.
3. CHECKS     QA runs the measurable checks on every option (legibility at phone size, safe zones,
              length, brand colors, typos). Failures go back before the human sees anything.
4. TASTE      The human picks, rejects or redirects, with one sentence on why.
5. ITERATE    Growth applies the feedback. Repeat 2–5 until the human says yes.
6. REMEMBER   The PM appends the decision and the reason to team/creative/taste.md. When the same
              preference shows up twice, the PM proposes it as a rule in brand/BRAND.md (the human
              approves the rule).
```

Every new brief starts by reading `team/creative/taste.md` and `brand/BRAND.md`, so the team doesn't repeat a
rejected idea.

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
- Options: A AI infographic (navy/amber) · B composed thumbnail-style (black/red/orange + owner photo)
- Verdict: B, after one change (HD photo)
- Why: "A's colors are horrible"; B reads technical and specific
- Rule proposed: repo art = dark background, bold technical title, owner photo → added to BRAND.md (approved)
```

Keep entries short. The point is that the next brief can search them.

## What this means for each agent

- **Growth** never sends a single creative option to the human, and never sends one that hasn't passed QA's checks.
- **QA** grades only what can fail. QA never writes "looks good" about creative work. It writes which checks
  passed, with values.
- **PM** owns the memory: it logs every verdict and turns repeated preferences into brand rules once the human
  approves them.
- **The human** gives direction and the final yes. Nothing creative goes public on the agents' judgment alone.
