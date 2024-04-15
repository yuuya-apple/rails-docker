# 当アプリケーションの実行手順

## 前提条件

ローカル環境において docker 及び git がインストールされているものとする。<br>
CLIでの実行とする。
## 実行手順

1. **リポジトリのクローン**<br>
   任意のディレクトリで以下を実行。
   ```
   git clone https://github.com/yuuya-apple/rails-docker.git
   ```
1. **dockerのbuild**<br>
   cloneしてきたディレクトリに移動し($ cd rails-docker)、以下を実行。
   ```
   docker-compose up -d
   ```
   ビルドと同時にコンテナが起動する。<br>
   起動確認は以下。<br>
   NAMEが`rails-docker-db-1-1`と`rails-docker-web-1`のコンテナのSTATUSがUPになっていれば良い。
   ```
   docker-compose ps -a
   ```

1. **コンテナへ入る**<br>
   以下を実行しwebサーバ側のコンテナへ入る。
   ```
   docker-compose exec web bash
   ```

1. **データベースの作成**<br>
   以下を実行してデータベースを作成。
   ```
   rails db:create
   ```

1. **マグレーションを実行**<br>
   以下を実行してマイグレーションを実行。
   ```
   rails db:migrate
   ```

1. **アプリケーションにアクセス**<br>
   ローカルにてブラウザを立ち上げ、[localhost:3000](localhost:3000)にアクセス。
   