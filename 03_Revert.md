# Git, GitHubとは？ - 巻き戻す

このセクションでは `git revert` を紹介し, Git でファイルを元に戻すやり方について説明します
  - panda

  * [タイムトラベルの準備](#タイムトラベルの準備)
    - [Local Git](#local-git)
    - [GitHub](#github)
    - [サンプル ファイル と ブランチ を作成する](#サンプル-ファイル-と-ブランチ-を作成する)
  * [元に戻す: 時計を巻き戻す](#元に戻す-時計を巻き戻す)
    - [歴史を見る](#歴史を見る)
    - [GitHub - timeline branch](#github---timeline-branch)
  * [過去を訪ねる](#過去を訪ねる)

## タイムトラベルの準備

### Local Git

前のセクションでは, `develop` ブランチを作成, マージ, 削除しました.

`master` ブランチだけにしましょう.  
`develop` ブランチがまだある場合削除してください.

1. Go into the `learning_js` folder

   ```sh
   cd ~/learning_js
   ```

2. Check the current situation with git

   ```sh
   git status
   ```

   ```
   On branch develop
   Your branch is up to date with 'origin/develop'.
   nothing to commit, working tree clean
   ```

   - Looks like the local repository is up to date with GitHub.
3. Check the repository's branches

   ```sh
   git branch
   ```

   ```terminal
   * develop
     master
   ```

4. Since we are in the `develop` branch, switch to the `master`

   ```sh
   git checkout master
   ```

   ```terminal
   Switched to branch 'master'
   Your branch is up to date with 'origin/master'.
   ```

5. Delete the `develop` branch

   ```sh
   git branch --delete develop
   ```

   ```terminal
   warning: deleting branch 'develop' that has been merged to
            'refs/remotes/origin/develop', but not yet merged to HEAD.
   Deleted branch develop (was 4f98baf).
   ```

6. develop_file.md ファイルも削除しましょう．

   ```sh
   rm develop_file.md
   ```

### GitHub
1. Github の `learning_js` リポジトリに移動します.
   - github.com/`UserName`/learning_js
2. ブランチが1つだけかどうかを確認する.
   - github.com/`UserName`/learning_js/branches
3. `develop` ブランチがあれば[ブランチを削除](https://docs.github.com/ja/github/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository#deleting-a-branch)
   - ![03_Revert_DeleteBranch](assets/03_Revert_DeleteBranch.png)

---

### サンプル ファイル と ブランチ を作成する
タイムトラベルためにファイルを作成する

1. Switch to the master branch

   ```sh
   git checkout master
   ```

2. `timeline` ブランチを作成します.

   ```sh
   git checkout -b timeline
   ```

   ```terminal
   Switched to a new branch 'timeline'
   ```

3. 次のファイルを作成して別々にコミットします.
   - `yr_1`, `yr_2`, `yr_3`

   ```sh
   touch yr_1
   git add yr_1
   git commit -m "Year 1"
   ```

   ```sh
   touch yr_2
   git add yr_2
   git commit -m "Year 2"
   ```

   ```sh
   touch yr_3
   git add yr_3
   git commit -m "Year 3"
   ```

## 元に戻す: 時計を巻き戻す

### 歴史を見る

Following four files should be inside the repository

   ```sh
   ls
   ```

   ```terminal
   README.md   yr_1   yr_2   yr_3
   ```

`git log --oneline`
  - ブランチ上でのコミットを一覧表示します.
  - チェックアウトおよび復帰コマンドに提供されたコミットハッシュを使用する.

   ```sh
   git log --oneline
   ```

   ```terminal
   7a5bbf4 (HEAD -> timeline) Year 3
   5215f6d Year 2
   f10f791 Year 1
   03098e7 (origin/master, master) README file created
   ```

`git push origin timeline`
  - これで `timeline` ブランチは GitHub にプッシュされています.
  - ブラウザでリポジトリにアクセスして確認します.

```sh
git push origin timeline
```

### GitHub - timeline branch

![03_Revert_timelineBranch](assets/03_Revert_timelineBranch.png)

# GitHub - timeline's commits

![03_Revert_timelineBranch_Commits](assets/03_Revert_timelineBranch_Commits.png)


## 過去を訪ねる

`git log --oneline`
  - ブランチ上でのコミットを一覧表示します
  - チェックアウトおよび復帰コマンドに提供されたコミットハッシュを使用する
   ```sh
   git log --oneline
   ```
   ```terminal
   7a5bbf4 (HEAD -> timeline, origin/timeline) Year 3
   5215f6d Year 2
   f10f791 Year 1
   03098e7 (origin/master, master) README file created
   ```

`git checkout [commit hash]`
  - 作業ディレクトリを[ `commit` ]とまったく同じ状態に変換します.
  - これが元に戻すコミットかどうかを確認します.
  - この状況で行われた変更は保存されません.
   ```sh
   git checkout f10f791
   ```
   ```terminal
   Note: switching to 'f10f791'.

   You are in 'detached HEAD' state. You can look around, make experimental
   changes and commit them, and you can discard any commits you make in this
   state without impacting any branches by switching back to a branch.

   If you want to create a new branch to retain commits you create, you may
   do so (now or later) by using -c with the switch command. Example:

     git switch -c <new-branch-name>

   Or undo this operation with:

     git switch -

   Turn off this advice by setting config variable advice.detachedHead to false

   HEAD is now at f10f791 Year 1
   ```

   ```sh
   ls
   ```

   ```terminal
   README.md  yr_1
   ```

## 1 Commit文過去に戻る

`git revert HEAD`
   - 1コミット前に戻ります.

   ```sh
   git checkout timeline
   ```
   ```terminal
   Previous HEAD position was f10f791 Year 1
   Switched to branch 'timeline'
   ```
   ```sh
   ls
   ```
   ```terminal
   README.md  yr_1  yr_2  yr_3
   ```
   ```sh
   git revert HEAD
   ```
   ```terminal
   Removing yr_3
   [timeline 450d385] Revert "Year 3"
    1 file changed, 0 insertions(+), 0 deletions(-)
    delete mode 100644 yr_3
   ```
   ```sh
   ls
   ```
   ```terminal
   README.md  yr_1  yr_2
   ```

## コミットハッシュで過去に戻る

`git log --oneline`

<span style="color:#AAAB25"> __727642d \(__ </span>  <span style="color:#38B9C7"> __HEAD \->__ </span>  <span style="color:#39C026"> __timeline__ </span>  <span style="color:#AAAB25"> __\)__ </span>  __Revert "Year 3"__  
<span style="color:#AAAB25"> __f7cf1cb \(__ </span>  <span style="color:#CA3323"> __origin/timeline__ </span>  <span style="color:#AAAB25"> __\)__ </span>  __Year 3__  
<span style="color:#AAAB25"> __f7fb07c__ </span>  __Year 2__  
<span style="color:#AAAB25"> __e4df7f2__ </span>  __Year 1__  
<span style="color:#AAAB25"> __03098e7 \(__ </span>  <span style="color:#CA3323"> __origin/master__ </span>  <span style="color:#AAAB25"> __\,__ </span>  <span style="color:#39C026"> __master__ </span>  __\) README file created__  


`git push origin timeline`

__Your branch is up to date with 'origin/timeline'\.__

`git log --oneline`

<span style="color:#AAAB25"> __727642d \(__ </span>  <span style="color:#38B9C7"> __HEAD \->__ </span>  <span style="color:#39C026"> __timeline__ </span>  <span style="color:#AAAB25"> __\,__ </span>  <span style="color:#CA3323"> __origin/timeline__ </span>  <span style="color:#AAAB25"> __\)__ </span>  __Revert "Year 3"__  
<span style="color:#AAAB25"> __f7cf1cb__ </span>  __Year 3__  
<span style="color:#AAAB25"> __f7fb07c__ </span>  __Year 2__  
<span style="color:#AAAB25"> __e4df7f2__ </span>  __Year 1__  
<span style="color:#AAAB25"> __03098e7 \(__ </span>  <span style="color:#CA3323"> __origin/master__ </span>  <span style="color:#AAAB25"> __\,__ </span>  <span style="color:#39C026"> __master__ </span>  __\) README file created__  

`git revert f7fb07` Year 2 commit's hash

```sh
git revert 5215f6d
```
Removing yr_2
[timeline 6c3367a] Revert "Year 2"
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 yr_2
```
`git log --oneline`

<span style="color:#AAAB25"> __f3fc335 \(__ </span>  <span style="color:#38B9C7"> __HEAD \->__ </span>  <span style="color:#39C026"> __timeline__ </span>  <span style="color:#AAAB25"> __\)__ </span>  __Revert "Year 2"__

<span style="color:#AAAB25"> __727642d \(__ </span>  <span style="color:#CA3323"> __origin/timeline__ </span>  <span style="color:#AAAB25"> __\)__ </span>  __Revert "Year 3"__

<span style="color:#AAAB25"> __f7cf1cb__ </span>  __Year 3__

<span style="color:#AAAB25"> __f7fb07c__ </span>  __Year 2__

<span style="color:#AAAB25"> __e4df7f2__ </span>  __Year 1__

<span style="color:#AAAB25"> __03098e7 \(__ </span>  <span style="color:#CA3323"> __origin/master__ </span>  <span style="color:#AAAB25"> __\,__ </span>  <span style="color:#39C026"> __master__ </span>  <span style="color:#AAAB25"> __\)__ </span>  __README file created__

Revert

`ls`

_README\.md yr\_1_

`git push origin timeline`

__git revert \[commit hash\]__
```

`git revert [commit hash]`
  - 前進する取り消しコマンド
  - 指定された[ `commit` ]によって加えられた変更を反転し, 新しいコミットとして結果を追加します.

## Reset vs Revert

| `git reset [commit]`                                              | `git revert [commit]`                           |
| ----------------------------------------------------------------- | ----------------------------------------------- |
| 元に戻す取り消し操作の削除                                        | 前進する取り消し操作                            |
| 過去の [`commit`] に戻り, それまでのすべてのコミットを削除します. | 過去の[ `commit` ]で新しいコミットを作成します. |
| これはすべてをクリーンアップします.                               | コミットは削除されません.                       |
| ただし, 削除されたコミットの履歴は失われます.                     | 公開/共有リポジトリに使用                       |

![03_Revert_GitRevert.png](assets/03_Revert_GitRevert.png)

## Git Command-Line カンニングペーパー

[GitHub Git チートシート - GitHub Cheatsheets](https://training.github.com/downloads/ja/github-git-cheat-sheet/)

### Create a Repository

| コマンド                      | 説明                                                                   |
| ----------------------------- | ---------------------------------------------------------------------- |
| `git init`                    | ローカルリポジトリを作成します                                         |
| `git clone [url]`             | GitHub (リモートリポジトリ)からリポジトリをクローン(ダウンロード)します |
| `git remote add origin [url]` | ローカルリポジトリをGitHub (リモートリポジトリ)に接続します             |

URL例= `https://github.com/`UserName`/`repo``

### Branches

| コマンド                   | 説明                                                                 |
| -------------------------- | -------------------------------------------------------------------- |
| `git status`               | コミット可能なすべての新規または変更のあるファイルを一覧で表示します |
| `git branch [branch-name]` | 新規ブランチを作成します                                             |
| `git branch -d [branch]`   | 指定されたブランチを削除します                                       |
| `git checkout [branch]`    | 指定されたブランチに移動します                                       |
| `git merge [branch]`       | 指定されたブランチを現在のブランチにマージします                     |

### Sync Changes Between Local & Remote

| コマンド                      | 説明                                                                                   |
| ----------------------------- | -------------------------------------------------------------------------------------- |
| `git fetch [remote] [branch]` | GitHub (リモートリポジトリ)から最新情報をローカルリポジトリへダウンロードします         |
| `git push [remote] [branch]`  | ローカルリポジトリのコミットをGitHub (リモートリポジトリ)にアップロード(プッシュ)します |
| `git pull [remote]`           | GitHubの変更履歴をローカルにダウンロードします                                         |

### Snapshotting

| コマンド                    | 説明                                                                 |
| --------------------------- | -------------------------------------------------------------------- |
| `git add [file]`            | 作業ディレクトリからステージングエリアへfileを追加します             |
| `git status`                | コミット可能なすべての新規または変更のあるファイルを一覧で表示します |
| `git add -A`                | 新規及び変更されたすべてのファイルをステージングエリアに追加します   |
| `git commit -m "[message]"` | メッセージと共に、リポジトリへ変更を記録します                       |
| `git rm -r [file]`          | Gitの管理対象からファイルまたはディレクトリを削除する                |

### Make Changes

| コマンド                         | 説明                                                               |
| -------------------------------- | ------------------------------------------------------------------ |
| `git log`                        | コミット履歴を一覧で表示します                                     |
| `git log --follow [file]`        | 名前の変更を含む指定したファイルのバージョン履歴の一覧を表示します |
| `git diff [branch A] [branch B]` | ２つのブランチ間の差分を表示します                                 |
| `git show [commit]`              | 指定されたコミットのメタ情報と変更内容を表示します                 |

### Redo Commits

| コマンド              | 説明                                                     |
| --------------------- | -------------------------------------------------------- |
| `git reset [commit]`  | 指定したcommitの状態まで強制的に戻します                 |
| `git revert [commit]` | 指定したcommitを取り消すためにコマンドです               |
| `git revert HEAD`     | 直前のコミットを取り消すための新しいコミットを作成します |

GitHub Desktop App

## GitHub Desktop App

ダウンロード: [GitHub Desktop | Simple collaboration from your desktop](https://desktop.github.com/)

GitHub Docs: [GitHub Desktopのドキュメント](https://docs.github.com/ja/desktop)
