# lib-mood

`mood` — mood (mode-of-data) operations for the handl runtime: the
`.hnl` documentation surface (`src/index.hnl`) plus the Rust crate
providing the `Op` impls.

## Layout

| path | role |
| --- | --- |
| `src/index.hnl` | the interface — documentation surface; atom spec in `atoms.yaml` |
| `src/lib.rs`, `src/ops.rs` | the Rust crate (`handl-lib-mood`) — `Op` impls + `mood_op_registry()` |
| `atoms.yaml` | atom spec (P-013/T-151) |
| `Cargo.toml`, `xtask/` | crate manifest + `cargo xtask` gate |
| `pkg.hnl` | package manifest — `modules: ["mood"]` |
| `scripts/hnl-gate.sh`, `workflows/gate.yaml` | the hnl gate / bupha entry |

## Contract

- Mood ops: ind/int/norm/pot/neg/cnd projection, intersection,
  normalization and fallback (see `pkg.hnl` description).
- Spec-driven layout: `atoms.yaml` is the spec; the `Op` impls live
  in this crate (`src/ops.rs`) and resolve via the host's
  `mood_impls()` table (`plugin-lib-stdlib` `ops/kernel_impls.rs`).

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
