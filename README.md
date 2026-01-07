# FastAPI のバックエンドサーバーを作成する際のディレクトリ構成例

## FastAPI サーバーの起動
```bash
docker compose up -d
```

FastAPI サーバーが起動したら、 `http://localhost:8000/docs` にアクセスして Swagger UI が表示されることを確認します。

## FastAPI サーバーの停止
```bash
docker compose down
```

## ライブラリ管理
`pyproject.toml` を編集し、必要なライブラリを追加、削除したのち、以下のコマンドを実行することで `uv.lock` を更新します。

```bash
docker compose run --rm backend uv lock
```