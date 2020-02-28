# 命令别称

命令别称的配置文件在 `config/command-utils/aliases.conf` 下。

配置举例：

```text
aliases {
    "give me {0} {1}" {
        commands=[
            "*give %player% {1} {0}",
            "*say %player% got {0} {1}!"
        ]
        permission="give-me"
    }
}
```

当执行 `/give me 30 minecraft:cookie` 时，你会获得30个曲奇（cookies）。当然前提是你有 `give-me` 权限来执行这个命令。

### 例子特点：

* `%player%` 代表执行命令的玩家的游戏ID
* `*`使命令通过后台执行，拥有所有权限。若没有 `*`，命令将会被当作指令源（command source）执行。

另外一个例子：公屏喊话

```text
"shout {...}" {
    commands=[
        """*tellraw @a ["",{"text":"<%player%> "},{"text":"{...}","bold":true}]"""
    ]
    permission=shout
}
```

### 例子特点

* `{...}` 是一个 `vararg` （可变参数函数）。这个可变参函在每个命令别称只能有一个，并且只会被在最后使用。可变参函捕捉所有从其所在位置直到末尾的所有东西。

如果你安装了 [PlaceholderAPI](https://github.com/Scott-CT/CommandUtilswiki-zh_CN/wiki/PlacehoderAPI-%EF%BC%88PAPI%EF%BC%89)，你可以在命令中使用所有的占位符（placeholder）。

## 冷却

```text
aliases {
    "give me {0} {1}" {
        commands=[
            "*give %player% {1} {0}",
            "*say %player% got {0} {1}!"
        ]
        permission="give-me"
        cooldown="1h"
    }
}
```

