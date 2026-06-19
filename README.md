# GitのグラフをMarkdownに表示するためのGitHub Actionsワークフロー

## 特徴

- [git-bahn/git-graph](https://github.com/git-bahn/git-graph)を使用
- SVG形式でグラフを作成
- 外部へのデータ送信を伴わずGitHubのみで完結
- 画像のリンク先がGitHubなので、プロキシによるキャッシュがなくすぐに反映される
  - パブリックリポジトリでは画像のURLが変わらないため、クライアント側のキャッシュの影響を受ける場合はある
- リポジトリ上に`git-graph`という名前のOrphanブランチを作り、そこにグラフ画像をアップロード
- グラフへの影響をできるだけ抑えるため、グラフ画像を含むコミットは1970年1月1日午前9時（UNIX時間のエポック）に作成される

## 例

![例](https://github.com/r02092/git-graph-gha/raw/git-graph/git-graph.svg)

## 使用方法

1. `.github/workflows/git-graph.yml`をコピーする（カスタマイズする場合など）  
   または、以下のように再利用可能なワークフローとして呼び出す

   ```yml
   uses: r02092/git-graph-gha/.github/workflows/git-graph.yml@main
   ```

2. Markdownに以下の形式のURLでグラフの画像を貼る
   ```
   https://github.com/<ユーザー名>/<リポジトリ名>/raw/git-graph/git-graph.svg
   ```

### 再利用可能なワークフローとして呼び出す際に利用できる引数

|引数名|デフォルト値|説明|
|-|-|-|
|`cache-key`|`0`|キャッシュのキー|
|`git-graph-ref`|`5ae210fa9f2cc59e4f51c9b40a98ea0fce5fa040`|使用する[git-bahn/git-graph](https://github.com/git-bahn/git-graph)のref|
|`max-count`|`20`|グラフに表示するコミットの数|
|`branch-name`|`git-graph`|グラフの画像を置くブランチ|
|`commit-msg`|`Gitのグラフを更新`|コミットメッセージ|
|`commit-name`|`github-actions[bot]`|コミットの作成者のユーザー名|
|`commit-email`|`41898282+github-actions[bot]@users.noreply.github.com`|コミットの作成者のメールアドレス|
|`commit-date`|`Thu Jan 1 00:00:00 1970 +0000`|コミットの日付|
