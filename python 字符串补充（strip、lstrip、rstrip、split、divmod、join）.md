# strip、lstrip、rstrip使用方法：
**字符串变量名.strip('指定字符')
字符串变量名.lstrip('指定字符')
字符串变量名.rstrip('指定字符')**

三个函数都可传入一个参数，指定要去除的首尾字符；strip用于去除字符串的首尾字符，lstrip用于去除左边的字符，rstrip用于去除右边的字符；三个函数若没有设置消去什么都默认为消去空格。
注意的是，传入的字符串依次被去除相应位置上，参数中出现的字符（只要相符合就行），直到字符串内相应位置再无含相应的字符就停止。生成的是一个新字符串，原字符串不改变。
``` python
>>> a='iii have a little'
>>> print(a.strip('ie'))     
 have a littl
>>> print(a.lstrip('ie'))
 have a little
>>> print(a.rstrip('ie'))     
iii have a littl
>>> a
'iii have a little'
```
# split
**字符串变量名.split('指定字符')**
用于让字符串按指定字符分割（注意只能指定一个字符），分割n次（没有指定则默认有相应的字符出现就分割），并将分割完成的字符串赋给新的n+1个变量（注意必须是n+1个，不然会默认全部给第一个）。
```python
>>> a=('www.baidu.com')
>>> b=a.split('.')
>>> print(b)
['www', 'baidu', 'com']
>>> c=a.split('.',1)      #被赋予的变量数不是n+1个时
>>> print(c)
['www', 'baidu.com']
>>> x, y=a.split('.', 1)
>>> print(x,y)
www baidu,com
>>> print(a)      #原变量不会被改变
www.baidu.com
```
该函数也可以用于提取字符串中的部分片段。
```python
>>> a.split("[")[1].split("]")        #在前面取‘[’切割完部分的右边，这个基础上以‘]’为标志再切割
['1,2,3,4', 'aaaaaa']
>>> a.split("[")[1].split("]")[0]        #提取分割完部分的左边元素（这里的[1]、[0]表示的是位置；或者说是第一个、第零个）
'1,2,3,4'
>>> a.split("[")[1].split("]")[0].split(",")         #再提取后的按“,”分割
['1', '2', '3', '4']
```
整合来看就可以很便捷的化简为：
```python
>>> a="ooooo[1,2,3,4]aaaaaa"
>>> b=a.split("[")[1].split("]")[0].split(",")      #这里的1和0表示的不是次数，而是位置：取符号位置的右/左
>>> print(b)
['1', '2', '3', '4']
```
## divmod()
变量=divmod(被除数，除数)
将商、余数以一个元组的形式传给变量。
```python
>>> a=divmod(8,3)      #传给一个变量
>>> a
(2,2)
>>> x,y=divmod(8,3)      #传给两个变量
>>> print(x,y)
2 2
```
## join()
 '连接符'.join(列表\元组变量)
把一个列表、元组中所有的元素用设置的分隔符连接起来，**但限于元素是字符型**。
```python
>>> a=['1','2','3']
>>> ",".join(a)
'1,2,3'
>>> b=[1,2,3]
>>> ','.join(b)
Traceback (most recent call last):
  File "<pyshell#50>", line 1, in <module>
    '|'.join(c)
TypeError: sequence item 0: expected str instance, int found
```