# Python







Python解释器是Python环境的本体，也就是python.exe文件。我们需要在环境变量的路径中将python.exe所在的目录添加上，这样在终端或者命令行中输入python指令时，就会默认打开该目录下的python.exe文件。



## 基础

**基础知识**

* Python是一种动态语言，变量类型可以随时变换

* 当使用`if __name__=='__main__':`条件语句时，通常会将需要在脚本作为主程序时执行的代码放在这个条件语句的下面。这样可以确保这部分代码仅在该脚本作为主程序执行时运行，而在被导入时不会执行。
* 看懂 traceback  通常要从traceback 末尾着手 

**常用知识**

* 在使用import语句导入模块时，每执行一条import语句都会创建一个命名空间，并且在该命名空间中执行与.py相关的所有语句，在执行时，需要在具体的变量，函数和类之前加 ‘’ 模块名.‘’，如果不想再每次导入模块时都创建一个新的命名空间，而是仅将具体的定义导入当前的命名空间中，这时可以使用from import，不需要再添加前缀，直接通过具体的变量，函数，和类名等直接访问，
* 命名空间可以理解为记录对象名字和对象之间对应关系的空间，Python的命名空间大多都是通过字典来实现的
* 使用from import语句导入模块中的定义时，需要保证所导入的内容在当前命名空间中是唯一的，否则将出现冲突，后导入的会覆盖先导入的，这时需要用import导入
* Python中的包就相当于文件夹，而模块就相当于.py文件

~~~py
#从setting包中导入size模块，通过该方式导入则在使用时需要使用完整名称
import setting.size
print(setting.size.width)

#使用from导入包中的模块，在使用时不需要带包前缀，但是需要带模块名
from setting import size
print(size.width)

#直接使用
from setting.size import width
print(width)


~~~



~~~py
print("不换行输出"，end='')
~~~

**命名规范**

:one:  模块名：全部小写，可以使用下划线

:two: 包名：全部小写，不推荐使用下划线，

:three: 类名：单词首字母大写

**驼峰命名** ：类名中的每个单词首字符大写，并且不适用下划线。实例名和模块名采用 小写，单词之间加上下划线

**注意**

* 单下划线开头的标识符，表示不能被直接访问的类属性 ，也不可通过 import from 导入
* 双下划线表示类私有成员
* 双下划线开始和结尾的 专用 



**Python函数**

- id（）函数获取变量地址
- print（）：输出自动换行
- pprint（）：自动格式化输出，有width参数，设置每行最大字符数

* range（start，end，step）： 结束值不包括end。如果只有一个参数，则表示的结束值
* sum（iterable，start）函数： 第二个参数表示起始值，从这个数开始求和
* sorted（）：表示排序，不改变原有顺序，
* tuple（），list（）
* type() 测试变量类型
* enumerate（iterable）：用于将可遍历的数据对象（列表，元组）组合为一个索引序列，标出数据下标，配合for循环
* zip（）:  将多个列表或者元组对应的位置组合为元组，返回zip对象
* randint(x,y) : 返回下x-y之间的随机数   **需要导入random**
* choice（）：将一个列表或者元组作为参数，随机返回其中的一个元素  **需要导入random**

**其他**

* if可以简化

~~~py
b=a if a>0 else -a
# 如果a>0,则b=a否则等于-a
~~~

* if 判断布尔

~~~py
if flag:
if not flag:
    
#以下为不规范写法

if flag==True
if flag==False

~~~

---





**语句**

* match case 语句

~~~py
match day:
    case 0:
        print("今天星期天")
    case 1：
    	print("今天星期一")
        
#match语句可以匹配字典

~~~

* while 循环

~~~p
while value :
	num+=1
	value--

~~~

* pass语句表示空语句

---



### 列表和元组

元组，列表，字典，字符串，集合为**序列**

**序列相加**

多个相同类型的序列可以相加，必须是相同序列

**切片**  

~~~~py
name_xulie[ start :end :step]
~~~~

**序列乘法**

~~~py
verse=[" 你想活出怎么的人生"]

verse_5= 5*verse 

~~~



**判断元素是否存在序列用 in**

~~~py
'判断的序列成员' in  verse

#存在则True否则Fasle

~~~

#### **列表 List**

:smile:   **创建列表**

~~~py
list_name = ["直接赋值创建列表",'我是列表']

