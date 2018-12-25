# 自定义数据类型

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

```haskell
let dylan = Person { firstName = "dylan", lastName = "Gao", age = 27, height = 1.70, phoneNumber = "13863962164" }
```
