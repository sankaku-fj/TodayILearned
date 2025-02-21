# 「Hello, World!」API を作る

「Hello, World!」と返すだけのAPIを作成する。

## Spring Initializr を使ってプロジェクトを作成

1. <https://start.spring.io/> にアクセス
2. 設定を以下のように変更

```
Project: Maven
Language: Java
Spring Boot: 最新の安定版
Group: com.example
Artifact: hello-api
Dependencies（依存関係）: Spring Web（APIを作るために必要）
```

3. 「Generate」ボタンをクリックし、ZIPファイルをダウンロード
4. 解凍して、IDE（IntelliJ IDEAやVS Code）で開く

### メインクラス・コントローラーの作成

Spring Bootアプリケーションのエントリーポイント

```java
// src/main/java/com/example/helloapi/HelloApiApplication.java

package com.example.helloapi;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class HelloApiApplication {
    public static void main(String[] args) {
        SpringApplication.run(HelloApiApplication.class, args);
    }
}
```

コントローラー

```java
// src/main/java/com/example/helloapi/controller/HelloController.java

package com.example.helloapi.controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("/api")
public class HelloController {

    @GetMapping("/hello")
    public String sayHello() {
        return "Hello, World!";
    }
}
```

* `@RestController` → REST APIを作るためのアノテーション
* `@RequestMapping("/api")` → APIのベースURLを/apiにする
* `@GetMapping("/hello")` → GET /api/helloにアクセスしたとき、"Hello, World!" を返す

### アプリケーションの実行

windows
```cmd
./mvnw spring-boot:run
```

### APIテスト

下のリンクにアクセスすると、`Hello, World!`が返ってくる。

```
http://localhost:8080/api/hello
```