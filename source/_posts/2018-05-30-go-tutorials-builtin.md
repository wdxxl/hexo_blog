---
title: Go Tutorials builtin
date: 2018-05-30 18:47:56
tags:
- golang
- tutorial
- builtin
categories:
- golang
---
Link01: [API - builtin](https://golang.org/pkg/builtin/)

Link02: [Padding 字节对齐](https://gocn.vip/article/673)

| Types         | Byte (字节) | bit (位)   | Range | Info  |
| ------------- |:-------------:| -----:|
| bool          | 1 |   |         | bool is the set of boolean values, true and false. 参考Padding字节对齐|
| byte          | 1 | 8 | 0 ~ 255 | type byte = uint8 (builtin.go)|
| int           | 8 | 64 | -9223372036854775808 ~ 9223372036854775807 | int is a signed integer type that is at least 32 bits in size. [OS Related] |
| int8          | 1 |  8 | -128 ~ 127                                 | math.MaxInt8  = 1<<7 - 1       |
| int16         | 2 | 16 | -32768 ~ 32767                             | math.MaxInt16 = 1<<15 - 1      |
| int32         | 4 | 32 | -2147483648 ~ 2147483647                   | math.MaxInt32 = 1<<31 - 1      |
| int64         | 8 | 64 | -9223372036854775808 ~ 9223372036854775807 | math.MaxInt64 = 1<<63 - 1      |
| rune          | 4 | 32 | -2147483648 ~ 2147483647                   | type rune = int32 (builtin.go) |
| uint          | 8 | 64 | 0 ～ 18446744073709551615                  | uint is an unsigned integer type that is at least 32 bits in size. [OS Related] |
| uint8         | 1 |  8 | 0 ~ 255                                    | math.MaxUint8 = 1<<8 - 1       |
| uint16        | 2 | 16 | 0 ~ 65535                                  | math.MaxUint16 = 1<<16 - 1     |
| uint32        | 4 | 32 | 0 ~ 4294967295                             | math.MaxUint32 = 1<<32 - 1     |
| uint64        | 8 | 64 | 0 ～ 18446744073709551615                  | math.MaxUint32 = 1<<64 - 1 [fmt uint64 ](https://stackoverflow.com/questions/16474594/how-can-i-print-out-an-constant-uint64-in-go-using-fmt) |
| float32       | 4 | 32 | 1.401298464324817e-45 ~ 3.4028234663852886e+38 | math.SmallestNonzeroFloat32, math.MaxFloat32 -- float32 is the set of all IEEE-754 32-bit floating-point numbers. |
| float64       | 8 | 64 | 5e-324 to  1.7976931348623157e+308             | math.SmallestNonzeroFloat64, math.MaxFloat64 -- float64 is the set of all IEEE-754 64-bit floating-point numbers. |
| complex64     |   |     |     | Tips: [imaginary number](http://www.ruanyifeng.com/blog/2012/09/imaginary_number.html) |
| complex128    |   |     |     | Tips: [What are imaginary number](https://math.stackexchange.com/questions/199676/what-are-imaginary-numbers) , [Guide of imaginary_number](https://betterexplained.com/articles/a-visual-intuitive-guide-to-imaginary-numbers/)|
| string        | 16 | 128 |          | string is the set of all strings of 8-bit bytes, conventionally but not necessarily representing UTF-8-encoded text. A string may be empty, but not nil. Values of string type are immutable. |
| uintptr       | 8 | 64 |                  |uintptr is an integer type that is large enough to hold the bit pattern of any pointer.|
| Map[string]string | 8 | 64 | | |
| Struct | | | | Refer Code Attached|


```
package main

import (
	"fmt"
	"unsafe"
)

type Man struct {
	Name    string
	Age     int
	Address string
}

func main() {
	m := Man{Name: "John", Age: 29}
	fmt.Println("struct - Man ", unsafe.Sizeof(m))                // struct - Man  40
	fmt.Println("struct - Man.Name", unsafe.Sizeof(m.Name))       // struct - Man.Name 16
	fmt.Println("struct - Man.Age", unsafe.Sizeof(m.Age))         // struct - Man.Age 8
	fmt.Println("struct - Man.Address", unsafe.Sizeof(m.Address)) // struct - Man.Address 16
}

```
