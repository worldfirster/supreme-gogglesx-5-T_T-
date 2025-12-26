HFA/ASMrc
本リポジトリでは、HFA/ASMrc を 設計思想・理論体系および実験的言語仕様 として扱います。
HFA/ASMrc（Hierarchical Framework Architecture / ASMrc）は、
顔文字や記号を 第一級命令 として扱う状態駆動型の実験的言語仕様
階層構造と最小定義を重視する 設計思想
異なるプログラム言語間の 意味互換（Semantic Compatibility） を可能にする仕様
を包含する総称です。
HFA/ASMrc は、階層構造を前提に、ソフトウェアやハードウェアの設計を 極端に簡潔な表現で扱う 個人発想（作成者：大野実）のフレームワークであり、HFA/ASMrc はプログラムや設計の “意味” を最小単位で扱い、状態遷移や副作用を明確に定義することで、異なる言語やシステム間での 比較・解析を可能にする思考実験的仕様 でもあります。
定義初出：2025年
Specification Version: v0.2
Documentation
このディレクトリには、HFA/ASMrc の正式仕様と設計文書を含みます。
spec/HFA-ASMrc-v0.2.md : 公式言語仕様 v0.2
kaomoji-instructions.md : 顔文字を第一級命令として定義した文書
spec/HFA-ASMrc-QMD-v0.x.md : Qi Men Dun Jia モデル（思考実験的拡張）
Design Note
HFA/ASMrc は 複雑なテンプレートや網羅的仕様を避ける
最小定義と状態遷移による意味表現 を優先
ZERO 状態を正式に定義し、意味が未確定な場合や他言語対応未確定の場合にも安全に扱う
Overview
状態駆動型
顔文字・記号を第一級命令
ZERO 状態：能力は存在するが、意図的に行使しない状態
Semantic Compatibility：異なる言語間での意味比較・解析を可能にする
最小単位表現：複雑なテンプレートや実装に依存せず、意味を最小単位で表現
Hierarchical Structure
HFA/ASMrc は 階層構造 により、超短命令でも意味を持たせます。
コードをコピーする

Program Level
├─ Header (optional)
├─ State Declaration (ZERO / NORMAL / OVER)
└─ CodeBlock
   ├─ Command Category (State / Time / Control / Expression)
   └─ Command (Opcode + Operand)
階層と状態 によって命令の有効性や副作用が自動解釈されます
Minimal Execution Example はこの階層と状態に従って意味を伝達します
Minimal Execution Example
コードをコピーする

▶ (・_・)       # Start execution
⏳ (｀・ω・´)    # Time progress
(^^)            # Affirmation / Request NORMAL transition
■               # End execution
1命令 = 1ステップ
状態による命令制約あり
無効命令は no-op または警告として扱う
Notes
ZERO 状態 は初期状態であり、能力はあるが行使しない
階層構造 により短い命令でも完全な意味を持たせられる
全プログラムは必ず ZERO 状態から開始
複雑なテンプレートや exhaustive specifications は意図的に避ける
Author
大野実
GitHub Account: worldfirster
