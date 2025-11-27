# 事务

__DSYSB__ 的原生事务有7个

[coinbase](t05_zh.md) 挖矿奖励，该事务不能主动创建
[create](t06_zh.md) 创建一个资产
[transfer](t07_zh.md) 转账
[exchange](t08_zh.md) 兑换
[deploy](t09_zh.md) 部署任务
[call](t0a_zh.md) 调用任务
[extension](t0b_zh.md) 增加资产或任务的生命力

除了 _coinbase_ 每一个事务的创建，都是用 _createrawtransaction_ 命令，该命令的简短写法也是 _create_，不要跟事务类型 _create_ 混淆


_createrawtransaction_ 的第一个参数是事务类型，第二个参数是一个包含了具体内容的 _JSON_ 数据，_JSON_ 数据的内部字段，没有顺序，并且字段名使用驼峰命名法

_createrawtransaction_ 成功后会返回一堆码，这堆码是该交易的二进制序列

_signrawtransaction_ 会用这个序列进行签名，生成包含签名的新的序列。你也可以用它的简写 _sign_

_sendrawtransaction_ 会用包含签名的序列作为参数，把这个事务发送到主程序 _dsysb_ 验证，如果通过，会加到事务池，并且广播到网络。其他节点收到后也会验证，如果通过，加到它们自己的事务池。这个命令也可以简写作 _send_

_decoderawtransaction_ 将 raw-data(hex) 字符串或者签名后的 raw-data 字符串作为参数，可以随时将序列转成事务内容查看

以上的命令中，除了 _sendrawtransaction_ 其他的命令只是显示返回结果，并不对程序内存数据和数据库做任何改变，所以可以放心使用

注意！每次 _sendrawtransaction_ 操作，都会向 _DSYSB_ 网络暴露 _from_ 地址的公钥，为了安全，一个暴露过 _from_ 地址的公钥不应该被使用，暴露的次数越多，该地址的私钥越容易被破解。__DSYSB__ 不是 _UTXO_ 模型，没有找零机制，但是增加了 _hier_ 字段，用来继承 _from_ 地址的一切资产. 指定 _hier_ 地址，相当于是指定了一个找零地址。如果不指定 _hier_ 地址，那么 _hier_ 地址默认就是 _from_ 地址本身


除了 _coinbase_ 每一个事务都会有手续费，手续费的算法是：
除了 _coinbase_ 每一个事务的 _JSON_ 数据中，都会有 _hier_ 字段，该字段继承了 _from_ 字段中的所有资产，同时弃用在这次事务中暴露过公钥的 _from_ 字段。如果 _hier_ 不填，则 _hier_ = _from_。这样 _from_ 不会被任何其他地址继承资产，不会从全局状态中删除，相当于不被弃用。 

```
手续费 = 序列的字节数 × 字节单价
```

在 _createrawtransaction_ 时，_JSON_ 数据中的 _nonce_ 和 _signer_ 是自动生成，非用户输入。

