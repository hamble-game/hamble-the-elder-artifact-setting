# a-new-game

HAMBLE - The Elder Artifact

新游戏策划

有两类非常有代表性的瓷砖游戏, roguelike和魔塔

roguelike以随机著称, 通过丰富的PRG的系统, 在随机的地图中深入探索, 完成游戏任务. 然而面对随机的系统, 玩家往往追求稳定的发展路线. 即不论装备如何成长, 都稳定的变强推进

而魔塔是标准的固定数值RPG, 较为简单的系统, 在固定的地图中寻找最优解

与roguelike的系统同样丰富, 但抛却了随机的固定数值RPG, 追求特定地图下的最优解, 是否会是一个合理的玩法?


## 规划

1. 完成一个详细的策划 (并建立一个开源组织, 把此项目转移过去)  
2. 提取核心部分制作粗略的demo
3. 制作一个固定地图的完整游戏
4. (制作更多地图或尝试随机产生地图)

---

**当前进展**

设定暂时先进行到这里, 制作可行性验证程度的demo

## 游戏部分

模仿roguelike的固定数值RPG

**设定 & 结局 & 开局 & 记分**  
+ 无随机的白盒: 没有任何随机元素, 怪物走最近路线, 多选时优先让abs(dx-dy)最小, 仍有多选时按照左右上下的顺序选择. 游戏所有机制明确告诉玩家
+ 战斗原因: 阻止邪教仪式, 阻止信奉生命之神的邪教的仪式
+ 上古装置: 随着一个奇异的彗星略过, 世界的平稳运行被打破, 发生各种灾难. 同时不知从何而来的邪教占据了一个远古遗迹, 抓了大量的牺牲品去进行仪式. 主角前去调查加救人. 随着深入探索, 发现世界的所有神其实是一个不知来源的上古装置驱动的, 邪教占据的巨大基地也是与装置一同被建造的, 彗星强化了装置的活动. 装置想要借助生命之神的模块来自主行动.
+ 正常结局1: 打断仪式击杀有上古装置加成的邪教头领
+ 正常结局2: 打断仪式后借助黑泥吞噬邪教头领, 并逃出遗迹 (之后召集一批人回来消灭了黑泥)
+ True End1: 信仰生命之神的结局. 不打断仪式, 被传送到上古装置, 击败满值生命设定的上古装置 (随着主角的生命之神达到高信仰, 上古装置更快满值, 放弃了邪教头领, 试图控制主角)
+ True End2: 无神论的结局. 搜集足够的线索, 直接找到上古装置, 击败接近满值生命设定的上古装置
+ 失败结局1: (主角死亡或行动过慢)上古装置占据了邪教头领, 世界步入崩坏
+ 失败结局2: 打断仪式后借助黑泥吞噬邪教头领, 未能逃出遗迹, 黑泥失控
+ 开局  
  不同的种族和职业  
  有不同额初始的神的喜好和装备, 个别有初始领悟和无法点开的领悟(牧师不允许点无神论)  
+ 计分: 世界的崩坏程度, 由回合数和上古装置的数值决定

**超大地图**  
+ 有陷阱的设定(始终能看到)
  - 三个阶段, 能看到, 能解除, 能回收
  - 分为 踏板 / 绊线 / 实体陷阱, 可以使用对应的道具替身来触发

**引入回合的机制**  
+ 玩家和激活的怪物每回合能行动(移动或攻击或释放技能)一次
+ 每三个回合, 玩家回复1%的血和蓝
+ 怪物每三个回合能额外行动一次
+ 怪物在以下情况会激活
  - 距离玩家小于等于3
  - 收到伤害且视野能看到玩家
+ 怪物在以下情况会取消激活
  - 距离玩家大于等于6且视野内没有玩家
+ boss随着回合数变强, 但增长越来越慢
+ 回合内机制 
  起始阶段-玩家行动阶段-玩家造成的环境伤害阶段-怪物行动阶段-怪物造成的环境伤害阶段-结束阶段  
  回合内的多次行动不会多次结算环境伤害, 同一个阶段内的事件, 先加入先触发  
  意味着先激活的怪物先行动

**领悟机制**  
+ 玩家最多5级, 初始能点开3个领悟, 每升一级可以多点开一个领悟, 预计10\~20个领悟, 每个领悟内3\~5个技能/法术
+ 每个领悟内的下一个技能/法术独立解锁, 总体是用的越多越能继续往后解锁
+ 技能是读回合cd的, 法术是耗蓝或耗血的, 个别是混合的
+ 预设玩家在通关时把能1个领悟学满, 2~3个接近满, 或者设定成只允许一个领悟能点满
+ 无神论  
  你隐藏了对神的想法
  - 所有神的好感值在计算加成时视为0
  - 所有神的好感值在计算加成时视为1000, 解锁条件:某个神的好感最高减最低达到3000
  - 所有神的好感值在计算加成时视为3000, :所有神在500\~-500之间
+ 灵巧身姿  
  你在战斗中非常灵巧
  - 普攻+2穿刺, 闪避+5, 盾牌不再提供抵抗值和格挡值
  - 普攻+2穿刺, 闪避+7 :闪避xx次攻击
  - 普攻+2穿刺, 闪避条到80即满 :在上次格挡后闪避xx次攻击
  - 普攻+2穿刺, 闪避后下回合可以多行动一次(不可叠加) :连续闪避一个怪物的攻击xx次, 期间不被其击中
+ 陷阱洞悉  
  你熟悉陷阱的构造
  - 陷阱等级+1 
  - 陷阱等级+1 :解除xx个陷阱
  - 陷阱等级+1 :部署xx个陷阱
  - 你不再触发陷阱, 能够把陷阱直接扔在怪物脚下并触发 :...
