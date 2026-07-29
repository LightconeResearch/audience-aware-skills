---
name: audience-definition
description: Interview a scientist about one audience and generate a durable, editable communication skill for it. Use whenever someone is defining a new audience, joining a new collaboration, taking on a new role, or says "create a communication skill for X", "make a skill for writing to my advisor", "define a skill for how the agent writes for the DESI working group", "set up a reader profile for my student", "define my audience", "write a communication skill for this team". Also use to re-interview and update an audience skill that already exists, or to build a profile of the user themselves as a reader. Only for CREATING or UPDATING a register. A request to APPLY one — "write this PR description for the WG", "explain this to my student" — goes to an existing audience skill, not here.
---

# Audience definition

Your role: understand how the user wants to communicate and who the audience
is, combine that understanding with general best practices, and produce a new
communication skill for that audience. **The user wants a draft they can edit.
They never want to write it themselves.** Ask few questions, ask them well,
generate something opinionated and concrete, and be explicit about what you
guessed.

This skill is self-contained. The reader-role priors are in
[`references/priors.md`](references/priors.md); the skeleton and constant
blocks are in [`assets/template.md`](assets/template.md). Nothing outside this
directory is load-bearing.

The steps, in order:

1. **Read the priors** — orient in the space of common roles before asking
   anything.
2. **Interview** — sized by the user's time budget.
3. **Synthesize a profile and repeat it back** — iterate until the user
   recognizes it.
4. **Ask where the skill should live.**
5. **Generate** — turn profile + template into a full skill, holistically.
6. **Hand over.**

## 1. Read the priors

Read [`references/priors.md`](references/priors.md) before interviewing. It
describes five priors — `audience-student`, `audience-collaborator`,
`audience-advisor`, `audience-prompter`, and `team-norms` (etiquette for
shared surfaces, not a reader) — each in full: reader model, register,
failure modes, and (for the student) pedagogy moves with time gates. It also
gives the two axes (knowledge entering vs. context held) used to place a
"something else" answer.

Priors are non-exhaustive, non-exclusive, and no reader fits one perfectly.
They inform the interview: they tell you what to listen for and which
follow-up matters. The generated skill is a **specialization of a prior, not
a fresh essay** — that is what keeps ten of them consistent with each other.
Where the interview contradicts the prior, the interview wins.

## 2. Interview

First settle **who is being modelled** — two interviews wear the same
clothes:

