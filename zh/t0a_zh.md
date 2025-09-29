# call

_call_ 命令会调用一个任务，会执行任务的内容。再执行的时候发生的错误，例如有一个 _vData_ 位置的数据，读取了 _call_ 的参数，正好是0，而下一条命令，又除以这个位置的数据，那么将会发生错误，调用会失败，_vData_ 数据将回退到调用前。这种错误很类似运行时错误

## 字段
- _from_ 调用者钱包地址
- _hier_ 继承者钱包地址
- _taskId_ 调用的任务ID
- _params_ 调用参数
- _nonce_ 防重放攻击
- _bytePrice_ 区块单价
- _signer_ 签名


整个 _call_ 命令的长度，不允许超过65536，因为其他的字段还占有固定的空间，所以 _params_ 的长度不得超过 65333

以下是一个完整的 _call_ 事务命令：

```bash
$ ./dsysbcmd create call '{"taskId":"5183693c3eca42cc068af12ad104803f6b1b8a86d53063da35e77efb2cac720c","from":"DCUz2Z2D8C9YC7ZWaVBwAx16vygpAG4fST","params":[],"bytePrice":1}'
```

此处的 _taskId_ 根据你自己生成任务的实际情况填写，不要照抄

执行完后，可以通过

```bash
$ ./dsysbcmd gettask 5183693c3eca42cc068af12ad104803f6b1b8a86d53063da35e77efb2cac720c
```

看任务的状态，主要看他里面的vData是否已经改变
