# Agent Skills

AIエージェント向けの自作の[スキル](https://agentskills.io/)をまとめるリポジトリです。

各スキルは `skills/<name>/SKILL.md` に置きます。実行に必要な補助ファイルは各スキルと一緒に配布します。

## スキル

| スキル | 用途 |
| --- | --- |
| [anki](skills/anki/SKILL.md) | Ankiで学習カードを設計・追加する |
| [design-it](skills/design-it/SKILL.md) | 利用者が求める体験を掘り下げる |
| [minus](skills/minus/SKILL.md) | 設計を見直して複雑さを減らす |
| [model-it](skills/model-it/SKILL.md) | 概念や因果関係を整理する |

## 開発

[mise](https://mise.jdx.dev/)でBunを導入し、テストを実行します。

```sh
mise install
mise exec -- bun test
```
