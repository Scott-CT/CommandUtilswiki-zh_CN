# 对于一个sponge的bug的修复方法

有一个sponge的bug，这个bug会破坏CommandUtils的核心部分。

具体：[https://github.com/SpongePowered/SpongeCommon/issues/1922](https://github.com/SpongePowered/SpongeCommon/issues/1922)

我希望这个bug能在1.13之后会被修复，因为新加入的功能。

现在，CommandUtils把所有的指令的延迟都改为了 0 ticks，这个方案可能不会对你产生直接影响，但是成功解决了问题。

但是还有些问题：当延迟某个列表中所有的指令为0 ticks的时候（就像服务器启动指令或者命令别称列表），这些指令不按照顺序出牌，却通过一种表面上随机的方式运行。为了解决这个问题，CommandUtils靠特定指令列表来延迟指令。第一个指令延迟 0 ticks，第二个 1 tick， 等等。

这里只是记录一下某些表现，所以你不会得到不可预料的结果。

