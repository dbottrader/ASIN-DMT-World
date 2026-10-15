# Function Intent Reconciliation — DMT originals vs DMT Codex Explorer (React port)
**Date:** 2026-10-14 · **Author:** Ace (Muse side) · **Basis:** dmt-handoff/verification/VERIFICATION-REPORT.md (40 vectors: 0 MATCH / 32 DIVERGENT / 8 MISSING)
**Purpose:** The harness answered *what* differs. This document asks, per difference, whether it is a bug or an intentional redesign — and records a recommended decision. Final decisions are Dennis's.

## Decision vocabulary
- **PRESERVE** — keep the original's behavior as canonical; the port must change to match.
- **REDEFINE** — keep the port's behavior; update the spec/labels so the port is described honestly.
- **REDESIGN** — neither side is canonical yet; a new decision is needed.
- **HYBRID** — keep both: original engine as compatibility/fidelity layer, port engine as the experimental deterministic mode.

## Standing recommendation
Do **not** delete or rewrite the current port. It is a working, tested, deterministic geometry engine with hashed receipts — that has value. Re-label it honestly: "DMT Codex Explorer v0.x — experimental reimplementation (inspired by, not equivalent to, the originals)." If fidelity to the originals is desired, build it as a separate compatibility layer, not by mutating the existing engine. (This matches OAI Ace's recommendation.)

---

## Per-geometry reconciliation

### 1. Chrysanthemum
| | |
|---|---|
| **Original behavior** | 7 fixed layers of quadratic-curve petals; petal count `n = 12 + round(sym*20)`; 133 paths at default vector; `depth` scales base radius R only; no seed — deterministic given time `t`. |
| **Port behavior** | `depth` closed sin-modulated radial paths (6 at default); `seed` drives phase offsets via mulberry32; `depth` changes ring count, not scale. |
| **Difference** | Different primitive kinds (quadratic petals vs radial paths), different counts (133 vs 6), different parameter semantics, different determinism model (time-driven vs seed-driven). |
| **Recommended decision** | **REDEFINE** (port keeps its engine; stop calling it the Chrysanthemum original) — or **HYBRID** if the original petal engine is wanted back as a fidelity mode. The two are not the same artwork and should not share a name without qualification. |

### 2. Metatron
| | |
|---|---|
| **Original behavior** | 13 fixed points, 78 all-pairs segments, 13 circles with canvas-pixel radii (`3+sym*5` px — canvas-size-dependent by design); 91 primitives, invariant across depth/density. |
| **Port behavior** | `min(depth,6)` scaled levels of 13 centers each + symmetry-star path; 547 primitives at default; structure varies with `depth`. |
| **Difference** | Topology changed (fixed 13-point figure vs leveled/iterated figure); coordinate model changed (canvas-pixel radii vs normalized field); parameter semantics changed (depth inert vs depth structural). |
| **Recommended decision** | **REDEFINE** — the port's leveled Metatron is a distinct composition. Note: the original's canvas-pixel radii are arguably a *defect* (resolution-dependent); the port's normalized model is the better engineering. If a "true Metatron" mode is wanted, **HYBRID**: port the 13-point/78-segment construction into the normalized coordinate model as a fidelity mode. |

### 3. Flower of Life
| | |
|---|---|
| **Original behavior** | 7 fixed circles; seed-independent; invariant across depth/density. |
| **Port behavior** | Hex-lattice ring field (depth-dependent count: 129 primitives at default, 471 at max) + bounding circle + rosette path; seed-independent (confirmed — never calls the PRNG). |
| **Difference** | 7 circles vs 129+ lattice field. Both seed-independent, so the determinism model agrees — but the geometry is a different composition (classical 7-circle seed-of-life vs expanded lattice). |
| **Recommended decision** | **REDEFINE** — the port is an *expansion* of the flower concept, not a reproduction. Lowest-cost **HYBRID** candidate: the original's 7-circle construction is trivial to add as a "classic" mode alongside the lattice. |

### 4. Spiral
| | |
|---|---|
| **Original behavior** | **No spiral routine exists** in the designated file (Phenomenology Lab contains only chrys/meta/flower). The only spiral in the bundle is in CODE_X: a single 700-point path, `r=R*q^0.72`, `a=q*20π+t*0.4`. |
| **Port behavior** | Golden-angle dot field + `symmetry` arm paths (296 primitives at default). |
| **Difference** | Designation error compounded by redesign: the file *named* for phenomenology/spiral has no spiral, and the port's spiral matches neither the CODE_X spiral nor anything in its designated file. |
| **Recommended decision** | **REDESIGN** — first decide what "spiral mode" is *supposed* to be. Options: (a) port the CODE_X 700-point spiral faithfully (**PRESERVE** of the only spiral that exists in the bundle); (b) keep the port's dot-field spiral as an original composition (**REDEFINE** with an honest name). Also correct the bundle naming: Phenomenology Lab should not imply a spiral it does not contain. |

### 5. CCD-9 decoder
| | |
|---|---|
| **Original behavior** | 1MB single-file decoder application. |
| **Port behavior** | None — SOURCE EXISTS / PORT MISSING. |
| **Difference** | Entire application absent from the port. |
| **Recommended decision** | **REDESIGN** — Dennis decides: is CCD-9 in scope for the Explorer at all? If yes, it is a separate porting project (1MB app, not a geometry mode). If no, record the exclusion explicitly. Either way, stop leaving it implicit. |

---

## Cross-cutting decisions

| # | Difference | Original | Port | Recommended |
|---|---|---|---|---|
| C1 | Parameter semantics (`depth`, `density`) | depth=scales R; density=decorations | depth=structure; density=sampling | **REDEFINE** — document the port's semantics as its own; do not present params as compatible across implementations |
| C2 | Determinism model | time-`t` driven, no seed | seed-driven mulberry32 (+frame) | **REDEFINE** — both are deterministic; they are deterministic in *different* ways. The port's model (seeded + hashed receipts) is the stronger provenance story; keep it, label it |
| C3 | Time model | continuous seconds, per-routine rotation rates | `frame/60`, global spin 0.2 | **REDEFINE** — cosmetic; document |
| C4 | Naming | files named for routines they contain (except spiral) | modes named for originals they don't reproduce | **REDEFINE** — rename or subtitle port modes: "Chrysanthemum (reinterpretation)" etc., until/unless HYBRID fidelity modes land |

## What this resolves and what it doesn't
- **Resolves:** whether the port is a faithful migration (no — measured); what each difference *is* (table above); what the cheapest honest path is (relabel, don't rewrite).
- **Doesn't resolve:** which HYBRID fidelity modes Dennis actually wants built; whether CCD-9 belongs in the Explorer; the coherence/Delta function (separate HOLD track — unchanged).

## Proposed next artifact (for OAI Ace's register)
If Dennis approves the HYBRID direction: a fidelity-mode build plan — one compatibility module per original (starting with flower-classic, the cheapest), each gated by the existing harness vectors before it may claim the original's name.
