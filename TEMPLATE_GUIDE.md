# テンプレート使用ガイド

このテンプレートは、uvを使用したPythonプロジェクトの雛形です。

## ライセンスについて

このテンプレート自体は **CC0 1.0 Universal** でライセンスされています。これは、このテンプレートを自由に使用、改変、配布できることを意味します。

- `TEMPLATE_LICENSE` ファイルには、テンプレート自体のライセンス（CC0）の全文が記載されています
- テンプレートから作成したプロジェクトには、お好きなライセンスを自由に設定できます
- `TEMPLATE_LICENSE` と `TEMPLATE_GUIDE.md` は、確認後に削除していただいて構いません

## テンプレートの使い方

### 1. リポジトリの作成

```bash
gh repo create your-project-name --template atu4403/uv-simple-template --clone
cd your-project-name
```

### 2. プレースホルダーの置換

**重要: `uv sync` を実行する前に、必ずプレースホルダーを置換してください。**

プレースホルダーのまま `uv sync` を実行すると、バリデーションエラーが発生します。これは意図的な動作で、確実に置換を行うための仕組みです。

#### 置換するプレースホルダー

以下のプレースホルダーをあなたのプロジェクトの値に置き換えます：

- `{{ project_name }}` → あなたのプロジェクト名（例: `my_awesome_project`）
- `{{ project_description }}` → プロジェクトの説明（例: `A sample Python project`）

#### VSCodeでの一括置き換え方法（推奨）

1. VSCodeでプロジェクトを開く
2. `Cmd+Shift+F` (macOS) または `Ctrl+Shift+F` (Windows/Linux) で検索を開く
3. 検索欄の左の「>」をクリックして置換モードに切り替え
4. 検索: `{{ project_name }}`、置換: `your_project_name`
5. 「すべて置換」をクリック
6. 同様に `{{ project_description }}` も置換

#### ディレクトリ名の変更

```bash
# プロジェクト名をmy_projectとした場合の例
mv "src/{{ project_name }}" "src/my_project"
```

**注意:** pyproject.tomlの`name`フィールドではハイフン（`my-project`）が使えますが、Pythonパッケージ名（ディレクトリ名）にはアンダースコア（`my_project`）を使用してください。

### 3. ライセンスの設定

あなたのプロジェクトのライセンスを設定します。

#### オプション1: gh コマンドでライセンスを追加

```bash
# 例: MITライセンスを追加
gh repo edit --add-license mit

# 利用可能なライセンス一覧を確認
gh repo edit --help
```

#### オプション2: 手動でLICENSEファイルを作成

お好きなライセンスの全文を `LICENSE` ファイルとして作成してください。

#### テンプレートファイルの削除（任意）

```bash
# テンプレート関連ファイルが不要な場合は削除
rm TEMPLATE_LICENSE TEMPLATE_GUIDE.md
```

### 4. 初期セットアップ

```bash
# 仮想環境の作成と依存関係のインストール
uv sync

# テストの実行（確認用）
uv run pytest

# リンターの実行（確認用）
uv run ruff check .
```

## プロジェクト構成

```
.
├── pyproject.toml            # プロジェクト設定ファイル
├── src/
│   └── {{ project_name }}/   # パッケージのソースコード（要置換）
│       └── __init__.py
└── tests/
    └── test_sample.py        # テストファイル
```

## 依存関係の追加

```bash
# 通常の依存関係
uv add package-name

# 開発用の依存関係
uv add --dev package-name
```

## よくある質問

### Q. uv sync でエラーが出る

A. プレースホルダー（`{{ project_name }}` など）を置換せずに `uv sync` を実行するとエラーになります。これは意図的な動作です。「2. プレースホルダーの置換」の手順に従って、必ず置換してから `uv sync` を実行してください。

### Q. Python バージョンを変更したい

A. pyproject.tomlの`requires-python`フィールドを編集してください。

```toml
requires-python = ">=3.11"  # Python 3.11以上
```

### Q. TEMPLATE_LICENSE と TEMPLATE_GUIDE.md は削除すべき？

A. 任意です。これらはテンプレートの使い方を説明するためのファイルなので：
- 確認後は削除して問題ありません
- リポジトリに残しておいても害はありません（ただし、あなたのプロジェクトには関係のないファイルです）
- `gh repo edit --add-license` を使う場合、LICENSEファイルは自動で作成されるため、TEMPLATE_LICENSEは不要になります

### Q. pyproject.toml の license フィールドは？

A. pyproject.toml にライセンス情報を追加することもできます：

```toml
[project]
name = "your-project"
version = "0.1.0"
license = {text = "MIT"}  # または {file = "LICENSE"}
```

詳しくは [PEP 621](https://peps.python.org/pep-0621/#license) を参照してください。

## 参考リンク

- [uv公式ドキュメント](https://docs.astral.sh/uv/)
- [PEP 621 - Storing project metadata in pyproject.toml](https://peps.python.org/pep-0621/)
