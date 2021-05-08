---
title: HTTP の意味論
head:
  - - meta
    - name: og:title
      content: HTTP の意味論
  - - meta
    - name: twitter:title
      content: HTTP の意味論
  - - meta
    - name: og:description
      content: http semantics を読んだのでまとめる
  - - meta
    - name: twitter:description
      content: http semantics を読んだのでまとめる
  - - meta
    - name: og:image
      content: https://res.cloudinary.com/dtapptgdd/image/upload/w_1000/l_text:Sawarabi Gothic_70_bold:http semantics について/v1620370500/Screen_Shot_2021-05-07_at_15.54.47_extlvu.png
  - - meta
    - name: twitter:image
      content: https://res.cloudinary.com/dtapptgdd/image/upload/w_1000/l_text:Sawarabi Gothic_70_bold:http semantics について/v1620370500/Screen_Shot_2021-05-07_at_15.54.47_extlvu.png
---

# {{ $frontmatter.title }}

HTTP は、分散型の協調的なハイパーテキスト情報システム用の，ステートレスな応用レベルのプロトコルである。  
全般的なアーキテクチャについて、用語について、中核のプロトコル、拡張機能の仕組み、"http" および "https" URI スキームについて、自分の知らなかったことを中心にまとめる。  
また、これは Real World HTTP を読むにあたっての自分用補助資料として活用していくつもりである。あくまで自分用。  
ただ、なんか列挙してあるやつで抜けてると不自然なやつとかは書くかも。
 
## 歴史
HTTP は、 1990年に導入されてから w3 の代表的なプロトコルとして使用されている。最初は GET メソッドのみの `所与のパス名で識別され，予めハイパーテキスト文書と見做されるリソース` を転送する用途のみという小さい構成から始まった。HTTP は web の成長と共に成長し、HTTP/0.9、HTTP/1.0 として定義された（Real World HTTP でも言及されている [RFC1945](https://triple-underscore.github.io/http-semantics-ja.html#RFC1945)）  
  
HTTP/1.1 は、既存との互換性は維持しつつ，プロトコルの各種特能を精緻化して、インターネットにまたがる相互運用能、スケール能、堅牢性を改善するべく設計された。  
これらは以下である。
- 固定的／動的（チャンク化）な内容用の長さに基づくデータ区切子
- 内容折衝用の一貫したフレームワーク
- 条件付き要請用の不透明な検証子
- キャッシュの一貫性をより良くするためのキャッシュ制御
- 部分的な更新用の範囲要請
- 既定の持続的な接続
  
※堅牢性は正確性、ソフトウェアでは堅牢性テストを行うことが多い  
  
HTTP/1.1 は、 1995年に導入され、[インターネット標準化過程](https://www.nic.ad.jp/ja/rfc-jp/Std-track.html) にて発行された。  
  
HTTP/2 は、複数の HTTP メッセージを同時的に交換するため，既存のプロトコル（TLS、TCP）の上層に多重化されたセッション層を導入した。また、効率的なフィールド圧縮とサーバプッシュも同時に実装された。  
HTTP/3 は、 QUIC（Quick UDP Internet Connections） を "TCP 越しに代えて、UDP 越しのセキュアな多重化されたトランスポート" として利用することにより，同時的なメッセージ用により高い独立性が伴っている。（ここはあとでもう少し詳しく調べる）  
  
## 基本的な用語

#### URI

Uniform Resource Identifier のことで、一定の書式によってリソースを指し示す識別子である。  
1998年8月に [RFC2396](https://tools.ietf.org/html/rfc2396) として規定された。  

[このQiitaの記事](https://qiita.com/FJ-K/items/322171f63aace906d150) が良さそう。  
> RFC2396ですが、簡単に表現すると”URLで利用できる文字”です。

これはどういうことかというと、URL で利用できる文字には予約文字と非予約文字があり、非予約文字がURLで使用可能になっている。（要は数字と記号は使える、日本語とか
はエンコードしないと使えないみたいな感じ）  

#### リソース

http request のターゲットをリソースという。  
HTTP は、リソースの資質を制限しない。  
HTTP の設計目標の一つに、リソースの識別を request の semantic から分離することというのがある。

#### 表現
#### 接続、クライアント、サーバ
#### メッセージ
#### UserAgent
#### サーバ
#### ミドルウェア
#### キャッシュ
#### メッセージの送受信

## HTTP における識別子

#### http uri スキーム

#### https uri スキーム

#### http/https の両者の比較