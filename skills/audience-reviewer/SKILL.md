---
name: audience-reviewer
description: Communicate with a reader who is evaluating the work and is as knowledgeable about it as the author — a peer reviewer, a code reviewer, or an AI review agent. Use when the user asks to prepare something for review, write a review response, draft a methods section for referees, or says "for the reviewer", "reviewer-facing", "submit this for review". Leads with claims and the evidence for them, and surfaces weaknesses rather than hiding them.
---

# Audience: Reviewer

**v0 draft.** Written to be argued with.

## Reader model

The reviewer knows this domain as well as you do. Often they know this *work* as
well as you do — they have read the spec, the diff, the draft. In our setting the
reviewer is frequently an AI agent with the full context loaded.

They are not reading to learn. They are reading to **find what is wrong**.

What they want: claims, and the evidence attached to each claim. What breaks the
result. What was not tested. Where the author's confidence exceeds the author's
evidence.

What they do not want: background they already have, motivation they already
accept, or a tour of how hard the work was.

What they do not have: time to reconstruct your reasoning from the artifact. If
a choice is not justified in the text, they must assume it was not considered.

## Register rules

**Lead with the claim.** Every section opens with the assertion it defends. The
reviewer decides in one sentence whether to read the rest.

**Attach evidence to each claim, inline.** Not in an appendix, not "see the
results". Number, figure, test, file:line. A claim with no attached evidence
reads as unsupported, whatever else the document says.

**Surface the weaknesses yourself.** State the limitation before the reviewer
finds it. This is not a rhetorical trick; it is the only way to have a
substantive exchange. An unstated limitation costs a review cycle.

**Separate what was tested from what was assumed.** Explicitly. These are
different epistemic categories and collapsing them is the single most common
failure in research writing.

**Skip the motivation.** One sentence maximum. They know why this matters.

**Length: short, dense, navigable.** Reviewers read many things. Structure so
they can jump: headed sections, one claim per section, tables where tables fit.
Density is a courtesy here, unlike with a student.

**No hedging as decoration.** "May potentially suggest" is noise. Either the
evidence supports the claim or it does not. State the confidence level once,
concretely: "consistent within 1.5σ", "n=3, not enough to distinguish".

**Cite the negative results.** What did you try that did not work? Reviewers
weight this heavily and it is almost always omitted.

## Do / don't

**Don't:**

> We implemented a robust and carefully validated pipeline for the shear
> measurement, following best practices from the literature. The results are in
> good agreement with expectations and demonstrate the effectiveness of our
> approach.

Zero claims, zero evidence, three adjectives doing the work of a number.

**Do:**

> **Claim:** the multiplicative bias is below 5×10⁻³.
> **Evidence:** image sims, 10⁶ galaxies, m = (2.1 ± 0.9)×10⁻³ (`sims/run_04/`).
> **Untested:** blending above 30 gal/arcmin². The sims are at 20. We expect
> degradation; we have not measured it.

---

**Don't** bury the limitation in the discussion section. **Do** put it next to
the claim it limits.

---

**Don't:**

> As is well known, the CMB lensing kernel peaks near z ≈ 2, and so…

If it is well known to this reader, cut it. If it is load-bearing, cite it and
move on.

**Do:** state the fact only when it is the premise of a claim, with a citation.

---

**Don't** respond to review comments defensively or at length. **Do** respond
per-point, in order, in one of three shapes: changed (with the diff), disagreed
(with the reason), or acknowledged as a real limitation (with what it would take
to fix).

## Structure that works

```
Claim
  Evidence
  Assumptions this rests on
  What would falsify it
Known limitations
Not tested
```

Repeat per claim. Boring and effective.

## When the reviewer is an AI

Mostly the same, with two differences:

- **Be machine-checkable where you can.** Concrete paths, exact commands, hashes.
  An AI reviewer will follow the pointer; a human often will not.
- **Do not rely on charity.** Ambiguity that a human colleague would resolve
  from context gets flagged. This is a feature. Write it out.

## Failure modes to watch for

- **Preemptive defensiveness.** Stating a limitation and then immediately arguing
  it away. State it, stop.
- **Evidence theater.** Long tables that do not bear on any claim.
- **Confidence laundering.** "Our analysis indicates" where "we assumed" is true.
- **Over-compression.** Density is good; unparseable is not. The reviewer should
  never have to open the code to understand the claim.

## Open for the group

- Is the peer-reviewer register really the same as the code-reviewer register?
  Argument for: both hunt for defects. Against: code review is line-level and
  conversational.
- Should this skill produce a self-review pass before output — the agent
  reviewing its own draft in this register?
