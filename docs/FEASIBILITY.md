# Parasite Eve release feasibility

Status: `bootstrap_verified`; four-platform `v0.3.6` package pending exact-package gates

The operator confirmed that the earlier private build reaches gameplay. The
new frozen-source build also passed measured headless startup on both supported
discs with SCPH-1001: Disc 1 reached frame 604 and Disc 2 reached frame 701.

The owned USA set contains `SLUS-00662` and `SLUS-00668`. Both discs contain
the same boot executable SHA-256,
`5d94938ee752e81ef375bd4493c9883850c25a86895f9cb0732cf3622b44351b`.
The frozen verifier classifies the set as one program on two data images. One
setup host is valid.

The package must validate and remember both discs. Mid-session disc change is
a separate gameplay seam and remains untested. The public package must not
contain a disc, retail BIOS, generated retail code, save, prebuilt playable
executable, or private absolute path.

The prior `v0.3.2` package passed payload and startup checks. Exact-package
Disc 1 startup reached frame 2953. Exact-package Disc 2 startup reached frame
4549. Both runs used SCPH-1001.

Two clean setup builds in different extraction paths produced identical runtime
bytes. The setup host SHA-256 is
`dfb2b5480c3a81b5d9bf653933fd7c14fbe018268b6d863a2591420bef4d59f7`.
The `v0.3.3` ZIP passed two fresh, spaced-path generation and build checks.
Both builds produced runtime SHA-256
`2748570fe0f7e1bc1aafc11c17c312764fed3987e3190d0a70f3544ee8fce28c`.
The final exact-ZIP runtime matched that hash. Headless Disc 1 startup reached
frame 2573. Disc 2 reached frame 3821. Both runs used SCPH-1001 and reported
no fatal event.

The candidate uses local framework child `b5750bd1` for deterministic build
identity. It is a child of test-registration correction `a16cc8b9` and
deterministic-link correction `6b742314`. That correction is a child of BIOS correction
`b2430fa4`. The BIOS correction is a child of CI correction `e6d054de`.
The CI correction is an additive child of frozen release base `afe9ab29`.
Publication and remote download verification are separate gates.

## v0.3.5 three-platform refresh

The candidate targets Windows x64, Linux x64, macOS Apple Silicon ARM64, and
macOS Intel x64. The setup package uses an additive framework correction that
excludes two non-SDK helpers with developer-machine paths. Each exact package
must pass the payload, setup, startup, responsiveness, and clean-exit gates on
its declared platform before publication.

## 2026-09-03 portable Linux package

The release workflow now builds Linux in a pinned Ubuntu 20.04 container.
The package gate rejects a setup host or emitter that needs a glibc version
newer than 2.31. This keeps the release compatible with the qualified Rocky
Linux 9 host. Windows and both macOS builds keep their existing runners.

## 2026-09-04 v0.3.6 POSIX setup-copy candidate

This candidate pins PSXRecomp f1d98082354641dd48750045517c23fe9ef13f34 and recomp-ui be8ac1d03ee19d55394b5a5f2d9d1506edd56659.
Linux and macOS packages use native CMake, Ninja, Python, C, and C++ tools.
Windows keeps the portable toolchain route. This change does not change game
code or the graduation state. Build-only CI and every exact-package release
gate must pass before publication.
