# aws-linux-webserver-project
EC2・Linux・Nginx・Node.js・Dockerを利用したインフラ構築プロジェクト


# AWS Linux Web Server 構築プロジェクト

## プロジェクト概要

AWS EC2（Ubuntu）上にLinuxサーバーを構築し、NginxとNode.jsを利用したWebアプリケーションをインターネットへ公開したプロジェクトです。

EC2インスタンスの作成からSSHによるリモート接続、Linuxサーバーの設定、AWS Security Groupの構成、Nginx Webサーバーの構築、Node.jsアプリケーションの実行、Dockerによるコンテナ化まで一連の構築を行いました。

また、構築中に発生したネットワークおよびサーバーの問題について、Linuxコマンドやログを利用して原因を調査し、解決まで実施しました。

---

# プロジェクト目的

- AWS EC2を利用したLinuxサーバー構築
- SSHによるリモートサーバー管理
- Nginx Webサーバーの構築・公開
- Node.jsアプリケーションの実行
- Dockerを利用したアプリケーションのコンテナ化
- Docker Volumeによるデータ永続化の実装
- Linux環境での障害調査およびトラブルシューティングの経験

---

# 使用技術

| 分類 | 技術 |
|------|------|
| Cloud | AWS EC2 |
| OS | Ubuntu Linux |
| Web Server | Nginx |
| Application | Node.js |
| Container | Docker / Docker Volume |
| Remote Access | SSH |
| Version Control | Git / GitHub |

---

# システム構成

```text
                Internet
                    │
                    ▼
        AWS Security Group
          (HTTP / SSH)
                    │
                    ▼
            EC2 (Ubuntu)
                    │
        ┌───────────┴───────────┐
        │                       │
      Nginx                 Node.js
        │                       │
        └───────────┬───────────┘
                    │
            Docker Container
                    │
             Docker Volume
```

※構成図は後日追加予定です。

---

# 主な構築内容

- AWS EC2（Ubuntu）インスタンス作成
- SSHによるリモート接続
- Linux環境の構築および基本操作
- Nginxのインストール・公開
- Node.js HTTPサーバーの構築
- Docker環境の構築
- Dockerfileによる独自イメージ作成
- Docker Volumeによるデータ永続化の確認

---

# トラブルシューティング

## ① ブラウザからNginxへアクセスできない

### 原因

AWS Security GroupでHTTP（TCP 80）が許可されていませんでした。

### 対応

Inbound RuleへHTTP（TCP 80）を追加しました。

### 結果

EC2のPublic IPアドレスから正常にWebページへアクセスできることを確認しました。

---

## ② Dockerコンテナ削除後にデータが消える

### 原因

コンテナ内部のデータはコンテナのライフサイクルに依存していました。

### 対応

Docker Volumeを作成し、`/data`ディレクトリへマウントしました。

### 結果

コンテナを再作成した後もデータが保持されることを確認しました。

---

# このプロジェクトで学んだこと

- AWS EC2を利用したLinuxサーバー構築
- Security Groupとポート制御の仕組み
- Linuxサービスおよびプロセス管理
- Docker ImageとContainerの違い
- Docker Volumeによるデータ永続化
- 障害発生時の原因調査およびトラブルシューティング

---

# 今後の改善予定

- Nginx Reverse Proxy構成
- Docker Compose導入
- HTTPS（Let's Encrypt）対応
- AWS RDSとの連携
- CloudWatchによる監視環境構築

---

# ディレクトリ構成

```text
aws-linux-webserver-project
│
├── README.md
├── docs
│   ├── 01-EC2.md
│   ├── 02-Linux.md
│   ├── 03-Nginx.md
│   ├── 04-Nodejs.md
│   ├── 05-Docker.md
│   └── 06-Docker-Volume.md
│
├── images
│   ├── architecture.png
│   ├── nginx.png
│   ├── node.png
│   ├── docker.png
│   └── volume.png
│
└── docker
    ├── Dockerfile
    └── server.js
```

---

# 詳細ドキュメント

- [01. EC2構築](docs/01-EC2.md)
- [02. Linux基本操作](docs/02-Linux.md)
- [03. Nginx構築](docs/03-Nginx.md)
- [04. Node.js](docs/04-Nodejs.md)
- [05. Docker](docs/05-Docker.md)
- [06. Docker Volume](docs/06-Docker-Volume.md)
