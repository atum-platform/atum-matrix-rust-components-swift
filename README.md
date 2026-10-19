# atum-matrix-rust-components-swift

Swift Package distribution of Atum's patched build of
[matrix-rust-sdk](https://github.com/matrix-org/matrix-rust-sdk), used by the Atum
iOS app. It mirrors the layout of
[element-hq/matrix-rust-components-swift](https://github.com/element-hq/matrix-rust-components-swift)
release `26.10.15`, with a small patch on top (see [NOTICE](NOTICE) and
[`patches/atum-phone.patch`](patches/atum-phone.patch)).

This is not a general-purpose fork. It is published so that Swift Package Manager can
resolve Atum's app dependency without private credentials. For your own projects,
use the upstream package.

## Versions

| Tag | Upstream release | Rust SDK revision | Platforms | XCFramework SHA-256 |
| --- | --- | --- | --- | --- |
| `26.10.15-atum.1` | `26.10.15` | `97a1589b70bd122c1d66e0d68ea008d8554076a5` | iOS 26 arm64 device + arm64 simulator | `aa109efa75a20d8cbb6097d83342680dd969e7d9b78050ab567077b0f25c8c84` |

Releases are immutable: a fix ships as a new tag (`-atum.2`, …), never as a
replaced asset.

## Verify

```sh
curl -LO https://github.com/atum-platform/atum-matrix-rust-components-swift/releases/download/26.10.15-atum.1/MatrixSDKFFI.xcframework.zip
swift package compute-checksum MatrixSDKFFI.xcframework.zip   # must equal the checksum in Package.swift
```

[`patches/atum-build-receipt.json`](patches/atum-build-receipt.json) is the CI build
receipt: toolchain (Rust 1.96.0, Xcode 27.0 27A266a), the per-file SHA-256 of every
header, static library and generated Swift file, and the patched-source digests.
[`patches/source.json`](patches/source.json) pins the upstream revisions and the
before/after digest of each patched file.

## License

Apache License 2.0 — see [LICENSE](LICENSE) and [NOTICE](NOTICE).
