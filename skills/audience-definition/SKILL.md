---
name: audience-definition
description: Interview a scientist about one audience and generate a durable, editable communication skill for it. Use whenever someone is defining a new audience, joining a new collaboration, taking on a new role, or says "create a communication skill for X", "make a skill for writing to my advisor", "define a skill for how the agent writes for the DESI working group", "set up a reader profile for my student", "define my audience", "write a communication skill for this team". Also use to re-interview and update an audience skill that already exists, or to build a profile of the user themselves as a reader. Only for CREATING or UPDATING a register. A request to APPLY one — "write this PR description for the WG", "explain this to my student" — goes to an existing audience skill, not here.
---

# Audience definition

A scientist is in several collaborations at once, with a different role in
each: lead of one working group, one voice among hundreds in another, sole
advisor to one student. Each deserves its own communication register, and the
register does not survive between sessions in the agent's head. It lives in a
small skill file. This skill produces those files: interview once, generate a
draft, hand it over. The user edits it and keeps it for years.

**The user wants a draft they can edit. They never want to write it
themselves.** That is the whole product constraint. Ask few questions, ask
them well, generate something opinionated and concrete, and be explicit about
what you guessed.

The architecture in one sentence: the LLM's job is to model the reader; the
skill's job is to supply the best practices that merge with that model. Here
you do both. This skill is self-contained: the reader-role priors are in
[`references/priors.md`](references/priors.md), the skeleton and constant
blocks in [`assets/template.md`](assets/template.md). Nothing outside this
directory is load-bearing.

## Priors

Do not generate from nothing. Five priors: `audience-student`,
`audience-collaborator`, `audience-advisor`, `audience-prompter`, and
`team-norms` (etiquette for shared surfaces, not a reader). They are
non-exhaustive, non-exclusive, and no reader fits one perfectly. The generated
skill is a **specialization of a prior, not a fresh essay** — that is what
keeps ten of them consistent with each other.

**Read [`references/priors.md`](references/priors.md) before generating.** It
carries each prior in full — reader model, register, failure modes, the
student pedagogy moves with their time gates — plus the two axes (knowledge
entering vs. context held) used to place a "something else" answer.

Where the interview contradicts the prior, the interview wins. Say so in one
line when you hand over.

## Who is being modelled?

Two interviews wear the same clothes. Settle this in the first exchange.

