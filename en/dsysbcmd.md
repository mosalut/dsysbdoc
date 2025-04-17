# 准备工作

## 系统要求：

- 操作系统：Linux (64 位)，Windows 10 (测试不足)。

# 安装配置
- 步骤：访问 GitHub 地址 [xxx](#)
## 源码编译 : 使用go语言，go语言官方文档 https://go.dev/doc/install/source
## 下载安装包：在linux home目录下创建一个文件夹dsysb,把下载的三个可执行程序都放在这里，启动分别参考[dsysb 中文文档](dsysb.md)，与[dsysbminer 简体中文](dsysbminer.md)。


# 用户端程序
`dsysbcmd` 程序是最上层的用户端程序，可以通过命令与dsysb 和 dsysbminer 进行交互。到此为止，所有的准备工作都已经完成。

## 创建地址
首次使用的客户需要先创建地址，使用命令(该命令不依赖其余服务)：
```bash
./dsysbcmd newaddress
```


然后使用以下命令校验地址生成是否成功，使用命令(该命令不依赖其余服务)：
```bash
./dsysbcmd getaddresses
```

## 开始挖矿
获取原生代币，使用命令(该命令依赖dsysbminer服务)：
```bash
./dsysbcmd start  <address> 
```
示例
```bash
./dsysbcmd start D9U8tiQ1BTNBabTHiPh7vKvJQCFDkxQQnX
```

## 停止挖矿
如果想停止挖矿，使用命令(该命令依赖dsysbminer服务)：
```bash
./dsysbcmd stop
```

## 查看余额
挖矿成功之后，查看原生代币 Satoshi 的余额,使用命令(该命令依赖dsysb服务)：
```bash
./dsysbcmd getbalance <address> 
```
示例
```bash
./dsysbcmd getbalance D9U8tiQ1BTNBabTHiPh7vKvJQCFDkxQQnX
```


## 发起转账
如果用户想发起一个转账，需要手动构建命令，使用命令(该命令依赖dsysb服务)：
```bash
./dsysbcmd createrawtransaction transfer '{"from":"<from_address>","to":"<to_address>","amount":<amount>}'
```
示例
```bash
./dsysbcmd createrawtransaction transfer '{"from":"DPinAXhUPqFBVa5ixoneHWE9JyRNCQDVkG","to":"DAScYXVT5woYVCmGExBhsgGDsWr776JsAk","amount":10000}'
```

这将生成一个原始的交易串。

## 签名交易
对上一步骤构建的交易签名,使用命令(该命令不依赖其余服务)：
```bash
./dsysbcmd sign <transaction_data>
```
示例
```bash
./dsysbcmd sign 6e6e6b09737300000000440a0d444b0a00e8764817000000102700000000000080969800443955387469513142544e426162544869506837764b764a514346446b7851516e58020000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
```
得到签名后的交易数据，然后使用发送命令发送交易数据，此时正在挖矿的程序会打包这个交易。

## 创建自己的 Token
如果想创建属于自己的 Token（类似 ERC20），使用命令(该命令依赖dsysb服务)：
```bash
./dsysbcmd createrawtransaction create '{"name":"<token_name>","symbol":"<token_symbol>","decimals":<decimals>,"totalSupply":<total_supply>,"from":"<from_address>","price":<price>,"blocks":<blocks>}'
```
示例：
```bash
./dsysbcmd createrawtransaction create '{"name":"ccccc","symbol":"WWW","decimals":9,"totalSupply":100000000000,"from":"DPZWKbiAnZwMayjK9ttSb7iZQELYaU43Xc","price":10000,"blocks":11001}'
```

然后查看所有的 Token 列表，使用命令(该命令依赖dsysb服务)：
```bash
./dsysbcmd getassets 
```

##  Token 转账
Token 转账的格式与原生代币类似，使用命令(该命令依赖dsysb服务)：
```bash
./dsysbcmd createrawtransaction transfer '{"from":"<from_address>","to":"<to_address>","amount":<amount>,"assetId":"<asset_id>"}'
```
示例：
```bash
./dsysbcmd createrawtransaction transfer '{"from":"DPinAXhUPqFBVa5ixoneHWE9JyRNCQDVkG","to":"DAScYXVT5woYVCmGExBhsgGDsWr776JsAk","amount":10000,"assetId":"xxxxxxx"}'
```

## 查询 Token 余额
查询 Token 的余额，使用命令(该命令依赖dsysb服务)：
```bash
./dsysbcmd getassetbalance <address> <asset_id> 
```
示例：
```bash 
./dsysbcmd getassetbalance D9U8tiQ1BTNBabTHiPh7vKvJQCFDkxQQnX 
```

## decode解码交易数据
用户有时候需要查看自己生成的签名信息或者交易信息是否正确，使用命令(该命令不依赖其余服务)：

```bash
./dsysbcmd decoderawtransaction <transaction_data> 
```
示例：
```bash 
./dsysbcmd decoderawtransaction  6e6e6b09737300000000440a0d444b0a00e8764817000000102700000000000080969800443955387469513142544e426162544869506837764b764a514346446b7851516e58020000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
```
如果能够正确解码的就是数据格式没问题的

## 获取blockchain list 从最新块开始 高度降序
使用命令(该命令依赖dsysb服务)：：
```bash
./dsysbcmd getblockchain
```

## 通过索引或者第index个block
使用命令(该命令依赖dsysb服务)：
```bash 
./dsysbcmd getblockbyindex <index>
```
示例：
```bash 
./dsysbcmd getblockbyindex 100
```

## 通过hash值获取block
使用命令(该命令依赖dsysb服务)：
```bash 
./dsysbcmd getblockbyhash <block_hash>
```

## 通过交易hash值获取第n个block中的交易
使用命令(该命令依赖dsysb服务)：
```bash 
./dsysbcmd gettransaction <block_hash> <block_index>
```

## 获取未被区块打包的交易列表
使用命令(该命令不依赖其余服务)：
```bash 
./dsysbcmd listtransactionpool
```

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
