# DSYSB 任务指令集

| 指令名 | 指令号 | 指令号16进制表示 | 操作 |
| --- | --- | --- | --- |
| ins_movsb | 0 | 0x0 | copy字节数组 | 
| ins_mov8 | 1 | 0x1 | copy 8位 |
| ins_mov16 | 2 | 0x2 | copy 16位 |
| ins_mov32 | 3 | 0x3 | copy 32位 |
| ins_mov64 | 4 | 0x4 | copy 64位 |
| ins_add8 | 5 | 0x5 | 8位有符号加法 |
| ins_add16 | 6 | 0x6 | 16位有符号加法 |
| ins_add32 | 7 | 0x7 | 32位有符号加法 |
| ins_add64 | 8 | 0x8 | 64位有符号加法 |
| ins_add8u | 9 | 0x9 | 8位无符号加法 |
| ins_add16u | 10 | 0xa | 16位无符号加法 |
| ins_add32u | 11 | 0xb | 32位无符号加法 |
| ins_add64u | 12 | 0xc | 64位无符号加法 |
| ins_sub8 | 13 | 0xd | 8位有符号减法 |
| ins_sub16 | 14 | 0xe | 16位有符号减法 |
| ins_sub32 | 15 | 0xf | 32位有符号减法 |
| ins_sub64 | 16 | 0x10 | 64位有符号减法 |
| ins_sub8u | 17 | 0x11 | 8位无符号减法 |
| ins_sub16u | 18 | 0x12 | 16位无符号减法 |
| ins_sub32u | 19 | 0x13 | 32位无符号减法 |
| ins_sub64u | 20 | 0x14 | 64位无符号减法 |
| ins_mul8 | 21 | 0x15 | 8位有符号乘法 |
| ins_mul16 | 22 | 0x16 | 16位有符号乘法 |
| ins_mul32 | 23 | 0x17 | 32位有符号乘法 |
| ins_mul64 | 24 | 0x18 | 64位有符号乘法 |
| ins_mul8u | 25 | 0x19 | 8位无符号乘法 |
| ins_mul16u | 26 | 0x1a | 16位无符号乘法 |
| ins_mul32u | 27 | 0x1b | 32位无符号乘法 |
| ins_mul64u | 28 | 0x1c | 64位无符号乘法 |
| ins_quo8 | 29 | 0x1d | 8位有符号除法 |
| ins_quo16 | 30 | 0x1e | 16位有符号除法 |
| ins_quo32 | 31 | 0x1f | 32位有符号除法 |
| ins_quo64 | 32 | 0x20 | 64位有符号除法 |
| ins_quo8u | 33 | 0x21 | 8位无符号除法 |
| ins_quo16u | 34 | 0x22 | 16位无符号除法 |
| ins_quo32u | 35 | 0x23 | 32位无符号除法 |
| ins_quo64u | 36 | 0x24 | 64位无符号除法 |
| ins_inc8 | 37 | 0x25 | 8位有符号自增 |
| ins_inc16 | 38 | 0x28 | 16位有符号自增 |
| ins_inc32 | 39 | 0x29 | 32位有符号自增 |
| ins_inc64 | 40 | 0x2a | 64位有符号自增 |
| ins_inc8u | 41 | 0x2b | 8位无符号自增 |
| ins_inc16u | 42 | 0x2c | 16位无符号自增 |
| ins_inc32u | 43 | 0x2d | 32位无符号自增 |
| ins_inc64u | 44 | 0x2e | 64位无符号自增 |
| ins_dec8 | 45 | 0x2f | 8位有符号自减 |
| ins_dec16 | 46 | 0x30 | 16位有符号自减 |
| ins_dec32 | 47 | 0x31 | 32位有符号自减 |
| ins_dec64 | 48 | 0x32 | 64位有符号自减 |
| ins_dec8u | 49 | 0x33 | 8位无符号自减 |
| ins_dec16u | 50 | 0x34 | 16位无符号自减 |
| ins_dec32u | 51 | 0x35 | 32位无符号自减 |
| ins_dec64u | 52 | 0x36 | 64位无符号自减 |
| ins_write_uint8 | 53 | 0x37 | 从寄存器写uint8到vData |
| ins_write_uint16 | 54 | 0x38 | 从寄存器写uint16到vData |
| ins_write_uint32 | 55 | 0x39 | 从寄存器写uint32到vData |
| ins_write_uint64 | 56 | 0x3a | 从寄存器写uint64到vData |
| ins_read_uint8 | 57 | 0x3b | 从vData读uint8到寄存器 |
| ins_read_uint16 | 58 | 0x3c | 从vData读uint16到寄存器 |
| ins_read_uint32 | 59 | 0x3d | 从vData读uint32到寄存器 |
| ins_read_uint64 | 60 | 0x3e | 从vData读uint64到寄存器 |
| ins_eq | 61 | 0x3f | 比较等于 |
| ins_gt | 62 | 0x40 | 比较大于 |
| ins_lt | 63 | 0x41 | 比较小于 |
| ins_gteq | 64 | 0x42 | 比较大于等于 |
| ins_lteq | 65 | 0x43 | 比较小于等于 |
| ins_eq_bytes | 66 | 0x44 | 比较字节序 |
| ins_height | 67 | 0x45 | 获取当前区块高度 |
| ins_transfer_dsb_from_caller | 68 | 0x46 | 任务调用者向任务发起者转DSB |
| ins_transfer_dsb_to_caller | 69 | 0x47 | 任务发起者向任务调用者转DSB |
| ins_transfer_from_caller | 70 | 0x48 | 任务调用者向任务发起者转asset token |
| ins_transfer_to_caller | 71 | 0x49 | 任务发起者向任务调用者转asset token |
| ins_pushsb | 72 | 0x4a | 从调用参数读取字节序到 vData |
| ins_push8 | 73 | 0x4b | 从调用参数读取8位字节到 vData |
| ins_push16 | 74 | 0x4c | 从调用参数读取16位字节到 vData |
| ins_push32 | 75 | 0x4d | 从调用参数读取32位字节到 vData |
| ins_push64 | 76 | 0x4e | 从调用参数读取64位字节到 vData |

ins_movsb
p0: 源
p1: 目标
p2: 长度

ins_mov8
p0: 源
p1: 目标

ins_add8
p0: 加数
p1: 加数
p2: 和

ins_sub8
p0: 被减数
p1: 减数
p2: 差

ins_mul8
p0: 乘数
p1: 乘数
p2: 积

ins_quo8
p0: 被除数
p1: 除数
p2: 商
p3: 余数

ins_inc8
p0: 自增数

ins_dec8
p0: 自减
