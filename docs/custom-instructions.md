# カスタム指示（Custom Instructions）

## 概要

カスタム指示は、プロジェクト固有のコーディング規約や設計方針をGitHub Copilotに認識させるための設定です。技術スタック、命名規則、エラー処理の方針などを記述することで、Copilotの提案精度と一貫性が向上します。

## 設定方法

### 基本設定

1. リポジトリのルートに `.github` ディレクトリを作成
2. `.github/copilot-instructions.md` ファイルを作成
3. Markdown形式で自然言語の指示を記述

### パス固有の指示

複数のルールを細かく管理する場合は、`.github/instructions/` 配下に `[任意名].instructions.md` ファイルを作成し、YAMLフロントマターで適用パターンを指定します。

```markdown
---
applyTo: "src/backend/**"
---
# バックエンド開発ルール
モデルクラスには必ずバリデーションを定義してください。
```

## 設定例

### 基本的なカスタム指示

```markdown
# 技術スタック
- Python 3.11
- FastAPI
- PostgreSQL

# 命名規則
- 関数名: snake_case
- クラス名: PascalCase
- 定数: UPPER_SNAKE_CASE

# コーディング規約
- 型ヒントを必ず使用する
- docstringはGoogle形式で記述する
- 1行の長さは最大88文字とする

# エラーハンドリング
- カスタム例外は `utils/exceptions.py` で定義する
- API例外は必ず適切なHTTPステータスコードを返す

# テスト方針
- 単体テストはpytestを使用する
- テストカバレッジは80%以上を維持する
```

### TypeScriptプロジェクトの例

```markdown
# 技術スタック
- TypeScript 5.x
- React 18
- Next.js 14

# 命名規則
- 関数・変数: camelCase
- コンポーネント・型・インターフェース: PascalCase
- 定数: UPPER_SNAKE_CASE

# 設計方針
- クリーンアーキテクチャを採用
- ビジネスロジックとUIを分離
- 依存性注入を活用

# エラー処理
- Result型パターンを使用（Either型でも可）
- try-catchは最小限に留める
```

## ベストプラクティス

- **簡潔に記述**: 冗長な説明は避け、要点のみを記載
- **具体的に**: 抽象的な表現より具体例を示す
- **階層化**: 大規模プロジェクトでは複数ファイルに分割して管理
- **更新を継続**: プロジェクトの変更に合わせて定期的に見直す

## 参考資料

- [GitHub Copilot リポジトリカスタム指示の追加](https://docs.github.com/ja/copilot/how-tos/configure-custom-instructions/add-repository-instructions)
- [カスタム指示について（英語）](https://docs.github.com/en/copilot/tutorials/customization-library/custom-instructions)
