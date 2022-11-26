■10.2.3 Rate または Cron を使用したスケジュール式

https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/services-cloudwatchevents-expressions.html

■エラー
なぜかbatchログが出力されなかった。
→batch_container_definitions　ファイルの
 "commannd" : ["/bin/date"]
が "comannd" : ["/bin/date"]になっていた。
applyは成功してしまうため、気づけない。

→修正後もログストリームの中身が無い。（調査中）
