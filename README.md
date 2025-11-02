# uv-simple-template

🧩 A simple Python project template for [uv](https://docs.astral.sh/uv/)

## 概要

このテンプレートは、uvを使用したPythonプロジェクトを素早く始めるための最小限の構成を提供します。

## 特徴

- ✨ **uv対応**: 最新のuv仕様に準拠したpyproject.toml
- 📦 **src layout**: モダンなsrcレイアウトを採用
- 🧪 **テスト環境**: pytestとruffが開発依存関係として設定済み
- 🚀 **すぐに使える**: プレースホルダーを置き換えるだけで開始可能

## 使い方

### クイックスタート

```bash
gh repo create your-project-name --template atu4403/uv-simple-template --clone
cd your-project-name
```

### 詳しい使い方

**[📖 TEMPLATE_GUIDE.md](./TEMPLATE_GUIDE.md) を参照してください**

ガイドには以下の情報が含まれています：
- プレースホルダーの置換方法
- ライセンスの設定方法
- 初期セットアップ手順
- よくある質問

## プロジェクト構成

```
.
├── pyproject.toml          # uv対応のプロジェクト設定
├── src/
│   └── {{project_name}}/   # パッケージソースコード
│       └── __init__.py
└── tests/
    └── test_sample.py      # サンプルテスト
```

## ライセンス

このテンプレート自体は **CC0 1.0 Universal** でライセンスされています。
詳細は [TEMPLATE_LICENSE](./TEMPLATE_LICENSE) を参照してください。

テンプレートから作成したプロジェクトには、お好きなライセンスを自由に設定できます。
