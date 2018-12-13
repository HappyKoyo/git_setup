3.Github入門 :octocat:
====

## 1.Githubにリポジトリを登録しよう
githubでは、前章で作ったリポジトリをネット上で管理することができます。

1.[Githubの公式サイト](https://github.com/join?source=experiment-header-dropdowns-home)からアカウントを作成します。  
プランは無料のやつで問題ありません。登録が完了すると、Welcome to Github!というメールが送られます。  

2.アカウントの登録が完了したら、[トップページ](https://github.com/)右上にあるSign inからサインインしてください。  

3.画面右上の+ボタンからNew Repositoryを選択します。

4.Repository nameをgit_tutorialにして、あとは何も変更せずにCreate repositoryをクリックする。

5.上の方に出てくる以下のようなURLをコピーする「https://github.com/your_name/git_tutorial.git」

6.ターミナルを開いて以下のコマンドを実行する。

```
$ cd ~/src/git_tutorial
# これで、ローカル（PC内）のリポジトリに、リモート（Github上）のリポジトリを対応させます。
$ git remote add origin コピーしたURL(例：https://github.com/your_name/git_tutorial.git)
# 最後に、リモートリポジトリに送信する。
$ git push -u origin master
```

## 2.Githubからリポジトリをクローン（ダウンロード）しよう
Githubからリポジトリをクローンします。

1.[ここ](https://github.com/HappyKoyo/git_setup)に行って、画面右にあるclone or downloadをクリックし、"https://github.com/HappyKoyo/git_setup.git"をコピー

2.保存したいディレクトリ内で、以下のコマンドを実行することでクローンすることができる。

```
$ git clone https://github.com/HappyKoyo/git_setup.git ←コピーしたURL
```
