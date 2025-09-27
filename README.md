# 📮 SearchForPostalCode

[![Deploy to GitHub Pages](https://github.com/KajiyaManzou/SearchForPostalCode/actions/workflows/deploy-to-gh-pages.yml/badge.svg)](https://github.com/KajiyaManzou/SearchForPostalCode/actions/workflows/deploy-to-gh-pages.yml)
[![.NET](https://img.shields.io/badge/.NET-8.0-purple)](https://dotnet.microsoft.com/download/dotnet/8.0)
[![Blazor WebAssembly](https://img.shields.io/badge/Blazor-WebAssembly-blue)](https://blazor.net/)
[![MudBlazor](https://img.shields.io/badge/MudBlazor-UI%20Library-orange)](https://mudblazor.com/)

日本の郵便番号から住所を検索するWebアプリケーションです。.NET Blazor WebAssemblyとMudBlazorを使用して開発されています。

## 🌐 ライブデモ

**🔗 [https://kajiyamanzou.github.io/SearchForPostalCode/](https://kajiyamanzou.github.io/SearchForPostalCode/)**

## ✨ 機能

- 📍 **郵便番号検索**: 7桁の郵便番号を入力して住所を検索
- 🎨 **モダンUI**: MudBlazorを使用したレスポンシブデザイン
- ⚡ **高速動作**: Blazor WebAssemblyによるクライアントサイド実行
- 📱 **レスポンシブ**: モバイルデバイス対応
- 🔄 **リアルタイム検索**: 即座に結果を表示

## 🛠️ 技術スタック

- **フレームワーク**: .NET 8.0
- **UI技術**: Blazor WebAssembly
- **UIライブラリ**: MudBlazor
- **API**: zipcloud.ibsnet.co.jp（郵便番号検索API）
- **デプロイ**: GitHub Pages
- **CI/CD**: GitHub Actions

## 🚀 ローカル開発

### 前提条件

- [.NET 8.0 SDK](https://dotnet.microsoft.com/download/dotnet/8.0) 以上
- 任意のIDEまたはエディタ（Visual Studio、Visual Studio Code、JetBrains Riderなど）

### セットアップ

1. **リポジトリをクローン**
   ```bash
   git clone https://github.com/KajiyaManzou/SearchForPostalCode.git
   cd SearchForPostalCode
   ```

2. **依存関係を復元**
   ```bash
   cd SearchForPostalCode
   dotnet restore
   ```

3. **アプリケーションを実行**
   ```bash
   cd src/SearchForPostalCode.App
   dotnet run
   ```

4. **ブラウザでアクセス**
   ```
   https://localhost:5001 または http://localhost:5000
   ```

### ビルド

```bash
# Release ビルド
dotnet build --configuration Release

# 公開用ビルド
dotnet publish src/SearchForPostalCode.App/SearchForPostalCode.App.csproj --configuration Release --output ./publish
```

## 🧪 テスト

```bash
# 単体テストを実行
dotnet test tests/SearchForPostalCode.Tests.Unit/

# コンポーネントテストを実行
dotnet test tests/SearchForPostalCode.Tests.Components/

# 全テストを実行
dotnet test
```

## 📁 プロジェクト構造

```
SearchForPostalCode/
├── src/
│   └── SearchForPostalCode.App/          # メインアプリケーション
│       ├── Pages/                        # Blazorページ
│       │   └── SearchPostalCode.razor    # 郵便番号検索ページ
│       ├── Shared/                       # 共有クラス
│       │   └── Address.cs               # APIレスポンスモデル
│       ├── Layout/                       # レイアウトコンポーネント
│       └── Program.cs                   # エントリーポイント
├── tests/
│   ├── SearchForPostalCode.Tests.Unit/   # 単体テスト
│   └── SearchForPostalCode.Tests.Components/ # コンポーネントテスト
├── .github/
│   └── workflows/
│       └── deploy-to-gh-pages.yml       # GitHub Actions ワークフロー
└── SearchForPostalCode.sln              # ソリューションファイル
```

## 🔧 設定

### API設定

このアプリケーションは[zipcloud.ibsnet.co.jp](https://zipcloud.ibsnet.co.jp/)の無料APIを使用しています。APIキーは不要です。

### GitHub Pages デプロイ

このリポジトリには自動デプロイ用のGitHub Actionsワークフローが含まれています：

1. `main`ブランチにプッシュすると自動的にビルド・デプロイが実行されます
2. GitHub Pages設定でSourceを「GitHub Actions」に設定してください

## 📄 ライセンス

このプロジェクトはMITライセンスの下で公開されています。詳細は[LICENSE](LICENSE)ファイルを参照してください。

## 🤝 貢献

貢献を歓迎します！以下の手順で参加できます：

1. このリポジトリをフォーク
2. 機能ブランチを作成 (`git checkout -b feature/amazing-feature`)
3. 変更をコミット (`git commit -m 'Add some amazing feature'`)
4. ブランチにプッシュ (`git push origin feature/amazing-feature`)
5. プルリクエストを作成

## 📞 サポート

問題や質問がある場合は、[Issues](https://github.com/KajiyaManzou/SearchForPostalCode/issues)でお知らせください。

## 🙏 謝辞

- [zipcloud.ibsnet.co.jp](https://zipcloud.ibsnet.co.jp/) - 郵便番号検索APIの提供
- [MudBlazor](https://mudblazor.com/) - 美しいUIコンポーネントライブラリ
- [Microsoft Blazor](https://blazor.net/) - 強力なWebフレームワーク

---

⭐ このプロジェクトが役に立った場合は、スターを付けてください！
