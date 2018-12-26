# �Զ�����������

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

�÷���
```haskell
let dylan = Person { firstName = "dylan", lastName = "Gao", age = 27, height = 1.70, phoneNumber = "13863962164" }
```

## 2. newtype

**`newtype`�ؼ����������Ѵ��ڵ����ͣ�����һ���µ���ݡ�**

### `newtype`��`data`������

* **1. `newtype`��`data`���Ƹ��࣬`newtype`ֻ����һ��ֵ�������������ֵ������ֻ����һ���ֶ�**

```haskell
-- �����÷���
newtype TooFew = TooFew                         -- ���ֶ�
newtype TooManyFields = Fields Int Int          -- ����һ���ֶ�
newtype TooManyCtors = Bad Int | Worse Int      -- ����һ��ֵ������
```

* **2. ʹ��`data`���������ͣ�������ʱ���в��ǵĻ�������`newtype`�������������޴˿���**
  
   ��ΪҪ���ٸ����͵�ֵ�����ĸ�ֵ�����������ġ���`newtype`���������ͣ���Ϊֻ����һ��ֵ������������û�����ָ�������ʹ�������е�ʱ��������ʱ�仹�ǿռ��϶�����Ч�ʡ���Ϊ`newtype`��ֵ��������ֻ���ڱ���ʱ��**������ʱ�ǲ����ڵġ�**

```haskell
newtype Time = Second Float
```

�����Զ�����һ��`Time`���ͣ�`Time`��`Float`�����ֲ�ͬ�����ͣ����Ǳ����ϴ洢��������ʽȴ����ͬ�ģ�����`Float`��ʽ�ģ����ڱ����ڼ���֪��`Time`�������ݴ�С�ʹ洢��ʽ����˱�����Ѳ�����Ҫֵ������`Second`��

### `newtype`��`type`������

`newtype`����һ���Ѵ��ڵ������Զ���һ��**������**��`type`��Ϊ�Ѵ��ڵ�������һ��**����**��

```haskell
newtype NewtypeFloat = NewFloat Float    -- NewtypeFloat��Float�ǲ�ͬ������
type DataFloat = Float                   -- DataFloat��Float�ı�����������ȫ�ȼۣ����Ի���
```
