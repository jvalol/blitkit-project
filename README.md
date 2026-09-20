# blitkit

A graphics engine in Rust, and the games that prove it works.

- [blitkit](blitkit) — the engine, a wrapper around wgpu.
- [pong](pong) — the first game on it.
- [snake](snake) — the second.
- [tetris](tetris) — the third.

Each is its own repo. They live together here because the games depend on the
engine by relative path, which is what keeps the engine honest: every game is a
test of using it from outside.

`./check-all` tests and lints all four in dependency order. `.cargo/config.toml`
points them at one shared build directory.

## Getting set up

Clone this repo, then clone the other four inside it. The games find the engine
at `../blitkit`, so those four folder names matter. What this one is called does
not.

```
git clone git@github.com:jvalol/blitkit-project.git
cd blitkit-project
git clone git@github.com:jvalol/blitkit.git
git clone git@github.com:jvalol/pong.git
git clone git@github.com:jvalol/snake.git
git clone git@github.com:jvalol/tetris.git
./check-all
```

Rust 1.87 or newer, which is wgpu's minimum. Each game runs with `cargo run`
from its own folder.