+ 元素支配  
  你能控制元素
  - 法术奥术冲击
  - 法术奥能护盾
  - 法术火球弹
  - 法术火墙
  - 释放这四个法术以及陨石术后仍能移动一次
+ 魔力修炼
  你能更加熟练的使用法术
  - ...
+ 死灵术  
  你曾师从巫师
  - 法术剧毒之触
  - 法术死亡缠绕
  - ...
+ 坚韧  
  你坚不可摧  
  - ...
+ 盾牌大师  
  - 格挡值+4 ...
  - ...
+ 武器精通  
  - 技能顺劈斩
  - ...

**伤害机制**  
+ 伤害来源有 法术/技能/普攻
+ 伤害类型有 打击/穿刺/火焰/奥术/剧毒
+ 每种伤害独立计算抵抗, 除剧毒外为伤害值减抵抗值是实际伤害
+ 剧毒的机制是在环境伤害阶段, 生命减去该值, 同时剧毒值下降剧毒抵抗的值
+ 格挡: 每次打击伤害判定时, 格挡条增加格挡率的数值, 当格挡条满时本次收到的打击伤害再额外减去格挡值
+ 闪避: 每次被普攻时, 闪避条增加闪避率的数值, 当闪避条满时无伤
+ 暴击: 每次普攻时, 暴击条增加暴击率的数值, 当暴击条满时计算双倍普攻加成
+ 怪物的格挡条/闪避条/暴击条初始是50%

**神的系统**  
(借鉴powder)  
+ 4~7个神, 有各自独立的喜好点数(也会影响上古装置的强度, 随着所有喜好的平方和增长)
+ 每个神在不同的喜好点数有各自的神恩和神罚
+ 无神论作为一个领悟
+ 起始默认较高的生命之神点数, 提供基础的生命值加成, 同时让玩家更容易选择培养这个神的好感
+ 设计思路是 神和技能的选择是玩法流派的主要区别, 预设 普攻+技能辅助/技能+普攻+法术辅助/法术 三种
+ 隐秘之神 Harpocrates Ἁρποκράτης 哈尔波克拉特斯
  - 加喜好
    + 对未激活的怪物造成伤害
    + 解除或回收陷阱
  - 减喜好
    + 同时激活多个怪物
    + 单个怪物激活过久
  - 对未激活的怪物的伤害加成
  - 提供一种陷阱法术
  - 神罚:脚边放陷阱(能反复使用的陷阱中最强的)
+ 战士之神 Ares Ἀρης 阿瑞斯
  - 加喜好
    + 同时激活多个怪物
    + 使用伤害技能
  - 减喜好
    - 法术击杀
  - 技能强度加成
  - 伤害技能
  - 神罚:被从天而降的神圣剑击中, 造成多次普攻伤害(做为神圣剑的唯一获取方式)
+ 法师之神 Medea Μήδεια 美狄亚
  - 加喜好
    + 消耗蓝
  - 减喜好
    + 普攻和伤害技能
    + 伤害技能击杀
  - 法术强度加成
  - 蓝量上限加成
  - 神罚:陨石术砸脸
+ 野蛮之神 Briareus Βριάρεώς 布里阿瑞俄斯
  - 加喜好
    + 普攻
  - 减喜好
    + 使用法术时, 如果喜好是正的, 先乘-1
    + 使用法术
    + 伤害技能击杀
    + 朝远离激活的怪物的方向移动
  - 普攻强度加成和法术抵抗加成
  - 伤害技能: 冲锋, 跳到一个未激活的怪物旁并对其进行两次普攻
  - 神罚:将玩家传送到决斗场(有场景debuff和奖励物品)
+ 生命之神 Lachesis Λάχεσις 拉刻西斯
  - 加喜好
    + 回血
  - 减喜好
    + 回蓝
  - 生命上限的加成
  - 回血法术
  - 神罚:剧毒冲击
+ 秩序之神 Eunomia Εὐνομία 欧诺弥亚
  - 加喜好
    + 普攻击杀
    + 满血满蓝
  - 减喜好
    + 对未激活的怪物造成伤害
    + 部署陷阱或触发陷阱
  - 更多的按回合的回复
  - blink法术: 下下个回合的结束阶段瞬移到指定位置(有视野的4格内, 期间站立不动)
  - 神罚:下一个怪物激活的回合给予其一个buff且能额外行动几次

**成就系统**  

一些相关设定

+ 工程师日志  
  散落在几个房间, 集齐作为解锁无神论的结局的条件, 也会给玩家一个技能和一些喜好值
+ 信徒笔记  
  散落在几个房间, 集齐作为解锁无神论的结局的条件, 也会给玩家一些喜好值
+ 冒险者日记  
  法师/战士, 集齐分别给玩家法术强度加成和技能伤害加成, 各个日记会记录一些怪物的弱点, 对该类怪物提供加成
+ 黑泥  
  让黑泥吞噬邪教头领  
  黑泥被设定成一个普攻后, 会按比例获得造成伤害的生命攻击抵抗的精英怪物, 行动力很高, 会攻击挡路的别的怪物  


## 实现部分

基于h5样板2.6.3

(这个设定用h5样板来做是否合适)

**项目构架**  
+ 拆成几个子项目
+ 用build脚本来组建
+ 设定部分
+ 文本部分
+ 图片/音乐等
+ 数据部分
+ 样板
+ 构建脚本

**大地图**  
+ 制作时每个块13*13, 同一时间只有9个是激活的
+ 一个26\*26作为当前区域, 每次移动结束后检查载入的9个块是否变化, 重新拼接活动区域

**游戏内提示**
+ 回满50血时弹框提示回血能加神的好感, 进入神的页面查看加成

