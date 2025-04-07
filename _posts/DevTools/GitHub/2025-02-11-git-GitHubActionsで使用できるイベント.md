---
title: GitHub Actions で使用できるイベント
category: Git
tags:
  - GitHub
  - CICD
---

<!-- more -->

## GitHub イベント一覧

GitHub Actions では、さまざまなイベントをトリガーにしてワークフローを実行できる．以下に主なイベントを列挙する．

- push
- pull_request
- issue_comment
- schedule
- workflow_dispatch

## イベント詳細

### push

リポジトリにコードをプッシュしたときに発火するイベントである．例えば、main ブランチに変更が加わった際に CI を実行する用途で使用できる．

```yaml
on:
  push:
    branches:
      - main
```

### pull_request

プルリクエストが作成、更新された際に発火するイベントである．レビュー前にテストを実行したり、ラベルを自動で付与したりする用途で使用できる．

```yaml
on:
  pull_request:
    types: [opened, synchronize, reopened]
```

### issue_comment

イシューやプルリクエストのコメントが追加された際に発火するイベントである．特定のコメントに反応してボットを動作させる用途で使用できる．

```yaml
on:
  issue_comment:
    types: [created]
```

### schedule

cron を使用してワークフローを定期実行するためのイベントである．例えば、毎日深夜にレポートを生成する場合に使用できる．

```yaml
on:
  schedule:
    - cron: "0 0 * * *" # 毎日 00:00 に実行
```

なお分単位で日時指定は可能だが，**時間ぴったりに起動するとは限らない**．よって，時間にシビアな処理には向かない．

### workflow_dispatch

手動実行用のイベントである．GitHub Actions の UI から任意のタイミングでワークフローを実行できる．

```yaml
on:
  workflow_dispatch:
```

## 適切なイベントの選択

目的に応じて適切なイベントを選択する．

- **コード変更時に自動実行する場合 → `push`**
- **プルリクエスト時にチェックを実行する場合 → `pull_request`**
- **定期的に処理を実行する場合 → `schedule`**
- **手動でワークフローを実行する場合 → `workflow_dispatch`**

## 参考

公式ドキュメント: [GitHub Actions Events](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows)
