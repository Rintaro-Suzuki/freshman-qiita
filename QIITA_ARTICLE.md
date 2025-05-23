# スタッフ体験会
SEパートへようこそ！

SEパートではスタッフ、選手がより自由に活動できるように、google document, google spreadsheet, google form, slack などのツールを横断して連携できるコードを書いたり、あったら便利な機能を詰め込んだアプリの開発をしたりしています。

今後は運動会に属しているという強みを活かし、スポーツ × IT を実現して選手の技術上達や戦術理解に役立つこと(例えばAIを使用して身体の動きや戦術を分析するなど...?)を考え、よりWarriorsの勝利に直結する仕事をしたいと考えています。

## なぜSEパートが必要なのか？
1. まだWarriros内には効率化できるところがたくさんあるから！<br>
SEパートに入ると、他のパートと話し合いを行う機会があります。そこでは他のパートから効率化したいけど手が回っていないことが挙がってきます。今もそのストックがあります。一緒に解決しましょう！

2. Warriorsの勝利に繋がりそうなのに活用できていないデータ・環境があるから！<br>
今までSAさんが貯めてきてくれたデータがあり、最先端の研究をしている大学に所属していますが、今はそのどちらも活かせていない状況です。みなさんの希望次第・行動次第でこれらの環境を活かして活動することができると思います！

この記事は、プログラミングの入門としてPythonを使ってシンプルなじゃんけんゲームを作りながら、プログラミングの基本概念を学ぶことを目的としています。

## プログラミングとは？
そもそもSEパートがやっているPCでのプログラミングとは、コンピュータに作業をさせるためにコンピュータにわかるように指示を出すことです。じゃんけんのようなシンプルなゲームでさえ、コンピュータに理解させるには、手順を追って指示を出す必要があります。
この記事も文字を打って画面に表示させるという一種のプログラミングです。すごいでしょー

## じゃんけんゲームを作ろう
それでは、Pythonでじゃんけんゲームを作っていきましょう。このゲームでは、プレイヤーがグー、パー、チョキのいずれかを選び、コンピュータがランダムに選んだ手と勝負します。

