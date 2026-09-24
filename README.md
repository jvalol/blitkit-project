# blitzkit

A graphics engine in Rust, and the games that prove it works.

- [blitzkit](blitzkit) — the engine, a wrapper around wgpu.
- [pong](pong) — the first game on it.
- [snake](snake) — the second.
- [tetris](tetris) — the third.
- [marble](marble) — the first one in 3D.

Each is its own repo, and each depends on the published blitzkit the way anyone
else would. They live together here because `.cargo/config.toml` overrides that
with the engine checkout, which is what keeps the engine honest: every game is a
test of using it from outside, and a breaking change shows up before it ships.

`./check-all` tests and lints all five in dependency order. `.cargo/config.toml`
points them at one shared build directory.

## Getting set up

Clone this repo, then clone the others inside it. The override names the engine
folder `blitzkit`, so that one matters. What this folder is called does not, and
outside it the games build against crates.io.

```
git clone git@github.com:jvalol/blitzkit-project.git
cd blitzkit-project
git clone git@github.com:jvalol/blitzkit.git
git clone git@github.com:jvalol/pong.git
git clone git@github.com:jvalol/snake.git
git clone git@github.com:jvalol/tetris.git
git clone git@github.com:jvalol/marble.git
./check-all
```

Rust 1.87 or newer, which is wgpu's minimum. Each game runs with `cargo run`
from its own folder.
