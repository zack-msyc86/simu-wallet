FROM golang:1.20

# uidが1000のユーザーを作成し、そのユーザーを使用します
RUN useradd -u 1000 -m user && \
    chown -R user:user /go

USER user

# ワーキングディレクトリの作成と設定
WORKDIR /app

# Goモジュールの依存関係をコピー
COPY go.mod go.sum ./
RUN go mod download

# ソースコードのコピー
COPY . .

# アプリケーションをビルド
RUN go build -o /go/main

# ポートの公開
EXPOSE 8080

# アプリケーションを実行
CMD ["/go/main"]