list_name1 = list(range(1,10)) #list()函数创建列表
~~~



:smile:  **删除列表**

~~~PY
del list_name
~~~



:smile: **遍历列表**

~~~py
#for循环遍历
for item in list_name:
    print(ietm)
~~~

~~~py
#enumerate()函数
for index,item in enumerate(list_name):
    print(index,item)
~~~



:smile:  **添加元素**

:one: 末尾添加元素  列表方法   .append()

~~~py
verse=['a','b']
verse.append("c")
~~~

:two: 插入添加 ： 列表方法：.insert()

:three:  复制  ：列表方法： .extend

~~~py
list_name1=['我是列表1']

list_name2=['我是列表2']

list_name1.extend(list_name1)
~~~



:smiley:**修改元素**

通过索引修改

~~~py
list_name1[0]="修改第一个元素"
~~~



**:small_airplane:删除元素**

:one: 根据索引删除

~~~py
del list_name1[0]
~~~



:two:根据元素值删除：

~~~py
if list_name.count("删除的元素")>0: #删除前先判断是否存在
    list_name.remove("删除的元素")
~~~



:smile_cat:**列表统计和排序**

:one:  统计次数和获取指定元素索引位置

~~~py
list_name.count("统计的元素")

lsit_name.index("该元素的首次索引位置")
~~~

:two:排序

~~~py
list_name.sorted(key=str.lower,reverse=True) #不区分大小写， 降序排列
#注意 列表方法 sort()改变原有的列表顺序
~~~

**:taco:列表推导式：**

 ~~~py
 import random
 random_num =[random.randint(10,100) for i in range(10)]
 
 #生成10个10-100范围的随机数
 
 price = [100,300,400,500,600]
 half_count  = [ int(x*0.5)  for x in price ]
 
 
 price = [100,300,400,500,600]
 
 list_count =[x for x in price if x > 300]  #选择符合条件的，price中大于300的生成新列表
 
 
 ~~~

**二维列表**

**:sailboat:直接定义二维列表**

~~~py
list_name=[
    [100,200,400],
    [10,20,30,40]
    
]
~~~

**:see_no_evil: for循环和推导式创建**

~~~py
list_name1=[]  			#创建空列表
for i in range(4):     #四行
    arr.append([])   #在空列表中添加空列表
    for j in range(5):  #五列
        arr[i].append(j) 
        
#列表推导式建立
arr = [[j for j in range(5)] for i in range(4)]
~~~



#### 元组 tuple

元组中的元素类型可以不同，通常保存不可修改的内容

**:seedling:  创建元组**

~~~py
#直接创建
tuple_name = ("我是元组",1017)
tuple_name2="我是元组",2900
tuple_name3="有逗号我是元组",
Sting_name="没有逗号我是字符串"
#创建空元组
empty_tuple=()

#创建数值元组
tuple_name=tuple(range(10))


~~~

**:jack_o_lantern:访问元组可以用切片和for循环**

~~~py
for  index ,item in  enumerate(tuple_name):
    print(index,item)
~~~

**:package:修改元组**

**元组是不可变序列，不能对单个值进行修改，但是可以重新赋值**，**元组也可以进行连接相加赋值**

~~~py
tuple_name[1]='修改单个元组值'  #这是错误的

tuple_name=('元组只能通过','整体赋值','进行修改')

tuple_name=tuple_name +("单个元组",)  #加单个元组逗号不能省略也不能在括号外面
~~~



**:book:元组推导式(生成的不一定是元组或者列表，而是一个生成器对象)**

~~~py
import random 
random_num = (random.randint(10,100) for i in range(10))
random_num = tuple(random_num)
~~~





### 字典和集合

**字典是 无序、可变的，键—值对 形式，字典可以任意嵌套，键必须唯一且不可变,键可以是字符串和元组，键可以是任意类型**,

如果后面的添加的键与存在的重复，则新值会覆盖原值

#### 字典

**:e-mail:字典的创建**

~~~py
dictionary ={"詹姆斯":23,"杜兰特":35,"库里":30}

#创建空字典
empty_dictionary=dict()

#通过映射函数

name=['杜兰特','詹姆斯','库里']
number=[35,23,30]
dictionary=dict(zip(name,number))

#键值对赋值形式创建字典
dictionary=dict("詹姆斯"=23,"杜兰特"=35,"库里"=30)

