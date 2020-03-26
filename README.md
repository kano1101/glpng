# glpng導入アシスト

glpngで調べてもmacに導入するための情報に困ったため、まとめさせていただきました。


## 使用方法

### 基本操作

```
$ cd ~/'作業用ディレクトリ'
$ git clone git@github.com:kano1101/glpng.git
$ cd glpng/src
$ make
$ cd ../
$ mv lib/libglpng.a ~/Desktop # お好きな場所へどうぞ
```

### 応用操作 - 適所へシンボリックリンク配置シェルスクリプトの実行
簡単なシンボリックリンクの作成シェルスクリプトを用意しました。
（警告）実践前に、Time Machineなどであらかじめバックアップを取った上、自己責任にておこなってください。
　　　　作者はいかなる場合にも責任は負いかねます。
```
$ cd ~/'作業用ディレクトリ'/glpng
$ chmod 775 setup.sh
$ ./setup.sh # シンボリックリンクを配置完了
```

これで設定完了です。
コンパイルオプションやMakefileで
```
-lglpng
```
を指定することにより、clangなどのコンパイラがビルド時に読みに行ってくれるようになります。

### 参考までにMakefile
こちらも自己責任でお願いします。
```
CC = clang++

CCFLAGS = -Wall -Wextra -c -std=c++11
LDFLAGS = -lglfw -lglpng -framework OpenGL

SourceDir = src
BuildDir = build
BinDir = bin
ProductName = Sample
UnixExecDir = $(BinDir)/unix-exec
UnixExec = $(UnixExecDir)/$(ProductName)

ResourcesDir = resc
Images = $(wildcard $(ResourcesDir)/imgs/*)

Sources = $(wildcard src/*.cpp)

Objects = $(patsubst $(SourceDir)/%.cpp,$(BuildDir)/%.o,$(Sources)) 


all: $(UnixExec)


$(UnixExec): $(Objects) $(Images)
	$(CC) $(LDFLAGS) $(Objects) -o $(UnixExec)
	cp $(Images) $(UnixExecDir)

$(Objects): $(BuildDir)/%.o: $(SourceDir)/%.cpp 
	$(CC) $(CCFLAGS) $< -o $@

test:
	cd $(UnixExecDir); ./$(ProductName)

.PHONY: clean
clean:
	rm -f $(BuildDir)/*o 
	rm -rf $(UnixExecDir)/*
```


## 著作権表記
このリポジトリで扱うライブラリglpngの著作者やこれに関わる全ての方に敬意を払い、心からLove&Thanksの思いを伝えたいと思います。
改めて、この場を借りてお礼をさせていただきます。本当にありがとうございます。

## 参考URL

### ZIPファイルの参照先とサンプルコード
https://faithandbrave.hateblo.jp/entry/20090120/1232433164

### ZIPファイルのダウンロード場所
https://openports.se/graphics/glpng

### 本作の開発要領参考元
https://tech.actindi.net/2010/03/17/3477747671

