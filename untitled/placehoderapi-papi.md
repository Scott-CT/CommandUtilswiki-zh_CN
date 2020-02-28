# PlacehoderAPI-（PAPI）

[PlaceholderAPI](https://ore.spongepowered.org/rojo8399/PlaceholderAPI)是一个很好的工具！你可以将它安装在你的服务器以获得对CommandUtils的最大使用。

如果正式版的功能还不够的话，你可以试试这款非正式发布，这个版本加入了 `%user%`占位符并且修复了一些bug，这个占位符甚至可以让你指定未加入服务器的玩家。

[PAPI非正式发布版本--RandomByte](https://github.com/randombyte-developer/PlaceholderAPI/releases/)

如果 `Scott_CT` 在线，那么下面的这个将起作用：

`/cmdUtils execute parsed Scott_CT *say %player% is cool!`

但是当他离线时，`%player%` 占位符就不会生效了。

为了解决这个问题，非正式发布版PAPI加入了 `%user%`：

`/cmdUtils execute parsed KitCrafty *say %user% is cool!`

这个指令也会在玩家离线时生效。

