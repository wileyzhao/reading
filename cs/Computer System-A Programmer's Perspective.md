## Chapter One: 计算机系统漫谈
计算机基本思想：
系统中所有的信息，包括磁盘文件、程序、数据等，都是由一串位表示的。

compilation system

<img width="700" alt="image" src="https://github.com/wileyzhao/reading/assets/21215474/94484c20-38ed-422d-874e-ca7ea3384575">

![56FDFB4A-0A15-46B3-80D5-0312711C81AA](https://github.com/wileyzhao/reading/assets/21215474/091efe43-b699-4852-9c1e-fc6fd658d144)


![F2B08A07-69E9-42C6-9B61-434C6F6CB427](https://github.com/wileyzhao/reading/assets/21215474/ce24af61-aef0-4c99-85f4-fc309dcf6f69)


文件就是字节序列，仅此而已。每个I/O设备，包括磁盘、键盘、显示器、甚至网络，都可以视为文件。

系统间通过网络通信，网络也是一种I/O设备，当系统从主存将一串字节复制到网络适配器时，数据流经过网络到达另一台机器，相似的，系统可以读取从其他机器发送过来的数据，并把数据复制到自己的主存中。

操作系统内核是应用程序和硬件之间的媒介。它提供三个基本的抽象：
1、文件是对I/O设备的抽象
2、虚拟存储器是对主存和磁盘的抽象
3、进程是对处理器、主存和I/O设备的抽象

## Chapter Two: 信息的表示和处理
字长（word size），知名证书和指针数据的标称大小（nominal size），字长决定的最重要的系统参数就是虚拟地址空间的最大大小。
c语言中数字数据类型的字节数
c声明
32位机器
64位机器
<img width="525" alt="image" src="https://github.com/wileyzhao/reading/assets/21215474/804330fb-590f-49e1-86ac-a4527fd1255e">


c和c++都支持有符号（默认）和无符号数。Java只支持有符号数。
关于整数数据类型的取值范围和表示，Java标准是非常明确地，它要求采用补码表示，这些非常具体的要求都是为了保证无论在什么机器上，Java程序运行的表现都完全一样。
补码：是对除了符号位外，对所有位取非，再加1    例如：-2 = [1000 0010]    补码为[1111 1110] = 126。

在大多数机器上，整数乘法除法的运算很慢，分别大概需要至少10、30的时钟周期，所以编辑器会尽量使用移位和加法的组合来代替乘法和除法。

电气和电子工程师协会（IEEE，读作“Eye-Triple-Eee”）


## Chapter Three: 程序的机器级表示

介绍两种相关的机器语言：Intel IA32 和 x86-64


理解指针：
1、每个指针都对应一个类型
2、每个指针都有一个值，这个值是某个特定类型对象的地址。NULL表示没有指向任何地方。
3、指针用 & 运算符创建
4、运算符 * 用于指针的间接引用，其结果是一个值
5、数组与指针紧密相连
6、将指针从一种类型强制转换成另一种类型，只改变它的类型，而不改变它的值
7、指针也可以指向函数


## Chapter Four: 处理器体系结构

实现所有Y86指令所需要的计算可以组织成六个基本阶段：
取指、译码、执行、访存、写回、更新PC

SEQ的硬件结构
![CACE5FF6-74A1-48E1-AFEE-1C7EEB2F830E](https://github.com/wileyzhao/reading/assets/21215474/ef7c2be1-e3f7-49f6-bb14-2d9620ce59e9)


## Chapter Five： 优化程序性能

延迟界限（latency bound）
因为下一条指令开始前，这条指令必须结束，所以会限定程序的性能。
吞吐量界限（throughput bound）
刻画了处理器功能单元的原始计算能力，这个界限是程序性能的终极极限。

为了提高执行速度，处理器会采用分支预测（branch prediction）技术，提前预测并执行分支，如果预测错误，就重新执行新的分支。

指令控制单元负责从存储器中读出指令，并产生一系列基本操作。然后执行单元完成这些操作，已经指出分支预测是否正确。


https://www.jianshu.com/p/15210eb3870d


程序优化性能的基本策略：
1、高级设计，选取适当的算法和数据结构，特别要警觉，避免使用那些会渐进的产生糟糕性能的算法和编程设计
2、基本编码的规则：
消除循环的低效率：将函数、定义等尽可能移除循环外
减少过程调用：
消除不必要的存储器引用：
3、低级优化：
展开循环，降低开销
通过使用多个累计变量和重新结合等技术，找到方法提高指令即并行 
用功能的风格重写条件操作，使得编译采用条件数据传送
总之，除了优化自身的代码外，还要优化给编译器造成的困难。

## Chapter Six: 存储器层次结构

随机访问存储器（Random-Access Memory, RAM）
SRAM - 静态RAM
DRAM - 动态RAM
传统的DRAM

通用串行总线（Universal Serial Bus, USB）


## Chapter seven: 链接

加载器将可执行目标文件中的代码和数据从磁盘拷贝到存储器中，然后通过跳转到程序的第一条指令或入口点（entry point）来运行该程序。这个将程序拷贝到存储器并运行的过程叫做加载（loading）。


## Chapter Eight：异常控制流(Exceptional Control Flow, ECF)

<img width="601" alt="image" src="https://github.com/wileyzhao/reading/assets/21215474/c6c28718-3848-4352-b21b-7ac0005b1d2c">

## Chapter Nine： 虚拟存储器

![628174F2-1101-4A29-ADEB-E71164F734AB](https://github.com/wileyzhao/reading/assets/21215474/ee75b20f-9afa-44f1-9313-bad194bb72c2)




由此得知，页表（页表条目（Page Table Entry, PTE）的数组）是存储在缓存/主存中的。

## Chapter Ten: 系统级I/O

![EBD53FB1-E72B-4F0B-ACC8-35D4D3732DD1](https://github.com/wileyzhao/reading/assets/21215474/fbfc1c2f-3fee-4b9f-addb-820296494883)


![ECAB5DC9-A16B-43C9-A650-DC03D9BB6513](https://github.com/wileyzhao/reading/assets/21215474/4c4b56fe-e8ff-4590-a9e9-357f3f48897b)


## Chapter Eleven：网络编程

事务（transaction）

![CA5B68EA-7CC1-4A9E-B94C-A50A78BEACBD](https://github.com/wileyzhao/reading/assets/21215474/2bcd3445-d02d-4dc4-8b34-228bf041b8f4)

![8F7AF27F-3632-4C89-8E86-3A4227936774](https://github.com/wileyzhao/reading/assets/21215474/77785e4f-b1ef-4a2e-9b98-3015ff9d9d79)



