# coding-agent-settings

GitHub Copilot Coding Agentで使用できる各種設定の説明と設定例を管理します。

## 前提条件

このリポジトリで扱う設定は、**GitHub Copilot Coding Agent**（コーディングエージェント）で作用する設定のみを対象としています。

### 対象となる設定

- **カスタム指示**（Custom Instructions）: リポジトリ全体に適用されるコーディング規約や設計方針
- **カスタムエージェント**（Custom Agents）: 特定のタスクに特化したAIエージェントの設定
- **エージェントスキル**（Agent Skills）: 特定の業務フローやタスクを実行するための手順書

### 対象外となる設定

- IDE（Visual Studio Code、JetBrains、Xcodeなど）でのみ利用可能な設定
- IDE固有の拡張機能やプラグイン設定

### 利用可能な環境

本リポジトリの設定は以下の環境で利用できます：

- GitHub Copilot Pro / Pro+ / Business / Enterprise
- GitHub Copilot Coding Agent（コーディングエージェント）
- GitHub Copilot CLI

## ドキュメント

- [設定の使い分けガイド](./docs/usage-guide.md) - どの設定をいつ使うべきか
- [カスタム指示の設定](./docs/custom-instructions.md)
- [カスタムエージェントの設定](./docs/custom-agents.md)
- [エージェントスキルの設定](./docs/agent-skills.md)

## このリポジトリの設定ファイル

このリポジトリ自体にGitHub Copilot Coding Agentの設定例が含まれています：

### AIモデル固有の指示

- [AGENTS.md](./AGENTS.md) - プロジェクト全体のエージェント設定（ルート）
- [CLAUDE.md](./CLAUDE.md) - Claude専用の指示
- [GEMINI.md](./GEMINI.md) - Gemini専用の指示
- [frontend/AGENTS.md](./frontend/AGENTS.md) - フロントエンド配下で優先される設定
- [backend/AGENTS.md](./backend/AGENTS.md) - バックエンド配下で優先される設定

### カスタム指示

- [.github/copilot-instructions.md](./.github/copilot-instructions.md) - プロジェクト全体の基本設定
- [.github/instructions/shell.instructions.md](./.github/instructions/shell.instructions.md) - シェルスクリプト固有のルール
- [.github/instructions/typescript.instructions.md](./.github/instructions/typescript.instructions.md) - TypeScript固有のルール
- [.github/instructions/validation-file.instructions.md](./.github/instructions/validation-file.instructions.md) - 単一ファイル用の例

### カスタムエージェント

- [.github/agents/test-specialist.agent.md](./.github/agents/test-specialist.agent.md) - テスト専門エージェント

### エージェントスキル

- [.github/skills/github-actions-debugging/SKILL.md](./.github/skills/github-actions-debugging/SKILL.md) - CI/CD障害デバッグ
- [.github/skills/webapp-testing/SKILL.md](./.github/skills/webapp-testing/SKILL.md) - Webアプリケーションテスト
- [.github/skills/database-migration/SKILL.md](./.github/skills/database-migration/SKILL.md) - データベースマイグレーション

## 参考資料

- [GitHub Copilot 公式ドキュメント](https://docs.github.com/ja/copilot)