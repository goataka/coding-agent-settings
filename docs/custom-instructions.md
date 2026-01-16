# カスタム指示（Custom Instructions）

[GitHub Copilot リポジトリカスタム指示の追加 - GitHub Docs](https://docs.github.com/ja/copilot/how-tos/configure-custom-instructions/add-repository-instructions)

## 概要

カスタム指示は、プロジェクト固有のコーディング規約や設計方針をGitHub Copilotに認識させるための設定です。技術スタック、命名規則、エラー処理の方針などを記述することで、Copilotの提案精度と一貫性が向上します。

## 設定方法

### 基本設定

1. リポジトリのルートに `.github` ディレクトリを作成
2. `.github/copilot-instructions.md` ファイルを作成
3. Markdown形式で自然言語の指示を記述

### パス固有の指示

複数のルールを細かく管理する場合は、`.github/instructions/` 配下に `[任意名].instructions.md` ファイルを作成し、YAMLフロントマターで適用パターンを指定します。

## 設定例

このリポジトリには実際の設定例が含まれています：

### 基本的なカスタム指示

TypeScript/React/Next.jsプロジェクト向けの基本設定です。

📄 [.github/copilot-instructions.md](../.github/copilot-instructions.md)

### 拡張子固有の指示

特定のファイルタイプに対してのみ適用されるルールを定義できます。

#### シェルスクリプト固有のルール

📄 [.github/instructions/shell.instructions.md](../.github/instructions/shell.instructions.md)

#### TypeScript固有のルール

📄 [.github/instructions/typescript.instructions.md](../.github/instructions/typescript.instructions.md)

### 単一ファイル固有の指示

特定のファイル1つだけに適用される詳細なルールを定義できます。

#### バリデーションファイルの例

📄 [.github/instructions/validation-file.instructions.md](../.github/instructions/validation-file.instructions.md)

## ベストプラクティス

- **簡潔に記述**: 冗長な説明は避け、要点のみを記載
- **具体的に**: 抽象的な表現より具体例を示す
- **階層化**: 大規模プロジェクトでは複数ファイルに分割して管理
- **更新を継続**: プロジェクトの変更に合わせて定期的に見直す

## その他の参考資料

- [カスタム指示について（英語）](https://docs.github.com/en/copilot/tutorials/customization-library/custom-instructions)
