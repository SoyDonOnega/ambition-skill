---
name: ambition
description: >-
  Benchmarks the work at hand against how a field-leading professional would do it:
  extracts their practices, techniques and tools from real exemplars, scores current
  practice against them on a 0–3 scale, has an isolated critic check the result, and
  returns a ranked adoption plan, then waits for the user to pick what to implement.
  Use when the user runs /ambition, optionally with a task, path or process.
license: MIT
compatibility: Needs web search and the ability to spawn an isolated subagent.
argument-hint: "[+range] [task, path or process]"
disable-model-invocation: true
---

# Ambition

Takes the work at hand and shows how a field-leading professional would do it: which practices, techniques and tools they use, how far current practice is from them, and a ranked plan to adopt what is worth adopting here. It does not implement anything: it shows the report and waits for the user to pick a plan item, change the report or drop it.

Paths in this file are relative to the skill root (the folder that contains this SKILL.md).

## When invoked

1. **Fix the object.** No argument → the work of the current session and the project it runs in. Argument → that task, path or process. State what the work is, what it is for and who uses the result. Read only the context needed (session, files, repo). If the object is still unclear, ask once.
2. **Current practice.** List how the work is done today: steps, starting material, tools, checks. Each item cites its evidence (file, line or session moment). What cannot be seen is marked unknown, never guessed. Defects found while reading (wrong output, crash, broken case) go to "Errors found" with `file:line`, how to reproduce and confidence; they are not practices.
3. **Field and exemplars.** Name one or two fields (no more). Search the web for 2–4 exemplars of top-level practice in each: published methodologies, standards, official guidance, public repos, books or talks by recognized teams. Read them. An exemplar that cannot be found and read does not count.
4. **Practices.** From the exemplars, extract 5–8 practices that separate top-level work from correct work. For each: the technique, the concrete tool or instrument (not vocabulary), the raw material it starts from, how it checks the result (the outside judge), its source, and criteria for levels 0–3 (0 not done · 1 partial · 2 solid · 3 as the exemplars). Score current practice on each, citing the evidence from step 2.
5. **Critic.** Spawn an isolated subagent with only `agents/ambition-critic.md`, the draft report, the exemplar links and the files cited in "Errors found". Apply its verdicts: drop or mark what it rejects, fix the scores it disputes with evidence, add its items to "What not to copy". One pass; do not argue with it in the thread.
6. **Plan.** Rank 3–5 gaps by impact on the outcome from step 1 against effort. Each item: the first concrete step in this project or setup, the prerequisite, the cost (free route first; paid marked), the baseline today (level and the concrete fact) and the outside judge that shows it worked.
7. **What not to copy.** Practices that only pay off at another scale, budget or team size, with the reason.
8. **`+range`** (only if given). Restate the work as verbs; name the fields best at those verbs, including one adversarial field; bring in their methods or checks, never their voices. Add what enters the plan.
9. Produce the output and stop. Next turn:
   - **Yes / item N** → implement that item as normal work; for builds, show the proposal before building.
   - **Changes** → revise the report, show it again and ask again.
   - **No** → stop.

## Rules

- Practices come from exemplars that were read, not from model memory. Every row in "Top level" links its source.
- Name people, firms or tools only when verified; otherwise describe the practice without a name. Never invent tools, versions, cases or citations. Keep verified fact apart from inference.
- No role-play: exemplars contribute methods and checks, never a voice or persona.
- Fit the practice to the user's scale; do not copy blindly.
- Free route first; mark what is paid.
- Every plan item has a baseline and an outside judge. If none exists, say so and state the confidence of the item.
- Legal, tax or regulatory work: the outside judge is primary sources (legislation, case law, administrative rulings, official guidance), cited at claim level; aggressive positions are flagged, not hidden.
- Never implement before the user confirms.
- Answer in the user's language.

## Output

```markdown
> Reviewer note — sources read · coverage (what of the work was read) · web check (date, number of searches) · critic verdict · open flags

## Errors found     (omit if none)
- <defect> — file:line · how to reproduce · confidence

## Plan
1. <practice> — first step here · prerequisite · cost · baseline (level, fact) · judge
2. …

## Top level
| Practice | Source | Technique | Tool | Judge | Criteria 0–3 |

## Gaps
| Practice | Us today (0–3, evidence) | Top level | Impact | Effort |

## Current practice
- …

## What not to copy
- …

## Range            (only with +range)
- …

## Sources
- …

---
Implement item 1? (yes / item N / change … / no)
```

Translate headings and the closing question into the user's language. In Spanish: Nota de revisión · Errores encontrados · Plan · Primer nivel · Diferencias · Cómo lo hacemos hoy · Qué no copiar · Alcance · Fuentes · "¿Implemento el punto 1? (sí / el N / cambia … / no)".

## Resources

- `agents/ambition-critic.md` — contract for the isolated critic of step 5.

## Harness notes

- Isolated subagent: Claude Code `Agent` tool with `subagent_type: "general-purpose"`; other harnesses: their subagent or task tool. Without subagents, run the critic as a separate pass that sees only its contract and inputs.
- Keep `agents/ambition-critic.md` in this folder; never copy it into a harness agents folder (it would show in the slash menu).
