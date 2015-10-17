#git(github)

##git、githubとは
###git　ソースコードのバージョン管理システムの一つ。
###github　gitを利用して世界中の人々が自分の作品(プログラムコードやデザインデータなど)を保存、公開することができるようにしたウェブサービスの名称。

##開発にgitを使う理由
 - gitをもし使わなければ、「全体」をコピーしてバージョン管理を行わなければならない
 - gitを使えば「変更点」だけを管理できる（これを「差分管理」という！）

##gitを使うメリット
 - 差分だけなので、データのサイズが小さくて済む
 - 差分という単位で便利な操作がいろいろできる（コミット）
 - バージョンの分岐ができる（branch）→大規模開発ができる！

##gitの基本的な動き・コミットの作り方
###リポジトリについて
####リポジトリとは…ファイルやディレクトリの状態を記録する場所
####リポジトリの種類
- ローカルリポジトリ　ユーザ一人ひとりが利用するために、自分の手元のマシン上に配置するリポジトリ
 - リモートリポジトリ　専用のサーバに配置して複数人で共有するためのリポジトリ

###コミットとは
####ファイルやディレクトリの追加・変更を、リポジトリに記録すること
![コミット1](https://dl.pushbulletusercontent.com/52lHA20Csq6Wafvwz879XqjbGC0FckNV/DSC_0003.JPG)
###コミットの作り方
####一度にどれだけコミットするかを考える（ステージング）
#####いろんなファイルをまとめてコミットするのか
![コミット2](https://dl.pushbulletusercontent.com/qIZw1fb7TQMIGnPnPsQoPl84uCDdhDRe/DSC_0004.JPG)
#####一つずつコミットするのか
![コミット3](https://dl.pushbulletusercontent.com/SqWCmPvhOUX4xvHNYv8e7UiHjB6wPf6S/DSC_0006.JPG)
####分け方はファイルの種類ごと(HTMLとかCSSとか)だったりページごとだったり
###流れとしては「開発する→ステージングする→コミットする」

##ブランチについて
###ブランチとは…「ラベル」の一つである。「枝」そのものではなくて、どこかのコミットを指している「ラベル」に過ぎない！
###masterブランチとは… リポジトリに最初のコミットを行うと作成されるブランチ。以後のコミットはブランチを切り替えるまでmasterブランチに追加されていく。

##HEADについて
###HEADとは…今いる場所を表す「ラベル」。常にHEADに対してコミットを追加するのが大原則！

##図で実際に動きを見てみる
###このように、コミットするとHEADとブランチが新しいコミットに動く。
![コミット3](https://dl.pushbulletusercontent.com/5cPKzDnWeKPoLum3kXBffq4hV833OecY/DSC_0007.JPG)

##margeについて
###margeとは…２つのブランチを１つにしたmargeコミットを作る
###図で実際の動きを見てみる
![コミット4](https://dl.pushbulletusercontent.com/qxbPcva6hcmjqUzeBjWuMgFNb59QF611/DSC_0010.JPG)

##revertについて
###revertとは…バグがあった時とかに、コミットを無かったことにする（正確に言うと対象の commit の変更を相殺するような差分commitを自動で生成する）。
###図で実際の動きを見てみる
![コミット5](https://dl.pushbulletusercontent.com/9TItqOuEx7H0tJDkduNXN8QqP1jojsQE/DSC_0011.JPG)
↓
![コミット6](https://dl.pushbulletusercontent.com/loNSAXHHfgLVEJZdSY9YorgkwfGKw9Vq/DSC_0012.JPG)
↓
![コミット7](https://dl.pushbulletusercontent.com/uZVbPaLVKSPqQlU8EkK4juuTXKNfR42O/DSC_0013.JPG)
###※コミットの削除は行わない！

##cherry-pickについて
###cherry-pickとは…指定したコミットを（別の新たなコミットとして）HEADに引っ付ける。
###図で見てみる
![コミット8](https://dl.pushbulletusercontent.com/PVhSd0ndiLXEQAywgPRhrB0evTvnIfCw/DSC_0014.JPG)

##rebaseについて
###rebaseとは…指定したブランチを丸ごと生やし直す。（前にあったブランチは削除される）cherry-pickを連続でやっている感じ。
###図で見てみる
![コミット9](https://dl.pushbulletusercontent.com/di2UgpxKiXkGko2MrbgpwqEoNmzMzAOl/DSC_0016.JPG)
###※margeは最新のmasterにリベースしてから行う。リベースを行うことで整理されて時系列順になるのでわかりやすい。また、conflict(コミット同士の競合)を防ぐことができる。

##github（リモートとローカル）

###全体像
![コミット10](https://dl.pushbulletusercontent.com/4ZR1tqhJ0jM5bLBKae3r9qOaREb3YY4i/DSC_0017.JPG)

###ローカルとリモートでのやり取りの流れ図
![コミット11](https://dl.pushbulletusercontent.com/S4WsDM6QiYlavylKHSCoNag0sLKFHPnJ/DSC_0018.JPG)

###githubを使っての実際の手順
1. 開発終わる
2. リモートの状態で取ってくる
3. リベース
4. リモートに戻る
5. プルリクエスト
6. マージ
###この手順を踏むことで、

##Q&A
###Q.一人で開発をしている時、マージする必要があるの？
###A.ある。なぜならどの時点でバグがあったのかが判定しやすいから。
###Q.なぜコミットを削除せずにrevertコミットを使うの？
###A.削除してしまうと、削除した範囲から切られたブランチがおかしくなっちゃうから。

