# Bunを使用したTurboスターター

TurborepoとBunを使用したモダンなモノレポスターターテンプレート。共有コンポーネントと設定を持つNext.jsアプリケーションを特徴としています。

## 言語

- [English README](./README.md)

## 特徴

- **モノレポアーキテクチャ**: 効率的なタスクオーケストレーションのためのTurborepo
- **Bunパッケージマネージャー**: 高速でモダンなJavaScriptランタイムとパッケージマネージャー
- **Next.js 15**: App RouterとTurbopackを備えた最新バージョン
- **共有コンポーネント**: 再利用可能なUIコンポーネントライブラリ
- **TypeScript**: すべてのパッケージで完全な型安全性
- **コード品質**: 高速なリントとフォーマットのためのBiome、その他のファイルにはPrettier
- **Gitフック**: Lefthookによる自動コード品質チェック
- **CI/CD**: 品質チェックとレビューのためのGitHub Actionsワークフロー

## 内容

このモノレポには以下のパッケージとアプリが含まれています：

### アプリ

- `web`: メインWebアプリケーション（Next.js） - http://localhost:3000
- `docs`: ドキュメンテーションサイト（Next.js） - http://localhost:3001

### パッケージ

- `@repo/ui`: 共有Reactコンポーネントライブラリ
- `@repo/typescript-config`: 共有TypeScript設定

## 必要条件

- [Bun](https://bun.sh/) >= 1.2.18
- Node.js >= 18

## はじめに

1. リポジトリをクローン：

```bash
git clone <repository-url>
cd my-turbo-stater-use-bun
```

2. 依存関係をインストール：

```bash
bun install
```

3. 開発を開始：

```bash
bun dev
```

## よく使用するコマンド

ルートディレクトリから以下のコマンドを実行します：

### 開発

```bash
# すべてのアプリを開発モードで起動
bun dev

# 特定のアプリを起動
bun dev --filter=web
bun dev --filter=docs
```

### ビルド

```bash
# すべてのアプリとパッケージをビルド
bun run build

# 特定のアプリをビルド
bun run build --filter=web
bun run build --filter=docs
```

### コード品質

```bash
# 型チェックを実行
bun check-types

# すべてのコードをフォーマット
bun format

# リントを実行
bun lint

# 完全チェック（フォーマット + リント）
bun check

# ルートディレクトリからフォーマット（全ファイルに影響）
bun format:root
```

## プロジェクト構造

```
my-turbo-stater-use-bun/
├── apps/
│   ├── web/         # メインWebアプリケーション
│   └── docs/        # ドキュメンテーションサイト
├── packages/
│   ├── ui/          # 共有コンポーネントライブラリ
│   └── typescript-config/  # 共有TypeScript設定
├── biome.jsonc      # Biome設定
├── lefthook.yml     # Gitフック設定
├── turbo.json       # Turborepo設定
└── package.json     # ルートパッケージ設定
```

## 設定

### Biome

このプロジェクトはJavaScript/TypeScriptのリントとフォーマットにBiomeを使用しています。設定は`biome.jsonc`にあります。

### Prettier

PrettierはJS/TS以外のファイル（JSON、YAML、Markdownなど）のフォーマットに使用されます。

### TypeScript

各パッケージには`@repo/typescript-config`の共有設定を拡張した独自の`tsconfig.json`があります。

### Gitフック

Lefthookでpre-commitフックが設定されており、コード品質を保証します：

- JS/TSファイルのBiomeフォーマットとリント
- その他のファイルのPrettierフォーマット

## 貢献

1. フィーチャーブランチを作成
2. 変更を加える
3. すべてのチェックが通ることを確認：`bun check`
4. 慣習的なコミットメッセージでコミット
5. プルリクエストを作成

### コミットメッセージ形式

```
type: subject

body (optional)
```

タイプ：

- `feat`: 新機能
- `fix`: バグ修正
- `docs`: ドキュメント変更
- `style`: コードスタイル変更（フォーマットなど）
- `refactor`: コードリファクタリング
- `test`: テスト変更
- `chore`: メンテナンスタスク
- `ci`: CI/CD変更

## ライセンス

このプロジェクトはオープンソースであり、[MITライセンス](LICENSE)の下で利用可能です。

## 謝辞

以下を使用して構築：

- [Turborepo](https://turbo.build/repo)
- [Bun](https://bun.sh/)
- [Next.js](https://nextjs.org/)
- [Biome](https://biomejs.dev/)
- [TypeScript](https://www.typescriptlang.org/)
