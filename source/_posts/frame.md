---
title: frame
date: 2023-04-12 16:11:25
tags: frame
---
 
前端三大框架的目标：利用数据驱动页面
{% asset_img target.png %}
核心问题，数据发生变化后，我们怎么去通知页面更新。

Angular 1 的脏检查，指的是 Angular 1 在对数据变化的检查上，遵循每次用户交互时都检查一次数据是否变化，有变化就去更新 DOM 这一方法。

Vue 1 的解决方案，就是使用响应式，初始化的时候，Watcher 监听了数据的每个属性，这样数据发生变化的时候，我们就能精确地知道数据的哪个 key 变了，去针对性修改对应的 DOM 即可
{% asset_img vue1_watcher.png %}

React 框架，在页面初始化的时候，在浏览器 DOM 之上，搞了一个叫虚拟 DOM 的东西，也就是用一个 JavaScript 对象来描述整个 DOM 树。种形式不仅让性能有个很好的保障，我们还多了一个用 JSON 来描述网页的工具，并且让虚拟 DOM 这个技术脱离了 Web 的限制。因为积累了这么多优势，虚拟 DOM 在小程序，客户端等跨端领域大放异彩。
{% asset_img react.png %}

# Use
阮一峰:
上面三种新技术，都是最近10年诞生的。当时，都号称解决了开发的重大问题，看上去很有希望。 因此，一诞生就成了热点，非常吸引眼球，这些工程师就都采用了。

我说说这些技术的优点。

Elm 语言保证网页脚本不再报错。

GraphQL 只发一个请求，就满足前端的所有数据需求。

ionic 让你使用任意 JS 框架，开发安卓和苹果的手机应用。

如果你是前端工程师，一看这些技术特点，大概立刻就会心动。

但是，当你真把它们用在生产环境，各种问题就会慢慢暴露出来，几年以后你可能就像上面的文章作者一样后悔莫及。

Elm：最新一次更新是2019年，与当前 JS 生态的融合越来越困难。

GraphQL：使用后的性能提升不明显，反而使后台架构变得复杂，而且分页、缓存等问题很麻烦。

ionic：文档不足且混乱，没有社区和生态。

等到后悔了，想要更换技术栈，就晚了。上车容易下车难，项目都持续投入好几年了，再修改架构谈何容易。

这件事的教训，就是使用新技术要谨慎。新技术有一个最大风险，往往被忽视，那就是它们没有经过足够的使用，问题都没有暴露出来。

我记得，有人做过研究，企业软件的成本，只有20%是早期的开发成本，剩下的80%都是后期的维护和更新成本。

很多的新技术，看上去可以节省前面20%的开发成本，但可能大大增加后面80%的维护成本。

现实生活中，那么多企业选择 Java，而不是那些时髦花哨的新技术，原因就在这里：Java 是经过考验的，不会出现奇怪的问题，有良好的长期维护，企业长期使用的风险和成本相对较低。

如果开发者真为自己考虑，想将来简单一点，不必每天为复杂奇怪的技术问题操心，应该优先选择那些可靠的老技术，用于公司的长期项目。

老技术的问题是，它很乏味：所有可能性都被探索过了，创造发挥的空间不大。很多程序员（尤其是新程序员）因此觉得，老技术展现不了技术能力，也不够好玩，新技术更有乐趣，对自己的提升更大。

这种想法并没错，但前提是你的项目不需要长期维护，否则使用未经考验的新技术是非常冒险的。


# PHP
## install
brew install php@7.3
## issues
Error: php@7.3 has been disabled because it is a versioned formula

brew tap shivammathur/php
brew install shivammathur/php/php@7.3
brew link php@7.3
## PHPBrew
版本管理
## composer
包管理
brew install composer
## run
php think run
## issues
Error: php@7.3 has been disabled because it is a versioned formula

brew tap shivammathur/php
brew install shivammathur/php/php@7.3
brew link php@7.3

## 调试
```html
<div>{php} dump($r); {/php}</div>
<div>{$r['id']}</div>
```
```php
echo 'rows:' . $rows;
```

## thinkphp
### run
php think run
### 查询结果排序
```php
$list = Db::name('Task')->where(['delete_time'=> 0])
->withoutField('content,md_content')
->order('flow_status asc')
->order('end_time asc')
```

### 数据处理
```php
if(request()->isAjax()){
} else {
     View::assign([ //用于向视图传递数据
        'r_v_list' => $r_v_list,
    ]);
    return view(); //用于渲染视图并返回响应
}
```

### 加请求参数
```
url: "/dashboard/index/release"
where:{'sort':'priority'},

if(isset($param['sort'])){
    $sortStr = 'priority asc';
}
```

### model 中初始化
```
public function getNewStatusAttr($value)
    {
        if($this->status == 2){
            return 1;
        }
    }
```

### sql
``` php
// 数据表中的"id"字段的值必须在$project_ids数组中
->where([ ['id', 'in', $project_ids]]) 

// 找出 $project_ids 中哪些元素不在 $r_project_ids 中
array_diff($project_ids,$r_project_ids)

// id不在$project_ids数组中的所有记录
->where([['id', 'not in', $project_ids]])

// 匹配 status 等于 1 或者 2 的记录
['status', 'in', [1, 2]] 
// 生成的sql语句
status IN (1, 2)
```

## HTML 模版中操作
### 判断
```
{eq name="变量名" value="指定值"}输出内容{/eq}
```
