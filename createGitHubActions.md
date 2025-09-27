# GitHub Actions ワークフロー作成レポート

## 概要
.NET Blazor WebAssemblyアプリ「SearchForPostalCode」をGitHub Pagesにデプロイするためのgithub actionを作成しました。

## 作成したファイル
- `.github/workflows/deploy-to-gh-pages.yml`

## 処理内容

### 1. プロジェクト構造の調査
- .NET ソリューションファイル: `SearchForPostalCode/SearchForPostalCode.sln`
- メインプロジェクト: `SearchForPostalCode/src/SearchForPostalCode.App/SearchForPostalCode.App.csproj`
- ターゲットフレームワーク: .NET 8.0
- プロジェクトタイプ: Blazor WebAssembly

### 2. GitHub Actionsワークフローの作成

#### トリガー条件
- mainブランチへのpush
- mainブランチへのpull request

#### 権限設定
```yaml
permissions:
  contents: read
  pages: write
  id-token: write
```

#### ビルドジョブ（build）
1. **チェックアウト**: `actions/checkout@v4` を使用
2. **.NET セットアップ**: `actions/setup-dotnet@v4` で .NET 8.0.x をインストール
3. **依存関係の復元**: `dotnet restore SearchForPostalCode/SearchForPostalCode.sln`
4. **ビルド**: Release構成でプロジェクトをビルド
5. **パブリッシュ**: WebAssemblyアプリを `./publish` フォルダにパブリッシュ
6. **ベースパス修正**: GitHub Pages用にindex.htmlのbase hrefを `/SearchForPostalCode/` に変更
7. **.nojekyllファイル追加**: Jekyll処理を無効化
8. **Pages設定**: `actions/configure-pages@v5` でPages環境を設定
9. **アーティファクトアップロード**: `actions/upload-pages-artifact@v3` でビルド成果物をアップロード

#### デプロイジョブ（deploy）
- mainブランチへのpushの場合のみ実行
- `actions/deploy-pages@v4` を使用してGitHub Pagesにデプロイ
- デプロイ後のURLを出力

### 3. 重要な設定項目

#### ベースパス設定
```bash
sed -i 's/<base href="\/" \/>/<base href="\/SearchForPostalCode\/" \/>/g' ./publish/wwwroot/index.html
```
- GitHub Pagesのサブディレクトリ（リポジトリ名）に対応するため、ベースパスを修正

#### Jekyll無効化
```bash
touch ./publish/wwwroot/.nojekyll
```
- GitHub PagesのデフォルトのJekyll処理を無効化し、静的ファイルとして配信

## 使用方法

### 初回設定
1. GitHubリポジトリのSettings → Pagesにアクセス
2. SourceをGitHub Actionsに設定

### デプロイ実行
1. このワークフローファイルをmainブランチにpush
2. GitHub Actionsが自動実行され、約5-10分でデプロイ完了
3. `https://kajiyamanzou.github.io/SearchForPostalCode/` でアクセス可能

## ワークフローの特徴
- **自動化**: mainブランチへのpushで自動デプロイ
- **セキュリティ**: 最小限の権限設定
- **効率性**: ビルドとデプロイを分離した2段階構成
- **互換性**: .NET 8.0 Blazor WebAssemblyに最適化
- **GitHub Pages対応**: ベースパス自動設定とJekyll無効化

## 注意事項
- mainブランチ以外からのpull requestではビルドのみ実行（デプロイは実行されない）
- デプロイには適切な権限設定が必要
- 初回デプロイ後、GitHub Pages設定の確認が推奨