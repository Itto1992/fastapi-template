FastAPI のアプリケーションを定義したディレクトリ

# ディレクトリ構成
```
.
├── main.py                   # FastAPIのエントリポイント
├── api/
│   ├── routers/              # エンドポイントを定義
│   ├── schemas/              # Pydantic: request/response DTO/
│   │   ├── requests
│   │   └── response
│   └── dependencies.py       # FastAPI Depends（肥大化したらディレクトリ化する）
├── application/
│   ├── usecases/             # ユースケース（アプリケーションサービス）
│   ├── ports/                # 外部に依存しないIF（Repository等の抽象）
│   └── exceptions.py         # アプリケーションの例外（肥大化したらディレクトリ化する）
├── domain/
│   ├── model/                # Entity / ValueObject / Aggregate
│   ├── services/             # ドメインサービス（純粋）
│   └── exceptions.py         # ドメインの例外（肥大化したらディレクトリ化する）
├── infrastructure/
│   ├── persistence/
│   │   ├── models            # ORMモデル
│   │   ├── repositories      # CRUD 操作
│   │   └── session.py        # DBセッション生成
│   └── external/             # 永続化以外の外部 API（肥大化したら個々のサブディレクトリを切ってもいい）
└── shared/
    ├── config.py             # アプリ共通の設定
    ├── logging.py            # ログ
    └── utils.py              # その他（肥大化したらディレクトリ化する）
```