# coding-agent-settings

GitHub Copilot Coding Agentで使用できる各種設定の説明と設定例を管理します。

## 前提条件

このリポジトリで扱う設定は、**GitHub Copilot Coding Agent**（コーディングエージェント）で作用する設定のみを対象としています。

### 利用可能な環境

本リポジトリの設定は以下の環境で利用できます：

- GitHub Copilot Pro / Pro+ / Business / Enterprise
- GitHub Copilot Coding Agent（コーディングエージェント）
- GitHub Copilot CLI

## 設定の種類と使い分け

GitHub Copilot Coding Agentには複数の設定方法があります。

- **カスタム指示**: コーディング規約や具体的なルールを指定
- **エージェント設定**: プロジェクト概要や背景をエージェントに説明

### 用途別の使い分け

**エージェント設定（エージェント向け説明）:**
- **プロジェクト概要・方針**（例: `AGENTS.md`） → [エージェント](#エージェントagentsmd等)
- **特定タスク専門家** → [カスタムエージェント](#カスタムエージェント)
- **定型作業手順** → [エージェントスキル](#エージェントスキル)

**カスタム指示（具体的なルール指定）:**
- **プロジェクト全体のルール** → [カスタム指示（リポジトリ全体）](#カスタム指示リポジトリ全体)
- **言語・ディレクトリ別ルール** → [カスタム指示（パス固有）](#カスタム指示パス固有単一ファイル)
- **特定ファイル専用ルール** → [カスタム指示（単一ファイル）](#カスタム指示パス固有単一ファイル)

まず**カスタム指示**から始めることを推奨します。プロジェクトの基本的なルールを定義してから、必要に応じてエージェントやスキルを追加していきます。小規模プロジェクトではカスタム指示だけでも十分な場合があります。

### カスタム指示の比較

| 項目 | 配置場所 | 適用範囲 | 適用タイミング |
|------|---------|---------|--------------|
| **カスタム指示**<br>（リポジトリ全体） | `.github/copilot-instructions.md` | リポジトリ全体 | 常時 |
| **カスタム指示**<br>（パス固有） | `.github/instructions/*.instructions.md` | 指定パス配下 | 常時（該当ファイル時） |
| **カスタム指示**<br>（単一ファイル） | `.github/instructions/*.instructions.md` | 特定ファイルのみ | 常時（該当ファイル時） |

### エージェント設定の比較

| 項目 | 配置場所 | 適用範囲 | 適用タイミング |
|------|---------|---------|--------------|
| **エージェント**<br>（AGENTS.md等） | ルートまたはディレクトリ内 | 最寄りのファイルから下位全体 | 常時（最寄り優先） |
| **カスタムエージェント** | `.github/agents/*.agent.md` | タスク・役割ごと | エージェント選択時 |
| **エージェントスキル** | `.github/skills/*/SKILL.md` | 特定の作業フローごと | 関連タスク実行時 |

## 設定詳細

### カスタム指示（リポジトリ全体）

**配置場所:** `.github/copilot-instructions.md`

**使うべき場合:**
- プロジェクトの技術スタック（言語、フレームワーク、ライブラリ）
- コーディング規約（命名規則、フォーマット）
- ディレクトリ構成とファイル配置ルール
- 全体的な設計方針（アーキテクチャパターン）

**例:**
```markdown
# 技術スタック
- Python 3.11、FastAPI、PostgreSQL

# 命名規則
- 関数: snake_case、クラス: PascalCase
```

**詳細:** [カスタム指示の設定](./docs/custom-instructions.md)

### カスタム指示（パス固有・単一ファイル）

**配置場所:** `.github/instructions/*.instructions.md`

**使うべき場合:**
- 特定の言語ファイルに対する規約（例: `**/*.py`, `**/*.ts`）
- 特定のディレクトリ配下のルール（例: `src/models/**/*`）
- 特定ファイルだけに適用する専用ルール

**例:**
```markdown
---
applyTo: "**/*.sh"
excludeAgent: "code-review"
---
# シェルスクリプトのルール
- shebangは必ず記述する
```

**`excludeAgent`プロパティ:**
- `excludeAgent: "code-review"` - コードレビュー時には適用しない（Coding Agentのみ適用）
- `excludeAgent: "coding-agent"` - Coding Agent実行時には適用しない（コードレビューのみ適用）

**詳細:** [カスタム指示の設定](./docs/custom-instructions.md)

### エージェント（AGENTS.md等）

**配置場所:** `AGENTS.md`（ルート）、`CLAUDE.md`、`GEMINI.md`、または任意のディレクトリ内

プロジェクトの概要、技術選択の理由、全体的な開発方針などを整理する場所として活用できます。

**使うべき場合:**
- プロジェクトの概要や背景をAIに理解させたい
- AIモデルごとに異なる指示を与えたい場合（CLAUDE.md, GEMINI.md）
- ディレクトリごとに異なるコンテキストを設定したい場合（AGENTS.md）
- 最寄りのAGENTS.mdが優先されるため、階層的な設定が可能

**配置例:**
```
プロジェクトリポジトリ/
├── AGENTS.md                 ← プロジェクト全体の概要・方針
├── CLAUDE.md                 ← Claude専用の指示
├── GEMINI.md                 ← Gemini専用の指示
├── frontend/
│   └── AGENTS.md             ← フロントエンド固有の概要
└── backend/
    └── AGENTS.md             ← バックエンド固有の概要
```

### カスタムエージェント

**配置場所:** `.github/agents/*.agent.md`

**使うべき場合:**
- テストコードの作成と品質管理
- API設計とバックエンド開発
- ドキュメント作成と保守
- セキュリティレビュー
- パフォーマンス最適化

**例:** test-specialist（テスト専門家）、backend-expert（バックエンド専門家）

**詳細:** [カスタムエージェントの設定](./docs/custom-agents.md)

### エージェントスキル

**配置場所:** `.github/skills/*/SKILL.md`

**使うべき場合:**
- CI/CDパイプラインのデバッグ手順
- データベースマイグレーション手順
- デプロイメント手順
- コードレビュープロセス
- 新機能開発の標準フロー

**例:** GitHub Actionsのワークフロー障害デバッグ、データベーススキーマ変更手順

**詳細:** [エージェントスキルの設定](./docs/agent-skills.md)

## このリポジトリの設定ファイル

このリポジトリ自体にGitHub Copilot Coding Agentの設定例が含まれています：

### エージェント設定

- [AGENTS.md](./AGENTS.md) - プロジェクト全体のエージェント設定（ルート）
- [CLAUDE.md](./CLAUDE.md) - Claude専用の指示
- [GEMINI.md](./GEMINI.md) - Gemini専用の指示
- [frontend/AGENTS.md](./frontend/AGENTS.md) - フロントエンド配下で優先される設定
- [backend/AGENTS.md](./backend/AGENTS.md) - バックエンド配下で優先される設定
- [.github/agents/test-specialist.agent.md](./.github/agents/test-specialist.agent.md) - テスト専門エージェント
- [.github/skills/github-actions-debugging/SKILL.md](./.github/skills/github-actions-debugging/SKILL.md) - CI/CD障害デバッグ
- [.github/skills/webapp-testing/SKILL.md](./.github/skills/webapp-testing/SKILL.md) - Webアプリケーションテスト
- [.github/skills/database-migration/SKILL.md](./.github/skills/database-migration/SKILL.md) - データベースマイグレーション

### カスタム指示

- [.github/copilot-instructions.md](./.github/copilot-instructions.md) - プロジェクト全体の基本設定
- [.github/instructions/shell.instructions.md](./.github/instructions/shell.instructions.md) - シェルスクリプト固有のルール
- [.github/instructions/typescript.instructions.md](./.github/instructions/typescript.instructions.md) - TypeScript固有のルール
- [.github/instructions/validation-file.instructions.md](./.github/instructions/validation-file.instructions.md) - 単一ファイル用の例

## 参考資料

- [GitHub Copilot 公式ドキュメント](https://docs.github.com/ja/copilot)