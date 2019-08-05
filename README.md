## Ruby 学习笔记

### 运算符

#### 算术运算符

算数运算符，顾名思义，常见的加减乘除，还有取余等：

| 运算符 | 描述                                    | 实例                        |
| ------ | --------------------------------------- | --------------------------- |
| +      | 加法 - 把运算符两边的操作数相加         | a + b 将得到 30             |
| -      | 减法 - 把左操作数减去右操作数           | a - b 将得到 -10            |
| \*     | 乘法 - 把运算符两边的操作数相乘         | a \* b 将得到 200           |
| /      | 除法 - 把左操作数除以右操作数           | b / a 将得到 2              |
| %      | 求模 - 把左操作数除以右操作数，返回余数 | b % a 将得到 0              |
| \*\*   | 指数 - 执行指数计算                     | a\*\*b 将得到 10 的 20 次方 |

```ruby
puts 1 + 2
puts 1 * 2
puts 2 - 1
puts 2 / 2
puts 11 % 3
puts 4**3
```

#### 比较运算符

假设变量 a 的值为 10，变量 b 的值为 20，那么：

| 运算符 | 描述                                                                                                                                            | 实例                                                                                                          |
| ------ | ----------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| ==     | 检查两个操作数的值是否相等，如果相等则条件为真。                                                                                                | (a == b) 不为真。                                                                                             |
| !=     | 检查两个操作数的值是否相等，如果不相等则条件为真。                                                                                              | (a != b) 为真。                                                                                               |
| >      | 检查左操作数的值是否大于右操作数的值，如果是则条件为真。                                                                                        | (a > b) 不为真。                                                                                              |
| <      | 检查左操作数的值是否小于右操作数的值，如果是则条件为真。                                                                                        | (a < b) 为真。                                                                                                |
| >=     | 检查左操作数的值是否大于或等于右操作数的值，如果是则条件为真。                                                                                  | (a >= b) 不为真。                                                                                             |
| <=     | 检查左操作数的值是否小于或等于右操作数的值，如果是则条件为真。                                                                                  | (a <= b) 为真。                                                                                               |
| <=>    | 联合比较运算符。如果第一个操作数等于第二个操作数则返回 0，如果第一个操作数大于第二个操作数则返回 1，如果第一个操作数小于第二个操作数则返回 -1。 | (a <=> b) 返回 -1。                                                                                           |
| ===    | 用于测试 case 语句的 when 子句内的相等。                                                                                                        | (1...10) === 5 返回 true。                                                                                    |
| .eql?  | 如果接收器和参数具有相同的类型和相等的值，则返回 true。                                                                                         | 1 == 1.0 返回 true，但是 1.eql?(1.0) 返回 false。                                                             |
| equal? | 如果接收器和参数具有相同的对象 id，则返回 true。                                                                                                | 如果 aObj 是 bObj 的副本，那么 aObj == bObj 返回 true，a.equal?bObj 返回 false，但是 a.equal?aObj 返回 true。 |

#### 赋值运算符

| 运算符 | 描述                                                       | 实例                            |
| ------ | ---------------------------------------------------------- | ------------------------------- |
| =      | 简单的赋值运算符，把右操作数的值赋给左操作数               | c = a + b 将把 a + b 的值赋给 c |
| +=     | 加且赋值运算符，把右操作数加上左操作数的结果赋值给左操作数 | c += a 相当于 c = c + a         |
| -=     | 减且赋值运算符，把左操作数减去右操作数的结果赋值给左操作数 | c -= a 相当于 c = c - a         |
| \*=    | 乘且赋值运算符，把右操作数乘以左操作数的结果赋值给左操作数 | c \_= a 相当于 c = c \_ a       |
| /=     | 除且赋值运算符，把左操作数除以右操作数的结果赋值给左操作数 | c /= a 相当于 c = c / a         |
| %=     | 求模且赋值运算符，求两个操作数的模赋值给左操作数           | c %= a 相当于 c = c % a         |
| \*\*=  | 指数且赋值运算符，执行指数计算，并赋值给左操作数           | c \*\*= a 相当于 c = c \*\* a   |

#### 并行赋值

Ruby 也支持变量的并行赋值。这使得多个变量可以通过一行的 Ruby 代码进行初始化。例如：

```ruby
a = 10
b = 20
c = 30
```

