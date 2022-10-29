●無料ドメイン
Freenum
アカウント情報
Mail awk.owi.1119@gmail.com
Pass Awkowi4311
https://my.freenom.com/clientarea.php

●freenomで取得したドメインをRoute53に委任する
https://blog.serverworks.co.jp/delegate-route53

●DNS名とドメイン名
https://www.itra.co.jp/webmedia/domain_dns_difference.html

●証明書発行
https://aws.taf-jp.com/blog/37623
AWS運用には無料のSSL証明書を活用しよう！（取得も簡単、難易度低です）

●証明書検証とは
https://dev.classmethod.jp/articles/https-server-certification-verify/

●8.4証明書検証
修正点あり。
list から set へ変更
従来は aws_acm_certificate で作成した無料証明書の検証用レコードは list タイプで domain_validation_options を返していました。そのため、以下のようにカウントインデックスをつけて aws_route53_record で検証用レコードを登録しています。
domain_validation_options は以下のような形で返されます。ぱっと見た感じ list タイプなのですが、3.0.0 以降では set タイプに変更されています。
set は list とは異なり順序付けされません。よって、以前のようなカウントインデックスは割り当てられず Error: Invalid index となるわけです。
