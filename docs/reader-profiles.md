# Reader profiles

**v0 draft.** Tear it apart.

## Roles are priors, not boxes

The four roles — student, collaborator, advisor, prompter — are broad strategies
for broad groups. They are useful because most readers are near one of them. They
are wrong because no reader sits exactly on one.

A role is a **prior**. It is where you start when you know nothing else. The real
object we want is a **reader profile**: a short, specific description of the
person about to read this, built by asking them.

So the layering is:

```
role (prior)  →  short interview  →  reader profile (posterior)  →  register
```

The role skills stay useful either way. A profile does not replace them; it tells
you which one to load and what to override.

## The standard-question interview

Short. Four questions. Ask them once, at the start, and reuse the answers.

### 1. How much time do you have right now?

**This is the first question and it is not negotiable.** A profile without a time
budget mis-sizes everything downstream.

Evidence from the group: we killed a genuinely good learning prompt purely on
time. Not because it was wrong — because nobody had thirty minutes. The register
had been chosen without knowing the budget, and the budget decided.

Time changes the *form*, not just the length. Five minutes of a student's time is
not a compressed tutorial; it is a different artifact.

### 2. What role are you closest to?

Student, collaborator, advisor, prompter. Ask, do not infer. "None of these, but
closest to X" is the most useful possible answer.

### 3. Knowledge entering, and context held?

These are two separate axes and collapsing them is the most common modelling
error.

- **Knowledge entering** — domain expertise. What they know about the field and
  the methods, independent of this project.
- **Context held** — day-to-day project state. Which run is which, what broke
  last week, what was decided on Tuesday.

The four roles are corners of this 2×2:

| | **Low context held** | **High context held** |
|---|---|---|
| **High knowledge** | Collaborator (peer, no trench time) | Advisor (holds the big picture, not your week) |
| **Low knowledge** | Student | Prompter (knows the goal, not the work) |

Read the corners as tendencies, not definitions. The advisor sits high on context
in the *strategic* sense and low in the *operational* one, which is exactly why a
2×2 is a sketch and a profile is the real thing.

### 4. What do you want to be able to do afterward?

Roles are ultimately defined by goals, not by knowledge state. The student's role
is not "knows less" — it is "wants to be able to answer questions about this
afterward". That goal is what makes scaffolding correct for them and wrong for
the advisor.

Ask for the goal. Accept answers like "decide whether to fund it", "reproduce it
next month", "not be lost in the group meeting".

## Reveal the assumptions

Before writing, the agent states its model of the reader, in two or three lines,
and invites correction.

> Writing this for: a peer, no context on my last week, ten minutes, wants to
> know whether to rerun their half. Correct me if that is wrong.

Cheap, fast, and it catches the mis-model before the artifact is built rather
than after. It also makes the model visible, which is the point — a silently
assumed reader cannot be argued with.

This pairs with the *declared beats sniffed* principle in the README. The agent
declares its model; the reader confirms or corrects it. Nothing is inferred from
cues and quietly acted on.

## Profile from history

The interview is the reliable path. There is a cheaper one: build the profile
from what already exists — memory files, past sessions, prior artifacts written
for this person.

Sketch:

1. Gather the history for this reader (session transcripts, memory, past
   documents).
2. Extract: what they already know, what they had to ask about, how long their
   replies suggest they read for, what they did with the output.
3. Emit a draft profile. Show it. Let them correct it.

Open question, and a real one: **how do you sweep the history?** One agent going
session by session, accumulating a profile, versus a fan-out of subagents each
reading a slice and a merge at the end. The first keeps continuity and drifts
slowly. The second is fast and may produce a profile that contradicts itself.

That comparison is itself an eval. It is filed as **T7** in
[`../evals/tasks.md`](../evals/tasks.md).

## The architecture, in one sentence

> **The LLM's job is to model the reader; the skill's job is to supply the best
> practices that merge with that model.**

The skill does not contain the reader. It contains what we know about writing
well for readers of that shape. The model supplies the specific person.

## Open for the group

- How much of the interview can be asked once per collaborator and cached, versus
  re-asked per artifact? Time budget clearly changes every session. Domain
  knowledge does not.
- Does a profile belong in the repo, in a project `CLAUDE.md`, or in the agent's
  memory? Profiles of real people are also a privacy surface.
- Is there a fifth question we are missing? Candidates: what medium (chat, doc,
  slides), and who else will read this later.