使用并行赋值可以更快地声明：

```ruby
a, b, c = 10, 20, 30
```

并行赋值在交换两个变量的值时也很有用：

```ruby
a, b = b, a
```

### 注释

注释是在运行时会被忽略的 Ruby 代码内的注释行。单行注释以 # 字符开始，直到该行结束，如下所示：
实例

```ruby
#!/usr/bin/ruby -w

# 这是一个单行注释。

puts "Hello, Ruby!"
```

#### 多行注释

您可以使用 `=begin` 和 `=end` 语法注释多行，如下所示：

```ruby
#!/usr/bin/ruby -w

puts "Hello, Ruby!"

=begin
这是一个多行注释。
可扩展至任意数量的行。
但 =begin 和 =end 只能出现在第一行和最后一行。 
=end
```

### 条件判断

Ruby 提供了其他现代语言中很常见的条件结构。在这里，我们将解释所有的条件语句和 Ruby 中可用的修饰符。

#### if...else 语句

```
if conditional [then]
   code...
[elsif conditional [then]
    code...]...
[else
    code...]
end
```

if 表达式用于条件执行。值 false 和 nil 为假，其他值都为真。请注意，Ruby 使用 elsif，不是使用 else if 和 elif。
如果 conditional 为真，则执行 code。如果 conditional 不为真，则执行 else 子句中指定的 code。
通常我们省略保留字 then 。若想在一行内写出完整的 if 式，则必须以 then 隔开条件式和程式区块。如下所示:

```ruby
if a == 4 then a = 7 end
```

实例

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

x=1
if x > 2
   puts "x 大于 2"
elsif x <= 2 and x!=0
   puts "x 是 1"
else
   puts "无法得知 x 的值"
end
```

![图片](https://user-images.githubusercontent.com/13142418/62419681-b9dcbe00-b6b8-11e9-907a-aedd3a797f32.png)


#### if 修饰符

语法

```
code if condition
```

如果 conditional 为真，则执行 code。

实例

```ruby
#!/usr/bin/ruby

$debug=1
puts "debug\n" if $debug
```

![图片](https://user-images.githubusercontent.com/13142418/62419702-66b73b00-b6b9-11e9-95d0-21584614add6.png)


#### unless 语句

语法

```
unless conditional [then]
   code
[else
   code ]
end
```

unless式和 if式作用相反，即如果 conditional 为假，则执行 code。如果 conditional 为真，则执行 else 子句中指定的 code。

实例

```ruby
#!/usr/bin/ruby

x=1
unless x>2
   puts "x 小于 2"
 else
  puts "x 大于 2"
end
```

![图片](https://user-images.githubusercontent.com/13142418/62419722-cca3c280-b6b9-11e9-807e-f6c7b88420b8.png)


#### unless 修饰符

语法

```
code unless conditional
```

如果 conditional 为假，则执行 code。

实例

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

$var =  1
print "1 -- 这一行输出\n" if $var
print "2 -- 这一行不输出\n" unless $var

$var = false
print "3 -- 这一行输出\n" unless $var
```

