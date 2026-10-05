# Scientific Understanding Engine

Agent skill (Claude Code format) that turns scientific material into the representation that best exposes its structure: controlled text, causal diagram, concept map, process diagram, equation walkthrough, plot, interactive HTML, simulation, animation, or video, or the smallest useful combination.

> The purpose is not to make difficult science look simple. The purpose is to make difficult science inspectable.

## Install / invoke

- Clone this repo into a skills folder so the folder name stays `scientific-understanding-engine`:
  - all projects: `git clone https://github.com/rcrohmana/scientific-understanding-engine ~/.claude/skills/scientific-understanding-engine`
  - one project: clone into `<project>/.claude/skills/scientific-understanding-engine`
- Triggers on understanding intents in any language ("Explain capillary pressure", "Jelaskan capillary pressure", "Gue masih bingung konsep Buckley-Leverett"). Manual: `/scientific-understanding-engine`.
- Modes: `auto` (default), `text`, `diagram`, `causal`, `interactive`, `simulation`, `video`. Say e.g. "mode interaktif" or "text only".

## Tree

```text
scientific-understanding-engine/
├── SKILL.md                         operational core: pipeline, AUTO logic, decision block, language, integrity rules, index
├── README.md
├── references/                      the "why" and detailed rules
│   ├── representation-selection.md  structure → representation table, escalation and down-selection rules, worked selections
│   ├── epistemic-status.md          12 status labels, forbidden conversions, how to show status
│   ├── scientific-integrity.md      rules, provenance, user-pushed claims
│   ├── visualization-guidelines.md  plot rules, arrow semantics, Mermaid conventions
│   └── output-modes.md              mode behavior and override conflicts
├── prompts/                         working templates per representation
│   ├── controlled-writing.md        ASD-STE100-inspired rules, incl. Indonesian application
│   ├── causal-reasoning.md          chains, hypothesis trees, arrow justification, hypothesis checking
│   ├── concept-map.md               concept maps + process diagrams + spatial diagrams
│   ├── mathematical-explainer.md
│   ├── paper-understanding.md
│   ├── interactive-html.md
│   ├── simulation.md
│   ├── animation.md
│   ├── video-explainer.md
│   ├── scientific-review.md         checklist + failure-mode scan
│   └── understanding-review.md
├── examples/
│   ├── concept-example.md           capillary pressure (ID)
│   ├── mechanism-example.md         CO2–carbonate permeability decrease (ID)
│   ├── mathematical-example.md      Buckley-Leverett shock front (ID, casual register)
│   ├── paper-example.md             fictional LSWF paper, reasoning extraction
│   ├── interactive-example.md       design + verification record
│   └── buckley-leverett-explainer.html  working reference implementation
└── tests/
    └── skill-test-cases.md          10 spec tests + 1 domain-generality + 4 Indonesian + 2 non-trigger
```

## Architecture

```text
Input → classify (A–J) → structure analysis → epistemic tagging → representation selection
      → generate (prompts/*) → scientific review → understanding review → deliver
```

- **SKILL.md** decides and routes. It holds what an agent needs on every call: AUTO questions, the Representation Decision block, language rules, integrity rules, module index.
- **references/** holds rules that several modules share (status labels, arrow semantics, integrity).
- **prompts/** holds one template per representation or review step. A module does not repeat shared rules; it points to references.

## Representation-selection logic (short)

1. Structure decides: definition → text; cause-effect → causal diagram; relations → concept map; sequence → process diagram; equations → math explanation; quantitative shape → plot; multi-parameter sensitivity → interactive; evolution in time/space → simulation; motion as mechanism → animation; sequential integration with narration → video.
2. Escalate only when the cheaper representation fails a stated test (text < diagram < plot < interactive < simulation < animation < video).
3. Remove any representation that repeats another, needs fabricated data, or shows unsupported relations.
4. Show the choice in the decision block (Intent → Topic → Problem structure → Best representation).

## Design decisions

| Decision | Reason |
|---|---|
| Claude Code skill (`name` + `description` frontmatter in `SKILL.md`) | Standard Claude Code skill format; works as a personal or project skill. |
| Skill files in English, examples in Indonesian | Agent-facing instructions follow the format of the other skills; Indonesian examples give explicit multilingual triggers and output models. |
| Indonesian trigger phrases inside the `description` | The description is what the skill selector reads. |
| Decision block mandatory | Makes representation choice inspectable (acceptance criterion 12) in the format the user specified. |
| Default language: user's language for reasoning; English terms kept under 4 conditions | User specification. |
| `concept-map.md` also covers process and spatial diagrams | Same mechanics (nodes, labeled edges); avoids three thin files. |
| Video module defaults to script + storyboard | Rendering depends on Manim/TTS/ffmpeg availability; the skill must not claim an unrendered video. |
| Host design skills (`artifact-design`, `dataviz`) loaded when present | This skill decides scientific content; host skills decide styling and page contract. |
| Paper example is fictional and labeled | A real paper summary would require the source; inventing one would break the skill's own Rule 3. |

## Extending

Add a representation (3D visualization, notebook explainer, digital twin, literature evidence map, uncertainty visualization, domain adapter): one row in `references/representation-selection.md` §1, an escalation test in §2 if needed, one `prompts/` module, one row in the SKILL.md module index, one test case.

## Limitations

- Test cases are specifications for evaluation; they were checked by reading through the skill (mental execution), not by an automated harness.
- Video rendering is not implemented as scripts; the module specifies the pipeline only.
- Domain examples lean on petroleum engineering; the rules are domain-general, but other fields have no worked example yet.
- Only the Buckley-Leverett page was executed and verified (headless Node + headless Edge screenshot).
