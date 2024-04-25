---
layout: wiki
wiki: golang-guide
title: 包、变量和函数
---

## 包

每个Go 程序都是由`包`构成的。程序从`main`包开始执行。并默认执行包中的`main`函数。

```go packages.go
package main

import "fmt"

func main() {
	fmt.Println("Hello, World!")
}
```

### 导入

使用`import`关键字导入包。
```go 
import "fmt"
```
也可以使用圆括号来导入多个包。例如：
```go
import (
	"fmt"
	"math/rand"
)
```
按照约定，包名和导入路径的最后一个元素一致，例如，`math/rand`包中的源码均以`rand`作为包名。

### 导出

在Go 中，如果一个名字已大写字母开头，则该名字是导出的。例如：`Pi`是个导出的名字，它导出自`math`包。
在导入一个包时，你只能访问该包导出的名字，任何未导出的名字在该包外都无法访问。

{% mark 同一包中的导出名是唯一的。%}

## 函数

使用`func`关键字定义函数。
语法：
```plaintext 
func 函数名称([参数]) [返回类型] {
    [return 语句]
}
```
例如：
```go 
func add(x, y int) int {
	return x + y
}
```
函数可以没有参数或者接受多个参数。{% mark 注意类型在变量名之后 %} 
当连续两个或多个函数的已命名形参类型相同时，除最后一个类型以外，其它可以省略。例如：
```go 
x int, y int
```
可以写成：
```go
x, y int
```

### 多值返回

函数可以没有返回值，或者返回一个或多个值。例如：
```go multiple-results.go
package main

import "fmt"

func swap(x, y string) (string, string) {
	return y, x
}

func main() {
	a, b := swap("hello", "world")
	fmt.Println(a, b)
}
```
swap函数返回了两个字符串。

### 命名返回值

Go的返回值可以被命名，它们会被视作定义在函数顶部的变量。
没有参数的`return`语句返回已命名的返回值。也就是{% mark 直接返回 color:blue %}
```go named-results.go
package main

import "fmt"

func split(sum int) (x, y int) {
	x = sum * 4 / 9
	y = sum - x
	return
}

func main() {
	fmt.Println(split(17))
}
```

## 变量

`var`关键字用于声明一个变量列表，跟函数的参数列表一样，类型在变量名之后。
```go variables.go 
package main

import "fmt"

// 定义变量
var c, python, java bool

func main() {
	var i int
	fmt.Println(i, c, python, java)
}
```
{% mark `var`语句可以出现在包或函数级别 %}

### 变量的初始化

变量声明可以包含初始值，每个变量对应一个
如果初始值已存在，则可以省略类型，变量会从初始值中获取类型
```go variables-with-initializers.go
package main

import "fmt"

var i, j int = 1, 2

func main() {
	var c, python, java = true, false, "no!"
	fmt.Println(i, j, c, python, java)
}
```

### 短变量声明

在函数中，可在类型明确的地方使用`:=`语法声明变量。
```go short-variable-declarations.go
package main

import "fmt"

func main() {
	var i, j int = 1, 2
	k := 3
	c, python, java := true, false, "no!"
	
	fmt.Println(i, j, k, c, python, java)
}
```
{% mark `:=`不能在函数外使用 color:yellow %}

## 基本类型

Go的基本类型有
```plaintext 
bool

string

int  int8  int16  int32  int64
uint uint8 uint16 uint32 uint64 uintptr

byte // alias for uint8
rune // alias for int32

float32 float64

complex64  complex128
```

`int`, `uint` 和 `uintptr` 在 32 位系统上通常为 32 位宽，在 64 位系统上则为 64 位宽。 当你需要一个整数值时应使用 `int` 类型，除非你有特殊的理由使用固定大小或无符号的整数类型。

```go basic-types.go 
package main

import (
	"fmt"
	"math/cmplx"
)

var (
	toBe   bool       = false
	maxInt uint64     = 1<<64 - 1
	z      complex128 = cmplx.Sqrt(-5 + 12i)
)

func main() {
	fmt.Printf("Type: %T value: %v\n", toBe, toBe)
	fmt.Printf("Type: %T value: %v\n", maxInt, maxInt)
	fmt.Printf("Type: %T value: %v\n", z, z)
}
```

### 零值
没有明确初始化值的变量声明会被赋予它们的**零值**。
数值类型的零值是0，布尔类型是false，字符串类型是""（空字符串）。

```go zero.go 
package main

import "fmt"

func main() {
	var i int
	var f float64
	var b bool
	var s string
	fmt.Printf("%v %v %v %q\n", i, f, b, s)
}
```

### 类型转换

表达式 `T(v)` 将表达式 `v` 转换为类型 `T` 的值。
例如：
```go 
var i int = 64
var f float64 = float64(i)
var u uint = uint(f)
```
或者
```go
i := 64
f := float64(i)
u := uint(f)
```
Go在不同类型的项之间赋值时需要**显示转换**。

### 类型推导

在声明一个变量而不指定其类型时（即使用不带类型的`:=`语法或`var =`表达式语法），变量的类型由右值推导得出。
当右值声明了类型时，新变量的类型与其相同
```go 
var i int
j := i   // j 也是int类型
```
不过当右边包含未声明类型的数值常量时，新变量的类型就可能是`int`，`float64`或`complex128`。这取决于常量的精度。
```go 
i := 42             // int
f := 3.14           // float64
g := 0.5 + 1.0i     // complex128
```

## 常量

常量的声明和变量类似，只不过使用`const`关键字。
常量可以是字符，字符串，布尔值或数值。
常量不能用`:=`语法声明。
```go constants.go 
package main

import "fmt"

const Pi = 3.14

func main() {
	const World = "世界"
	fmt.Println("Hello", World)
	fmt.Println("Happy", Pi, "Day")

	const Truth = true
	fmt.Println("Go rules?", Truth)
}
```

### 数值常量
一个未指定类型的常量由上下文来决定其类型
```go numeric-constants.go
package main

import "fmt"

const (
	// Big 将 1 左移 100 位来创建一个非常大的数字
	// 即这个数的二进制是 1 后面跟着 100 个 0
	Big = 1 << 100
	// Small 再往右移 99 位，即 Small = 1 << 1，或者说 Small = 2
	Small = Big >> 99
)

func needInt(x int) int { return x*10 + 1 }
func needFloat(x float64) float64 {
	return x * 0.1
}

func main() {
	fmt.Println(needInt(Small))
	fmt.Println(needFloat(Small))
	fmt.Println(needFloat(Big))
}
```
















