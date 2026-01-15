# 技術スタック
- Node.js 20.x
- TypeScript 5.x
- React 18
- Next.js 14

# 命名規則
- 関数・変数: camelCase
- コンポーネント・型・インターフェース: PascalCase
- ファイル名: kebab-case
- 定数: UPPER_SNAKE_CASE

# コーディング規約
- TypeScriptの型推論を活用し、明示的な型定義は必要な場合のみ
- `any`型の使用は避け、`unknown`を検討する
- 関数は単一責任の原則に従う
- 純粋関数を優先し、副作用は最小限に

# ディレクトリ構成
- `src/components/`: 再利用可能なReactコンポーネント
- `src/pages/`: Next.jsのページコンポーネント
- `src/hooks/`: カスタムReact Hooks
- `src/lib/`: ビジネスロジックとユーティリティ
- `src/types/`: 型定義ファイル

# エラーハンドリング
- エラーは適切な型で定義する
- APIエラーは一貫したエラーレスポンス形式を返す
- フロントエンドでは Error Boundary を活用

# テスト方針
- 単体テスト: Vitest
- E2Eテスト: Playwright
- テストカバレッジ: 80%以上を目標
