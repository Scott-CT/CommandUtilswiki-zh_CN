# 执行命令

## If

`/cu execute if <conditionCmd> <commands...>`

条件指令 `conditionCmd` 先被执行，若条件指令输出 `CommandResult` 为 `SUCCESS`，其后的指令将会被执行。

你需要用 `"` 包裹所有的在 `if` 中的命令

```text
/cu execute if "*cu has money KitCrafty 30" "*say KitCrafty has at least 30$"
                 ^-- 条件命令                  ^-- 执行命令
```

更长的一个例子：

```text
/cu execute if "*cu has money KitCrafty 30" "*say KitCrafty has at least 30$" "*give KitCrafty minecraft:cookie 1" "*say and therefore he got one cookie"
                 ^-- 条件命令                     ^-- 执行命令 #1                  ^-- 执行命令 #2                    ^-- 执行命令 #3
```

你可以用任何这个插件的[条件指令](https://github.com/Scott-CT/CommandUtilswiki-zh_CN/wiki/%E6%9D%A1%E4%BB%B6%E5%91%BD%E4%BB%A4)或者其他插件的能返回一个有意义的 `CommandResult` 的指令。你可以在[我的discord服务器](https://discordapp.com/invite/ZHZ9Z8T)询问我问题。

你也可以对 `CommandResult` 取反。 `/cu execute if not ...`

## Delay

`/cu execute delayed <duration> <command>`

`duration` 在这里有更详细的介绍。

例子：`/cu execute delayed 2s say This was delayed by 2 seconds!`

注意：这个延迟在服务器重启中不会持续！所以并不推荐直接延迟1天。

## WhenOnline

`/cu execute whenOnline <playerName>|<playerUuid> <command>`

这允许自动在特定玩家上线时执行特定命令。这个执行命令可能在彩票等需求中特别有用，比如说彩票赢家在下线的时候赢了，当他上线的时候就会收到彩票奖励，给你个例子尝尝：

`/cu execute whenOnline Scott_CT *give $p minecraft:cookie 3`

`$p` 会被替换为命令对象，这里是 `Scott_CT`。`*`使命令被控制台执行，拥有所有权限。

如果玩家在 `execute whenOnline` 被执行时在线，其指令会被指令，不会出问题的。所以你可以把任何指令添加进这个执行指令里，使得其更加安全。因为玩家在线的时候你给他总是比较好的嘛对吧~

指令会按照排版顺序进行执行。

## Parsed （解析）

`/cu execute parsed <targetPlayerName>|<targetPlayerUuid> <command>` `/cu execute parsed Scott_CT *say The player name is %player%!`

依赖[PlaceholderAPI](https://github.com/Scott-CT/CommandUtilswiki-zh_CN/wiki/PlacehoderAPI-%EF%BC%88PAPI%EF%BC%89)解析特定指令。任何占位符都可以使用。如果你正在用[PAPI v4.5 pre release](https://github.com/Scott-CT/CommandUtilswiki-zh_CN/wiki/PlacehoderAPI-%EF%BC%88PAPI%EF%BC%89)，你甚至可以使用 `%user%` 来指定离线玩家。

