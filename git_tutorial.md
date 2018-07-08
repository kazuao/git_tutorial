# Git チュートリアル

## Gitの基本的な概念

### Gitが管理する３つのエリア（ローカル）

- ワーキングディレクトリ
- ステージングエリア
- ローカルリポジトリ



#### ワーキングディレクトリ

現在、いじってるプロジェクトが入っているディレクトリ

Gitによって変更を監視している



 #### ステージングエリア

コミットする単位を管理するためのエリア

管理することで、コミット履歴に何をしているコミットなのかをわかりやすくすることができる



#### ローカルリポジトリ

メタデータと実データを格納する場所

保存するためにはコミットを行う必要がある。



![git_local](git_images/git_local.png

)



### チーム開発を知る

#### リモートリポジトリ

ローカルリポジトリをリモート上（他の人が参照できる場所）に反映したもの。



### push とfetch

- push   →   ローカルリポジトリからリモートリポジトリにコピーする。
- fetch  →   リモートリポジトリからローカルリポジトリに最新情報を取り込むこと。

　　　　　　  fetchのみだとデータを使うことはできない。



### merge

２つ以上のブランチの開発履歴を非取るにまとめることができる。

同じ名前のリモートリポジトリとローカルリポジトリも同様。



### pull 

fetch + mergeの機能。

リモート上からデータを取ってきて、併合する。



## Git便利コマンド

- git status

  `$ git status`

  とにかく手癖で打つ。今の状態を知るためにとにかく打つ。

- git log  ~

  gitのcommit履歴を閲覧する。一人で開発している時はあまり使わないかもしれないが、

  チーム開発をしていると、とにかく打つ。

  - git log --graph

    `$ git log --graph`

    git のcommit履歴をグラフ化してくれる。見やすい。便利。

  - git log --graph --oneline

     `$ git log --graph --oneline`

    上記のグラフを一行で簡潔に表示してくれる。便利。[—oneline]はいろいろなコマンドで使うので覚えておくと便利。

- git reset 

  いろいろ取り消すコマンド。さまざまな効用がある。最初はコマンドを間違えがちなので覚えておくと取り返しがつきやすい。

  - git reset <file name>

    `$ git reset hoge.swift`

  ステージングエリアに追加されたファイルをステージングエリアから削除する。

  git addの取り消しみたいな。

  <file name>をつけないとステージングエリアから全て削除する。←→git add .

  - git reset --hard

    `$ git reset --hard`

    ワーキングディレクトリも直前のコミット時の状態に戻る。

    前回のセーブ(commit)から進めてたけど、リセットしてやり直すみたいな。

  - git reset <commit id>

    `$ git reset 507160a`

    ワーキングディレクトリはそのままでコミット履歴だけ消す。

    いっぱいコミットしたけど、まとめ直したいな。という時に。

- git push --set-upstream origin <branch name>

  `$ git push --set-upstream origin master`

  次回以降のpushでいちいちorigin <branch name>を記入しなくて済むようになるやつ。

- git stash

  `$ git stash`

  作業途中のデータを一旦避難できる。

  作業途中でまだ、コミットしたくないけど、ブランチ切り替えたいときなど。

  - git stash pop

    `$ git stash pop`

    stashを取り出すコマンド

    どのブランチでも取り出せるので要注意

- git rebase <branch name>

  `$ git rebase develop`

  現ブランチと対象ブランチのコミット履歴を一直線にすることができる。めっちゃ便利。

  - git rebase -i <branch number>（もしくは<HEAD~3>など)

    `$ git rebase -i 507160a`

    ブランチのコミット履歴を修正できる。便利

- --allow-empty

  `$ git commit --allow-empty -m "<色々メッセージ>"`

  ワーキングディレクトリが空でもfirst commitができる。めっちゃ便利！

  

## hubコマンド

Githubを利用している場合に便利なコマンド

- hub pull-request

  `$ hub pull-request -b <branch name>`

  コマンド上でpull requestを出すことができる。

  

- hub browse

  `$ hub browse`

  コマンドからGithubのWebページを開ける。地味に便利。