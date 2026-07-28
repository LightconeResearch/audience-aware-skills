---
name: team-norms
description: Apply collaboration etiquette when posting to a shared surface — GitHub PRs and issues, team Slack, mailing lists, or any channel other humans read. Use before opening a PR, commenting on an issue, posting a status update, tagging a person, or sending anything to a group. Covers update batching, concision, and when to involve a human; the Team profile section customizes it per group.
---

# Team norms

**v0 draft.** The general section asserts things we believe are near-universal.
The `## Team profile` section is where a group overrides them.

## Why this exists

Role tells an agent what *register* to write in. Norms tell it what *etiquette*
to observe: how often to post, how long, to whom.

An agent can produce six PR comments in a row totalling five pages. Each may be
individually correct. Together they are a cost imposed on everyone subscribed to
the thread. Nobody reads the sixth. Some people stop reading the first.

**Concision is respect.** The unit of cost is not your tokens. It is your
collaborators' attention, which is finite and shared.

## General norms

We think these hold almost everywhere. Argue with any of them.

### Batching

- **One update per unit of work, not per step.** Finish the thing, then post.
- **Do not narrate progress in a shared channel.** Progress belongs in your own
  notes. Outcomes belong in the channel.
- **Amend rather than append.** A PR description you own gets edited in place. A
  new comment for every revision buries the thread.
- **If you are about to post twice in a row, don't.** Combine, or wait.

### Length

- **A PR description fits on one screen.** What changed, why, how to check it.
- **An issue comment is a few paragraphs at most.** Longer content goes in a
  linked file or a collapsed `<details>` block.
- **Never paste a long log.** Paste the six lines that matter and link the rest.
- **Length signals importance.** A long post claims a large share of attention.
  Make sure it earns it.

### Tagging people

- **Tag when you need an action or a decision from that specific person.**
- **Do not tag for visibility.** Visibility is what the channel is for.
- **Do not tag to be polite.** It is not polite; it is an interrupt.
- **One tag per ask.** Tagging four people means nobody thinks it is theirs.

### Conversational replies

- **A reply to a person is not a status update.** It is a conversation. Answer
  the point they made, in a couple of sentences.
- **Get human approval before posting a conversational reply**, especially one
  that tags someone. Draft, show, then post. Routine non-conversational updates
  (editing your own PR body) do not need this.
- **Never post disagreement without a human reading it first.**

### Signing

- When an agent writes a post on a person's account, sign it: `— <agent name> on
  behalf of <person>`. Readers deserve to know what they are replying to.

### Restraint

- **Not everything you find needs saying.** The most common agent failure on a
  shared surface is volume, not error.
- **Silence is a valid output.** No update is better than a null update.

## Team profile

Fill this in for your group. An unfilled template is generic advice; a filled one
is usable.

Copy the questions, answer them, and keep the answers in this file (or in a
project `CLAUDE.md` that points here).

### Intake questions

**Cadence**
1. How often does this team want progress updates? (per-PR / daily / weekly /
   only when done / only when blocked)
2. Is there a standing meeting that updates should feed rather than replace?

**Channels**
3. Which surface is for what? (issues vs PRs vs Slack vs email)
4. Which channels are high-attention — where a post costs a lot?
5. Is there a low-stakes channel where verbosity is fine?

**Length**
6. What is a long post here — a screen? A paragraph? A page?
7. Does this team prefer prose, bullets, or tables?

**Tagging and approval**
8. Who may be tagged directly, and for what?
9. Does anything need human approval before posting? (default: yes for replies
   to people)
10. Who is the reviewer of record for outgoing communication?

**Register**
11. Formal or casual? Emoji or not?
12. Are agent-authored posts signed as such? Required or discouraged?

**Local rules**
13. What is a norm here that an outsider would get wrong?
14. What has annoyed people in the past?

### Example filled profile

> **Team:** Lightcone Research, summit working group.
>
> **Cadence.** Updates when a piece lands, not while it is in progress. No daily
> standup posts. Blocked items surface immediately.
>
> **Channels.** GitHub issues hold discussion and decisions. PRs hold the change
> and its review. Slack is for coordination and things that expire within a day —
> nothing durable lives there.
>
> **Length.** One screen for a PR description. A few paragraphs for an issue
> comment. Anything longer becomes a file in the repo with a link.
>
> **Tagging.** Tag one person, when you need something specific from them. Do not
> tag the group. Do not tag for FYI.
>
> **Approval.** Any reply to another person is drafted and shown to Cail before
> posting. PR bodies and issue descriptions the agent owns are edited freely.
>
> **Register.** Casual is fine. Simplified Technical English discipline for
> anything a collaborator reads to get oriented: short sentences, active voice,
> one claim per sentence. Dry wit permitted; stacked subordinate clauses not.
>
> **Signing.** Agent-authored posts sign `— <name> on behalf of Cail`.
>
> **Local rule an outsider would get wrong.** Describe the state, not the
> journey. Commits, PRs, and docs say what is true now. Chronology goes in a
> dedicated history surface or nowhere.
>
> **What has annoyed people.** Volume. Five pages of PR commentary across six
> comments, where one paragraph was needed.

## Failure modes to watch for

- **Norm theater.** Announcing "I'll keep this brief" and then not.
- **Batching into a monolith.** Batching means fewer posts, not one enormous one.
- **Over-asking for approval.** The approval rule covers conversational replies,
  not every edit.
- **Applying one team's profile to another team's channel.** Check whose surface
  you are on.

## Open for the group

- How much of the general section survives contact with a second team? We suspect
  batching and tagging are universal; length norms probably are not.
- Should the profile live in the skill, or in a separate config the skill reads?
- Is there a norms axis for *how much the agent should think out loud* in public?
