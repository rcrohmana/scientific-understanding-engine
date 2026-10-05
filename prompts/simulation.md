# Module: Simulation

Use when the system evolves in time or space and initial/boundary conditions matter. An educational simulation must never look like a predictive engineering simulator.

## Model definition (write before coding)

| Item | Content |
|---|---|
| Governing equations | exact form used |
| Variables | state, control, output; units |
| Parameters | symbol, unit, value, source tag |
| Initial conditions | |
| Boundary conditions | |
| Numerical method | scheme, grid/time step, stability condition (e.g. CFL, explicit diffusion r = ηΔt/Δx² ≤ 0.5) |
| Assumptions | physical and numerical |

## Implementation rules

- Analytic solution first if one exists; numerical only when needed. If both exist, show the numerical result converging to the analytic one for at least one case.
- Enforce stability limits in code (auto-adjust Δt or refuse unstable input).
- Check conservation (mass/volume balance) and report the error.
- Parameter controls change real model inputs only (see `interactive-html.md` wiring rules).
- Show intermediate states (profiles at several times), not only the final number.

## Outputs

- Spatial profile(s) and/or time series.
- Key derived quantities (e.g. breakthrough time, pressure at observation point).
- A short "what the user is seeing" explanation tied to the current parameters.

## Mandatory section: What this model does NOT represent

List omitted physics (e.g. heterogeneity, gravity, capillarity, compressibility, 3D effects, geochemistry), and state the consequence of each omission where known.

Add the label: "Educational model. Not for engineering prediction."

## Delivery formats

- Interactive HTML (JS) for small 1D/2D models.
- Python script + plots (matplotlib) for heavier models or when the user works in Python/notebooks.
- If neither can be run here, deliver the model definition and code, and state that it was not executed.
