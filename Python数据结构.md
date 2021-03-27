## Python数据结构

### 列表(List)

`列表是有序集合，没有固定大小，能够保存任意数量任意类型的 Python 对象，语法为 [元素1, 元素2, ..., 元素n]。`

#### 1.列表创建

* 利用range()创建列表

```python
x = list(range(10))
print(x, type(x))
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] <class 'list'>
```

* 利用列表推到式创建列表（List Comprehension）

```python
x = [i for i in range(10)]
print(x, type(x))
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] <class 'list'>

x=[]
for i in range(10):
    x.append(i)
print(x, type(x))
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] <class 'list'>
```

​		注：list元素可以是任何对象，所保存的是对象的指针。

```python
a = [0] * 3
x = [a] * 4
print(x, type(x))
# [[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]] <class 'list'>

x[0][0] = 1
print(x, type(x))
# [[1, 0, 0], [1, 0, 0], [1, 0, 0], [1, 0, 0]] <class 'list'>
#x[0][0] = 1,相当于给一个二元数组的首列赋值位1
```

#### 2.列表添加元素

* `lisit.append(obj)`，接受任何类型的参数，**追加**在列表末尾。

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.append(['Thursday', 'Sunday'])
print(x)  
# ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', ['Thursday', 'Sunday']]

print(len(x))  # 6
```

* `list.extend(obj)`， 将一个对象里的东西全部**合并**到一个列表后面

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.extend(['Thursday', 'Sunday'])
print(x)  
# ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Thursday', 'Sunday']

print(len(x))  # 7
```

* `list.insert(index, obj)`，指定位置插入obj

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.insert(2, 'Sunday')
print(x)
# ['Monday', 'Tuesday', 'Sunday', 'Wednesday', 'Thursday', 'Friday']

print(len(x))  # 6
```

#### 3.删除列表元素

* `list.remove(obj)`  移除列表中某一个值得对应项

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.remove('Monday')
print(x)  # ['Tuesday', 'Wednesday', 'Thursday', 'Friday']
```

* `list.pop([index=-1])` 移除列表中的一个元素（默认最后一个），并且返回改元素的值。

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
y = x.pop()
print(y)  # Friday
```

`remove`和`pop`都可以删除元素，前者指定要删除的对象，后者是一个索引

* 批量删除用`delx[a:b]`

#### 4.获取列表元素

* 通过索引值获得单个元素，索引值从0开始
* 索引值指定-1，可以返回最后一个列表元素。以此类推。

列表切片的几种特殊方式

​	1.通用方式`[start : stop : step]`

* step默认为1
* stop缺省时，默认遍历完所有元素。
* start缺省时，默认从首元素开始遍历。

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
print(x[3:])  
print(x[0::1])
print(x[-1::-1])
print(x[0::])
print(x[-3:]) 
***sys.out***
['Thursday', 'Friday']
['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
['Friday', 'Thursday', 'Wednesday', 'Tuesday', 'Monday']
['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
['Wednesday', 'Thursday', 'Friday']
```

* 下表界限问题参考

```python
week = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
print(week[1:3])  # ['Tuesday', 'Wednesday']
print(week[-3:-1])  #['Wednesday', 'Thursday']
print(week[:-3:-1])  # ['Wednesday', 'Thursday']
```

* 浅拷贝`[:]`复制所有元素
* 深拷贝`[::-1]`倒叙复制所有元素

#### 5.列表常用操作符

- 等号操作符：`==`
- 连接操作符 `+`
- 重复操作符 `*`
- 成员关系操作符 `in`、`not in`

>  `「等号 ==」，只有成员、成员位置都相同时才返回True。`

> `列表拼接有两种方式，用「加号 +」和「乘号 *」，前者首尾拼接，后者复制拼接。`

```python
list1 = [123, 456]
list2 = [456, 123]
list3 = [123, 456]

print(list1 == list2)  # False
print(list1 == list3)  # True

list4 = list1 + list2  # extend()
print(list4)  # [123, 456, 456, 123]

list5 = list3 * 3
print(list5)  # [123, 456, 123, 456, 123, 456]

list3 *= 3
print(list3)  # [123, 456, 123, 456, 123, 456]

print(123 in list3)  # True
print(456 not in list3)  # False
```

#### 6.列表杂项

`list.count(obj)`统计某一元素出现的次数

