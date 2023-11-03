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

## 設定済みの設定ファイル

### gitFlow.json

git-flow向けにベースブランチをdevelopに設定する。

### groupJest.json

npmの[jest](https://www.npmjs.com/package/jest)と[ts-jest](https://www.npmjs.com/package/ts-jest)をグループにする設定。

### groupLinters.json

Linter周りのグループ設定。
Renovate標準の[packages:linters](https://docs.renovatebot.com/presets-packages/#packageslinters)に加えて，[prettier](https://www.npmjs.com/package/prettier)もLinterとしてグループ化する。

### groupNode.json

Node.jsをグループ化する設定。

### groupVeeValidate.json

[vee-validate](https://github.com/logaretm/vee-validate/)をグループ化する設定。
npmの[vee-validate](https://www.npmjs.com/package/vee-validate)パッケージと[@vee-validate](https://github.com/logaretm/vee-validate/tree/main/packages)以下のパッケージをグループ化する。

### lockFileMaintenance.json

ロックファイルのメンテナンスについての設定。
スケジュールを毎月1日の9:00から21:00に実行し，自動でマージする。

### pin.json

pinについての設定。
スケジュールを[schedule:daily](https://docs.renovatebot.com/presets-schedule/#scheduledaily)に設定し，自動でマージする。

### reviewer.json

レビュアーを [@hiroxto](https://github.com/hiroxto) に設定する。

### schedule.json

アップデートのスケジュールを設定。
日本時間の毎週月曜日の9:00から21:00に実行するように設定。


## 設定を上書きする

`renovate.json`内で上書きする。

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

プリセットの一部を読み込みたくない時は`ignorePresets`を使う。

```json
{
    "$schema": "https://docs.renovatebot.com/renovate-schema.json",
    "extends": [
        "github>hiroxto/renovate-config"
    ],
    "ignorePresets": [
        "github>hiroxto/renovate-config:schedule"
    ]
}
```
