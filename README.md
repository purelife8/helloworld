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

## ディレクトリ構成

```text
.
├── README.md
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
