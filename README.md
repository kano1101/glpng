# glpng導入アシスト

glpngで調べてもmacに導入するための情報に困ったため、まとめさせていただきました。


## 使用方法

### 基本準備操作

```
$ cd ~/'作業用ディレクトリ'
$ git clone git@github.com:kano1101/glpng.git
$ cd glpng/src
$ make
$ cd ../
$ mv lib/libglpng.a ~/Desktop # お好きな場所へどうぞ
```

### 応用操作 - 適所へシンボリックリンク配置シェルスクリプトの実行
Time Machineなどであらかじめバックアップを取った上、自己責任にておこなってください。
簡単なシンボリックリンクの作成シェルスクリプトを用意しました。
```
$ cd ~/'作業用ディレクトリ'/glpng
$ chmod 775 setup.sh
$ ./setup.sh # 
```
これで設定完了です。
clangなどのコンパイル時に読みに行ってくれるようになります。


## 謝辞
glpngに関わる全ての人に愛と感謝を伝えます。
良きプログラムライフを。


## 参考URL

### ZIPファイルの参照先とサンプルコード
https://faithandbrave.hateblo.jp/entry/20090120/1232433164

### ZIPファイルのダウンロード場所
https://openports.se/graphics/glpng

### 本作の開発要領参考元
https://tech.actindi.net/2010/03/17/3477747671

