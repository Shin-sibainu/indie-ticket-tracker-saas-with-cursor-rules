# Next.js ベストプラクティス

## 1. アプリケーション構造とルーティング

### 重要度: 高

- App Router を使用し、ページとコンポーネントを適切に分離
- 以下のディレクトリ構造を遵守:
  ```
  src/
  ├── app/             # ルーティング
  ├── components/      # 共通コンポーネント
  ├── lib/            # ユーティリティ関数
  ├── hooks/          # カスタムフック
  ├── types/          # 型定義
  └── styles/         # グローバルスタイル
  ```

## 2. パフォーマンス最適化

### 重要度: 高

- `next/image`を使用した画像の最適化
- `next/font`によるフォントの最適化
- 適切なレンダリング戦略の選択:
  - 静的ページ: Static Generation
  - 動的データ: Server-side Rendering
  - クライアントの状態: Client-side Rendering

## 3. データフェッチング

### 重要度: 高

- Server Components でのデータフェッチを優先
- キャッシュ戦略の適切な使用:
  ```typescript
  // 例: キャッシュの使用
  async function getData() {
    const res = await fetch("...", { next: { revalidate: 3600 } });
    return res.json();
  }
  ```

## 4. TypeScript の使用

### 重要度: 高

- 厳格な型チェックの有効化
- コンポーネントの Props 型定義
- API レスポンスの型定義

```typescript
// 例: 型定義
interface Props {
  title: string;
  children: React.ReactNode;
}

export default function Component({ title, children }: Props) {
  // ...
}
```

## 5. スタイリング規約

### 重要度: 中

- Tailwind CSS を優先的に使用
- CSS Modules は必要な場合のみ使用
- グローバルスタイルは最小限に抑える

## 6. エラーハンドリング

### 重要度: 高

- エラーバウンダリの実装
- カスタムエラーページの作成（404, 500）
- ユーザーフレンドリーなエラーメッセージ

## 7. セキュリティ

### 重要度: 高

- 環境変数の適切な管理
- CSRF トークンの実装
- Content Security Policy の設定
- API ルートでの入力バリデーション

## 8. デプロイメント

### 重要度: 高

- 本番環境へのデプロイ前チェックリスト
- 環境変数の確認
- ビルドの最適化
- パフォーマンスメトリクスの監視

## 10. コード品質

### 重要度: 中

- ESLint と Prettier の設定
- コードレビューのガイドライン
- コミットメッセージの規約
