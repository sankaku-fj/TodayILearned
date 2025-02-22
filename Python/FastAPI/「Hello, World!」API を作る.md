# 「Hello, World!」API を作る

```
pip install fastapi uvicorn
```

* FastAPI: Webフレームワーク本体
* Uvicorn: ASGIサーバ（FastAPIはASGIベースで動作する）

```py
from fastapi import FastAPI

app = FastAPI()

@app.get("/hello")
def hello():
    return {"message": "Hello, World!"}

# `uvicorn` でサーバーを起動する
# `uvicorn main:app --reload`
```

このコードを main.py として保存し、`uvicorn main:app --reload` で実行する。  
http://127.0.0.1:8000/hello にアクセスすると `{"message": "Hello, World!"}` が返る。