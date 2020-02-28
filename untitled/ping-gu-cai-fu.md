# 评估财富

```text
aliases {
  "wealth {0}" {
    commands=[
      """*cu execute if "*cu has money {0} 12" "internal_wealth_1 {0}"""",
      """*cu execute if not "*cu has money {0} 12" "*say {0} is broke!""""
    ]
    permission=""
  }
  "internal_wealth_1 {0}" {
    commands=[
      "*say {0} has a little money",
      """*cu execute if "*cu has money {0} 25" "*say and even a bit more!""""
    ]
    permission=admin
  }
}
```

用 `/weath <player>` 来执行。

