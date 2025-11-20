# CppShield 🔒🛡️

**让现代 C++ 拥有 Rust 级别的内存与线程安全**

CppShield 是一款基于 Clang 深度定制的工业级静态分析工具，目标是：在编译期就把 C++ 最致命的内存安全漏洞（use-after-free、use-after-move、double free、data race、buffer overflow 等）全部拦截，让老项目也能享受“默认安全”的快感。

我们不满足于 Clang-Tidy 那种“只能提醒”的 lint，而是实现了真正的**路径敏感借用检查器（Borrow Checker）**和**所有权追踪系统**，对标 Rust 的核心安全保证。

### 当前里程碑（2025.11 进行中）
- [x] 完整的工业级 LibTooling + Clang Static Analyzer 骨架（支持 compile_commands.json、增量分析、跨平台）
- [x] 成功构建 CFG 并过滤系统头/非主文件
- [ ] 检测 `std::move` 后的非法使用（use-after-move）← 当前冲刺目标
- [ ] unique_ptr/shared_ptr 双删、泄漏、裸指针生命周期检查
- [ ] 原始指针的借用检查（Owned / MovedFrom / MutBorrowed / ImmBorrowed）
- [ ] 线程安全分析（Send + Sync trait 模拟）
- [ ] 跨翻译单元分析（CTA）
- [ ] SARIF 报告 + VS Code / CLion 插件

### 最终愿景
> “There are only two kinds of C++ programs:  
> those that have been audited by CppShield,  
> and those that will crash in production.”

### 为什么叫 CppShield？
因为它就是现代 C++ 的**防护盾**——在亿级代码库里，替你挡下那些悄无声息就能让系统崩塌的内存安全漏洞。

### CppShield 🔒🛡️ Make Modern C++ as Safe as Rust

CppShield is an industrial-grade static analyzer deeply built on Clang 19+, aiming to eliminate 99% of the most dangerous memory safety bugs in C++ at compile time: use-after-free, use-after-move, double free, data races, buffer overflows, etc.

Instead of superficial linting like Clang-Tidy, we are implementing a real **path-sensitive borrow checker** and **ownership tracking system** that mirrors Rust’s core safety guarantees.

Current Progress (Nov 2025):
- [x] Full industrial LibTooling + Clang Static Analyzer skeleton
- [x] CFG construction & main-file filtering
- [ ] Detect use-after-move after std::move ← sprinting
- [ ] unique_ptr/shared_ptr double-delete & leak detection
- [ ] Raw pointer borrow checking (Owned/MovedFrom/Borrowed states)
- [ ] Thread-safety analysis (Send+Sync simulation)
- [ ] Cross-translation-unit analysis
- [ ] SARIF reports + IDE plugins

Star it. Watch it. Fork it.  
Let’s shield the C++ world together.