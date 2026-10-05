# Module: Explainer Video

Use only when several representations must be integrated in sequence and narration lowers cognitive load, or the user explicitly asks for a video. Never because it looks impressive.

## Teaching sequence (adapt; skip what the topic does not need)

```text
Question → Intuition → System → Variables → Mechanism → Mathematics
→ Visualization → Parameter sensitivity → Worked example → Limitations → Conceptual summary
```

## Deliverables, in order

1. **Script** — narration per scene, controlled writing, in the user's language (technical terms per SKILL.md language rules).
2. **Storyboard** — per scene: duration, visual (diagram/plot/equation/transformation), what moves and why, on-screen text (minimal), epistemic labels shown.
3. **Assets** — equations, plots, diagrams generated from the same verified model code.
4. **Render** (only if tools exist) — Manim / matplotlib / HTML capture → TTS → subtitles (SRT from script) → composition (e.g. ffmpeg).

## Rules

- Visual reasoning over text slides. On-screen text ≤ ~10 words per scene except equations and labels.
- Each scene passes the animation justification test (`animation.md`).
- Limitations scene is mandatory for model-based content.
- Uncertainty and competing hypotheses appear on screen, not only in narration.
- Same scientific review as any artifact; review the script before rendering.

## Implementation notes

- Python + Manim for constructions and equation transforms; matplotlib for data plots; ffmpeg for composition.
- TTS: local engine or API. API keys come from environment variables (e.g. `os.environ["TTS_API_KEY"]`). Never hard-code or print secrets.
- Keep per-scene files so a scene can be fixed without re-rendering everything.
- Check tool availability first (`which manim ffmpeg`, `python -c "import manim"`). If missing, deliver script + storyboard + static key frames and state clearly that no video was rendered. Install tools only with the user's agreement.
