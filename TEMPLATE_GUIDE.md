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

以下のファイルに含まれるプレースホルダーを実際の値に置き換えてください。

#### pyproject.toml

- `{{project_name}}` → あなたのプロジェクト名（例: `my_awesome_project`）
- `{{ project_description }}` → プロジェクトの説明（例: `A sample Python project`）

#### src/{{project_name}}/__init__.py

- ディレクトリ名 `{{project_name}}` → あなたのプロジェクト名に変更
  ```bash
  mv "src/{{project_name}}" "src/your_project_name"
  ```

#### tests/test_sample.py

- ファイル内の `{{project_name}}` → あなたのプロジェクト名に置換

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
├── pyproject.toml          # プロジェクト設定ファイル
├── src/
│   └── {{project_name}}/   # パッケージのソースコード
│       └── __init__.py
└── tests/
    └── test_sample.py      # テストファイル
```

## 依存関係の追加

```bash
# 通常の依存関係
uv add package-name

# 開発用の依存関係
uv add --dev package-name
```

## よくある質問

### Q. プロジェクト名にハイフンを使いたい

A. pyproject.tomlの`name`フィールドではハイフンを使用できますが、Pythonパッケージ名（ディレクトリ名）にはアンダースコアを使用してください。

例:
- pyproject.toml: `name = "my-awesome-project"`
- ディレクトリ: `src/my_awesome_project/`

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
