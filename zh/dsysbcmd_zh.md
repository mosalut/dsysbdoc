# 交互命令程序
_dsysbcmd_ 可以通过命令与dsysb 和 dsysbminer 进行交互。

使用格式：

```bash
$ ./dsysbcmd 选项 参数1 参数2 参数n...
```

### setconnnum
设置最大P2P连接数

参数：
- 连接数


### listnodes
列出已连接的节点


### listaddresses/getaddresses
列出本节点钱包地址


### newaddress
生成新的钱包地址


### validateaddress
验证钱包地址


### exportwallet
导出钱包地址.

参数：
- 钱包地址


### importwallet
导入钱包私钥.

参数：
- 钱包私钥


### createrawtransaction / create
创建交易

参数：
- 交易类型
1. create: 创建资产
2. transfer: 转账
3. exchange: 兑换
4. deploy: 部署任务
5. call: 调用任务
6. extension: 扩展资产或任务的生命周期
- JSON 字符串 Example: ./dsysb createrawtransaction '{"axid":"0xa....","type":"transfer","from":addressF,"to":addressTo,"Amount":100,"assetId":id}' returns a rawtransaction.
[JSON 字段详情](json_zh.md)


### decoderawtransaction / decode
交易解码

参数：
- 交易序列码


### signrawtransaction / sign
对交易进行签名

参数：
- 交易序列码


### sendrawtransaction / send
发送交易

参数：
- 已签名的交易序列码


### getaccount
查看账户

参数：
- 钱包地址


### getassets
列出资产


### getasset
查看资产内容

参数：
- 资产ID


### gettasks
列出任务


### gettask
查看任务内容

参数：
- 任务ID


### getstate
查看链上全局状态


### getblockchain
查看整个区块链

参数：
- 要显示的区块数，非必填，默认10


### getblockbyindex
通过高度获取区块内容

参数：
- 高度


### getblockbyhash
通过HASH获取区块内容

参数：
- HASH


### gettransaction
在最近的n个区块中，查找事务，并显示

参数：
- TXID
- n


### gettxinpool
在事务池中查找事务，并显示

参数：
- TXID


### listtransactionpool / listtxpool
列出事务池中所有事务


### getbalance
查看余额

参数：
- 钱包地址


### getassetbalance
查看资产余额

参数：
- 钱包地址
- 资产ID


### broadcast
广播消息

参数：
- 消息内容


### start
开始挖矿

参数：
- 要用于挖矿的钱包地址
- 要开始矿工程序的端口号，非必填，默认为8569


### stop
停止挖矿

参数:
- 要停止矿工程序的端口号，非必填，默认为8569


### pause
暂停挖矿

参数:
- 要暂停矿工程序的端口号，非必填，默认为8569


### recover
恢复挖矿

参数:
- 要恢复矿工程序的端口号，非必填，默认为8569


### atbs
钱包地址转字节数组

参数：
- 钱包地址


### nidtbs: Asset id or task id to bytes
资产ID 或任务ID 转字节数组

参数：
- 资产ID 或任务ID


### help
本文档


# 5. 常见问题

1. **发送交易数据失败**：如果用户创建了一个交易，decode 后发现用户的 nonce 值为 0，这时候在发送交易数据时会导致失败。需要用户先参与挖矿之后再次创建并发送交易才能成功。

2. **Miner 程序启动失败**：如果 miner 程序启动失败，可能是用户的 dsysb程序出了问题。

3. **创建个人资产失败**：在创建个人资产时，如果用户的总资产数小于需要消耗的聪数，就会导致创建失败，但可能看不到具体的日志。

4. **特殊字符导致创建失败**：在创建个人资产时，不能出现特殊字符，否则也会导致失败。

5. **错误的交易数据编解码**：如果用户对一个错误的交易数据进行编解码，`decoderawtransaction` 会报错，这时需要检查用户的交易数据是否正确。

6. **特殊字符导致数据错乱**：在创建个人资产时，如果输入了某种特殊字符，可能导致数据错乱，建议使用英文字母进行命名。

7. **转账失败**：转账时，如果 `from` 与 `to` 相同，也会导致失败。

8. **区块查找失败**：在查询区块时，如果输入了一个不存在的区块或者小于 0 的数字，也会导致失败。

9. **通过 Hash 值查找区块失败**：输入的 Hash 值不正确也会导致查询失败。

10. **创建重复资产失败**：创建完全一样的资产会导致创建失败。

11. **Level DB Not Found**：该错误表示数据库中的 Key 没有找到。
