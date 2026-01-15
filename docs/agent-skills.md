# エージェントスキル（Agent Skills）

## 概要

エージェントスキルは、特定の業務フローやタスクを実行するための手順書をCopilotに提供する機能です。定型的な作業手順やドメイン固有の知識を「スキル」として定義することで、Copilotがより効率的にタスクを実行できるようになります。

## 設定方法

### ファイルの配置

#### プロジェクトスキル（リポジトリ単位）
```
.github/
└── skills/
    ├── webapp-testing/
    │   └── SKILL.md
    └── github-actions-debugging/
        └── SKILL.md
```

#### パーソナルスキル（個人単位）
```
~/.copilot/
└── skills/
    └── custom-workflow/
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

### GitHub Actions障害デバッグスキル

```markdown
---
name: github-actions-failure-debugging
description: GitHub Actionsのワークフロー失敗時のデバッグ手順。ワークフローのデバッグを依頼された際に使用
---

# GitHub Actions障害デバッグスキル

GitHub Actionsのワークフロー失敗時のデバッグ手順です。

## デバッグ手順

1. `list_workflow_runs` ツールを使用して、最近のワークフロー実行状況を確認
2. `summarize_job_log_failures` ツールでエラーログの要約を取得し、問題箇所を特定
3. 詳細が必要な場合は `get_job_logs` または `get_workflow_run_logs` で完全なログを取得
4. 自分の環境でエラーを再現
5. 修正を実施し、コミット前に動作確認

## 注意事項

- ログは大量になる可能性があるため、要約から始めること
- 複数のジョブが失敗している場合は並行して調査
```

### Webアプリケーションテストスキル

```markdown
---
name: webapp-testing
description: Webアプリケーションのテスト実施手順。E2Eテストの作成や実行を依頼された際に使用
---

# Webアプリケーションテストスキル

## テスト準備

1. テスト対象の機能仕様を確認
2. テストケースの洗い出し（正常系・異常系）
3. テストデータの準備

## テスト実装手順

### 単体テスト
- コンポーネントは独立してテスト
- モックやスタブを活用
- エッジケースも含める

### 統合テスト
- APIとの連携を確認
- データフローを検証
- エラーハンドリングをテスト

### E2Eテスト
- ユーザーシナリオに基づいて実施
- 主要な業務フローを網羅
- ブラウザ互換性を考慮

## テスト実行

```bash
# 単体テスト実行
npm run test:unit

# 統合テスト実行
npm run test:integration

# E2Eテスト実行
npm run test:e2e
```

## カバレッジ確認

テストカバレッジは最低80%を目標とする。
```

### データベースマイグレーションスキル

```markdown
---
name: database-migration
description: データベーススキーマ変更とマイグレーション手順。DB変更を依頼された際に使用
---

# データベースマイグレーションスキル

## マイグレーション作成手順

1. 変更内容の設計と影響範囲の確認
2. マイグレーションファイルの作成
3. ロールバック用のダウンマイグレーションも作成
4. 開発環境でテスト実行

## 実装ガイドライン

### テーブル作成
- 主キーは必ず定義
- インデックスは適切に設定
- 外部キー制約を活用

### カラム変更
- NULL制約の追加は既存データを確認
- デフォルト値を適切に設定
- データ型変更は慎重に

### データ移行
- 大量データの場合はバッチ処理
- トランザクション管理を徹底
- バックアップを必ず取得

## 実行コマンド

```bash
# マイグレーション作成
npm run migration:create -- [マイグレーション名]

# マイグレーション実行
npm run migration:run

# ロールバック
npm run migration:revert
```
```

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

## 参考資料

- [エージェントスキルについて（日本語）](https://docs.github.com/ja/copilot/concepts/agents/about-agent-skills)
- [エージェントスキルについて（英語）](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills)
- [VS Code でのエージェントスキル利用](https://code.visualstudio.com/docs/copilot/customization/agent-skills)