`list.index(x[, start[, end]])`找出列表中某一个值第一个匹配项的索引位置。

`list.reverse() ` 反向列表中元素

`list.sort(key=none, reverse=False)`

> - `key` -- 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，指定可迭代对象中的一个元素来进行排序。
> - `reverse` -- 排序规则，`reverse = True` 降序， `reverse = False` 升序（默认）。
> - 该方法没有返回值，但是会对列表的对象进行排序。

### 元组(Tuple)

`「元组」定义语法为：(元素1, 元素2, ..., 元素n)`

#### 1.创建元组

- Python 的元组与列表类似，不同之处在于tuple被创建后就不能对其进行修改，类似字符串。
- 元组使用小括号，列表使用方括号。
- 元组与列表类似，也用整数来对它进行索引 (indexing) 和切片 (slicing)。
- 创建元组可以用小括号 ()，也可以什么都不用，为了可读性，建议还是用 ()。
- 元组中只包含一个元素时，需要在元素后面添加逗号，否则括号会被当作运算符使用。

```python
print(8 * (8))  # 64
print(8 * (8,))  # (8, 8, 8, 8, 8, 8, 8, 8)

x = (1)
print(type(x))  # <class 'int'>
x = 2, 3, 4, 5
print(type(x))  # <class 'tuple'>
x = []
print(type(x))  # <class 'list'>
x = ()
print(type(x))  # <class 'tuple'>
x = (1,)
print(type(x))  # <class 'tuple'>
```

#### 2.更新

* 重新赋值

#### 3.元组相关的操作符

* 同列表

#### 4.内置方法

* ` tuple.count()`

* `tuple.index()`

#### 5.解压元组(unpack)

* 按照元组数据结构定义

* 也可以使用通配符*来匹配多个元素，生成含有多个元素的列表[]

### 字符串

#### 1.字符串的切片和拼接

- 类似于元组具有不可修改性
- 从 0 开始 (和 Java 一样)
- 切片通常写成 `start:end` 这种形式，包括「`start` 索引」对应的元素，不包括「`end`索引」对应的元素。
- 索引值可正可负，正索引从 0 开始，从左往右；负索引从 -1 开始，从右往左。使用负数索引时，会从最后一个元素开始计数。最后一个元素的位置编号是 -1。

> `类似于列表的拼接，不再赘述`

#### 2.字符串的常用内置方法

* `capitalize()`将字符串的第一个字符转化为大写。
* `lower()` 转换字符串中所有大写字符为小写。
* `upper()` 转换字符串中的小写字母为大写。
* `swapcase()` 将字符串中大写转换为小写，小写转换为大写。
* `count(str, beg= 0,end=len(string))` 返回`str`在 string 里面出现的次数，如果`beg`或者`end`指定则返回指定范围内`str`出现的次数。
* `endswith(suffix, beg=0, end=len(string))` 检查字符串是否以指定子字符串 `suffix` 结束，如果是，返回 True，否则返回 False。如果 `beg` 和 `end` 指定值，则在指定范围内检查。
* `startswith(substr, beg=0,end=len(string))` 检查字符串是否以指定子字符串 `substr` 开头，如果是，返回 True，否则返回 False。如果 `beg` 和 `end` 指定值，则在指定范围内检查。
* `find(str, beg=0, end=len(string))` 检测 `str` 是否包含在字符串中，如果指定范围 `beg` 和 `end`，则检查是否包含在指定范围内，如果包含，返回开始的索引值，否则返回 -1。
* `rfind(str, beg=0,end=len(string))` 类似于 `find()` 函数，不过是从右边开始查找。
* `isnumeric()` 如果字符串中只包含数字字符，则返回 True，否则返回 False。
* `ljust(width[, fillchar])`返回一个原字符串左对齐，并使用`fillchar`（默认空格）填充至长度`width`的新字符串。
* `rjust(width[, fillchar])`返回一个原字符串右对齐，并使用`fillchar`（默认空格）填充至长度`width`的新字符串。
* `lstrip([chars])` 截掉字符串左边的空格或指定字符。
* `rstrip([chars])` 删除字符串末尾的空格或指定字符。
* `strip([chars])` 在字符串上执行`lstrip()`和`rstrip()`。
* `partition(sub)` 找到子字符串sub，把字符串分为一个三元组`(pre_sub,sub,fol_sub)`，如果字符串中不包含sub则返回`('原字符串','','')`。
* `rpartition(sub)`类似于`partition()`方法，不过是从右边开始查找。
* `replace(old, new [, max])` 把 将字符串中的`old`替换成`new`，如果`max`指定，则替换不超过`max`次。
* `split(str="", num)` 不带参数默认是以空格为分隔符切片字符串，如果`num`参数有设置，则仅分隔`num`个子字符串，返回切片后的子字符串拼接的列表。
* `split(str="", num)` 不带参数默认是以空格为分隔符切片字符串，如果`num`参数有设置，则仅分隔`num`个子字符串，返回切片后的子字符串拼接的列表。
* `maketrans(intab, outtab)` 创建字符映射的转换表，第一个参数是字符串，表示需要转换的字符，第二个参数也是字符串表示转换的目标。
* `translate(table, deletechars="")` 根据参数`table`给出的表，转换字符串的字符，要过滤掉的字符放到`deletechars`参数中。

