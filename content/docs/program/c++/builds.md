---
title: "编译和构建"
---

## 1.bazel构建工具介绍和使用

    由 Google 开发的一款构建和测试工具，专为速度和可靠性而设计，能处理任何规模的项目。
    其核心理念是可复现性——也就是说，只要代码相同，任何人、在任何地方构建出来的结果都应该是完全一致的。
    Bazel 是一个基于工件的构建系统。虽然基于任务的构建系统比构建脚本更高级，但它们会让工程师自行定义任务，从而赋予他们过多权力。

## 2.优点
* 增量编译


## 3.构建示例
以下是 Bazel 中的 buildfile（通常命名为 BUILD）的示例：
``` shell
java_binary(
    name = "MyBinary",
    srcs = ["MyBinary.java"],
    deps = [
        ":mylib",
    ],
)
java_library(
    name = "mylib",
    srcs = ["MyLibrary.java", "MyHelper.java"],
    visibility = ["//java/com/example/myproduct:__subpackages__"],
    deps = [
        "//java/com/example/common",
        "//java/com/example/myproduct/otherlib",
    ],
)
```

在 Bazel 中，BUILD 文件用于定义目标，这里的两种目标类型分别为 java_binary 和 java_library。每个目标都对应于系统可以创建的工件：二进制目标会生成可直接执行的二进制文件，而库目标会生成可供二进制文件或其他库使用的库。每个目标都有：

name：命令行和其他目标如何引用目标
srcs：要编译以为目标创建工件的源文件
deps：必须先于此目标构建并链接到此目标的其他目标


