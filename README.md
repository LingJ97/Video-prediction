# Video-prediction
# WeChat_Big_Data_Challenge_DeepCTR_baseline

## 基于[DeepCTR](https://github.com/shenweichen/DeepCTR)实现的多任务学习模型[MMOE](https://dl.acm.org/doi/10.1145/3219819.3220007)
- 特征：本方案关注于模型，仅使用以下6个较为基础的原始特征：['userid', 'feedid', 'authorid', 'bgm_song_id', 'bgm_singer_id', 'videoplayseconds']


- 线上结果：

  | 得分     | 查看评论 | 点赞     | 点击头像 | 转发     |
  | -------- | -------- | -------- | -------- | -------- |
  | 0.633475 | 0.612465 | 0.613346 | 0.700479 | 0.643898 |


## 运行环境
 python 3.6
 deepctr==0.8.5
 tensorflow-gpu(tensorflow)
 pandas
 scikit-learn

### deepctr安装说明
- CPU版本
  ```bash
  $ pip install deepctr==0.8.5
  ```
- GPU版本
  先确保已经在本地安装`tensorflow-gpu`,版本为 **`tensorflow-gpu>=1.4.0,!=1.7.*,!=1.8.*`**，然后运行命令
    ```bash
    $ pip install deepctr==0.8.5 --no-deps
    ```

## 运行说明
1. 新建data目录，下载比赛数据集，放在data目录下并解压，得到wechat_algo_data1目录

2. ```
   python run_mmoe.py
   ```

   根据离线测试和线上提交修改`run_mmoe.py`中的`ONLINE_FLAG`变量

## 运行时间

在Tesla P40 24G GPU、E5-2650 v4 CPU机器上，训练时间为205s/epoch（6708846条样本）。

训练时显存占用为695MiB，内存占用为2.2G。

预测时间如下：

```
4个目标行为421985条样本预测耗时（毫秒）：352.331
4个目标行为2000条样本平均预测耗时（毫秒）：1.670
```

## 其他

[DeepCTR](https://github.com/shenweichen/DeepCTR)是一个易用、可扩展的深度学习点击率预测算法包。

添加特征时，仅添加feature_columns即可，无需改动模型；

在模型方面，DeepCTR包含20余个现有的CTR模型（如DeepFM、xDeepFM、DCN、AutoInt、DIN、FiBiNET等），可直接通过模型名调用。如需自定义模型，DeepCTR中也有很多高复用性的模型（例如DNN、FM、BiInteractionPooling、CIN、CrossNet等）。

预祝大家在本次大赛中取得好成绩！
