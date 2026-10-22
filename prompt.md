# 自動チェックテンプレートの作成
各DUT（インバータ回路、inverter_base.gds）は、ユーザから投稿される予定です。
そこで、DUTのGDSをチェックするサイトを作りたいと思います。

https://github.com/OpenSUSI/TR-1um_MPW_template を参考にして、LVSとDRCをgithub actionsで実行するプロジェクトをRISC-V-Day_MPW_templateというディレクトリに作ってください。MDPはいらないので削除してください。
（すでに、TR-1um_MPW_templateにclone済みです。）

利用するPDKは、 https://github.com/ishi-kai/gf180mcuD でお願いします。すでに、gf180mcuDにclone済みですので、ローカルの試験はこれを利用してください。
本番は、 https://github.com/ishi-kai/gf180mcuD を利用する前提でOKです。


## 仕様
- srcに、GDSファイルをアップロードしてもらう。
- GDSファイルやTopセルは、DUT名で"inv_dut_NNN"として、info.yamlの  top_cell: "inv_dut_NNN"は削除してください。
- LVS用のファイルは事前に全回路分を準備して、LVSディレクトリに入れておいてください。
- LVS用のファイルはcdlでも構いません。
- インバータ回路の情報は、dut_params.csvを参考にしてください。
- 

### PDKの改造
- gf180mcuDディレクトリ内は変更してしまってよいです。
- 密度エラーは出ないようにしてください。
- inverter_base.gdsのPR_BNDRYレイヤーが「中心座標：x=0, y=0」「縦：50um x 横：20um」以外に変更されていたら、エラーが出るようにしてください。
- inverter_base.gdsのPR_BNDRYレイヤーエリア外に何かがレイアウトされている場合は、エラーが出るようにしてください。
- inverter_base.gdsのPR_BNDRYレイヤーエリア内の、VDD,VSS,A,QラベルとMetal1レイヤーが変更されている場合もエラーが出るようにしてください。
