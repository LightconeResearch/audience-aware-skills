# audience-aware-skills

Agent communication about research should adapt to **who reads it**.

A status update for the person who asked for the work is not the same document as
an explanation for a student. A note to a supervisor is not a note to the
colleague on the other half of the project. Today most agents write one register
for everyone: complete, eager, long. That register is wrong for almost every
reader.

This repo's product is [`skills/audience-definition/`](skills/audience-definition/SKILL.md):
a meta-skill that interviews you about one real audience and generates a small,
editable communication skill for it. Run it, get your skill.

Seeded at the AAI4Science Developer Summit. Issue:
https://github.com/LightconeResearch/AAI4ScienceDeveloperSummit/issues/12

Everything here is a draft. Tear it apart.

## The two axes

**Axis 1 — reader role.** Who is reading, and what do they already know?

| Role | Relative to the author | Wants |
|---|---|---|
| **Student** | Knows less | To understand. Not to be handed the answer. |
| **Collaborator** | Knows as much; holds none of your day-to-day state | The high-level picture, with local detail on demand. |
| **Advisor / Supervisor** | Knows *differently* — bigger picture, funding, authority | The decision points and what they imply. |
| **Prompter** | Asked for the work | The outcome and the decisions. Minimal ceremony. |

The collaborator is a peer on your team with the same scientific goal — a
postdoc, a PhD student, faculty who is not your advisor. The delta is not
knowledge, it is **trench time**: they have not fought your bug for a week.

The advisor is often a human with five minutes. The prompter is the person in
the terminal right now.

Roles are **priors, not boxes**. No real reader sits exactly on one. The layer
above them is a reader profile built by a short interview — see
[`docs/reader-profiles.md`](docs/reader-profiles.md).

Formal peer review — adversarial claims-and-evidence, a referee trying to break
the work — is a distinct mode and is *not* the collaborator skill. It may get its
own skill later.

**Axis 2 — team norms.** How does this group want to be communicated with?

Role tells you the register. Norms tell you the etiquette: how often to post, how
long an update may be, when to tag a human, when to stay quiet. Six PR comments
in a row producing five pages of text is not thoroughness. It is a cost imposed
on collaborators.

Some norms are close to universal (concision is respect). Some are local (this
lab wants a daily digest; that one wants nothing until it is done). So
`archive/skills/team-norms/` is a template plus an intake you fill in for your team.

## Regardless of role

Four things hold across every register. Each role skill states its own version in
one line; the general form lives here.

**Uncertainty tolerance scales with the reader's ability to push back.** An
expert can challenge a wrong claim cheaply — it costs them a sentence. A student
cannot; they absorb the error and build on it. So the rule is asymmetric. For a
high-pushback reader you may think out loud freely. For a low-pushback reader,
either be very sure, or say out loud that you are not. Every role skill's reader
model carries a line on what it costs *that* reader when the author is wrong.

**Declared beats sniffed.** Never infer the reader's expertise from cues in their
message and then quietly steer. Reading someone as a novice because they used a
plain word is a guess acted on invisibly, and it is condescending when wrong. The
reader model comes from the **declared** role or profile. The register rule that
follows: present options and your reasoning. Go first with your own view — "you
go first" is the agent's job — but the reader decides. Do not foreclose.

**Critical thinking is universal, not role-gated.** A student has as much
critical-thinking potential as an advisor. Only the knowledge differs. So every
register invites pushback, and every register welcomes the reframing question —
"why are we asking it this way at all?" Naive questions are generative. Anyone
who has done outreach knows this: the question from outside the lock-in is the
one that opens a new area. The student skill in particular must not treat
scaffolding toward the known answer as its only job.

**Agents ask first.** "Better to ask forgiveness than permission" is advice for
humans, who bear the consequences of their own actions. Agents invert it. An
agent acting on someone's behalf asks before the irreversible or the
consequential — posting, sending, publishing, deleting. This one also lives in
`archive/skills/team-norms/`.

## The product: define your own audience

The roles above are **priors**. Real work happens in a named context — the DESI
lensing WG where you lead, the Rubin channel where you are one of hundreds, the
one student you advise. Each of those deserves its own skill.

