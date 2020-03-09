![Image](https://github.com/AnthonyQi88/Linux/blob/master/Images/penguin.jpg)

# コマンド簡単説明
番号|コマンド
---|---
0001| wc
0002| cut


# コマンド説明

## 0001 wc
短いオプション|長いオプション|意味
---|---|---
-c|	--bytes	      |バイト数を表示する
-m|	--chars	      |文字数を表示する（マルチバイト文字に対応）
-l|	--lines				|改行の数を表示する
-w|	--words				|単語数を表示する
-L|	--max-line-length	|最も長い行の長さを表示する

--files0-from=リスト	NULL文字で区切られたファイル名のリストを指定する（「--files0-from=- 」とした場合は、ファイル名を標準入力から読み込む）

## 0002 cut
cutはテキストファイルを横方向に分割するコマンドだ。
csv(comma-separated values）データなどの一覧表から、必要な項目だけを抜き出す時に使う。

### 出力指定オプション（いずれか1つを必ず指定）
短いオプション|	長いオプション|	意味
---|---|---
-b| 出力リスト	--bytes=出力リスト	      |切り出す位置のリストをバイト数で指定する
-c| 出力リスト	--characters=出力リスト	|切り出す位置のリストを文字数で指定する
-f| 出力リスト	--fields=出力リスト	    |切り出す位置のリストをタブ区切りのフィールドで指定する（区切り文字は「-d」オプションで変更可能）

### リストの指定方法
指定	|意味
---|---
N	  |N番目のバイト、文字またはフィールド（行頭を1とする）
N-M	|N番目からM番目まで
N-	|N番目から行末まで
-M	|頭からM番目まで

### その他の主なオプション
短いオプション|	長いオプション	     		|意味
---|---|---
-d |--delimiter=文字			|フィールドの区切り文字として、タブの代わりに使用する文字を指定する（1文字のみ）**自定义分割字符，默认为制表符**
同上|--output-delimiter=文字列	|出力の区切り文字として使用する文字列を指定する（1文字以上が使用可能。デフォルトでは入力の区切り文字を使用）
-s |--only-delimited			|区切り文字を含まない行を出力しない
同上|--complement				|出力指定した箇所以外を出力する

デフォルトの区切り文字は「タブ（Tab）」です。区切り文字を変えたい場合は「-d」または「--delim=」で指定します。使用できるのは「,」など、1文字に限られます。空白の場合は「--delim=" "」のように指定します。
### 实验证明
```shell
[anthony@localhost Documents]$ cat cut_test.txt   #原始文件
No Name Mark Percent
1 LISA 100 99 
2 ALICE 88 89 
[anthony@localhost Documents]$ cut -f2,4 cut_test.txt #只看第2和4field的内容
Name Percent
LISA 99
ALICE 89
[anthony@localhost Documents]$ cut -f3 --complement cut_test.txt #除了第3filed的内容都看
No Name Percent
1 LISA 99 
2 ALICE 89 
[anthony@localhost Documents]$ cut -f1,3 --output-delimiter=";" cut_test.txt #把分割符号从默认的制表符换成指定的；
No;Mark
1;100
2;88

[anthony@localhost Documents]$ cat /etc/passwd | head -2  #原始文件
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
[anthony@localhost Documents]$ cut -f 1,7 --delimiter=":" /etc/passwd | head -2 #以冒号为指定分割符号进行数据分割并取出1和7位内容
root:/bin/bash
bin:/sbin/nologin
[anthony@localhost Documents]$ cut -f 1,7 --delimiter=":" --output-delimiter="------" /etc/passwd | head -2 
#以冒号做分隔符并指定6个横线作为输出分隔符
root------/bin/bash
bin------/sbin/nologin

[anthony@localhost Documents]$ cat cut_test2.txt #原始文件
/var/log/cli
test1/test2/test3/
hello world
[anthony@localhost Documents]$ cut -d'/' -f2 cut_test2.txt #以斜杠为分割字符并取出第二个元素，没有斜杠的内容也会被打印出来
var
test2
hello world
[anthony@localhost Documents]$ cut -d'/' -f2 -s --only-delimited cut_test2.txt #只打印有/部分的内容
var
test2
[anthony@localhost Documents]$ cut -d'/' -f2 -s --complement cut_test2.txt #只选取有斜杠的地方并扔掉f2的内容
/log/cli
test1/test3/
```







