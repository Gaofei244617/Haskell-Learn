# 自定义数据类型

## 1. data

Examples:

```haskell
data Day = Monday | Tuesday | Wednesday | Thursday | Friday | Saturday | Sunday
```

```haskell
data Maybe a = Nothing | Just a
```

```haskell
data Shape = Circle Float Float Float | Rectangle Float Float Float Float deriving (Show)
```

用法：

```haskell
let a = Circle 0 0 5.0
```

1. `Circle`和`Rectangle`称为值构造器，`Circle`有3个字段，`Rectangle`有4个字段；
2. 值构造器本质上为一个函数（`Circle :: Float -> Float -> Float -> Shape`）；

```haskell
data Person = Person String String Int Float String deriving (Show)
```

记录语法：

```haskell
data Person = Person { firstName::String,
                       lastName::String,
                       age::Int,
                       height::Float,
                       phoneNumber::String} deriving (Show)
```

用法：
```haskell
let dylan = Person { firstName = "dylan", lastName = "Gao", age = 27, height = 1.70, phoneNumber = "13863962164" }
```

## 2. newtype

**`newtype`关键字用来给已存在的类型，设置一个新的身份。**

### `newtype`和`data`的区别：

* **1. `newtype`比`data`限制更多，`newtype`只能有一个值构造器，且这个值构造器只能有一个字段**

```haskell
-- 错误用法：
newtype TooFew = TooFew                         -- 无字段
newtype TooManyFields = Fields Int Int          -- 多于一个字段
newtype TooManyCtors = Bad Int | Worse Int      -- 多于一个值构造器
```

* **2. 使用`data`创建的类型，在运行时具有簿记的花销，而`newtype`创建的类型则无此开销**
  
   因为要跟踪该类型的值是由哪个值构造器创建的。而`newtype`创建的类型，因为只能有一个值构造器，所以没有这种负担，这使得在运行的时候，无论在时间还是空间上都更有效率。因为`newtype`的值构造器，只用于编译时，**在运行时是不存在的。**

```haskell
newtype Time = Second Float
```

以上自定义了一个`Time`类型，`Time`和`Float`是两种不同的类型，但是本质上存储的数据形式却是相同的（都是`Float`形式的）。在编译期即可知道`Time`类型数据大小和存储形式，因此编译后已不再需要值构造器`Second`。

### `newtype`和`type`的区别：

`newtype`是用一个已存在的类型自定义一个**新类型**，`type`是为已存在的类型起一个**别名**。

```haskell
newtype NewtypeFloat = NewFloat Float    -- NewtypeFloat和Float是不同的类型
type DataFloat = Float                   -- DataFloat是Float的别名，二者完全等价，可以互换
```
