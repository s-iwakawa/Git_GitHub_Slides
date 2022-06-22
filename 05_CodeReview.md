# Kintone Dojo コードレビュー

_🇺🇸 English version: [05_CodeReview_EN.md](05_CodeReview_EN.md)_

## 概要 <!-- omit in toc -->
* [`kintone_dojo` Repoの使用方法](#kintone_dojo-repoの使用方法)
* [Demo YouTube Videos](#demo-youtube-videos)
  * [`kintone_dojo` Task Demo](#kintone_dojo-task-demo)
  * [GitHub Code Review + GitHub Desktop App](#github-code-review--github-desktop-app)

## `kintone_dojo` Repoの使用方法
* ⚠️ このリポジトリは, `kintone_dojo` の割り当てにのみ使用してください。
* ⚡ 講義ノートを別の場所に保存します。
* これは, `git` または GitHub の問題が講義中にメモのに 影響しないためです

`kintone_dojo`の割り当てを開始するとき：
1. mainブランチから, `task##`というタイトルの新しいブランチを作成します。
    * `$ git checkout -b task01`
2. 新しいブランチに **Task##** フォルダを作成します。
    * `$ mkdir Task01`
3. コードを記述して, このフォルダーにコミットします。
    * `$ git add Task01.html Task01.js`
    * `$ git commit -m "Task01 - 最初のドラフト"`

コードレビューの準備ができたら：
1. ブランチを GitHub にプッシュします
    * `git push origin task01`
2. `task ##` ブランチを `main` とマージするプルリクエストを作成します。
3. レビュー担当者を割り当てます

## Demo YouTube Videos

### `kintone_dojo` Task Demo
* [![kintone_dojo_branch_demo_terminal.png](img/`kintone_dojo_branch_demo_terminal.png)](https://youtu.be/-9amExonLI4)

### GitHub Code Review + GitHub Desktop App
* [![kintone_dojo_branch_demo_app.png](img/`kintone_dojo_branch_demo_app.png)](https://youtu.be/u1-q8nh5irk)

## List of Lecture Guides <!-- omit in toc -->
[README.md](README.md) ⚙️
