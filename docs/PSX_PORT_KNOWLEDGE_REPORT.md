# Parasite Eve knowledge report

- Date: 2026-09-01
- Retail identity: USA `SLUS-00662` and `SLUS-00668`
- Architecture lane: source-only owned-input setup host
- Release target: Windows x64, Linux x64, macOS ARM64, and macOS x64; candidate version `0.3.5`

## Current state

The two-disc set is one program on two data images. The `v0.3.3` candidate keeps
the game source unchanged and uses the shared additive framework correction.
The final package passed its payload audit. Two fresh, spaced-path builds
produced identical runtime bytes. The final exact-ZIP runtime matched those
bytes. Headless Disc 1 startup reached frame 2573. Disc 2 reached frame 3821.
Both runs used SCPH-1001 and reported no fatal event.

The operator previously confirmed gameplay on the private build. Connected
in-game disc change remains open and is not inferred from independent startup.

## Release controls

- Framework: 94ea3b28c1b2f10f4b0ed960145bc96d415f2c36
- Deterministic build identity: `b5750bd13fb2366a13d0cf7f06ab9584bd2fd583`
- Deterministic link correction: `6b74231479230e2c4d11d3e817af5d4a7739ae0b`
- BIOS profile correction: `b2430fa43602131b0d5c71d5d31ccf5b567f1601`
- Correction parent: `e6d054de1538881cd81dcf3592de1f561afdbb5b`
- Frozen release base: `afe9ab299aab0eeba1cc31f81bc4baf4e7fb2ab7`
- Recomp-UI: `4eda65430a431e5685ae0c515ebcd912c7843bff`
- RetComM Studio: `249422969c1c59ac2a1f8aa2299e876a7133998e`
- Distribution: owned input only
- Platform claim: pending exact-package gates on all four targets

## Open gates

1. Bind publication authorization to the exact release manifest.
2. Create and audit the private release draft.
3. Redownload and verify the exact remote bytes.
4. Complete a natural connected disc-change route.

## Corpus consulted

The release work uses `PSX-DISC-001`, `PSX-PUB-004`, `PSX-PUB-006`,
`PSX-WIN-005`, `PSX-WIN-006`, and the release regression ledger.

## v0.3.5 three-platform refresh

The source now binds the package-only privacy correction and targets Windows
x64, Linux x64, macOS ARM64, and macOS x64. The replacement build-only CI,
complete archive audit, and native package gates remain required. This source
change does not publish a release or claim platform support.

## 2026-09-04 v0.3.6 POSIX setup-copy candidate

This candidate pins PSXRecomp f1d98082354641dd48750045517c23fe9ef13f34 and recomp-ui be8ac1d03ee19d55394b5a5f2d9d1506edd56659.
Linux and macOS packages use native CMake, Ninja, Python, C, and C++ tools.
Windows keeps the portable toolchain route. This change does not change game
code or the graduation state. Build-only CI and every exact-package release
gate must pass before publication.
