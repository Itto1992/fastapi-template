ユースケース（エンドポイント内における認証・認可を除くビジネスロジック）を定義するディレクトリ

# 実装ルール
- `routers` で定義したエンドポイントと同じフォルダ構成、ファイル名、関数名にする
- 各ユースケースは関数として実装し、クラスは原則用いない

**例**
```
.
├── routers/
│   ├── projects/
│   │   ├── create_project.py
│   │   ├── list_projects.py
│   │   ├── update_project.py
│   │   └── delete_project.py
│   └── users/
│       ├── create_user.py
│       ├── list_users.py
│       ├── update_user.py
│       └── delete_user.py
└── usecases/
    ├── projects/
    │   ├── create_project.py
    │   ├── list_projects.py
    │   ├── update_project.py
    │   └── delete_project.py
    └── users/
        ├── create_user.py
        ├── list_users.py
        ├── update_user.py
        └── delete_user.py
```

- データベース操作は[リポジトリ層](../repositories/README.md)を通じて行う
- 外部 API との通信は[インフラ層](../infrastructure/README.md)を通じて行う