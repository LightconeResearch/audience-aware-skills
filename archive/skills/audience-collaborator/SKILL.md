---
name: audience-collaborator
description: Communicate with a peer on your own team who shares the scientific goal and matches your expertise — a postdoc, a PhD student, or a faculty member who is not your advisor. Use when the user asks to write something up for a colleague, brief a teammate, hand off a piece of work, prepare for a group meeting, or says "for my collaborator", "for the team", "explain this to <peer>", "write this up for the group". Assumes shared background and shared goal; assumes no knowledge of the author's day-to-day state.
---

# Audience: Collaborator

**v0 draft.** Written to be argued with.

## Reader model

The collaborator knows the field about as well as you do. Same rough expertise
level, same team, same scientific goal. A postdoc down the hall. A PhD student
on the other half of the project. A faculty member who is not your advisor.

The gap is not knowledge. **The gap is trench time.** They have not fought your
bug for a week. They have not held the state you have been holding: which run is
which, which branch is live, why you are three levels deep in a covariance
conditioning rabbit hole. You have that state. They do not, and they should not
have to acquire it to read you.

So the split is:

- **Assume they hold** the project goal, the broader context, the standard
  methods, the vocabulary, the reason this work matters.
- **Never assume they hold** your local state. Any detail that only makes sense
  from inside your last week is context you must supply — or omit.

What they want: a high-level summary first, and local detail on demand. Not a
transcript of your week.

**When you are wrong, it costs them little.** They can challenge a bad claim
cheaply and they will. That buys you room to think out loud, to say "I believe X
but have not shown it", to float a half-formed idea. Use the room. This is the
reader with whom uncertainty is cheapest to voice. See *Regardless of role* in
the repo README.

## Register rules

**Summary first, detail on demand.** Open with where the work stands and what it
means for the shared goal. Then offer the depth: "the messy part is the
covariance conditioning — say the word and I'll go into it."

**Name your state; do not assume it.** "Run 04" means nothing to them. "Run 04
(the one with the apodized mask)" costs six words and saves a message.

**Think out loud, but mark it.** Label what is established, what you believe,
and what you are guessing. Peers correct guesses for free. Unlabeled guesses
become someone else's assumption.

**Ask real questions.** This is the reader you can genuinely ask. "Have you hit
this before?" is a good use of a colleague and a bad use of a student.

**Lead with what changes for them.** If your result moves their piece of the
project, that goes first, above your own narrative.

**Skip the background. Keep the bridge.** No method tutorials. But do say which
of your local threads a claim comes out of.

**Length: short, expandable.** A few paragraphs. Link the detail. If they want
the rabbit hole they will ask, and then you can go all the way down.

## Do / don't

**Don't:**

> Spent most of the week on the covariance. The conditioning was bad so I tried
> shrinkage, then a Hartlap correction, then went back and checked the mode
> coupling, which turned out to be fine. Then I found the mask was the issue.
> Reran everything. Numbers attached.

Trench narrative. The reader has to reconstruct the point from the journey.

**Do:**

> Short version: the covariance problem was the mask, not the estimator. Fixed,
> and the null test now passes (χ²/dof 1.4 → 1.05).
>
> Relevant to you: this changes the bandpower window functions, so the numbers I
> gave you last week are stale — new ones in `runs/mask_fix/`.
>
> Happy to walk through the conditioning diagnostics if useful. Short answer:
> they were a red herring.

---

**Don't** use your private names for things. **Do** gloss them once: "the big
run (600 sims, full footprint)".

---

**Don't:**

> The bias is small.

**Do:**

> The bias looks small — m ≈ 2×10⁻³ — but I've only checked one field, so treat
> that as a working number, not a result.

Marked confidence. The peer now knows how hard to lean on it.

---

**Don't** hide the thing you are stuck on because it is embarrassing. **Do**
state it plainly. A week of trench time is exactly what a fresh peer can
short-circuit in five minutes.

## Structure that works

```
Where it stands, one or two lines.
What changed for you. (their piece of the shared goal)
Confident in / guessing at.
The open question, if you have one for them.
Detail on request: (name the threads, do not unspool them)
```

## Failure modes to watch for

- **State dumping.** Pouring a week of context on someone who did not live it.
- **State assuming.** The opposite: referring to your local threads as if they
  were common knowledge.
- **Over-formality.** This is a colleague, not a referee. A polished
  claims-and-evidence document is the wrong artifact and costs you speed.
- **Under-marking confidence.** Peers propagate what you tell them. An unmarked
  guess travels.
- **Withholding the mess.** The stuck part is often the most useful thing to give
  this reader.

## Not covered here: formal peer review

Adversarial review — a referee report, a response to referees, a code review
whose job is to find defects — is a different mode. That reader is not on your
team and is not reading for the shared goal. They are reading to break the work.
The register is claims paired with evidence, limitations stated before they are
found, tested separated from assumed.

That mode probably deserves its own skill. We split it out of this one on
purpose. Merging "colleague" and "referee" gave a skill that was too formal for
the colleague and too warm for the referee.

## Open for the group

- Does an AI review agent belong in the future peer-review skill, or is it a
  third mode again? It has the referee's job and none of the referee's social
  cost.
- Is "collaborator" one role or two — the peer working on your piece versus the
  peer working on an adjacent piece? The second needs more bridging.
- How much marked uncertainty is too much? There is a register where everything
  is hedged and nothing is claimed.
