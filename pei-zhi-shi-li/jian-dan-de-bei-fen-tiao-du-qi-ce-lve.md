# 简单的备份调度器（策略）

这个例子创建了一个服务器备份命令的别称，能每10m重复一次。这个别称必须被放进 `execute-on-server-startup.conf` 来在每次服务器启动时开启。注意，CommandUtils没有备份功能，你需要你个其他有备份功能并且可以输入命令进行服务器备份的插件或者mod来实现这个备份命令。所以以下例子中 `backupPlugin startBackup` 必须替换为你的备份插件以及命令。

`aliases.conf`:

```text
aliases {
    backup {
        commands=[
            "*say Doing backup...",
            "*backupPlugin startBackup",
            "*cu execute delayed 10m backup"
        ]
        permission="admin.backup"
    }
}
```

`execute-on-server-startup.conf`:

```text
commands=[
    "*backup"
]
```

