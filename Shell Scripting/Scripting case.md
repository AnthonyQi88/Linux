# 实验索引
编号|实验内容
---|---
0001|连续输出a-g,1-10
0002|对于连续数组中的数字，输出偶数。 
0003|随机生成10个数，并筛选出最大值
0004|定义一个数组，数组中的元素是var/log/目录下所有以.log结尾的文件的名称；统计其下标为偶数的文件中的行数之和
0005|写一个函数可以计算加减乘



# 实验内容
## 0001 实现连续输出
```shell
[root@localhost Documents]# echo {a..g}    #连续输出a到g
a b c d e f g
[root@localhost Documents]# echo {1..10}   #连续输出1到10
1 2 3 4 5 6 7 8 9 10

[root@localhost Documents]# echo $(seq 1 10)
1 2 3 4 5 6 7 8 9 10
```
## 0002 输出连续数组中的偶数
实验题目：
1. In this exercise, you will need to loop through and print out all even numbers from the numbers list in the same order they are received. Don't print any numbers that come after 232 in the sequence.
```shell
NUMBERS=(222 2 3 3433 232 121 333 443)

for num in ${NUMBERS[@]}; do
	if [ $num == 232 ]; then
		break
	elif [ $(($num % 2)) == 0 ]; then
		echo $num
	fi
done
```
## 0003 随机生成十个数字，并筛选出最大值。
```shell
declare -a rand
declare -i max=0

for i in {1..10}; do
	rand[$i]=$RANDOM 
	echo "rand[$i]: ${rand[$i]}"
	[ ${rand[$i]} -gt $max ] && max=${rand[$i]}
done

echo "MAX_NUM: $max"
```
## 0004 定义一个数组，数组中的元素是var/log/目录下所有以.log结尾的文件的名称；统计其下标为偶数的文件中的行数之和
```shell
declare -a files
files=(/var/log/*.log)

declare -i lines=0

for i in $(seq 0 $[${#files[@]}-1]);do
    if [ $[$i%2] -eq 0 ];then
        let lines+=$(wc -l ${files[$i]} | cut -d' ' -f1)
    fi
done
echo "Lines: $lines"
```
## 0005 写一个函数 - Write a function called ENGLISH_CALC which can process sentences such as:'3 plus 5', '5 minus 1' or '4 times 6' and print the results as: '3 + 5 = 8', '5 - 1 = 4' or '4 * 6 = 24' respectively. 
```shell
function ENGLISH_CALC {
  a=$1
  b=$3
  signn=$2
  if [ $signn == "plus" ]; then
    echo "$a + $b = $(($a+$b))"
  elif [ $signn == "minus" ]; then
    echo "$a - $b = $(($a-$b))"
  elif [ $signn == "times" ]; then
    echo "$a * $b = $(($a*$b))"
  fi
}

# testing code
ENGLISH_CALC 3 plus 5
ENGLISH_CALC 5 minus 1
ENGLISH_CALC 4 times 6
```