![图片](https://user-images.githubusercontent.com/13142418/62419738-3d4adf00-b6ba-11e9-855d-c90a4b01cf52.png)

#### case 语句

语法

```
case expression
[when expression [, expression ...] [then]
   code ]...
[else
   code ]
end
```

case先对一个 expression 进行匹配判断，然后根据匹配结果进行分支选择。

它使用 ===运算符比较 when 指定的 expression，若一致的话就执行 when 部分的内容。

通常我们省略保留字 then 。若想在一行内写出完整的 when 式，则必须以 then 隔开条件式和程式区块。如下所示:

```
when a == 4 then a = 7 end
```

因此：

```
case expr0
when expr1, expr2
   stmt1
when expr3, expr4
   stmt2
else
   stmt3
end
```

基本上类似于：

```
_tmp = expr0
if expr1 === _tmp || expr2 === _tmp
   stmt1
elsif expr3 === _tmp || expr4 === _tmp
   stmt2
else
   stmt3
end
```

实例

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

$age =  5
case $age
when 0 .. 2
    puts "婴儿"
when 3 .. 6
    puts "小孩"
when 7 .. 12
    puts "child"
when 13 .. 18
    puts "少年"
else
    puts "其他年龄段的"
end
```

![图片](https://user-images.githubusercontent.com/13142418/62419785-5902b500-b6bb-11e9-85a4-130587abf2a2.png)


### 循环

Ruby 中的循环用于执行相同的代码块若干次。

#### while 语句

语法

```
while conditional [do]
   code
end
```

或者

```
<pre>
while conditional [:]
   code
end
```

当 conditional 为真时，执行 code。

语法中 do 或 : 可以省略不写。但若要在一行内写出 while 式，则必须以 do 或 : 隔开条件式或程式区块。

实例

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

$i = 0
$num = 5

while $i < $num  do
   puts("在循环语句中 i = #$i" )
   $i +=1
end
```


####  while 修饰符

语法

```
code while condition
```

或者

```
begin 
  code 
end while conditional
```

当 conditional 为真时，执行 code。

如果 while 修饰符跟在一个没有 rescue 或 ensure 子句的 begin 语句后面，code 会在 conditional 判断之前执行一次。
实例

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

$i = 0
$num = 5
begin
   puts("在循环语句中 i = #$i" )
   $i +=1
end while $i < $num
```


#### until 语句

```
until conditional [do]
   code
end
```

当 conditional 为假时，执行 code。

语法中 do 可以省略不写。但若要在一行内写出 until 式，则必须以 do 隔开条件式或程式区块。

实例

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

$i = 0
$num = 5

until $i > $num  do
   puts("在循环语句中 i = #$i" )
   $i +=1;
end
```


#### until 修饰符

语法

```
code until conditional
```

或者

```
begin
   code
end until conditional
```

当 conditional 为假时，执行 code。

如果 until 修饰符跟在一个没有 rescue 或 ensure 子句的 begin 语句后面，code 会在 conditional 判断之前执行一次。

实例

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

$i = 0
$num = 5
begin
   puts("在循环语句中 i = #$i" )
   $i +=1;
end until $i > $num
```

#### for 语句

语法

```
for variable [, variable ...] in expression [do]
   code
end
```

针对 expression 中的每个元素分别执行一次 code。

实例

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

for i in 0..5
   puts "局部变量的值为 #{i}"
end
```

在这里，我们已经定义了范围 0..5。语句 for i in 0..5 允许 i 的值从 0 到 5（包含 5）。

for...in 循环几乎是完全等价于：

```
(expression).each do |variable[, variable...]| code end
```

但是，for 循环不会为局部变量创建一个新的作用域。

语法中 do 可以省略不写。但若要在一行内写出 for 式，则必须以 do 隔开条件式或程式区块。

实例

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

(0..5).each do |i|
   puts "局部变量的值为 #{i}"
end
```


#### break 语句

语法

```
break
```

终止最内部的循环。如果在块内调用，则终止相关块的方法（方法返回 nil）。

实例

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

for i in 0..5
   if i > 2 then
      break
   end
   puts "局部变量的值为 #{i}"
end
```


#### next 语句

语法

```
next
```

跳到最内部循环的下一个迭代。如果在块内调用，则终止块的执行（yield 或调用返回 nil）。

实例

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

for i in 0..5
   if i < 2 then
      next
   end
   puts "局部变量的值为 #{i}"
end
```

#### redo 语句

语法

```
redo
```

重新开始最内部循环的该次迭代，不检查循环条件。如果在块内调用，则重新开始 yield 或 call。

实例

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

for i in 0..5
   if i < 2 then
      puts "局部变量的值为 #{i}"
      redo
   end
end
```

这将产生以下结果，并会进入一个无限循环：

#### retry 语句

语法

```
retry
```

如果 retry 出现在 begin 表达式的 rescue 子句中，则从 begin 主体的开头重新开始。

```
begin
   do_something # 抛出的异常
rescue
   # 处理错误
   retry  # 重新从 begin 开始
end
```

如果 retry 出现在迭代内、块内或者 for 表达式的主体内，则重新开始迭代调用。迭代的参数会重新评估。

```
for i in 1..5
   retry if some_condition # 重新从 i == 1 开始
end
```

实例

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

for i in 1..5
   retry if  i > 2
   puts "局部变量的值为 #{i}"
end
```

这将产生以下结果，并会进入一个无限循环：


### 方法

Ruby 方法与其他编程语言中的函数类似。Ruby 方法用于捆绑一个或多个重复的语句到一个单元中。

方法名应以小写字母开头。如果您以大写字母作为方法名的开头，Ruby 可能会把它当作常量，从而导致不正确地解析调用。

方法应在调用之前定义，否则 Ruby 会产生未定义的方法调用异常。

语法

```
def method_name [( [arg [= default]]...[, * arg [, &expr ]])]
   expr..
end
```

所以，您可以定义一个简单的方法，如下所示：

```
def method_name 
   expr..
end
```

您可以定义一个接受参数的方法，如下所示：

```
def method_name (var1, var2)
   expr..
end
```

您可以为参数设置默认值，如果方法调用时未传递必需的参数则使用默认值：

```
def method_name (var1=value1, var2=value2)
   expr..
end
```

当您要调用方法时，只需要使用方法名即可，如下所示：

```
method_name
```

但是，当您调用带参数的方法时，您在写方法名时还要带上参数，例如：

```
method_name 25, 30
```

使用带参数方法最大的缺点是调用方法时需要记住参数个数。例如，
如果您向一个接受三个参数的方法只传递了两个参数，Ruby 会显示错误。

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

def test(a1="Ruby", a2="Perl")
   puts "编程语言为 #{a1}"
   puts "编程语言为 #{a2}"
end
test "C", "C++"
test
```

#### 从方法返回值

Ruby 中的每个方法默认都会返回一个值。这个返回的值是最后一个语句的值。例如：

```ruby
def test
   i = 100
   j = 10
   k = 2
end
tvar = test
puts tvar
```

在调用这个方法时，将返回最后一个声明的变量 k。



#### return 语句

Ruby 中的 return 语句用于从 Ruby 方法中返回一个或多个值。
语法

```
return [expr[',' expr...]]
```

如果给出超过两个的表达式，包含这些值的数组将是返回值。如果未给出表达式，nil 将是返回值。

实例

```
return

或

return 12

或

return 1,2,3
```


看看下面的实例：

```ruby
#!/usr/bin/ruby

def test
   i = 100
   j = 200
   k = 300
return i, j, k
end
var = test
puts var
```


#### 可变数量的参数

假设您声明了一个带有两个参数的方法，当您调用该方法时，您同时还需要传递两个参数。

但是，Ruby 允许您声明参数数量可变的方法。让我们看看下面的实例：

```ruby
#!/usr/bin/ruby

def sample (*test)
   puts "The number of parameters is #{test.length}"
   for i in 0...test.length
      puts "The parameters are #{test[i]}"
   end
end
sample "Zara", "6", "F"
sample "Mac", "36", "M", "MCA"
```

在这段代码中，您已经声明了一个方法 sample，接受一个参数 test。但是，这个参数是一个变量参数。这意味着参数可以带有不同数量的变量。所以上面的代码将产生下面的结果：

![图片](https://user-images.githubusercontent.com/13142418/62423960-b23e0900-b6fa-11e9-84ab-25ddf6281a22.png)

#### 类方法

当方法定义在类定义外部时，方法默认标记为 private。另一方面，定义在类定义中的方法默认标记为 public。方法默认的可见性和 private 标记可通过模块（Module）的 public 或 private 改变。

当你想要访问类的方法时，您首先需要实例化类。然后，使用对象，您可以访问类的任何成员。

Ruby 提供了一种不用实例化类即可访问方法的方式。让我们看看如何声明并访问类方法：

```ruby
class Accounts
   def reading_charge
   end
   def Accounts.return_date
       puts "2019"
   end
end

# 我们已经知道方法 return_date 是如何声明的。
# 它是通过在类名后跟着一个点号，点号后跟着方法名来声明的。
# 您可以直接访问类方法，如下所示：
Accounts.return_date
```

如需访问该方法，您不需要创建类 Accounts 的对象。

#### alias 语句

这个语句用于为方法或全局变量起别名。别名不能在方法主体内定义。即使方法被重写，方法的别名也保持方法的当前定义。

为编号的全局变量（$1, $2,...）起别名是被禁止的。重写内置的全局变量可能会导致严重的问题。

语法

```
alias 方法名 方法名
alias 全局变量 全局变量
```

实例

```
alias foo bar
alias $MATCH $&
```

在这里，我们已经为 bar 定义了别名为 foo，为 $& 定义了别名为 $MATCH。

#### undef 语句

这个语句用于取消方法定义。undef 不能出现在方法主体内。

通过使用 undef 和 alias，类的接口可以从父类独立修改，但请注意，在自身内部方法调用时，它可能会破坏程序。

语法

```
undef 方法名
```

实例

下面的实例取消名为 bar的方法定义：

```
undef bar
```

### 块

您已经知道 Ruby 如何定义方法以及您如何调用方法。类似地，Ruby 有一个块的概念。

- 块由大量的代码组成。
- 您需要给块取个名称。
- 块中的代码总是包含在大括号 {} 内。
- 块总是从与其具有相同名称的函数调用。这意味着如果您的块名称为 test，那么您要使用函数 test 来调用这个块。
- 您可以使用 yield 语句来调用块。

语法

```
block_name{
   statement1
   statement2
   ..........
}
```

在这里，您将学到如何使用一个简单的 yield 语句来调用块。
您也将学到如何使用带有参数的 yield 语句来调用块。
在实例中，您将看到这两种类型的 yield 语句。

#### yield 语句

让我们看一个 yield 语句的实例：

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

def test
   puts "在 test 方法内"
   yield
   puts "你又回到了 test 方法内"
   yield
end
test {puts "你在块内"}
```

![图片](https://user-images.githubusercontent.com/13142418/62424097-c4b94200-b6fc-11e9-8659-c24b90969262.png)

您也可以传递带有参数的 yield 语句。下面是一个实例：

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

def test
   yield 5
   puts "在 test 方法内"
   yield 100
end
test {
   |i| 
   puts "你在块 #{i} 内"
}
```

在这里，yield 语句后跟着参数。您甚至可以传递多个参数。在块中，您可以在两个竖线之间放置一个变量来接受参数。
因此，在上面的代码中，yield 5 语句向 test 块传递值 5 作为参数。

现在，看下面的语句：

```
test {|i| puts "你在块 #{i} 内"}
```

在这里，值 5 会在变量 i 中收到。现在，观察下面的 puts 语句：

```
puts "你在块 #{i} 内"
```

这个 puts 语句的输出是：

```
你在块 5 内
```

如果您想要传递多个参数，那么 yield 语句如下所示：

```
yield a, b
```

此时，块如下所示：

```
test {|a, b| statement}
```

参数使用逗号分隔。

#### 块和方法

您已经看到块和方法之间是如何相互关联的。您通常使用 yield 语句从与其具有相同名称的方法调用块。因此，代码如下所示：

```ruby
#!/usr/bin/ruby

def test
  yield
end
test{ puts "Hello world"}
```

本实例是实现块的最简单的方式。您使用 yield 语句调用 test 块。

但是如果方法的最后一个参数前带有 &，那么您可以向该方法传递一个块，且这个块可被赋给最后一个参数。如果 * 和 & 同时出现在参数列表中，& 应放在后面。

```ruby
#!/usr/bin/ruby

def test(&block)
   block.call
end
test { puts "Hello World!"}
```

#### BEGIN 和 END 块

每个 Ruby 源文件可以声明当文件被加载时要运行的代码块（BEGIN 块），以及程序完成执行后要运行的代码块（END 块）。

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

BEGIN { 
  # BEGIN 代码块
  puts "BEGIN 代码块"
} 

END { 
  # END 代码块
  puts "END 代码块"
}
  # MAIN 代码块
puts "MAIN 代码块"
```

一个程序可以包含多个 BEGIN 和 END 块。BEGIN 块按照它们出现的顺序执行。END 块按照它们出现的相反顺序执行。当执行时，上面的程序产生产生以下结果：

```
BEGIN 代码块
MAIN 代码块
END 代码块
```

### 模块（Module）

模块（Module）是一种把方法、类和常量组合在一起的方式。模块（Module）为您提供了两大好处。

- 模块提供了一个命名空间和避免名字冲突。
- 模块实现了 mixin 装置。

模块（Module）定义了一个命名空间，相当于一个沙盒，在里边您的方法和常量不会与其他地方的方法常量冲突。

模块类似与类，但有一下不同：

- 模块不能实例化
- 模块没有子类
- 模块只能被另一个模块定义

```
module Identifier
   statement1
   statement2
   ...........
end
```

模块常量命名与类常量命名类似，以大写字母开头。方法定义看起来也相似：模块方法定义与类方法定义类似。

通过类方法，您可以在类方法名称前面放置模块名称和一个点号来调用模块方法，您可以使用模块名称和两个冒号来引用一个常量。

实例

```ruby
#!/usr/bin/ruby

# 定义在 trig.rb 文件中的模块

module Trig
   PI = 3.141592654
   def Trig.sin(x)
   # ..
   end
   def Trig.cos(x)
   # ..
   end
end
```

我们可以定义多个函数名称相同但是功能不同的模块：

```ruby
#!/usr/bin/ruby

# 定义在 moral.rb 文件中的模块

module Moral
   VERY_BAD = 0
   BAD = 1
   def Moral.sin(badness)
   # ...
   end
end
```

就像类方法，当您在模块中定义一个方法时，您可以指定在模块名称后跟着一个点号，点号后跟着方法名。

#### require 语句

require 语句类似于 C 和 C++ 中的 include 语句以及 Java 中的 import 语句。
如果一个第三方的程序想要使用任何已定义的模块，则可以简单地使用 Ruby require 语句来加载模块文件：

语法

```
require filename
```

在这里，文件扩展名 .rb 不是必需的。

实例

```ruby
$LOAD_PATH << '.'

require 'trig.rb'
require 'moral'

y = Trig.sin(Trig::PI/4)
wrongdoing = Moral.sin(Moral::VERY_BAD)
```

在这里，我们使用 $LOAD_PATH << '.' 让 Ruby 知道必须在当前目录中搜索被引用的文件。
如果您不想使用 $LOAD_PATH，那么您可以使用 require_relative 来从一个相对目录引用文件。

注意：在这里，文件包含相同的函数名称。所以，这会在引用调用程序时导致代码模糊，
但是模块避免了这种代码模糊，而且我们可以使用模块的名称调用适当的函数。

#### include 语句

您可以在类中嵌入模块。为了在类中嵌入模块，您可以在类中使用 include 语句：
语法

```
include modulename
```

如果模块是定义在一个单独的文件中，那么在嵌入模块之前使用 require 语句引用该文件时必需的。

实例

假设下面的模块写在 `ruby/support.rb` 文件中。

```ruby
module Week
   FIRST_DAY = "Sunday"
   def Week.weeks_in_month
      puts "You have four weeks in a month"
   end
   def Week.weeks_in_year
      puts "You have 52 weeks in a year"
   end
end
```

现在，您可以在类中引用该模块，如下所示：

```ruby
#!/usr/bin/ruby
$LOAD_PATH << './ruby'
require "support"

class Decade
include Week
   no_of_yrs=10
   def no_of_months
      puts Week::FIRST_DAY
      number=10*12
      puts number
   end
end
d1=Decade.new
puts Week::FIRST_DAY
Week.weeks_in_month
Week.weeks_in_year
d1.no_of_months
```

这将产生以下结果：

![图片](https://user-images.githubusercontent.com/13142418/62424340-2c24c100-b700-11e9-9b10-6537ad594258.png)

#### Mixins

在阅读本节之前，您需要初步了解面向对象的概念。

当一个类可以从多个父类继承类的特性时，该类显示为多重继承。

Ruby 不直接支持多重继承，但是 Ruby 的模块（Module）有另一个神奇的功能。它几乎消除了多重继承的需要，提供了一种名为 mixin 的装置。

Mixins 向您提供了一种完美的为类添加功能的控制方式。但是，它们真正的强大在于当 mixin 中的代码开始与使用它的类中的代码交互时。

让我们看看下面的示例代码，深入了解 mixin：

```ruby
module A
   def a1
   end
   def a2
   end
end
module B
   def b1
   end
   def b2
   end
end

class Sample
include A
include B
   def s1
   end
end

samp=Sample.new
samp.a1
samp.a2
samp.b1
samp.b2
samp.s1
```

模块 A 由方法 a1 和 a2 组成。
模块 B 由方法 b1 和 b2 组成。
类 Sample 包含了模块 A 和 B。
类 Sample 可以访问所有四个方法，即 a1、a2、b1 和 b2。
因此，您可以看到类 Sample 继承了两个模块，您可以说类 Sample 使用了多重继承或 mixin 。
