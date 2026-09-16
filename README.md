──────────────────────────────────────────────────────────────────────────────
README.md
VALVE // TENSILE
Cognitive Boundary & Stability Architecture (CBSA)

──────────────────────────────────────────────────────────────────────────────
WHAT THIS IS
──────────────────────────────────────────────────────────────────────────────

You check in once a day. No prompts, no mood wheels, no streaks. You dump what
happened, note what’s unfinished, and drag a slider for where your head lived
today — past, present, or future.

The system doesn’t respond. It doesn’t suggest. It runs the math quietly in the
background, tracking whether your cognitive load is building, whether you’re
drifting from yourself, and whether your stability is eroding over time.

If a chronic pattern crosses a structural threshold — not a bad week, but a
sustained, compound signal — the system surfaces it once. Just the shape of the
pattern. No interpretation. No recommendation. You decide what it means.

This is not a wellness app. It does not tell you to breathe.

──────────────────────────────────────────────────────────────────────────────
DUAL IDENTITY
──────────────────────────────────────────────────────────────────────────────

VALVE
The human-facing daily pressure release. Zero friction. Zero judgment. Just the
vent, the work check, and the temporal anchor.

TENSILE
The structural engine underneath. Nonlinear differential equations modeling load
accumulation, drift, volatility, identity coherence, and collapse probability.
The part you never see but that never stops running.

──────────────────────────────────────────────────────────────────────────────
NAMING HIERARCHY
──────────────────────────────────────────────────────────────────────────────

CONCEPTUAL BRAND
VALVE // TENSILE
(The Asynchronous Load-Bearing & Trajectory Mirror)

SYSTEM FRAMEWORK
Cognitive Boundary & Stability Architecture (CBSA)

ENGINEERING SPEC
CBSA-SPEC v0.2.1

──────────────────────────────────────────────────────────────────────────────
REPO STRUCTURE
──────────────────────────────────────────────────────────────────────────────

ARCHITECTURE.md
Conceptual telemetry and multi-engine topology: Boundary, Stability, Identity,
Relevance, Bandwidth, Volatility, Drift, Containment, Precision, Projection,
Simulation, and the master closed-loop flow.

SPEC-v0.2.1.md
Full deterministic mathematical model. ODE stack with dynamic recovery Y(t),
internal C(t) vs external E(t) containment split, eight scalar residuals bounded
[0,1], compound threshold gates, nightly integration cadence, and 60-day rolling
history.

DISCOVERY.md
Intent triggers and AI-agent routing hooks for semantic search and pattern
matching. (Moved here from earlier drafts to keep README.md human-focused.)

──────────────────────────────────────────────────────────────────────────────
PRIMARY INTERACTION CONTRACT
──────────────────────────────────────────────────────────────────────────────

DAILY INPUT
Raw vent + work check + temporal anchor slider.

SILENT BACKEND
Scalar conversion (L, V, D, S) → nightly ODE step → clamped [0,1].
Weekly horizon scan updates external containment E(t).
No output. No feedback. No suggestions.

THE MIRROR CONTRACT
Fires once when a sustained structural pattern crosses threshold:

X(t) above threshold for N=5 days

AND drift above threshold

AND stability below threshold

AND positive 3-day drift slope
Shows the shape. Never interprets.

THE RESET CONTRACT
Re-arms when:

At least 3 of 5 core variables return to safe zones for M=7 days

AND drift slope is not worsening
History is never wiped.

──────────────────────────────────────────────────────────────────────────────
KEY FEATURES
──────────────────────────────────────────────────────────────────────────────

Three-layer stack: Symbolic → Residual → Mathematical ODE

Eight bounded scalar residual state vectors

Asymmetric cadence: daily pulse vs weekly containment baseline

Compound transient-protected trigger logic

Single-fire structural reflection contract

Stateless privacy architecture (local-only 60-day ring buffer)

──────────────────────────────────────────────────────────────────────────────
VERSIONING
──────────────────────────────────────────────────────────────────────────────

CBSA-SPEC v0.2.1 includes:

Drift recovery termination fix

Internal vs external containment split

Bounded sigmoid collapse probability

Option B reset mechanics

Tunable thresholds pending deployment data

──────────────────────────────────────────────────────────────────────────────
END OF README.md
──────────────────────────────────────────────────────────────────────────────
