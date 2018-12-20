## Linux 加载可执行目标文件


运行时内存映像：
```
内存内核
======= 2^48-1 地址
用户栈(运行时创建)
...
...      <- 栈指针
=======

共享库的内存映射区域(动态库)

=======  <- 堆内存
...
...
运行时堆(由malloc创建)
=======
读/写段
.data, .bss
-------
只读代码段
(.init, .text, .rodata)
======= 0x400000
        0
```


## iOS App运行

### 启动流程

总启动时间 = main()之前的时间  + main()之后的时间

#### main()之前的时间
 
t = dylib 加载动态库 + 自身App可执行文件加载


动态库包括 系统framework、oc runtime、第三方的framework、

#### 动态库加载流程
1. load dylib image 读取文件，加载到内存
2. rebase image
3. bind image
4. objc setup
5. initializers

详细：https://techblog.toutiao.com/2018/05/29/untitled-24/

#### main()之后的时间

main方法执行之后到AppDelegate类中的- (BOOL)Application:(UIApplication *)Application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions方法执行结束前这段时间

#### 启动分析

https://techblog.toutiao.com/2018/05/29/untitled-24/

#### runtime 加载

https://www.jianshu.com/p/c54efcb54018

