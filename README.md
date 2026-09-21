# blitkit

A graphics engine in Rust, and the games that prove it works.

- [blitkit](blitkit) — the engine, a wrapper around wgpu.
- [pong](pong) — the first game on it.
- [snake](snake) — the second.
- [tetris](tetris) — the third.
- [marble](marble) — the first one in 3D.

Each is its own repo. They live together here because the 2D games depend on the
engine by relative path, which is what keeps the engine honest: every game is a
test of using it from outside. Marble goes further and takes blitkit from
crates.io, the way anyone else would.

`./check-all` tests and lints all five in dependency order. `.cargo/config.toml`
points them at one shared build directory.

## Getting set up

Clone this repo, then clone the others inside it. Pong, snake and tetris find
the engine at `../blitkit`, so those folder names matter. What this one is
called does not, and marble takes blitkit from crates.io rather than by path.

```
git clone git@github.com:jvalol/blitkit-project.git
cd blitkit-project
git clone git@github.com:jvalol/blitkit.git
git clone git@github.com:jvalol/pong.git
git clone git@github.com:jvalol/snake.git
git clone git@github.com:jvalol/tetris.git
git clone git@github.com:jvalol/marble.git
./check-all
```

Rust 1.87 or newer, which is wgpu's minimum. Each game runs with `cargo run`
from its own folder.
