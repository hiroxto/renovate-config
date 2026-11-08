# renovate-config

Renovate の設定済みプリセット。

`renovate.json` の `extends` に設定して使う。

```json
{
    "$schema": "https://docs.renovatebot.com/renovate-schema.json",
    "extends": [
        "github>hiroxto/renovate-config"
    ]
}
```

プリセットについて詳しくは [Renovateのドキュメント](https://docs.renovatebot.com/config-presets/) を参照。

[Shareable Config Presets | Renovate Docs](https://docs.renovatebot.com/config-presets/)

## デフォルト設定

`github>hiroxto/renovate-config` を指定すると `default.json` が読み込まれる。

- 通常の更新は日本時間の月曜〜金曜の 9:00〜21:00 に新しいブランチを作成する。
- リリースを安定と判定するまでの最低経過時間（`minimumReleaseAge`）は1日とする。
- リポジトリごとに同時に開ける Renovate の PR 数に上限を設けない（`prConcurrentLimit` は `0`）。
- レビュアーは `hiroxto` を指定する。
- ロックファイルのメンテナンスは日本時間の毎週月曜日 9:00〜21:00 に行う。
- 依存関係のバージョンを固定する更新には [`schedule:daily`](https://docs.renovatebot.com/presets-schedule/#scheduledaily) を適用する。
- GitHub Actions のダイジェストの固定と更新は時間帯を制限しない。

読み込まれる Renovate 標準のプリセットは [`default.json`](default.json) を参照。

## 設定を上書きする

単に設定を上書きするだけなら， `renovate.json` 内で上書きする。

```json
{
    "$schema": "https://docs.renovatebot.com/renovate-schema.json",
    "extends": [
        "github>hiroxto/renovate-config"
    ],
    "schedule": [
        "every weekend"
    ]
}
```

標準プリセットの一部を除外するには `ignorePresets` に指定する。

```json
{
    "$schema": "https://docs.renovatebot.com/renovate-schema.json",
    "extends": [
        "github>hiroxto/renovate-config"
    ],
    "ignorePresets": [
        "group:phpstan"
    ]
}
```
