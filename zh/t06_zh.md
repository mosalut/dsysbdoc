# create

创建资产，它依靠自身数据，计算出一个 _assetId_，如果该 _assetId_ 重复，那么将创建失败

为了防止链上有很多无用的垃圾资产数据，__DSYSB__ 认为，如果一个资产没有人维护了，那它就该失效，后面的区块中，不再保留它。为了有一个失效机制，我们给资产一个生命力的字段，生命力的单位是区块，并且生命力是有价格的。它的单价，也是之后用到这个资产事务的手续费单价的门槛。即用到这个资产的事务的手续费单价 _bytePrice_，必须大于等于这个资产的生命力单价

生命力的费用由资产创建者负担

## 字段

- _name_ 资产名称，5 - 10 个数字或字母
- _symbol_ 资产简写，3 - 5 个数字或字母
- _decimals_ 小数位数
- _totalSupply_ 总供应量
- _price_ 生命力单价
- _blocks_ 生命力
- _from_ 创建者钱包地址
- _nonce_ 防止重放攻击
- _bytePrice_ 字节单价
- _signer_ 签名

以下是一个完整的 _create_ 事务命令：

```bash
$ ./dsysbcmd create create '{"name":"aaaaaa","symbol":"AAA","decimals":8,"totalSupply":1000000000000000,"price":10,"blocks":10000,"from":"D892kxbavZUUmj5DHoVCJAFUWsWMeJCGQY","bytePrice":1}'
```

等两个区块左右，可以用

```bash
$ ./dsysbcmd getassets
```

列出所有资产 _assetId_ ，所以看到新增的资产的 _assetId_

再用

```bash
$ ./dsysbcmd getasset <assetId>
```

看具体的资产内容，找到自己的资产，并记住他的资产ID，以后用于转账等操作

资产中有一个 _remain_ 字段，表示还剩多少生命力
