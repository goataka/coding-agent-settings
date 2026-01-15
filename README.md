# coding-agent-settings

GitHub Copilot Agentで使用できる各種設定の説明と設定例を管理します。

## 前提条件

このリポジトリで扱う設定は、**GitHub Copilot Agent**（コーディングエージェント）で作用する設定のみを対象としています。

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
- GitHub Copilot Agent（コーディングエージェント）
- GitHub Copilot CLI

## 設定ファイル

- [カスタム指示の設定](./docs/custom-instructions.md)
- [カスタムエージェントの設定](./docs/custom-agents.md)
- [エージェントスキルの設定](./docs/agent-skills.md)

## 参考資料

- [GitHub Copilot 公式ドキュメント](https://docs.github.com/ja/copilot)