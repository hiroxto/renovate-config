# renovate-config

Renovate の設定済みプリセット。

`renovate.json` の `extends` に設定して使う。

```json
{
  "extends": [
    "github>hiroxto/renovate-config"
  ]
}
```

プリセットについて詳しくは [Renovateのドキュメント](https://docs.renovatebot.com/config-presets/) を参照。

[Shareable Config Presets | Renovate Docs](https://docs.renovatebot.com/config-presets/)

## 設定済みの設定ファイル

### docker.json

Docker関連の設定。
`docker-compose`と`dockerfile`のアップデートを有効化するが，自動マージは全てオフに設定されている。

### groupJest.json

jestとts-jestをグループにする設定。

### groupLinters.json

Linter周りのグループ設定。
Renovate標準の`packages:linters`に加えて，`prettier`もLinterとしてグループ化する。

### lockFileMaintenance.json

ロックファイルのメンテナンスについての設定。
スケジュールを毎月1日の9:00から21:00に実行し，自動でマージする。

### pin.json

pinについての設定。
スケジュールを`schedule:daily`に設定し，自動でマージする。

### schedule.json

アップデートのスケジュールを設定。
日本時間の毎週月曜日の9:00から21:00に実行するように設定。

### update.json

パッケージのアップデートを設定。
設定しているマネージャーは以下の通り。

- bundler
- composer
- github-actions
- gomod
- npm

全てパッチアップデートのみを自動マージする。

## 設定を上書きする

プリセットの一部を読み込みたくない時は`ignorePresets`を使う。

```json
{
  "extends": [
    "github>hiroxto/renovate-config"
  ],
  "ignorePresets": [
    "github>hiroxto/renovate-config:schedule"
  ]
}
```

上書きしたいだけなら，`renovate.json`で上書きする。

```json
{
  "extends": [
    "github>hiroxto/renovate-config"
  ],
  "schedule": [
    "every weekend"
  ]
}
```
