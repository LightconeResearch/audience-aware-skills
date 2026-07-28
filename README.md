# audience-aware-skills

Agent communication about research should adapt to **who reads it**.

A status update for the person who asked for the work is not the same document as
an explanation for a student. A note to a supervisor is not a note to a peer
reviewer. Today most agents write one register for everyone: complete, eager,
long. That register is wrong for almost every reader.

This repo holds v0 skills that make an agent pick a register on purpose, plus a
way to check whether the skills actually help.

Seeded at the AAI4Science Developer Summit. Issue:
https://github.com/LightconeResearch/AAI4ScienceDeveloperSummit/issues/12

Everything here is a draft. Tear it apart.

## The two axes

**Axis 1 — reader role.** Who is reading, and what do they already know?

| Role | Assumed knowledge | Wants |
|---|---|---|
| **Student** | Less than the author | To understand. Not to be handed the answer. |
| **Reviewer** | As much as the author | To find what is wrong. Claims, evidence, gaps. |
| **Advisor / Supervisor** | More than the author | The decision points. Where judgment was exercised. |
| **Prompter** | Asked for the work | The outcome and the decisions. Minimal ceremony. |

In practice the reviewer is often an AI. The advisor is often a human with five
minutes. The prompter is the person in the terminal right now.

**Axis 2 — team norms.** How does this group want to be communicated with?

Role tells you the register. Norms tell you the etiquette: how often to post, how
long an update may be, when to tag a human, when to stay quiet. Six PR comments
in a row producing five pages of text is not thoroughness. It is a cost imposed
on collaborators.

Some norms are close to universal (concision is respect). Some are local (this
lab wants a daily digest; that one wants nothing until it is done). So
`skills/team-norms/` is a template plus an intake you fill in for your team.

## Repo layout

```
README.md                      you are here
CONTRIBUTING.md                how to add a role, tune a skill, run an eval
skills/
  audience-student/SKILL.md    teach; check comprehension before revealing
  audience-reviewer/SKILL.md   claims and evidence; invite attack
  audience-advisor/SKILL.md    decisions and judgment calls; assume expertise
  audience-prompter/SKILL.md   outcome first; no ceremony
  team-norms/SKILL.md          collaboration etiquette + team profile intake
evals/
  README.md                    with/without protocol and judging rubric
  tasks.md                     concrete eval tasks
```

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

Clone the repo and point your agent at the skills.

```bash
git clone <this-repo>
cd audience-aware-skills
```

For Claude Code, symlink or copy a skill into your project:

```bash
mkdir -p ~/.claude/skills
ln -s "$PWD/skills/audience-advisor" ~/.claude/skills/audience-advisor
```

Then ask for work aimed at a reader: "summarize this PR for my advisor",
"explain this analysis to a first-year student". The description in each
`SKILL.md` decides whether the skill fires.

To use the team-norms skill, first fill in the `## Team profile` section with
your group's answers. The template without a profile is generic. With one it is
useful.

## Friday demo target

1. A set of skills. (`skills/`)
2. An evaluation of them. (`evals/`)
3. Documentation and a template for adjusting them. (`CONTRIBUTING.md`,
   the team profile intake.)

## Open questions

- Do roles compose? "Explain to a student, but my advisor is also reading."
- Is `prompter` a role or a default? Most agent output is already aimed there.
- Does the reviewer skill differ when the reviewer is an AI rather than a human?
- How much of team-norms is really universal? We assert some. We may be wrong.
