# exchange

_exchange_ 事务是兑换，它由两个 _transfer_ 组成。

第一个 _transfer_ 的 _from_ 地址，必须是第二个 _transfer_ 的 _to_ 地址

第一个 _transfer_ 的 _to_ 地址，也必须是第二个 _transfer_ 的 _from_ 地址

两个 _transfer_ 的 _assetId_ 不可相同，不填 _assetId_ 时代表 _DSB_，所以只能一个不填

以下是一个完整的 _transfer_ 事务命令：

```bash
$ ./dsysbcmd create exchange '[{"assetId":"799c410ec35a61fe49ed209c457e3ba9d7bb40bcc9b0c6a304d2269c26a43592","from":"DMwoNvKQn7JRoovVqh7P9JvyvTwsVrrr3q","to":"DD7iFJRyd8GpKcLr3zuai96pzAPspuZxPa","amount":10000,"bytePrice":10},{"assetId":"121639f97c3b296b67edc208948e4d041bd4755f7a98274d6284d152be4af679","from":"DCUz2Z2D8C9YC7ZWaVBwAx16vygpAG4fST","to":"DMwoNvKQn7JRoovVqh7P9JvyvTwsVrrr3q","amount":50000,"bytePrice":10}]' 
```
