---
layout: wiki
wiki: golang-guide
title: 流程控制语句
---

## for

基本的for循环由三部分组成，它们用分号隔开：
- 初始化语句：在第一次迭代前执行
- 条件表达式：在每次迭代前执行
- 后置语句：在每次迭代的结尾执行

初始化语句通常为一句短变量声明，该声明仅在`for`语句的作用域中可见
{% mark 当条件表达式返回`false`时，循环终止 color:yellow %}

{% note color:default 注意： 和C、Java、JavaScript 之类的语言不同，Go 的 for 语句后面的三个构成部分外没有小括号， 大括号 { } 则是必须的。 %}

```go for.go 
package main

import "fmt"

func main() {
	for i := 0; i < 10; i++ {
		fmt.Println(i)
	}
}
```

{% mark color:yellow 初始化语句和后置语句是可选的。  %}
```go for-continue.go
package main

import "fmt"

func main() {
	i := 0
	for ;i < 10; {
		i++
	}
	fmt.Println(i)
}
```

此时，可以把分号移除，功能就变成了`while`
```go for-as-while.go
package main

import "fmt"

func main() {
	i := 0
	for i < 10 {
		i++
	}
	fmt.Println(i)
}
```
### 无限循环

如果省略循环条件，则循环将无限执行下去。
```go for-forever.go
package main

import "fmt"

func main() {
	for {
		fmt.Println("forever")
	}
}
```

## if

Go中的`if`语句和`for`循环类似，表达式无需小括号`( )`，大括号`{ }`是必须的。

```go if.go
package main

import "fmt"

func check(i int) string {
	if i > 0 {
		return "true"
	}
	return "false"
}

func main() {
	fmt.Println(check(1))
}
```

同`for`一样，`if`语句可以在条件表达式前执行一个简单的初始化语句。
初始化语句声明的变量作用域仅在`if`语句内。

```go if-with-init.go
package main

import (
	"fmt"
	"math/rand"
)

func main() {
	if i := rand.Intn(10); i > 5 {
		fmt.Println("i is", i)
	}
	fmt.Println("over")
}
```

### else

在`if`的初始化语句中声明的变量，在`else`语句中也可以使用
也可以使用`else-if`语句继续进行条件判断

```go if-and-else.go
package main

import (
	"fmt"
	"math/rand"
)

func main() {
	if i := rand.Intn(10); i > 5 {
		fmt.Println(i, "> 5")
	} else if i > 3 {
		fmt.Println(i, "> 3")
	} else {
		fmt.Println(i, "<= 3")
	}
}
```

## switch

`switch`是编写一连串`if-else`语句的快捷方式。它运行第一个值等于条件表达式的`case`语句。
Go 自动提供了每个case中的break语句。
`case`中的语句可以常量，也可以是表达式。

```go switch.go
package main

import (
	"fmt"
	"runtime"
)

func main() {
	fmt.Printf("Go runs on ")
	switch os := runtime.GOOS; os {
	case "darwin":
		fmt.Println("OS X.")
	case "linux":
		fmt.Println("Linux.")
	default:
		// freebsd, openbsd,
		// plan9, windows...
		fmt.Printf("%s.\n", os)
	}
}
```

`switch`中的`case`语句从上往下顺次执行，知道匹配成功时停止。

### 没有条件的switch
`switch`可以没有条件，相当于`switch true`。
这种形式能将一长串`if-then-else`写得更加清晰。

```go switch-with-no-condition.go
package main

import "time"

func main() {
	t := time.Now()
	switch {
	case t.Hour() < 12:
		println("Good morning!")
	case t.Hour() < 19:
		println("Good afternoon.")
	default:
		println("Good evening.")
	}
}
```



## defer

`defer`语句会将函数推迟到外层函数返回之后执行。
推迟调用的函数其参数会立即求值，但直到外层函数返回前该函数都不会被调用。

```go defer.go
package main

import "fmt"

func main() {
	defer fmt.Println("world")
	fmt.Printf("hello ")
}
```

### defer 栈

`defer`语句可以有多个，多个`defer`推迟的函数会压入一个栈中，按照后进先出的顺序执行

```go defer-multi.go
package main

import "fmt"

func main() {
	for i := 0; i < 10; i++ {
		defer fmt.Print(i, ",")
	}
}
```

上面代码的输出结果是
```plaintext result
go run .
9,8,7,6,5,4,3,2,1,0,
```
