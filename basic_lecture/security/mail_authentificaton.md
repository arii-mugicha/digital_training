# SPF
Sended Policy Framework

メールの送信元IPアドレスを用いて認証する技術

## 仕組み
1. 送信側が、送信側のDNSサーバに**SPFレコード**を登録する
   - SPFレコードにはメールサーバのIPアドレスを記載する
3. メールを送信し、受信側は**差出人ドメイン**と**送信元IPアドレス**を確認する
4. ドメイン情報をもとにDNSサーバにSPFレコードを問い合わせる
5. 取得したSPFレコードのIPアドレスと送信元IPアドレスを検証する

# DKIM
Domain Keys  Identifed Mail
- デジタル署名を用いて**メール認証**と**改竄の検知**を行う

## DKIMの仕組み
1. メールサーバに秘密鍵を、DNSサーバに公開鍵を登録
2. 秘密鍵で署名してメールを送信
3. 受信者はドメインをもとにDNSサーバに公開鍵を問い合わせ
4. 署名を公開鍵を用いて復号することで検証

# DMARC
Domain-based Message Authentification, Reporting, and Comformance
- SPFやDKIM認証が失敗したときにどのようにそのメールを取り扱うのかを決める仕組み

 ## DMARCの仕組み
 1. DNSサーバに**DMARCポリシー**を登録する
 2. 認証失敗時にDNSサーバからDMARCポリシーを取得、その後の処理を決定
