---
Название: Go
layout: 2017/sheet
prism_languages: [go, bash]
weight: -3
tags: [Featured]
category: C-like
обновлено: 2020-06-21
---

## Начало
{: .-three-column}

### Введение
{: .-intro}

- [A tour of Go](https://tour.golang.org/welcome/1) _(tour.golang.org)_
- [Go repl](https://repl.it/languages/go) _(repl.it)_
- [Golang wiki](https://github.com/golang/go/wiki/) _(github.com)_

### Hello world
{: .-prime}

#### hello.go
{: .-file}

```go
package main

import "fmt"

func main() {
  message := greetMe("world")
  fmt.Println(message)
}

func greetMe(name string) string {
  return "Hello, " + name + "!"
}
```

```bash
$ go build
```

Или попробуйте [Go repl](https://repl.it/languages/go), или [A Tour of Go](https://tour.golang.org/welcome/1).

### Переменные

#### Объявление переменных

```go
var msg string
var msg = "Hello, world!"
var msg string = "Hello, world!"
var x, y int
var x, y int = 1, 2
var x, msg = 1, "Hello, world!"
msg = "Hello"
```

#### Спимок объявлений

``` go
var (
  x int
  y = 20
  z int = 30
  d, e = 40, "Hello"
  f, g string
)
```

#### Сокращённый вариант (Вывод типа)

```go
msg := "Hello"
x, msg := 1, "Hello"
```

### Константы

```go
const Phi = 1.618
const Size int64 = 1024
const x, y = 1, 2
const (
  Pi = 3.14
  E  = 2.718
)
const (
  Sunday = iota
  Monday
  Tuesday
  Wednesday
  Thursday
  Friday
  Saturday
)
```

Константа может быть символом, строкой, логическим или числовым значением.

Смотри: [Constants](https://tour.golang.org/basics/15)

## Основные типы
{: .-three-column}

### Строки

```go
str := "Hello"
```

```go
str := `Multiline
string`
```

Строка имеет тип `string`.

### Числа

#### Распространённые типы

```go
num := 3          // int
num := 3.         // float64
num := 3 + 4i     // complex128
num := byte('a')  // byte (alias for uint8)
```

#### Другие типы

```go
var u uint = 7        // uint (unsigned)
var p float32 = 22.7  // 32-bit float
```

### Массивы

```go
// var numbers [5]int
numbers := [...]int{0, 0, 0, 0, 0}
```

Массивы имеют фиксированный размер.

### Срезы

```go
slice := []int{2, 3, 4}
```

```go
slice := []byte("Hello")
```

Срезы имеют динамический размер, в отличии от массивов.

### Указатели

```go
func main () {
  b := *getPointer()
  fmt.Println("Value is", b)
}
```
{: data-line="2"}

```go
func getPointer () (myPointer *int) {
  a := 234
  return &a
}
```
{: data-line="3"}

```go
a := new(int)
*a = 234
```
{: data-line="2"}

Указатель обозначает место размещения переменной в памяти. Память в Go управляется сборщиком мусора.

Смотри: [Pointers](https://tour.golang.org/moretypes/1)

### Преобразования типа

```go
i := 2
f := float64(i)
u := uint(i)
```

Смотри: [Type conversions](https://tour.golang.org/basics/13)

## Управление ходом вычислений
{: .-three-column}

### Условия

```go
if day == "sunday" || day == "saturday" {
  rest()
} else if day == "monday" && isTired() {
  groan()
} else {
  work()
}
```
{: data-line="1,3,5"}

Смотри: [If](https://tour.golang.org/flowcontrol/5)

### Выражения в if

```go
if _, err := doThing(); err != nil {
  fmt.Println("Uh oh")
}
```
{: data-line="1"}

Условия в выражениях `if` могут предварятся блоком перед `;`. Переменные объявленные в блоке действуют до конца `if`.

Смотри: [If with a short statement](https://tour.golang.org/flowcontrol/6)

### Выбор

```go
switch day {
  case "sunday":
    // cases don't "fall through" by default!
    fallthrough

  case "saturday":
    rest()

  default:
    work()
}
```

Смотри: [Switch](https://github.com/golang/go/wiki/Switch)

### Цикл For

```go
for count := 0; count <= 10; count++ {
  fmt.Println("My counter is at", count)
}
```

Смотри: [For loops](https://tour.golang.org/flowcontrol/1)

### Цикл по диапазону

```go
entry := []string{"Jack","John","Jones"}
for i, val := range entry {
  fmt.Printf("At position %d, the character %s is present\n", i, val)
}
```

Смотри: [For-Range loops](https://gobyexample.com/range)

### Цикл While

```go
n := 0
x := 42
for n != x {
  n := guess()
}
```

Смотри: [Go's "while"](https://tour.golang.org/flowcontrol/3)

## Функции
{: .-three-column}

### Лямбды

```go
myfunc := func() bool {
  return x > 10000
}
```
{: data-line="1"}

Функции являются объектами первого класса.

### Возврат нескольких значений

```go
a, b := getMessage()
```

```go
func getMessage() (a string, b string) {
  return "Hello", "World"
}
```
{: data-line="2"}


### Именование возвращаемых значений

```go
func split(sum int) (x, y int) {
  x = sum * 4 / 9
  y = sum - x
  return
}
```
{: data-line="4"}

Определив имена возвращаемых значений в сигнатуре функции, `return` (без аргументов) вернёт переменные с этими именами.

Смотри: [Named return values](https://tour.golang.org/basics/7)

## Пакеты
{: .-three-column}

### Импорт

```go
import "fmt"
import "math/rand"
```

```go
import (
  "fmt"        // gives fmt.Println
  "math/rand"  // gives rand.Intn
)
```

Это эквивалентные варианты.

Смотри: [Importing](https://tour.golang.org/basics/1)

### Псевдонимы

```go
import r "math/rand"
```
{: data-line="1"}

```go
r.Intn()
```

### Экспотритуемые имена

```go
func Hello () {
  ···
}
```

Экспортируемое имя начинается с заглавной буквы.

Смотри: [Exported names](https://tour.golang.org/basics/3)

### Пакеты

```go
package hello
```

Каждый файл в пакете начинается с `package`.

## Конкурентность
{: .-three-column}

### Go-рутины

```go
func main() {
  // A "channel"
  ch := make(chan string)

  // Начало конкуретного выполнения
  go push("Moe", ch)
  go push("Larry", ch)
  go push("Curly", ch)

  // Чтение 3 результатов
  // (Поскольку выполнение конкурентное,
  // порядок не гарантирован!)
  fmt.Println(<-ch, <-ch, <-ch)
}
```
{: data-line="3,6,7,8,13"}

```go
func push(name string, ch chan string) {
  msg := "Hey, " + name
  ch <- msg
}
```
{: data-line="3"}

Каналы - конкурентно-безопасное взаимодействие объектов, используются в go-рутинах.

Смотри: [Goroutines](https://tour.golang.org/concurrency/1), [Channels](https://tour.golang.org/concurrency/2)

### Буферризация каналов

```go
ch := make(chan int, 2)
ch <- 1
ch <- 2
ch <- 3
// Фатальная ошибка:
// все go-рутины заснули are asleep - блокировка!
```
{: data-line="1"}

Буферизированные каналы ограничивают количество сообщений которые они могут сохранить.

Смотри: [Buffered channels](https://tour.golang.org/concurrency/3)

### Закрытие каналов

#### Закрытие канала

```go
ch <- 1
ch <- 2
ch <- 3
close(ch)
```
{: data-line="4"}

#### Итерация пока канал закрыт

```go
for i := range ch {
  ···
}
```
{: data-line="1"}

#### Закрытие если `ok == false`

```go
v, ok := <- ch
```

Смотри: [Range and close](https://tour.golang.org/concurrency/4)

### WaitGroup

```go
import "sync"

func main() {
  var wg sync.WaitGroup
  
  for _, item := range itemList {
    // Увеличение счётчика WaitGroup
    wg.Add(1)
    go doOperation(&wg, item)
  }
  // Ожидание завершения go-рутины
  wg.Wait()
  
}
```
{: data-line="1,4,8,12"}

```go
func doOperation(wg *sync.WaitGroup, item string) {
  defer wg.Done()
  // do operation on item
  // ...
}
```
{: data-line="2"}

WaitGroup ожидают завершения коллекции go-рутин. Основная go-рутина вызывает Add для установки номера go-рутине для ожиданя. G0-рутина вызывает `wg.Done()` при завершении.
Смотри: [WaitGroup](https://golang.org/pkg/sync/#WaitGroup)


## Управление ошибками

### Откладывание (Defer)

```go
func main() {
  defer fmt.Println("Done")
  fmt.Println("Working...")
}
```
{: data-line="2"}

Откладывает выполнение функции до тех пор, пока окружающая функция не возвращается.
Аргументы вычисляются немедлено, но вызов функции откладывается.

Смотри: [Defer, panic and recover](https://blog.golang.org/defer-panic-and-recover)

### Отложенные функции

```go
func main() {
  defer func() {
    fmt.Println("Done")
  }()
  fmt.Println("Working...")
}
```
{: data-line="2,3,4"}

Лямда прекрасно подходит для отложеных блоков.

```go
func main() {
  var d = int64(0)
  defer func(d *int64) {
    fmt.Printf("& %v Unix Sec\n", *d)
  }(&d)
  fmt.Print("Done ")
  d = time.Now().Unix()
}
```
{: data-line="3,4,5"}
Отложеные функции используют текущее значение d, 
The defer func uses current value of d, если мы не используем указатель для получения конечного значения в конце main.

## Структуры
{: .-three-column}

### Определение

```go
type Vertex struct {
  X int
  Y int
}
```
{: data-line="1,2,3,4"}

```go
func main() {
  v := Vertex{1, 2}
  v.X = 4
  fmt.Println(v.X, v.Y)
}
```

Смотри: [Structs](https://tour.golang.org/moretypes/2)

### Литералы

```go
v := Vertex{X: 1, Y: 2}
```

```go
// Имя поля можно опустить
v := Vertex{1, 2}
```

```go
// Y неявное
v := Vertex{X: 1}
```

Вы также можете указать имена полей.

### Указатели на структуры

```go
v := &Vertex{1, 2}
v.X = 2
```

Эффект от `v.X` такой же как у `(*v).X`, когда `v` указатель.

## Методы

### Приемники

```go
type Vertex struct {
  X, Y float64
}
```

```go
func (v Vertex) Abs() float64 {
  return math.Sqrt(v.X * v.X + v.Y * v.Y)
}
```
{: data-line="1"}

```go
v := Vertex{1, 2}
v.Abs()
```

Это не классы, но вы можете определить функцию с _приёмником_.

Смотри: [Methods](https://tour.golang.org/methods/1)

### Изменения

```go
func (v *Vertex) Scale(f float64) {
  v.X = v.X * f
  v.Y = v.Y * f
}
```
{: data-line="1"}

```go
v := Vertex{6, 12}
v.Scale(0.5)
// `v` is updated
```

Определив ваш приёмник как указатель (`*Vertex`), вы можете возвращать изменённый объект.

Смотри: [Pointer receivers](https://tour.golang.org/methods/4)

## Интерфейсы

### Основы интерфейсов

```go
type Shape interface {
  Area() float64
  Perimeter() float64
}
```

### Структура

```go
type Rectangle struct {
  Length, Width float64
}
```

Структура `Rectangle` неявно реализует интерфейс `Shape` рализуя все его методы.

### Методы

```go
func (r Rectangle) Area() float64 {
  return r.Length * r.Width
}

func (r Rectangle) Perimeter() float64 {
  return 2 * (r.Length + r.Width)
}
```

Методы объявленные в `Shape` реализуются в `Rectangle`.

### Пример интерфейса

```go
func main() {
  var r Shape = Rectangle{Length: 3, Width: 4}
  fmt.Printf("Type of r: %T, Area: %v, Perimeter: %v.", r, r.Area(), r.Perimeter())
}
```

## Ссылки

### Официальные ресурсы
{: .-intro}

- [A tour of Go](https://tour.golang.org/welcome/1) _(tour.golang.org)_
- [Golang wiki](https://github.com/golang/go/wiki/) _(github.com)_
- [Effective Go](https://golang.org/doc/effective_go.html) _(golang.org)_

### Доугие ссылки
{: .-intro}

- [Go by Example](https://gobyexample.com/) _(gobyexample.com)_
- [Awesome Go](https://awesome-go.com/) _(awesome-go.com)_
- [JustForFunc Youtube](https://www.youtube.com/channel/UC_BzFbxG2za3bp5NRRRXJSw) _(youtube.com)_
- [Style Guide](https://github.com/golang/go/wiki/CodeReviewComments) _(github.com)_
