FROM node:21.2.0-alpine3.17

# docker-compose.ymlからWORKDIRの値を受け取る
ARG WORKDIR

# コンテナのホームディレクトリを設定する
ENV HOME=/${WORKDIR}

# コマンド実行する作業ディレクトリの設定する
WORKDIR ${HOME}

# Alpineのリポジトリから最新インデックスを取得し、npm自体も最新版に更新する
RUN apk update && npm install -g npm

# Viteで開発サーバーを起動する
CMD ["npm", "run", "dev"]
