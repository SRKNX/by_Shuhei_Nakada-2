FROM nginx:1.25.3-alpine

# Nginxに関わる設定ファイルを全削除
RUN rm -f /etc/nginx/conf.d/*

# 独自の設定ファイルを機能する場所に配置する
COPY nginx.conf /etc/nginx/conf.d/custum.conf
