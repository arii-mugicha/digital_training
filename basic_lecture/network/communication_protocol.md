# 通信プロトコル
例は以下。
| 層名 | TCP/IPモデル |プロトコル例|
|-----|-----|-----|
| アプリケーション層 | アプリケーション層 | DHCP/NTP/IMAP/POP/SMTP |
| プレゼンテーション層 | アプリケーション層 | " |
| セッション層 | アプリケーション層 | " |
| トランスポート層 | トランスポート層 | TCP/UDP |
| ネットワーク層 | インターネット層 | IP/ARP/RARP/ICMP |
| データリンク層 |ネットワークインターフェース層 | PPP/PPPoE |
| 物理層 |ネットワークインターフェース層 | " |

## ネットワークインターフェース層
- PPP (Point-to-Point Protocol)  
  1vs1のコンピュータ接続
- PPPoE (PPP over Ethernet)  
  イーサネットを利用したPPP機能の提供

## インターネット層
- ARP (Address Resolution Protocol)  
  IPアドレスからMACアドレスを取得
- RARP (Reverse ARP)
  MACアドレスからIPアドレスを取得
- ICMP (Internet Control Message Protocol)
  IPを利用した通信おけるエラーメッセージ、制御メッセージの転送プロトコル

## トランスポート層
- TCP (Transmission Control Protocol)
  - 信頼性の高い通信を行う
  - `SYN(確立要求) -> ACK(確認応答)+SYN(確立要求)` -> ACK の3段階の認証(**3ウェイハンドシェイク**)
- UDP (User Datagram Protocol)
  - 高速性、リアルタイム性を重視したプロトコル
  - 相手の応答を待たないコネクションレス型

## アプリケーション層
- DHCP (Dynamic Host Configuration Protocol)  
  機器ごとにIPアドレスを割り当てる
- Network Time Protocol  
  ネットワークに接続される機器の時刻を同期する

### 電子メールに関するプロトコル
- SMTP (Simple Mail Transfer Protocol)  
  電子メールの配送
- POP (Post Officec Protocol)  
  メールサーバの電子メールを端末にコピー
- IMAP (Internet Message Access Protocol)  
  メールサーバに届いた電子メールを直接参照する
