# flash-anki-app

## 参照するmdファイル
作業がひと区切りついたタイミング（機能実装完了、バグ修正完了など）で、その内容をdocs/progress_log.mdに追記してください。
方針・計画はdocs/project_plan.md、学習ログはdocs/learning_log.mdを参照してください

## プロジェクト概要

AWS用語集をフラッシュカード形式で学習するためのWebアプリケーション。
Anki(スペースドリピティション学習ツール)のような使い方で、AWSサービス名・用語とその説明をカード化し、繰り返し学習できることを目指す。

- カード(用語 ⇔ 説明)のCRUD管理
- 学習(復習)機能の提供
- 将来的にはユーザーごとの学習履歴・進捗管理も想定

## 技術スタック

| 分類 | 技術 | 備考 |
|---|---|---|
| 言語 | Java 21 | LTS |
| フレームワーク | Spring Boot 3.5.x | Spring Web (REST API), Spring Data JPA |
| ビルドツール | Gradle (Groovy DSL) | Gradle Wrapper 8.14.3 同梱、`./gradlew` で実行 |
| データベース | H2 Database (インメモリ) | 開発・検証用。**将来的にAWS DynamoDBへ移行予定** |
| パッケージ | `io.github.rakisuto.flashankiapp` | |

### DynamoDB移行について

現在はローカル開発を優先し、H2のインメモリDBでスキーマ設計・API実装を進める。
将来DynamoDBへ移行する際は、Spring Data JPAのRepository層を境界としてデータアクセス実装を差し替えられるよう、サービス層とリポジトリ層の分離を意識して実装すること。

## よく使うコマンド

```bash
# ビルド(テスト含む)
./gradlew build

# ビルド(テストをスキップ)
./gradlew build -x test

# アプリケーション起動 (http://localhost:8080)
./gradlew bootRun

# テスト実行
./gradlew test

# 実行可能jarの生成
./gradlew bootJar
# 生成物: build/libs/flash-anki-app-0.0.1-SNAPSHOT.jar

# クラスパスや依存関係の確認
./gradlew dependencies

# ビルド生成物のクリーン
./gradlew clean
```

### H2 Console

アプリ起動後、以下にアクセスするとDBの内容をブラウザから確認できる。

- URL: http://localhost:8080/h2-console
- JDBC URL: `jdbc:h2:mem:flashankidb`
- User Name: `sa`
- Password: (空欄)

## githubへのpush,commitについて
git commitのメッセージは必ずユーザーが最終確認・編集してから実行すること。コマンド実行前に変更内容の要約のみ提示すること