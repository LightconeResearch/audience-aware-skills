# Contributing

This is a working-group repo, not a product. Drafts are welcome. Half-finished
skills with a note saying what is missing are welcome. Disagreement in a PR
description is welcome.

Open a PR. If you are not sure it is right, open it as a draft and say so.

## Repo conventions

- Skills live in `skills/<name>/SKILL.md`.
- Frontmatter is YAML with `name` and `description`. The `description` states
  **when the skill should trigger** — the agent reads it to decide. Write it as
  trigger conditions and example phrasings, not as a summary.
- Body is markdown. Aim for 100-200 lines. Longer means the agent will skim it
  the same way a human would.
- Every skill ends with an `## Open for the group` section. Say what you are
  unsure about. That section is the point of a v0.

## Adding a new role

This describes evolving the priors that `audience-definition` generates from —
`archive/skills/`. Most new audiences don't need a new role; they need an
interview with `audience-definition`. Add a role only when it earns a distinct
place on both axes below, not per-team or per-person.

1. **Justify the role on two axes, not one.** Knowledge entering (domain
   expertise) and context held (day-to-day project state) are separate. A new
   role needs a distinct position on both, plus a distinct answer to what they
   are reading *for*. See
   [`skills/audience-definition/assets/priors.md`](skills/audience-definition/assets/priors.md).
   Round 2 example: "collaborator" earned its place once we saw the delta from
   the author is trench time, not knowledge. "Funder" might earn one: knows less
   about the method, reads for whether to keep paying.

2. **Create `archive/skills/audience-<role>/SKILL.md`** with these sections, in order:
   - frontmatter (`name`, `description` with triggers)
   - `## Reader model` — what they know, what context they hold, what they want,
     what time they have, and **what it costs this reader when the author is
     wrong** (the uncertainty-tolerance line; see *Regardless of role* in the
     README)
   - `## Register rules` — what to lead with, what to withhold, length discipline
   - `## Do / don't` — at least three concrete paired examples, with real text.
     Abstract advice does not change agent behavior; examples do.
   - `## Structure that works` — a skeleton, if there is one
   - `## Failure modes to watch for`
   - `## Open for the group`

3. **Add a task to `evals/tasks.md`** that discriminates for the new role.

4. **Add per-role rubric rows to `evals/README.md`.**

5. **Add the role to the table in `skills/audience-definition/SKILL.md`'s
   priors list**, and to the two-axes table in `README.md` if it changes that
   framing.

6. **Run at least one eval before merging.** An unevaluated role is a guess.

## Adjusting a skill for your team

Do not fork the whole repo.

**For team etiquette**, fill in the `## Team profile` section of
`archive/skills/team-norms/SKILL.md`. Answer the intake questions for your group. Keep
your filled profile in your own copy, or contribute it back as an additional
example — a second filled profile is genuinely useful, because it shows which
general norms survive contact with another team.

**For role register**, add a `## Local overrides` section at the end of the role
skill:

```markdown
## Local overrides

**Team:** <group>

- Our advisor wants the plot first, before any text.
- Updates go in the weekly doc, never in Slack.
- We say "collaborator" for anyone in the consortium, not just our own team.
```

Overrides beat the general body. State that if it is not obvious to the agent.

If your override feels like it should be general, propose it. That is how the
universal section gets tested.

## Running an eval

Follow [`evals/README.md`](evals/README.md). Short version:

1. Pick a task from `evals/tasks.md`.
2. Generate control (no skill) and treatment (skill loaded), same prompt.
3. Judge blind with a role-playing agent.
4. Add a row to `evals/results.md` with the scores and a two-line note.

**Do not judge your own skill.** Trade with someone. The rotation is not
ceremony — an author cannot see their own skill's blind spots, and this is the
one part of the loop that keeps us honest.

Commit the raw outputs under `evals/runs/<task-id>/`. Numbers without artifacts
cannot be re-examined.

## Proposing changes to an existing skill

- **Small edits** (a better example, a clearer rule): open a PR, no ceremony.
- **Structural changes** (removing a rule, changing the reader model): open a PR
  and say what evidence prompted it. Ideally an eval result. A strong intuition
  is also fine — say that it is one.
- **Disagreement with a rule:** the fastest path is an eval where following the
  rule scores worse. Second fastest is a `## Open for the group` entry.

## PR etiquette here

We are writing a skill about collaboration etiquette. It would be poor form to
ignore it.

- One PR per idea.
- PR description on one screen: what changed, why, how to check.
- Amend the description; do not append comments to revise it.
- Tag someone only when you need something from them.

## Style

- Short sentences. Active voice. One claim per sentence.
- Roles are priors, not boxes. Write them that way; no skill should imply its
  reader is a fixed type.
- Concrete over abstract. Show the bad output and the good one.
- Mark uncertainty as uncertainty. "We think" is a fine thing to write.
- No emoji in skill bodies.
