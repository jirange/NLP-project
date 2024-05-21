## 相关链接

[电商知识图谱链接预测挑战赛_学习赛_天池大赛-阿里云天池的团队 (aliyun.com)](https://tianchi.aliyun.com/competition/entrance/532033/information)

Baseline：[电商知识图谱链接预测baseline，TransE模型的pytorch实现_天池notebook-阿里云天池 (aliyun.com)](https://tianchi.aliyun.com/notebook/438624)

## 任务说明

知识图谱链接预测任务

本任务给出一个三元组的头实体h和关系r，要求选手预测对应的尾实体t。
输入：（头实体<\t>关系）
输出：（尾实体）
**样例**
**输入：**"化妆棉<\t>适用群体<\t>?"
**输出：**"女性"

## 赛题数据

OpenBG500是电子商务领域的知识图谱，包含500个关系，从阿里巴巴藏经阁开放商业知识图谱[AliOpenKG](https://kg.alibaba.com/index.html)中筛选采样得到。包括：

- OpenBG500_train.tsv : 训练集
- OpenBG500_dev.tsv : 验证集
- OpenBG500_test.tsv： 测试集，选手需为每条记录预测10个尾实体
- OpenBG500_entity2text.tsv：实体对应文本
- OpenBG500_relation2text.tsv：关系对应文本
- OpenBG500_example_pred.tsv: 提交结果示例

## 数据格式

- 实体关系对应文本数据，tsv格式

```
# OpenBG500_entity2text.tsv / OpenBG500_relation2text.tsv
实体id（关系id）<\t>实体（关系）对应文本<\n>
```

- 训练集/验证集数据，tsv格式：

```
# OpenBG500_train.tsv / OpenBG500_dev.tsv
头实体id<\t>关系id<\t>尾实体id<\n>
```

- 测试集/提交示例：

```
# OpenBG500_test.tsv，选手需要为每行记录补充10个预测的尾实体，提交格式参照OpenBG500_example_pred.tsv
头实体id<\t>关系id<\n>

# OpenBG500_example_pred.tsv
头实体id<\t>关系id<\t>尾实体1-id<\t>尾实体2-id<\t>...<\t>尾实体10-id<\n>
```

## 评测指标

**MRR、HIT@10、HIT@3、HIT@1**

尾实体预测的MRR（Mean Reciprocal Rank）：主评测指标，该评测指标是链接预测正确实体排名的倒数平均

HIT@1、HIT@3、HIT@10：描述了链接预测中得分最高的top K（K=1,3,10）个实体中包含正确实体的概率。

## 比赛相关

### 如何提交

选手需要为测试集中每条记录预测10个尾实体，在天池网站提交预测后的OpenBG500_test.tsv文件，提交示例见OpenBG500_example_pred.tsv文件。
说明： 一般来说，关系推理和链接预测任务中只需要预测出得分最高的实体即可，但为了获取正确的评测指标，所以请提供得分最高的十个实体，如果无法提供，请使用其他字符串填充。

### Baseline

https://github.com/OpenBGBenchmark/OpenBG500



