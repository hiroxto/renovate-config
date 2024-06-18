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

## デフォルトで読み込まれる設定

`extends` で `"github>hiroxto/renovate-config"` を指定した場合， default.json が読み込まれる。
default.json で設定済みの項目は以下の通り。

### Renovateのプリセット

- [config:recommended](https://docs.renovatebot.com/presets-config/#configrecommended)
- [:enableRenovate](https://docs.renovatebot.com/presets-default/#enablerenovate)
- [:timezone(Asia/Tokyo)](https://docs.renovatebot.com/presets-default/#timezonearg0)
    - タイムゾーンを Asia/Tokyo にする。
- [:disableDependencyDashboard](https://docs.renovatebot.com/presets-default/#disabledependencydashboard)
    - ダッシュボードを無効化する。

### defaultSchedule.json

アップデートのスケジュールを設定。
日本時間の第3月曜日の9:00から21:00に実行するように設定。

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

## デフォルトでは読み込まれないプリセット

作成済みではあるが default.json には入れていないプリセット。
利用する際は，以下の様に `extends` で明示的に指定する必要がある。

```json
{
    "$schema": "https://docs.renovatebot.com/renovate-schema.json",
    "extends": [
        "github>hiroxto/renovate-config:gitFlow"
    ]
}
```

### gitFlow.json

git-flow向けにベースブランチをdevelopに設定する。

### reviewer.json

レビュアーを [@hiroxto](https://github.com/hiroxto) に設定する。

### scheduleDaily.json

アップデートのスケジュールを日本時間の平日の9:00から21:00に実行するように設定。

### scheduleWeeklyMonday.json

アップデートのスケジュールを設定。
日本時間の毎週月曜日の9:00から21:00に実行するように設定。
旧デフォルトスケジュール。

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

default.json で読み込まれるプリセットの一部を読み込みたくない時は `ignorePresets` を使う。

```json
{
    "$schema": "https://docs.renovatebot.com/renovate-schema.json",
    "extends": [
        "github>hiroxto/renovate-config"
    ],
    "ignorePresets": [
        "github>hiroxto/renovate-config:defaultSchedule"
    ]
}
```
