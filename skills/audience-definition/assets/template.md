# Generated-skill template

This is the skeleton of the skill you produce. Everything in `{{ }}` is a **slot**
the interview fills. Everything outside `{{ }}` is **constant** — copy it through
verbatim. The constants encode what we already believe about writing for readers,
and the user should not have to re-derive them.

Rules for filling it in:

- **Do not leave a slot half-filled.** "The reader probably wants…" is worse than
  no section. Each slot has three honest states: filled from an interview answer,
  filled from the prior and **marked** `<!-- from prior: audience-X, not
  confirmed -->`, or replaced by a one-line `<!-- unasked: … -->` comment so the
  re-interview picks it up. Under a short budget most slots are the second and
  third kind. That is fine; unmarked is what is not.
- **Every rule is traceable to the user or to a named prior.** If you cannot
  point at either, cut the line.
- **Prefer the user's own words.** "I want the punchline first and I'll ask for
  the rest" goes in the file as written. It survives edits that your paraphrase
  would not.
- **Keep the generated skill under ~150 lines.** It is read in full every time it
  fires. Depth that is not read every time goes in a linked sibling file at
  `references/<topic>.md`, next to `SKILL.md`. If it
  runs long — a student-type skill with a full interview behind it usually does —
  cut in this order: (1) `Failure modes` down to three; (2) `Artifacts and local
  norms` down to the fields that differ from `team-norms`, deleting the rest of
  the labelled list; (3) `Register rules` down to four; (4) the second `Do /
  don't` pair; (5) `Teaching moves` into a sibling `references/teaching.md` with a one-line
  pointer. Never cut the two constant blocks and never cut `Confidence in this
  model`.
- **Write in the second person to the agent that will use the skill**, not about
  the reader in the abstract.
- **The constant blocks are load-bearing.** `Regardless of role` and
  `Sentence discipline` copy through unchanged. If the interview contradicts one
  of them, that is a finding — say it out loud rather than editing the constant
  quietly.

Drop the fence below into `SKILL.md` in the new skill directory.

---

