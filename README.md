# 📦 install-files リポジトリ

このリポジトリは、アプリケーションのビルドや実行に必要な各種ファイル（例：`.tar` 形式のイメージファイル）を管理するためのものです。  
Git LFS を利用して大容量ファイル（例：`maven-image.tar`）をバージョン管理しています。

## 📂 ディレクトリ構成

```bash
├── maven-image.tar # Git LFS 管理対象  GITサーバー用
├── .gitattributes # LFS 設定ファイル
└── README.md # このファイル
```


## 🛠️ LFS のセットアップ&tarのpush手順

```bash
git init
git lfs install
git lfs track "*.tar"
git lfs track "*.tgz"
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

# オフライン環境に持ち込み、以下を実行する
docker load -i maven-3.9.5-java21.tar

# GitLab CI や IntelliJ が Maven を使うには、依存JARを事前に取得してローカルリポジトリ化する必要があります
#オンライン側で実行
mvn dependency:go-offline
#オフライン側に持ち込む
.m2/repository フォルダを丸ごとコピー
GitLab CIなら .gitlab-ci.yml でキャッシュ指定済み
IntelliJにもこのフォルダを指定すればOK

```

## 🔍 Markdown書式上のポイント

- **行末に2つのスペース（␣␣）で改行**を実現
- セクションごとに `---` で区切ると見やすい
- コードブロックは ```` ```bash ```` や ```` ```md ```` を使う
- `#` や `##` で見出しを適切に使うとGitHubで目次が自動生成される
