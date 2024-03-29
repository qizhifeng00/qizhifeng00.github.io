# Rust

入门到入土

## 变量

在 rust 里变量只能赋值一次，不可分配第二个值
可以加 mut 在变量名前面使其可变

```rust
//不可变
let x = 5;
//可变
let x mut = 5;
```

## Modules

> Rust 有许多特性可以让你管理代码的组织，包括哪些细节是公开的，哪些细节是私有的，以及程序中每个范围内的名称。这些功能有时统称为模块系统，包括：

Packages：一种 Cargo 功能，可让您构建、测试和共享 crate
Crates：生成库或可执行文件的模块树
Modules：让您控制路径的组织、范围和隐私
Paths：命名项目的一种方式，例如结构、函数或模块
