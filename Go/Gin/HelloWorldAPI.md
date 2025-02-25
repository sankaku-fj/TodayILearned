# 「Hello, World!」API を作る

「Hello, World!」と返すだけのAPIを作成する。

### プロジェクトフォルダの作成

```sh
mkdir hello-api
cd hello-api
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

### モジュールの初期化

```sh
go mod init hello-api
```

```sh
go mod tidy
```

### APIの実行

```sh
go run main.go
```

`http://localhost:8080/`