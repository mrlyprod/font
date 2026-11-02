mrly-font; a MrlyMath crate: the alphabet, a stroked pixel font of 108 characters, painted whole or written stroke by stroke

# FONT

- Its bindings sit beside it, written by `mrly-bridge` from `bridge.toml` and `src/`: `js/` (`@mrlyprod/font`), `py/` (`mrly.font`) and `cli/` (`mrly-font`); `manifest.json` lists every crossing and `.gitattributes` every generated file.
- Builds on nothing; `scripts/bridge.sh` rewrites the bindings.
- `scripts/check.sh` is the one gate: fmt, clippy, test, doc, bridge check, ruff, wasm, the leaves' tests, leak.
- A fresh clone runs `scripts/wasm.sh` once before any host builds: it writes `js/pkg/`, which is not committed.
- Until the crates are published, clone the fleet beside this repo: `scripts/bridge.sh` runs the sibling `../bridge`, and a `.cargo/config.toml` with `[patch.crates-io]` rows points every `mrly-*` dependency at its sibling folder.
- Docs: [docs.rs/mrly-font](https://docs.rs/mrly-font).

```rust
assert_eq!(mrly_font::supported().len(), 108);
assert_eq!(mrly_font::glyph('a').unwrap().rows[0], "01110");
assert_eq!(mrly_font::raster("42").len(), 5);
```
