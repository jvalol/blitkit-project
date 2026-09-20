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
