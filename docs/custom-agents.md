# カスタムエージェント（Custom Agents）

[カスタムエージェント設定リファレンス - GitHub Docs](https://docs.github.com/ja/copilot/reference/custom-agents-configuration)

## 概要

カスタムエージェントは、特定のタスクや役割に特化したAIアシスタントをリポジトリ単位で定義できる機能です。テスト担当、設計担当、ドキュメント担当など、専門性を持ったエージェントを作成できます。

## 設定方法

### ファイルの配置

カスタムエージェントの設定ファイルは `.github/agents/` ディレクトリに配置します。

```
.github/
└── agents/
    ├── test-specialist.agent.md
    ├── backend-expert.agent.md
    └── documentation-writer.agent.md
```

### 基本構成

YAMLフロントマターでエージェントの属性を定義し、その後にMarkdown形式で具体的な指示を記述します。

```yaml
---
name: エージェント名（小文字・ハイフン区切り）
description: エージェントの役割と目的の説明
tools: 利用可能なツールのリスト
infer: true または false（自動選択の有無）
---

エージェントの具体的な役割、専門性、推奨手法などをMarkdownで記述
```

## 設定例

このリポジトリには実際の設定例が含まれています：

### テスト専門エージェント

テストコードの作成、品質レビュー、カバレッジ向上に特化したエージェントです。

📄 [.github/agents/test-specialist.agent.md](../.github/agents/test-specialist.agent.md)

## プロパティ説明

### 必須プロパティ

- **name**: エージェントの識別子（小文字、ハイフン区切り）
- **description**: エージェントの目的と専門領域（Copilotがエージェント選択時に参照）

### オプショナルプロパティ

- **tools**: 利用可能なツールのリスト
  - `["*"]`: すべてのツールを許可
  - `["read", "edit", "search"]`: 特定のツールのみ許可
  - `[]`: すべてのツールを無効化
- **infer**: Copilotが自動でこのエージェントを提案するか（デフォルト: true）

### 利用可能なツール

| ツール名 | 用途 |
|---------|------|
| read | ファイルの読み取り |
| edit | ファイルの編集 |
| search | テキスト・ファイル検索 |
| shell | シェルコマンド実行 |
| web | Web情報の取得 |
| agent | 他のカスタムエージェント呼び出し |

## ベストプラクティス

- **専門性を明確に**: 各エージェントは特定の領域に特化させる
- **役割の分離**: 責任範囲を明確にし、重複を避ける
- **制約の明示**: やってはいけないことも記述する
- **実例を含める**: 期待する出力例を示すと効果的

## その他の参考資料

- [カスタムエージェント設定リファレンス（英語）](https://docs.github.com/en/copilot/reference/custom-agents-configuration)
