# CLAUDE.md

このファイルは、Claude Code (claude.ai/code) がこのリポジトリで作業する際のガイダンスを提供します。

## 言語設定

- 入力言語に関わらず、出力は日本語で行ってください。

## コミットメッセージガイドライン

- コミットメッセージには慣習的なコミット形式を使用してプレフィックスを追加してください：
  - `feat:` 新機能
  - `fix:` バグ修正
  - `docs:` ドキュメント変更
  - `style:` フォーマット変更（コードロジックの変更なし）
  - `refactor:` コードの再構築
  - `test:` テストの追加/修正
  - `chore:` メンテナンスタスク
  - `ci:` CI/CD関連の変更

## プロジェクト概要

これはBunをパッケージマネージャーとして使用するTurborepoモノレポです。プロジェクトは以下で構成されています：

- 2つのNext.jsアプリケーション（`web`と`docs`）
- 共有UIコンポーネントライブラリ（`@repo/ui`）
- 共有TypeScript設定（`@repo/typescript-config`）

## よく使用するコマンド

すべてのコマンドはルートディレクトリから実行してください：

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
```

### コード品質

```bash
# すべてのパッケージで型チェックを実行
bun check-types

# コードフォーマット（TS/JSにはBiome、その他のファイルにはPrettier）
bun format

# リントを実行
bun lint

# 完全チェック（フォーマット + リント）
bun check

# ルートディレクトリからフォーマット（全ファイルに影響）
bun format:root
```

### Gitフック

プロジェクトはLefthookを使用してpre-commitフックを自動実行します：

- Biomeフォーマットとリント
- 非JS/TSファイルのPrettierフォーマット

## アーキテクチャ

### モノレポ構造

- `/apps/web` - メインWebアプリケーション（Next.js、ポート3000）
- `/apps/docs` - ドキュメンテーションサイト（Next.js、ポート3001）
- `/packages/ui` - 共有Reactコンポーネントライブラリ
- `/packages/typescript-config` - 共有TypeScript設定

### 主要技術

- **ビルドシステム**: 依存関係を考慮したタスク実行のTurborepo
- **パッケージマネージャー**: Bun（preinstallスクリプトで強制）
- **フレームワーク**: App RouterとTurbopackを使用したNext.js 15
- **言語**: 厳格な型チェックを備えたTypeScript
- **コード品質**: JS/TSのリント/フォーマットにBiome、その他のファイルにPrettier
- **React**: バージョン19.1.0

### CI/CDワークフロー

- `code-quality.yml` - プッシュとPRでBiomeチェックを実行
- `claude.yml`と`claude-code-review.yml` - コードレビュー用のClaude AI統合
- `auto-assign.yml` - PRに自動的にレビュアーを割り当て
- `approve-me.yml` - 自動承認ワークフロー

### 開発メモ

- 各パッケージには独自の`biome.jsonc`設定があります
- ルートの`biome.jsonc`はタブインデントとダブルクォートを使用
- TypeScript `noEmit`は出力ファイルを生成せずに型チェックを実行
- すべてのパッケージはESモジュールを使用（`"type": "module"`）
