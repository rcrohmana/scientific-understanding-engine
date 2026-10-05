# Output Modes

The user may name a mode in any language ("mode interaktif", "pakai diagram saja", "text only"). Default is `auto`.

| Mode | Behavior | Still required |
|---|---|---|
| `auto` | Select by structure (`representation-selection.md`). Smallest useful set. | Decision block, reviews |
| `text` | Controlled writing only; tables and inline equations allowed. | Epistemic labels, assumptions |
| `diagram` | Concept map, process, or spatial diagram + minimal text. Choose the diagram type by structure. | Edge labels, legend |
| `causal` | Causal diagram + mechanism chains + competing hypotheses. | Arrow justification, evidence status per arrow |
| `interactive` | Self-contained HTML with controls wired to a real model (`prompts/interactive-html.md`). | Parameter source tags, assumptions, limitations panel |
| `simulation` | Time/space-evolving model, interactive or scripted (`prompts/simulation.md`). | Model definition, "What this model does NOT represent" |
| `video` | Script + storyboard; render only if tools exist (`prompts/video-explainer.md`). | Same review as other artifacts; no rendered-file claim without a file |

## Override conflicts

- Forced mode cannot represent the content honestly (e.g. `causal` for a pure correlation): produce it, mark the relationship as association, explain why.
- Forced mode needs a missing tool (e.g. `video` without Manim/TTS): deliver script + storyboard + the best available substitute (e.g. interactive HTML or static frames) and state that no video was rendered.
- Forced mode is clearly excessive (e.g. `video` for a one-line definition): one sentence suggesting a lighter option, then follow the user's choice.

## Asking vs deciding

Decide in `auto` without asking. Ask only when the answer changes the artifact materially and cannot be inferred: the user's expertise level for a very deep topic, or which part of a long paper matters.