- **First-hand** — interviewing the reader themselves ("how should agents
  write *to me*"). Reliable. Ask directly, use their words.
- **Second-hand** — interviewing an author about an audience they write *for*
  ("how should I write to my advisor"). The generated skill says whose model
  it is and marks the guesses. Suggest the cheap fix: send the standard
  questions to the actual reader.

In second-hand mode every standard question has a second version: the
verbatim form asks about the *interviewee*; the skill is about the *reader*.
Ask the reader-facing version too (what the reader is to the author, how long
the reader gives one artifact, what the *reader* found hard to parse, what the
*reader* wants at a gap). The author's answers size the interview; they do not
fill the reader model. If the author cannot answer a reader-facing version,
leave that slot unknown and say so. This propagates into the generated skill's
`## Confidence in this model` block — delete that block only when the model is
first-hand and complete.

## The interview

Four standard questions, Q1–Q4. Ask them verbatim; do not paraphrase them
into your own voice. Ask in small batches — two or three per turn, not a
form. Reflect back what you heard. Stop early when you have enough.

**Q1 — time budget. Ask it alone, first, before anything else.** It sizes the
interview itself, so nothing can precede it.

> **How long do you have right now? Two minutes / fifteen / an hour / as long
> as it takes**

**Q2 — role** (picks the prior; "something else" is the most useful answer):

> **Which role applies to you the most as part of this research team?
> 1. Advisor 2. Peer 3. Student 4. Something else -- please provide**

**Q3 — gap handling** (the teaching-vs-briefing dial; sharper than the role
label):

> **When you hit something you don't know, do you want the answer, an
> explanation of the topic, or a question that gets you there?**

**Q4 — parsing failure** (fills the `Do / don't` pair in the reader's own
vocabulary; the richest question — push for a specific incident, **except at
two minutes, where you skip it entirely**):

> **Tell me about the last time AI-assisted work was difficult to parse. What
> is one actionable thing that would have helped with comprehension?**

Alongside Q2, take one line of context: which collaboration, which surfaces
(PRs, issues, Slack, reports, talks).

Then optional follow-ups, skipped freely under a tight budget:

- **Q5 — knowledge entering, and context held.** Two separate axes; collapsing
  them is the most common modelling error.
- **Q6 — what should they be able to do afterward?** Roles are defined by
  goals, not knowledge.
- **Q7 — cost of being wrong.** Can this reader push back in a sentence, or do
  they absorb the error and build on it? Sets the uncertainty rule.
- **Q8 — artifacts and local norms.** Two or three surfaces that actually
  occur; only what differs from `team-norms`.
- **Q9 — one norm an outsider would get wrong**, and one thing that has
  annoyed people here.
- **Q10 — real examples.** One thing that landed, one that did not. Two real
  samples beat twenty adjectives.

**The time answer binds the interview:**

- **Two minutes** — Q2 and Q3 only, with the one-line context. Skip Q4. No
  follow-ups. Generate from the prior and mark what came from the prior.
- **Fifteen** — add Q4 and Q5–Q8.
- **An hour or more** — add Q9 and Q10, and walk the draft line by line.

Say which mode you are in: a short interview makes a thinner skill, and the
user should know that is what they are buying. Two-minute mode is
prior-derived and legitimate **if labelled**: mark prior-filled blocks
`<!-- from prior: audience-X, not confirmed -->`, leave unasked sections as
`<!-- unasked: … -->`, and say so in `## Confidence in this model`. Never
write a prior-derived line in the voice of a user answer.

### Role → prior

Q2 asks what the **interviewee** is; priors are named for what the **reader**
is. Confusing them inverts the register.

- **First-hand:** map straight through (Advisor → `audience-advisor`, Peer →
  `audience-collaborator`, Student → `audience-student`).
- **Second-hand:** ask what the audience is *to the author*, and map that. A
  WG lead writing to their WG lands on student or collaborator, never advisor.
- **Plural audiences:** name the nearest prior for the *typical* reader, call
  it approximate, add one line on who else is in the room. Do not stack
  priors.
- **"Something else":** place it on the two axes in `references/priors.md`
  plus can-they-push-back-cheaply; keep their label in the reader model.

**Time is two quantities.** The Q1 answer is the interviewee's afternoon; the
reader's `Time:` slot is how long that audience gives one artifact.
First-hand they are close; second-hand they are unrelated — ask, or leave the
slot out.

## Generating the skill

1. **Reveal your model before you write.** Two or three lines, then "correct
   me if that is wrong." It catches a mis-model before you build on it.
2. Read `assets/template.md` (skeleton) and the chosen prior in
   `references/priors.md`. Fill the slots; constants copy through.
3. **Never write a line in the voice of a user answer unless the user said
   it.** A guess dressed as a fact is the one output that makes this skill
   worse than nothing. Empty is honest; labelled prior-derived is fine.
4. Write to `~/.claude/skills/audience-<slug>/SKILL.md`, creating the
   directory — live immediately, no install step. Alternatives only if asked:
   the project's `.claude/skills/`, or a shared repo. **Never write a profile
   of a real person into a git repo without the user's explicit permission.**
   Overflow goes in `references/<topic>.md` beside the generated SKILL.md.
5. If the generated skill references `team-norms` by name, inline the
   load-bearing lines — a norms section that points at an absent skill has no
   norms section.

Craft rules for the generated file: all triggering lives in the frontmatter
description (name the audience, the artifacts, the phrases the user will
type; lean slightly pushy — agents undertrigger). Body under ~150 lines, read
in full every time it fires. Imperative voice. Explain why instead of
stacking MUSTs. Do not overfit to one anecdote — generalize the move, keep
the example as illustration. Name it plainly (`audience-desi-lensing-wg`).
Reread it cold and cut.

### Student-type skills

Fire the pedagogy when the **reader** is student-shaped: the prior is
`audience-student`, or the reader-facing gap answer is "a question that gets
me there". (In second-hand mode the author's own Q3 answer triggers nothing —
a WG lead who likes Socratic treatment does not make their WG a class.)

The teaching moves and their time gates live in `references/priors.md`
(Student section) and the template's `Teaching moves` block. **Gate by the
reader's budget, not the interview's:** an hour gets all the moves; fifteen
minutes gets restate-first, drill-the-whys, and the five-minute artifact; two
minutes gets the five-minute artifact alone.

## Handing it over

Five things, no ceremony:

1. Where the file is; if `~/.claude/skills/`, it is already live.
2. The reader model quoted inline, with "correct me if that is wrong."
3. The two or three lines you were least sure about, named as guesses.
4. One trigger phrase they can try right now.
5. "Come back in three months when you know this group better and we
   regenerate it."

Then stop. Do not walk them through the file — they will read it. Never ask
the user to write a section themselves; if a slot is empty, ask one more
question or cut it.

## Re-interviewing

An audience skill goes stale because the user's model of the team improves.
When updating: read the existing file first, ask what changed and what turned
out wrong, re-ask Q10 (examples turn over fastest), and **edit in place
rather than regenerating** — the user's own edits are the most valuable
content in the file and they survive. Preserve the `name` and directory.
Check any `references/` sibling too. Do not badger: never offer to
re-interview more than once a day, and only when something suggests the model
has moved.

## Failure modes

- **Interrogation.** Twelve questions to a person who said two minutes.
- **Generic output.** If it would fit any team, you did not use the
  interview. Their project nouns should appear in it.
- **Guessing to fill the template.** Empty is honest; invented is not.
- **Ignoring the prior.** Ten unrelated skills instead of ten
  specializations.
- **Treating a second-hand model as first-hand** — sharpest form: mapping the
  author's own role and generating an advisor register for people they
  advise.
- **Importing the interview budget into the reader model.** Their two spare
  minutes are not their working group's reading habit.
- **Handing back an essay.** They asked for a file, not a lecture about it.
- **Slop.** No "Great question!", no "comprehensive framework", no bullets
  restating their own headings.