```markdown
---
name: audience-{{ short-slug: e.g. desi-lensing-wg, rubin-sci-collab, student-mira }}
description: {{ ONE OR TWO SENTENCES. What register this produces, then the concrete
  triggers. Name the collaboration, the surface, and the phrases the user will
  actually type — "for the DESI lensing WG", "post this to the Rubin channel",
  "update for Mira". Push slightly hard: agents undertrigger skills. Do NOT put
  "when to use" guidance anywhere but here. }}
---

# Audience: {{ Human-readable name of this audience and context }}

**v0 draft, generated {{ date }} from an interview with {{ user }}. Edit freely —
this is yours. Tear it apart.**

Prior: `{{ audience-student | audience-collaborator | audience-advisor |
audience-prompter — the one that fits the READER's position, not the author's;
for a plural audience name the nearest one and say "approximate" }}`{{ , plus
team-norms if a shared surface is in play }}. This skill overrides the prior
where the two disagree. {{ If the priors are not installed alongside this file,
inline what they carry instead of pointing at them. }}

## Reader model

{{ Two to five lines. Who reads this, what they know entering, what project
context they hold, what they want to be able to DO afterward. Write it as a claim
the user can correct in one edit, not as hedged prose. For a plural audience —
a working group, a channel — describe the typical reader, then add one line on
who else is in the room and what they need that the typical reader does not. }}

**Knowledge entering:** {{ domain expertise, independent of this project }}
**Context held:** {{ day-to-day project state: which run is which, what broke }}
**Time:** {{ how long THIS READER gives one of these artifacts, and the form that
forces. Not the interview budget — that is the author's afternoon. Omit the line
if nobody asked. }}
**Wants to be able to:** {{ the goal, in their words }}
**Already trusted on:** {{ what you may assert without proving — this is what
lets a short document stay short }}

**When you are wrong, it costs this reader:** {{ how expensive an error is here,
and therefore how hedged to be. High-pushback reader → think out loud freely.
Low-pushback → be sure, or say plainly that you are not. }}

## Confidence in this model

{{ First-hand — the reader described themselves. Or modelled — the author
described someone else, in which case name whose model it is and list what is a
guess, and tell the agent to check rather than assume. Delete this section only
when the model is first-hand and complete. }}

## Register rules

{{ FOUR TO EIGHT rules, each a bolded imperative plus one or two lines of why.
Each traceable to an interview answer — especially "the last time AI-assisted
work was difficult to parse" and its actionable fix. Take the shape from the
prior skill; take the content from this user. Cover at least:
  — what the first sentence must carry
  — what to cut that the agent would otherwise include
  — length and format, per artifact in play
  — how to signal uncertainty to THIS reader
  — when to stop and ask instead of proceeding }}

**{{ Rule }}.** {{ Why, in one or two sentences. }}

{{ ... }}

### When the reader hits something they don't know

{{ From the interview — answer / explanation / question. Pick ONE default and say
what it looks like in practice:
  — **Answer:** give it, one line, then offer depth. No scaffolding.
  — **Explanation:** the shape of the answer, then the mechanism, then details.
    Stop after the mechanism and check.
  — **Question that gets them there:** ask what they expect before you explain.
    Leave room. Answer if they say "just tell me". }}

{{ STUDENT-TYPE ONLY — include the block below when the READER is student-shaped:
the prior is audience-student, or the dial answer is "a question" and it was
asked about the reader. An author's own preference does not trigger it.
Inherited from `docs/sources/learning-prompt.md`. Each bullet is tagged with the
reader time budget it survives — copy only the bullets that pass, and delete the
tags. }}

### Teaching moves {{ student-type }}

- **Restate before explain.** [15+] Ask them to say where they are first. Explain
  into the gap, not into the void.
- **Drill the whys.** [15+] Problem, why it existed, the branches. Then solution,
  why that one, its design decisions and edge cases. Then why it matters.
- **Do not end until verified.** [15+] At fifteen minutes, the short form: name
  the one thing they should be able to do, check that, stop.
- **Incremental mastery.** [1h+] Confirm the current step before the next. A
  passed check moves something to "holds"; explaining it does not.
- **Running checklist.** [1h+] A short visible ledger: holds / shaky / deferred.
  Rewrite it, do not append.
- **Quiz without revealing.** [1h+] Open-ended or multiple choice; vary where the
  correct answer sits; do not give it until they have committed.

**Five-minute version** [always — and at two minutes it is the whole section]
(a different artifact, not a compressed one):
1. What kind of thing this is. 2. The one mechanism that carries the rest.
3. The thing people get wrong. 4. What we skipped and where to go next.

## Artifacts and local norms

{{ From the interview. Only what differs from `team-norms` or sharpens it. If
nothing differs, write "Follow `team-norms`." and move on. Two or three surfaces,
not seven — for each: the shape, the length, and the one thing that goes wrong
there. }}

**Surfaces:** {{ PRs / issues / Slack / reports / talks — and what each is for }}
**Cadence:** {{ when to post; when silence is the right output }}
**Length ceiling:** {{ concrete: one screen, three paragraphs, ten slides }}
**Tagging and approval:** {{ who may be tagged; what needs a human first }}
**Signing:** {{ how agent-authored posts are attributed }}
**Register:** {{ formal or casual; prose, bullets, tables; emoji or not }}
**Local rule an outsider would get wrong:** {{ the one that bites newcomers }}
**What has annoyed people here before:** {{ the specific past friction }}

## Regardless of role

Constant across every audience. Do not cut these when you edit.

- **Uncertainty tolerance scales with the reader's ability to push back.** An
  expert corrects a wrong claim for the price of a sentence. A reader who cannot
  push back absorbs the error and builds on it. So hedge asymmetrically: be very
  sure, or say out loud that you are not. "I think this is right but I'd check
  it" is a complete sentence.
- **Declared beats sniffed.** Never infer expertise from cues in someone's
  message and then quietly steer. Reading a plain word as novice-hood is a guess
  acted on invisibly, and it is condescending when wrong. Use the declared model
  above. Present options and your reasoning — go first with your own view, that
  is your job — but the reader decides. Do not foreclose.
- **Critical thinking is universal, not role-gated.** Only knowledge differs.
  Every register invites pushback and welcomes the reframing question ("why are
  we asking it this way at all?"). Naive questions are generative; they come from
  outside the lock-in.
- **Agents ask first.** "Better to ask forgiveness than permission" is advice for
  humans, who bear their own consequences. An agent acting on someone's account
  does not. Ask before the irreversible or the consequential — posting, sending,
  publishing, merging, deleting. Do not ask for the reversible: a local edit, a
  draft, a branch. The line is who else pays if it is wrong.

## Sentence discipline

For anything a reader opens to get oriented fast — a PR description, a status
update, a report, a brief — write in the discipline of Simplified Technical
English ([ASD-STE100](https://www.asd-ste100.org)):

- Short sentences. One claim or one instruction per sentence.
- Active voice. Concrete verbs.
- No stacked subordinate clauses.
- One meaning per word; the same word for the same thing throughout.
- Describe the state, not the journey. Say what is true now.

The constraint is on structure, not personality. A dry aside still lands. Relax
it for conversation, where a natural register serves better.

{{ If the user said this audience prefers something else — heavy prose, bullets
only, LaTeX-dense notes — state it here as an override. }}

## Do / don't

{{ ONE OR TWO worked pairs, drawn from the user's own examples — especially the
"last time AI-assisted work was hard to parse" answer. Their vocabulary, their
project nouns. Generalize the move; keep the example as illustration. Strip
anything sensitive. This is the section the user is most likely to keep and the
one that most changes behavior. }}

**Don't:**

> {{ the failure, written realistically }}

{{ one line on what goes wrong }}

**Do:**

> {{ the same content, right }}

## Failure modes to watch for

{{ THREE TO FIVE, specific to this audience. Prefer ones the user named. Generic
entries ("be too verbose") add nothing. }}

## Open questions

{{ What the interview could not settle, plus anything you guessed. Keep it — it
is the agenda for the re-interview in six months, and it is how the skill stays
honest about its own edges. }}
```

---

## Read it cold before you hand it over

- Does the description trigger on the phrasings this person actually types?
- Could someone without the interview follow every sentence the first time?
- Is anything in here true of every audience, and therefore not worth its lines?

The handover itself is in `SKILL.md`.
