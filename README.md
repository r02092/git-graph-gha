# GitのグラフをMarkdownに表示するためのGitHub Actionsワークフロー

## 特徴

- [git-bahn/git-graph](https://github.com/git-bahn/git-graph)を使用
- SVG形式でグラフを作成
- 外部へのデータ送信を伴わずGitHubのみで完結
- 画像のリンク先がGitHubなので、プロキシによるキャッシュがなくすぐに反映される
- リポジトリ上に`git-graph`という名前のOrphanブランチを作り、そこにグラフ画像をアップロード
- グラフへの影響をできるだけ抑えるため、グラフ画像を含むコミットは1970年1月1日午前9時（UNIX時間のエポック）に作成される

## 例

![例](https://github.com/r02092/git-graph-gha/raw/git-graph/git-graph.svg)

## 使用方法

1. `.github/workflows/git-graph.yml`をコピーする（カスタマイズする場合など）  
   または、以下のように再利用可能なワークフローとして呼び出す

   ```yml
   uses: r02092/git-graph-gha/.github/workflows/git-graph.yml
   ```

2. Markdownに以下の形式のURLでグラフの画像を貼る
   ```
   https://github.com/<ユーザー名>/<リポジトリ名>/raw/git-graph/git-graph.svg
   ```
