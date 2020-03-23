# 概要

## Tournament

参加者は`Participant`として定義される。

トーナメントは下記の構成となっている。

- Group
- Round
- Bracket
- Ranking
- Match

試合は、`Games`または`Match Games`と呼ばれる試合のサブセットでさらに詳細に分けられる。

## Participant

参加者はトーナメントに関連付けられている。

複数のトーナメントに参加する場合、各トーナメントごとにそれぞれ別のIDが振られる。

## Stage

10種類用意されている。

- Single Elimination
- Double Elimination
- Gauntlet
- Round-Robin Groups
- Bracket Groups
- League
- Swiss System
- (Free-For-All)Simple
- (Free-For-All)Single Elimination
- (Free-For-All)Bracket Groups

それぞれのStageには、参加者間の試合をアレンジする独自の方法がある。そのタイプによっては、StageにはGroup、Round、Match、Bracket、Rankingなどのサブ要素が含まれている場合がある。

## Group

Groupとは、通常は参加者の一部のみが参加するStageの一部を表す。ほとんどの場合、Groupごとに参加者が分かれるため、同時にプレイすることができる。しかし、予選＆決勝などに分かれている場合、別のGroupの結果を待たなければならないこともある。

Stageの種類によっては、Groupを必要としないものもある。その場合でも、他のStageの構成と同じように、1つのGroupをプレースホルダとして作成する。（Groupが必要ないようなケースでもGroupが作られる。）

## Round

Roundは、Group内の1試合に相当する。Roundの目的は、必要に応じてすべての参加者が同時にプレーできるステップを提供すること。

## Bracket

Bracketとは、試合の結果（勝敗）によって参加者が次にどこに行くかが決まる競技の一種。BracketのMatchは、Bracket間で接続されており、多くの場合、ツリーとして表されます。

## Ranking

Rankingとは試合の結果が参加者にポイントを与える報酬のタイプの競争を表す。StageまたはGroupが完了すると、Rankingを使用して、Stageの参加者の最終的な順位が決定される。

## Match

マッチとは、1人以上の参加者が参加する小規模な構造化されたプレーのことである。これらの参加者は、試合形式と、場合によってはプレーの小さなステップ(ゲームやマッチゲームなど)に従って、お互いに対戦する。最後に、結果は試合形式によって定義される。

試合に参加する参加者の数に応じて、結果は異なる方法で計算される。参加者が2人のみの場合、それは決闘と呼ばれ、結果は勝敗で表される。参加者が2人以上の場合は`ffa`と型付けされ、結果は順位で表示される。

マッチには対戦相手が含まれる。対戦相手には番号と、参加者のスコアや結果、その他の試合情報などの試合関連データが含まれている。
