# デプロイ手順（帰宅後15分）

## 1. GitHubに新リポジトリ作成

```
リポジトリ名: life-os
公開設定: Public（GitHub Pages無料のため）
```

## 2. このフォルダをpush

```powershell
git init
git add .
git commit -m "feat: Life OS initial setup"
git remote add origin https://github.com/Takashi-home/life-os.git
git push -u origin main
```

## 3. GitHub Pages を有効化

Settings → Pages → Source: `main` branch / `/ (root)`
→ URL: `https://Takashi-home.github.io/life-os/`

## 4. Slack Webhook URL を取得

1. https://api.slack.com/apps → Create New App
2. Incoming Webhooks → Activate
3. Add New Webhook → チャンネル選択
4. Webhook URL をコピー

## 5. GitHub Secrets を設定

Settings → Secrets and variables → Actions → New repository secret

| Name | Value |
|------|-------|
| `SLACK_WEBHOOK` | Slackで取得したWebhook URL |

## 6. スマホでの初回設定

1. `https://Takashi-home.github.io/life-os/` を開く
2. ⚙️ ボタン → 設定
3. GitHub: `Takashi-home/life-os` + Personal Access Token（`repo`権限）
4. Slack: Webhook URL
5. 保存

## 動作確認

- Actions タブ → `毎朝ダイジェスト通知` → Run workflow
- Slack に通知が来れば完了

---

## Personal Access Token の作り方

1. GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
2. Generate new token → `repo` にチェック → Generate
3. コピーしてSettings画面のToken欄に貼り付け（一度しか表示されないので注意）

---

## コスト

| 項目 | 費用 |
|------|------|
| GitHub Pages | 無料（publicリポジトリ） |
| GitHub Actions | 無料（2000分/月） |
| Slack Incoming Webhooks | 無料 |
| Claude API | 不使用（Actions内はPythonのみ） |

**Claude Code（Proプラン）は対話時のみ使用。自動化はすべてGitHub Actionsが実行。**

---

## 既存アプリとの連携

既存のSupernoteアプリへのリンクはダッシュボードの「天理教スーパーノート」カードに設定済み。
StudyAppも同様にリンクを追加できます（設定→カード編集）。