#### 3.字符串格式化

* `format` 格式化函数

```python
str8 = "{0} Love {1}".format('I', 'Lsgogroup')  # 位置参数
print(str8)  # I Love Lsgogroup

str8 = "{a} Love {b}".format(a='I', b='Lsgogroup')  # 关键字参数
print(str8)  # I Love Lsgogroup

str8 = "{0} Love {b}".format('I', b='Lsgogroup')  # 位置参数要在关键字参数之前
print(str8)  # I Love Lsgogroup

str8 = '{0:.2f}{1}'.format(27.658, 'GB')  # 保留小数点后两位
print(str8)  # 27.66GB
```

* python字符串格式化符号

| `符 号` | `描述`                                 |      |
| ------- | :------------------------------------- | ---- |
| `%c`    | `格式化字符及其ASCII码`                |      |
| `%s`    | `格式化字符串，用str()方法处理对象`    |      |
| `%r`    | `格式化字符串，用rper()方法处理对象`   |      |
| `%d`    | `格式化整数`                           |      |
| `%o`    | `格式化无符号八进制数`                 |      |
| `%x`    | `格式化无符号十六进制数`               |      |
| `%X`    | `格式化无符号十六进制数（大写）`       |      |
| `%f`    | `格式化浮点数字，可指定小数点后的精度` |      |
| `%e`    | `用科学计数法格式化浮点数`             |      |
| `%E`    | `作用同%e，用科学计数法格式化浮点数`   |      |
| `%g`    | `根据值的大小决定使用%f或%e`           |      |
| `%G`    | `作用同%g，根据值的大小决定使用%f或%E` |      |

- 格式化操作符辅助指令

| 符号  | 功能                                                         |
| ----- | ------------------------------------------------------------ |
| `m.n` | m 是显示的最小总宽度,n 是小数点后的位数（如果可用的话）      |
| `-`   | 用作左对齐                                                   |
| `+`   | 在正数前面显示加号( + )                                      |
| `#`   | 在八进制数前面显示零('0')，在十六进制前面显示'0x'或者'0X'(取决于用的是'x'还是'X') |
| `0`   | 显示的数字前面填充'0'而不是默认的空格                        |

### 字典

#### 1.可变类型和不可变类型

* 数字，字符串，元组是不可变的，列表，字典是可变的。

- 序列是以连续的整数为索引，与此不同的是，字典以"关键字"为索引，关键字可以是任意不可变类型，通常用字符串或数值。
- 字典是 Python 唯一的一个 映射类型，字符串、元组、列表属于序列类型。

那么如何快速判断一个数据类型 `X` 是不是可变类型的呢？两种方法：

- 麻烦方法：用 `id(X)` 函数，对 X 进行某种操作，比较操作前后的 `id`，如果不一样，则 `X` 不可变，如果一样，则 `X` 可变。
- 便捷方法：用 `hash(X)`，只要不报错，证明 `X` 可被哈希，即不可变，反过来不可被哈希，即可变。

1.对不可变类型的变量重新赋值，实际上是重新创建一个不可变类型的对象，并将原来的变量重新指向新创建的对象（如果没有其他变量引用原有对象的话（即引用计数为0），原有对象就会被回收）。

​		 对于不可变类型int，无论创建多少个不可变类型，只要值相同，都指向同个内存地址。同样情况的还有比较短的字符串。

