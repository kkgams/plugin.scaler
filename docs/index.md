---
title: plugin.scaler
description: Scale tile maps.
status: reference
---

# plugin.scaler

A [GAMS](https://github.com/kkgams/gams) WASM plugin for scaling tile maps.

| Unit | Source / artifact | Original work |
| --- | --- | --- |
| Tilemap scaler | `plugins/scaler.comp/main.go` / `plugin.scaler.wasm` | GAMS |

## API

`plugins/scaler.comp/wit/package.wit` defines `gams:scaler/scaler@1.0.0`: `scale(src, config)` with a scale factor and optional cardinal door sizes, returning a tile map or error. Maps contain layers with widths, flat tile arrays and string-pair properties. The `scaler-plugin` world uses Host-provided WASI imports.

## Development

Use `nix develop` (or direnv) for pinned Go 1.25, TinyGo, wasm-tools and documentation tools. No sibling checkout is required.

| Command | Purpose |
| --- | --- |
| `make build` | Compile and validate the component with embedded notices. |
| `make package` | Prepare `build.nosync/plugin.scaler.wasm`, `LICENSES.zip` and `SHA256SUMS` incrementally. |
| `make test` | Run the existing native plugin and SDK Go tests. |
| `make check` | Check Python tooling syntax; native tests are separate from WASM runtime coverage. |
| `make open` | Build and open this local Project in the released macOS Apple Silicon Host. |
| `make docs` | Build the wiki to `build.nosync/site`. |
| `make serve-docs` | Preview the wiki; `DOCS_PORT` defaults to 8080. |
| `make validate-docs` | Validate wiki content. |
| `make clean` | Remove all of `build.nosync/`, `tools/` and `gams_modules/`, including unmarked contents; refuse tracked files and symlinks before deleting anything. |

The local Project browses files with pinned published Units; it is not a tilemap editor or runtime test. Downloads preserve accompanying notices and existing Host tools. Packaging does not verify native Host/API behavior.
