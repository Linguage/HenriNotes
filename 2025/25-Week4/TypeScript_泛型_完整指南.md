TypeScript 泛型：完整指南  
- 原文标题：TypeScript Generics: A Complete Guide  
- 链接：https://www.syncfusion.com/blogs/post/typescript-generics-guide?ref=dailydev  

- **文章类别**：博客  

---

**内容整理**：

### 文章框架
```
├── 引言
│   ├── TypeScript 泛型简介
│   └── 泛型的重要性
├── TypeScript 泛型是什么？
│   ├── 泛型的定义
│   └── 泛型的作用
├── 使用 TypeScript 泛型的场景
│   ├── 泛型函数
│   │   ├── 单个泛型参数
│   │   └── 多个泛型参数
│   ├── 默认泛型类型
│   ├── 泛型接口
│   ├── 泛型类
│   └── 泛型约束
├── 结论
└── 相关博客推荐
```

### 文章内容

#### 引言
- TypeScript 泛型允许开发者编写可重用的代码，这些代码可以处理多种数据类型，同时保持类型安全。它们是构建健壮且可扩展的 TypeScript 应用程序的基础。

#### TypeScript 泛型是什么？
- **泛型的定义**：TypeScript 泛型允许开发者在代码中定义占位符类型，从而在保持类型安全的同时，使代码更加灵活、可扩展且可重用。泛型通过在编译时进行类型检查，确保代码的类型安全性。
- **泛型的作用**：在没有泛型的情况下，开发者需要为每种数据类型编写多个版本的函数或类，这会导致代码重复。泛型允许通过单一实现处理多种类型，同时保留静态类型检查。

#### 使用 TypeScript 泛型的场景
- **泛型函数**
  - **单个泛型参数**：
    ```typescript
    function identity<T>(value: T): T {
      return value;
    }
    const result1 = identity<number>(42);      // result1: number
    const result2 = identity<string>("hello"); // result2: string
    ```
    TypeScript 会确保输入类型和返回类型一致。
  - **多个泛型参数**：
    ```typescript
    function multipleParams<T, U>(first: T, second: U): [T, U] {
      return [first, second];
    }
    const result1 = multipleParams<string, number>("hello", 42); // result1: [string, number]
    ```
    泛型可以处理多个不同类型的输入，并确保类型安全。

- **默认泛型类型**：
  ```typescript
  function createArray<T = string>(length: number, value: T): T[] {
    return Array(length).fill(value);
  }
  const stringArray = createArray(3, "hello"); // 默认类型为 string
  const numberArray = createArray<number>(3, 42); // 显式指定类型为 number
  ```
  如果未指定类型，泛型会使用默认类型。

- **泛型接口**：
  ```typescript
  interface Box<T> {
    value: T;
  }
  const numberBox: Box<number> = { value: 123 };
  const stringBox: Box<string> = { value: "hello" };
  ```
  泛型接口可以确保接口的属性类型严格符合定义。

- **泛型类**：
  ```typescript
  class Storage<T> {
    private data: T;
    setItem(item: T): void {
      this.data = item;
    }
    getItem(): T {
      return this.data;
    }
  }
  const numberStorage = new Storage<number>();
  numberStorage.setItem(123);
  const item = numberStorage.getItem(); // 返回类型为 number
  ```
  泛型类可以处理不同类型的值，同时保持类型安全。

- **泛型约束**：
  ```typescript
  function printLength<T extends { length: number }>(value: T): void {
    console.log(value.length);
  }
  printLength("hello"); // 输出：5
  printLength([1, 2, 3]); // 输出：3
  ```
  泛型约束可以限制泛型接受的类型，确保它们具有特定的属性。

#### 结论
TypeScript 泛型允许开发者编写灵活、可重用且类型安全的代码。通过在类、方法和接口中使用泛型，可以管理多种数据类型而无需重复代码。文章还介绍了泛型约束、默认类型等关键用例，展示了如何通过这些特性提高代码的可扩展性和可维护性。理解 TypeScript 泛型有助于编写更精确、更灵活且类型安全的代码，使 TypeScript 应用程序更加健壮。

#### 相关博客推荐
- [Webpack vs Vite: Which Bundler is Right for You?](https://www.syncfusion.com/blogs/post/webpack-vs-vite-bundler-comparison)
- [Build Micro Frontends with single-spa: A Guide](https://www.syncfusion.com/blogs/post/build-micro-frontends-with-single-spa)
- [Master Asynchronous JavaScript with RxJS](https://www.syncfusion.com/blogs/post/master-asynchronous-javascript-with-rxjs)
- [Axios and Fetch API? Choosing the Right HTTP Client](https://www.syncfusion.com/blogs/post/axios-vs-fetch-choose-right-http-client)

### 文章标签
#TypeScript ， #Generics ， #Programming ， #TypeSafety