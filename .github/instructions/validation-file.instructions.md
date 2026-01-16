---
applyTo: "src/utils/validation.ts"
---

# validation.ts ファイル固有のルール

このファイルはバリデーション関数を集約するファイルです。

## このファイルでのルール

- すべてのバリデーション関数は戻り値として`{ valid: boolean; error?: string }`を返す
- 正規表現は定数として定義し、再利用する
- エラーメッセージは日本語で記述する
- 各バリデーション関数には必ずJSDocコメントを付ける

## 例

```typescript
/**
 * メールアドレスの形式をバリデーションする
 */
export function validateEmail(email: string): { valid: boolean; error?: string } {
  // 実装
}
```
