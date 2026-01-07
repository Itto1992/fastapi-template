FastAPI のアプリケーションを定義したディレクトリ

# ディレクトリ構成
```
.
├── infrastructure  # DB など外部サービスとのコネクタを定義
├── models  # DB のスキーマを定義
├── repositories  # DB に対する CRUD 操作を定義
├── routers  # FastAPI のエンドポイントを定義
├── schemas  # エンドポイントの入出力になるスキーマを定義
├── usecases  # ルータの実際の処理（ビジネスロジック・サービス層）を定義
└── utils  # 上記以外のモジュール（共通の依存処理・エラーなど）を定義
```