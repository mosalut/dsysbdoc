# DSYSB 任务指令集

| 指令名 | 指令号 | 指令号16进制表示 | 操作 |
| --- | --- | --- | --- |
| [ins_movsb](#ins_movsb) | 0 | 0x0 | copy字节数组 | 
| [ins_mov8](#ins_mov) | 1 | 0x1 | copy 8位 |
| [ins_mov16](#ins_mov) | 2 | 0x2 | copy 16位 |
| [ins_mov32](#ins_mov) | 3 | 0x3 | copy 32位 |
| [ins_mov64](#ins_mov) | 4 | 0x4 | copy 64位 |
| [ins_add8](#ins_add) | 5 | 0x5 | 8位有符号加法 |
| [ins_add16](#ins_add) | 6 | 0x6 | 16位有符号加法 |
| [ins_add32](#ins_add) | 7 | 0x7 | 32位有符号加法 |
| [ins_add64](#ins_add) | 8 | 0x8 | 64位有符号加法 |
| [ins_add8u](#ins_add) | 9 | 0x9 | 8位无符号加法 |
| [ins_add16u](#ins_add) | 10 | 0xa | 16位无符号加法 |
| [ins_add32u](#ins_add) | 11 | 0xb | 32位无符号加法 |
| [ins_add64u](#ins_add) | 12 | 0xc | 64位无符号加法 |
| [ins_sub8](#ins_sub) | 13 | 0xd | 8位有符号减法 |
| [ins_sub16](#ins_sub) | 14 | 0xe | 16位有符号减法 |
| [ins_sub32](#ins_sub) | 15 | 0xf | 32位有符号减法 |
| [ins_sub64](#ins_sub) | 16 | 0x10 | 64位有符号减法 |
| [ins_sub8u](#ins_sub) | 17 | 0x11 | 8位无符号减法 |
| [ins_sub16u](#ins_sub) | 18 | 0x12 | 16位无符号减法 |
| [ins_sub32u](#ins_sub) | 19 | 0x13 | 32位无符号减法 |
| [ins_sub64u](#ins_sub) | 20 | 0x14 | 64位无符号减法 |
| [ins_mul8](#ins_mul) | 21 | 0x15 | 8位有符号乘法 |
| [ins_mul16](#ins_mul) | 22 | 0x16 | 16位有符号乘法 |
| [ins_mul32](#ins_mul) | 23 | 0x17 | 32位有符号乘法 |
| [ins_mul64](#ins_mul) | 24 | 0x18 | 64位有符号乘法 |
| [ins_mul8u](#ins_mul) | 25 | 0x19 | 8位无符号乘法 |
| [ins_mul16u](#ins_mul) | 26 | 0x1a | 16位无符号乘法 |
| [ins_mul32u](#ins_mul) | 27 | 0x1b | 32位无符号乘法 |
| [ins_mul64u](#ins_mul) | 28 | 0x1c | 64位无符号乘法 |
| [ins_quo8](#ins_quo) | 29 | 0x1d | 8位有符号除法 |
| [ins_quo16](#ins_quo) | 30 | 0x1e | 16位有符号除法 |
| [ins_quo32](#ins_quo) | 31 | 0x1f | 32位有符号除法 |
| [ins_quo64](#ins_quo) | 32 | 0x20 | 64位有符号除法 |
| [ins_quo8u](#ins_quo) | 33 | 0x21 | 8位无符号除法 |
| [ins_quo16u](#ins_quo) | 34 | 0x22 | 16位无符号除法 |
| [ins_quo32u](#ins_quo) | 35 | 0x23 | 32位无符号除法 |
| [ins_quo64u](#ins_quo) | 36 | 0x24 | 64位无符号除法 |
| [ins_inc8](#ins_inc) | 37 | 0x25 | 8位有符号自增 |
| [ins_inc16](#ins_inc) | 38 | 0x28 | 16位有符号自增 |
| [ins_inc32](#ins_inc) | 39 | 0x29 | 32位有符号自增 |
| [ins_inc64](#ins_inc) | 40 | 0x2a | 64位有符号自增 |
| [ins_inc8u](#ins_inc) | 41 | 0x2b | 8位无符号自增 |
| [ins_inc16u](#ins_inc) | 42 | 0x2c | 16位无符号自增 |
| [ins_inc32u](#ins_inc) | 43 | 0x2d | 32位无符号自增 |
| [ins_inc64u](#ins_inc) | 44 | 0x2e | 64位无符号自增 |
| [ins_dec8](#ins_dec) | 45 | 0x2f | 8位有符号自减 |
| [ins_dec16](#ins_dec) | 46 | 0x30 | 16位有符号自减 |
| [ins_dec32](#ins_dec) | 47 | 0x31 | 32位有符号自减 |
| [ins_dec64](#ins_dec) | 48 | 0x32 | 64位有符号自减 |
| [ins_dec8u](#ins_dec) | 49 | 0x33 | 8位无符号自减 |
| [ins_dec16u](#ins_dec) | 50 | 0x34 | 16位无符号自减 |
| [ins_dec32u](#ins_dec) | 51 | 0x35 | 32位无符号自减 |
| [ins_dec64u](#ins_dec) | 52 | 0x36 | 64位无符号自减 |
| [ins_write_uint8](#ins_write_uint) | 53 | 0x37 | 从寄存器写uint8到vData |
| [ins_write_uint16](#ins_write_uint) | 54 | 0x38 | 从寄存器写uint16到vData |
| [ins_write_uint32](#ins_write_uint) | 55 | 0x39 | 从寄存器写uint32到vData |
| [ins_write_uint64](#ins_write_uint) | 56 | 0x3a | 从寄存器写uint64到vData |
| [ins_read_uint8](#ins_read_uint) | 57 | 0x3b | 从vData读uint8到寄存器 |
| [ins_read_uint16](#ins_read_uint) | 58 | 0x3c | 从vData读uint16到寄存器 |
| [ins_read_uint32](#ins_read_uint) | 59 | 0x3d | 从vData读uint32到寄存器 |
| [ins_read_uint64](#ins_read_uint) | 60 | 0x3e | 从vData读uint64到寄存器 |
| [ins_eq](#ins_eq) | 61 | 0x3f | 比较等于 |
| [ins_gt](#ins_gt) | 62 | 0x40 | 比较大于 |
| [ins_lt](#ins_lt) | 63 | 0x41 | 比较小于 |
| [ins_gteq](#ins_gteq) | 64 | 0x42 | 比较大于等于 |
| [ins_lteq](#ins_lteq) | 65 | 0x43 | 比较小于等于 |
| [ins_eq_bytes](#ins_eq_bytes) | 66 | 0x44 | 比较字节序 |
| [ins_height](#ins_height) | 67 | 0x45 | 获取当前区块高度 |
| [ins_transfer_dsb_from_caller](#ins_transfer_dsb_from_caller) | 68 | 0x46 | 任务调用者向任务发起者转DSB |
| [ins_transfer_dsb_to_caller](#ins_transfer_dsb_to_caller) | 69 | 0x47 | 任务发起者向任务调用者转DSB |
| [ins_transfer_from_caller](#ins_transfer_from_caller) | 70 | 0x48 | 任务调用者向任务发起者转asset token |
| [ins_transfer_to_caller](#ins_transfer_to_caller) | 71 | 0x49 | 任务发起者向任务调用者转asset token |
| [ins_pushsb](#ins_pushsb) | 72 | 0x4a | 从调用参数读取字节序到 vData |
| [ins_push8](#ins_push) | 73 | 0x4b | 从调用参数读取8位字节到 vData |
| [ins_push16](#ins_push) | 74 | 0x4c | 从调用参数读取16位字节到 vData |
| [ins_push32](#ins_push) | 75 | 0x4d | 从调用参数读取32位字节到 vData |
| [ins_push64](#ins_push) | 76 | 0x4e | 从调用参数读取64位字节到 vData |


- 以下pn说明，除非特别指定为值，代表的都是具体数据的开始位置索引。一些长度数据是值


<h3 id="ins_movsb">ins_movsb</h3>

```
p0: 源
p1: 目标
p2: 长度值
```

p0,p1为数据所在vData的index


<h3 id="ins_mov">ins_mov8&nbsp;ins_mov16&nbsp;ins_mov32&nbsp;ins_mov64</h3>

```
p0: 源
p1: 目标
```

p0,p1为数据所在vData的index


<h3 id="ins_add">ins_add8&nbsp;ins_add16&nbsp;ins_add32&nbsp;ins_add64&nbsp;ins_add8u&nbsp;ins_add16u&nbsp;ins_add32u&nbsp;ins_add64u</h3>

```
p0: 加数
p1: 加数
p2: 和
```

p0,p1,p2为数据所在vData的index


<h3 id="ins_sub">ins_sub8&nbsp;ins_sub16&nbsp;ins_sub32&nbsp;ins_sub64&nbsp;ins_sub8u&nbsp;ins_sub16u&nbsp;ins_sub32u&nbsp;ins_sub64u</h3>

```
p0: 被减数
p1: 减数
p2: 差
```

p0,p1,p2为数据所在vData的index


<h3 id="ins_mul">ins_mul8&nbsp;ins_mul16&nbsp;ins_mul32&nbsp;ins_mul64&nbsp;ins_mul8u&nbsp;ins_mul16u&nbsp;ins_mul32u&nbsp;ins_mul64u</h3>

```
p0: 乘数
p1: 乘数
p2: 积
```

p0,p1,p2为数据所在vData的index


<h3 id="ins_quo">ins_quo8&nbsp;ins_quo16&nbsp;ins_quo32&nbsp;ins_quo64&nbsp;ins_quo8u&nbsp;ins_quo16u&nbsp;ins_quo32u&nbsp;ins_quo64u</h3>

```
p0: 被除数
p1: 除数
p2: 商
p3: 余数
```

p0,p1,p2,p3为数据所在vData的index


<h3 id="ins_inc8">ins_inc8&nbsp;ins_inc16&nbsp;ins_inc32&nbsp;ins_inc64&nbsp;ins_inc8u&nbsp;ins_inc16u&nbsp;ins_inc32u&nbsp;ins_inc64u</h3>

```
p0: 自增数
```

p0为数据所在vData的index


<h3 id="ins_dec8">ins_dec8&nbsp;ins_dec16&nbsp;ins_dec32&nbsp;ins_dec64&nbsp;ins_dec8u&nbsp;ins_dec16u&nbsp;ins_dec32u&nbsp;ins_dec64u</h3>

```
p0: 自减
```

p0为数据所在vData的index

<h3 id="ins_write_uint">ins_write_uint8&nbsp;ins_write_uint16&nbsp;ins_write_uint32&nbsp;ins_write_uint64</h3>

```
p0: 目标
```

从虚拟寄存器写入到p0



<h3 id="ins_read_uint">ins_read_uint8&nbsp;ins_read_uint16&nbsp;ins_read_uint32&nbsp;ins_read_uint64</h3>

```
p0: 源
```

从p0读取到虚拟寄存器


<h3 id="ins_eq">ins_eq</h3>

```
p0: 用来比较的数字
p1: 用来比较的数字
p2: 即将跳转的目的
p3: 一个flag值，用来判断数字位长，0:8, 1:16, 2:32, 3:64
```

如果p0 == p1则指令跳转到p2执行，为避免出现循环，指令只能向未来跳转，不可向历史跳转



<h3 id="ins_gt">ins_gt</h3>

```
p0: 用来比较的数字
p1: 用来比较的数字
p2: 即将跳转的目的
p3: 一个flag值，用来判断数字位长，0:8, 1:16, 2:32, 3:64
```

如果p0 > p1则指令跳转到p2执行，为避免出现循环，指令只能向未来跳转，不可向历史跳转


<h3 id="ins_lt">ins_lt</h3>

```
p0: 用来比较的数字
p1: 用来比较的数字
p2: 即将跳转的目的
p3: 一个flag值，用来判断数字位长，0:8, 1:16, 2:32, 3:64
```

如果p0 < p1则指令跳转到p2执行，为避免出现循环，指令只能向未来跳转，不可向历史跳转


<h3 id="ins_gteq">ins_gteq</h3>

```
p0: 用来比较的数字
p1: 用来比较的数字
p2: 即将跳转的目的
p3: 一个flag值，用来判断数字位长，0:8, 1:16, 2:32, 3:64
```

如果p0 >= p1则指令跳转到p2执行，为避免出现循环，指令只能向未来跳转，不可向历史跳转


<h3 id="ins_lteq">ins_lteq</h3>

```
p0: 用来比较的数字
p1: 用来比较的数字
p2: 即将跳转的目的
p3: 一个flag值，用来判断数字位长，0:8, 1:16, 2:32, 3:64
```

如果p0 <= p1则指令跳转到p2执行，为避免出现循环，指令只能向未来跳转，不可向历史跳转


<h3 id="ins_eq_bytes">ins_eq_bytes</h3>

```
p0: 用来比较的字节序
p1: 用来比较的字节序
p2: 即将跳转的目的
p3: 字节序长度值
```

如果p0 == p1则指令跳转到p2执行，为避免出现循环，指令只能向未来跳转，不可向历史跳转


<h3 id="ins_height">ins_height</h3>
获取当前区块高度，暂将结果保存到虚拟寄存器的vUint32中


<h3 id="ins_transfer_dsb_from_caller">ins_transfer_dsb_from_caller</h3>

```
p0: 转账金额
```

从任务调用者地址向任务发起地址转p0 satoshi DSB


<h3 id="ins_transfer_dsb_to_caller">ins_transfer_dsb_to_caller</h3>

```
p0: 转账金额
```

从任务发起地址向任务调用者地址转p0 satoshi DSB


<h3 id="ins_transfer_from_caller">ins_transfer_from_caller</h3>

```
p0: 指定资产ID
p1: 转账金额
```

从任务调用者地址向任务发起地址转p0 satoshi 的指定资产


<h3 id="ins_transfer_to_caller">ins_transfer_to_caller</h3>

```
p0: 指定资产ID
p1: 转账金额
```

从任务发起者地址向任务调用者地址转p0 satoshi 的指定资产


<h3 id="ins_pushsb">ins_pushsb</h3>

```
p0: 任务调用参数
p1: 接收参数的vData
p2: 长度值
```

调用任务时，传递字节序参数


<h3 id="ins_push">ins_push8&nbsp;ins_push16&nbsp;ins_push32&nbsp;ins_push64</h3>

```
p0: 任务调用参数
p1: 接收参数的vData
```

调用任务时，传递数字参数
