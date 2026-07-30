# audience-aware-skills

Agents write about research in one register for everyone: complete, eager,
long. That register is wrong for almost every reader. The **reader** is the
human who will read what the agent writes — a student, a peer, an advisor, the
person who asked for the work. Each reader deserves a different register.

The product is [`skills/know-your-audience/`](skills/know-your-audience/SKILL.md).
It interviews you about one real audience. It then writes that audience into
your **single personal communication skill**: universal preferences once in
the body, one editable reference file per audience. The agent is always the
author — the skill governs how it writes to you and to the people it writes
to on your behalf. The common roles (student, collaborator, advisor,
prompter) are **priors**, not boxes: the interview turns a prior into a
profile of your reader, and the profile sets the register. Where the
interview contradicts the prior, the interview wins.

Seeded at the AAI4Science Developer Summit
([issue #12](https://github.com/LightconeResearch/AAI4ScienceDeveloperSummit/issues/12)).
Everything here is a draft. Tear it apart.

## Install

**Claude Code**:

```bash
claude plugin marketplace add LightconeResearch/audience-aware-skills
claude plugin install audience-aware-skills@lightcone
```

**Codex**:

```bash
codex plugin marketplace add LightconeResearch/audience-aware-skills
codex plugin add audience-aware-skills@lightcone
```

**Manual** (any agent that reads an Agent Skills directory):

```bash
cp -r skills/know-your-audience ~/.claude/skills/
```

## Layout

```
skills/know-your-audience/   The product: interview → generated audience skill.
.agents/plugins/             Codex marketplace manifest.
.claude-plugin/              Claude Code marketplace and plugin manifests.
.codex-plugin/               Codex plugin manifest.
evals/                        With/without-skill comparison protocol and tasks.
archive/skills/               v0 per-role skills — the priors' provenance.
CONTRIBUTING.md               How to tune a skill, evolve a prior, run an eval.
```

## Friday demo target

1. A set of skills. (`skills/`)
2. An evaluation of them. (`evals/`)
3. Documentation and a template for adjusting them. (`CONTRIBUTING.md`)

Content lands via pull request so the group can comment on it.
