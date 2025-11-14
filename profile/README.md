# Zero Programming Language

Zero 是一个现代编程语言项目，主要包含两个核心实现：使用 Rust 编写的字节码编译器与虚拟机（Zero-Compiler），以及使用 C++17 编写的编译器工具链（CZC）。

## 项目组成

### Zero-Compiler (Rust)

基于 Rust 实现的完整编译器工具链，采用字节码编译器 + 虚拟机架构，提供从源码到执行的完整支持。

#### 核心特性

- **字节码编译**: 将 Zero 源代码编译为高效的字节码指令
- **虚拟机执行**: 基于栈的虚拟机，快速执行字节码
- **静态类型系统**: 编译期类型检查与智能类型推导
- **数组支持**: 完整的数组字面量、索引访问和类型检查
- **字节码序列化**: 支持保存和加载编译后的 .zbc 字节码文件
- **控制流**: if/else、while、for 循环等完整的控制流结构
- **函数系统**: 支持函数声明、调用和递归

#### 架构设计

```text
源代码 -> Lexer -> Tokens -> Parser -> AST -> Compiler -> Bytecode -> VM -> 执行
```

采用现代编译器设计，清晰分离各个编译阶段：

- **词法分析器 (Lexer)**: 将源代码转换为 Token 流
- **语法分析器 (Parser)**: 构建抽象语法树，采用递归下降解析
- **类型检查器 (Type Checker)**: 静态类型检查和类型推导
- **编译器 (Compiler)**: 将 AST 编译为字节码指令
- **虚拟机 (VM)**: 执行字节码指令

#### 技术栈

- **语言**: Rust Edition 2021
- **依赖**: 最小化依赖，主要使用 Rust 标准库
- **测试**: Cargo 内置测试框架

### CZC (C++)

使用 C++17 实现的编译器工具链，提供词法分析、语法分析、代码格式化等完整的编译器功能。

#### 编译器特性

- **完整的词法分析**: 支持 UTF-8 编码、科学计数法、字符串转义等高级特性
- **鲁棒的语法分析**: 基于递归下降的 Parser，构建具体语法树 (CST)
- **智能错误诊断**: 多语言错误消息系统（英文、中文、韩文），精确的错误定位
- **代码格式化**: 提供可配置的代码格式化工具
- **Token 预处理**: 智能处理科学计数法等特殊 Token
- **模块化设计**: 清晰的命名空间和组件分离

#### 模块组成

- **lexer**: 词法分析器，包含 Token 定义和 UTF-8 处理
- **parser**: 语法分析器，构建 CST 并进行语法检查
- **cst**: 具体语法树节点定义
- **ast**: 抽象语法树构建和访问者模式
- **diagnostics**: 诊断系统，支持多语言错误消息
- **formatter**: 代码格式化器，支持可配置的格式选项
- **token_preprocessor**: Token 预处理器
- **utils**: 工具类，包括源码追踪、文件收集等

#### 构建技术

- **语言**: C++17
- **构建系统**: CMake 3.15+
- **文档**: Doxygen
- **测试**: CTest
- **代码质量**: clang-format, clang-tidy

## 开发状态

### 已完成

- 完整的词法分析器（支持 UTF-8、科学计数法、转义字符等）
- 语法分析器（递归下降解析）
- 抽象语法树（完整的 AST 节点）
- 静态类型系统（基础类型 + 数组类型）
- 类型检查器（编译期类型检查）
- 类型推导（局部类型推导）
- 数组支持（字面量、索引访问、类型检查）
- 字节码编译器（AST -> 字节码）
- 虚拟机（基于栈的 VM）
- 字节码序列化/反序列化
- 基本数据类型和运算
- 控制流（if/while/for）
- 函数定义和调用
- 递归函数支持
- 代码格式化工具
- 多语言错误诊断系统

### 进行中

- 数组方法（push、pop、insert 等）
- 函数返回类型注解完整支持
- 性能优化和基准测试

### 计划中

- 模块系统（import/export）
- 标准库（字符串、数组、IO 等）
- 错误处理（try-catch）
- 闭包（捕获外部变量）
- 垃圾回收（标记-清除 GC）
- 泛型支持
- 结构体/类
- REPL（交互式解释器）
- 调试器（断点、单步执行）
- LSP 支持（IDE 集成）
- 包管理器

## 文档

### Zero-Compiler

- [语言规范](https://github.com/Zero-Compiler/Zero-Compiler/blob/main/docs/LANGUAGE_SPEC.md)
- [架构文档](https://github.com/Zero-Compiler/Zero-Compiler/blob/main/docs/ARCHITECTURE.md)
- [类型系统](https://github.com/Zero-Compiler/Zero-Compiler/blob/main/docs/TYPE_SYSTEM.md)
- [数组系统](https://github.com/Zero-Compiler/Zero-Compiler/blob/main/docs/ARRAYS.md)
- [字节码格式](https://github.com/Zero-Compiler/Zero-Compiler/blob/main/docs/BYTECODE_FORMAT.md)
- [贡献指南](https://github.com/Zero-Compiler/Zero-Compiler/blob/main/CONTRIBUTING.md)

### CZC

暂无

## 许可证

Zero-Compiler: MIT License
CZC: The Unlicense

## 致谢

本项目的设计和实现受到以下项目的启发：

- [Crafting Interpreters](https://craftinginterpreters.com/) by Robert Nystrom
- [Writing An Interpreter In Go](https://interpreterbook.com/) by Thorsten Ball
- Lua VM Architecture
