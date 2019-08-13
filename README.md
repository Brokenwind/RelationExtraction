# Entity-Relation-Extraction
Entity and Relation Extraction Based on TensorFlow. 基于 TensorFlow 的实体及关系抽取，2019语言与智能技术竞赛信息抽取任务解决方案。

more info: [2019语言与智能技术竞赛](http://lic2019.ccf.org.cn) 

## Abstract
该代码以管道式的方式处理实体及关系抽取任务，首先使用一个多标签分类模型判断句子的关系种类，然后把句子和可能的关系种类输入序列标注模型中，序列标注模型标注出句子中的实体，最终结合预测的关系和实体输出实体-关系列表：（实体1，关系，实体2）。

The code deals with entity and relationship extraction tasks in a pipeline way. First, a multi-label classification model is used to judge the relationship types of sentences. Then, the sentence and possible relationship types are input into the sequence labeling model. The sequence labeling model labels the entities in sentences, and finally combines the predicted relationship with the entity output entity-relationship list: (entity 1, relationship, entity 2).

相关模型：[Schema-based-Knowledge-Extraction](https://github.com/yuanxiaosc/Schema-based-Knowledge-Extraction) 该模型联合了关系预测和实体输出，是一个联合模型，同时输出关系和实体。

## [2019语言与智能技术竞赛](http://lic2019.ccf.org.cn/kg)

### 竞赛任务
给定schema约束集合及句子sent，其中schema定义了关系P以及其对应的主体S和客体O的类别，例如（S_TYPE:人物，P:妻子，O_TYPE:人物）、（S_TYPE:公司，P:创始人，O_TYPE:人物）等。 任务要求参评系统自动地对句子进行分析，输出句子中所有满足schema约束的SPO三元组知识Triples=[(S1, P1, O1), (S2, P2, O2)…]。
输入/输出:
(1) 输入:schema约束集合及句子sent
(2) 输出:句子sent中包含的符合给定schema约束的三元组知识Triples

**例子**
输入句子： ```"text": "《古世》是连载于云中书城的网络小说，作者是未弱"```

输出三元组： ```"spo_list": [{"predicate": "作者", "object_type": "人物", "subject_type": "图书作品", "object": "未弱", "subject": "古世"}, {"predicate": "连载网站", "object_type": "网站", "subject_type": "网络小说", "object": "云中书城", "subject": "古世"}]}```

### 数据简介
本次竞赛使用的SKE数据集是业界规模最大的基于schema的中文信息抽取数据集，其包含超过43万三元组数据、21万中文句子及50个已定义好的schema，表1中展示了SKE数据集中包含的50个schema及对应的例子。数据集中的句子来自百度百科和百度信息流文本。数据集划分为17万训练集，2万验证集和2万测试集。其中训练集和验证集用于训练，可供自由下载，测试集分为两个，测试集1供参赛者在平台上自主验证，测试集2在比赛结束前一周发布，不能在平台上自主验证，并将作为最终的评测排名。

## Getting Started
### Environment Requirements
+ python 3.6+
+ Tensorflow 1.12.0+

### 提交给官方评测的部分实验结果

|分类模型|序列标注模型|准确率|召回率|F1值|
|-|-|-|-|-|
|epochs6ckpt1000|epochs9ckpt4000|0.8549|0.7028|0.7714|
|epochs6ckpt13000|epochs9ckpt10000|0.8694|0.7188|0.7869|
|epochs6ckpt20000|epochs9ckpt17000|0.8651|0.738|0.7965|
|epochs6ckpt23000|epochs9ckpt20000|0.8714|0.7289|0.7938|
