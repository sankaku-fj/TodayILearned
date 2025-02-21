# Spring Boot の位置関係（アーキテクチャ） 

## 小規模なWebサービスの例

```
┌───────────────┐
│ Frontend      │（React, Vue, Angularなど）
│ (Web, Mobile) │
└──────▲────────┘
       │ API呼び出し (HTTP, JSON)
       ▼
┌───────────────┐
│ Spring Boot   │（単一のバックエンド）
│ - REST API    │
│ - ビジネスロジック │
│ - 認証・認可   │
└──────▲────────┘
       │ DBアクセス (JPA, JDBC)
       ▼
┌───────────────┐
│ Database      │（MySQL, PostgreSQL）
└───────────────┘
```

## 大規模なWebサービス（負荷分散あり）の例

```
                     ┌──────────┐
                     │ Frontend │
                     │ (Web, App)│
                     └────▲─────┘
                          │ API呼び出し
          ┌──────────────┴──────────────┐
          │       Load Balancer         │（Nginx, AWS ALB）
          └──────────────▲──────────────┘
                 ┌───────┴────────┐
                 │ Spring Boot #1 │
                 │ Spring Boot #2 │（複数インスタンスでスケール）
                 │ Spring Boot #3 │
                 └───────▲────────┘
                 │                │
                 ▼                ▼
          ┌──────────┐   ┌──────────┐
          │ Cache          │   │ Database │（DB負荷軽減のためRedisなど導入）
          │ (Redis)        │   │ (MySQL,  │
          │                │   │ PostgreSQL) │
          └──────────┘   └──────────┘
```