# extension

_extension_ 延续资产或任务的生命力，延续的单价就是当时创建部署时的价格

## 字段
- _aot_ 资产或任务，0为资产，1为任务
- _from_ 延续者钱包地址
- _hier_ 继承者钱包地址
- _nId_ 资产或任务的ID
- _blocks_ 要延续的区块数量
- _nonce_ 防重放攻击
- _bytePrice_ 字节单价
- _signer_ 签名


以下是一个完整的 _extension_ 事务命令：

```bash
create extension '{"aot":0,"from":"DFAHcNwsoXGrDmSE7vTxriFGNM7tVDm17J","nId":"4ab40229733e4c964a87e19cb502e9517fc954b1f1fc7f3daffa02355e5eecf8","blocks":0,"bytePrice":2}'
```