#使用dict对象fromkeys
name=['杜兰特','詹姆斯','库里']
dictionary2 =dict.fromkeys(name) #所有键的值都为None

#通过元组和列表创建字典
name=('杜兰特','詹姆斯','库里')
number=[35,23,30]
dictionary={name:number}

~~~



:japanese_castle:**删除和清空字典**

~~~py
del dictionary

dictionary.clear()               #清空字典
value = dictionary.pop('key')    #删除字典元素，并且返回指定键对应的值
(key,value) = dictionary.popitem() 			 #弹出最后一个字典元素
~~~



:kimono: **访问字典**

~~~py
print("KD的号码是",dictiaonary["杜兰特"] if "杜兰特" in dictionary else "没有KD")

print("KD的号码是",dictionary.get('杜兰特','没有杜兰特'))
~~~



:goal_net:**遍历字典**

~~~py
#	dictionary.item() 获取字典的 键值对 列表

for item  in dictionary.item():
    print(item)
  
for key,value  in dictionary.item():
    print(key,"and",value)
    
# values() 和  keys()方法获取 键值，使用方法类似，也需要通过for循环遍历

~~~

***:eight_pointed_black_star:添加，修改，和删除字典元素**

~~~py
dictionary['科比']=24

del dictionary['詹姆斯']

#删除不存在的键
if '詹姆斯' in dictionary :
    del dictionary['詹姆斯']
    
~~~

:ocean: **字典推导式**

---





#### 集合Set

集合是用来保存不重复元素的，有可变和不可变两种，set集合是无序可变的

空集合只能通过set（）函数来创，不能用{ }，因为{ }是表示创建一个空字典

:ice_cream: **集合操作**

~~~py
# 通过"{}"直接创建集合
set_name={'集合是无序的','且重复元素只会保留一个','集合成员可以是不同类型','每次输出可能顺序不同'}

#通过set()函数创建集合
set_name=set() #创建空集合
set_name=set(['set()函数将列表或者元组等转换为集合'])


~~~



~~~py
set_name.add('向集合中添加元素')

set_name.pop()
set_name.remove('删除指定元素')
set_name.clear()
~~~

**集合运算: 交集 &       并集 |    差集 - **





### 字符串



:raised_back_of_hand:**字符串**



:page_with_curl:**字符串常用操作**

~~~py
#拼接字符串，非字符类型需要通过str()函数先转换为字符类型
print(str1 + str(num) +str2)

#获取字符串长度
print(len(str))

#字符串可以用切片截取
str1=str[0:9]


#字符串方法 spilt()分割字符串
#使用spilt()方法时，不指定参数则默认采用空白符进行分割，无论有几个空白符都被视为一个分隔符
print(str.spilt('.',4)) 		#采用'.' 分隔符，只分割前四个

#合并字符串 str.join(iterable)

#count()方法检索出现次数
'我有几个*啊***'.count('*')
'前14个字符我有几个*啊***'.count('*',0,14)

#find()方法返回子串出现的首次索引位置
"输出*第一次出现的索引位置，不存在的返回-1".find('*',0,10)

#判断子串是否存在
Flag= '子串是否存在' in str  
FF='子串是否大于-1来判断子串是否存在'.find('子串') > -1
#rfind()方法与find()类似，rfind()从右边开始检索

#index()方法返回索引
str.('返回子串索引位置，没有会抛出异常')

#判断字符串是否以'子串开头'或者结尾
str.startswith("判断是否以子串开头")
str.endswith("判断是否以子串结尾")

#转化大小写
str.lower()
str.upper()

#去除字符
"@去除字符串两侧的字符,不指定默认去除空白符".strip("@")
'去除字符串左侧的字符'.lstrip()
'去除字符串右侧的字符'.rstrip()
~~~



:incoming_envelope:**格式化字符串**





---





### 正则表达式





---



### 函数

**基础知识**

~~~py
function_name.__defaults__ # 查看默认值


def function_name(height,weight,person='路人甲'): #参数默认值
    print(person,height)
    
  
#	使用可变对象作为函数参数的默认值时，多次调用可能会导致意料之外的情况
#	所以为形式参数设置默认值时，默认参数必须要指向不可变对象


