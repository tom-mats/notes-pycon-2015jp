# PythonとPyCoRAMでお手軽にFPGAシステムを開発してみよう

+ Pyverilog : Verlog HDL解析生成ツール
+ PyCoRam : IPコア高位設計フレームワーク
+ Veriloggen　:

も使用する．

## FPGAとは

### ヘテロジニアスコンピューティング

* multicore
+ GPGPU
* manycore (multicoreとGPGPUnotyyukann )
* FPGA Xlinx virtex-7(DDR3 DRAM)

最近は ARM + FPGAの構成が多い．ARM上でLinuxを動かして，FPGAの処理を監視する．
* バスも共有
* テストボードは10万円台からある
* Zynq

## ハードウェアの構成

+ HDLからコンパイルして回路情報のデータを生成する

## 高位合成ツール

* C, C++などの高級言語からHDLのコードを生成するツール，コンパイラ

### 商用ツール

* Xilinx Vivado HLS

* OpenCL系

### オープンソース

* LegUp : 性能があまり出ない
* Synthesijer : Java

## Pythonによる高位設計ツールPyCoRAM

* HDL上でスケジューリングするのは大変だけど，うまくしないと速度ができない

### PyCoRAM

* 抽象化していろいろなFPGAにも使えるようにしている
* データ制御をメインで書く
* データフローはVerlog HDLで行っている

## Pythonの抽象構文木(AST)

PythonからHDLに変換するには抽象構文木を使う

### VisitorパターンでASTをたどる

### Pyvelilog

Pyverilog : Verilogの解析生成ツール

+ Verlilogの構文解析
* データフロー解析
+ 制御フロー解析
* Pythonから HDLを生成
  + 少し使いにくい
  + Veriloggen

### Veriloggen

+ PythonからHDLを設計する
+ Verilogのメタプログラミングができる

## 今後の高位合成ツール

* FPGAのオープンソースは少ない
   -> FPGA版のLLVMが欲しいな

# 質問

+
