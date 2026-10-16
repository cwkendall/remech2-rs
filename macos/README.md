# ReMech 2 on macOS (Apple Silicon)

ReMech 2 built natively for Apple Silicon: upstream's own code, which
builds the whole game from source, with the few changes macOS needs.
Graphics go through wgpu on Metal.

You need your own copy of the game (see the main `README.md`).

## Download

Builds from this branch are attached to the fork's GitHub Actions runs
(`ReMech2-macOS-arm64`), and to releases. The app isn't notarised: after
unzipping, clear the download flag once with
`xattr -d com.apple.quarantine remech2`, or open it with right-click,
Open.

## Build

With Rust installed (rustup):

```sh
cargo build --release
target/release/remech2
```

## Running

It finds the game in the folder it's started from, if that folder has
`MW2.PRJ` or an empty `portable.txt`; otherwise in
`~/Library/Application Support/ReMech2/game` (settings and saves go
beside it, in `user/`). If neither has the game, it offers to install it
from the CD, as the main `README.md` describes.

The game pauses whenever its window isn't focused (as on Windows): no
frames, no keys. Click the window if it was started from another app.

## Upstream

Changes that macOS needs in upstream's code are kept small and
`cfg`-gated, so they can be offered upstream.
