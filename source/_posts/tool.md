---
title: tool
date: 2022-01-24 11:54:14
tags: vite
---


# css
Autoprefixer

# vite
## BG
在浏览器支持 ES 模块之前，JavaScript 并没有提供原生机制让开发者以模块化的方式进行开发。这也正是我们对 “打包” 这个概念熟悉的原因：使用工具抓取、处理并将我们的源码模块串联成可以在浏览器中运行的文件。

时过境迁，我们见证了诸如 webpack、Rollup 和 Parcel 等工具的变迁，它们极大地改善了前端开发者的开发体验。

然而，当我们开始构建越来越大型的应用时，需要处理的 JavaScript 代码量也呈指数级增长。包含数千个模块的大型项目相当普遍。基于 JavaScript 开发的工具就会开始遇到性能瓶颈：通常需要很长时间（甚至是几分钟！）才能启动开发服务器，即使使用模块热替换（HMR），文件修改后的效果也需要几秒钟才能在浏览器中反映出来。如此循环往复，迟钝的反馈会极大地影响开发者的开发效率和幸福感。

Vite 旨在利用生态系统中的新进展解决上述问题：浏览器开始原生支持 ES 模块，且越来越多 JavaScript 工具使用编译型语言编写。

# python
## Jupyter Notebook
pip install jupyter
jupyter notebook

# go
## 安装
https://go.dev/dl/

## 版本号
go version

# xxl-job
## 环境
Maven3+ 【mvn -v】
Jdk1.8+  【java -version】
Mysql5.7+

### Mysql版本
``` bash
mysql -u username -p
SELECT VERSION();
```

## 日志
----------- xxl-job job execute start -----------
----------- Param:
2024-02-27 02:00:00 [cn.eth.framework.logback.MdcLogAspect#jobAround]-[31]-[xxl-job, JobThread-25-1708970400043] mdc traceId: NC2ADPN1
2024-02-27 02:00:05 [com.xxl.job.core.thread.JobThread#run]-[179]-[xxl-job, JobThread-25-1708970400043] 
----------- xxl-job job execute end(finish) -----------


# powerjob
{% asset_img powerjob01.png %}

## processor
### map 大任务拆分
```java
@Slf4j
@Component
public class MapProcessorDemo extends MapProcessor { //继承MapProcessor
 
    private static final int batchSize = 100; //单批发送数据量
    private static final int batchNum = 2; //一共2批，默认上限为200批，再多就要适当调整batchSize大小了
 
    @Override
    public ProcessResult process(TaskContext context) throws Exception {
 
        if (isRootTask()) { //如果是根任务（说明map刚被调度到），则触发任务拆分
            log.info("根任务，需要做任务拆分~");
            List<SubTask> subTasks = Lists.newLinkedList();
            for (int j = 0; j < batchNum; j++) {
                SubTask subTask = new SubTask();
                subTask.siteId = j;
                subTask.itemIds = Lists.newLinkedList();
                subTasks.add(subTask); //批次入集合
                for (int i = 0; i < batchSize; i++) { //内部id集合，这里只是举例，实际业务场景可以是从db里获取的业务id集合
                    subTask.itemIds.add(i);
                }
            }
            return map(subTasks, "MAP_TEST_TASK"); //最后调用map，触发这些批次任务的执行
        } else { //子任务，说明批次已做过拆分，此时被调度到时会触发下方逻辑
            SubTask subTask = (SubTask) context.getSubTask(); //直接从上下文对象里拿到批次对象
            log.info("子任务，拿到的批次实体为：{}", JSON.toJSONString(subTask));
            return new ProcessResult(true, "RESULT:true");
        }
    }
 
    @Getter
    @NoArgsConstructor
    @AllArgsConstructor
    private static class SubTask { //定义批次实体（业务方可自由发挥）
        private Integer siteId; //批次id
        private List<Integer> itemIds; //批次内部所携带的id（可以是我们自己的业务id）
    }
}
```

### mapReduce 大任务拆分与归并
``` java
@Slf4j
@Component
public class MapProcessorDemo extends MapProcessor { //继承MapProcessor
 
    private static final int batchSize = 100; //单批发送数据量
    private static final int batchNum = 2; //一共2批，默认上限为200批，再多就要适当调整batchSize大小了
 
    @Override
    public ProcessResult process(TaskContext context) throws Exception {
 
        if (isRootTask()) { //如果是根任务（说明map刚被调度到），则触发任务拆分
            log.info("根任务，需要做任务拆分~");
            List<SubTask> subTasks = Lists.newLinkedList();
            for (int j = 0; j < batchNum; j++) {
                SubTask subTask = new SubTask();
                subTask.siteId = j;
                subTask.itemIds = Lists.newLinkedList();
                subTasks.add(subTask); //批次入集合
                for (int i = 0; i < batchSize; i++) { //内部id集合，这里只是举例，实际业务场景可以是从db里获取的业务id集合
                    subTask.itemIds.add(i);
                }
            }
            return map(subTasks, "MAP_TEST_TASK"); //最后调用map，触发这些批次任务的执行
        } else { //子任务，说明批次已做过拆分，此时被调度到时会触发下方逻辑
            SubTask subTask = (SubTask) context.getSubTask(); //直接从上下文对象里拿到批次对象
            log.info("子任务，拿到的批次实体为：{}", JSON.toJSONString(subTask));
            return new ProcessResult(true, "RESULT:true");
        }
    }
 
    @Getter
    @NoArgsConstructor
    @AllArgsConstructor
    private static class SubTask { //定义批次实体（业务方可自由发挥）
        private Integer siteId; //批次id
        private List<Integer> itemIds; //批次内部所携带的id（可以是我们自己的业务id）
    }
}
```

# 阿里云
## OSS
Python判断文件是否存在
```py
# 填写Object的完整路径，Object完整路径中不能包含Bucket名称。
exist = bucket.object_exists('exampleobject.txt')
# 返回值为true表示文件存在，false表示文件不存在。
if exist:
    print('object exist')
else:
    print('object not exist')
```

# PostMan/apiPost
body 脚本
``` js
apt.setRequestBody(
    {
        "no": "test",
        "param": JSON.stringify({"page":1,"pageSize":1})
    }
)
```