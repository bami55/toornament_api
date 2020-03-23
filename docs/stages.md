# Stages

## Single Elimination

Type: `single_elimination`

シングルエリミネーション。負けたら終わりのオーソドックスなトーナメント。

|Stage Settings||
|-|-|
|size [integer]|Stageに参加するParticipantの数|
|third_decider [boolean]|3位決定戦の有無|
|threshold [integer]|これ以上試合をしてはいけない時期を定義する数値。しきい値以下のシードを含むマッチは、そのマッチがその後のマッチで必要とされる場合を除き、Bracketから削除される (敗者のBracketなど)。|

## Double Elimination

Type: `double_elimination`

Stageは、勝者のBracketと敗者のBracketの2つのBracketに分かれている。勝者のBracketは、負けたことのない競技者のみを含むシングルエリミネーション。敗者Bracketには、一度負けた競技者のみが含まれる。最後に、両方のBracketの勝者の間でグランドファイナルが行われる。

|Stage Settings||
|-|-|
|size [integer]|Stageに参加するParticipantの数|
|skip_round1 [boolean]|勝者のBracketの最初のラウンドがプレイされるかどうか。このラウンドがプレイされない場合、競技者の一部は勝者のBracketで始まり、一部は敗者のBracketで始まる。|
|grand_final [string]]|グランドファイナルのタイプ："none"は、2つのBracketsの間にグランドファイナルがないことを意味する。 "simple"とは、グランドファイナルに1つの試合しかないことを意味し、"double"とは、敗者のBracketから来た競技者は2回勝たないと優勝できないことを意味する。|
|threshold [integer]|これ以上試合をしてはいけない時期を定義する数値。しきい値以下のシードを含むマッチは、そのマッチがその後のマッチで必要とされる場合を除き、Bracketから削除される (敗者のBracketなど)。|

## Bracket Groups

Type: `bracket_groups`

Bracket Groups Stageは、いくつかのGroupにStageがあり、各Groupには少数の競合者が含まれる小さなBracketが含まれる。プレイヤーは、あるGroupから別のGroupに移動しない。彼らは同じGroupでプレイし続ける。

|Stage Settings||
|-|-|
|size [integer]|Stageに参加するParticipantの数|
|nb_groups [integer]|グループ番号|
|bracket_type [string]]|各グループで使用されるBracketのタイプ："single"はシングルエリミネーションを表し、"double"はダブルエリミネーションを表す。|
|threshold [integer]|これ以上試合をしてはいけない時期を定義する数値。しきい値以下のシードを含むマッチは、そのマッチがその後のマッチで必要とされる場合を除き、Bracketから削除される (敗者のBracketなど)。|
|arrival [string]|Stageに到着した際に、グループ内のライバルを分散させるために使用される到着方法。（adjacent, sequential, snake, branch）|
|departure [string]|競技者がステージを離れるときに、グループからステージに競技者を再割り当てするために使用される出発方法。 "mirror"方式は、到着時に使用したのと同じ方式を再現する。default：mirror（adjacent, sequential, snake, branch, mirror）|

## Round robin groups

Type: `pools`

複数の小グループで構成されたステージのこと。各グループ総当たり形式で行う。

|Stage Settings||
|-|-|
|size [integer]|Stageに参加するParticipantの数|
|nb_groups [integer]|グループ番号|
|arrival [string]|Stageに到着した際に、グループ内のライバルを分散させるために使用される到着方法。（adjacent, sequential, snake, branch）|
|departure [string]|競技者がステージを離れるときに、グループからステージに競技者を再割り当てするために使用される出発方法。 "mirror"方式は、到着時に使用したのと同じ方式を再現する。default：mirror（adjacent, sequential, snake, branch, mirror）|
|pairing_method [string]|ペアリング方法は、プレイヤーがどのようにペアリングされるかを説明する。"manual"方式はペアリングを行わず、グループ設定で手動でペアリングを記述する。"standard"方式は、標準的なラウンドロビン方式を適用する。"double_standard"は標準方式を2回適用し、1回は通常方式、1回は逆方式とする。default："standard"（manual, standard, double_standard）|
|calculators [array]|ランキングの計算方式。デフォルトでは勝利：3、引分：1、敗北：0で計算される。Rankingの方で詳しく解説。|
|tiebreakers [array]|タイブレークの設定。Rankingの方で詳しく解説。|

