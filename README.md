# ambition

Agent skill `/ambition`: rewrite a prompt to be more ambitious — higher, deeper, wider — and confirm before running it. Part of OneStack.

## What it does

Applies three lenses to a task prompt and returns a rewritten prompt plus what the agent needs to carry it out:

- **Altitude** — the outcome behind the task: the decision it serves, what it would take for the agent to own the outcome, the routine it could replace.
- **Depth** — how a field-leading professional would do it: raw material instead of digested summaries, real methods and tools, and an **outside judge** (test, reconciliation, primary source) instead of the model grading itself.
- **Range** — the task restated as verbs, the fields best at those verbs (plus a red team), and the method each one contributes — no role-play.

Ambition goes into methods and goals, never into claims: no forced feasibility, unknowns stay unknown, and legal or tax work is judged against primary sources. Like `/mirror`, it shows the result and stops: you confirm, change or drop the rewritten prompt.

Based on Felix Rieseberg, [How to be more ambitious: A tutorial for humans with models](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/) (13 October 2026); the wording and the altitude and range checklists are our own adaptation.

## Usage

```text
/ambition Prepárame un memo del impacto de Pilar Dos para el comité
/ambition +depth <prompt>              # one lens; +altitude, +depth, +range can be combined
```

Output (in the input's language): Tarea → Altura → Profundidad → Alcance → Prompt reescrito → Qué necesita el agente → "¿Ejecuto el prompt reescrito? (sí / cambia … / no)".

## Install

From OneStack: `./sync-install.sh` — or copy this folder as `<skills dir>/ambition/`.

## Requirements

None.

## Layout

- `SKILL.md` — the skill.

## License

MIT — see `LICENSE`.