#   *parameter表示接收任意多个实际参数并将其放到一个元组中 
#	如果想要一个已存在的列表
def printcoffe (*coffe):
    for item in coffe:
        print(item)
printcoffe('生椰拿铁','丝绒拿铁')

       
    
#	**parameter 表示接收任意多个类似关键字参数一样显式赋值的实际参数，并将其放到一个字典中

    
~~~

### 文件

Python中内置了文件对象，在使用文件对象时，首先需要通过内置的open()方法创建一个文件对象

~~~py
file = open('message.txt','w',encoding='utf-8')

#	打开文件后需要及时关闭
file.close()

#	打开文件时使用with语句，with语句执行完毕后关闭已经打开的文件

with expression as target :   #		target用于指定一个变量，将expression 的结果保存到该变量中
    with_body             
with open("message.txt",'w') as file_targetz:
    pass

#写入文件内容
file.write(string)
file =open("message.txt",'a')
file.write("追加文件内容\n")
flie.close()

#	读取文件
flie.read(size)

with open('message.txt','r') as file :
    file.seek(5,0)  #0文件开头，1当前位置，2文件末尾
    string=file.read(7)
    print(string)
    
#	读取一行
file.readline()
#	读取全部行 ，返回的是字符串列表
file.readlines() 
~~~

#### 目录（文件夹)操作

---

#### 高级文件操作

---

### 异常处理和调试

~~~py

def division():
    apple = int(input("请输入苹果个数："))
    kids  = int(input("请问有多少小朋友："))
    assert apple>kids ,'如果前面的表达式为真，则什么都不做，否则会打印此内容'
    if apple<kids:
        raise ValueError("apple is not enough")
    result = apple // kids

    print(result)
try:
    division()
except(ZeroDivisionError):
    print("不指定异常则表示任何异常")
except(ValueError) as error:
    print("异常：",error)
else:
    print("没有异常时执行，有异常不执行")
finally:
    print("无论有无异常都将会执行，常用于释放资源")

~~~

### 测试类

---

# Anaconda 命令

## 基本命令

**查看conda版本** 

~~~cmd

conda --version
conda -V

~~~

**更新conda**

~~~cmd
conda update conda
conda update anaconda
conda upgrade conda
conda upgrade anaconda

~~~

**查看conda帮助信息**

~~~cmd
conda --help
conda -h

~~~

## 常用命令

#### **创建环境**

~~~cmd
安装指定解释器的版本号
conda create --name SVM python=3.5

在新创建的环境中创建多个包
conda create --name SVM python=3.6 numpy pandas matplotlib


~~~

#### **显示已存在的环境**

~~~cmd
conda env list
conda info -e
conda info --envs

~~~

#### **激活/切换，退出环境**

~~~cmd

conda activate test_name
conda activate (空) 			 回到基础环境
deactivate  （没有环境名）		 退回至root
~~~

#### **复制环境**

~~~cmd
conda create --name new_name --clone old_name
~~~

#### **删除环境**

~~~cmd
重命名可以先克隆然后删除
conda remove --name testcode
~~~

#### **获取环境中已存在的包信息**

~~~cmd
查看当前环境中已安装的包信息:
conda list
查看指定环境中已安装的包信息:
conda list --name <env_name>
pip查看当前环境中已安装的包信息:
pip list
pip freeze
pip查看当前环境中可升级的包信息:
pip list -o

~~~

## 安装包

:sailboat:**conda 安装包**

~~~cmd
在当前环境中安装包:
conda install <package_name>

在指定环境中安装包:

conda install --name <env_name> <package_name>
安装特定版本的包:
conda install package=version

~~~

:package:**pip安装包**

~~~cmd
在当前环境中安装包:
pip install <package_name>

安装特定版本的包:
pip install <package_name>==version

~~~

  当使用conda install无法进行安装时，可以使用pip进行安装。

pip指定特定版本是“==”,而conda是“=”。

pip只是包管理器，无法对包进行管理。因此如果想在指定环境中使用pip进行安装包，则需要先切换到指定环境中，再用pip命令安装。

pip无法更新python，因此pip不能讲python视为包。

pip可以安装一些conda无法安装的包，conda也可以安装一些pip无法安装的包。当使用一种命令无法安装时，可以尝试使用另一种命令。

pip安装包或许直接忽略依赖项而安装，仅在结果中提示错误，conda安装包自动安装其依赖项。























