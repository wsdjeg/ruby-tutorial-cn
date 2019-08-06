## Ruby 学习笔记

在入门学习 Ruby 的过程中，看了不少网上的教程，经常遇到的是明明代码和教程上完全一模一样，但是运行后各种报错。
本文主要使用 markdown 格式整理了 Ruby 编程语言学习的相关资料，可以直接在线阅读。
也可以克隆至本地，使用 SpaceVim 进行阅读，可以同时运行代码块中的 Ruby 脚本：

1. 安装 SpaceVim
2. 载入相关语言模块：`lang#markdown` 和 `lang#ruby`
3. 左侧章节目录导航快捷键 F2
4. 运行当前代码块片段快捷键 `SPC l r`

效果图如下：

![图片](https://user-images.githubusercontent.com/13142418/62452427-c0476480-b7a2-11e9-884e-04e6a6b30aaa.png)

也欢迎加入 Ruby 中文群一起交流学习：

[![](https://img.shields.io/badge/Telegram-Ruby-blue.svg)](https://t.me/joinchat/EazwPxcE953p4ZkxJg-qTg)

<!-- vim-markdown-toc GFM -->

- [运算符](#运算符)
  - [算术运算符](#算术运算符)
  - [比较运算符](#比较运算符)
  - [赋值运算符](#赋值运算符)
  - [并行赋值](#并行赋值)
- [注释](#注释)
  - [多行注释](#多行注释)
- [条件判断](#条件判断)
  - [if...else 语句](#ifelse-语句)
  - [if 修饰符](#if-修饰符)
  - [unless 语句](#unless-语句)
  - [unless 修饰符](#unless-修饰符)
  - [case 语句](#case-语句)
- [循环](#循环)
  - [while 语句](#while-语句)
  - [while 修饰符](#while-修饰符)
  - [until 语句](#until-语句)
  - [until 修饰符](#until-修饰符)
  - [for 语句](#for-语句)
  - [break 语句](#break-语句)
  - [next 语句](#next-语句)
  - [redo 语句](#redo-语句)
  - [retry 语句](#retry-语句)
- [方法](#方法)
  - [从方法返回值](#从方法返回值)
  - [return 语句](#return-语句)
  - [可变数量的参数](#可变数量的参数)
  - [类方法](#类方法)
  - [alias 语句](#alias-语句)
  - [undef 语句](#undef-语句)
- [块](#块)
  - [yield 语句](#yield-语句)
  - [块和方法](#块和方法)
  - [BEGIN 和 END 块](#begin-和-end-块)
- [模块（Module）](#模块module)
  - [require 语句](#require-语句)
  - [include 语句](#include-语句)
  - [Mixins](#mixins)
- [字符串（String）](#字符串string)
  - [双引号字符串](#双引号字符串)
  - [转义字符](#转义字符)
  - [字符编码](#字符编码)
- [数组（Array）](#数组array)
  - [创建数组](#创建数组)
  - [数组内建方法](#数组内建方法)
- [哈希（Hash）](#哈希hash)
  - [创建哈希](#创建哈希)
  - [哈希内置方法](#哈希内置方法)
- [范围（Range）](#范围range)
  - [作为序列的范围](#作为序列的范围)
  - [作为条件的范围](#作为条件的范围)
  - [作为间隔的范围](#作为间隔的范围)
- [迭代器](#迭代器)
  - [each 迭代器](#each-迭代器)
  - [collect 迭代器](#collect-迭代器)
- [文件的输入与输出](#文件的输入与输出)
  - [puts 语句](#puts-语句)
  - [gets 语句](#gets-语句)
  - [putc 语句](#putc-语句)
  - [print 语句](#print-语句)
- [异常](#异常)
  - [retry 语句](#retry-语句-1)
  - [raise 语句](#raise-语句)
  - [ensure 语句](#ensure-语句)
  - [else 语句](#else-语句)
  - [Catch 和 Throw](#catch-和-throw)
  - [类 Exception](#类-exception)
- [面向对象](#面向对象)
  - [类定义](#类定义)
  - [定义对象](#定义对象)
  - [initialize 方法](#initialize-方法)
  - [实例变量](#实例变量)
  - [访问器 & 设置器 方法](#访问器--设置器-方法)
  - [实例方法](#实例方法)
  - [类方法 & 类变量](#类方法--类变量)
  - [to_s 方法](#to_s-方法)
  - [访问控制](#访问控制)
  - [类的继承](#类的继承)
  - [方法重载](#方法重载)
  - [运算符重载](#运算符重载)

<!-- vim-markdown-toc -->

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

unless 式和 if 式作用相反，即如果 conditional 为假，则执行 code。如果 conditional 为真，则执行 else 子句中指定的 code。

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

case 先对一个 expression 进行匹配判断，然后根据匹配结果进行分支选择。

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

#### while 修饰符

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

下面的实例取消名为 bar 的方法定义：

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

但是如果方法的最后一个参数前带有 &，那么您可以向该方法传递一个块，且这个块可被赋给最后一个参数。如果 \* 和 & 同时出现在参数列表中，& 应放在后面。

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

### 字符串（String）

Ruby 中的 String 对象存储并操作一个或多个字节的任意序列，通常表示那些代表人类语言的字符。

最简单的字符串是括在单引号（单引号字符）内。在引号标记内的文本是字符串的值：

```
'这是一个 Ruby 程序的字符串'
```

如果您需要在单引号字符串内使用单引号字符，那么需要在单引号字符串使用反斜杠，这样 Ruby 解释器就不会认为这个单引号字符会终止字符串：

```
'Won\'t you read O\'Reilly\'s book?'
```

反斜杠也能转义另一个反斜杠，这样第二个反斜杠本身不会解释为转义字符。

以下是 Ruby 中字符串相关的特性。

#### 双引号字符串

在双引号字符串中我们可以使用 #{} 井号和大括号来计算表达式的值：

字符串中嵌入变量：

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

name1 = "Joe"
name2 = "Mary"
puts "你好 #{name1},  #{name2} 在哪?"
```

字符串中进行数学运算：

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

x, y, z = 12, 36, 72
puts "x 的值为 #{ x }"
puts "x + y 的值为 #{ x + y }"
puts "x + y + z 的平均值为 #{ (x + y + z)/3 }"
```

Ruby 中还支持一种采用 %q 和 %Q 来引导的字符串变量，%q 使用的是单引号引用规则，而 %Q 是双引号引用规则，后面再接一个 (! [ { 等等的开始界定符和与 } ] ) 等等的末尾界定符。

跟在 q 或 Q 后面的字符是分界符.分界符可以是任意一个非字母数字的单字节字符.如:[,{,(,<,!等,字符串会一直读取到发现相匹配的结束符为止.

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

desc1 = %Q{Ruby 的字符串可以使用 '' 和 ""。}
desc2 = %q|Ruby 的字符串可以使用 '' 和 ""。|

puts desc1
puts desc2
```

#### 转义字符

下标列出了可使用反斜杠符号转义的转义字符或非打印字符。

注意：在一个双引号括起的字符串内，转义字符会被解释；在一个单引号括起的字符串内，转义字符会被保留。

| 反斜杠符号 | 十六进制字符 | 描述                                             |
| ---------- | ------------ | ------------------------------------------------ |
| \a         | 0x07         | 报警符                                           |
| \b         | 0x08         | 退格键                                           |
| \cx        |              | Control-x                                        |
| \C-x       |              | Control-x                                        |
| \e         | 0x1b         | 转义符                                           |
| \f         | 0x0c         | 换页符                                           |
| \M-\C-x    |              | Meta-Control-x                                   |
| \n         | 0x0a         | 换行符                                           |
| \nnn       |              | 八进制表示法，其中 n 的范围为 0.7                |
| \r         | 0x0d         | 回车符                                           |
| \s         | 0x20         | 空格符                                           |
| \t         | 0x09         | 制表符                                           |
| \v         | 0x0b         | 垂直制表符                                       |
| \x         |              | 字符 x                                           |
| \xnn       |              | 十六进制表示法，其中 n 的范围为 0.9、 a.f 或 A.F |

#### 字符编码

Ruby 的默认字符集是 ASCII，字符可用单个字节表示。如果您使用 UTF-8 或其他现代的字符集，字符可能是用一个到四个字节表示。

您可以在程序开头使用 \$KCODE 改变字符集，如下所示：

```ruby
$KCODE = 'u'
```

下面是 \$KCODE 可能的值。

| 编码 | 描述                                 |
| ---- | ------------------------------------ |
| a    | ASCII （与 none 相同）。这是默认的。 |
| e    | EUC。                                |
| n    | None （与 ASCII 相同）。             |
| u    | UTF-8。                              |

字符串内建方法

我们需要有一个 String 对象的实例来调用 String 方法。下面是创建 String 对象实例的方式：

```
new [String.new(str="")]
```

这将返回一个包含 str 副本的新的字符串对象。现在，使用 str 对象，我们可以调用任意可用的实例方法。例如：

```ruby
#!/usr/bin/ruby

myStr = String.new("THIS IS TEST")
foo = myStr.downcase

puts "#{foo}"
```

这将产生以下结果：

```
this is test
```

### 数组（Array）

Ruby 数组是任何对象的有序的、整数索引的集合。数组中的每个元素都与一个索引相关，并可通过索引进行获取。

数组的索引从 0 开始，这与 C 或 Java 中一样。一个负数的索引时相对于数组的末尾计数的，也就是说，索引为 -1 表示数组的最后一个元素，-2 表示数组中的倒数第二个元素，依此类推。

Ruby 数组可存储诸如 String、 Integer、 Fixnum、 Hash、 Symbol 等对象，甚至可以是其他 Array 对象。Ruby 数组不像其他语言中的数组那么刚性。当向数组添加元素时，Ruby 数组会自动增长。

#### 创建数组

有多种方式创建或初始化数组。一种方式是通过 new 类方法：

```
names = Array.new
```

您可以在创建数组的同时设置数组的大小：

```
names = Array.new(20)
```

数组 names 的大小或长度为 20 个元素。您可以使用 size 或 length 方法返回数组的大小：

```ruby
#!/usr/bin/ruby

names = Array.new(20)
puts names.size  # 返回 20
puts names.length # 返回 20
```

您可以给数组中的每个元素赋值，如下所示：

```ruby
#!/usr/bin/ruby

names = Array.new(4, "mac")

puts "#{names}"
```

您也可以使用带有 new 的块，每个元素使用块中的计算结果来填充：

```ruby
#!/usr/bin/ruby

nums = Array.new(10) { |e| e = e * 2 }

puts "#{nums}"
```

数组还有另一种方法，[]，如下所示：

```
nums = Array.[](1, 2, 3, 4,5)
```

数组创建的另一种形式如下所示：

```
nums = Array[1, 2, 3, 4,5]
```

在 Ruby 核心模块中可以有一个只接收单个参数的 Array 方法，该方法使用一个范围作为参数来创建一个数字数组：

```
#!/usr/bin/ruby

digits = Array(0..9)

puts "#{digits}"
```

以上实例运行输出结果为：

```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

#### 数组内建方法

我们需要有一个 Array 对象的实例来调用 Array 方法。下面是创建 Array 对象实例的方式：

```
Array.[](...) [or] Array[...] [or] [...]
```

这将返回一个使用给定对象进行填充的新的数组。现在，使用创建的对象，我们可以调用任意可用的实例方法。例如：

```
#!/usr/bin/ruby

digits = Array(0..9)

num = digits.at(6)

puts "#{num}"
```

这将产生以下结果：

```
6
```

### 哈希（Hash）

哈希（Hash）是类似 "employee" => "salary" 这样的键值对的集合。哈希的索引是通过任何对象类型的任意键来完成的，而不是一个整数索引，其他与数组相似。

通过键或值遍历哈希的顺序看起来是随意的，且通常不是按照插入顺序。如果您尝试通过一个不存在的键访问哈希，则方法会返回 nil。

#### 创建哈希

与数组一样，有各种不同的方式来创建哈希。您可以通过 new 类方法创建一个空的哈希：

```
months = Hash.new
```

您也可以使用 new 创建带有默认值的哈希，不带默认值的哈希是 nil：

```
months = Hash.new( "month" )
```

或

```
months = Hash.new "month"
```

当您访问带有默认值的哈希中的任意键时，如果键或值不存在，访问哈希将返回默认值：

```ruby
#!/usr/bin/ruby

months = Hash.new( "month" )

puts "#{months[0]}"
puts "#{months[72]}"
```

```ruby
#!/usr/bin/ruby

H = Hash["a" => 100, "b" => 200]

puts "#{H['a']}"
puts "#{H['b']}"
```

您可以使用任何的 Ruby 对象作为键或值，甚至可以使用数组，所以下面的实例是一个有效的实例：

```
[1,"jan"] => "January"
```

#### 哈希内置方法

我们需要有一个 Hash 对象的实例来调用 Hash 方法。下面是创建 Hash 对象实例的方式：

```
Hash[[key =>|, value]* ] or

Hash.new [or] Hash.new(obj) [or]

Hash.new { |hash, key| block }
```

这将返回一个使用给定对象进行填充的新的哈希。现在，使用创建的对象，我们可以调用任意可用的实例方法。例如：

```ruby
#!/usr/bin/ruby

$, = ", "
months = Hash.new( "month" )

months = {"1" => "January", "2" => "February"}

keys = months.keys

puts "#{keys}"
```

### 范围（Range）

范围（Range）无处不在：January 到 December、 0 到 9、等等。Ruby 支持范围，并允许我们以不同的方式使用范围：

- 作为序列的范围
- 作为条件的范围
- 作为间隔的范围

#### 作为序列的范围

范围的第一个也是最常见的用途是表达序列。序列有一个起点、一个终点和一个在序列产生连续值的方式。

Ruby 使用 ''..'' 和 ''...'' 范围运算符创建这些序列。两点形式创建一个包含指定的最高值的范围，三点形式创建一个不包含指定的最高值的范围。

```
(1..5)        #==> 1, 2, 3, 4, 5
(1...5)       #==> 1, 2, 3, 4
('a'..'d')    #==> 'a', 'b', 'c', 'd'
```

序列 1..100 是一个 Range 对象，包含了两个 Fixnum 对象的引用。如果需要，您可以使用 to_a 方法把范围转换为列表。尝试下面的实例：

```ruby
#!/usr/bin/ruby

$, =", "   # Array 值分隔符
range1 = (1..10).to_a
range2 = ('bar'..'bat').to_a

puts "#{range1}"
puts "#{range2}"
```

范围实现了让您可以遍历它们的方法，您可以通过多种方式检查它们的内容：

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

# 指定范围
digits = 0..9

puts digits.include?(5)
ret = digits.min
puts "最小值为 #{ret}"

ret = digits.max
puts "最大值为 #{ret}"

ret = digits.reject {|i| i < 5 }
puts "不符合条件的有 #{ret}"

digits.each do |digit|
   puts "在循环中 #{digit}"
end
```

#### 作为条件的范围

范围也可以用作条件表达式。例如，下面的代码片段从标准输入打印行，其中每个集合的第一行包含单词 start，最后一行包含单词 end.：

```
while gets
   print if /start/../end/
end
```

范围可以用在 case 语句中：

```ruby
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

score = 70

result = case score
when 0..40
	"糟糕的分数"
when 41..60
	"快要及格"
when 61..70
	"及格分数"
when 71..100
   	"良好分数"
else
	"错误的分数"
end

puts result
```

#### 作为间隔的范围

范围的最后一个用途是间隔测试：检查某些值是否落在范围表示的间隔里。这是使用 === 相等运算符来完成计算

```ruby
#!/usr/bin/ruby

if ((1..10) === 5)
  puts "5 lies in (1..10)"
end

if (('a'..'j') === 'c')
  puts "c lies in ('a'..'j')"
end

if (('a'..'j') === 'z')
  puts "z lies in ('a'..'j')"
end
```

### 迭代器

迭代器是集合支持的方法。存储一组数据成员的对象称为集合。在 Ruby 中，数组和散列可以称之为集合。

迭代器返回集合的所有元素，一个接着一个。在这里我们将讨论两种迭代器，each 和 collect。

#### each 迭代器

each 迭代器返回数组或哈希的所有元素。

语法

```
collection.each do |variable|
   code
end
```

为集合中的每个元素执行 code。在这里，集合可以是数组或哈希。

实例

```ruby
#!/usr/bin/ruby

ary = [1,2,3,4,5]
ary.each do |i|
   puts i
end
```

each 迭代器总是与一个块关联。它向块返回数组的每个值，一个接着一个。值被存储在变量 i 中，然后显示在屏幕上。

#### collect 迭代器

collect 迭代器返回集合的所有元素。

语法

```
collection = collection.collect
```

collect 方法不需要总是与一个块关联。collect 方法返回整个集合，不管它是数组或者是哈希。

实例

```ruby
#!/usr/bin/ruby

a = [1,2,3,4,5]
b = Array.new
b = a.collect{ |x| x * 2 }
puts b
```

注意：collect 方法不是数组间进行复制的正确方式。这里有另一个称为 clone 的方法，用于复制一个数组到另一个数组。

当您想要对每个值进行一些操作以便获得新的数组时，您通常使用 collect 方法。例如，下面的代码会生成一个数组，其值是 a 中每个值的 10 倍。

```ruby
#!/usr/bin/ruby

a = [1,2,3,4,5]
b = a.collect{
    |x|
    10*x
}
puts b
```


### 文件的输入与输出

Ruby 提供了一整套 I/O 相关的方法，在内核（Kernel）模块中实现。所有的 I/O 方法派生自 IO 类。

类 IO 提供了所有基础的方法，比如 read、 write、 gets、 puts、 readline、 getc 和 printf。

本章节将讲解所有 Ruby 中可用的基础的 I/O 函数。如需了解更多的函数，请查看 Ruby 的 IO 类。

#### puts 语句

在前面的章节中，您赋值给变量，然后使用 puts 语句打印输出。

puts 语句指示程序显示存储在变量中的值。这将在每行末尾添加一个新行。

实例

```ruby
#!/usr/bin/ruby

val1 = "This is variable one"
val2 = "This is variable two"
puts val1
puts val2
```

#### gets 语句

gets 语句可用于获取来自名为 STDIN 的标准屏幕的用户输入。

实例

下面的代码演示了如何使用 gets 语句。该代码将提示用户输入一个值，该值将被存储在变量 val 中，最后会被打印在 STDOUT 上。

```ruby
#!/usr/bin/ruby

puts "Enter a value :"
val = gets
puts val
```

#### putc 语句

与 puts 语句不同，puts 语句输出整个字符串到屏幕上，而 putc 语句可用于依次输出一个字符。

实例

下面代码的输出只是字符 H：

```ruby
#!/usr/bin/ruby

str="Hello Ruby!"
putc str
```

#### print 语句

print 语句与 puts 语句类似。唯一的不同在于 puts 语句在输出内容后会跳到下一行，而使用 print 语句时，光标定位在同一行。

实例

```ruby
#!/usr/bin/ruby

print "Hello World"
print "Good Morning"
```


### 异常

异常和执行总是被联系在一起。如果您打开一个不存在的文件，且没有恰当地处理这种情况，那么您的程序则被认为是低质量的。

如果异常发生，则程序停止。异常用于处理各种类型的错误，这些错误可能在程序执行期间发生，所以要采取适当的行动，而不至于让程序完全停止。

Ruby 提供了一个完美的处理异常的机制。我们可以在 begin/end 块中附上可能抛出异常的代码，并使用 rescue 子句告诉 Ruby 完美要处理的异常类型。

语法

```
begin #开始
 
 raise.. #抛出异常
 
rescue [ExceptionType = StandardException] #捕获指定类型的异常 缺省值是StandardException
 $! #表示异常信息
 $@ #表示异常出现的代码位置
else #其余异常
 ..
ensure #不管有没有异常，进入该代码块
 
end #结束
```

从 begin 到 rescue 中的一切是受保护的。如果代码块执行期间发生了异常，控制会传到 rescue 和 end 之间的块。

对于 begin 块中的每个 rescue 子句，Ruby 把抛出的异常与每个参数进行轮流比较。如果 rescue 子句中命名的异常与当前抛出的异常类型相同，或者是该异常的父类，则匹配成功。

如果异常不匹配所有指定的错误类型，我们可以在所有的 rescue 子句后使用一个 else 子句。

实例

```ruby
#!/usr/bin/ruby

begin
   file = open("/unexistant_file")
   if file
      puts "File opened successfully"
   end
rescue
      file = STDIN
end
print file, "==", STDIN, "\n"
```


#### retry 语句

您可以使用 rescue 块捕获异常，然后使用 retry 语句从开头开始执行 begin 块。

语法

```
begin
    # 这段代码抛出的异常将被下面的 rescue 子句捕获
rescue
    # 这个块将捕获所有类型的异常
    retry  # 这将把控制移到 begin 的开头
end
```

实例

```ruby
#!/usr/bin/ruby

fname = "/unexistant_file"
begin
   file = open(fname)
   if file
      puts "File opened successfully"
      file.close
   end
rescue
   fname = "README.md"
   retry
end
```

以下是处理流程：

- 打开时发生异常。
- 跳到 rescue。fname 被重新赋值。
- 通过 retry 跳到 begin 的开头。
- 这次文件成功打开。
- 继续基本的过程。

注意：如果被重新命名的文件不存在，本势力代码会无限尝试。所以异常处理时，谨慎使用 retry。

#### raise 语句

您可以使用 raise 语句抛出异常。下面的方法在调用时抛出异常。它的第二个消息将被输出。

语法

```
raise 

OR

raise "Error Message" 

OR

raise ExceptionType, "Error Message"

OR

raise ExceptionType, "Error Message" condition
```

第一种形式简单地重新抛出当前异常（如果没有当前异常则抛出一个 RuntimeError）。这用在传入异常之前需要解释异常的异常处理程序中。

第二种形式创建一个新的 RuntimeError 异常，设置它的消息为给定的字符串。该异常之后抛出到调用堆栈。

第三种形式使用第一个参数创建一个异常，然后设置相关的消息为第二个参数。

第四种形式与第三种形式类似，您可以添加任何额外的条件语句（比如 unless）来抛出异常。

实例

```ruby
#!/usr/bin/ruby

begin  
    puts 'I am before the raise.'  
    raise 'An error has occurred.'  
    puts 'I am after the raise.'  
rescue  
    puts 'I am rescued.'  
end  
puts 'I am after the begin block.'  
```

另一个演示 raise 用法的实例：

```ruby
#!/usr/bin/ruby

begin  
  raise 'A test exception.'  
rescue Exception => e  
  puts e.message  
  puts e.backtrace.inspect  
end
```

#### ensure 语句

有时候，无论是否抛出异常，您需要保证一些处理在代码块结束时完成。例如，您可能在进入时打开了一个文件，当您退出块时，您需要确保关闭文件。

ensure 子句做的就是这个。ensure 放在最后一个 rescue 子句后，并包含一个块终止时总是执行的代码块。它与块是否正常退出、是否抛出并处理异常、是否因一个未捕获的异常而终止，这些都没关系，ensure 块始终都会运行。

语法

```
begin 
   #.. 过程
   #.. 抛出异常
rescue 
   #.. 处理错误 
ensure 
   #.. 最后确保执行
   #.. 这总是会执行
end
```

实例

```ruby
begin
  raise 'A test exception.'
rescue Exception => e
  puts e.message
  puts e.backtrace.inspect
ensure
  puts "Ensuring execution"
end
```

#### else 语句

如果提供了 else 子句，它一般是放置在 rescue 子句之后，任意 ensure 之前。

else 子句的主体只有在代码主体没有抛出异常时执行。

语法

```
begin 
   #.. 过程 
   #.. 抛出异常
rescue 
   #.. 处理错误
else
   #.. 如果没有异常则执行
ensure 
   #.. 最后确保执行
   #.. 这总是会执行
end
```

实例

```ruby
begin
 # 抛出 'A test exception.'
 puts "I'm not raising exception"
rescue Exception => e
  puts e.message
  puts e.backtrace.inspect
else
   puts "Congratulations-- no errors!"
ensure
  puts "Ensuring execution"
end
```

使用 $! 变量可以捕获抛出的错误消息。

#### Catch 和 Throw

raise 和 rescue 的异常机制能在发生错误时放弃执行，有时候需要在正常处理时跳出一些深层嵌套的结构。此时 catch 和 throw 就派上用场了。

catch 定义了一个使用给定的名称（可以是 Symbol 或 String）作为标签的块。块会正常执行知道遇到一个 throw。

语法

```
throw :lablename
#.. 这不会被执行
catch :lablename do
#.. 在遇到一个 throw 后匹配将被执行的 catch
end

OR

throw :lablename condition
#.. 这不会被执行
catch :lablename do
#.. 在遇到一个 throw 后匹配将被执行的 catch
end
```

实例

下面的实例中，如果用户键入 '!' 回应任何提示，使用一个 throw 终止与用户的交互。

```ruby
def promptAndGet(prompt)
   print prompt
   res = readline.chomp
   throw :quitRequested if res == "!"
   return res
end

catch :quitRequested do
   name = promptAndGet("Name: ")
   age = promptAndGet("Age: ")
   sex = promptAndGet("Sex: ")
   # ..
   # 处理信息
end
promptAndGet("Name:")
```

#### 类 Exception

Ruby 的标准类和模块抛出异常。所有的异常类组成一个层次，包括顶部的 Exception 类在内。下一层是七种不同的类型：

- Interrupt
- NoMemoryError
- SignalException
- ScriptError
- StandardError
- SystemExit

Fatal 是该层中另一种异常，但是 Ruby 解释器只在内部使用它。

ScriptError 和 StandardError 都有一些子类，但是在这里我们不需要了解这些细节。最重要的事情是创建我们自己的异常类，它们必须是类 Exception 或其子代的子类。

让我们看一个实例：

```ruby
class FileSaveError < StandardError
   attr_reader :reason
   def initialize(reason)
      @reason = reason
   end
end
```

现在，看下面的实例，将用到上面的异常：

```ruby
File.open(path, "w") do |file|
begin
    # 写出数据 ...
rescue
    # 发生错误
    raise FileSaveError.new($!)
end
end
```

在这里，最重要的一行是 raise FileSaveError.new($!)。我们调用 raise 来示意异常已经发生，把它传给 FileSaveError 的一个新的实例，由于特定的异常引起数据写入失败。


### 面向对象

Ruby 是纯面向对象的语言，Ruby 中的一切都是以对象的形式出现。Ruby 中的每个值都是一个对象，即使是最原始的东西：字符串、数字，甚至连 true 和 false 都是对象。类本身也是一个对象，是 Class 类的一个实例。本章将向您讲解所有与 Ruby 面向对象相关的主要功能。

类用于指定对象的形式，它结合了数据表示法和方法，把数据整理成一个整齐的包。类中的数据和方法被称为类的成员。

#### 类定义

当您定义一个类时，您实际是定义了一个数据类型的蓝图。这实际上并没有定义任何的数据，而是定义了类的名称意味着什么，也就是说，定义了类的对象将由什么组成，以及在该对象上能执行什么操作。

类定义以关键字 class 开始，后跟类名称，最后以一个 end 进行分隔表示终止该类定义。例如，我们使用关键字 class 来定义 Box 类，如下所示：

```
class Box
   code
end
```

按照惯例，名称必须以大写字母开头，如果包含多个单词，每个单词首字母大写，但此间没有分隔符（例如：CamelCase）。

#### 定义对象

类提供了对象的蓝图，所以基本上，对象是根据类进行创建的。我们使用 new 关键字声明类的对象。下面的语句声明了类 Box 的两个对象：

```ruby
box1 = Box.new
box2 = Box.new
```


#### initialize 方法

initialize 方法是一个标准的 Ruby 类方法，与其他面向对象编程语言中的 constructor 工作原理类似。当您想要在创建对象的同时初始化一些类变量，initialize 方法就派上用场了。该方法带有一系列参数，与其他 Ruby 方法一样，使用该方法时，必须在前面放置 def 关键字，如下所示：

```ruby
class Box
   def initialize(w,h)
      @width, @height = w, h
   end
end
```

#### 实例变量

实例变量是类属性，它们在使用类创建对象时就变成对象的属性。每个对象的属性是单独赋值的，和其他对象之间不共享值。在类的内部，是使用 @ 运算符访问这些属性，在类的外部，则是使用称为访问器方法的公共方法进行访问。下面我们以上面定义的类 Box 为实例，把 @width 和 @height 作为类 Box 的实例变量。

```ruby
class Box
   def initialize(w,h)
      # 给实例变量赋值
      @width, @height = w, h
   end
end
```

#### 访问器 & 设置器 方法

为了在类的外部使用变量，我们必须在访问器方法内部定义这些变量，这些访问器方法也被称为获取器方法。下面的实例演示了访问器方法的用法：

```ruby
#!/usr/bin/ruby -w

# 定义类
class Box
   # 构造器方法
   def initialize(w,h)
      @width, @height = w, h
   end

   # 访问器方法
   def printWidth
      @width
   end

   def printHeight
      @height
   end
end

# 创建对象
box = Box.new(10, 20)

# 使用访问器方法
x = box.printWidth()
y = box.printHeight()

puts "Width of the box is : #{x}"
puts "Height of the box is : #{y}"
```

与用于访问变量值的访问器方法类似，Ruby 提供了一种在类的外部设置变量值的方式，也就是所谓的设置器方法，定义如下：

```ruby
#!/usr/bin/ruby -w

# 定义类
class Box
   # 构造器方法
   def initialize(w,h)
      @width, @height = w, h
   end

   # 访问器方法
   def getWidth
      @width
   end
   def getHeight
      @height
   end

   # 设置器方法
   def setWidth=(value)
      @width = value
   end
   def setHeight=(value)
      @height = value
   end
end

# 创建对象
box = Box.new(10, 20)

# 使用设置器方法
box.setWidth = 30
box.setHeight = 50

# 使用访问器方法
x = box.getWidth()
y = box.getHeight()

puts "Width of the box is : #{x}"
puts "Height of the box is : #{y}"
```

#### 实例方法

实例方法的定义与其他方法的定义一样，都是使用 def 关键字，但它们只能通过类实例来使用，如下面实例所示。它们的功能不限于访问实例变量，也能按照您的需求做更多其他的任务。

```ruby
#!/usr/bin/ruby -w

# 定义类
class Box
   # constructor method
   def initialize(w,h)
      @width, @height = w, h
   end
   # 实例方法
   def getArea
      @width * @height
   end
end

# 创建对象
box = Box.new(10, 20)

# 调用实例方法
a = box.getArea()
puts "Area of the box is : #{a}"
```


#### 类方法 & 类变量

类变量是在类的所有实例中共享的变量。换句话说，类变量的实例可以被所有的对象实例访问。类变量以两个 @ 字符（@@）作为前缀，类变量必须在类定义中被初始化，如下面实例所示。

类方法使用 def self.methodname() 定义，类方法以 end 分隔符结尾。类方法可使用带有类名称的 classname.methodname 形式调用，如下面实例所示：


```ruby
#!/usr/bin/ruby -w

class Box
   # 初始化类变量
   @@count = 0
   def initialize(w,h)
      # 给实例变量赋值
      @width, @height = w, h

      @@count += 1
   end

   def self.printCount()
      puts "Box count is : #@@count"
   end
end

# 创建两个对象
box1 = Box.new(10, 20)
box2 = Box.new(30, 100)

# 调用类方法来输出盒子计数
Box.printCount()
```



#### to_s 方法

您定义的任何类都有一个 to_s 实例方法来返回对象的字符串表示形式。下面是一个简单的实例，根据 width 和 height 表示 Box 对象：

```ruby
#!/usr/bin/ruby -w

class Box
   # 构造器方法
   def initialize(w,h)
      @width, @height = w, h
   end
   # 定义 to_s 方法
   def to_s
      "(w:#@width,h:#@height)"  # 对象的字符串格式
   end
end

# 创建对象
box = Box.new(10, 20)

# 自动调用 to_s 方法
puts "String representation of box is : #{box}"
```



#### 访问控制

Ruby 为您提供了三个级别的实例方法保护，分别是 public、private 或 protected。Ruby 不在实例和类变量上应用任何访问控制。

- Public 方法： Public 方法可被任意对象调用。默认情况下，方法都是 public 的，除了 initialize 方法总是 private 的。
- Private 方法： Private 方法不能从类外部访问或查看。只有类方法可以访问私有成员。
- Protected 方法： Protected 方法只能被类及其子类的对象调用。访问也只能在类及其子类内部进行。

下面是一个简单的实例，演示了这三种修饰符的语法：

```ruby
#!/usr/bin/ruby -w

# 定义类
class Box
   # 构造器方法
   def initialize(w,h)
      @width, @height = w, h
   end

   # 实例方法默认是 public 的
   def getArea
      getWidth() * getHeight
   end

   # 定义 private 的访问器方法
   def getWidth
      @width
   end
   def getHeight
      @height
   end
   # make them private
   private :getWidth, :getHeight

   # 用于输出面积的实例方法
   def printArea
      @area = getWidth() * getHeight
      puts "Big box area is : #@area"
   end
   # 让实例方法是 protected 的
   protected :printArea
end

# 创建对象
box = Box.new(10, 20)

# 调用实例方法
a = box.getArea()
puts "Area of the box is : #{a}"

# 尝试调用 protected 的实例方法
box.printArea()
```

#### 类的继承


继承，是面向对象编程中最重要的概念之一。继承允许我们根据另一个类定义一个类，这样使得创建和维护应用程序变得更加容易。

继承有助于重用代码和快速执行，不幸的是，Ruby 不支持多继承，但是 Ruby 支持 mixins。mixin 就像是多继承的一个特定实现，在多继承中，只有接口部分是可继承的。

当创建类时，程序员可以直接指定新类继承自某个已有类的成员，这样就不用从头编写新的数据成员和成员函数。这个已有类被称为基类或父类，新类被称为派生类或子类。

Ruby 也提供了子类化的概念，子类化即继承，下面的实例解释了这个概念。扩展一个类的语法非常简单。只要添加一个 < 字符和父类的名称到类语句中即可。例如，下面定义了类 BigBox 是 Box 的子类：

```ruby
#!/usr/bin/ruby -w

# 定义类
class Box
   # 构造器方法
   def initialize(w,h)
      @width, @height = w, h
   end
   # 实例方法
   def getArea
      @width * @height
   end
end

# 定义子类
class BigBox < Box

   # 添加一个新的实例方法
   def printArea
      @area = @width * @height
      puts "Big box area is : #@area"
   end
end

# 创建对象
box = BigBox.new(10, 20)

# 输出面积
box.printArea()
```

#### 方法重载

虽然您可以在派生类中添加新的功能，但有时您可能想要改变已经在父类中定义的方法的行为。这时您可以保持方法名称不变，重载方法的功能即可，如下面实例所示：


```ruby
#!/usr/bin/ruby -w

# 定义类
class Box
   # 构造器方法
   def initialize(w,h)
      @width, @height = w, h
   end
   # 实例方法
   def getArea
      @width * @height
   end
end

# 定义子类
class BigBox < Box

   # 改变已有的 getArea 方法
   def getArea
      @area = @width * @height
      puts "Big box area is : #@area"
   end
end

# 创建对象
box = BigBox.new(10, 20)

# 使用重载的方法输出面积
box.getArea()
```


#### 运算符重载

我们希望使用 + 运算符执行两个 Box 对象的向量加法，使用 * 运算符来把 Box 的 width 和 height 相乘，使用一元运算符 - 对 Box 的 width 和 height 求反。下面是一个带有数学运算符定义的 Box 类版本：


```ruby
#!/usr/bin/ruby -w
class Box
  def initialize(w,h) # 初始化 width 和 height
    @width,@height = w, h
  end

  def +(other)         # 定义 + 来执行向量加法
    Box.new(@width + other.width, @height + other.height)
  end

  def -@               # 定义一元运算符 - 来对 width 和 height 求反
    Box.new(-@width, -@height)
  end

  def *(scalar)        # 执行标量乘法
    Box.new(@width*scalar, @height*scalar)
  end
  def to_s
      "(w:#@width,h:#@height)"  # 对象的字符串格式
  end
end

box1 = Box.new(1,2)
box2 = Box.new(2,4)
puts box1
puts box2
puts box1 + box2
```
