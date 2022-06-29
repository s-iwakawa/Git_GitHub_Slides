# Git Cheat Sheet

_🇯🇵 日本語版: [04_CheatSheet.md](04_CheatSheet.md)_

The following is an overview of useful Git command line (CLI) commands.

[GitHub Git Cheat Sheet - GitHub CheatSheet](https://training.github.com/downloads/github-git-cheat-sheet/)

## Create a Repository

| Command                       | Explanation                                                             |
| ----------------------------- | ----------------------------------------------------------------------- |
| `git init`                    | ローカルリポジトリを作成します                                          |
| `git clone [url]`             | GitHub (リモートリポジトリ)からリポジトリをクローン(ダウンロード)します |
| `git remote add origin [url]` | ローカルリポジトリをGitHub (リモートリポジトリ)に接続します             |

URL例= `https://github.com/`UserName`/`repo

## Branches

| Command                    | Explanation                                                          |
| -------------------------- | -------------------------------------------------------------------- |
| `git status`               | コミット可能なすべての新規または変更のあるファイルを一覧で表示します |
| `git branch [branch-name]` | 新規ブランチを作成します                                             |
| `git branch -d [branch]`   | 指定されたブランチを削除します                                       |
| `git checkout [branch]`    | 指定されたブランチに移動します                                       |
| `git merge [branch]`       | 指定されたブランチを現在のブランチにマージします                     |

## Sync Changes Between Local & Remote

| Command                       | Explanation                                                                             |
| ----------------------------- | --------------------------------------------------------------------------------------- |
| `git fetch [remote] [branch]` | GitHub (リモートリポジトリ)から最新情報をローカルリポジトリへダウンロードします         |
| `git push [remote] [branch]`  | ローカルリポジトリのコミットをGitHub (リモートリポジトリ)にアップロード(プッシュ)します |
| `git pull [remote]`           | GitHubの変更履歴をローカルにダウンロードします                                          |

## Snapshot

| Command                     | Explanation                                                          |
| --------------------------- | -------------------------------------------------------------------- |
| `git add [file]`            | 作業ディレクトリからステージングエリアへfileを追加します             |
| `git status`                | コミット可能なすべての新規または変更のあるファイルを一覧で表示します |
| `git add -A`                | 新規及び変更されたすべてのファイルをステージングエリアに追加します   |
| `git commit -m "[message]"` | メッセージと共に, リポジトリへ変更を記録します                       |
| `git rm -r [file]`          | Gitの管理対象からファイルまたはディレクトリを削除する                |

## Make Changes

| Command                          | Explanation                                                        |
| -------------------------------- | ------------------------------------------------------------------ |
| `git log`                        | コミット履歴を一覧で表示します                                     |
| `git log --follow [file]`        | 名前の変更を含む指定したファイルのバージョン履歴の一覧を表示します |
| `git diff [branch A] [branch B]` | ２つのブランチ間の差分を表示します                                 |
| `git show [commit]`              | 指定されたコミットのメタ情報と変更内容を表示します                 |

## Redo Commits

| Command               | Explanation                                              |
| --------------------- | -------------------------------------------------------- |
| `git reset [commit]`  | 指定したcommitの状態まで強制的に戻します                 |
| `git revert [commit]` | 指定したcommitを取り消すためにcommandです                |
| `git revert HEAD`     | 直前のコミットを取り消すための新しいコミットを作成します |

## Done <!-- omit in toc -->
[README_EN.md](README_EN.md) ⚙️
