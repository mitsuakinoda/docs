---
categories: 'sdk'
date: 2015-05-19T23:50:00+09:00
description: 'Growthbeat API ついて説明します'
draft: false
title: Growthbeat API Gudeliene
---

# 概要

Growthbeat ではサーバー API を用意しております。Growthbeat プラットフォームに蓄積されたデータを管理画面外からも取得することが可能となっております。

## APIを使用する前に

API を利用するには Growthbeat への会員登録が必要となります。API を使用するにはアカウントに紐付いている API キーの使用が必須となります。API キーの取得方法は [こちら](http://support.growthbeat.com/manual/growthbeat/#apiキーの確認) を参照してください。

# リクエスト

APIとの全ての通信にはHTTPSプロトコルを利用します。

|利用サービス|アクセス先ホスト|
|:---:|:---:|
|Growthbeat|api.growthbeat.com|
|Growth Analytics|api.analytics.growthbeat.com|
|Growth Message|api.message.growthbeat.com|
|Growth Push|api.growthpush.com|


# 利用制限

API を使用すると API ごとにリクエスト数が加算されます。ご契約のリクエスト数、現在のリクエスト数に応じて使用する API を考慮してください。月のAPIの上限を超えますと APIに てデータが取得できなくなりますのでご了承ください。

# データ形式

APIとのデータの送受信にはJSONを利用します。JSONをリクエストボディに含める場合、リクエストのContent-Typeヘッダに `application/json` を指定し、リクエストヘッダーは `application/x-www-form-urlencoded` で送信してください。
GETリクエストにバラメータを含める場合にはURIクエリを利用します。

正常なレスポンスの場合は、リファレンスにあるAPIごとのJSON形式のレスポンスが返ります。エラーレスポンス時には、エラーコード、エラーメッセージのみのJSON形式のレスポンスが返ります。

**正常なレスポンス例**

```
curl -X GET \
-H 'Accept: application/json' \
'https://api.growthbeat.com/1/accounts/YOUR_ACCOUNT_ID?credentialId=YOUR_API_KEY'
```

```
{
    "name":"Subaccount for Growthbeat",
    "id":"YOUR_ACCOUNT_ID",
    "created":"2014-06-26T06:44:56+0000"
}
```

**エラーレスポンス例**

```
curl -X GET \
-H 'Accept: application/json' \
'https://api.growthbeat.com/1/accounts/YOUR_ACCOUNT_ID?credentialId=YOUR_API_KEY'
```

```
{
    "code":null,
    "message":"Bad Request"
}
```

# 活用例

* [Notifications API 経由で、特定のユーザーに対してPush通知を送る方法](http://faq.growthbeat.com/article/51-notifications-api-push)

