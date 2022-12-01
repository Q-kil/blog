---
title: python
date: 2022-11-22 22:01:02
tags:
---

# Base
## 安装
python.org download

python3 -V
pip3 -V

## 卸载
删除Python 3.7 框架，打开终端，输入
sudo rm -rf /Library/Frameworks/Python.framework/Versions/3.7

删除 Python 3.7 应用目录
cd /Applications
sudo rm -rf Python 3.7

删除/usr/local/bin 目录下指向的Python3.7 的连接
cd /usr/local/bin/

ls -l /usr/local/bin

rm Python3.7相关的文件和链接

#Python3.7相关的文件和链接需要自行确认是否删除

5. 删除 Python 的环境路径

vi ~/.bash_profile

6. 确认python 是否已经删除

python3.7

-bash: python3.7: command not found

## requirements.txt 管理套件相依性
### 安装
```zsh
$ pip install -r requirements.txt
```

## pyenv
Python版本管理

### 安装pyenv
```zsh
git clone https://github.com/pyenv/pyenv.git ~/.pyenv


echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n eval "$(pyenv init -)"\nfi' >> ~/.zshrc
```

echo 命令的含义是：将引号中内容写入某文件中
请注意，以上的三条 echo 命令的最后一条长长的命令，请你保证它引号中的内容处于 ~/.bashrc 或者 ~/.zshrc 的最底部。
因为在 pyenv 初始化期间会操作 path 环境变量，导致不可预测的行为。

### CLI
``` zsh
# 查看当前版本
pyenv version

# 查看所有版本
pyenv versions

# 查看所有可安装的版本
pyenv install --list

# 安装指定版本
pyenv install 3.6.5
# 安装新版本后rehash一下
pyenv rehash

# 删除指定版本
pyenv uninstall 3.5.2

# 指定全局版本
pyenv global 3.6.5

# 指定多个全局版本, 3版本优先
pyenv global 3.6.5 2.7.14

# 实际上当你切换版本后, 相应的pip和包仓库都是会自动切换过去的
```

### install 太慢问题
进入源码页面下载`.tar.xz`文件，https://www.python.org/downloads/source/

将下载的 Python 版本压缩包放到 pyenv 的缓存文件夹: `~/.pyenv/cache`

执行安装命令
```zsh
$ pyenv install 3.9.15
python-build: use openssl@1.1 from homebrew
Downloading readline-8.1.tar.gz...
-> https://ftpmirror.gnu.org/readline/readline-8.1.tar.gz
Installing readline-8.1...
Installed readline-8.1 to /Users/qkil/.pyenv/versions/3.9.15

Installing Python-3.9.15...
python-build: use zlib from xcode sdk
WARNING: The Python lzma extension was not compiled. Missing the lzma lib?
Installed Python-3.9.15 to /Users/qkil/.pyenv/versions/3.9.15
```

## 语言
- 高级编程语言
- 解释型语言（翻译）
  C：编译型语言，执行前先编译，再汇编，再链接，更接近机器执行的代码。比python速度更快，执行效率更高
- 语法和自然语言很像

## 运行特定版本
```zsh
python3.9 -V
python3.10 -V

# 查看python3 多少位
$ python3
Python 3.11.0 (v3.11.0:deaf509e8f, Oct 24 2022, 14:43:23) [Clang 13.0.0 (clang-1300.0.29.30)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import platform
>>> platform.architecture()
('64bit', '')
>>>
```

## 交互式运行
```
$ python3 -i 2.py
Hello world!
>>> print('h')
h

非交互式运行
$ python3 -i 2.py
Hello world!
```

# 语法
## 输入输出
``` py
var=input()
print(var)
```

## 类型
- 整数 int 8
- 浮点数 float 8.8
- 字符串 str '8'
- 布尔值 bool True,False

### 判断类型
type(8)
type('8')
type("8")
type(True)

### 类型转换
int('8')
str(123)
bool(123) //非0返回True

## 注释
```py
# 首先第一行写程序用来做什么的
```

## int
n += 1

## 字符串
### 长度
len(str)
### 取值
单个：str[0]
多个：str[0:4] /不包含4
后面：str[-1]

