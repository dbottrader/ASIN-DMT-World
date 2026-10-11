# ASIN-DMT-World source recovery manifest

- Recovery date: 2026-10-11
- Source location: ChatGPT Library raw-byte materialization
- Purpose: preserve and reconcile original DMT World HTML artifacts before faithful-port work
- Integrity scope: SHA-256 values below identify the recovered file bytes. They do not independently establish authorship, creation date, historical deployment state, or equivalence to any remote copy.
- Handling rule: preserve originals byte-for-byte. Do not decode, normalize, minify, or rewrite the CCD-9 artifact during intake.

| Artifact | Bytes | SHA-256 |
|---|---:|---|
| `ASIN_DMT_World_CODEX_RESONANCE_ENGINE.html` | 17,002 | `008a7c19183b0dcdfeb8fe7cd7cbf4c750a7125426ad49f882ccb9e08e53bedf` |
| `ASIN_DMT_World_SPATIAL_CODEX_FIXED.html` | 15,372 | `e5c6a0771054500634ca20352637830612d79315add041571ca2ab6afdfa897d` |
| `ASIN_DMT_World_Lab_FIXED.html` | 12,334 | `4148b83b275b185c55201612484ac8b545c4b82a9a44fd8ffae57d4f08f0a2d1` |
| `ASIN_DMT_World_Phenomenology_Lab.html` | 7,756 | `438b9faea161fa7e4d4ff66015ed16046d700bedf9b241a372d710264258bba6` |
| `CCD-9_Decode_791(1).html` | 1,055,184 | `900bf538b6a8138d6bd3880b6f579f1e4ec7aa09f1f596dabe12e7349917613d` |

## Evidence state

- **OBSERVED:** The five files were materialized from the ChatGPT Library into a local working directory.
- **VERIFIED:** The generated ZIP passed its CRC test and the five member hashes matched the listed SHA-256 values.
- **REPORTED, not independently observed here:** Muse-side reports that the ZIP was uploaded to the shared Google Drive folder and that all five hashes were verified there.
- **PENDING:** Compare these hashes against the Drive copies and any copies committed to this repository.
- **PENDING:** Inspect CCD-9 structure and encoding without modifying the preserved original.
- **PENDING:** Reconcile original HTML imports, runtime logic, assets, and deployment state against the faithful-port implementation.

## Related handoff locations

- GitHub repository: https://github.com/dbottrader/ASIN-DMT-World
- Shared Drive folder (Muse-side): https://drive.google.com/drive/folders/1inEIn6e8XL3AIh3_burqS_GVnIKQVgIG

## Promotion rule

Do not label an artifact reproduced or a port complete until the source is identified, dependencies are accounted for, the implementation runs, and a repeatable verification receipt is recorded.
