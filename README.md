# モデリング勉強会（お題：Twitter）

## 仕様

仕様は以下の通り（Wikipediaより一部抜粋）
基本的にはツイート関連で、プロテクト、非公開ユーザー、ブロック、ミュート、いいねなどはスコープ外

### ツイート (tweet)
ユーザーから投稿される140字以内の文章のことで、それぞれに固有のURLが割り当てられる。文字数に半角・全角の区別はない。以前は日本版公式サイトで「つぶやき」として表記されていたが、「ツイート」に統一された。元々は字数制限は無かったのだが、携帯電話のSMS機能を利用した投稿が多かったため、そのSMS機能の字数制限160字から利用者名分の20文字を引いた字数を上限とする様に仕様が変更された。

### リツイート (retweet)
他のユーザーの投稿を再投稿すること。自身のフォロワーにそのツイートを見せることができる。RTと略すことが多い。後述する非公式リツイートと区別する目的で、公式リツイートとも呼ばれる。
リツイート機能は2009年11月に英語版の一部ユーザーを対象に試験的に実装され[48]。2010年1月22日より日本語版Twitterにも追加されている。元のツイートが削除されると公式リツイートも削除される。
自分がフォローしている人のうち誰かがリツイートした場合、自分がフォローしていない人の投稿であっても、その投稿が自分のタイムラインに表示される。
2015年4月7日より、リツイートしたユーザーの独自のコメントを入れてのリツイートが可能となった。コメントは116文字まで入力可能。コメントを入れてリツイートした場合は引用ツイートの形となり、コメントを入れずにリツイートした場合は今までのリツイートと同様の表示である[49]。

### タイムライン (timeline)
ログインユーザーがフォローしている人の投稿やリツイートが時系列に並べて表示される画面。TLと略されることもある。最新の投稿が一番上に表示され、古い投稿は下に流れていく。

### リプライ (reply)
他のユーザーに宛てた投稿のこと。「@ユーザー名（投稿したい内容）」の書式で投稿すると、そのユーザー宛の返信扱いとなる。自分宛の投稿は一覧ページで確認することができる。ツイートの最初に@ユーザー名を入力して投稿すると、投稿をしたユーザーとされたユーザーのどちらか片方のみをフォローしている第三者ユーザーのタイムラインには表示されないが、双方をフォローしているユーザーのタイムラインには表示される。一方@ユーザー名をツイートの途中に入れて投稿すると、さらに投稿をしたユーザーをフォローしている第三者ユーザーのタイムラインにも表示されるため、あえて@ユーザー名の前に"."をいれたり"@"を2つ重ねたりする場合もある。リプライはその投稿を行なったユーザーのページを開けば誰でも見ることができるので、ダイレクトメッセージと違いプライベート性は低い。
リプライには返信元ツイートの情報が付加される機能がある[注 5]。これを利用して会話の流れをスレッド形式で表示することもできる。

### フォロー (follow)
他のユーザーのツイートを自分のタイムラインに表示できるようにユーザーを自分のフォローリストに登録すること。相手のユーザーのフォロワーになるということ。相手の設定によってはフォローされたことが通知される。

## モデルのポイント

* コアドメインはTweet（よって、Tweetは他のエンティティの変更の影響を受けない）
* deletableパッケージ=削除のコンテキスト
