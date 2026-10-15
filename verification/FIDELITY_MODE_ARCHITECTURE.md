# Fidelity-Mode Architecture — DMT Codex Explorer
**Date:** 2026-10-14 · **Author:** Ace (Muse side) · **Status:** PROPOSAL (Dennis decides)
**Basis:** VERIFICATION-REPORT.md (0/32/8) + FUNCTION_INTENT_RECONCILIATION.md
**Rule:** No existing port code is modified. Fidelity modes are additive. A mode may claim an original's name only after passing the harness vectors for that geometry.

## 1. Geometry Registry

```ts
type FidelityMode = {
  name: string;            // "classic" | "field" (field = current reinterpretation)
  source: string;          // original file + routine, or "original composition"
  status: "HOLD" | "BUILD" | "TESTED" | "REPRODUCED";
  harness: string | null;  // path to vector results gating the name claim
};

type GeometryEntry = {
  id: "chrysanthemum" | "metatron" | "flower" | "spiral";
  modes: FidelityMode[];
  defaultMode: string;     // which mode the UI selects initially
};

export const GEOMETRY_REGISTRY: GeometryEntry[] = [
  {
    id: "flower",
    defaultMode: "field",
    modes: [
      { name: "field", source: "original composition (hex-lattice ring field + rosette)", status: "TESTED", harness: "vectors/flower_vectors.json (current behavior)" },
      { name: "classic", source: "ASIN_DMT_World_Lab_FIXED.html → drawFlower (7 fixed circles)", status: "HOLD", harness: null },
    ],
  },
  {
    id: "metatron",
    defaultMode: "field",
    modes: [
      { name: "field", source: "original composition (leveled 13-center figures + star path)", status: "TESTED", harness: "vectors/metatron_vectors.json (current behavior)" },
      { name: "classic", source: "ASIN_DMT_World_SPATIAL_CODEX_FIXED.html → meta (13 points, 78 segments, 13 circles; pixel radii translated to normalized coords)", status: "HOLD", harness: null },
    ],
  },
  {
    id: "chrysanthemum",
    defaultMode: "field",
    modes: [
      { name: "field", source: "original composition (sin-modulated radial paths)", status: "TESTED", harness: "vectors/chrysanthemum_vectors.json (current behavior)" },
      { name: "classic", source: "ASIN_DMT_World_CODEX_RESONANCE_ENGINE.html → chrys (7 fixed layers, quadratic-curve petals, n = 12 + round(sym*20))", status: "HOLD", harness: null },
    ],
  },
  {
    id: "spiral",
    defaultMode: "field",
    modes: [
      { name: "field", source: "original composition (golden-angle dot field + arm paths)", status: "TESTED", harness: "vectors/spiral_vectors.json (current behavior)" },
      // "classic" BLOCKED on the source-naming decision: Phenomenology Lab has no spiral;
      // candidate source is CODE_X's 700-point path (r=R*q^0.72, a=q*20π+t*0.4).
      { name: "classic", source: "TBD — requires spiral source decision (CODE_X candidate)", status: "HOLD", harness: null },
    ],
  },
];
```

## 2. UI contract
- Mode selector per geometry: `Classic` / `Field` toggle, visible in the geometry panel.
- Labels: "Flower — Classic (7-circle original)" vs "Flower — Field (lattice reinterpretation)". No mode ships without its subtitle.
- `defaultMode: "field"` — current behavior is preserved as the default; nothing the user sees today changes.
- Receipts include `geometry`, `mode`, and `registry_version` so a receipt is never ambiguous about which engine produced it.

## 3. Parameter contract per mode
- `classic` modes: original parameter semantics. `depth` scales base radius R; `density` affects decorative layers only; **no seed** (seed control hidden/disabled in classic mode — the originals have no seed); time `t` in seconds drives animation.
- `field` modes: current semantics unchanged (`depth` = structural complexity, `density` = sampling, `seed` = deterministic control).
- The panel documents both semantics side by side. (Resolves C1 from the reconciliation.)

## 4. Promotion gate (per mode)
1. **BUILD** — classic module implemented in isolation (pure function, same canonical-primitive interface as the harness).
2. **TESTED** — the 8 harness vectors for that geometry run against the classic module; results recorded.
3. **REPRODUCED** — independent run confirms (Muse-side + OAI Ace-side, same as the algebra gate).
4. Only then may the mode be labeled with the original's unqualified name in the UI. Until then: "classic (candidate)".

## 5. Implementation order (agreed with OAI Ace)
1. **Flower Classic** — lowest complexity (7 fixed circles), easiest validation. Proves the pattern.
2. **Metatron Classic** — good test of normalized-coordinate translation (original uses canvas-pixel radii `3+sym*5`; translate to field-normalized units, document the mapping).
3. **Chrysanthemum Classic** — harder (quadratic-curve petals, 7 fixed layers).
4. **Spiral** — blocked until Dennis decides the source (CODE_X 700-point path vs. new composition).
5. **CCD-9** — out of scope for this document; needs Dennis's scope decision first.

## 6. Explicit non-goals
- No rewrite of the existing `field` engine.
- No change to current default behavior or existing receipts.
- No fidelity claim without harness vectors passing.

## 7. Decision needed from Dennis
Approve / reject / amend: (a) the registry + dual-mode UI contract; (b) the implementation order; (c) the spiral source decision; (d) whether CCD-9 enters the Explorer's scope.
