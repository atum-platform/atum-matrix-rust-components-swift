# 2026-10-21 Founder SDK distribution source (26.10.15-atum.2)

Bounded local commit on branch `release/26.10.15-atum.2` (from `cf18be30`).
Purpose: prepare the source-only immutable SDK distribution for the Founder phone
bridge so the parent can open the one SDK PR, review it, and publish.

## What this commit contains

- `Sources/MatrixRustSDK/matrix_sdk_ffi.swift` regenerated with the Founder patch
  (all other generated Swift files are byte-identical to `26.10.15-atum.1`).
- `patches/atum-phone.patch`: Founder patch, SHA-256
  `d7b68182ed249fbc27b0993eedd7390c389ad844a121172727d34284b9247694`.
- `patches/source.json`: Founder manifest copied verbatim from the mobile pack
  (`sdk/phone-26.10.15-founder/source.json`), SHA-256
  `37b6fe5f7b14bdb38fd477d0d615ccc5546115c34bc69a1bf5c866efa51dbf2e`.
  Its status label is intentionally unchanged.
- `patches/atum-build-receipt.json`: CI build receipt from artifact
  `sdk-phone-phone-26.10.15-founder` (run `39609567202`), SHA-256
  `665ee0804d844a74920b3a223989ae71930c0c976dfd3e02f924de5c0c12f455`.
- `Package.swift`: remote target `26.10.15-atum.2`, checksum
  `0367555a1b7a1f0e775037ba1db2b9d93320255eb4919bcf781b32d3a9ada9c2`.
- `README.md` / `NOTICE`: new version row, verify example, Founder patch scope.

## Provenance

- Artifact zip SHA-256:
  `0367555a1b7a1f0e775037ba1db2b9d93320255eb4919bcf781b32d3a9ada9c2`
  (retained at `_atum-ops-scratch-1019/launch/phone-sdk-founder-publication-r1/artifact`).
- Artifact/receipt and proof matched the run at consumer `17f8fe2`.
- Generated Swift SHA-256 `65f8e32db590d01cef98049e2879f9037afa3c1a3e33de404329370325256eb2`
  equals the receipt's `generatedSwift.sha256`; markers
  `func accountDataRaw(eventType:`, `func fetchGlobalAccountDataRaw(eventType:)`,
  `class Room` are present.
- Upstream: matrix-rust-sdk `97a1589b70bd122c1d66e0d68ea008d8554076a5`,
  components release `26.10.15` (`dbdf59e13d0eade7fd9cbd01cfd564693b85b761`).

## Verification done in this commit

- `swift package dump-package` parsed the manifest (no resolve, no build, no download).
- `git diff --check` clean; no `.zip` or `.xcframework` in the tree.

## Not done here

- No push, PR, tag, release, CI dispatch, install, API write or spend.
- No mobile pin or consumer change (mobile is read-only from here).
- No Rust rebuild; the binary is the already-proofed artifact.
- No historical manifest mutation.

## Parent next steps

1. Open the one SDK PR from `release/26.10.15-atum.2`, review, merge to `main`.
2. Create the immutable `26.10.15-atum.2` release with the zip and
   `patches/atum-build-receipt.json` as assets; verify `isImmutable`.
3. Fold the mobile pin plus the Founder consumer into the existing mobile batch,
   after the SDK commit is published.
