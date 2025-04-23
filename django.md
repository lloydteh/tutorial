## Django入門

### 1.0 環境
- VS Codeを使用。PyCharmでは、特にインストールに関してやり方異なる。Djangoに関する説明は基本Editor/IDEに関係なく、両方同じ。
- Linux系のOS（Windowsは
- Python v3.10
- Django v5.2

### 1.1 インストール
```python
# プロジェクトフォルダ作成
mkdir project && cd project

# 仮想環境
python -m venv .venv
source .venv/bin/activate

# djangoをインストール
pip install django

# インストール確認
django-admin --version

```


### 1.2 プロジェクトとアプリの作成
一つのプロジェクトで、appを追加していくやり方
#### 1.2.1 プロジェクト作成
```python
# インストール問題なければ、プロジェクト作成. この例では、projectnameという名で作成します。
django-admin startproject projectname
```
生成したプロジェクトファイル：
```
projectname/             # 任意の名前、一般的にはdjangoのプロジェクト名と同じ
│
├── projectname/         # Djangoのプロジェクト名
│   ├── __init__.py      
│   ├── asgi.py          # 非同期サーバーゲートウェイインタフェース
│   ├── settings.py      # 設定ファイル
│   ├── urls.py          # URL宣言
│   └── wsgi.py          # 同期サーバーゲートウェイインタフェース
│
├── manage.py            # DjangoのCLI
│
└── .venv/               # Virtual environment
```
- asgiとwsgiは、デプロイの時に使う。ほとんど編集する必要がない。（編集必要の例：middlewareやwebsocketを使う）
- settings.pyは、DB、メディアフォルダ、セキュリティなど、アプリを設定する
- urls.pyはアプリのurl pathを設定するファイル。Reactで言うとrouteのpathname。ブラウザ上のurlのpathを指定する。

#### 1.2.2　アプリ追加
```python
python manage.py startapp appname
```
生成されたアプリのフォルダとそのファイル：
```
appname/
├── migrations/ 　　# DB 操作
├── __init__.py
├── admin.py　　　　# モデル（DB）登録用
├── apps.py        # アプリ名定義、pytorchのモデルloadもここで行う
├── models.py      # DB のテーブル（schemaなど）定義
├── tests.py       # テストコード
└── views.py       # HTTPリクエストやAPIに返すデータを定義
```
DjangoのコンセプトはModel, View, Templete. ModelはDB、Viewでデータを処理や出力、Templateは表示のやり方。