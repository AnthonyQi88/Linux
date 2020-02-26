  # 数组
  
  ## 小小笔记
  
  1. echo ${my_array}只能打印出这个数组里面第一个元素(下标为0)，打印全部元素一定要加[@]也就是echo ${my_array[@]}。
  2. 想查看全部元素的话 **[@]和[\*]** 都可以使用。
  
 1. **添加数组元素**
  
  - 可以以索引为单位依次向数组中添加
```
[root@localhost Documents]# my_array[1]="abc"
[root@localhost Documents]# my_array[2]="bbb"
```

- 也可以用read -a的方式交互式的进行添加。

```shell
[root@localhost Documents]# read -a my_array1
first second third last
[root@localhost Documents]# echo ${my_array1}
first
[root@localhost Documents]# echo ${my_array1[@]}
first second third last
```

- 当然也可以直接投入。

```shell
[root@localhost Documents]# my_array2=(first second third)
[root@localhost Documents]# echo ${my_array2[@]}
first second third
```

2. **查看数组元素**

```
[root@localhost Documents]# echo ${my_array[1]}
abc
[root@localhost Documents]# echo ${my_array[@]}
abc bbb ccc
[root@localhost Documents]# echo ${my_array1[*]}
first second third last
[root@localhost Documents]# echo "${my_array[1]}, ${my_array[2]}"
abc, bbb
```

3. **查看数组个数**
```
[root@localhost Documents]# echo ${#my_array[@]}
3

[root@localhost Documents]# echo ${#my_array1[*]}
4


```
4. **查看数组中最后的元素**
```
[root@localhost Documents]# echo ${my_array1[${#my_array1[*]}-1]}
last
```

  

  
  
  
