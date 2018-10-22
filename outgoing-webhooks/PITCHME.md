# 発信ウェブフック - Outgoing Webhooks

---

## 目次
1. 発信ウェブフックとは
2. 必要な知識
3. Slack の設定
4. フックアプリ作成

---

## 1. 発信ウェブフックとは
Slack での発言が特定の文字列から始まった場合に、指定したサーバに対してメッセージを送信し、サーバで処理された結果を受け取れる機能

---

## 2. 必要なモノ
- Slack アカウントとカスタムインテグレーション設定権限
- インターネットに繋がるWebサーバ

---

## 3. Slack の設定
1. SlackのAPP管理>カスタムインテグレーション>発信ウェブフック項目を開き、設定を追加・編集を開始する。
![slack1.png](outgoing-webhooks/slack1.png)

+++

## 3. Slack の設定
2. 発信トリガーとなる文字列と送信先サーバを設定する。(チャンネル指定は任意)
![slack2.png](outgoing-webhooks/slack2.png)

---

## 4. フックアプリ作成
1. Slack からはポストデータが送られるのでとりあえずダンプして中身を確かめる。
2. レスポンスは最低限文字列を値とする text プロパティを持つJSONを返すだけで良い。(デフォルトでレスポンスボディをJSONとして解釈してくれる。)
3. 例はPHPだが 1, 2 ができれば何でも良い。

```php
<?php
echo json_encode([
	'text' => json_encode($_POST)
], JSON_UNESCAPED_UNICODE);
```

![result1.png](outgoing-webhooks/result1.png)

+++

## 4. フックアプリ作成
3. 後は実際にやりたいことをコーディングするだけ

---

## おわり


