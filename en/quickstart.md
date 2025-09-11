# Quick Start

## 系统支持
- Linux
- Windows

## 安装

你可以从源代码进行编译，或者使用编译好的文件

以下提供了下载路径：


| Linux | Windows |
| --- | --- |
| [v0.0.1](#) | [v0.0.1](#) |
  

_注意，如果你从其他地方下载，可能会下载到篡改过的文件_

解压下载的文件

- __dsysb__：主程序，他负责与其他节点通信，并且验证其他节点过来的数据，同时也负责读写本地数据库

- __dsysbminer__：矿工程序，如果你要挖矿请启动它

- __dsysbcmd__：命令程序，他负责用户与 __dsysb__ 以及 __dsysbminer__ 交互

- __config__：配置文件

- __removedatabase__：__Linux__ 中，清空节点中区块链数据的脚本，防止手动用rm误删到钱包，__windows__ 下不需要该文件

## 启动 dsysb

进入到解压后的目录，并运行：

```
./dsysb -network_id=1 -remote_host=<ip:port>
```

\-network\_id指定了你要加入的网络，共支持 0 - 16, 
- 0: __Mainnet__ 编写这个文档时，__Mainnet__ 还没有上线，默认
- 1 - 15: __Testnet__ 编写这个文档时，只有1号 __Testnet__，其他预留

_\-remote\_host_，通常你可以通过配置文件中提供的节点列表 _remote\_hosts_ 进入 __DSYSB__ 网络，命令行中的 _\-remote\_host_ 可以追加一个你熟知的节点，如果配置文件中的节点为空，那么你必须通过 _\-remote\_host_ 指定一个节点才可以进入网络

关于 __dsysb__ 命令的其他参数，请看[这里](#)

## 启动 dsysbminer
如果你想参与挖矿，在 __dsysb__ 程序已经启动的情况下，在用另一个窗口到相同的目录下，输入：

```
./dsysbminer
```

这是挖矿程序在后台启动了，但是并没有开始挖矿，需要 __dsysbcmd__ ，来控制他开始、停止、暂停和恢复挖矿。

## 使用 dsysbcmd

在 __dsysb__ 程序已经启动的情况下，在用另一个窗口到相同的目录下，输入：

#### 显示区块高度

```
./dsysbcmd getindex
```

#### 生成钱包地址

```
./dsysbcmd newaddresses // 果是第一次生成，会创建钱包数据库 wallet.db
```

#### 列出地址

```
./dsysbcmd getaddresses // 列出本节点下所有钱包地址
```

#### 开始挖矿

```
./dsysbcmd start <wallet address>
```
_start_选项需要一个矿工的钱包地址


#### 停止挖矿

```
./dsysbcmd stop 
```

#### 暂停挖矿

```
./dsysbcmd pause
```

#### 恢复挖矿

```
./dsysbcmd recover 
```

如果你通过挖矿，或者他人想你的钱包地址转账，使你的钱包地址有了足够的DSB或者其他资产，那么你可以把它们转给其他人。


#### 转账事务

```
./dsysbcmd createrawtransaction transfer '{"from":"<发送的地址>","to":"<接收的地址>","amount":<金额>,"bytePrice":<字节单价>}'

./dsysbcmd createrawtransaction transfer '{"from":"D892kxbavZUUmj5DHoVCJAFUWsWMeJCGQY","to":"DBwz7C6u6ggHJXnERzWt2co8yT5gTFtBw5","amount":10000000,"bytePrice":10}'
```

- 执行以上命令会显示一个事务数据，这个数据就是这个事务的二进制内容。
- _createrawtransaction_ 表示要创建一个事务，可以简写成 _create_
- 在命令中，单引号中的内容，事实上都是一个 _JSON_ 数据
- 在命令中，所有 _JSON_ 外的选项或参数，都是小写。所有 _JSON_ 字段名，都用驼峰命名法，比如这里的 _bytePrice_
- _JSON_ 字段没有先后顺序
- 在命令中，所有输入和输出的单位都是 _satoshi_，比如这里的 _amount_ 和 _bytePrice_ 的值
- _transfer_ 表示事务的类型是转账
- 每个事务都需要一个 _bytePrice_ 来指定发送者愿意为这个事务提供的字节单价
- 如果 _JSON_ 数据中，没有指定 _assetId_ ，那么就会转 __DSB__。否则将转指定的资产。

```
	字节单价 × 事务数据的字节数 = 手续费
```

矿工为了自己的利益，会将事务池中的事务，按字节单价进行降序排序，然后再打包。

将以上显示的事务数据转回明文

#### 将事务解码

```
./dsysbcmd decoderawtransaction <事务数据>
```

- _decoderawtransaction_ 可以简写为_decode_
- 显示后的内容中会有该笔事务的_txid_等信息
- 此时signature信息都为0

#### 对事务签名

```
./dsysbcmd signrawtransaction <事务数据>
```

- _signrawtransaction_ 可以简写为_sign_
- 显示签名后的事务数据

如果此时你再用 _decoderawtransaction_ 解码签名后的事务数据，你会看到 _signature_ 已经有非0值了

```
./dsysbcmd decode <签名后的事务数据>
```

注意：在复制事务数据时，不要把空格，换行等符号复制进去。

最后我们要把签名后的事务数据发送给主程序，如果主程序验证通过，将会把这笔事务广播到网络，其他节点就会接收到并验证

```
./dsysbcmd sendrawtransaction <签名后的事务数据>
```

- _sendrawtransaction_ 可以简写为 _send_

如果这时没有任何输出，那么恭喜你，成功的发送了一笔事务

现在创建一个资产

#### 创建资产的事务

```
./dsysbcmd create create '{"name":"<5-10个字母或数字>","symbol":"<3-5个字母或数字>","decimals":<表示小数点后位数>,"totalSupply":<总供应量>,"from":"<创建者钱包地址>","price":<区块单价>,"blocks":<生命力>,"bytePrice":20}'

'{"name":"aaaaaa","symbol":"AAA","decimals":8,"totalSupply":1000000000000000,"price":10,"blocks":10000,"from":"D892kxbavZUUmj5DHoVCJAFUWsWMeJCGQY","bytePrice":1}'
```

- 此处的第一个 _create_ 是 _createrawtransaction_ 的简写，第二个 _create_ 表示事务的类型是创建资产
- 通过一个资产的所有字段内容，可以计算出它的 _assetId_，如果一个 _assetId_ 已经存在，说明已经有相同的资产存在了，所以会创建失败
- 考虑到如果对资产不限制，那么很多资产创建到链后，没人关心，没人使用，会一直延续在未来的区块中，变成垃圾，所以有以下措施
- _blocks_ 表示这个资产的生命力，它是以区块为单位的，这里是10000，也就从这个资产到链上，到它经过10000个区块后，如果没有人愿意为它续命，那么它将不复存在。当然，之前区块中的记录还是有的
- _price_ 表示生命力单价，创建一个资产除了要付手续费给矿工，还要为其生命力支付 __DSB__。每次记账的矿工，拿到的是它的单价，一共可以拿10000次。而不是资产创建时，一次性拿走所有的生命力费用，事实上创建的时候还没有消耗 _blocks_，所以这时记账的矿工，将不会收到生命力费用。之后的记账才收到
- _price_ 的另一个作用是手续费门槛，也就是之后用 _transfer_ 转账这个资产的 _bytePrice_ 必须大于等于这个 _price_，并且用 _extension_ 延续资产生命时的也沿用当前 _price_
- 这个资产创建后，都会在 _from_ 地址的余额下，初始为 _JSON_ 中的 _totalSupply_
- 关于这一点，这个设计有过一个缺陷，因为 _from_ 地址在发送事务时会暴露公钥，用于其他节点验签。暴露公钥的地址相对不安全，而现在初始的 _totalSupply_ 都在这个地址中，需要转到新的地址，但是这期间就可能发生被盗走。由于写这个文档的时候，__Mainnet__ 还没有上线，是在 __Testnet__ 中供社区使用，所以这一版本，不做改动。之后会在_JSON_中加入_to_地址，用来接收初始的 _totalSupply_

然后通过 _signrawtransaction_ 和 _sendrawtransaction_ 来发送这笔事务。

事务被进入到事务池后，并没有立即被打包，因为主程序的仍然还在等待其他事务进入事务池。

当自己的矿工程序挖出一个块时，主程序才会把当前事务池中的事务打包到新的区块中，最多打包511个，因为还有挖矿奖励事务：_coinbase_，总共512个。剩下延后到后面的区块

新区块打包之后并不会立刻到链上，需要矿工程序把它挖出来，或者说是计算出来，这是 __PoW__ 的标准做法，在此不做赘述

所以当你看到矿工程序显示目前在挖第10个块，这是你发送的事务，那么这个事务将在第11个块挖出来后，才到链上，才能查询到。而11个块挖出来时，矿工程序显示的是在挖12个块，所以看上去是隔了一个块（10,12）

等到创建资产的事务成功到链上之后，我们可以查看它

#### 列出资产

```
./dsysbcmd getassets
```

- _getassets_ 会列出所有链上资产的 _assetId_

#### 产看资产

```
./dsysbcmd getasset <assetId>
```

- _getassets_ 会显示一个资产的详细内容

#### 查看链上事务

```
./dsysbcmd gettransaction <txid>
```

#### 列出池中事务

```
./dsysbcmd listtransactionpool
```

- _listtransactionpool_ 可以简写成 _listtxpool_。
- 事务池里的事务被打包后，将移出事务池。


#### asset转账

```
./dsysbcmd createrawtransaction transfer '{"from":"<发送的地址>","to":"<接收的地址>","assetId":<assetId>,"amount":<金额>,"bytePrice":<字节单价>}'

./dsysbcmd createrawtransaction transfer '{"from":"D892kxbavZUUmj5DHoVCJAFUWsWMeJCGQY","to":"DBwz7C6u6ggHJXnERzWt2co8yT5gTFtBw5","assetId":"121639f97c3b296b67edc208948e4d041bd4755f7a98274d6284d152be4af679","amount":10000000,"bytePrice":10}'
```

- 同样还要经过 _signrawtransaction_，_sendrawtransaction_ 并等待出两个块

#### 所有事务

- _coinbase_ 挖矿奖励
- _create_ 创建资产
- _transfer_ 转账
- _exchange_ 兑换
- _deploy_ 部署任务
- _call_ 调用任务
- _extension_ 延续资产或任务的生命力

Quick Start中没有提到的事务，将在详细教程中描述
