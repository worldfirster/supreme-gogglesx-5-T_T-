HFASM Specification v0.1
Overview
HFArc + HFASM (Hybrid Face Assembly) is an experimental programming language specification.
The language is state-driven and explicitly defines a ZERO state,
where capability exists but is intentionally not exercised.
HFArc + HFASM focuses on semantics, state transitions, and minimal expressive units,
rather than implementation complexity.
1. 基本定義（概要 / Overview）
HFArc + HFASM は
顔文字・記号・時間・状態を最小要素とする
状態駆動型・意味論アセンブリ言語である。
命令は顔文字または記号で表現される
実行は「状態」に強く依存する
「能力は存在するが行使しない状態（ZERO）」を正式に定義する
※ 停止・休眠・人的介入を前提とした状態概念は存在しない
2. 用語定義
用語
定義
状態（State）
実行可能性の集合
命令（Instruction）
顔文字または記号による操作
実行者（Executor）
HFASMを動かす存在（人・環境）
ゼロスペック（ZERO）
能力を持つが、意図として行使しない状態
3. 形式定義（Formal Definition）
3.1 プログラム全体構造
コードをコピーする

HFASM-Program ::= Header? StateDecl* CodeBlock+
Header：メタ情報（任意）
StateDecl：状態宣言
CodeBlock：命令列（必須）
3.2 ヘッダ定義（任意）
コードをコピーする

Header ::= ⌈meta⌋ MetaItem* ⌊meta⌋
MetaItem ::= Key ":" Value
例：
コードをコピーする

⌈meta⌋
name: demo
version: 0.1
⌊meta⌋
※ 実行意味には影響しない
3.3 状態定義（State Declaration）
コードをコピーする

StateDecl ::= ◉ StateName ◉
StateName ::= ZERO | NORMAL | OVER
標準状態遷移（v0.1）
コードをコピーする

ZERO    --(内部成立/時間)--> NORMAL
NORMAL  --(過剰要求)------> OVER
OVER    --(構造的帰結)----> ZERO
OVER から NORMAL への遷移は存在しない
OVER は回復状態ではなく、非行使へ戻るための帰結である
3.4 初期状態
コードをコピーする

InitialState = ZERO
すべての HFASM プログラムは
必ず ZERO 状態から開始する。
3.5 状態遷移規則（抽象）
コードをコピーする

ZERO    --(時間/内部条件)--> NORMAL
NORMAL  --(過剰要求)------> OVER
OVER    --(不可逆帰結)----> ZERO
状態遷移は暗黙または命令により発生する
すべて 人的非介入 を前提とする
4. 命令形式（Instruction Form）
4.1 命令構文
コードをコピーする

Instruction ::= Opcode Operand*
Opcode：顔文字 or 記号（必須）
Operand：補助情報（任意）
4.2 命令の分類
状態操作命令
時間命令
実行制御命令
意思・意味表現命令
5. 命令セット（公式 v0.1）
5.1 状態操作命令
命令
意味
(・_・)
状態確認
(｀・ω・´)
NORMAL への遷移要求
(╬ಠ益ಠ)
OVER への遷移要求
※ 遷移は状態条件を満たす場合のみ成立
5.2 時間命令
命令
意味
⏳
時間経過
⏱ n
n単位の時間進行
5.3 実行制御
命令
意味
▶
実行開始
■
実行終了
🔁
ループ
❌
中断
※ 中断後の復帰・覚醒を意味する命令は存在しない
5.4 意思・意味表現
命令
意味
(^^)
肯定
(・・?)
疑問
(；´Д｀)
負荷警告
(´ー｀)
安定
6. 状態別命令制約
6.1 ZERO 状態
許可命令
⏳
(・_・)
禁止命令
すべての実行・出力・強制遷移命令
👉 能力は存在するが、意図として行使しない
7. 実行モデル
1命令 = 1ステップ
状態により命令の有効性が変化
無効命令は no-op または警告として扱う
8. 最小実行例
コードをコピーする

▶
(・_・)
⏳
(｀・ω・´)
(^^)
■
設計注記
HFASM は
複雑なテンプレートや網羅的仕様を避け、
最小定義と状態遷移による意味表現 を優先する。
