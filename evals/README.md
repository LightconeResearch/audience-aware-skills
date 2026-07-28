# Evaluation protocol

Do the skills help? We should not guess.

This protocol is deliberately hand-runnable. No harness, no scripts. One person
can run one task in under twenty minutes. Before Friday, that is the point.

## The loop

**1. Pick a task.** From [`tasks.md`](tasks.md), or write your own. Each task
names a target role.

**2. Generate the control (without skill).** Fresh agent session, no audience
skill loaded. Give it the task prompt exactly as written. Save the output to
`evals/runs/<task-id>/control.md`. `evals/runs/<task-id>/` is created on first
run.

**3. Generate the treatment (with skill).** Fresh session. Load only the one
skill under test. Same task prompt, unchanged. Save to
`evals/runs/<task-id>/treatment.md`.

Do not edit either output. Do not re-roll a bad control.

**4. Judge blind.** A third fresh agent session. Give it:
- the role definition (the reader model section of the skill under test, or your
  own description of the reader)
- the two outputs, labelled **A** and **B**, order randomized
- the rubric below

Tell it to role-play the reader: "You are a second-year PhD student. You have not
seen this analysis before." Then score.

The reader-model section is fine to hand over — that's just who the judge is
playing. The judge must not see the rest of the skill body: the register rules
and worked examples. Those are what would let it pattern-match the skill's own
vocabulary instead of judging the output on its merits.

**5. Record.** Fill a row in the results table. Note what the skill changed and
what it broke.

**6. Rotate.** The person who wrote a skill should not be the person who runs its
eval. Take a role each, then swap.

## Rubric

Score each output 1-5 on every criterion. 3 is "acceptable, unremarkable".

### Universal criteria (all roles)

| Criterion | 1 | 5 |
|---|---|---|
| **Fit to reader** | Written for someone else entirely | Clearly written for this reader |
| **Concision** | Padded; I skimmed | Nothing to cut, nothing missing |
| **Actionability** | I don't know what to do with this | I know exactly what to do next |
| **Honesty** | Overclaims; hides gaps | States confidence accurately |

### Per-role criteria

**Student**
| Criterion | 1 | 5 |
|---|---|---|
| Comprehension checking | Dumped the answer | Asked, left room, then revealed |
| Scaffolding | One undifferentiated block | Built up in usable layers |
| Anchoring | Assumed knowledge I lack | Started from something I hold |
| Did I actually learn it? | No | I could explain it to someone else |

**Reviewer**
| Criterion | 1 | 5 |
|---|---|---|
| Claim/evidence pairing | Assertions float free | Every claim has evidence attached |
| Weakness disclosure | I had to find the gaps | Limitations stated up front |
| Assumed vs tested | Collapsed | Cleanly separated |
| Attackability | Nothing to grip | I know exactly where to push |

**Advisor**
| Criterion | 1 | 5 |
|---|---|---|
| Decisions foregrounded | Chronology of activity | Decisions and their reasons, first |
| Uncertainty flagged | All presented as settled | The doubtful calls are marked |
| Ask is clear | No ask, or buried | I know what is wanted from me |
| Fits my five minutes | No | Yes |

**Prompter**
| Criterion | 1 | 5 |
|---|---|---|
| Outcome first | Preamble before the result | First sentence is the outcome |
| Silent decisions surfaced | None mentioned | Every non-obvious call named |
| Ceremony | Greeting + filler + sign-off | None |
| Length vs content | Scaled to effort | Scaled to surprise |

**Norms** (T5)
| Criterion | 1 | 5 |
|---|---|---|
| Update batching | One post per thought | Batched into one update |
| Appropriate length | Log pasted whole | Trimmed to what the thread needs |
| Tagging restraint | Tags anyone, anytime | Tags only when the tag is earned |
| Matches team profile | Ignores the filled profile | Follows it |

### Judge output format

Ask the judge for exactly this:

```
A: universal [n,n,n,n]  role [n,n,n,n]  total /40
B: universal [n,n,n,n]  role [n,n,n,n]  total /40
Preferred: A|B
Why, in three sentences:
One thing the preferred output still gets wrong:
```

That last line is the most useful output of the whole exercise. Collect them.

## Results table

Keep one table in `evals/results.md`:

| Task | Role | Skill | Control /40 | Treatment /40 | Δ | Judge preferred | Judge run by |
|---|---|---|---|---|---|---|---|
| T1 | student | audience-student | 22 | 31 | +9 | B (treatment) | — |

Add a short prose note per row. The numbers tell you whether. The note tells you
why, and that is what changes the next draft.

## Things that will go wrong

- **The judge favors length.** Watch for it. If the longer output always wins,
  the judge is not reading as the role.
- **The skill's vocabulary leaks.** If the treatment uses the skill's exact
  phrases and the judge rewards them, the eval is measuring style matching.
- **One-sample noise.** n=1 per task. Treat a Δ under about 4 as noise. Run the
  same task twice if a result matters.
- **Task too easy.** If the control already scores 35, the task does not
  discriminate. Pick a harder one.
- **The skill helps on its own criteria and hurts elsewhere.** Watch the universal
  scores, not just the role ones. This is the failure we most want to catch.

## Minimum for Friday

Four tasks, one per role. One control and one treatment each. One judge pass per
pair. Eight generations, four judgments. That is a demo.
