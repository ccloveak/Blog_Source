---
title: Typescript Tips (1)
author: せいい
top: false
cover: false
toc: true
tags:
  - output
categories:
  - Frontend
date: 2021-01-17 10:44:56
summary: Typescript中的基础类型
---

## 背景
* 工作中使用typescript感觉有欠缺的地方
* 重新过一遍typescript官方文档，希望能有收获

## 基础类型
1. `boolean`
* 简单的true/false值
```Typescript
let isDone: boolean = false;
```

2. `number`
* 支持十进制,十六进制,二进制,八进制字面量
```Typescript
let decLiteral: number = 6;             //十进制
let hexLiteral: number = 0xf00d;        //十六进制
let binaryLiteral: number = 0b1010;     //二进制
let octalLiteral: number = 0o744;       //八进制
```

3. `string`
* 模版字符串
```Typescript
let name: string = `Gene`;
let age: number = 37;
let sentence: string = `Hello, my name is ${ name }.
I'll be ${ age + 1 } years old next month.`;
```

4. 数组 Array
* 在元素类型后面接上 []，表示由此类型元素组成的一个数组
```Typescript
let list: number[] = [1, 2, 3];
```
* 使用数组泛型，Array<元素类型>
```Typescript
let list: Array<number> = [1, 2, 3];
```

5. 元组 Tuple
* 元组类型允许表示一个已知元素数量和类型的数组，各元素的类型不必相同。
```Typescript
// Declare a tuple type
let x: [string, number];
// Initialize it
x = ['hello', 10]; // OK
// Initialize it incorrectly
x = [10, 'hello']; // Error
console.log(x[0].substr(1)); // OK
console.log(x[1].substr(1)); // Error, 'number' does not have 'substr'
x[3] = 'world'; // OK, 字符串可以赋值给(string | number)类型
console.log(x[5].toString()); // OK, 'string' 和 'number' 都有 toString
x[6] = true; // Error, 布尔不是(string | number)类型
// 这部分无法归纳总结，官网示例很详细了。。。
```

6. `enum`
* 使用枚举类型可以为一组数值赋予友好的名字
```Typescript
enum Color {Red, Green, Blue}
let c: Color = Color.Green;
```
```Typescript
enum Color {Red = 1, Green = 2, Blue = 4}
let c: Color = Color.Green;
```
```Typescript
enum Color {Red = 1, Green, Blue}
let colorName: string = Color[2];
console.log(colorName);  // 显示'Green'因为上面代码里它的值是2
```

7. `any`
* 为在**编程阶段**还不清楚类型的变量指定一个类型
* 所以在请求合并前，不该有any类型存在

8. `void`
* 一个函数没有返回值时，其返回值类型是 `void`
* 不要傻乎乎的去声明一个变量为 `void` 类型

9. `null` 和 `undefined`
* 默认情况下`null`和`undefined`是所有类型的子类型
* 尽可能地使用 `--strictNullChecks`
* 官网这里尽可能的想说明白，但是确实有点复杂。。。
* 留个印象，期待在看最佳实践的时候会恍然大悟。

10. `never`
* `never`类型表示的是那些永不存在的值的类型。
* 留个印象，期待在看最佳实践的时候会恍然大悟。
```Typescript
// 返回never的函数必须存在无法达到的终点
function error(message: string): never {
    throw new Error(message);
}
// 推断的返回值类型为never
function fail() {
    return error("Something failed");
}
// 返回never的函数必须存在无法达到的终点
function infiniteLoop(): never {
    while (true) {
    }
}
```

11. `object`
* `object`表示非原始类型
```Typescript
declare function create(o: object | null): void;
create({ prop: 0 }); // OK
create(null); // OK

create(42); // Error
create("string"); // Error
create(false); // Error
create(undefined); // Error
```

## 类型断言

* 通过*类型断言*这种方式可以告诉编译器，“相信我，我能行，我知道自己在干什么”。
* 没有运行时的影响，只是在编译阶段起作用。 TypeScript会假设你已经进行了必须的检查

1. “尖括号”语法
```Typescript
let someValue: any = "this is a string";
let strLength: number = (<string>someValue).length;
```
2. `as`语法
* 在TypeScript里使用JSX时，只有 `as`语法断言是被允许的
```Typescript
let someValue: any = "this is a string";
let strLength: number = (someValue as string).length;
```

## 参考

* [文档](https://www.tslang.cn/docs/handbook/basic-types.html)
