# Development log

## 2026-09-01: deterministic Windows link

Repeated MinGW links changed 16 bytes in the product executable. The changes
included the PE timestamp and the build-ID record. Raw SHA-256 continuity was
therefore not possible.

GNU ld documents `--no-insert-timestamp` for PE targets. It states that the
option writes a zero timestamp so identical inputs can produce identical files:
<https://www.sourceware.org/binutils/docs/ld/Options.html>.

Framework commit `6b74231479230e2c4d11d3e817af5d4a7739ae0b` now applies
`--no-insert-timestamp` and an explicit content-based build ID to MinGW product
links. A source test guards both options. Two repeat-link probes produced the
same SHA-256 value. Two links from the exact package also produced SHA-256
`BCCF4C64D43FD5AFA7A5C29A4EE0445E187EA9369E2D0B653C83FB4A8D27C10E`.
This value replaces the stale candidate hash.

The next clean extraction changed 12 bytes. Four bytes came from `__DATE__`
and `__TIME__` in the crash identity. Those input changes also changed eight
bytes in the content-derived RSDS identifier. Framework commit `b5750bd1`
removes the volatile macros and extends the source regression to guard both
the compile input and the MinGW link options. Distinct-path clean-build proof
remains a release gate.

Two clean package builds in different extraction paths now produce SHA-256
`879FFDE21A49A9894531CE062884B6178ADD6EF51BC288DA7A1A8F3B35DFE502`.
This exact value replaces all earlier candidate runtime hashes.

## 2026-09-01: v0.3.3 executable-name reconciliation

The source uses `Parasite_Eve` for the CMake output, code-generation setup,
and package setup host. Two fresh extractions of the initial `v0.3.3` ZIP had
no build directory or executable-name marker. Both generated from the owned
Disc 1 and SCPH-1001 inputs. Both hidden builds produced runtime SHA-256
`2748570FE0F7E1BC1AAFC11C17C312764FED3987E3190D0A70F3544EE8FCE28C`.
The final exact-ZIP build matched that hash. Headless startup reached frame
2573 on Disc 1 and frame 3821 on Disc 2. Both runs reported no fatal event.
