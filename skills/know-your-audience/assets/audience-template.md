# Audience template — one reference file per audience

This is the skeleton of a per-audience reference file, written to
`references/<slug>.md` inside the user's communication skill (see
`body-template.md`). It carries everything specific to one audience and
nothing universal — the constant blocks live in the body, once.

Everything in `{{ }}` is a **slot** the interview fills. Rules:

- **Do not leave a slot half-filled.** "The reader probably wants…" is worse
  than no section. Each slot has three honest states: filled from an
  interview answer; filled from the prior and **marked** `<!-- from prior:
  audience-X, not confirmed -->`; or replaced by a one-line
  `<!-- unasked: … -->` comment so the re-interview picks it up. Under a
  short budget most slots are the second and third kind. That is fine;
  unmarked is what is not.
- **Every rule is traceable to the user or to a named prior.** If you cannot
  point at either, cut the line.
- **Prefer the user's own words.** They survive edits that a paraphrase
  would not.
- **Keep it under ~120 lines.** It is read in full whenever this audience is
  written for. Cut in this order: `Failure modes` down to three; `Artifacts
  and local norms` down to the fields that differ from the universal norms;
  `Register rules` down to four; the second `Do / don't` pair.
- **Write in the second person to the agent**, not about the reader in the
  abstract.

---

```markdown
# Audience: {{ human-readable name of this audience and context }}

**v0 draft, generated {{ date }} from an interview with {{ user }}. Edit
freely.**

Prior: `{{ audience-student | audience-collaborator | audience-advisor |
audience-prompter — the one that fits the READER's position relative to the
user; for a plural audience name the nearest one and say "approximate" }}`.
This file overrides the prior where the two disagree.

## Reader model

{{ Two to five lines. Who reads what the agent writes here, what they know
entering, what project context they hold, what they want to be able to DO
afterward. Write it as a claim the user can correct in one edit, not as
hedged prose. For a plural audience — a working group, a channel — describe
the typical reader, then one line on who else is in the room. }}

**Knows the field:** {{ domain expertise, independent of this project }}
**Knows the project:** {{ day-to-day state: which run is which, what broke }}
**Time:** {{ how long THIS READER gives one artifact, and the form that
forces. Not the interview budget. Omit the line if nobody asked. }}
**Wants to be able to:** {{ the goal, in their words }}
**Already trusted on:** {{ what you may assert without proving — this is what
lets a short document stay short }}

**When you are wrong, it costs this reader:** {{ how expensive an error is
here, and therefore how hedged to be. High-pushback reader → think out loud
freely. Low-pushback → be sure, or say plainly that you are not. }}

## Confidence in this model

{{ First-hand — the reader described themselves (the user, or the actual
reader answered the questions). Or modelled — the user described someone
else: name whose model it is, list what is a guess, and check rather than
assume. Delete this section only when the model is first-hand and complete. }}

## Register rules

{{ FOUR TO EIGHT rules, each a bolded imperative plus one or two lines of
why. Each traceable to an interview answer — especially "the last time
AI-assisted work was difficult to parse" and its actionable fix. Take the
shape from the prior; take the content from this user. Cover at least:
  — what the first sentence must carry
  — what to cut that the agent would otherwise include
  — length and format, per artifact in play
  — how much justification each claim needs: receipts and plots, or a
    skimmable summary
  — how to signal uncertainty to THIS reader
  — when to stop and ask instead of proceeding }}

**{{ Rule }}.** {{ Why, in one or two sentences. }}

{{ ... }}

### When the reader hits something they don't know

{{ From the interview — answer / explanation / question. Pick ONE default
and say what it looks like in practice:
  — **Answer:** give it, one line, then offer depth. No scaffolding.
  — **Explanation:** the shape of the answer, then the mechanism, then
    details. Stop after the mechanism and check.
  — **Question that gets them there:** ask what they expect before you
    explain. Leave room. Answer if they say "just tell me". }}

{{ STUDENT-TYPE ONLY — include the block below when the READER is
student-shaped: the prior is audience-student, or the gap-handling answer is
"a question that gets me there" and it was asked about the reader. Full
versions of these moves are in the generator's priors reference (Student
section); inline what you use. Each bullet is tagged with the reader time
budget it survives — copy only the bullets that pass, and delete the tags. }}

### Teaching moves {{ student-type }}

- **Restate before explain.** [15+] Ask them to say where they are first.
  Explain into the gap, not into the void.
- **Drill the whys.** [15+] Problem, why it existed, the branches. Then
  solution, why that one, its design decisions and edge cases. Then why it
  matters.
- **Do not end until verified.** [15+] At fifteen minutes, the short form:
  name the one thing they should be able to do, check that, stop.
- **Incremental mastery.** [1h+] Confirm the current step before the next. A
  passed check moves something to "holds"; explaining it does not.
- **Running checklist.** [1h+] A short visible ledger: holds / shaky /
  deferred. Rewrite it, do not append.
- **Quiz without revealing.** [1h+] Open-ended or multiple choice; vary
  where the correct answer sits; do not give it until they have committed.

**Five-minute version** [always — and at two minutes it is the whole
section] (a different artifact, not a compressed one):
1. What kind of thing this is. 2. The one mechanism that carries the rest.
3. The thing people get wrong. 4. What we skipped and where to go next.

## Artifacts and local norms

{{ From the interview. Only what differs from the universal preferences in
the skill body, or sharpens them. If nothing differs, write "Follow the
body." and move on. Two or three surfaces, not seven — for each: the shape,
the length, and the one thing that goes wrong there. }}

**Surfaces:** {{ PRs / issues / Slack / reports / talks — and what each is for }}
**Cadence:** {{ when to post; when silence is the right output }}
**Length ceiling:** {{ concrete: one screen, three paragraphs, ten slides }}
**Tagging and approval:** {{ who may be tagged; what needs a human first }}
**AI disclosure:** {{ this audience's norms on AI usage and its disclosure;
link the collaboration's document if one exists }}
**Register:** {{ formal or casual; prose, bullets, tables; emoji or not }}
**Local rule an outsider would get wrong:** {{ the one that bites newcomers }}
**What has annoyed people here before:** {{ the specific past friction }}

## Do / don't

{{ ONE OR TWO worked pairs, drawn from the user's own examples — especially
the "last time AI-assisted work was hard to parse" answer. Their vocabulary,
their project nouns. Generalize the move; keep the example as illustration.
Strip anything sensitive. This is the section the user is most likely to
keep and the one that most changes behavior. }}

**Don't:**

> {{ the failure, written realistically }}

{{ one line on what goes wrong }}

**Do:**

> {{ the same content, right }}

## Failure modes to watch for

{{ THREE TO FIVE, specific to this audience. Prefer ones the user named.
Generic entries ("be too verbose") add nothing. }}

## Open questions

{{ What the interview could not settle, plus anything you guessed. Keep it —
it is the agenda for the re-interview, and it is how the file stays honest
about its own edges. }}
```

---

## Read it cold before you hand it over

- Could someone without the interview follow every sentence the first time?
- Is anything in here true of every audience, and therefore the body's job?
- Do the user's project nouns appear? If it would fit any team, the
  interview was not used.
