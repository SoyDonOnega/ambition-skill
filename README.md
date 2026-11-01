# ambition

Agent skill `/ambition`: benchmark the work at hand against how a field-leading professional would do it and get a ranked adoption plan. Part of OneStack.

## What it does

- **Current practice** — how the work is done today, each point backed by evidence from the session or the files.
- **Top level** — 5–8 practices taken from real exemplars (published methods, standards, official guidance, public repos) that were searched and read, each with its technique, tool, outside judge, source and criteria for levels 0–3.
- **Gaps** — current practice scored 0–3 against each practice.
- **Errors found** — defects spotted while reading the work, with `file:line`, reproduction and confidence.
- **Critic** — an isolated subagent checks sources, tools, scores, errors and plan before the report is shown.
- **Plan** — 3–5 items ranked by impact and effort, each with a first step in this project, prerequisite, cost (free route first), baseline and outside judge; plus what not to copy at this scale.
- **`+range`** — optional: methods borrowed from other fields, including an adversarial one.

It shows the report and stops: you pick an item to implement, change the report or drop it. Legal or tax work is judged against primary sources.

The outside-judge idea comes from Felix Rieseberg, [How to be more ambitious: A tutorial for humans with models](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/) (13 October 2026).

## Usage

```text
/ambition                                  # the work of this session / project
/ambition the quarterly VAT filing process
/ambition +range src/pipeline/
```

Output (in the input's language): Reviewer note → Errors found → Plan → Top level → Gaps → Current practice → What not to copy → Sources → "Implement item 1? (yes / item N / change … / no)".

## Install

From OneStack: `./sync-install.sh` — or copy this folder as `<skills dir>/ambition/`.

## Requirements

Web search and isolated subagents in the harness.

## Layout

- `SKILL.md` — the skill.
- `agents/ambition-critic.md` — contract for the isolated critic.

## License

MIT — see `LICENSE`.
