# Worked Teardowns (Instagram)

Three teardowns showing the output `ig-hook-extractor` produces: a caption, a
carousel, and a Reel. Captions are illustrative, not real posts.

---

## Example 1: caption (single image)

**Pasted caption (first line):**
> I deleted 4,000 of my 6,000 email subscribers and my open rate doubled.

**Teardown:**

- **Formula:** IG2 Contrarian Truth (0.7) / IG1 Number-First Result (0.6). The
  odd-precision numbers pull toward IG1, but the move is a contrarian one
  (deleting subscribers), so it reads primarily as IG2.
- **Surface:** single image. The whole idea fits the caption; the image is a
  supporting visual.
- **Hook (first 125 chars):** the contrarian action stated flatly, with two real
  numbers (4,000 of 6,000) that make it land. No setup.
- **Close:** likely a one-line reason + a send/save prompt.
- **Primary goal:** shares. "Delete your list and improve" is a sent-to-a-friend
  idea ("see, I was right").
- **Why it worked:** a defensible counter-move plus hard numbers is
  screenshot-ready. The numbers pre-empt the "prove it" comment.
- **Blank template:**
  ```
  I {contrarian action with a real number} and {surprising better result}.

  {The one-line reason it worked.}

  {Send/save prompt.}
  ```
- **Cautions:** none in the hook. Confirm the numbers are real before reusing.

---

## Example 2: carousel

**Pasted slides:**
> Slide 1: "7 portfolio mistakes that cost junior designers the interview (most do #4)"
> Slides 2-8: one mistake each
> Slide 9: "the 7 on one slide. save it before your next application."

**Teardown:**

- **Formula:** IG5 Listicle Carousel (0.9).
- **Surface:** carousel, 9 slides. A numbered teaching list earns its room with
  one item per slide.
- **Hook (slide 1):** the promise (7 mistakes) + the open loop ("most do #4")
  + the stakes (cost the interview). Earns the swipe.
- **Body:** one mistake per slide; the recap slide is the save-bait artifact.
- **Close (slide 9):** the list condensed on one slide + an explicit save prompt.
- **Primary goal:** saves. A condensed reference slide is built to be saved.
- **Why it worked:** the loop forces the swipe to #4; the single-slide recap
  makes the whole carousel worth keeping.
- **Blank template:**
  ```
  Slide 1: {N} {mistakes/tips} that {specific stake}. (most do #{k})
  Slides 2..N-1: one item each, named, with a concrete example
  Slide N: the {N} on one slide. {save prompt with a reason}
  ```
- **Cautions:** keep the strongest item early in the list, not on the last body
  slide.

---

## Example 3: Reel

**Pasted first 3 seconds:**
> On-screen text: "you are posting Reels at the worst time."
> First spoken line: "here is when your audience is actually online, free."

**Teardown:**

- **Formula:** IG9 Pattern-Interrupt Reel (0.8).
- **Surface:** Reel. The hook is the first frame text + the open loop.
- **Hook (first 3 seconds):** a claim that makes scrolling past feel like missing
  out, plus an immediate promise to resolve it. On-screen text lets silent
  viewers get it.
- **Body:** likely the actual timing advice, fast cuts, on-screen labels.
- **Close:** a save or follow prompt; a loop-able last frame lifts rewatch.
- **Primary goal:** shares (a "you are doing it wrong" payoff gets sent) with a
  saves secondary if the timing data is concrete.
- **Why it worked:** the first frame is a pattern interrupt; retention through
  the first 3 seconds is what earns the push to non-followers.
- **Blank template:**
  ```
  First frame: "{a claim that makes scrolling past feel costly}."
  First line: "{drop straight into the payoff, no welcome-back}."
  Body: the actual answer, fast, on-screen labels.
  End: {save or follow prompt} + a loop-able last frame.
  ```
- **Cautions:** the Reel must pay off the claim fast, or the swipe-away hurts reach.
