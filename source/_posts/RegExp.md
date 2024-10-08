---
title: RegExp
date: 2020-06-29 11:10:08
categories:
- RegExp
tags:
- RegExp
---

Regular Expression 
正则表达式
正则 - 规则

根字符串打交道：
校验
提取

# Base
| -- | -- |
| 特别字符 ｜ 说明 ｜
｜ . ｜ 匹配除换行符 \n之外的任何单字符。要匹配 .，请使用 \。 |
| $1 | 小括号中的值 |
| \W | 非字母和数字 |


更多字符：https://www.cnblogs.com/afarmer/archive/2011/08/29/2158860.html

# 写法
## 创建正则
js风格 new RegExp()
perl风格 /\d+/
{% label yellow@注意：不是字符`/\//` %}

search   类似于indexOf，是位置
match    匹配
replace  替换

re.test(str) => boolean

``` js
let str = 'shfaAdsd';
// let re = new RegExp('a', 'i');
let re = /a/i;
alert(str.search(re));
```

``` js
// 查找数字
let str = 'cad9sdf';
let re = /\d/; // \d 转义
// js风格
let re = new RegExp('\\d') // \在js中是转义，\\代表\
alert(str.search(re));
```

const REGEXP_S = /\/s\//;
    if (device == 'Android' || device == 'iOS') {
      if (href.search(REGEXP_S) != -1) {
        window.location.href = `https://${document.domain}/s/`;
      } else {
        window.location.href = `https://${document.domain}/m/`;
      }
      
    }

## 选项
i  Ignore  忽略大小写
g  Global  全局匹配
m          多行模式
   单行模式（默认） ^$指的是整个字符串的开头和结尾；不会识别字符串里面的换行
   多行模式（m）   ^$指的是每一行的开头和结尾；识别字符串中的\n

*混用

## 转义
\d digit   数字

\.  点
## 懒
贪婪匹配？
越多越好——正则默认情况会倾向于匹配尽可能长的东西

量词——几个
1.如果不加量词，就是一个
{3}  3个
/+    多个 /\d+/ 多个数字

``` js
let str = 'asf 233 dsfsf 4232 dfs 234sfsf 23sd';
let re = /\d+/g;
alert(str.match(re));
```

## 元字符
[]
1.或
  /a[abc]s/   aas  abs  acs

2.范围
  [a-z]
  [0-9]  \d
  [a-z0-9]

3.排除
  [^abc]
  [^0-9]

## 量词
{n}  
{n,m}
{n,}
{0,m}

/+   {1,}
/*   {0,}
？   {0,1}

## 谓语（修饰符）
^   行首
$   行尾

``` js
// 网址
let re = /^https?:\/\//;
re.test(str);
```


# 其他
## 手机号
1.11位数字
2.13x/150/158/170/172开头

或 ｜
/^(13\d|15[08]|17[0-4])\d{8}$/


test() 方法执行一个检索，用来查看正则表达式与指定的字符串是否匹配。返回 true 或 false。
const PHONE_REGEX = /^1\d{10}$/;
PHONE_REGEX.test(this.phone)

## 邮箱
aaa @ aa.com

1.用户名：数字、字母、下划线，最多64位
  \w == [a-z0-9_]
  \w{1,64}

2.网址：英文、数字、中划线
  [a-z0-9\-]{1,256}

3.后缀：（.英文2～6位）1～2个
  (\.[a-z]{2,6}){1,2}

/^\w{1,64}@[a-z0-9\-]{1,256}(\.[a-z]{2,6}){1,2}$/

99%
var emailRegex = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;

## 用户名
（数字、字母、下划线）8～12位
/^\w{8,32}$/

## 银行卡4个字符空格
```js
let cardNo = '123412341234';
const cardNoFormat = cardNo.replace(/(.{4})/g, '$1,');
console.log(cardNoFormat.split(','));
```

## 花括号内的字符串
```js
const str = `{{first.DATA}}\n资料名称：{{keyword1.DATA}}\n资料简介：{{keyword2.DATA}}\n{{remark.DATA}}`;
const regex = /\{\{(.+?)\}\}/g;
let wxTemplateParams =  str.match(regex);
```
