---
applyTo: "**/*.sh"
---

# シェルスクリプト固有のルール

- shebangは必ず記述する（`#!/bin/bash` または `#!/bin/sh`）
- set -euo pipefail でエラーハンドリングを強化する
- 変数は ${} で囲む
- shellcheck の警告に従う
