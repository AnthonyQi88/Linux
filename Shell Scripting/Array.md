# 数组
## 小小笔记
编号|快速提示
---|---
01|echo ${my_array}只能打印出这个数组里面第一个元素(下标为0)，打印全部元素一定要加[@]也就是echo ${my_array[@]}。
02|想查看全部元素的话 **[@]和[\*]** 都可以使用。
03|echo ${my_array2[${#my_array2[@]}-1]}可以用来查看数组my_array2的最后一个元素。


# 目录

编号|内容
---|---
1000|添加数组元素
1001|以索引为单位
1002|用read -a进行交互式添加
1003|用等号一口气进行大量投入
<--->|<--->
2000|查看数组
2001|查看数组个数
2001|查看数组个数最后的元素


# 正文

## 1001 添加数组元素
  
### 1001 可以以索引为单位依次向数组中添加
```
[root@localhost Documents]# my_array[1]="abc"
[root@localhost Documents]# my_array[2]="bbb"
```

### 1002 也可以用read -a的方式交互式的进行添加。

```shell
[root@localhost Documents]# read -a my_array1
first second third last
[root@localhost Documents]# echo ${my_array1}
first
[root@localhost Documents]# echo ${my_array1[@]}
first second third last
```

### 1003 当然也可以直接用等号进行投入。

```shell
[root@localhost Documents]# my_array2=(first second third)
[root@localhost Documents]# echo ${my_array2[@]}
first second third
```

## 2000 查看数组
```
[root@localhost Documents]# echo ${my_array[1]}  #查看下标为1的元素
abc
[root@localhost Documents]# echo ${my_array[@]}  #查看数组内全部元素
abc bbb ccc
[root@localhost Documents]# echo ${my_array1[*]}  #查看数组内全部元素
first second third last
[root@localhost Documents]# echo "${my_array[1]}, ${my_array[2]}"  #连续查看两个指定下标的元素
abc, bbb
```
### 2001 查看数组个数
```
[root@localhost Documents]# echo ${#my_array[@]}
3
[root@localhost Documents]# echo ${#my_array1[*]}
4
```
### 2002查看数组中最后的元素
```
[root@localhost Documents]# echo ${my_array1[${#my_array1[*]}-1]}
last
```

  

  
  
  
