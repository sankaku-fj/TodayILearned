# 「Hello, World!」API を作る

「Hello, World!」と返すだけのAPIを作成する。

### プロジェクトフォルダの作成

```sh
mkdir hello-api
cd hello-api
```

### モジュールの初期化

ディレクトリ名とGoモジュール名は必ずしも同じである必要はないが、後々の管理や、外部パッケージとして利用する際に分かりやすくなるため、モジュール名をディレクトリ名と揃えたほうがいい。

```sh
go mod init hello-api
```

### main.go

```go
package main

import (
	"fmt"
	"net/http"
)

func helloHandler(w http.ResponseWriter, r *http.Request) {
	w.WriteHeader(http.StatusOK)
	fmt.Fprintf(w, "Hello, World!")
}

func main() {
	http.HandleFunc("/", helloHandler)
	fmt.Println("Server is running on http://localhost:8080")
	http.ListenAndServe(":8080", nil)
}
```

### APIの実行

```sh
go run main.go
```