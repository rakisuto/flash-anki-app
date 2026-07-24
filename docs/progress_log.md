# 進捗ログ（AWS用語集＋フラッシュカードアプリ）

方針・計画本体は `project_plan.md` を参照。本ファイルは日々の進捗のみを記録する。

---

## Day1（AWSアカウント初期設定）— 完了 ✅

- AWSアカウント作成（クレジットカード登録・電話認証まで完了）
- 請求アラート有効化（CloudWatch請求アラート／AWS無料利用枠アラート 両方チェック）
- IAMユーザー作成（`AdministratorAccess`を直接アタッチ）
- ルートユーザーからサインアウトし、IAMユーザーでログインし直し完了

**保留・未確認事項：**
- AWS Budgetsでの月次予算アラート（$1程度）… 未実施の可能性あり、次回冒頭で確認
- ルートユーザーのMFA設定 … 未実施の可能性あり、次回冒頭で確認

---

## Day2（Claude Codeでのプロジェクト作成）— 完了 ✅

- [x] プロジェクト名・パッケージ名を決める（`flash-anki-app` / `io.github.rakisuto.flashankiapp`）
- [x] Spring Bootプロジェクトの雛形をClaude Codeに作成してもらう
- [x] CLAUDE.mdの初期版を作成
- [x] ビルド確認、H2接続確認まで完了
- [x] mdファイル（project_plan / progress_log）をプロジェクト直下の`docs/`フォルダに配置
- [x] CLAUDE.mdにgit commit運用ルール（コミットメッセージは必ずユーザーが確認・編集してから実行）を追記
- [x] GitHubリポジトリ（https://github.com/rakisuto/flash-anki-app）にリモート追加し、初回push完了

---

## Day3（用語データのモデル設計）— 着手前

予定タスク：
- [ ] 用語データのフィールド設計（用語名、カテゴリ、説明文、正答率、出題回数、最終出題日時 など）
- [ ] Entityクラスとして実装

---

## 次回やること

Day3から着手。用語データのモデル設計 → Entityクラス実装。
（保留事項：Budgets設定／MFA設定の実施有無を確認）
