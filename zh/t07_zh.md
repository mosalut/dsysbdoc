# transfer

_transfer_ 是转账事务

## 字段

- _from_ 发送者钱包地址
- _to_ 接收者钱包地址
- _amount_ 金额
- _assetId_ 要转账的资产ID，如果不填就是全0，同时代表 _DSB_
- _nonce_ 防止重放攻击
- _bytePrice_ 字节单价
- _signer_ 签名

以下是一个完整的 _transfer_ 事务命令：

```bash
$ ./dsysbcmd create transfer '{"from":"DCUz2Z2D8C9YC7ZWaVBwAx16vygpAG4fST","to":"DUAv3s7ATF1s3ghkzPGDCTSFdgSTEfJw6g","amount":300000000,"bytePrice":1}'
```

转账之后可以用 _getbalance_ 或 _getaccount_ 命令查看钱包余额或账户变动情况
