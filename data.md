# �Զ�����������

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

�÷���

```haskell
let a = Circle 0 0 5.0
```

1. `Circle`��`Rectangle`��Ϊֵ��������`Circle`��3���ֶΣ�`Rectangle`��4���ֶΣ�
2. ֵ������������Ϊһ��������`Circle :: Float -> Float -> Float -> Shape`����

```haskell
data Person = Person String String Int Float String deriving (Show)
```

��¼�﷨��

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
