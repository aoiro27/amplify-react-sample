# CognitoにLINEログインを追加するまで

1.LINE Developersにサインインする
https://developers.line.biz/console/

2.プロパイダを作成
![Alt text](image.png)

3.作成したプロバイダにチャンネルを追加する
![Alt text](image-1.png)

チャンネル基本設定から、Open ID Connect申請をして保存
![Alt text](image-2.png)
![Alt text](image-3.png)

4.コールバックURLを開く
Congitoドメイン + /oauth2/idpresponseを設定する
![Alt text](image-4.png)

5.チャンネルを公開する
![Alt text](image-5.png)

6.Cognito側にLINEログインを追加する
IDPを追加する
![Alt text](image-6.png)

![Alt text](image-7.png)

- クライアント IDに上記LINEログインチャンネルのチャンネルIDを指定する
- クライアントのシークレットに上記LINEログインチャンネルのクライアントシークレットを指定する
- 許可されたスコープに[profile email openid]を指定する


![Alt text](image-8.png)
- 発行者 URL を通じた自動入力を選択する
- 発行者 URLにhttps://access.line.meを指定する
- OpenID Connect 属性にemailを指定する

7. Cognito ホスティングUIにLINEログインを組み込む
![Alt text](image-9.png)
![Alt text](image-10.png)
![Alt text](image-11.png)
![Alt text](image-12.png)