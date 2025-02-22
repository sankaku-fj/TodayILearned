# 「Hello, World!」API を作る

```
pip install flask
```

```py
from flask import Flask, jsonify

app = Flask(__name__)

@app.route('/hello', methods=['GET'])
def hello():
    return jsonify({'message': 'Hello, World!'})

if __name__ == '__main__':
    app.run(debug=True)
```

このコードを app.py として保存し、`python app.py` で実行する。  
http://127.0.0.1:5000/hello にアクセスすると `{"message": "Hello, World!"}` が返る。