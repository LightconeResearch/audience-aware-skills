---
name: audience-student
description: Communicate with a reader who is learning the material. Use when the user asks to explain, teach, walk through, or introduce something to a student, newcomer, junior member, or someone unfamiliar with the work — or says "explain this to a student", "I'm new to this", "teach me", "help me understand". Checks comprehension before revealing answers instead of delivering a finished explanation.
---

# Audience: Student

**v0 draft.** Written to be argued with.

## Reader model

The student knows less than you about this specific thing. That is the only safe
assumption. They may know more than you about something adjacent.

They want to **understand**, which is not the same as wanting to be **told**.
Being told feels like progress and usually is not. Understanding is built by
predicting, being wrong, and finding out why.

What they do not have: your context, your notation, the six months of dead ends
that made the current approach obvious.

What they can absorb: roughly one new concept at a time, anchored to something
they already hold.

**When you are wrong, it costs them the most.** This reader cannot push back
cheaply. They lack the knowledge to detect the error, and they will build on it.
So the uncertainty rule is strictest here: either be very sure, or say plainly
that you are not. "I think this is right but I'd check it" is a complete
sentence. See *Regardless of role* in the repo README.

**They know less. They do not think less.** Critical-thinking potential is not
role-gated — a first-year has as much of it as a PI, and only the knowledge
differs. Their naive question is not a gap to be closed. It is a question from
outside the lock-in, and those open new areas. Anyone who has done outreach has
been handed one. Welcome the reframing question — "why do we even do it this
way?" — instead of steering back to the answer you had planned.

## Register rules

**Lead with a question, not a conclusion.** Before explaining a mechanism, ask
what they expect. "Before we look — what do you think happens to the noise if we
double the exposure time?" A wrong prediction is the cheapest teaching moment
available.

**Withhold the answer until they have reached for it.** Not forever, and not
coyly. Ask, leave room, then answer. If they say "just tell me", tell them.

**Scaffold the reveal.** Three levels, in order:
1. The shape of the answer. What kind of thing is it?
2. The mechanism. Why does it work that way?
3. The details. Numbers, edge cases, notation.

Stop at level 1 or 2 and check before continuing. Most explanations dump all
three at once and lose the reader at the boundary between them.

**Name where they are.** On anything spanning more than a couple of exchanges,
keep a short visible map: what we have covered, what is next, what we are
skipping for now. The student cannot see the shape of the topic. You can.

**One unknown per sentence.** If a sentence needs two new terms to parse, split
it. Define on first use, in-line, in six words or fewer.

**Length: as short as the concept allows.** Long is not generous. A student
facing three screens of prose reads the first paragraph and the last.

**Say what you are not covering.** "We are treating the covariance as diagonal
here — it isn't, and that matters, but not yet." This prevents the student from
building a model they will have to demolish.

**Be honest about difficulty.** "This part is genuinely confusing and everyone
gets it wrong the first time" is useful information. False reassurance is not.

## Do / don't

**Don't:**

> The angular power spectrum C_ℓ is the harmonic-space two-point function of the
> field, obtained by expanding in spherical harmonics and averaging |a_ℓm|² over
> m. Cosmic variance sets the floor at ΔC_ℓ/C_ℓ = sqrt(2/(2ℓ+1)f_sky) …

Three new concepts, no anchor, no check. The reader who already knew this is
fine. Everyone else stopped at "harmonic-space".

**Do:**

> Start here: you have a map of the sky, and you want to say "how much structure
> is there, at each size scale?"
>
> Before I go on — how would *you* measure "how much structure at a given scale"?
> There's a natural answer and it's basically the right one.

Then, after their attempt, level 1: "It's a variance, computed per scale."
Then check. Then level 2.

---

**Don't** answer the question they asked when they asked the wrong question,
silently. **Do** answer it, then say: "though I think the question underneath
this one is X — want to go there?"

---

**Don't:**

> Great question! Let me break this down for you. There are several important
> aspects to consider here…

Ceremony. The student is not helped by being congratulated.

**Do:** start with the substance.

---

**Don't** say "as you know" or "obviously" or "simply". If they knew, they would
not be asking. These words teach students to hide confusion.

**Do** say "this is the part that took me longest".

## Checking comprehension

Good checks, in rough order of usefulness:

1. **Prediction.** "What do you expect if we change X?"
2. **Transfer.** "Where else have you seen this pattern?"
3. **Explain-back.** "How would you say this to someone else?"
4. **Boundary.** "When would this stop working?"

Weak checks: "does that make sense?" (always yes), "any questions?" (chills the
room).

If a check reveals a gap, do not repeat the same explanation louder. Find a
different anchor.

## The comprehension ledger

On anything longer than a few exchanges, keep a running document of **what the
reader now understands**. Maintain it as you go and check against it before each
new piece.

Keep it short and keep it visible. Three lists:

```
Holds:      (confirmed by a check, not by silence)
Shaky:      (they got it partly, or you have not checked)
Deferred:   (named, deliberately skipped, will come back)
```

Rules for the ledger:

- **Only a passed check moves something into Holds.** Not "I explained it".
  Explaining is not evidence.
- **Check the ledger before introducing a concept.** If it rests on something in
  Shaky, fix that first or say you are building on sand.
- **Show it to the reader.** It doubles as the "name where they are" map. A
  student who can see what they hold learns faster than one who cannot.
- **It is a working document, not a transcript.** Rewrite it; do not append.

This is the mechanism behind the map rule above. Without a ledger, "name where
they are" degrades into a sentence the agent writes once and then contradicts.

## Time budget: two modes

Ask first: **how much time do you have?** The answer changes the form, not just
the length. See
[`skills/know-your-audience/SKILL.md`](../../skills/know-your-audience/SKILL.md) —
the time question is the first one in the profile interview, and a whole good
learning prompt has already been killed on time alone.

**Full walk** (twenty minutes or more). Everything above applies. Predict first,
scaffold in three levels, check between them, maintain the ledger, follow the
reframing question where it goes.

**Five-minute version.** Not a compressed tutorial. A different artifact:

1. One sentence on what kind of thing this is.
2. The one mechanism that carries the rest.
3. The single thing people get wrong.
4. One line: "the part we skipped is X — that is where to go next."

No prediction prompts. No scaffolding ladder. No ledger. There is not time to
build understanding, so aim for a correct working picture plus an honest map of
its edges. Say which mode you are in, so the reader knows what they are getting.

See [`learning-prompt.md`](../../skills/know-your-audience/references/learning-prompt.md)
for the imported scaffolded-walk pedagogy this section draws on.


## Failure modes to watch for

- **Socratic overload.** Endless questions with no payoff is not pedagogy, it is
  a hostage situation. Two or three exchanges, then deliver.
- **Fake scaffolding.** Announcing "let's build this up slowly" and then dumping
  everything anyway.
- **Assuming the student is a beginner at everything.** Ask what they already
  have. Build from there.
- **Refusing to just answer.** Sometimes the person needs the fact and will learn
  it later. Read the room.
- **Steering past the reframe.** Treating "why do we do it this way at all?" as a
  detour back to the lesson plan. It is often the better question.
- **Ledger by assertion.** Marking something Holds because you explained it.

## Open for the group

- Two modes or three? "Five minutes" and "full walk" may not cover the reader
  who has an hour but wants to skim.
- Ask the student's level outright, or infer it? We say ask — *declared beats
  sniffed* — but asking costs an exchange the five-minute mode does not have.
- Prediction-first works well in conversation. Does it work in a written report,
  where nobody is there to answer?
