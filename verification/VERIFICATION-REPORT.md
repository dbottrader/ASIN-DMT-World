# DMT Originals vs React Port — Behavioral Equivalence Report

**Run:** 2026-10-14T15:31:43.488891+00:00  
**Harness:** `~/workspace/dmt-handoff/verification/`  
**Port source:** Lovable "DMT Codex Explorer" `e675e232-5a2d-48e2-a7ea-73f5fd40616c`, `src/lib/codex/geometry.ts` (fetched 2026-10-14; verbatim copy at `port_source_geometry.ts.txt`; mulberry32 cross-validated against node)  
**Room:** `world` (the port's `lattice` overlay has no original-side counterpart)  
**Canonical form:** primitives rounded to 6 decimals; originals normalized by their base radius R (see `originals_impl.py` header for the full mapping).

## Verdict key
- **MATCH** — identical canonical output
- **PARTIAL** — same structure, numeric drift
- **DIVERGENT** — structurally different output
- **MISSING** — one side not implemented or errored

## Per-geometry results (designated pairings)

| Geometry | Designated original file | MATCH | PARTIAL | DIVERGENT | MISSING |
|---|---|---|---|---|---|
| chrysanthemum | ASIN_DMT_World_CODEX_RESONANCE_ENGINE.html → `chrys` | 0 | 0 | 8 | 0 |
| metatron | ASIN_DMT_World_SPATIAL_CODEX_FIXED.html → `meta` | 0 | 0 | 8 | 0 |
| flower | ASIN_DMT_World_Lab_FIXED.html → `drawFlower` | 0 | 0 | 8 | 0 |
| spiral | ASIN_DMT_World_Phenomenology_Lab.html → **no spiral routine exists** | 0 | 0 | 0 | 8 |

**Overall (32 vectors):** 0 MATCH / 0 PARTIAL / 24 DIVERGENT / 8 MISSING

### chrysanthemum

| Vector | frame | seed | depth | density | Verdict | Detail |
|---|---|---|---|---|---|---|
| default-f0 | 0 | 108 | 6 | 96 | **DIVERGENT** | orig n=133 {'path': 133} vs port n=6 {'path': 6} |
| default-f30 | 30 | 108 | 6 | 96 | **DIVERGENT** | orig n=133 {'path': 133} vs port n=6 {'path': 6} |
| seed7-f0 | 0 | 7 | 6 | 96 | **DIVERGENT** | orig n=133 {'path': 133} vs port n=6 {'path': 6} |
| seed2026-f30 | 30 | 2026 | 6 | 96 | **DIVERGENT** | orig n=133 {'path': 133} vs port n=6 {'path': 6} |
| seed42-sym24 | 15 | 42 | 6 | 96 | **DIVERGENT** | orig n=224 {'path': 224} vs port n=6 {'path': 6} |
| min-depth-den | 0 | 108 | 1 | 12 | **DIVERGENT** | orig n=133 {'path': 133} vs port n=1 {'path': 1} |
| max-depth-den | 30 | 108 | 12 | 240 | **DIVERGENT** | orig n=133 {'path': 133} vs port n=12 {'path': 12} |
| default-f60 | 60 | 108 | 6 | 96 | **DIVERGENT** | orig n=133 {'path': 133} vs port n=6 {'path': 6} |

### metatron

| Vector | frame | seed | depth | density | Verdict | Detail |
|---|---|---|---|---|---|---|
| default-f0 | 0 | 108 | 6 | 96 | **DIVERGENT** | orig n=91 {'path': 78, 'circle': 13} vs port n=547 {'circle': 78, 'path': 469} |
| default-f30 | 30 | 108 | 6 | 96 | **DIVERGENT** | orig n=91 {'path': 78, 'circle': 13} vs port n=547 {'circle': 78, 'path': 469} |
| seed7-f0 | 0 | 7 | 6 | 96 | **DIVERGENT** | orig n=91 {'path': 78, 'circle': 13} vs port n=547 {'circle': 78, 'path': 469} |
| seed2026-f30 | 30 | 2026 | 6 | 96 | **DIVERGENT** | orig n=91 {'path': 78, 'circle': 13} vs port n=547 {'circle': 78, 'path': 469} |
| seed42-sym24 | 15 | 42 | 6 | 96 | **DIVERGENT** | orig n=91 {'path': 78, 'circle': 13} vs port n=547 {'circle': 78, 'path': 469} |
| min-depth-den | 0 | 108 | 1 | 12 | **DIVERGENT** | orig n=91 {'path': 78, 'circle': 13} vs port n=92 {'circle': 13, 'path': 79} |
| max-depth-den | 30 | 108 | 12 | 240 | **DIVERGENT** | orig n=91 {'path': 78, 'circle': 13} vs port n=547 {'circle': 78, 'path': 469} |
| default-f60 | 60 | 108 | 6 | 96 | **DIVERGENT** | orig n=91 {'path': 78, 'circle': 13} vs port n=547 {'circle': 78, 'path': 469} |

### flower

| Vector | frame | seed | depth | density | Verdict | Detail |
|---|---|---|---|---|---|---|
| default-f0 | 0 | 108 | 6 | 96 | **DIVERGENT** | orig n=7 {'circle': 7} vs port n=129 {'circle': 128, 'path': 1} |
| default-f30 | 30 | 108 | 6 | 96 | **DIVERGENT** | orig n=7 {'circle': 7} vs port n=129 {'circle': 128, 'path': 1} |
| seed7-f0 | 0 | 7 | 6 | 96 | **DIVERGENT** | orig n=7 {'circle': 7} vs port n=129 {'circle': 128, 'path': 1} |
| seed2026-f30 | 30 | 2026 | 6 | 96 | **DIVERGENT** | orig n=7 {'circle': 7} vs port n=129 {'circle': 128, 'path': 1} |
| seed42-sym24 | 15 | 42 | 6 | 96 | **DIVERGENT** | orig n=7 {'circle': 7} vs port n=129 {'circle': 128, 'path': 1} |
| min-depth-den | 0 | 108 | 1 | 12 | **DIVERGENT** | orig n=7 {'circle': 7} vs port n=9 {'circle': 8, 'path': 1} |
| max-depth-den | 30 | 108 | 12 | 240 | **DIVERGENT** | orig n=7 {'circle': 7} vs port n=471 {'circle': 470, 'path': 1} |
| default-f60 | 60 | 108 | 6 | 96 | **DIVERGENT** | orig n=7 {'circle': 7} vs port n=129 {'circle': 128, 'path': 1} |

### spiral

| Vector | frame | seed | depth | density | Verdict | Detail |
|---|---|---|---|---|---|---|
| default-f0 | 0 | 108 | 6 | 96 | **MISSING** | original side not implemented |
| default-f30 | 30 | 108 | 6 | 96 | **MISSING** | original side not implemented |
| seed7-f0 | 0 | 7 | 6 | 96 | **MISSING** | original side not implemented |
| seed2026-f30 | 30 | 2026 | 6 | 96 | **MISSING** | original side not implemented |
| seed42-sym24 | 15 | 42 | 6 | 96 | **MISSING** | original side not implemented |
| min-depth-den | 0 | 108 | 1 | 12 | **MISSING** | original side not implemented |
| max-depth-den | 30 | 108 | 12 | 240 | **MISSING** | original side not implemented |
| default-f60 | 60 | 108 | 6 | 96 | **MISSING** | original side not implemented |

## Supplementary: port spiral vs CODE_X spiral

The designated spiral original (Phenomenology Lab) contains no spiral routine — see `originals_impl.py` header. For reference, the port's spiral was also compared against the spiral routine that *does* exist in `ASIN_DMT_World_CODEX_RESONANCE_ENGINE.html` (700-point single path, `r=R*q^0.72`, `a=q*20π+t*0.4`).

| Vector | Verdict | Detail |
|---|---|---|
| default-f0 | **DIVERGENT** | orig n=1 {'path': 1} vs port n=296 {'circle': 288, 'path': 8} |
| default-f30 | **DIVERGENT** | orig n=1 {'path': 1} vs port n=296 {'circle': 288, 'path': 8} |
| seed7-f0 | **DIVERGENT** | orig n=1 {'path': 1} vs port n=296 {'circle': 288, 'path': 8} |
| seed2026-f30 | **DIVERGENT** | orig n=1 {'path': 1} vs port n=296 {'circle': 288, 'path': 8} |
| seed42-sym24 | **DIVERGENT** | orig n=1 {'path': 1} vs port n=312 {'circle': 288, 'path': 24} |
| min-depth-den | **DIVERGENT** | orig n=1 {'path': 1} vs port n=14 {'circle': 6, 'path': 8} |
| max-depth-den | **DIVERGENT** | orig n=1 {'path': 1} vs port n=1448 {'circle': 1440, 'path': 8} |
| default-f60 | **DIVERGENT** | orig n=1 {'path': 1} vs port n=296 {'circle': 288, 'path': 8} |

## Structural findings (why they diverge)

1. **Parameter semantics differ.** In the originals, `depth` only scales the base radius R, `density` only drives decorative particle counts, and there is no seed — core geometry is deterministic given time `t`. In the port, `depth` changes layer/ring counts, `density` changes sample counts, and `seed` drives phase offsets via mulberry32.
2. **Chrysanthemum:** original = 7 fixed layers of quadratic-curve petals (`n = 12 + round(sym*20)` petals); port = `depth` closed sin-modulated radial paths. Different primitive kinds and counts.
3. **Metatron:** original = 13 fixed points, 78 all-pairs segments, 13 circles with canvas-pixel radii (`3+sym*5` px — canvas-size-dependent by design); port = `min(depth,6)` scaled levels of 13 centers each plus a symmetry-star path.
4. **Flower of Life:** original = 7 fixed circles; port = hex-lattice ring field (`depth`-dependent count) + bounding circle + rosette path. Both sides are seed-independent (confirmed: port `flower` never calls `rnd()`).
5. **Spiral:** no spiral routine exists in the designated original file. The CODE_X spiral (single 700-point path) is structurally unlike the port's spiral (golden-angle dot field + `symmetry` arm paths).
6. **Time model:** originals use continuous seconds `t` with per-routine rotation rates; the port uses `frame/60` with a global `spin = frame/60*0.2`. Vectors use `t = frame/60` so frame 30 = t 0.5 s on both sides.

## Boundary notes

- Decorative layers (tunnel rings, particles, gradients) excluded on the original side — the port likewise emits only field primitives.
- The port's `lattice` room overlay was not compared (no original counterpart).
- `CCD-9_Decode_791(1).html` is out of scope (no port exists) — unchanged, still HOLD.
- Nothing was modified in the originals or the Lovable project (read-only).