- **First-hand** — the user is the reader ("how should agents write *to
  me*"). Reliable; use their words.
- **Second-hand** — the user is an author describing an audience ("how should
  I write to my advisor"). The verbatim questions ask about the *interviewee*,
  but the skill is about the *reader* — so ask the reader-facing version too:
  what the reader is to the author, how long the reader gives one artifact,
  what the *reader* found hard to parse. The author's answers size the
  interview; they do not fill the reader model. If a reader-facing answer is
  unavailable, leave that slot unknown and say so. The generated skill states
  whose model it is and marks the guesses; suggest the cheap fix of sending
  the standard questions to the actual reader.

Four standard questions, Q1–Q4. Ask them verbatim; do not paraphrase them
into your own voice. Ask in small batches — two or three per turn, not a
form. Reflect back what you heard. Stop early when you have enough.

**Q1 — time budget. Ask it alone, first, before anything else.** It sizes the
interview itself, so nothing can precede it.

> **How long do you have right now? Two minutes / fifteen / an hour / as long
> as it takes**

**Q2 — role** ("something else" is the most useful answer):

> **Which role applies to you the most as part of this research team?
> 1. Advisor 2. Peer 3. Student 4. Something else -- please provide**

**Q3 — gap handling** (the teaching-vs-briefing dial; sharper than the role
label):

> **When you hit something you don't know, do you want the answer, an
> explanation of the topic, or a question that gets you there?**

**Q4 — parsing failure** (the richest question — push for a specific
incident, **except at two minutes, where you skip it entirely**):

> **Tell me about the last time AI-assisted work was difficult to parse. What
> is one actionable thing that would have helped with comprehension?**

Alongside Q2, take one line of context: which collaboration, which surfaces
(PRs, issues, Slack, reports, talks).

Optional follow-ups, skipped freely under a tight budget:

- **Q5 — knowledge entering, and context held.** Two separate axes; collapsing
  them is the most common modelling error.
- **Q6 — what should they be able to do afterward?** Roles are defined by
  goals, not knowledge.
- **Q7 — cost of being wrong.** Can this reader push back in a sentence, or do
  they absorb the error and build on it? Sets the uncertainty rule.
- **Q8 — artifacts and local norms.** Two or three surfaces that actually
  occur; only what differs from general etiquette.
- **Q9 — one norm an outsider would get wrong**, and one thing that has
  annoyed people here.
- **Q10 — real examples.** One thing that landed, one that did not. Two real
  samples beat twenty adjectives.

**The time answer binds the interview:**

- **Two minutes** — Q2 and Q3 only, with the one-line context. Skip Q4.
- **Fifteen** — add Q4 and Q5–Q8.
- **An hour or more** — add Q9 and Q10, and walk the draft line by line.

Say which mode you are in: a short interview makes a thinner skill, and the
user should know that is what they are buying.

## 3. Synthesize the profile, repeat it back

Pause before writing anything. Collect what you heard into a short profile:
which prior is nearest, where this reader departs from it, the register that
follows. Mapping notes:

- Q2 asks what the **interviewee** is; priors are named for what the
  **reader** is. First-hand, map straight through. Second-hand, ask what the
  audience is *to the author* and map that — a WG lead writing to their WG
  lands on student or collaborator, never advisor.
- **Plural audiences:** name the nearest prior for the *typical* reader, call
  it approximate, add one line on who else is in the room. Do not stack
  priors.
- **Time is two quantities.** The Q1 answer is the interviewee's afternoon;
  the reader's `Time:` slot is how long that audience gives one artifact.
  First-hand they are close; second-hand they are unrelated — ask, or leave
  the slot out.

Then repeat the profile back in two or three lines — "writing for: a peer, no
context on my last week, ten minutes, wants to decide whether to rerun their
half; correct me if that is wrong" — and iterate until the user recognizes
it. This is cheap and it catches a mis-model before anything is built on it.

## 4. Ask where the skill lives

Always ask; do not assume. Two decisions, both the user's:

**Location.** Global (`~/.claude/skills/`, live everywhere immediately), the
project's `.claude/skills/` (audience is project-bound), or a shared repo.
Profiles describe real, named colleagues — **never write one into a git repo
without the user's explicit permission.**

**Layout.** Two shapes, user's choice:

- **One skill per audience** — `audience-<slug>/SKILL.md` each. Simple,
  independent.
- **One personal communication skill** — common principles and personal
  constants (sign-offs, voice) in the body, one reference file per audience
  (`references/desi.md`, `references/advisor.md`). Fewer skills, no
  duplication of the shared parts. If the user already has such a skill, add
  a reference file to it instead of creating a new skill.

Keep whichever shape they pick minimal.

## 5. Generate

Read [`assets/template.md`](assets/template.md) and the chosen prior, then
write the skill from your **holistic understanding of the profile** — the
person communicating, their role, and who the audience is. This is not a
mechanical mapping of answers onto template slots; the template is a
skeleton, and the profile is what animates it. Constants copy through.
Reference files beside the generated skill are allowed when the user wants
them, not required.

Rules:

- **Never write a line in the voice of a user answer unless the user said
  it.** A guess dressed as a fact is the one output that makes this skill
  worse than nothing. Prior-derived content is legitimate **if labelled**:
  mark such blocks `<!-- from prior: audience-X, not confirmed -->`, leave
  unasked sections as `<!-- unasked: … -->`, and say so plainly in the
  generated skill's `## Confidence in this model` block. Delete that block
  only when the model is first-hand and complete.
- If the reader is student-shaped, apply the pedagogy moves and their time
  gates from the Student section of `references/priors.md` — gated by the
  **reader's** budget, not the interview's.
- If the generated skill references `team-norms` by name, inline the
  load-bearing lines — a norms section that points at an absent skill has no
  norms section.

Craft rules for the generated file: all triggering lives in the frontmatter
description (name the audience, the artifacts, the phrases the user will
type; lean slightly pushy — agents undertrigger). Body under ~150 lines, read
in full every time it fires. Imperative voice. Explain why instead of
stacking MUSTs. Do not overfit to one anecdote — generalize the move, keep
the example as illustration. Name it plainly (`audience-desi-lensing-wg`).
Reread it cold and cut.

## 6. Hand over

Five things, no ceremony:

1. Where the file is; if global, it is already live.
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
Check any reference files too. Do not badger: never offer to re-interview
more than once a day, and only when something suggests the model has moved.

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
