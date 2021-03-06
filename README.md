# 1. 简介
这是一个非常早期的 demo，但已经实现了一个操作系统最最最基本的模块，包含有起始扇区、loader 和内核 demo（尽管“内核”只打印了几行字）

你可以通过在一个裸机或虚拟机中加载这个 demo 系统来启动他

可以参考完整的系列日志，具备从 0 到目前的详细原理与实践过程：[实现一个操作系统](https://techlog.cn/article/list/10183466)

# 2. 目录结构
```
.
├── Makefile
├── README.md
├── bochsrc.bxrc
├── boot
│   ├── boot.asm
│   ├── inc
│   │   ├── fat12hdr.asm
│   │   ├── lib.asm
│   │   └── pm.asm
│   └── loader.asm
├── boot.img
├── include
│   └── functions.h
├── kernel
│   ├── global.c
│   ├── i8259.c
│   ├── i8259.h
│   ├── kernel.asm
│   ├── protect.c
│   └── protect.h
└── lib
    ├── extern.asm
    ├── functions.c
    └── interrupt.asm

5 directories, 19 files
```

# 3. 启动方式
## 3.1 直接启动
无论在哪个环境，你都可以通过下载[bochs 虚拟机](http://bochs.sourceforge.net)，加载目录中的 bochsrc.bxrc 配置文件，启动 bochs 虚拟机，执行 `c` 或 `continue` 指令运行该 demo 系统
- 我所使用的 bochs 版本为 2.6.11，如果你使用的是其他版本，可能需要对上述配置文件略做修改

当然，你也可以用任何一个虚拟机，将 boot.img 作为虚拟软盘启动系统即可

## 3.2 编译启动
在根目录下，执行：
> make all

可以编译全部代码并生成最新的 boot.img，根据上述直接启动的方法，可以通过 bochs 虚拟机加载并启动 boot.img

# 4. 更新记录
- 2020.07.18 首次上传，实现从 BIOS 进入起始扇区，起始扇区加载 loader，loader 进入保护模式并加载 demo kernel
- 2021.04.22 在 kernel 中添加 CPU 异常以及硬件中断响应机制

# 5. 鸣谢
本系统 demo 主要参考于渊所著的《Orange'S 一个操作系统的实现》，其他参考资料见完整日志

# 6. 微信公众号
![Snipaste_2021-04-21_13-30-12](https://user-images.githubusercontent.com/5253434/115501427-c991a100-a2a5-11eb-8263-48452ff4c5f8.jpg)
