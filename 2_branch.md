2.リポジトリの管理 :octocat:
====

## 1.変更差分の確認
gitのメイン機能の一つ、変更差分確認をします。
まず、前回作ったgit_tutorialへ移動し、hoge.txtを変更します。

```
$ cd src/git_tutorial
$ gedit hoge.txt
# aaaの下にbbbを追加
$ git status
ブランチ master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   hoge.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
ステージ領域に上がっているファイルに変更があったことを教えてくれます。
git diffコマンドで、前回のコミットからの変更点を確認しましょう。

```
$ git diff
diff --git a/hoge.txt b/hoge.txt
index 72943a1..dbee026 100644
--- a/hoge.txt
+++ b/hoge.txt
@@ -1 +1,2 @@
 aaa
+bbb
```
これで、bbbがhoge.txtに追加されていることが確認できます。
変更部分に問題が無いことを確認して、ステージ領域に上げます。

```
$ git add hoge.txt
```


## 2.ファイルの追加と削除
ファイルを新規作成してコミットしてみましょう。

```
$ gedit fuga.txt
# cccと書き込む
$ git add fuga.txt
$ git status
ブランチ master
コミット予定の変更点:
  (use "git reset HEAD <file>..." to unstage)

	new file:   fuga.txt
	modified:   hoge.txt

$ git commit -m "add fuga.txt"
[master da8ad1b] add fuga.txt
 2 files changed, 2 insertions(+)
 create mode 100644 fuga.txt
```
慣れてきましたか？
今度はステージ領域に上げたファイルを削除してみます。

```
$ rm fuga.txt
$ git status
ブランチ master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	deleted:    fuga.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
一見上手く行っているように見えますが、実は領域にfuga.txtが残ったままになります。  
このままコミットすると、fuga.txtが記録されてしまうため、git rmで削除します。

```
$ git rm fuga.txt
$ git status
ブランチ master
コミット予定の変更点:
  (use "git reset HEAD <file>..." to unstage)

	deleted:    fuga.txt

$ git commit -m "delete fuga.txt"
```
ファイルを削除したときは、必ずgit rmも同時にしましょう。

## 3.消したファイルを復活させる
git logを使って昔のコミットを見ましょう

```
$ git log
commit 8a2fcdc7f5a6fc30db2388c991780fd98c0dba88
Author: your_name <your_email_adress>
Date:   Thu Dec 13 04:35:06 2018 +0900

    delete fuga.txt

commit da8ad1b1947a5f194f924aafc9b21c43f9a93a79
Author: your_name <your_email_adress>
Date:   Thu Dec 13 04:28:03 2018 +0900

    add fuga.txt

commit a1d88e01514af5888b74affcf1434889ef5116b9
Author: your_name <your_email_adress>
Date:   Tue Dec 11 12:02:12 2018 +0900

    first commit
```
ここで変更履歴を見ることができます。fuga.txtを復活させる場合は、真ん中のコミットにもどします。  
commitの横に書いてあるのが、コミットIDです。
コミットIDを指定して、そのバージョンへ戻ります。  
今回は、fuga.txtがあったバージョンへ戻しましょう。

```
$ git reset --hard da8ad1b1947a5f194f924aafc9b21c43f9a93a79
HEAD is now at da8ad1b add fuga.txt
```
これで、fuga.txtが復活しているはずです。

### 次回 [3.Github入門](https://github.com/HappyKoyo/git_setup/blob/master/3_github_tutorial.md)