### 判断是否在字符串中
'1' in '123'
'0' not in '123'

### 分割
data.split('|')

### 去除
line.strip('\n')

### 元组
存储内容，不可变更
（1, 10) > (2, 20)
看成：110 > 220

```py
a=(1,3,5,7)
b=4
list filter(lambda x: x < b, a) #取出a中小于4的元素
```

### 字符串模版
'%s 年的生肖是 %s' %(year, s)

## 数组
```py
list = []
list.append('X') #新增
list.remove('X') #删除
``` 

## 逻辑判断
### 条件语句
``` py
x = 'abcd'
if x == 'abc' :
  print('相等')
elif x == 'xyz':
  print('xyz')
else:
  print('都不相等')
```

### 循环语句
#### while语句
``` py
while 表达式：# 表达式如果为真，会一直执行, 直到表达式为假
  代码块

while True:
  print('a')
  break # 终断

import time
num = 5
while True:
  num = num + 1
  if num == 10:
    continue # 跳过本次
  print(num)
  time.sleep(1)
```

#### for语句
``` py
for 迭代变量 in 可迭代对象：
  代码块

for s in [1,2,3]:
  print(s)

for i in range(1,13): # range(13) 1,--12; 不包含最后一个数
  print(i)
```

## 函数
### 定义
``` py
def 函数名称():
  代码
  return 需要返回的内容
```

### 调用
函数名称()

# Issuse
## Missing dependencies for SOCKS support
环境变量中则设置了 socks5 的代理; ~/.zshrc
Python 本身在没有安装 pysocks 时并不支持 socks5 代理
取消代理后，安装
pip install pysocks



# 研究
## NLP
NLP：Natural Language Processing，自然语言处理
将人类之间交流沟通所用的语言经过处理转化为机器所能理解的机器语言。
目的就是让机器理解并生成人类的语言，从而和人类平等流畅地沟通交流。

### 两种方向
- 自然语言理解（Natural Language Understanding, NLU）【如何理解文本】
- 自然语言生成（Natural Language Generation, NLG）【理解文本后如何生成自然文本】

### 应用
作为人工智能领域的底层技术，自然语言处理常常与智能语音、知识图谱等技术方向衔接捆绑。通过语音识别、语音合成、语义分析等细化技术的互相组合，以对话式AI、机器翻译、文字审核、知识库等类型的产品和应用出现。
在实际应用层面，则常常用以满足较为复杂的社交网络文本情感分析、客户信息挖掘等的需求，比如电商平台中构建知识图谱实现智能导购，挖掘客户兴趣以实现精准营销；客服场景中智能机器人提供客服服务、翻译机器人在跨境电商业务中对商品信息、广告词等进行翻译。

由于自然语言作为人类社会信息的载体，使得NLP不只是计算机科学的专属。在医疗健康、金融、法律、教育等领域，同样存在着海量的文本，NLP也就成为了重要支持技术。

#### 医疗行业
- 从病历、检验单、医嘱等医疗文本中提取患者的性别年龄、临床症状等关键信息，将非结构化数据转化成一致、统一的表格等形式的结构化数据
- 基于提取出的信息，并且让机器掌握医生具备的医疗知识，构建出显示各类医疗信息之间关系的知识图谱，比如患者症状、药物、疾病诊疗等
- 知识图谱可以根据患者的症状诊断疾病，或者根据特定的疾病推断出未来可能出现的症状

## Issuse
### 应用领域？
- 电子医生 -> 智能辅助诊疗
- Siri手机助手
- 智能客服


# OCR
OCR：Optical Character Recognition，光学字符识别
指电子设备（例如扫描仪或数码相机）检查纸上打印的字符，通过检测暗、亮的模式确定其形状，然后用字符识别方法将形状翻译成计算机文字的过程

在NLP的相关产品中，OCR扮演着不可或缺的角色，主要是在关于文档处理的一些场景中，例如，pdf等格式的文档抽取、文档审核、文档比对等。

## 应用
- 银行卡拍照识别
- 快递信息拍照，自动录入

# Paddle
人工智能 > 机器学习 > 深度学习

