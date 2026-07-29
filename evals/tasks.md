# Eval tasks

Seven tasks. Each names a target role and gives a prompt to run verbatim in both
the control and treatment conditions.

Rules:
- **Run the prompt as written.** Do not add "be concise" or "explain simply" —
  that is the skill's job, and adding it destroys the comparison.
- The prompt must not name the skill or the role's vocabulary.
- Substitute your own subject matter where a task says `<...>`. Keep the same
  substitution across control and treatment.

---

## T1 — Explain an analysis to a student

**Role:** student
**Skill under test:** `audience-student`

> A second-year PhD student has joined the project. They know undergraduate
> statistics and some Python. They have not worked with `<method / analysis>`
> before. Help them understand how it works and why we do it this way.

**What discriminates:** does the output ask before telling? Does it check whether
the student followed, and does the check do any work?

**Judge persona:** "You are that second-year student. You are motivated but you
have never seen this method."

---

## T2 — Summarize a week of work for a supervisor

**Role:** advisor
**Skill under test:** `audience-advisor`

Supply the agent with a real work record: a git log, a set of notes, or a session
transcript covering a few days.

> Here is what I did this week: `<git log / notes>`. Write the update I send to
> my supervisor.

**What discriminates:** decisions versus chronology. Is the uncertain call
flagged? Is there a clear ask? Does it fit on one screen?

**Judge persona:** "You are the PI. You supervise six people. You have four
minutes and you are between meetings."

---

## T3 — Brief a teammate after a week in the weeds

**Role:** collaborator
**Skill under test:** `audience-collaborator`

Supply a real work record from a week that went deep on one problem: a git log, a
session transcript, a set of notes. It must contain local state — run names,
branch names, a dead end.

> Here is my week: `<record>`. Write the message I send to `<colleague>`, who
> works on the other half of this project.

**What discriminates:** does it lead with where things stand, or with the
journey? Are local names glossed? Is what changed *for the reader* stated early?
Are guesses marked as guesses?

**Judge persona:** "You are a postdoc on the same project. You know the field and
the goal as well as they do. You have not touched their code in two weeks."

---

## T4 — Report back on a completed task

**Role:** prompter
**Skill under test:** `audience-prompter`

Give the agent a small, real, self-contained job — fix a bug, add a flag, write a
function — with at least two decisions embedded (an ambiguous naming choice, an
optional check that is slow).

> `<the task>`. When you're done, tell me what happened.

**What discriminates:** outcome in the first sentence. Are the two embedded
decisions surfaced? Is there ceremony?

**Judge persona:** "You asked for this and then went to lunch. You are back and
you have one minute before your next thing."

---

## T5 — Post a PR update to a shared thread

**Role:** any (norms axis)
**Skill under test:** `team-norms`, with a filled team profile

Set up a PR with three rounds of review feedback already applied.

> I've addressed all the review comments on this PR. Post the update to the
> thread.

**What discriminates:** one post or several? Is the description amended rather
than appended? Is anyone tagged, and is the tag earned? Is a log pasted whole?

**Judge persona:** "You are a collaborator subscribed to this PR. You get every
notification. You have thirty other threads."

---

## T6 — The same content, four ways

**Role:** all four (cross-cutting)
**Skill under test:** all four audience skills

Take one substantive result — a real finding with a caveat.

> Write up `<the result>` for: (a) a student who has not met the method, (b) a
> colleague on the other half of the project, (c) my supervisor, (d) me, since I
> asked for it.

Run once without skills, once with all four loaded.

**What discriminates:** without skills, the four outputs tend to be the same
document at four lengths. With skills they should differ in **what is led with**
and **what is omitted**, not only in verbosity.

**Judge:** four judges, one per persona. Each scores only their own version.
Then ask a fifth: "are these four genuinely different documents, or one document
resized?" This task records four rows in the results table — T6-student,
T6-collaborator, T6-advisor, T6-prompter — plus a free-text note from the fifth,
meta-judge pass.

This is the best single demo of the premise. If T6 does not show a difference,
the premise is in trouble and we should know that on Friday.

---

## T7 — Build a reader profile from history

**Role:** cross-cutting (the profile layer, not a register)
**Skill under test:** none yet — this evaluates a *method*, not a skill

See [`../skills/audience-definition/SKILL.md`](../skills/audience-definition/SKILL.md).
A reader profile
can be built by interview, or reconstructed from history: memory files, past
sessions, prior artifacts written for that person.

Pick a real reader with a history in the repo or in session logs.

> From this history, build a profile of `<reader>`: what they know, what project
> context they hold, how much they read, what they use the output for.

Run it two ways:

- **A — single sweep.** One agent walks the history session by session,
  accumulating and revising one profile.
- **B — fan-out.** Subagents each take a slice, then a merge pass reconciles.

**What discriminates:** this is not control-versus-treatment. It is a method
comparison. Judge on: is the profile internally consistent? Does it contradict
itself across periods? Does it catch change over time (the reader learned
something in month three)? What did each method miss that the other found? And
the cost: wall time and tokens.

**Judge persona:** the reader themselves, if they are willing. "Is this you?"
That is the only ground truth available and it is a good one.

**Why this matters:** if history-derived profiles work, the interview becomes a
correction step rather than the whole mechanism.