* float是不可变类型

```python
修改代码声明两个相同值的浮点型变量，查看它们的id，发现它们并不是指向同个内存地址，这点和int类型不同（这方面涉及Python内存管理机制，Python对int类型和较短的字符串进行了缓存，无论声明多少个值相同的变量，实际上都指向同个内存地址。）。
>>> i = 2.5
>>> id(i)
140564351733040
>>> j = 2.5
>>> id(j)
140564351733016
```

#### 2.字典的定义

字典 是无序的 键:值（`key:value`）对集合，键必须是互不相同的（在同一个字典之内）。

- `dict` 内部存放的顺序和 `key` 放入的顺序是没有关系的。
- `dict` 查找和插入的速度极快，不会随着 `key` 的增加而增加，但是需要占用大量的内存。

字典 定义语法为 `{元素1, 元素2, ..., 元素n}`

- 其中每一个元素是一个「键值对」-- 键:值 (`key:value`)
- 关键点是「大括号 {}」,「逗号 ,」和「冒号 :」
- 大括号 -- 把所有元素绑在一起
- 逗号 -- 将每个键值对分开
- 冒号 -- 将键和值分开

#### 3.创建和访问字典

* ```python
  dic = dict()
  dic['values'] = value
  ```

* ```python
  dic = dict([('', num1),('', num2),('',num3)])
  ```

* ```python
  dic = dict(str1="", str2="")
  `这种情况下，键只能为字符串类型，并且创建的时候字符串不能加引号，加上就会直接报语法错误`
  ```

#### 4.字典的内置方法

* `dict.fromkeys(seq,value)` 用于创建一个新字典，以序列 `seq` 中元素做字典的键，`value` 为字典所有键对应的初始值

* `ict.keys()`返回一个可迭代对象，可以使用 `list()` 来转换为列表，列表为字典中的所有键。
* `dict.values()`返回一个迭代器，可以使用 `list()` 来转换为列表，列表为字典中的所有值。
* `dict.items()`以列表返回可遍历的 (键, 值) 元组数组。
* `dict.get(key, default=None)` 返回指定键的值，如果值不在字典中返回默认值。
* `dict.setdefault(key, default=None)`和`get()`方法 类似, 如果键不存在于字典中，将会添加键并将值设为默认值。
* `key in dict` `in` 操作符用于判断键是否存在于字典中，如果键在字典 dict 里返回`true`，否则返回`false`。而`not in`操作符刚好相反，如果键在字典 dict 里返回`false`，否则返回`true`。
* `dict.pop(key[,default])`删除字典给定键 `key` 所对应的值，返回值为被删除的值。`key` 值必须给出。若`key`不存在，则返回 `default` 值。
* `del dict[key]` 删除字典给定键 `key` 所对应的值。
* `dict.popitem()`随机返回并删除字典中的一对键和值，如果字典已经为空，却调用了此方法，就报出KeyError异常。
* `dict.clear()`用于删除字典内所有元素
* `dict.copy()`返回一个字典的浅复制。
* `dict.update(dict2)`把字典参数 `dict2` 的 `key:value`对 更新到字典 `dict` 里。

###  集合

Python 中`set`与`dict`类似，也是一组`key`的集合，但不存储`value`。由于`key`不能重复，所以，在`set`中，没有重复的`key`。

注意，`key`为不可变类型，即可哈希的值。

```python
num = {}
print(type(num))  # <class 'dict'>
num = {1, 2, 3, 4}
print(type(num))  # <class 'set'>
```

#### 1.集合的创建

- 先创建对象再加入元素。

- 在创建空集合的时候只能使用`s = set()`，因为`s = {}`创建的是空字典。

- 直接把一堆元素用花括号括起来`{元素1, 元素2, ..., 元素n}`。

- 重复元素在`set`中会被自动被过滤。

- ```python
  basket.add('string')
  ```

* 使用`set(value)`工厂函数，把列表或元组转换成集合。

#### 2.访问集合中的数据

- 可以使用`len()`內建函数得到集合的大小。

- 可以使用`for`把集合中的数据一个个读取出来。

- 可以通过`in`或`not in`判断一个元素是否在集合中已经存在

#### 3.集合中的内置方法

- `set.add(elmnt)`用于给集合添加元素，如果添加的元素在集合中已存在，则不执行任何操作。

