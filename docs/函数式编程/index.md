# 函数式编程

> 函数式编程的目标是使用函数来抽象作用在数据之上的控制流与操作,从而在系统中消除副作用并减少对状态的改变

写代码时:

1. 可扩展性
2. 易模块化
3. 可重用性
4. 可测性
5. 易推理性

## 指导思想

- 函数式编程将函数看作积木, 通过高阶函数来提高代码的模块化和可用性
- 通过响应式编程来降低事件驱动程序的复杂性

## 函数式编程是声明式编程

声明式: 这种范式描述一系列操作, 并不会暴露内部实现和数据流

命令式: 很具体的告诉计算机如何执行某个任务

```javascript
// 命令式
for (let i = 0; i < 10; i++) {
  console.log(i * i);
}

// 声明式
arr.map(item => item * item);
```

## 纯函数

所有的函数对于相同的输入都将返回相同的值，使得并发代码和缓存成为了可能

1. 输出仅取决于提供的输入, 不依赖于外部状态
2. 不会造成超出其作用域的变量的污染
3. 输出是可以预见的