[`skills/audience-definition/`](skills/audience-definition/SKILL.md) is the
meta-skill that makes them. It interviews you about one audience — four standard
questions from the group, plus as much more as your time budget allows — merges
your answers with the universal best practices in
[`assets/template.md`](skills/audience-definition/assets/template.md), and hands
back a small `SKILL.md` you edit and keep. It writes into `~/.claude/skills/` by
default, so it is live immediately and profiles of real colleagues stay out of
git. You never write it yourself. You
re-interview later, when your model of the team has moved.

```
"create a communication skill for my DESI lensing working group"
```

The v0 role skills in `archive/` are what it starts from; the generated skill is
a specialization of one of them, not a fresh essay. That is what keeps ten of
them consistent with each other.

## Where this plugs in

Not only chat. The larger target is **agent-generated science communication
artifacts** — text about research that a model writes and a human reads.

The concrete case that prompted this: Lightcone's ASTRA → MyST report generation.
The `lc` report flow turns an analysis spec and its results into a narrative
write-up. Today that narrative is written for an unnamed audience, which in
practice means a generic one. These skills make **"who is this report for?"** a
parameter of the generation.

Generalize from there. Anything that communicates science with generated text —
reports, summaries, docs, figure captions, release notes, meeting briefs — has a
reader, and today most of them do not name one.

## Repo layout

```
README.md                        you are here
CONTRIBUTING.md                  how to tune a skill, evolve a prior, run an eval
skills/
  audience-definition/           THE PRODUCT: interview → generated audience skill
    SKILL.md                     the interview and how to draft from it
    assets/template.md           skeleton of a generated skill: constants + slots
archive/
  README.md                      why these are kept, not deleted
  skills/                        the v0 role skills: student, collaborator, advisor,
                                  prompter, team-norms — audience-definition's priors
evals/
  README.md                      with/without protocol and judging rubric
  tasks.md                       concrete eval tasks
docs/
  reader-profiles.md             roles as priors; the interview that builds a profile
  sources/learning-prompt.md     pedagogy that student-type skills inherit
```

The architecture, in one sentence:

> **The LLM's job is to model the reader; the skill's job is to supply the best
> practices that merge with that model.**

Skills use the Claude Code format: a directory under `skills/`, containing
`SKILL.md` with YAML frontmatter (`name`, `description`) and a markdown body. The
`description` states when the skill should trigger.

## The eval loop

We do not want to guess whether these help. The loop:

1. Pick a task from `evals/tasks.md`.
2. Run it **without** the skill. Save the output.
3. Run it **with** the skill. Save the output.
4. Have an agent role-play the target reader. It scores both outputs blind,
   against the rubric in `evals/README.md`.
5. Record the scores. Note what the skill changed and what it broke.

Group members take one role each, then rotate. Rotating matters: the person who
wrote the student skill is the worst judge of it.

Full protocol in [`evals/README.md`](evals/README.md).

## Quickstart

Clone the repo and point your agent at the generator.

```bash
git clone https://github.com/LightconeResearch/audience-aware-skills.git
cd audience-aware-skills
mkdir -p ~/.claude/skills
ln -s "$PWD/skills/audience-definition" ~/.claude/skills/audience-definition
```

Then ask for a skill for a real audience:

```
"create a communication skill for my DESI lensing working group"
```

`audience-definition` interviews you — starting with how much time you have —
and writes a small `SKILL.md` to `~/.claude/skills/audience-<slug>/`, live
immediately. You edit it and keep it; re-run the interview when your model of
the audience moves.

If you want a specific v0 role skill directly rather than a generated one —
useful for eval baselines or quick experiments — they still work, symlinked
straight from `archive/skills/`:

```bash
ln -s "$PWD/archive/skills/audience-advisor" ~/.claude/skills/audience-advisor
```

To use `team-norms` this way, fill in its `## Team profile` section first. The
template without a profile is generic. With one it is useful.

## Friday demo target

1. A set of skills. (`skills/`)
2. An evaluation of them. (`evals/`)
3. Documentation and a template for adjusting them. (`CONTRIBUTING.md`,
   `docs/reader-profiles.md`, the team profile intake.)

## Open questions

- Do roles compose? "Explain to a student, but my advisor is also reading."
- Is `prompter` a role or a default? Most agent output is already aimed there.
- Does formal peer review deserve its own skill, and is the AI referee a third
  mode again?
- How much of team-norms is really universal? We assert some. We may be wrong.
- How far does the profile layer go before roles stop earning their keep?
