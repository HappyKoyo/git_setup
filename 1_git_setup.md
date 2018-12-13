1.Git入門 :octocat:
====
この章ではソフトウェアのバージョン管理を行うツール「**git**」について、説明をします。

## 1.gitのインストール
まず最初にインストールをしましょう。

```
$ sudo apt-get install git
```

## 2.gitの初期設定
```
$ git config --global user.name ユーザ名
$ git config --global user.email メールアドレス
```

## 3.演習  
実習形式で使い方を学んでもらいます。  
今回は~/srcの中にgit_tutorialというディレクトリを作り、そこでファイル管理をすることを考えます。  
gitではリポジトリというものに変更点を保存して、管理をします。（厳密にいうと、リポジトリとはミニファイルシステムのスナップショットを保存しているもの）  
では、まずリポジトリの初期化をしましょう。

```
$ mkdir -p src/git_tutorial
$ cd src/git_tutorial
# ディレクトリを作成したとき、最初に一度だけgit initをしてリポジトリの初期化します。  
$ git init
```
今回は以下のようなメッセージが出ます。

```
Initialized empty Git repository in /home/your_name/src/git_tutorial/.git/
```
リポジトリを初期化することができました。
次に、リポジトリの状態を確認するコマンド、git statusを使ってみます。

```
$ git status
```
すると、以下のように表示されるはずです。(Ubuntu内部の言語が日本語の場合)

```
ブランチ master

最初のコミット

nothing to commit (create/copy files and use "git add" to track)
```
ここで、ブランチとコミットという聞き慣れない２つの単語が出てきました。
コミットとは、リポジトリに変更を保存することです。  
ブランチは後で説明します。  
このgit statusは今回の演習で何度も出てきます。覚えておきましょう。
現在は、ディレクトリの中に何も無いので、ファイルなどは表示されません。  
ファイルを追加してみましょう。hoge.txtにaaaとうって保存してください。  

```
$ gedit hoge.txt
# aaaと打って保存する
$ git status
ブランチ master

最初のコミット

追跡されていないファイル:
  (use "git add <file>..." to include in what will be committed)

	hoge.txt

nothing added to commit but untracked files present (use "git add" to track)
```
追跡されていない(gitが管理していない)ファイル一覧に、hoge.txtが現れました。  
gitは対象ディレクトリ内のファイルを保存・編集しても自動的に追跡しません。  
ステージ領域というところにファイルを登録することで初めて追跡するようになります。  
hoge.txtを追跡(gitが管理)できるようにgit addコマンドでステージ領域にファイルを追加しましょう。  

```
$ git add hoge.txt
$ git status
ブランチ master

最初のコミット

コミット予定の変更点:
  (use "git rm --cached <file>..." to unstage)

	new file:   hoge.txt
```
これで、hoge.txtをステージ領域に上げることができました。  
git add はrmやreset等で取り下げることができます。(rmやresetの使い方は自分で調べてみてください)
次に、リポジトリにステージ領域の内容を記録(コミット)するために、git commitコマンドを使います。

```
$ git commit -m "first commit"
[master (root-commit) a1d88e0] first commit
 1 file changed, 1 insertion(+)
 create mode 100644 hoge.txt
```
ここで、git statusコマンドを実行してみましょう。

```
$ git status
ブランチ master
nothing to commit, working directory clean
```
これで、リポジトリに記録することができました。  
変更がある場合は、変更するファイルをステージ領域に加え、新しくコミットしましょう。
最後に、コミットがいつ行われたかを確認するgit logコマンドを使ってみましょう。

```
$ git log
commit a1d88e01514af5888b74affcf1434889ef5116b9
Author: HappyKoyo <robot.engineer.koyo@gmail.com>
Date:   Tue Dec 11 12:02:12 2018 +0900

    first commit
```
これで、ディレクトリの変更履歴を保存することができました。

### 次回 [2.リポジトリの管理](https://github.com/HappyKoyo/git_setup/blob/master/2_branch.md)
