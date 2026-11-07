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

- 通常の更新は日本時間の平日 9:00〜21:00 に新しいブランチを作成する。
- レビュアーは `hiroxto` を指定する。
- ロックファイルのメンテナンスは日本時間の毎月第1月曜日 9:00〜21:00 に行い、自動マージする。
- 依存関係のバージョンを固定する更新には [`schedule:daily`](https://docs.renovatebot.com/presets-schedule/#scheduledaily) を適用し、自動マージする。
- GitHub Actions のダイジェストの固定と更新は時間帯を制限しない。

読み込まれる Renovate 標準のプリセットは [`default.json`](default.json) を参照。

## 個別に指定できるプリセット

- `github>hiroxto/renovate-config:scheduleDaily` は、日本時間の平日 9:00〜21:00 に更新ブランチを作成する。
- `github>hiroxto/renovate-config:lockFileMaintenance` は、ロックファイルのメンテナンスを設定する。
- `github>hiroxto/renovate-config:pin` は、依存関係のバージョンを固定する更新を設定する。

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
