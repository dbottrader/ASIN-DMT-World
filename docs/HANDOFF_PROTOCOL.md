# Two-Ace Handoff Protocol

Dennis's standing orders, 2026-10-11: both Aces document everything in this repo and work together. Cascade protocol. Full green light. Don't stop.

## The two sides

- **Ace (Muse side)** — runs on the operator machine. Can do: code, compute, GitHub pushes, Drive up/down, deployments, web research, verification.
- **Ace (ChatGPT side, "Ace 2026")** — holds Dennis's ChatGPT Library with the original DMT World HTML sources. Cannot upload to Drive or push to GitHub from its session; routes those through the Muse side.

## Channel map

- This repo: versioned source, docs, diffs, issues, manifests, receipts
- Drive folder ASIN-DMT-World-Shared-Drop: large artifacts, exports, bundles
- ChatGPT Library folder ASIN-DMT-World-Shared-Drop: OAI Ace staging area
- ChatGPT thread "Ace Back to Base": live Ace-to-Ace messaging

## Rules

1. Every claim gets a receipt (SHA-256 for files, commit hashes for changes, test output for code).
2. Status labels: OBSERVED / TESTED / PROMOTED / HOLD. Promotion stays HOLD until independently reproduced.
3. Every proposed change names its source revision, records the patch, runs the relevant tests, reports the actual result.
4. No promotion from a description alone.
5. Findings land in docs/ the same day, under the Ace that produced them.
6. Negative results are findings. Failed reproductions and corrected claims stay in the record.

## Current workstream

Faithful-port reconciliation of the DMT Codex: original HTML sources (5 files, hashes in manifests/original-bundle-sha256sums.txt) vs the Lovable "DMT Codex Explorer" React build, which is currently NOT a faithful port (substitutes a different mathematical renderer — confirmed independently by both Aces and Slick Rick, 2026-10-11).
