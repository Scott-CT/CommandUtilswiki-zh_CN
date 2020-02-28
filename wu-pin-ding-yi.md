# 物品定义

如果你想用CommandUtils来指定特定物品，这里提供两种方式：

1. 使用正常的物品id：

   ```text
   minecraft:cookie
   minecraft:stone

   pixelmon:master_ball
   ```

2. 使用 [ByteItems ](https://ore.spongepowered.org/RandomByte/ByteItems)定义。当然你必须先安装这个插件。 用 `/byteItems save <id>` 来保存一个物品，然后重新在CommandUtils中使用。你可以通过[ByteItems wiki](https://github.com/randombyte-developer/byte-items/wiki)获取更多信息。

   ```text
   byte-items:test1
   byte-items:vote-reward
   ```

