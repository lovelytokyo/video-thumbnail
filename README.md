# 概要
Pararell execution test Of Video thumbnail generator。
[動画からサムネイルを生成するpythonプログラム](git@github.com:flavioribeiro/video-thumbnail-generator.git)を
並列実行してCPU使用率を観測するため。


## 実行

諸般の事情 (Global Interpreter Lock) により、Pythonでは Thread並列化による高速化はできないためProcess並列化する
4つのプロセスを立ち上げて１０００回サムネイル生成処理を行う。
 
- Run
  - /path/to/time python mutiprocess.py {process数} {動画数}
  - `/path/to/time python mutiprocess.py 4 1000`
 

## 実行環境

- 機種名：	MacBook Pro
- プロセッサ名：	Intel Core i7
- プロセッサ速度：	2 GHz
- プロセッサの個数：	1
- コアの総数：	4

## 結果
- ３０個の動画を8プロセスたちあげる
→CPU７０〜８０％　実行時間：40sec

- １０００個の動画を８プロセスたちあげる
→CPU７５〜８５％　実行時間：1093.41sec 18分　１本辺り約１秒

- １０００個の動画を４プロセスたちあげる
→CPUが４５~６５％　実行時間：2128.97sec 35分　１本辺り約２秒

## 課題
progressbarを表示しないようにしたらもっと早くなるかも

## 参考
http://qiita.com/yubais/items/5a9d91fe03fe715b21d0