## 作業する環境
このスタッフ体験会では [Google Colaboratory](https://colab.research.google.com/?hl=ja) というブラウザ上でPythonを記述、実行できるサービスを使用します。このサービスを使うと、コードを動かせるソフトウェアをインストールする必要がありません。
使い方は、リンクを押してもらい、左上の「ファイル」-> 「ドライブの新しいノートブック」でpythonを書くためのNotebookを開くことができます。ここにコードを書いていきます。

## おすすめサイト
以下の説明ではわかりにくいところがあったときにおすすめのサイトをあげておきます。<br>
1. [Python早見表](https://chokkan.github.io/python/index.html)<br>
東京工業大学(現・東京科学大学)が作った、Pythonの基本的なコードが書かれたサイトです。項目ごとにまとまっているので、見やすいです。コードを書くのに困ったとき、Macなら [command] + F,Windowsなら [Ctrl] + Fのページ内検索も使えば、書き方の疑問が解決されると思います。<br>

2. [Python公式ドキュメント](https://docs.python.org/ja/3/)<br>
これを読めるのが一番理想です(公式なので...)。 検索機能を使って知りたい構文を入れれば公式の解説を読むことができます。

## 実際のコード
```python
# ======== モジュールのインポート ========
# モジュールとは簡単にいうと誰かが作ってみんなが使えるように残してくれた便利機能のことです。コード内に持ってくる(importする)ことによって使えるようにします。
import random
```

このゲームはプレーヤーがやめることを選択しない限り何回も遊ぶことを想定して作ります。なのであらかじめループ構造にしておく必要があります。
```python
# ======== 無限ループ ========
# while文は下の形で使われ、条件を満たす限り、「繰り返したい処理」を何度も行います
# while 条件式:
#     繰り返したい処理
while True:
```

### インデント
while以下の文はインデント(字下げ)をすることによって文頭にtabひとつ分のスペースを空けてコードを書いていかなければなりません。<br>
これは見やすさのためでもありますが、pythonに関してはインデントしないとコードが動かないためです。(インデントしなくても動く言語も多いですが...)

```python
# ======== ユーザーに手を選ばせる ========
# input関数が呼ばれるとキーボードによる入力を受け取ります。
# 括弧内の文字列は、ユーザーに表示されるメッセージです。
# 入力された値は、設定したuser_action という変数に保存されます。
    user_action = input("選択してください（グー、パー、チョキ）: ")

# ======== コンピュータの手の準備 ========
# リストとは、複数の値をまとめて保存できるデータ構造です。
# ここでは、コンピュータが選べる3つの選択肢をリストとして定義しています。
# リストの各項目は、カンマで区切られ、[] で囲まれています。
    possible_actions = ["グー", "パー", "チョキ"]

# ======== コンピュータが手を選択 ========
# random.choice() 関数は、リストからランダムに1つの要素を選びます。
# ここでは、possible_actions リストから1つの選択肢をランダムに選んで、
# computer_action という変数に保存しています。
    computer_action = random.choice(possible_actions)

# ======== 結果の表示 ========
# print() 関数は、画面に文字列を表示します。
# f"..." という書き方は「f-string」と呼ばれ、文字列の中に変数の値を埋め込むことができます。
# 変数は中括弧 {} で囲みます。
    print(f"あなたは{user_action}を選びました。コンピュータは{computer_action}を選びました。")
```

このコードでは：
1. randomモジュールをインポートしてコンピュータの選択をランダムする

2. input関数でユーザーの入力を受け取る

3. コンピュータがランダムに選択する

4. 両者の選択を表示する

という手段で画面に表示していきます。

### 勝敗判定のロジック
次に、勝敗を判定するロジックを追加します：

```python
# ======== 勝敗判定のロジック ========
# if-elif-else文は、条件に基づいて異なる処理を行うための構文です。見慣れない elif は else と if の組み合わせと考えると良いです。以下のように使います。
if 条件A:
    Aを満たす場合にする処理
elif 条件B:
    Aを満たさないが、Bを満たす場合にする処理
else:
    AもBも満たさない場合にする処理

# 条件が成立すれば、そのブロック(if, elif, else の次のインデントに書かれている)内のコードが実行されます。

# まず、引き分けのケースをチェックします。
# == は「等しい」という比較演算子です。(一つの = は「代入」という意味なので、等しいことは表しません。)

    if user_action == computer_action:
        print(f"両者とも{user_action}を選びました。引き分けです！")

# 引き分けでない場合は、ユーザーの選択ごとに勝敗を判定します。
# elif は「さもなくて、もし〜なら」という意味です。

    elif user_action == "グー":
        # ネストされたif文（入れ子になった条件分岐）で、コンピュータの選択に応じた結果を表示します。
        if computer_action == "チョキ":
            print("グーはチョキに勝ちます！あなたの勝ちです！")
        else:
        # コンピュータがチョキでなければ、パーです（残る選択肢はパーしかないため）
            print("パーはグーに勝ちます！あなたの負けです。")
    elif user_action == "パー":
        if computer_action == "グー":
            print("パーはグーに勝ちます！あなたの勝ちです！")
        else:
            print("チョキはパーに勝ちます！あなたの負けです。")
    elif user_action == "チョキ":
        if computer_action == "パー":
            print("チョキはパーに勝ちます！あなたの勝ちです！")
        else:
            print("グーはチョキに勝ちます！あなたの負けです。")
```

このコードでは条件分岐（if-elif-else文）を使って、じゃんけんのルールに従って勝敗を判定しています。

### ゲームを繰り返し遊べるようにする
最後に、ゲームを繰り返し遊べるようにループを追加しましょう：
```python
    play_again = input("もう一度プレイしますか？（はい/いいえ）: ")
    if play_again.lower() != "はい":
        print("ゲームを終了します。お疲れ様でした！")
        break
```

このコードでは while True でループを作成し、ユーザーが「終了」と入力するか、「もう一度プレイしますか？」の質問に「はい」以外で答えるまでゲームを続けます。

## ここで学んだプログラミングの基本概念
このじゃんけんゲームを通して、以下のプログラミングの基本概念を学びました：

1. 変数 - user_actionやcomputer_actionのように、データを保存するための「箱」<br>処理した結果などを後で使用する場合は変数を設定していれておきましょう！

2. データ型 - 文字列（"グー"など）やリスト（possible_actions）<br>
整数型(int), 浮動小数点型(float), ブール型(bool), 文字型(string)などの種類がある。

3. 条件分岐 - if-elif-else文を使った条件分岐<br>

4. ループ - while文を使った繰り返し処理<br>

5. 関数 - input()やrandom.choice()などの機能を呼び出す<br>

# 発展課題「ブラックジャックのCPUを作ろう」

## ブラックジャックのルール
プレイヤーとディーラー(運営)が戦うゲームで、21により近づけるようにカードを引き、近い方が勝ちというゲーム。ディーラーの挙動を作成します。<br>
主なゲーム内のアクションはチップのベットとカードのドローの選択<br>
カードが21を越えればburstで強制負けになります。<br>
基本は勝てばbetの2倍、引き分けならbetの返還、負けならbetが回収されます。<br>
カードの種類は A, 2, 3, 4, 5, 6, 7, 8, 9, 10, J, Q, K の 13種類<br>
Aは1または11(任意選択)、絵札(J, Q, K)は10として扱います。A + 絵札で21となりゲームの名を冠するBlack Jackという役になりbetの2.5倍を獲得できます<br>
詳しく知りたい方はBlack Jackのルールで調べてみてください。

1. トランプとプレイヤーの持ち金をセットしましょう
```python
#inputでプレイヤーの持ち金をplayer_moneyセットしよう
#トランプカードを格納した配列をtrump_cardに用意しよう。各スート(♠︎、❤︎、♣︎、♦︎)の1~13の52枚を使用します。以下を配列を使用してもらえれば大丈夫です。もっと効率よくゲームを進められる配列を考えついたらそちらを使ってもらって大丈夫です！
trunp_card = [♠A,♠2,♠3,♠4,♠5,♠6,♠7,♠8,♠9,♠10,♠J,♠Q,♠K,
♥A,♥2,♥3,♥4,♥5,♥6,♥7,♥8,♥9,♥10,♥J,♥Q,♥K,
♦A,♦2,♦3,♦4,♦5,♦6,♦7,♦8,♦9,♦10,♦J,♦Q,♦K,
♣A,♣2,♣3,♣4,♣5,♣6,♣7,♣8,♣9,♣10,♣J,♣Q,♣K]
```
2. カジノディーラーからの"place your bet"の合図でゲームが開始
```python
#input()を使用してbetしてその数を格納してみましょう
#今回はいくらでもbetできることにします。好きな数字をいれてください。
#入力された数は文字(string)なので数字にして新たな変数に格納してあげましょう。int()という関数を使用します
bet = input('bet金額: ')
bet_number = int(bet)
#これでnumber型になりました
#inputの後にno more betを表示しbetを締め切ります。print()という関数を使用しますが、調べる練習だと思って使い方を調べてみてください。
```
3. カジノディーラーがプレイヤーとディーラーに2枚ずつカードを配布する
```python
#プレーヤーが先に2枚引きます
#player_card,dealer_cardという配列にtrump_cardからランダムに選んだ2枚を入れてみよう
#カードは有限なので取り出したカードは元の配列から削除してください(調べてみてください)
#プレイヤーには自分の2枚のカードとディーラーの1枚目をprintで開示する
```
4. 自分のアクションを決める
自分のカードを見てカードを引く(hit)、番を終了する(stand)、betを2倍にする(Doubling Down)を決める。<br>
本当はもう少し詳しいルールがあるけど、今回はここまでにします。
```python
#前回のじゃんけんの手を決める時と同様にactionを決めさせてそれに応じてif文で条件分岐を作ろう
player_action = input()
possible_actions = []
if
    処理
```
5. ディーラーがアクションを行う
## CPUの戦略
CPUの戦略について考えます。
CPUは引いたカードの和が17を超えるまで引き、超えたら引くのをやめる。
```python
ディーラーの2枚目のカードを開示(print)
条件分岐する
ディーラーのアクションとドローの場合はそのカードも表示
```
6. 勝敗を判定する
```python
#引き分け、勝ち、負け、Black Jackの4つで条件分岐を行い、リターンしてplayer_moneyに加算する。
#最後はget_coinという変数に勝ち取ったお金をいれてください。
#勝敗とリターン(get_coin)を表示
print(f"勝ち: {get_coin}枚獲得")
#f"xxx{number}xxx"この書き方をすることでnumberを文字型に変更して文字と繋げて表示できる
```
7. ゲームを繰り返し遊べるようにする
最後に、前回と同様ゲームを繰り返し遊べるようにループを追加しましょう
```python
#最初と最後にwhileと終了条件を追加
```




