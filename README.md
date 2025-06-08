# 📦 install-files リポジトリ

このリポジトリは、アプリケーションのビルドや実行に必要な各種ファイル（例：`.tar` 形式のイメージファイル）を管理するためのものです。  
Git LFS を利用して大容量ファイル（例：`maven-image.tar`）をバージョン管理しています。

## 📂 ディレクトリ構成

```bash
├── maven-image.tar # Git LFS 管理対象
├── .gitattributes # LFS 設定ファイル
└── README.md # このファイル
```


## 🛠️ LFS のセットアップ手順（Linux）

```bash
git init
git lfs install
git lfs track "*.tar"
git add .\maven-image.tar
git add .gitattributes
git commit -m "add maven-image.tar"
git remote add origin https://github.com/m-ashina-nss/install-files.git
git push origin master
```

## 🏗️ maven-image.tar の作成方法
```bash
docker pull maven:3.9.5-eclipse-temurin-21
docker save maven:3.9.5-eclipse-temurin-21 -o maven-image.tar
```

## 🔍 Markdown書式上のポイント

- **行末に2つのスペース（␣␣）で改行**を実現
- セクションごとに `---` で区切ると見やすい
- コードブロックは ```` ```bash ```` や ```` ```md ```` を使う
- `#` や `##` で見出しを適切に使うとGitHubで目次が自動生成される
