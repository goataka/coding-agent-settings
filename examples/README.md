# 設定例

このディレクトリには、GitHub Copilot Agentの各種設定ファイルの実例を含んでいます。

## ディレクトリ構成

```
examples/
└── .github/
    ├── copilot-instructions.md          # カスタム指示の例
    ├── agents/                            # カスタムエージェントの例
    │   └── test-specialist.agent.md
    └── skills/                            # エージェントスキルの例
        └── github-actions-debugging/
            └── SKILL.md
```

## 利用方法

これらのファイルをそのままコピーして自分のリポジトリで使用できますが、プロジェクトの特性に合わせてカスタマイズすることを推奨します。

### カスタム指示の利用

```bash
# リポジトリのルートにコピー
cp examples/.github/copilot-instructions.md your-repo/.github/
```

### カスタムエージェントの利用

```bash
# エージェントディレクトリごとコピー
cp -r examples/.github/agents your-repo/.github/
```

### エージェントスキルの利用

```bash
# スキルディレクトリごとコピー
cp -r examples/.github/skills your-repo/.github/
```

## カスタマイズのポイント

- **カスタム指示**: プロジェクトの技術スタック、コーディング規約に合わせて修正
- **カスタムエージェント**: プロジェクトで必要な専門エージェントを追加
- **エージェントスキル**: プロジェクト固有のワークフローや手順を追加
