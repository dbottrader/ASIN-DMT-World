# DMT World handoff: next actions

## Immediate sequence

1. Preserve the five recovered HTML originals and compare each SHA-256 against the shared Drive copy.
2. Inspect the repository tree and deployment-linked source to identify which originals, assets, dependencies, and runtime modules are already present.
3. Build a source-to-port map: original file/function -> current implementation path -> status -> test/receipt.
4. Inspect `CCD-9_Decode_791(1).html` separately because it is about 1.05 MB and may contain encoded or generated payloads. Preserve raw bytes; analyze a copy.
5. Reproduce each artifact's core behavior in isolation before combining them into one app.
6. Record browser/runtime, commands, expected results, observed results, and hashes in `receipts/`.

## Evidence vocabulary

Use **OBSERVED**, **CONTEXT**, **HYPOTHESIS**, **TEST**, and **CONCLUSION**. Distinguish **EXISTS**, **EXECUTED**, **REPRODUCED**, and **ESTABLISHED**.

A successful file hash proves byte identity against the stated digest, not authorship, historical provenance, correct behavior, or deployment equivalence.

## Division of labor

### ChatGPT-side work
- Read accessible GitHub files and history through the connected GitHub tools.
- Record findings and create text-based manifests/receipts in the repository where write access permits.
- Analyze source artifacts already present in the working session.
- Avoid claiming access to Google Drive contents or live deployments unless those are actually inspected.

### Muse/local-side work
- Run `sha256sum -c manifests/SHA256SUMS.txt` in the directory containing the five originals (adjust the manifest path if needed).
- Provide the resulting terminal output and the exact commit SHA or Drive file identifiers for the copies checked.
- Run browser tests/build commands that require the local project environment, credentials, GPU, or deployment access unavailable in this session.
- Return logs and artifact hashes, not screenshots alone, for testable claims.

## Current limitations to close

- Drive upload is reported by the Muse side; this session has not independently read the Drive folder.
- The local archive's five file hashes were verified against the generated archive during recovery. Remote Drive parity remains pending independent evidence.
- Repository-wide source/dependency and deployment reconciliation remains pending.
