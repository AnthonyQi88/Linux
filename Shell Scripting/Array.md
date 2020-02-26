  # 数组
  
 1. **添加数组元素**
  
```
[root@localhost Documents]# my_array[1]="abc"
[root@localhost Documents]# my_array[2]="bbb"
[root@localhost Documents]# my_array[3]="ccc"
```

2. **查看数组元素**

```
[root@localhost Documents]# echo ${my_array[1]}
abc
[root@localhost Documents]# echo ${my_array[@]}
abc bbb ccc
[root@localhost Documents]# echo "${my_array[1]}, ${my_array[2]}"
abc, bbb
```

3. **查看数组个数**
```
[root@localhost Documents]# echo ${#my_array[@]}
3

```
4. **查看数组中最后的元素**
```
[root@localhost Documents]# echo ${my_array[${#my_array}-1]}
ccc
```

5. **Arrays are zero-based: the first element is indexed with the number 0.**
  
6. 
  
  
  
