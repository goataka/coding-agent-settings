# エージェントスキル（Agent Skills）

[エージェントスキルについて - GitHub Docs](https://docs.github.com/ja/copilot/concepts/agents/about-agent-skills)

## 概要

エージェントスキルは、特定の業務フローやタスクを実行するための手順書をCopilotに提供する機能です。定型的な作業手順やドメイン固有の知識を「スキル」として定義することで、Copilotがより効率的にタスクを実行できるようになります。

## 設定方法

### ファイルの配置

プロジェクトスキルは `.github/skills/` ディレクトリに配置します。

```
.github/
└── skills/
    ├── webapp-testing/
    │   └── SKILL.md
    └── github-actions-debugging/
        └── SKILL.md
```

### 基本構成

各スキルは専用ディレクトリに `SKILL.md` ファイルを配置します。ファイル名は必ず `SKILL.md` としてください。

```yaml
---
name: スキル名（小文字・ハイフン区切り）
description: スキルの目的と利用タイミングの説明
license: ライセンス情報（オプショナル）
---

スキルの具体的な手順、例、ガイドラインをMarkdownで記述
```

## 設定例

このリポジトリには実際の設定例が含まれています：

### GitHub Actions障害デバッグスキル

CI/CDパイプラインの失敗を体系的にデバッグする手順を提供します。

📄 [.github/skills/github-actions-debugging/SKILL.md](../.github/skills/github-actions-debugging/SKILL.md)

### Webアプリケーションテストスキル

Webアプリケーションのテスト作成と実行の標準手順を定義します。

📄 [.github/skills/webapp-testing/SKILL.md](../.github/skills/webapp-testing/SKILL.md)

### データベースマイグレーションスキル

データベーススキーマ変更時の安全なマイグレーション手順を提供します。

📄 [.github/skills/database-migration/SKILL.md](../.github/skills/database-migration/SKILL.md)

## スキルとカスタム指示の使い分け

### エージェントスキルが適している場合
- 複数ステップの業務フロー
- 特定の状況でのみ必要な専門知識
- 定型的な作業手順

### カスタム指示が適している場合
- 常に守るべきコーディング規約
- プロジェクト全体に適用されるルール
- 技術スタックや設計方針

## ベストプラクティス

- **明確な手順**: ステップバイステップで記述
- **実行可能**: 具体的なコマンドや操作を含める
- **コンテキスト**: いつ使うべきかを明示
- **スクリプト同梱**: 必要に応じて補助スクリプトも配置可能
- **小さく分割**: 1つのスキルは1つの業務フローに集中

## 共有スキルの活用

コミュニティで公開されているスキルも利用できます：

- [Anthropic Skills Collection](https://github.com/anthropics/skills)
- [GitHub Awesome Copilot](https://github.com/github/awesome-copilot)

## その他の参考資料

- [VS Code でのエージェントスキル利用](https://code.visualstudio.com/docs/copilot/customization/agent-skills)
