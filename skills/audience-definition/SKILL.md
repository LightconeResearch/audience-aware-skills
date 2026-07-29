---
name: audience-definition
description: Interview a scientist about one audience and generate a durable, editable communication skill for it. Use whenever someone is defining a new audience, joining a new collaboration, taking on a new role, or says "create a communication skill for X", "make a skill for writing to my advisor", "define a skill for how the agent writes for the DESI working group", "set up a reader profile for my student", "define my audience", "write a communication skill for this team". Also use to re-interview and update an audience skill that already exists, or to build a profile of the user themselves as a reader. Only for CREATING or UPDATING a register. A request to APPLY one — "write this PR description for the WG", "explain this to my student" — goes to the role skills or an existing audience skill, not here.
---

# Audience definition

**v0 draft.** Written to be argued with.

## What this is

A scientist is in several collaborations at once, with a different role in each:
lead of a DESI working group, one voice among hundreds in Rubin, sole advisor to
one student. Each of those deserves its own communication register, and the
register does not survive between sessions in the agent's head. It lives in a
small skill file.

This skill produces those files. Interview once, generate a draft, hand it over.
The user edits it and keeps it for years. Re-interview when their model of the
team changes — which it will, faster than they expect.

**The user wants a draft they can edit. They never want to write it themselves.**
That is the whole product constraint. Ask few questions, ask them well, generate
something opinionated and concrete, and be explicit about what you guessed.

The architecture, unchanged from the repo README:

> The LLM's job is to model the reader; the skill's job is to supply the best
> practices that merge with that model.

Here you do both: interview to get the reader, merge with the constants in
`assets/template.md`.

## Priors: the existing role skills

Do not generate from nothing. The table below is the distilled prior — everything
this skill needs at generation time. Pick the one or two rows that fit and match
their register.

| Prior | Reader |
|---|---|
| `audience-student` | knows less; wants to understand, not to be told |
| `audience-collaborator` | peer, same expertise, no trench time |
| `audience-advisor` | knows *differently*; authority and altitude; five minutes |
| `audience-prompter` | asked for the work; wants outcome and decisions |
| `team-norms` | etiquette for shared surfaces: cadence, length, tagging |

Read `README.md` and `docs/reader-profiles.md` for the two-axes framing. The
generated skill is a **specialization of a prior, not a fresh essay** — that is
what keeps ten of these consistent with each other. (The original v0 drafts
these rows were distilled from live in `archive/skills/`, for history — not
needed to run this interview.)

`docs/reader-profiles.md` describes its own "four questions". It predates the
summit set and its Q3 and Q4 are this skill's optional Q5 and Q6. **Use the four
below.** Read reader-profiles for the axes and the reasoning, not for the script.

Where the interview contradicts the prior, the interview wins. Say so in one line
when you hand over. That contradiction is data for the repo.

## Before you start: who is being modelled?

Two different interviews wear the same clothes. Settle this in the first
exchange.

- **Interviewing the reader themselves** ("how should agents write *to me*").
  First-hand and reliable. Ask directly, use their words.