|Group Settings||
|-|-|
|size [integer]|Groupに参加するParticipantの数|
|pairing_values [array]|このグループで使用されるペアリングが含まれている。ペアリング値は、それぞれがペアリングの配列を含むラウンドの配列で表される。ペアリングは、2つのシード番号を持つ配列で構成される。例: [[[1,2],[3,4],[5,6]],[[1,4],[2,5],[3,6]]]|

## Gauntlet

Type: `gauntlet`

ガントレットステージは、低いシードの参加者が高いシードの対戦相手と徐々に対戦するBracket。

|Stage Settings||
|-|-|
|size [integer]|Groupに参加するParticipantの数|

## League

Type: `league`

リーグステージは、大規模なグループが少ないステージです。各グループには、ステージ競技者のサブセットが含まれ、ラウンドロビン方式を使用して、総当たりを行う。

|Stage Settings||
|-|-|
|size [integer]|Stageに参加するParticipantの数|
|nb_groups [integer]|グループ番号|
|arrival [string]|Stageに到着した際に、グループ内のライバルを分散させるために使用される到着方法。（adjacent, sequential, snake, branch）|
|departure [string]|競技者がステージを離れるときに、グループからステージに競技者を再割り当てするために使用される出発方法。 "mirror"方式は、到着時に使用したのと同じ方式を再現する。default：mirror（adjacent, sequential, snake, branch, mirror）|
|pairing_method [string]|ペアリング方法は、プレイヤーがどのようにペアリングされるかを説明する。"manual"方式はペアリングを行わず、グループ設定で手動でペアリングを記述する。"standard"方式は、標準的なラウンドロビン方式を適用する。"double_standard"は標準方式を2回適用し、1回は通常方式、1回は逆方式とする。default："standard"（manual, standard, double_standard）|
|calculators [array]|ランキングの計算方式。デフォルトでは勝利：3、引分：1、敗北：0で計算される。Rankingの方で詳しく解説。|
|tiebreakers [array]|タイブレークの設定。Rankingの方で詳しく解説。|

|Group Settings||
|-|-|
|size [integer]|Groupに参加するParticipantの数|
|pairing_values [array]|このグループで使用されるペアリングが含まれている。ペアリング値は、それぞれがペアリングの配列を含むラウンドの配列で表される。ペアリングは、2つのシード番号を持つ配列で構成される。例: [[[1,2],[3,4],[5,6]],[[1,4],[2,5],[3,6]]]|

## Swiss System

Type: `swiss`

スイスラウンド方式を採用した単一グループのStage。

|Stage Settings||
|-|-|
|size [integer]|Stageに参加するParticipantの数|
|nb_groups [integer]|現在、単一のグループのみが許可されているため、値は「1」のみ。|
|arrival [string]|Stageに到着した際に、グループ内のライバルを分散させるために使用される到着方法。（adjacent, sequential, snake, branch）|
|departure [string]|競技者がステージを離れるときに、グループからステージに競技者を再割り当てするために使用される出発方法。 "mirror"方式は、到着時に使用したのと同じ方式を再現する。default：mirror（adjacent, sequential, snake, branch, mirror）|
|pairing_method [string]|ペアリング方法は、プレイヤーがどのようにペアリングされるかを説明する。"manual"方式はペアリングを行わず、グループ設定で手動でペアリングを記述する。"p_balanced"方式は、スコアグループ内で同じレベル差を使用してプレイヤーをペアにする。"p_opposite"方式はスコアグループ内のトップランクを優先することにより、プレイヤーをペアリングします。 "p_random"方式はスコアグループ内でランダムにペアになる。default："p_balanced"（manual, p_balanced, p_opposite, p_random）|
|calculators [array]|ランキングの計算方式。デフォルトでは勝利：2、引分：1、不戦勝：1、敗北：0で計算される。Rankingの方で詳しく解説。|
|tiebreakers [array]|タイブレークの設定。Rankingの方で詳しく解説。|

