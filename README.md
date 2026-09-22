# helloworld

このプロジェクトでは、さまざまなプログラミング言語のソースコードを GitHub からクローンし、ビルド・実行する手順を紹介します。

## 対応言語

- Fortran
- Rust
- Python

## Clone

次のコマンドでリポジトリをクローンします。

```bash
git clone https://github.com/<ユーザー名>/<リポジトリ名>.git
cd <リポジトリ名>
```

## Fortran

```bash
cd fortran
make
./hello
```

出力例:

```text
 Hello, world!
```

## Rust

```bash
cd rust
cargo run
```

出力例:

```text
Hello, world!
```

## Python

プロジェクトのルートディレクトリで実行します。

```bash
python3 python/hello.py
```

出力例:

```text
Hello, World!
```

## VS Code Remote - SSH

VS Code の Remote - SSH 拡張を使うと、SSH 接続したリモートホスト上でコンパイル・実行できます。

### 必要なもの

- [VS Code Remote - SSH 拡張](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)
- SSH 接続できる Linux ホスト
- リモートホスト上の `gfortran`、Rust、Python

### 実行手順

1. VS Code に Remote - SSH 拡張をインストールします。
2. コマンドパレットから **Remote-SSH: Connect to Host...** を実行し、接続先を選択します。
3. 接続先のターミナルでリポジトリをクローンします。

```bash
git clone https://github.com/<ユーザー名>/<リポジトリ名>.git
cd <リポジトリ名>
```

> [!note]
> オフラインのリモートホストからはGitHubのレポジトリを直接clone、pushすることができません。
> この場合は、オンラインのPCで共有フォルダにレポジトリをクローンしたのち、Remote-SSHで当該フォルダを開き編集します。
> 編集が終わったら、オンラインPCに戻り、変更をレポジトリにpushします。
> （commitのようなローカルレポジトリの変更はオフラインのリモートホストからでも可能です。）

4. 接続先のターミナルで、次のコマンドを実行します。

```bash
# Fortran
cd fortran && make && ./hello

# Rust
cd rust && cargo run

# Python（プロジェクトのルートから）
python3 python/hello.py
```

## WSL

WSL（Windows Subsystem for Linux）を使うと、Windows 上で Linux 環境のコンパイラやツールを利用できます。

> [!note]
> WSLのディストロは原理的には何でもいいのですが、デファクトスタンダートとなっている `Ubuntu` を選んでおくのが無難です。

### 必要なもの

- Windows の WSL
- WSL 上の Linux ディストリビューション
- [VS Code WSL 拡張](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl)
- WSL 上の `gfortran`、Rust、Python

### 実行手順

1. WSL を起動し、リポジトリをクローンします。
2. VS Code で **WSL: Connect to WSL** を実行して WSL に接続します。
3. WSL のターミナルで、次のコマンドを実行します。

```bash
git clone https://github.com/<ユーザー名>/<リポジトリ名>.git
cd <リポジトリ名>

# Fortran
cd fortran && make && ./hello

# Rust
cd ../rust && cargo run

# Python（プロジェクトのルートから）
cd ..
python3 python/hello.py
```

## Dev Container

### 必要なもの

- [VS Code Dev Containers 拡張](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
- Docker

### 起動手順

1. VS Code でこのプロジェクトを開きます。
2. コマンドパレットから **Dev Containers: Reopen in Container** を実行します。
3. コンテナの作成が完了したら、ターミナルで各言語のコマンドを実行します。

### コンテナ内での実行

```bash
# Fortran
cd fortran && make && ./hello

# Rust
cd rust && cargo run

# Python（プロジェクトのルートから）
python3 python/hello.py
```

## GitHub Codespaces

GitHub Codespaces を使うと、ローカル環境を準備せずに GitHub 上の開発環境をクラウドで起動できます。ブラウザまたは VS Code から利用できます。

### 起動手順

1. GitHub でこのリポジトリを開きます。
2. **Code** ボタンを選択し、**Codespaces** タブを開きます。
3. **Create codespace on main** を選択します。
4. Codespace の作成が完了したら、ターミナルで各言語のコマンドを実行します。

### Codespaces 内での実行

```bash
# Fortran
cd fortran && make && ./hello

# Rust
cd rust && cargo run

# Python（プロジェクトのルートから）
python3 python/hello.py
```

## GitHub Actions

GitHub Actions を使って、リポジトリへの変更時に各言語のビルドと実行を自動確認できます。

### 実行されるタイミング

次の操作を行うと、Fortran、Rust、Python のワークフローが実行されます。

- `main` ブランチなどへの `push`
- Pull Request の作成・更新

### 実行結果の確認

1. GitHub でリポジトリを開きます。
2. **Actions** タブを選択します。
3. 次のワークフローから確認したいものを選択します。
	- **Fortran Hello World**: Fortran のインストール、ビルド、実行
	- **Rust Hello World**: Rust のビルド、実行
	- **Python Hello World**: Python プログラムの実行
4. 実行履歴から対象のコミットまたは Pull Request を選択し、各ステップのログを確認します。

### ビルド成果物

Fortran と Rust のワークフローが正常に完了すると、実行ファイルを成果物としてダウンロードできます。

- Fortran: `fortran-hello`
- Rust: `rust-hello`

ワークフローの実行結果画面にある **Artifacts** から成果物をダウンロードします。Rust の成果物は 7 日間保存されます。

## ディレクトリ構成

```text
.
├── README.md
├── .gitignore
├── .devcontainer
│   ├── devcontainer.json
│   └── Dockerfile
├── .github
│   └── workflows
│       ├── fortran.yaml
│       ├── python.yaml
│       └── rust.yaml
├── fortran
│   ├── Makefile
│   └── hello.f90
├── python
│   └── hello.py
└── rust
	├── Cargo.toml
	└── src
		└── main.rs
```