- **Interviewing an author about an audience they write *for*** ("how should I
  write to my advisor"). Second-hand. The generated skill says whose model it is
  — "Cail's model of Nabila, not Nabila's" — and marks the guesses. Suggest the
  cheap fix: send the four standard questions to the actual reader.

This propagates into the generated skill's `## Confidence in this model` block.
Delete that section only when the model is first-hand and complete — otherwise
keep it. A guessed profile that reads as certain is exactly the failure the
repo's *declared beats sniffed* principle warns about.

**In second-hand mode, every standard question has a second version.** All four
ask about *you*; the skill is about *them*. Ask the reader-facing version too:
what the reader is to the author (→ prior), how long the reader gives one of
these (→ the `Time:` slot), a time *they* found agent output hard to parse, what
*they* want when they hit a gap. The author's own answers still size the
interview — they do not fill the reader model. If the author cannot answer a
reader-facing version, leave that slot unknown and say so.

## The interview

The four standard questions came from the group and were posted on the summit
issue
([issue #12](https://github.com/LightconeResearch/AAI4ScienceDeveloperSummit/issues/12)).
Ask them verbatim. Do not paraphrase them into your own voice.

**Ask the budget question alone, first, before anything else — including Q0.**
It sizes the interview itself, so nothing can precede it.

> **How long do you have right now? Two minutes / fifteen / an hour / as long as
> it takes**

Everything after this obeys the answer. From here on, ask in small batches — two
or three questions per turn, not a form. Reflect back what you heard before
moving on. Stop early when you have enough; a short good interview beats a
complete one.

**Q0 — Who and where.** Which collaboration, which surfaces (PRs, issues, Slack,
reports, talks). One line each is fine. Under a two-minute budget, fold this into
one question and take one line total. Role is not part of Q0 — the verbatim role
question below carries it.

> **Which role applies to you the most as part of this research team? 1. Advisor
> 2. Peer 3. Student 4. Something else -- please provide**

> **When you hit something you don't know, do you want the answer, an explanation
> of the topic, or a question that gets you there?**

> **Tell me about the last time AI-assisted work was difficult to parse. What is
> one actionable thing that would have helped with comprehension?**

Each one is load-bearing, and each fills a named slot:

- **Role** → picks the prior, via the mapping below. "Something else" is the most
  useful answer you can get; it tells you which prior to override and where.
- **Time** → sizes the interview and gates the pedagogy. It changes the *form*,
  not just the length. It is not the reader's `Time:` line — see below.
- **Answer / explanation / question** → the gap-handling default. It separates a
  teaching register from a briefing register better than the role label does.
- **Hard to parse** → the `Do / don't` pair, in the reader's own vocabulary. The
  richest question, and the section that most changes agent behavior. Push for a
  specific incident — **except at two minutes, where you skip it entirely.** It
  cannot be answered that fast, and pressing someone who told you they have no
  time is the fastest way to lose them.

### Role → prior

The role question asks what the **interviewee** is. The priors are named for what
the **reader** is. Those are not the same, and confusing them inverts the
register.

- **First-hand** (they are the reader): the role maps straight through — Advisor →
  `audience-advisor`, Peer → `audience-collaborator`, Student → `audience-student`.
- **Second-hand**: ask outright, "what is this audience to you — someone you
  advise, a peer, someone who advises you, someone who asked you for the work?"
  Map *that*. A WG lead writing to their WG lands on `audience-student` or
  `audience-collaborator`, never `audience-advisor`.

**Plural audiences.** A working group is postdocs, students and PIs at once. Name
the nearest prior for the *typical* reader, call it approximate, and add one line
to `Reader model` on who else is in the room. Do not stack four priors.

**"Something else."** Ask what they would call it, then place it on the README's
two axes — knowledge relative to yours, ability to push back. Those pick the
nearest prior. Keep their label in the reader model; put what the prior gets
wrong in `Open questions`.

**Time is two quantities.** The budget answer is the interviewee's afternoon. The
reader's `Time:` slot is how long that audience gives one artifact. First-hand,
they are close enough to reuse. Second-hand, they are unrelated: ask, or leave
the slot out. A two-minute interview does not mean a two-minute reader.

Then, as needed — skip freely under a tight budget:

**Q5 — Knowledge entering, and context held.** Two axes; collapsing them is the
most common modelling error. Domain expertise is not project state. A reader can
be world-class and still not know which run is which.

**Q6 — What should they be able to do afterward?** Roles are defined by goals,
not knowledge. "Decide whether to fund it." "Reproduce it next month." "Not be
lost in the group meeting."

**Q7 — Cost of being wrong.** Can this reader push back in a sentence, or do they
absorb the error and build on it? Sets the uncertainty rule.

**Q8 — Artifacts and local norms.** The two or three surfaces that actually
occur, and for each: right length, cadence, who may be tagged, what needs a human
before it goes out, formal or casual. Only what differs from `team-norms` — do
not re-elicit the universal parts. A skill covering seven surfaces covers none.

**Q9 — One norm an outsider would get wrong**, and one thing that has annoyed
people here. Two questions, cheap, and they produce content nothing else does.

**Q10 — Real examples.** One thing written for this audience that landed, one
that did not. Two real samples beat twenty adjectives.

### The time answer is binding on the interview too

- **Two minutes** — three questions after the budget one: a one-line Q0, the role
  question, the gap-handling dial. **Skip the parsing question.** Accept short
  answers, ask no follow-ups, do not push for specifics. Then generate from the
  prior and mark what came from the prior.
- **Fifteen** — add the parsing question and Q5–Q8.
- **An hour or more** — add Q9 and Q10, and walk the draft line by line.

Say which mode you are in. A short interview makes a thinner skill, and the user
should know that is what they are buying.

**Two-minute mode is prior-derived, and that is legitimate — if it is labelled.**
The rule against guessing forbids passing an invention off as something the user
said; it does not forbid using the prior. Fill the reader model and register
rules from the prior, mark each such block `<!-- from prior: audience-X, not
confirmed -->`, say so in plain words in `## Confidence in this model`, and leave
unasked sections as `<!-- unasked: … -->` for the re-interview. Never write a
prior-derived line in the voice of a user answer.

## Generating the skill

1. **Reveal your model before you write.** Two or three lines, then "correct me
   if that is wrong." Cheap, and it catches a mis-model before you build on it.
2. Read `assets/template.md`. The priors table above is sufficient to fill it;
   read the archived draft at `archive/skills/<the-prior>/SKILL.md` only if you
   want more texture on tone than the table row gives.
3. Fill the slots. Constants copy through. **Never write a line in the voice of a
   user answer unless the user said it.** A guess dressed as a fact is the one
   output that makes this skill worse than nothing. Prior-derived content is
   allowed and labelled (see the two-minute rule above); anything neither said
   nor derivable from the prior becomes an `<!-- unasked: … -->` comment.
4. Write to `~/.claude/skills/audience-<slug>/SKILL.md`, creating the directory.
   That is the default and it means the skill works the moment you finish — no
   install step. Two alternatives, only if the user asks: the project's own
   `.claude/skills/` when the audience is project-bound, or this repo's `skills/`
   when they mean to share it. Do not default to this repo: these files describe
   named colleagues, and a git repo is the wrong home for that. If overflow needs
   a sibling file (see below), write it alongside as
   `<same-dir>/audience-<slug>/references/<topic>.md`, next to `SKILL.md`.
5. If a prior or `team-norms` is referenced by name, check it is installed too. If
   it is not, either install it alongside or inline the load-bearing lines into
   the generated file. A skill whose norms section says "Follow `team-norms`" and
   whose `team-norms` is absent has no norms section.

### What makes the generated skill good

Imported from the official `skill-creator` skill, and worth obeying:

- **The description is the trigger.** All "when to use this" lives in the
  frontmatter description, never in the body. Name the audience, the
  collaboration, the artifacts, and the phrases the user will actually type.
  Agents undertrigger skills, so lean slightly pushy.
- **The body is read in full every time it fires.** Keep it under ~150 lines.
  Anything not needed on every invocation goes in a sibling file with a pointer:
  `skills/audience-<slug>/references/<topic>.md`.
- **Explain why; do not stack MUSTs.** A rule with its reason generalizes to
  cases you did not foresee. A bare imperative does not. Caps-lock ALWAYS is a
  yellow flag — reframe it.
- **Imperative voice, addressed to the agent.** "Lead with the outcome," not "the
  agent should try to lead with the outcome."
- **Do not overfit to one anecdote.** The parsing-failure story is an example,
  not the spec. Generalize the move, then keep the example as illustration.
- **Name it plainly.** `audience-desi-lensing-wg`, not `audience-custom-1`.
- **Reread it cold and cut.** Lines that are not pulling weight cost attention on
  every future invocation.

### Student-type skills

Fire this when the **reader** is student-shaped: the prior is `audience-student`,
or the gap-handling dial says "a question that gets me there" *about the reader*.
In second-hand mode the dial answer is about the author unless you asked the
reader-facing version, so it does not trigger anything on its own. A WG lead who
personally likes Socratic treatment does not make their working group a class.

When it does fire, the generated skill inherits the moves from
[`docs/sources/learning-prompt.md`](../../docs/sources/learning-prompt.md):
restate before explain, incremental mastery gates, a running comprehension
checklist, drill the whys, quiz without revealing, do not end until verified.

**Gate them by time budget.** That prompt was abandoned by a group member purely
on time — it is excellent and it costs thirty minutes.

The budget here is the **reader's**, not the interview's. Copy only the bullets
the gate allows; the template marks each one.

- **An hour or more** — all six bullets, plus the five-minute artifact.
- **Fifteen** — restate-first, drill-the-whys, and the five-minute artifact. No
  ledger, no quiz. Keep "do not end until verified" in its short form: name the
  one thing they should be able to do, check that, stop.
- **Two minutes** — no bullets at all. The five-minute artifact is the whole
  teaching section: what kind of thing it is, the one mechanism, the common
  error, what we skipped.

## Handing it over

Short. Five things, no ceremony:

1. Where the file is. If it went to `~/.claude/skills/`, say it is already live —
   it fires in any new session, and `/context` lists it if they want to check.
2. The reader model quoted inline, with "correct me if that is wrong."
3. The two or three lines you were least sure about, named as guesses.
4. One trigger phrase they can try right now.
5. The standing offer: "come back in three months when you know this group
   better and we regenerate it."

Then stop. Do not walk them through the whole file — they will read it. Never ask
the user to write a section themselves; if a slot is empty, ask one more question
or cut it. Offer the with/without eval loop (`evals/README.md`) as an option;
most users want the file and nothing else.

## Re-interviewing

An audience skill goes stale because the user's model of the team improves. When
asked to update one: read the existing file first, ask what changed and what
turned out wrong, ask Q10 again — examples turn over faster than anything else —
and **edit in place rather than regenerating**. The user's own edits are the most
valuable content in the file; anything that does not look like generated text is
theirs and it survives. Preserve the `name` and the directory. Move settled items
out of `Open questions`. If the skill has a `references/` sibling, check it too —
content pushed there during generation goes stale the same way, and an update
that only touches `SKILL.md` misses it.

## Failure modes to watch for

- **Interrogation.** Twelve questions to a person who said two minutes.
- **Generic output.** If the generated skill would fit any team, you did not use
  the interview. Their project nouns should appear in it.
- **Guessing to fill the template.** Empty is honest; invented is not.
- **Ignoring the prior.** Ten unrelated skills instead of ten specializations.
- **Treating a second-hand model as first-hand.** Say whose model it is. The
  sharpest form: mapping the author's own role to the prior, and generating the
  register for an advisor when they are writing *to* people they advise.
- **Importing the interview budget into the reader model.** Their two spare
  minutes are not their working group's reading habit.
- **Handing back an essay.** They asked for a file, not a lecture about the file.
- **Slop.** No "Great question!", no "comprehensive framework", no bullets that
  restate their own headings.

## Open for the group

- Profiles of real people are a privacy surface. We default to `~/.claude/skills/`
  for that reason. Is that enough?
- What is cached per person and what is re-asked per artifact? Time changes every
  session; domain knowledge does not.
- Can a profile be drafted from history instead of an interview? T7 in
  `evals/tasks.md`.
