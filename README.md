# C/C++ 基础必修题

NCUSCC 踏浪者平台「C/C++ 必修」模块的四道练习题参考实现,覆盖统计、结构体、环形缓冲、多文件构建四个基础考点。

## 题目清单

| 题目 | 文件 | 考点 |
|------|------|------|
| 读数统计 | `readings.cpp` | 防溢出(`long long`)、min/max 初始化、空输入处理 |
| 设备巡检记录 | `device.cpp` | 结构体封装、过滤/统计/查询拆函数 |
| 固定容量读数窗口 | `window.c` | 环形缓冲、下标取模防越界 |
| 多文件统计工具 | `stats.h` `stats.cpp` `main.cpp` `CMakeLists.txt` | 头文件保护、声明与实现分离、CMake 构建 |

## 环境要求

- 编译器:GCC / g++(Linux 环境)
- C 标准:C11 或以上
- C++ 标准:C++17 或以上
- 构建工具:CMake 3.10+(仅多文件统计工具需要)

> 注意:`#include <bits/stdc++.h>` 是 GCC 专用头文件,在 Linux 的 g++ 下正常,Windows 的 MSVC 不支持。

## 目录结构

```
.
├── README.md
├── readings.cpp          # 读数统计
├── device.cpp            # 设备巡检记录
├── window.c              # 固定容量读数窗口
├── stats.h               # 多文件统计工具:头文件
├── stats.cpp             # 多文件统计工具:实现
├── main.cpp              # 多文件统计工具:入口
└── CMakeLists.txt        # 多文件统计工具:构建配置
```

## 编译与运行

### 1. 读数统计

```bash
g++ -std=c++17 readings.cpp -o readings
./readings < input.txt
```

从标准输入读取若干整数,输出 `个数 总和 最小值 最大值`。

### 2. 设备巡检记录

```bash
g++ -std=c++17 device.cpp -o device
./device
```

用结构体封装设备记录,演示按状态过滤、求值总和、按 ID 查询。

### 3. 固定容量读数窗口

```bash
gcc window.c -o window
./window < readings.txt
```

只保留最近 8 个读数,按从旧到新的顺序输出。

### 4. 多文件统计工具

```bash
cmake -S . -B build
cmake --build build
./build/main
```

头文件、实现文件、入口文件分离,通过 CMake 统一构建。

## 说明

- 本仓库为参考实现,用于梳理各题的核心考点;实际平台题目若提供原始源码,请在其基础上按相同思路修复。
- 每道题均为独立小程序,可单独编译运行。
- 若想按题目分目录管理,可将每个题目的文件放入各自的子文件夹,再为每个子文件夹单独配置构建。

## 许可证

MIT License
