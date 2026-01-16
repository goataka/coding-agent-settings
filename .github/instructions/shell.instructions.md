---
applyTo: "**/*.sh"
excludeAgent: "code-review"
---

# シェルスクリプト固有のルール

このルールはCoding Agent実行時のみ適用されます（コードレビューでは適用されません）。

- shebangは必ず記述する（`#!/bin/bash` または `#!/bin/sh`）
- set -euo pipefail でエラーハンドリングを強化する
- 変数は ${} で囲む
- shellcheck の警告に従う
