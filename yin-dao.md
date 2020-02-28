# 引导

这一页将帮助你了解本插件的基本结构。

## 概览

所有的以 `*` 开头的指令会被控制台执行，所以这种指令拥有所有的权限。

所有的在任何配置文件和本插件里的命令都可以包含来自 PlaceholderAPI 的占位符。

本插件中每一个子指令都有特定的权限节点，但是最终是由控制台或者管理员来执行这些指令，所以只要给管理员们 `command-utils` 权限即可。

根命令：

* `/commandUtils`
* `/cmdUtils`
* `/cu`

  这三个指令实际上没有任何区别，但是 `/cu` 最短。23333

## 命令别称

命令别称基本上就是一种用户自定义的指令。举个例子，一个别称可以出发 `/give` 和 `/say` 指令。在配置文件中大概看起来是这样：

```text
"giveMeCookies" {
  commands = [
    "*give %player% minecraft:cookie 3",
    "*say %player% is hungry and just got three cookies!"
  ]
}
```

[关于命令别称的详细介绍](https://github.com/Scott-CT/CommandUtilswiki-zh_CN/wiki/%E5%91%BD%E4%BB%A4%E5%88%AB%E7%A7%B0)

## `execute` （执行）命令

这种指令可变更指令的执行。举个例子，执行被延迟了，或者只有满足某个条件才可以被执行。命令如下：

* `/cmdUtils execute whenOnline`
* `/cmdUtils execute delayed`
* `/cmdUtils execute if`
* `/cmdUtils execute parsed`

[关于执行命令的详细介绍](https://github.com/Scott-CT/CommandUtilswiki-zh_CN/wiki/%E6%89%A7%E8%A1%8C%E5%91%BD%E4%BB%A4)

## 条件命令

这种命令一般与 `/cmdUtils execute if` 联合使用。如果某种条件被满足，这个指令就会输出 'success signal'（成功信号）。这个信号是一种原版对于指令执行的反馈。这种反馈在sponge名叫 `CommandResult`，被用于原版的与命令方块使用的比较器。条件命令的好处是其他插件可以添加条件判断，并且其他插件添加的条件判断也可用被 `/cmdUtils execute if` 指令调用。指令列表如下：

* `/cmdUtils is before`
* `/cmdUtils is after`
* `/cmdUtils has money`
* `/cmdUtils has payed`
* `/cmdUtils has in hand`
* `/cmdUtils has given from hand`
* `/cmdUtils has permission`

[关于条件命令的详细介绍](https://github.com/Scott-CT/CommandUtilswiki-zh_CN/wiki/%E6%9D%A1%E4%BB%B6%E5%91%BD%E4%BB%A4)

## 其他

本插件提供一个叫 `execute-on-server-startup.conf`的配置文件，可用于在服务器开启时执行某些指令。

[详细信息](https://github.com/Scott-CT/CommandUtilswiki-zh_CN/wiki/%E5%9C%A8%E6%9C%8D%E5%8A%A1%E5%99%A8%E5%90%AF%E5%8A%A8%E6%97%B6%E6%89%A7%E8%A1%8C%E6%8C%87%E4%BB%A4)

