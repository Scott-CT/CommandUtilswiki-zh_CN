# 条件命令

使用 [`/cu execute if ...`](https://github.com/Scott-CT/CommandUtilswiki-zh_CN/wiki/%E6%89%A7%E8%A1%8C%E5%91%BD%E4%BB%A4#if)来调用条件命令。

## Is before & after

`/cu is before <时间戳>`

`/cu is after <时间戳>`

返回 `SUCCESS` 如果时间戳是在设定 `时间戳` 之前或者之后。时间戳的格式必须遵守下面的要求：

```text
小时:分钟:秒.毫秒-天.月.年
00:36:25.300-19.05.2018
必须是24小时制，并且比如说5号，必须写05。
```

小贴士：你可能想要使用 [PlaceholderAPI](https://github.com/Scott-CT/CommandUtilswiki-zh_CN/wiki/PlacehoderAPI-%EF%BC%88PAPI%EF%BC%89) 通过其JavaScript能力来自动生成一个时间戳，请看这个[例子](https://github.com/Scott-CT/CommandUtilswiki-zh_CN/wiki/%E9%99%90%E5%88%B6%E6%8C%87%E4%BB%A4%E6%89%A7%E8%A1%8C%E6%97%B6%E9%97%B4)。

## Has money

`/cu has money <playerName>|<playerUuid> <money>`

返回 `SUCCESS` 如果玩家有和设定的钱数目相同或者超出的金钱数量。

## Has payed

`/cu has payed <playerName>|<playerUuid> <money>`

返回 `SUCCESS` 如果成功从玩家账户取出相应数额的钱。

## Has in hand

`/cu has in hand <playerName>|<playerUuid> <item> [quantity = 1]`

返回 `SUCCESS` 如果玩家在主手上有指定的物品。[阅读这个来学习如何指定物品](https://github.com/Scott-CT/CommandUtilswiki-zh_CN/wiki/%E7%89%A9%E5%93%81%E5%AE%9A%E4%B9%89)。

如果没有指定物品数量，其默认值是1。如果你你设定一个更高的量，玩家就必须有至少特定量的物品才可以成功操作。

## Has given from hand

`/cu has given from hand <playerName>|<playerUuid> <item> [quantity = 1]`

这个指令和 `/cu has in hand ...` 很相似，但是这个指令可以删除玩家主手的特定物品。这对于 'shop sell' 命令十分有用。[阅读这个来学习如何指定物品](https://github.com/Scott-CT/CommandUtilswiki-zh_CN/wiki/%E7%89%A9%E5%93%81%E5%AE%9A%E4%B9%89)。

如果没有指定物品数量，其默认值是1。如果你你设定一个更高的量，玩家就必须有至少特定量的物品才可以成功操作。

## Has in inventory

`/cu has in inventory <playerName>|<playerUuid> <item> [quantity = 1]`

返回 `SUCCESS` 如果玩家背包里有特定的物品。[阅读这个来学习如何指定物品](https://github.com/Scott-CT/CommandUtilswiki-zh_CN/wiki/%E7%89%A9%E5%93%81%E5%AE%9A%E4%B9%89)。

如果没有指定物品数量，其默认值是1。如果你你设定一个更高的量，玩家就必须有至少特定量的物品才可以成功操作。

## Has given from inventory

`/cu has given from inventory <playerName>|<playerUuid> <item> [quantity = 1]`

这个指令和 `/cu has in inventory ...` 很相似，但是这个指令可以删除玩家背包里的特定物品。[阅读这个来学习如何指定物品](https://github.com/Scott-CT/CommandUtilswiki-zh_CN/wiki/%E7%89%A9%E5%93%81%E5%AE%9A%E4%B9%89)。

如果没有指定物品数量，其默认值是1。如果你你设定一个更高的量，玩家就必须有至少特定量的物品才可以成功操作。

## Has permission

`/cu has permission <playerName>|<playerUuid> <permission>`

返回 `SUCCESS` 如果玩家有特定的权限。

## Has chance

`/cu has chance <chance>`

返回随机概率生成器的结果。`chance` 必须在 `0.0` 和 `1.0` 之间。`0.8` 代表 `80%` 。

