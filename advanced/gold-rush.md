---
description: 为探险家们开辟的通道
---
# 淘金热

进化星球的居民们充满了探险的精神。每当一个新大陆被发现，许多先驱冒险者玩家选择放弃原有大陆上安逸的生活，将土地还给 EVE，以交换一块新大陆上的土地，在新的家园开拓新的疆土，谱写淘金热的传奇。EVE 将会从选出最优秀的一批勇士，率先开启新大陆上的征程。

## 参与方式

在新大陆开放前一定时间内，拥有旧大陆土地的玩家可以通过 [evolution.land](https://www.evolution.land/)，进入淘金热活动页面进行参与。

1. 进入进化星球官网 [evolution.land](https://www.evolution.land/) ，点击上方菜单栏中的「淘金热」，并链接您的数字钱包。

2. 选择「迁移的源大陆」以及「迁移的目标大陆」。

3. 添加旧大陆上的土地，供 EVE 回收。

4. 填写准备金，参与摇号。
   
   *注：准备金的 RING 数量越多，被抽中的概率越高。报名结束前，可以更换用于迁移的土地以及调整准备金的数量。*

5. 填写接收新大陆地块的地址。
   
   *注：待摇号结束后，淘金热玩家需要在活动页面，把源大陆地块交付给EVE，确认后，可到目标新大陆中领取地块。未抽中的玩家则需要在领取地块页面领回准备金。*

**淘金须知**

* 在交付土地前，请将地块上放置的使徒和道具及时取出。

* 增加为土地迁移预付的准备金，将提高摇号被选中的概率。准备金越高，被摇中的概率越大。

* 摇中后，锁定的土地将被系统回收并进行拍卖，准备金将被系统收取。未摇中则返还土地与准备金。

* 在报名截止 24 小时前，可以新增/删除地块、调整费用、修改新大陆地址。

* 新大陆地块将按照资源总量从高到低进行排序，旧大陆上摇中的玩家将以（地块资源总量 x 0.6 + 投入 RING x 0.4）的数值从高到底进行排序，玩家依次对应获得新大陆上的地块。

* 玩家可以在活动结束后，到活动公告页面查看获取的详情，同时玩家也可以选择往期的目标大陆查看历史活动数据详情。

## 摇号规则

摇号采用加权随机算法。从不同权重的 N 个元素中随机选择一个，并使得总体选择结果是按照权重分布的。

假设 4 块土地 A、B、C、D 参与摇号, 抵押金额分别为1、2、3、4，随机结果中 A：B：C：D 的比例要为1：2：3：4。

累加每个土地的权重 A(1)-B(3)-C(6)-D(10)，则 4 个元素的的权重管辖区间分别为 (0,1]、(1,3]、(3,6]、(6,10]。

然后随机出一个 (0,10] 之间的随机数。落在哪个区间，则该区间的元素即为按权重命中的元素。

要选取 M 块土地, 则可以按上面的方法选取一块土地后, 将该土地从集合中去除, 再反复按上面的方法抽取剩余的土地。

随机数的选取为块的哈希, 假如最终开奖块是 B, 则从 B - M 个块开始抽取, 一共抽取 M 个块的哈希作为抽奖的随机数。

一次 ropsten 上的抽奖举例：

```
假设 4 块土地 A、B、C、D 参与摇号, 抵押金额分别为 1、2、3、4
区间为 (0,1]、(1,3]、(3,6]、(6,10]
最终开奖块为 10000
 
第 9998 个块的哈希为：0x09cc4bb3ab6bb019e6bdca3a79d07c8d72919cf561489ac9101e4217b3cb8131
其对 1e19 求余加 1 为：0.094 RING
落在(0,1] 区间，对应土地 A 中奖
去除土地 A 后，B，C, D 区间分别为 (0,2]、(2,5]、(5,9]
 
第 9999 个块的哈希为：
0x9e552bad9996f391acea81a0d77556958e96314f897ed0abbb16d0d36a54668f
其对 9e18 求余加 1 为：1.087 RING
落在 (0,2] 区间, 对应土地 B 中奖
 
抽奖完毕，土地 A 和土地 B 中奖。
```

我们会以活动结束时间前的块高作为随机种子，按上述算法进行摇号，摇中的玩家即获得迁移资格。