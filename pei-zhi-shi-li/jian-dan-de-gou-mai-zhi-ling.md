# 简单的购买指令

```text
aliases {
  "buy basic" {
    commands=[
      """*cu execute if not "*cu has money %player% 300" "*msg %player% You need at least 300$!"""",
      """*cu execute if "*cu has payed %player% 300" "*give %player% minecraft:cookie 50" "*give %player% minecraft:apple 20" "*msg %player You bought the basic pack!" """
    ]
    permission=""
    cooldown="1h"
  }
}
```

