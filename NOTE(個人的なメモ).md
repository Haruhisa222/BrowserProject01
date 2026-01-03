# Git : https://github.com/d0iasm/sababook


# 第一章(ブラウザとは)-------------------------------------------------------------
## 1.ブラウザの概要・解説<---!復習!

#第二章(URL解析)------------------------------------------------------------------
##1.URLの解析:saba_core/src/url.rs
"http://example.com:8080/path/to/resource?key=value"を、スキーム、ホスト、ポート番号、パス、クエリパラメータに分離
 
 #第三章(HTTP実装)----------------------------------------------------------------
 ##1.HTTPリクエストの構築:net/wasabi/src/http.rs
 HttpCrient作成、ドメイン名->IPアドレス、ソケットアドレス定義、ストリーム構築、リクエストライン構築、ヘッダ構築
 
 ##2.HTTPリクエスト送信,レスポンス受信:net/wasabi/src/http.rs
 
 ##3.HTTPレスポンス構造体の構築:net/wasabi/src/http.rs, saba_core/src/http.rs, saba_core/src/error.rs
 レスポンス構造体作成、ヘッダ構造体作成、エラー構造体作成、ヘッダとボディ分割、レスポンス構造体を返す<---!復習!
 (受信された HTTPレスポンス文字列を構造体として扱いやすく整形する)
 
 ##4.wasabiOS上での動作確認:src/main.rs
 ターミナル1でローカルサーバを立て、ターミナル2でQEMU上でwasabiOSを起動させてテスト
 
 #第四章(HTML解析)----------------------------------------------------------------
 ##1.字句解析:saba_core/src/renderer/html/token.rs, saba_core/src/renderer/html/attribute.rs
 HTML文字列を1文字ずつ処理して、トークン(最小単位)に分割する
 以下のようなステートマシン( 状態遷移機械)を実装   <---!復習!
         |トークン生成|          　|トークンに文字追加|
 [開始]-->[  Data  　]<--「">"」--[   Tag name    ]
             |                    ↑      ↑
             |                 /         |
           「"<"」     開始タグトークン生成　 |
             |          /      終了タグトークン生成
             ↓       /                   |
        [  Tag open ]--「"/"」-->[  End tag open  ]
 
 ##2.DOMツリーの構築:
 HTML-+--HEAD
      |
      +--BODY--+--H1:Hello,World
               |
               +--DIV--+--P:paragraph
                       |
                       +--UL...
                       
##

