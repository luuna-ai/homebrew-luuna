# Luuna Homebrew tap (draft)

This tap contains a source-build formula draft for the **Luuna CLI/runtime
suite**: terminal client and runtime plus the pinned Missions, Atlas, and Beacon
CLIs. It does not install the Luuna workbench desktop app or the separate Luuna
AI desktop app.

The formula is pinned to immutable organization commits and includes a
versioned, SHA-256-verified Bun runtime. The dedicated tap source is prepared
for review, but Homebrew audit/install and native platform builds have not yet
passed. Treat these files as an unverified draft until macOS and Linux builds
and installation smoke checks succeed. Do not advertise the formula as a
supported installation path yet.

## Intended commands after platform validation

```sh
brew tap luuna-ai/luuna
brew install luuna-ai/luuna/luuna
luuna-doctor
lu help
luuna-runtime --help
luuna-missions --help
luuna-atlas --help
luuna-beacon --help
```

Upgrade with `brew upgrade luuna`; uninstall with `brew uninstall luuna`.
Homebrew will leave the user's `~/.luuna` data directory in place. The runtime
also requires a separately installed/configured Pi executable and provider
credentials for model-backed work; installation does not create or store
credentials.

## Formula review

On each supported Mac and Linux architecture, validate the formula with:

```sh
brew audit --strict --formula Formula/luuna.rb
brew install --build-from-source --formula ./Formula/luuna.rb
luuna-doctor
```

Run the formula's test block and verify upgrade/uninstall behavior while keeping
`~/.luuna` untouched. Record platform, architecture, toolchain versions, and
actual command outputs. The original packaging workspace lacked Homebrew, Ruby,
Rust, Bun, and a usable Go toolchain, so none of those checks are claimed here.

Desktop packaging is tracked separately in [DESKTOP-RELEASE-MATRIX.md](DESKTOP-RELEASE-MATRIX.md).
