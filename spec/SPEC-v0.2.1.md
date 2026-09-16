──────────────────────────────────────────────────────────────────────────────
SPEC-v0.2.1.md
Cognitive Boundary & Stability Architecture (CBSA)
Engineering Specification v0.2.1

──────────────────────────────────────────────────────────────────────────────
PURPOSE
──────────────────────────────────────────────────────────────────────────────

This specification defines the deterministic mathematical model underlying
CBSA. It describes the residual variables, nightly ODE integration, threshold
logic, sustained windows, collapse probability, containment structure, and
reset mechanics. It is not a psychological model. It is a stability model.

──────────────────────────────────────────────────────────────────────────────
RESIDUAL VARIABLES
──────────────────────────────────────────────────────────────────────────────

CBSA maintains eight scalar residual variables, each clamped to [0,1]:

L(t)        Load
V(t)        Volatility
D(t)        Drift
S(t)        Stability
C_int(t)    Internal Containment
E(t)        External Containment
B(t)        Bandwidth (drain vs recovery)
I(t)        Identity Coherence

All variables update daily from VALVE input and nightly ODE integration.

──────────────────────────────────────────────────────────────────────────────
INPUT CONVERSION
──────────────────────────────────────────────────────────────────────────────

Daily input consists of:

Raw vent text

Work check (unfinished tasks, load markers)

Temporal anchor slider (past → present → future)

Input is converted into residual deltas:

ΔL, ΔV, ΔD, ΔS, ΔC_int, ΔE, ΔB, ΔI

Text analysis is structural only.
No emotional interpretation is applied.

──────────────────────────────────────────────────────────────────────────────
ODE INTEGRATION
──────────────────────────────────────────────────────────────────────────────

Each night, CBSA performs a deterministic ODE step:

X(t+1) = X(t) + f(X(t), parameters)
for all residual variables X ∈ {L, V, D, S, C_int, E, B, I}

All updates are clamped to [0,1].

Key components:

Drift recovery termination
D(t+1) = D(t) - α_D4 * Y(t)

Containment split
C_int(t) and E(t) evolve independently.

Stability variance
S(t+1) incorporates wobble and damping terms.

Bandwidth slope
B(t+1) reflects drain vs recovery.

Identity coherence
I(t+1) tracks multi-day consistency.

──────────────────────────────────────────────────────────────────────────────
THRESHOLD LOGIC
──────────────────────────────────────────────────────────────────────────────

Thresholds are tunable and bounded.
A threshold breach does not trigger output by itself.
Only sustained, compound breaches matter.

──────────────────────────────────────────────────────────────────────────────
SUSTAINED WINDOWS
──────────────────────────────────────────────────────────────────────────────

A sustained window is defined as:

X(t) > threshold_X
for N consecutive days
with N = 5 in v0.2.1

──────────────────────────────────────────────────────────────────────────────
COLLAPSE PROBABILITY
──────────────────────────────────────────────────────────────────────────────

Collapse probability Z(t) is a bounded sigmoid:

Z(t) = sigmoid(
w1*L(t)

w2*D(t)

w3*V(t)

w4*S(t)

w5*B_tilde(t)

w6*I(t)

θ_Z
)

Z(t) is clamped to [0,1].
Z(t) is never shown to the user.

──────────────────────────────────────────────────────────────────────────────
MIRROR CONTRACT TRIGGER
──────────────────────────────────────────────────────────────────────────────

The Mirror Contract fires once when:

X(t) sustained above threshold for N=5 days

Drift D(t) above threshold

Stability S(t) below threshold

Drift slope positive for 3 days

Mirror output shows shape only.
No interpretation.
No advice.
No loops.

──────────────────────────────────────────────────────────────────────────────
RESET CONTRACT (OPTION B)
──────────────────────────────────────────────────────────────────────────────

The system re-arms when:

At least 3 of 5 core variables return to safe zones

Sustained for M=7 days

Drift slope dD/dt <= 0

History is never wiped.

──────────────────────────────────────────────────────────────────────────────
WEEKLY HORIZON SCAN
──────────────────────────────────────────────────────────────────────────────

Weekly horizon scan updates E(t):

E(t+7) = E(t) + horizon_adjustment

Drift slope is recalculated across 7 days.
Stability trend is derived from S(t) variance.

Weekly scan does not trigger the Mirror Contract.

──────────────────────────────────────────────────────────────────────────────
ROLLING HISTORY
──────────────────────────────────────────────────────────────────────────────

CBSA maintains a 60-day rolling vector ring buffer:

H = { X(t-59), ..., X(t) }

History is local-only.

──────────────────────────────────────────────────────────────────────────────
VERSION CHANGES IN v0.2.1
──────────────────────────────────────────────────────────────────────────────

v0.2.1 includes:

Drift recovery termination fix

Internal vs external containment split

Full collapse probability formula with B_tilde and I(t)

Option B reset mechanics

Threshold tuning parameters

Weekly horizon scan formalization

Stability wobble damping

Identity coherence smoothing

Precision layer bounding rules

──────────────────────────────────────────────────────────────────────────────
END OF SPEC-v0.2.1.md
──────────────────────────────────────────────────────────────────────────────
