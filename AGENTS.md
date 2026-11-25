# lib-mood

`mood` — mood (mode-of-data) operations for the handl runtime: the
`.hnl` interface (`src/index.hnl`, cap/op declarations) plus the Rust
crate embedding it.

## Layout

| path | role |
| --- | --- |
| `src/index.hnl` | the interface — cap/op declarations |
| `src/lib.rs`, `src/ops.rs` | the Rust crate (`handl-plugin-lib-mood`-style embedding) |
| `atoms.yaml` | atom declarations |
| `Cargo.toml`, `xtask/` | crate manifest + `cargo xtask` gate |
| `pkg.hnl` | package manifest — `modules: ["mood"]` |
| `scripts/hnl-gate.sh`, `ci.sh` | the hnl gate / bupha entry |

## Contract

- Mood ops: ind/int/norm/pot/neg/cnd projection, intersection,
  normalization and fallback (see `pkg.hnl` description).
- Transitional layout: implementations are native Rust handls in
  `plugin-lib-utils`.

## Verification

```bash
cargo xtask gate        # fmt --check → clippy -D warnings → test → doc
HNL=../host-cli/target/debug/hnl scripts/hnl-gate.sh   # the .hnl side
```

## License

MIT.

<!-- myco:agent-awareness -->

## Agent awareness

- Session start / any work discussion: run `myco status --prompt`
  before proposing next steps — know the board first.
- User describes new work → offer to capture it (`myco todo add`,
  `issue new`, `proposal new`). Don't wait to be asked.
- Picking up a task: `myco resume <ID>` is the briefing.
- Wrapping up: `myco handoff <ID>` anything resumable; keep statuses
  honest (claimed → in-progress → blocked/done).

<!-- /myco:agent-awareness -->
