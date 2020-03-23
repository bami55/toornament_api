# Rankings

特定のステージタイプ（Round-robin Groups, League and Swiss System）では、ランキングが計算される。このランキングには、試合とステージ設定に記載されているランキング設定が必要。これらの設定は、Calculators（ポイントの計算方法）とタイブレークの2つのカテゴリに分かれている。

## Calculators

Calculatorsは、競技者にポイントがどのように付与されるかを記述する。複数のCalculatorが設定されている場合、各Calculatorのポイントの合計が競技者に与えられる。Calculatorsの順序は、結果を変更しない。

Calculatorsを設定してポイントを付与する方法の詳細については、ヘルプセンターの[Points system](https://help.toornament.com/matches/new-ways-to-award-points)の説明を参照。

ステージ設定では、Calculatorの設定を含む配列でCalculatorsが設定されている。

```json
[
    { "name": "calculator name", "options": options },
    { "name": "calculator name", "options": options },
    ...
]
```

|NAME|OPTIONS|
|-|-|
|match_bye_points|{"bye": integer}|
|match_result_forfeit_penalties|{"forfeit": integer}|
|match_set_result_forfeit_penalties|{"forfeit": integer}|
|match_result_points|{"win": integer, "draw": integer, "loss": integer}|
|match_score_points|{}|
|match_game_result_points|{"win": integer, "draw": integer, "loss": integer}|

Example

```json
[
    {
        "name": "match_result_points",
        "options": {
            "win": 2,
            "draw": 1,
            "loss": 0
        }
    },
    {
        "name": "match_bye_points",
        "options": {
            "bye": 1
        }
    }
]
```

## Tiebreakers

Tiebreakersは、同じポイント数を持つ競技者同士の同点を処理する方法を設定する。Tiebreakersの順番は**重要**。

特定のTiebreakersがどのように動作するかについては、ヘルプセンターの [Tiebreakers](https://help.toornament.com/matches/the-tiebreakers) のドキュメントを参照。

Tiebreakersの設定は、ステージ設定でTiebreakerの設定を含む配列で行う。ステージタイプの性質上、設定しても無意味な設定値もあるため、ステージタイプによっては利用できないTiebreakersもある。

```json
[
    { "name": "tiebreaker name", "options": options },
    { "name": "tiebreaker name", "options": options },
    ...
]
```

|NAME|OPTIONS|
|-|-|
|buchholz|{}|
|cumulative_opponents|{}|
|cumulative|{}|
|manual|{}|
|match_result_head_to_head|{}|
|match_result_overall|{}|
|match_forfeit_head_to_head|{}|
|match_forfeit_overall|{}|
|match_score_against_head_to_head|{}|
|match_score_against_overall|{}|
|match_score_difference_head_to_head|{}|
|match_score_difference_overall|{}|
|match_score_for_head_to_head|{}|
|match_score_for_overall|{}|
|median_buchholz|{}|
|played_least|{}|
|played_most|{}|
|points_head_to_head|{}|
|points_overall|{}|
|random|{}|

Example

```json
[
    {
        "name": "points_overall",
        "options": []
    },
    {
        "name": "match_result_head_to_head",
        "options": []
    }
]
```
