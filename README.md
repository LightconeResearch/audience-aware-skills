# audience-aware-skills

Agents write about research in one register for everyone: complete, eager,
long. That register is wrong for almost every reader. The **reader** is the
human who will read what the agent writes — a student, a peer, an advisor, the
person who asked for the work. Each reader deserves a different register.

The product is [`skills/audience-definition/`](skills/audience-definition/SKILL.md).
It interviews you about one real audience. It then generates a small, editable
communication skill for that audience. The common roles (student, collaborator,
advisor, prompter) are **priors**, not boxes: the interview turns a prior into
a profile of your reader, and the profile sets the register. Where the
interview contradicts the prior, the interview wins. The skill is
self-contained — everything it needs is in its directory.

Seeded at the AAI4Science Developer Summit
([issue #12](https://github.com/LightconeResearch/AAI4ScienceDeveloperSummit/issues/12)).
Everything here is a draft. Tear it apart.

## Layout

```
skills/audience-definition/   The product: interview → generated audience skill.
evals/                        With/without-skill comparison protocol and tasks.
docs/sources/                 Credited source material.
archive/skills/               v0 per-role skills — the priors' provenance.
CONTRIBUTING.md               How to tune a skill, evolve a prior, run an eval.
```

## Friday demo target

1. A set of skills. (`skills/`)
2. An evaluation of them. (`evals/`)
3. Documentation and a template for adjusting them. (`CONTRIBUTING.md`)

Content lands via pull request so the group can comment on it.
