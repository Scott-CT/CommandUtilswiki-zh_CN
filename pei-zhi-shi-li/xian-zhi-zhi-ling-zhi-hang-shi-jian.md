# 限制指令执行时间

背景：玩家赢得了彩票/奖励，胜利者并不在线，但是我们想把奖励给他。

奖励命令为

`/give %user_name% minecraft:cookie 5`

我们必须用 `%user_name%` 占位符，因为只有这个才能指定离线玩家。如果我们用了 `%player_name%` ，就无法指定离线玩家，也就是偏离了我们的本意了。关于PlaceholderAPI的安装，请看[这里](https://github.com/randombyte-developer/PlaceholderAPI/releases)或者是mcbbs你倒是自己找找啊！

延迟到胜利者上线的指令：

`/cu execute whenOnline %user_name% *give %user_name% minecraft:cookie 5`

这样是可以实现的，但是如果你只想让胜利者在接下来的三天内上线才能拿到奖励的话，就得用 `/cu execute if "*cu is before <timestamp>" "..."`指令：

`/cu execute whenOnline %user_name% *cu execute if "*cu is before <时间戳>" "*give %user_name% minecraft:cookie 5"`

但是我们怎么得到时间戳呢？我们可以使用一个 [JavaScript placeholder](https://github.com/ronaldburns/PlaceholderAPI/wiki/JavaScript-placeholders)

下面是一个我们的用例：

`config/placeholderapi/javascript/timestamp.js`

```text
function isEmpty(string) {
  return (!string || 0 === string.length());
}

function toNumberOrZero(string) {
  return isEmpty(string) ? 0 : parseInt(string);
}

with(new JavaImporter(java.lang, java.time, java.time.temporal, java.util, java.util.regex, java.text)) {
  var duration = args[0];
  var now = Instant.now();

  var durationRegex = Pattern.compile("(?:(\\d+)d)?(?:(\\d+)h)?(?:(\\d+)m)?(?:(\\d+)s)?(?:(\\d+)ms)?");

  var matcher = durationRegex.matcher(duration);

  if (!matcher.find()) {
    throw new IllegalArgumentException("'" + duration + "' isn't a valid duration! Use something like '3d2h12m30s800ms'")
  }

  var days = toNumberOrZero(matcher.group(1));
  var hours = toNumberOrZero(matcher.group(2));
  var minutes = toNumberOrZero(matcher.group(3));
  var seconds = toNumberOrZero(matcher.group(4));
  var milliseconds = toNumberOrZero(matcher.group(5));

  var time = now
    .plus(days, ChronoUnit.DAYS)
    .plus(hours, ChronoUnit.HOURS)
    .plus(minutes, ChronoUnit.MINUTES)
    .plus(seconds, ChronoUnit.SECONDS)
    .plus(milliseconds, ChronoUnit.MILLIS);

  var format = new SimpleDateFormat("HH:mm:ss.SSS-dd.MM.yyyy");
  out = format.format(java.util.Date.from(time));
}
```

\(翻译者不会写js，找翻译者莫得用处！\) 所以现在占位符 `%javascript_timestamp%` 使用了一个duration语句然后返回一个 `<时间戳>` ，这个 `<时间戳>` 可以被 `after` 和 `before` 调用。

这是我们的最终命令：

`/cu execute whenOnline %user_name% *cu execute if "*cu is before %javascript_timestamp_3d%" "*give %user_name% minecraft:cookie 5""`

我们可以把这个指令放到任何地方使用，例如手动使用，命令方块，或者用一个命令别称qwq。

如果我们想用命令别称调用这个指令，我们必须指定胜利者玩家。 我们想要的别称是 `/reward <player>` 。我们用 [`/cu execute parsed ...`](https://github.com/Scott-CT/CommandUtilswiki-zh_CN/wiki/%E6%89%A7%E8%A1%8C%E5%91%BD%E4%BB%A4#parsed-%E8%A7%A3%E6%9E%90) 指令来将玩家放入指令。

```text
aliases {
    "reward {0}" {
        commands=[
            "*cu execute parsed {0} *cu execute whenOnline %user_name% *cu execute if \"*cu is before %javascript_timestamp_3d%\" \"*give %user_name% minecraft:cookie 5\""
        ]
        permission="admin.give-reward"
    }
}
```

