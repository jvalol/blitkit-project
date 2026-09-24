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

## Demos

The engine carries its own, run from the `blitzkit` folder.

```
cargo run --release --example klein
```

A Klein bottle you can turn any way you drag it, drawn as a wire mesh so the
neck is visible where it passes through the wall. The surface has no outside, so
both sides of it are drawn and neither one is culled away. `cubes` and `rolling`
are the other two: lit textured geometry, and a ball with collision and shadows.
