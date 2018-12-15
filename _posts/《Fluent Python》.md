---
layout:     post
title:      Fluent Python
subtitle:   读书笔记
date:       2018-06-05
author:     WYB
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - Python
---

# Chapter 2 An Array of Sequences
### Augmented Assignment with Sequences
+=的实现是__iadd__方法，如果没有这个方法解释器就会用__add__方法。这两个会有区别的，因为大多时候+=是不会改变对象，而用__add__方法就可能是创建个新对象再把引用给过去，查id就不一样。

*=当然就是__imul__方法了。

##### A+=Assigment Puzzler
这个主要就是个费解的错误，作者试图在typle里对一个list赋值，结果报错，但是赋值操作又成功了……

结论：
1. 在tuple中放置mutable items很蠢。
2. Augmented Assignment 不是原子操作。
3. 建议查看Python bytecode。

### list.sort and the sorted Built-In Function

前者会改变原来对象顺序并返回None，后者创建了新的对象。两个都有关键字key reverse。

### Managing Ordered Sequences with bisect
The bisect can use bisect function and insort function to quickly find and insert items in any sorted sequences.

# Chapter 3 Dictionaries and Sets

### Generic Mapping Types

All mapping types in the standard library use the basic dict in their implementation.

The keys must be hashable
1. An object is hashable if its has a hash value which never changed during its lifetime.( _ _ hash _ _ ()   )
2. And can be compared to other objects.(_ _ eq() _ _)
3. The atomic immutable types are all hashable.
4. A frozenset is hashable.
5. A tuple is hashable only if its items are hashable.
6. User-defined types are hashable by default.

### dict Comprehensions
这里就是说有种简单字典建立方法，用字典结构的列表建立。

### Overview of Common Mapping Methods
dict defaultdict OrderedDict 里一些方法实现情况。

### Handling Missing Keys with setdefault

就是在讲处理dict里key又时会遇到missing keys 这时候理论上会返回错误信息，然后这里提供个方法可以编造个key继续运行。

### Mappings with Flexible Key Lookup

##### defaultdict

##### THe __missing__ Method

### Variations of dict
Some mapping types.
1. collections.OrderedDict
  
  一个永远保持输入顺序的字典。
2. collections.ChainMap

 一个可以把一堆字典合成一个字典进行搜索的字典。
3. collections.Counter

可以用来对key计数。

4. collections.UserDict

a pure Python mapping.

### Subclassing UserDict

The reasons we use UserDict rather than built-in dict is that the built-in has some implementation shortcuts that end up forcing us to override methods that we can just inherit from UserDict with no problems.

### Immutable Mappings
用的types里MappingProxyType类改一下。

MappingProxyType(dict_)
### Set Theory
set elements is hashable.
The set type is not hashable,but frozenset is. You can have a frozenset inside a set. 

set have some operators
1. a|b
2. a&b
3. a-b

# Chapter 7 Function Decorators and Closures
### Decorators 101
修饰器就是把被修饰函数当作输入，然后返回一个函数顶替被修饰函数。
### When Python Executes Decorators
Function decorators are executed as soon as the module is improved,but the decorated functions only run when they are actually invoked.
### Decorator-Enhanced Strategy Pattern
上一章的例子，如果忘记把新函数更新加入列表就会出现微妙的bug，但是可以写个修饰器专门干这个事情，让修饰器出现在每个函数函数之前。
### Variable Scope Rules
变量的作用范围。

如果函数里对某变量有assignment,则函数内其他地方都认为该变量作用在内部，如果没有则认为在外部。如果函数内既有assignment又希望作用外部需要在函数开始地方用global声明一下。

### Closures
A closure is a function with an extended scope that encompasses nonglobal variables referenced in the body of the function but not defined there.  
说白了就是在函数内用了一个没有定义的非全局变量。对于这个函数来说，这个变量就是free variable.  
free variable is a variable that is not bound in the local scope.  
Python keeps the name of local and free variables in the __code __attribute that represents the compiled bdy of the function.  
To summarize A closure is a function that retains the bindings of the free variables that exits when the function if defined, so they can be used later when the fnction is invoked and the defining scope is no longer available.  
__A function may need to deal with external variables that are nonglobal is when it is nested in another function.__
### The nonlocal Declaration
