---
name: audience-advisor
description: Communicate with a reader who holds the bigger picture and the decision authority, and has very little time — a PhD advisor, supervisor, PI, or senior collaborator. Use when the user asks to summarize work for a supervisor, prepare a meeting update, write a progress report, or says "for my advisor", "for the PI", "supervisor update", "what do I tell my boss". Leads with decisions and judgment calls, not with what was done.
---

# Audience: Advisor / Supervisor

**v0 draft.** Written to be argued with.

## Reader model

The advisor does not know more than you. They know **differently**.

Post-PhD this is the key correction. On the fine grain — this method, this
dataset, this pipeline — **the author is the world expert**. The advisor is not
going to out-detail you and should not have to. What they hold instead:

- the **bigger picture** — how this fits the group's programme, the field, the
  next three years
- the **incentives** — funding, deadlines, what the grant promised, who else is
  working on this
- the **decision authority** — they can redirect the work; a peer can only
  object

They have seen the failure mode before, and they can often tell from one plot
that something is off. That is pattern recognition at the level of *judgment*,
not detail.

They have five minutes. Possibly three. They are reading between two other
things.

What they want: **the decision points, and what each one implies for the bigger
picture.** An advisor is not auditing your labor. They are checking your calls
and looking for the one you got wrong.

What to skip: technical depth they will trust you on. If you say the estimator is
unbiased, they will take it. Spending your five minutes proving it costs you the
one you needed judged. Skip the chronology and the method descriptions too.

What they do not have: your day-to-day context. They do not remember which run is
which. Name things.

**When you are wrong, it costs them little — but only if they can see the call.**
An advisor pushes back cheaply and has the authority to act on the pushback. A
decision presented as settled gets no pushback at all. So: decide, then mark the
two you doubt. See *Regardless of role* in the repo README.

## Register rules

**Lead with the decision, not the activity.** "I chose X over Y because Z" beats
"I spent the week testing X and Y". The second buries the content.

**Flag the calls you are least sure about, first.** This is the highest-value
thing in the whole update. The advisor's comparative advantage is judging exactly
these. Put them where they cannot be missed.

**Separate: decided / open / blocked.** Three headings, or three clearly marked
groups. An advisor scanning wants to know instantly which items need them.

**Be explicit about what you want from them.** "No action needed", "I want your
read on the second point", "this is blocked on your access to the cluster". An
update with no ask wastes both of you.

**Assume expertise. Do not explain the method.** If you used a Kaiser-Squires
inversion, say so. Do not describe it. On the fine grain they trust you; spend
the space elsewhere.

**Say what each decision implies for the bigger picture.** "Cutting ℓ < 100"
means nothing to a PI in three minutes. "Cutting ℓ < 100 — costs ~15% of the
constraining power, keeps us on schedule for the March deadline" is a decision
they can actually make.

**Length: one screen.** If it does not fit, you have not decided what matters.
Detail goes below a fold, or in a linked document, or in the appendix they will
not read unless a number surprises them.

**Numbers, not adjectives.** "Improved" is meaningless. "χ²/dof went 1.8 → 1.1"
is a fact they can act on.

**Show the plot.** One figure that carries the result is worth the whole text. An
advisor reads figures first regardless of what you intended.

**Do not hide the bad result.** They will find it, and the cost of having hidden
it is far higher than the cost of the result.

## Do / don't

**Don't:**

> This week I set up the pipeline on the cluster, which took longer than
> expected due to a module conflict. Once that was resolved I ran the first
> batch of sims, then found an issue with the mask, fixed it, and reran. The
> results are attached — let me know what you think!

Chronology. The reader must extract the content themselves. "Let me know what
you think" is not an ask.

**Do:**

> **Decided:** using the apodized mask (C2, 10 arcmin) rather than binary.
> Binary leaked ~15% power into the first bandpower; apodized is clean.
>
> **Unsure — want your read:** I'm cutting ℓ < 100 rather than modelling the
> large-scale systematic. That's a real information loss. Is that the call you'd
> make, or is the model worth the effort?
>
> **Open:** χ²/dof = 1.4 on the null test (fig 1). Not obviously broken, not
> obviously fine.
>
> Nothing blocked. Full detail: `notes/2026-07-24.md`.

---

**Don't** ask "does this look right?" with an unlabeled plot attached. **Do**
say what you think it shows and where you doubt it.

---

**Don't** apologize for slow progress or explain the obstacles. **Do** state
where things stand and what you need. If time was lost, one clause: "lost two
days to a cluster outage".

---

**Don't** send six updates over a week. **Do** batch to one, at a rhythm the
advisor set. See the `team-norms` skill.

## Structure that works

```
One-line state of the work.
Decided:      (with the reason, one line each)
Unsure:       (the calls you want judged — highest value, keep it short)
Open:         (results that are neither good nor bad yet)
Blocked:      (with the specific ask and the person)
Detail:       (link, not text)
```

## The hardest part

The advisor cannot correct what they cannot see. Their comparative advantage is
judgment, so the update should make it **easy for them to disagree with you**.
Write so that a wrong choice is visible, not so that the work looks good. An
update optimized to look competent is worth less than one optimized to be
corrected.

## Failure modes to watch for

- **Bragging by volume.** Long updates read as insecurity, not productivity.
- **Burying the ask.** The one thing you need from them, in the last line.
- **Hedged decisions.** "I sort of went with X for now" — did you or didn't you?
- **Over-deference.** Do not present every choice as open. Decide, then flag the
  two you actually doubt.
- **Under-deference.** Do not present a shaky call as settled.

## Open for the group

- Advisor and collaborator both assume expertise. We now say the difference is
  *authority plus altitude* — the advisor can redirect the work and holds the
  funding picture. Is that enough to justify two skills?
- Does "the author is the fine-grained expert" hold for a PhD student, or only
  post-PhD? If it flips, the skill needs a mode switch.
- Should this skill know the advisor's cadence (weekly meeting? async?) and adapt
  batching? That may belong in `team-norms` instead.
