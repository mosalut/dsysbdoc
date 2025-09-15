# 多个miner挖矿

为了充分利用系统的线程，可以启动多个 _dsysbminer_ 连接同一个 _dsysb_。

_dsysbminer_ 的默认 _http_ 端口是 8569

```bash
$ ./dsysbminer &
$ ./dsysbminer -http_port=8570 &
$ ./dsysbminer -http_port=8571 &
$ ./dsysbminer -http_port=8572 &
```

这样就在四个不同的端口启动了4个 _dsysbminer_

然后在用 _dsysbcmd_ 来开启挖矿时，最后要加上一个 _dsysbminer_ 的 _http_ 端口号，默认也是 8569，例如：

```bash
$ ./dsysbcmd start DUAv3s7ATF1s3ghkzPGDCTSFdgSTEfJw6g
$ ./dsysbcmd start DT4RqdQUPwkuJkhx7E145dvXUeAcwyKaN2 8570
$ ./dsysbcmd start DSxFbZR313JUkjAkx7fyHzciuQXuhaK2Sn 8571
$ ./dsysbcmd start DSrfva2rXhLtkzzhqbyEkn7TrKUL8DUGA9 8572
```

这样你就开启了四个 _dsysbminer_ 的挖矿，停止、暂停和恢复挖矿，也是在最后加上端口号，默认为 8569

注意！不要让在同一个 _dsysb_ 下的多个 _dsysbminer_ 用同一个钱包地址去挖矿，因为那样会造成重复计算，算力会浪费。

在计算挖矿时，同一个 _dsysb_ 在同一个时期，会个同一个区块数据给到所有连接它的 _dsysbminer_，而这些 _dsysbminer_ 的区块数据和钱包地址一样的情况下，_nonce_ 累加带来的数据变化也是一样的，所以以上的命令行举例中，使用的是不同的钱包地址