- `set.update(set)`用于修改当前集合，可以添加新的元素或集合到当前集合中，如果添加的元素在集合中已存在，则该元素只会出现一次，重复的会忽略。

- `set.remove(item)` 用于移除集合中的指定元素。如果元素不存在，则会发生错误。
- `set.discard(value)` 用于移除指定的集合元素。`remove()` 方法在移除一个不存在的元素时会发生错误，而 `discard()` 方法不会
- `set.pop()` 用于随机移除一个元素。

由于 set 是无序和无重复元素的集合，所以两个或多个 set 可以做数学意义上的集合操作。

- `set.intersection(set1, set2)` 返回两个集合的交集。
- `set1 & set2` 返回两个集合的交集。
- `set.intersection_update(set1, set2)` 交集，在原始的集合上移除不重叠的元素。
- `set.union(set1, set2)` 返回两个集合的并集。
- `set1 | set2` 返回两个集合的并集。
- `set.difference(set)` 返回集合的差集。
- `set1 - set2` 返回集合的差集。
- `set.difference_update(set)` 集合的差集，直接在原来的集合中移除元素，没有返回值。
- `set.symmetric_difference(set)`返回集合的异或。
- `set1 ^ set2` 返回集合的异或。
- `set.symmetric_difference_update(set)`移除当前集合中在另外一个指定集合相同的元素，并将另外一个指定集合中不同的元素插入到当前集合中。
- `set.issubset(set)`判断集合是不是被其他集合包含，如果是则返回 True，否则返回 False。
- `set1 <= set2` 判断集合是不是被其他集合包含，如果是则返回 True，否则返回 False。
- `set.issuperset(set)`用于判断集合是不是包含其他集合，如果是则返回 True，否则返回 False。
- `set1 >= set2` 判断集合是不是包含其他集合，如果是则返回 True，否则返回 False。
- `set.isdisjoint(set)` 用于判断两个集合是不是不相交，如果是返回 True，否则返回 False。

#### 4.不可变集合

Python 提供了不能改变元素的集合的实现版本，即不能增加或删除元素，类型名叫`frozenset`。需要注意的是`frozenset`仍然可以进行集合操作，只是不能用带有`update`的方法。

- `frozenset([iterable])` 返回一个冻结的集合，冻结后集合不能再添加或删除任何元素。

### 序列

在 Python 中，序列类型包括字符串、列表、元组、集合和字典，这些序列支持一些通用的操作，但比较特殊的是，集合和字典不支持索引、切片、相加和相乘操作。

#### 1.内置函数

* `list(sub)`把可迭代对象转换为列表

- `tuple(sub)` 把一个可迭代对象转换为元组。

- `str(obj)` 把obj对象转换为字符串
- `len(s)` 返回对象（字符、列表、元组等）长度或元素个数。
  - `s` -- 对象。

* `max(sub)`返回序列或者参数集合中的最大值

* `sum(iterable[, start=0])` 返回序列`iterable`与可选参数`start`的总和。

  * ```python
    print(sum([1, 3, 5, 7, 9]))  # 25
    print(sum([1, 3, 5, 7, 9], 10))  # 35
    print(sum((1, 3, 5, 7, 9)))  # 25
    print(sum((1, 3, 5, 7, 9), 20))  # 45
    ```

* `sorted(iterable, key=None, reverse=False)` 对所有可迭代的对象进行排序操作。
  - `iterable` -- 可迭代对象。
  - `key` -- 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，指定可迭代对象中的一个元素来进行排序。
  - `reverse` -- 排序规则，`reverse = True` 降序 ， `reverse = False` 升序（默认）。
  - 返回重新排序的列表。

* `reversed(seq)` 函数返回一个反转的迭代器。

- `seq` -- 要转换的序列，可以是 tuple, string, list 或 range

* `enumerate(sequence, [start=0])`

* ```
  zip(iter1 [,iter2 [...]])
  ```

  - 用于将可迭代的对象作为参数，将对象中对应的元素打包成一个个元组，然后返回由这些元组组成的对象，这样做的好处是节约了不少的内存。
  - 我们可以使用 `list()` 转换来输出列表。
  - 如果各个迭代器的元素个数不一致，则返回列表长度与最短的对象相同，利用 `*` 号操作符，可以将元组解压为列表