|Group Settings||
|-|-|
|size [integer]|Groupに参加するParticipantの数|

|Round Settings||
|-|-|
|size [integer]|Roundに参加するParticipantの数|
|pairing_values [array]|このラウンドで使用されるペアリングが含まれている。ペアリング値は、ペアリングの配列で表される。ペアリングは、2つのシード番号を持つ配列で構成される。手動のペアリング方法を使用する場合、有効なペアリングテーブルが含まれている必要がある。別のペアリング方法が使用される場合、ラウンドの作成時に計算されたペアリングが含まれる。例: [[1,2],[3,4],[5,6]]|

## Simple

Type: `simple`

Simpleステージは、1つまたは複数の試合があるステージ。1グループ＆1ラウンドのみ。マッチ間に関係はない。

|Stage Settings||
|-|-|
|size [integer]|Stageに参加するParticipantの数|
|match_type [string]|ステージの試合の種類。1vs1 か free for allのどちらかを選択。（duel, ffa）|
|nb_matches [integer]|ステージで利用できる試合数。|
|arrival [string]|Stageに到着した際に、グループ内のライバルを分散させるために使用される到着方法。default：sequential（adjacent, sequential, snake）|
|departure [string]|競技者がステージを離れるときに、グループからステージに競技者を再割り当てするために使用される出発方法。 "mirror"方式は、到着時に使用したのと同じ方式を再現する。default：mirror（adjacent, sequential, snake, branch, mirror）|

## Single Elimination FFA

Type: `ffa_single_elimination`

シングルエリミネーションFFAステージとは、競技者が試合ごとにランク付けされたブラケットのことです。上位の競技者のみが最後の試合までブラケットで進行します。

|Stage Settings||
|-|-|
|size [integer]|Stageに参加するParticipantの数|
|match_size [integer]|1試合あたりのプレイヤー数。|
|match_winners [integer]|1試合あたりの出場資格者数。|
|threshold [integer\|null]|これ以上試合をしてはいけない時期を定義する数値。しきい値以下のシードを含むマッチは、そのマッチがその後のマッチで必要とされる場合を除き、Bracketから削除される (敗者のBracketなど)。|

## Bracket Groups FFA

Type: `ffa_bracket_groups`

ブラケットグループ FFA ステージとは、複数のグループからなるステージのことで、競技者の数を減らした小さなブラケットを含むステージのこと。競技者は、1つのグループから別のグループに移動することはない。彼らは同じグループでプレーし続ける。

|Stage Settings||
|-|-|
|size [integer]|Stageに参加するParticipantの数|
|nb_groups [integer]|グループ番号|
|match_size [integer]|1試合あたりのプレイヤー数。|
|match_winners [integer]|1試合あたりの出場資格者数。|
|threshold [integer]|これ以上試合をしてはいけない時期を定義する数値。しきい値以下のシードを含むマッチは、そのマッチがその後のマッチで必要とされる場合を除き、Bracketから削除される (敗者のBracketなど)。|
|arrival [string]|Stageに到着した際に、グループ内のライバルを分散させるために使用される到着方法。（adjacent, sequential, snake）|
|departure [string]|競技者がステージを離れるときに、グループからステージに競技者を再割り当てするために使用される出発方法。 "mirror"方式は、到着時に使用したのと同じ方式を再現する。default：mirror（adjacent, sequential, snake, branch, mirror）|

> 「ペアリング」という単語が度々出てくるが、おそらく「対戦カード」という解釈で問題ないと思われる。
