---
name: ambition
description: >-
  Rewrites a task prompt to be more ambitious along three lenses — altitude (the outcome
  behind the task), depth (how a field-leading professional would do it, from raw
  material, judged by something outside the model) and range (methods from other fields)
  — and returns the rewritten prompt for the user to confirm before running it. Use when
  the user runs /ambition <prompt>, optionally with +altitude, +depth or +range.
license: MIT
argument-hint: "[+altitude | +depth | +range] <prompt or task>"
disable-model-invocation: true
---

# Ambition

Takes a prompt or task and returns a **deeper, higher and wider** version of it — not a bigger one — plus what the agent would need to carry it out. It does not run the task: it shows the rewritten prompt and waits for the user to confirm, change or drop it.

Based on Felix Rieseberg, *How to be more ambitious: A tutorial for humans with models* (13 October 2026, felixrieseberg.com). The wording and the altitude and range checklists here are our own adaptation.

## When invoked

1. Take the input after `/ambition` (pasted prompt, task or attached brief). If it is empty, ask once for the prompt to work on.
2. Select lenses: `+altitude`, `+depth`, `+range` (one or more). No flag means all three.
3. Read only the context needed to ground the answers (attached files, the repo, data the user points to). Do not start the task itself.
4. Answer the questions of each selected lens (below) in short bullets tied to this task — never generic advice.
5. Write the **rewritten prompt**: one prompt, ready to run, in the user's language, that asks for exactly what the lenses found — outcome, raw material, methods and tools, the outside judge and how the result is checked, the methods borrowed from other fields, the deliverable, and what not to do.
6. List what the agent needs that is not available yet (data, access, tools, a place to run and verify).
7. Produce the output template and end with the confirmation question. Stop.
8. Next turn:
   - **Yes** ("sí", "adelante", "hazlo") → run the rewritten prompt as normal work.
   - **Changes** → apply them to the prompt, show the full output again and ask again.
   - **No** → stop.

## Lenses

### Altitude — the outcome behind the task

1. **Goal behind the goal:** what should happen once this is done?
2. **Decision served:** which decision the work feeds, and who makes it.
3. **Owning the outcome:** what the agent would need to keep the outcome true without new prompts each time (data feeds, access, a way to reproduce and verify on its own).
4. **Process it could replace:** the recurring routine this could replace or run beside, and how to show on past data that it would have worked.

For creative tasks altitude helps less: say so in one line and keep it short.

### Depth — how a field-leading professional would do it

1. **What the best would do** that the user is not asking for.
2. **Rawest material** they would start from, instead of what has already been digested.
3. **Methods and tools** they would actually use — instruments, not vocabulary (databases and statistical models instead of tables; primary sources instead of summaries).
4. **Outside judge:** what, other than the model or the user, shows the result is right — ideally something runnable (a test, a reconciliation, held-out data, a primary source, an expert review).
5. **Assumption to test:** one belief the task takes for granted, and how to check it against the raw material.

### Range — methods from other fields

1. **Verbs, not nouns:** restate the task as what it really does (a quarterly review is not "a deck": it is getting busy people to believe a cause-and-effect story and decide under uncertainty).
2. **Fields** that are best at those verbs, including one adversarial field (red team).
3. **What each field does:** its method, check or artifact — never its voice or persona.
4. **What to bring in:** which of those methods enter the rewritten prompt, and why.

## Rules

- Deeper, higher, wider — not bigger: no extra deliverables the outcome does not need.
- Ambition goes into methods and goals, never into claims. Never assert that something is feasible or true to push the work; unknowns stay marked as unknown.
- Every rewritten prompt names an outside judge. If none exists, say so in the prompt and require the result to state its confidence and what would verify it.
- No role-play: other fields contribute methods, not voices.
- Legal, tax or regulatory tasks: the outside judge is the primary sources (legislation, case law, administrative rulings, official guidance), cited at claim level; aggressive positions are flagged, not hidden.
- Never run the task before the user confirms.
- Answer in the user's language.

## Output

```markdown
## Tarea
- <the task restated in one or two lines>

## Altura
- Objetivo detrás del objetivo: …
- Decisión que sirve: …
- Para hacerse cargo del resultado: …
- Proceso que podría sustituir: …

## Profundidad
- Lo que haría un profesional de primer nivel: …
- Material en bruto: …
- Métodos y herramientas: …
- Juez externo: …
- Supuesto a poner a prueba: …

## Alcance
- En verbos: …
- Disciplinas → qué aporta cada una: …
- Equipo rojo: …

## Prompt reescrito
<the full rewritten prompt in a fenced text block>

## Qué necesita el agente
- …

---
¿Ejecuto el prompt reescrito? (sí / cambia … / no)
```

Translate the headings when the input is not in Spanish. Drop the sections of lenses that were not selected.
