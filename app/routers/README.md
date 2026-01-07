各種ルータを定義するディレクトリ

# 実装ルール
- 1つのルータにつき1つのサブディレクトリを作成する
- 1つのエンドポイントにつき1つのファイルを作成する

**例**
```
.
└── routers/
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

- ルータごとに共通する依存がある場合は個別のエンドポイントの `Depends` ではなく、ルータの `dependencies` に定義する

**例**
```python
from fastapi import APIRouter, Depends
from app.utils.dependencies.authorization import get_current_user

router = APIRouter(
    prefix="/projects",
    tags=["projects"],
    dependencies=[Depends(get_current_user)],
)
```

- そのエンドポイントの中でのみ利用される依存は各ファイルの中で定義する。例えば、エンドポイント依存の認可ロジックなど
- エンドポイントはユースケース（サービス）の薄いラッパーに留める。これによってテストが容易になる

**例**
```python
# create_project.py
class UserPolicy:

    @staticmethod
    def can_create_project(user: User) -> bool:
        # なんらかの認可ロジック
        return True


def authorize_create_project(
    current_user: User = Depends(get_current_user),
) -> None:
    if not UserPolicy.can_create_project(current_user):
        raise HTTPException(status_code=403, detail="Not authorized to create project")


@router.post("/")
def create_project(
    project: CreateProjectRequest,
    _: None = Depends(authorize_create_project),
):
    # プロジェクト作成のユースケース（サービス）を実行するだけ
    return project_service.create_project(project)
```