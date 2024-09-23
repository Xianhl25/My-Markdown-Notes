# 硬件

## 电子电路

### SoC架构



### 数字信号与模拟信号

数字信号是指自变量是离散的、因变量也是离散的信号。这种信号的自变量用整数表示，因变量用有限数字中的一个数字来表示。

### 电子器件

#### 电压源

无论带什么样的负载，输出电压保持不变的电路。

一个电路想要输出电压不变，那它必须有强有力的输出电流能力。

电压源最根本的能力是要能提供负载所需的电流，至于输出电压精确稳定，可以依靠别的手段来实现。

当负载改变时，同样的输出结果，对于电源的电动势和内阻如何改变是有很多可能性的。只不过通常情况下，我们假定电动势不变，来计算黑匣子中的等效内阻是多少。电压源的等效内阻并不反映真实电源电动势和导线电阻，而是人们约定的一种电路参数描述方式。

#### 电流源

无论接什么负载，输出电流都是恒定的。

与电压源类似，电流源的内阻其实也是捏造出来。

#### 电阻

电阻的本质是对电流起阻碍作用的元器件。

电阻如果想对流过自身的电流产生影响，实际是通过改变电阻两端的电压来实现的。

电阻的特性方程可以写成$u=i·R$，其含义在于：

1. 电流流过电阻会产生与电源激励电压相反的电压；
2. 随着电流的增大，电阻产生的反向电压与电源电压相等时，电流就不会再增大了，电阻于是就起到了对电流的阻碍作用。

#### 电容

电容的特性方程$i_C = C \frac{du_C}{dt}$，其意义在于：

1. 电容是靠吞吐足够的电流来维持电压稳定的
2. 电压变化率越大，电容的吞吐电流就越大
3. 电容可以在短时间内视为理想电压源

#### 电感

电感是对电流的变化起阻碍作用的元器件

#### 元器件的阻抗

电容、电感在电路中的作用可以看成是容抗和感抗在起作用，它们统称为阻抗。

#### 滤波器原理

正是由于电容和电感的阻抗与频率有关，才使得电路中有了滤波器。

搭配电阻、电容和电感三种元器件，可以实现低通、高通、带通等滤波器。

### 电路

《》

现代信号处理的过程：

1. 将非电信号通过换能器电路转换为连续的电信号
2. 经过模/数转换电路把连续的电信号变成数字电信号
3. 采用数字信号处理电路对数字信号进行处理
4. 处理后的信号再经过数/模转换电路转换成连续的电信号
5. 最后通过换能器把电信号还原成非电信号

#### 电路中的主要物理量

##### 电流

电荷在电场的作用下定向移动而产生电流，电流的

##### 电位

### 总线

🔗：http://t.csdnimg.cn/U2kdm、

总线是连接各个部件的信息传输线，使各个部件共享的传输介质

总线分为内部总线、系统总线和通信总线。

* 内部总线指芯片内部连接各元件的总线
* 系统总线指连接计算机各部件的总线，系统总线又可以分为三类，数据总线、地址总线和控制总线
* 外部总线是计算机系统之间或计算机系统与其他系统之间的通信

### FLASH

🔗：[48. 读写内部FLASH — [野火\]STM32库开发实战指南——基于野火霸道开发板 文档 (embedfire.com)](https://doc.embedfire.com/mcu/stm32/f103badao/std/zh/latest/book/FLASH.html)

在STM32芯片内部有一个FLASH存储器，它主要用于存储代码，我们在电脑上编写好应用程序后，使用下载器把编译后的代码文件烧录到该内部FLASH中，由于FLASH存储器的内容在掉电后不会丢失，芯片重新上电复位后，内核可从内部FLASH中加载代码并运行。

除了使用外部的工具（如下载器）读写内部FLASH外，STM32芯片在运行的时候，也能对自身的内部FLASH进行读写，因此， 若内部FLASH存储了应用程序后还有剩余的空间，我们可以把它像外部SPI-FLASH那样利用起来，存储一些程序运行时产生的需要掉电保存的数据。

SPI-Flash是一种使用SPI（Serial Peripheral Interface）接口的Flash存储器。SPI接口是一种串行接口，它使用较少的引脚，因此SPI-Flash可以有很小的封装尺寸，适合在空间有限的应用中使用。SPI-Flash通常用于存储大量的数据，如图像、音频等。和内部Flash一样，SPI-Flash也具有非易失性。

由于访问内部FLASH的速度要比外部的SPI-FLASH快得多，所以在紧急状态下常常会使用内部FLASH存储关键记录；为了防止应用程序被抄袭， 有的应用会禁止读写内部FLASH中的内容，或者在第一次运行时计算加密信息并记录到某些区域，然后删除自身的部分加密代码，这些应用都涉及到内部FLASH的操作。

### ADC

### DMA

DMA，即直接内存访问，是一种可以让某些硬件子系统在主存和设备之间直接传输数据，而无需CPU的干预的技术。

在传统的CPU存取数据方式中，CPU是数据传输的核心，所有的数据传输都要通过CPU进行。这样会占用大量的CPU时间，使得CPU无法处理其他任务。

传统的CPU存取数据的过程主要包括以下步骤：

1. 地址寄存器加载：CPU首先将需要访问的内存地址加载到地址寄存器中
2. 发送访问信号：CPU通过总线向内存发送访问信号，指示内存准备进行数据传输
3. 数据传输：根据CPU的指示，内存将数据通过总线发送到CPU，或者CPU将数据通过总存发送到内存
4. 数据接收：CPU接收到数据后，将其加载到数据寄存器中，然后进行后续的处理

在整个过程中，CPU需要负责所有的数据传输任务，这意味着在数据传输过程中，CPU不能进行其他的任务，大大降低了系统的工作效率

使用DMA的主要场景是需要处理大量数据，或者当数据传输对时间敏感时。

### PWM

### 定时器中断



### 寄存器

链接：[寄存器 - 维基百科，自由的百科全书 (wikipedia.org)](https://zh.wikipedia.org/wiki/寄存器)

寄存器（Register）是中央处理器内用来暂存指令、数据和地址的电脑存储其。寄存器的存贮容量有限，读写速度非常快。

寄存器位于存储器层次结构的最顶端，也是CPU可以读写的最快的存储器。寄存器通常都是以他们可以保存的比特数量来计量，举例来说，一个8位寄存器或32位寄存器。在中央处理器中，包含寄存器的部件有指令寄存器（IR）、程序计数器和累加器。

### GPIO

链接：http://t.csdnimg.cn/v3GU3

General Purpose Input Output（通用输入输出），简称IO口，也叫总线扩展器。GPIO口是由引脚、功能寄存器组成。不同的架构中的GPIO封装不同，所使用的引脚数与寄存器数不同。

GPIO的作用是用来控制连接在此GPIO口上的外设。在驱动层我们通过读写GPIO口中的功能寄存器来改变连接在此GPIO上的外设状态。

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240304103132972.png" alt="image-20240304103132972" style="zoom: 50%;" />

* 推挽输出：连接在输出控制电路里的数字器件，可以输出高电平与低电平。
* 开漏输出：只能输出低电平。开漏负载能力较强，因为有上拉电阻，所以一般长时间的设备会用开漏输出。
* 推挽式复用功能：可输出高低电平，驱动能力强。由其他外设控制输出。
* 开漏式复用功能：不能输出高电平，必须有外部（或内部）上拉才能输出高电平。由其他外设控制输出。

F4/F7/H7系列和F1系列的GPIO差异点

* F1在输出模式，禁止使用内部上下拉；F4/F7/H7在输出模式，可以使用内部上下拉
* 不同系列IO翻转速度可能不同

### 物理层

链接：[计算机网络笔记(四)——物理层 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/52248268)

物理层是指通过传输介质，以及相关的通信协议、标准建立起来的物理线路

### 差分信号

### 速度刚度

也称为动态刚度，是指系统对速度变化的响应。它描述了系统在受到外部力作用时，速度如何改变。速度刚度通常与阻尼有关，影响系统的振动特性。

### 位置刚度

也称为静态刚度，是指系统对位移变化的响应。它描述了系统在受到外部力作用时，位移如何改变。位置刚度通常与弹性有关，影响系统的静态行为。

### 回调函数

### 调试接口

链接：http://t.csdnimg.cn/pxfQA

JTAG和SWD是两种常用的调试接口，均可用于程序的下载和调试

ST-Link是用于STM8和STM32微控制器在线调试器和编程器，本身具有SWIM、JTAG/SWD通信接口。

* SWIM：Single Wire Interface Module，单线接口模块
* JTAG：Joint Test Action Group，联合测试工作组规定的一种仿真协议，是一种国际标准测试协议
* SWD：Serial Wire Debugging，串行调试接口

因为SWD占用的引脚数相比JTAG较少，所以一般情况下项目大部分都是采用SWD作为仿真测试接口。

### 通信协议

#### USART

#### I2C

#### RS232 串口

#### SPI

#### CAN



## STM32入门教程



### Keil工程结构

* 基于寄存器
* 基于标准库/库函数
* 基于HAL库

搭建基于标准库/库函数的工程模板：

* STM32的启动文件——Start文件夹包含以下文件

  1. stm32f10x.h——STM32的外设寄存器描述文件，用于描述STM32有哪些寄存器和它对应的地址

  2. system文件——用于配置时钟

![image-20240228102615948](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240228102615948.png)

![image-20240228102730863](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240228102730863.png)

* 内核寄存器的描述文件：包含内核的寄存器描述以及内核的配置函数

把文件复制到文件夹后，还需要将文件添加到工程中。

* 首先添加启动文件。这个启动文件有很多分类，我们只能添加其中一个，需要根据芯片型号来选择。视频中选择后缀为md.s的启动文件。
* 剩下的c和h文件都要添加进来。
* 最后需要在工程选项里添加这个文件夹的头文件路径：魔术棒按钮——工程选项——C/C++——Include Paths——把start文件夹的路径添加进来。

这些文件都是可读的文件，不能够进行修改。

新建User文件夹，放置main函数

新建Library文件夹，用于存放库函数

![image-20240228105551684](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240228105551684.png)

在固件库的src文件夹下是库函数的文件：misc是内核的库函数，其他的是内核外的外设库函数。

在inc文件夹下是库函数的头文件

![image-20240228105945621](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240228105945621.png)

conf文件是用来配置库函数头文件的包含关系的，两个it文件是用来存放中断函数的。将这三个文件复制到User文件夹下。

添加宏定义：魔术棒（工程选项）——C/C++——Define，添加宏定义：USE_STDPERIPH_DRIVER，这样才能包含标准外设库，也就是库函数。

当然还需要添加上User和Library文件夹的路径。

这样，基于库函数的工程就建好了。

### 直接控制寄存器点亮小灯

* 使能GPIOC的时钟

```c
RCC->APB2ENR = 0x00000010;
```

* 配置GPIOC端口

```c
GPIOC->CRH = 0x00300000;
```

* 

### 使用库函数点亮小灯

库函数其实也是间接地配置寄存器，所以步骤和直接使用寄存器是一样的。

* 使能时钟，配置GPIOC的外设时钟

```C
RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOC, ENABLE);
```

* 配置端口模式，首先定义初始化结构体

```C
GPIO_InitTypeDef GPIO_InitStructure;
GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
GPIO_InitStructure.GPIO_Pin = GPIO_Pin_13;
GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
```

```c
GPIO_Init(GPIOC, &GPIO_InitStructure);
```



* 设置电平

```c
GPIO_SetBits(GPIOC, GPIO_Pin_13); // 设置为高电平
```

```C
GPIO_ResetBits(GPIOC, GPIO_Pin_13); // 设置为低电平
```

### 报错

error: #268: declaration may not appear after executable statement in block

需要将变量定义在main函数的开头，即所有函数的前面，否则会报错。不然就在工程选项——C/C++中勾选C99。

*** Target ‘xxx‘ uses ARM-Compiler ‘Default Compiler Version 5‘ which is not available.

这个原因是Compiler Version 5编译器在Keil 5.37以后就不再默认安装了。从这个版本开始，Keil默认安装的是Compiler Version 6.18。

## HAL库开发

### C语言基础知识复习

#### stdint.h

#### 如何给寄存器某个位赋值

#### 宏定义

#### 条件编译

#### extern声明

#### typedef

#### 结构体

#### 指针

指针就是内存的地址

指针变量是保存了指针的变量

指针使用的2大最常见问题：

1. 未分配（申请）内存就用
2. 越界使用

#### 代码规范

1. 所有函数/变量名字非特殊情况，一般使用小写字母
2. 注释风格使用doxgen风格，除屏蔽外，一律使用/**/方式进行注释
3. TAB键统一使用4个空格对其，不使用默认的方式进行对齐
4. 每两个函数之间，一般有且只有一个空行
5. 相对独立的程序块之间，使用一个空行隔开
6. 全局变量命名一般使用g_开头，全局指针命名一般使用p_开头
7. if for while do case switch default等语句单独占一行，一般无论有多少行执行语句，都要加花括号

### STM32系统框架

#### Cortex M内核&芯片

![image-20240228191626488](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240228191626488.png)

#### F1系统架构

#### F4系统架构

#### F7系统架构

#### H7系统架构

### HAL库开发

#### 初识HAL库

CMSIS

HAL库简介

#### STM32Cube固件包浅析

STM32Cube固件包文件夹简介

Drivers——驱动源码，Middlewares——中间文件，Projects——ST官方开发板例程

Drivers文件夹：

* BSP——板级支持包，用于适配ST官方的开发板
* CMSIS——符合CMSIS的组件，包括：DSP库、Cortex-M内核及其设备文件、微控制器专用头文件、启动文件、专用系统文件等
* STM32F1xx_HAL_Driver——HAL库外设驱动源码，包括F1系列HAL库源文件和头文件

CMSIS文件夹：

Device文件夹——微控制器专用头文件、启动文件、专用系统文件

Include文件夹——Cortex-M内核及其设备文件、编译器相关头文件

Device和Include文件夹的关键文件介绍

* stm32f1xx.h
* stm32f103xx.h
* system_stm32f1xx.c/.h
* startup_stm32f103xe.s

上面这些文件是针对所使用的开发板而言的。

#### HAL库框架结构

HAL库文件夹结构

STM32F1xx_HAL_Driver：

* Inc、Src是HAL库和LL库驱动源码，Inc是外设驱动源码头文件，Src是外设驱动源码。

HAL库文件介绍

HAL库API函数和变量命名规则

#### 如何使用HAL库

基于CMSIS应用程序文件描述

CMSIS核心层、设备驱动层（HAL库源码）、用户程序文件

STM32开发文件结构分布

![image-20240229110305591](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240229110305591.png)

用户想要开发MCU上的硬件，必须经过CMSIS层，其中CMSIS层包含了设备驱动层和CMSIS核心层。

**HAL库的用户配置文件（stm32f1xx_hal_conf.h）**

* 裁剪HAL库外设驱动源码
* 设置外部高速晶振频率（HSE_VALUE）
* 设置外部低速晶振频率（LSE_VALUE）

设备驱动层包含初始化HAL、滴答时钟等，外设API驱动程序、扩展外设API驱动程序、部分HAL驱动调用的LL库驱动。**一般来说，要用哪个外设，才把这个外设对应的驱动程序添加到工程当中。**如果把所有的驱动程序都添加到工程当中就会减慢编译的速度。实际上类似于使用用户配置文件进行裁剪。

**stm32f1xx_hal.c文件**

这个文件内容较多，包括HAL库的初始化、系统滴答、基准电压配置、IO补偿、低功耗、EXTI配置等都集合在这个文件里面。具体可以查看STM32F103开发指南。

HAL_init函数：

* 使能FLASH预取缓存
* 配置中断优先级分组
* 使用滴答定时器作为时钟基准，配置1ms滴答（官方的配置是在HAL_init函数里面，但是正点原子的配置是在delay.c文件里面）
* 初始化其它底层硬件
* 返回函数状态

#### 新建HAL库版本MDK工程

**新建工程前的准备工作**

* 下载相关STM32Cube官方固件包
* 搭建开发环境

**新建HAL库版本MDK工程步骤**

1. 新建工程文件夹

   * Drivers：存放于硬件相关的驱动层文件
   * Middlewares：存放正点原子提供的中间层组件文件和第三方中间层文件
   * Output：存放工程编译输出文件
   * Projects：存放MDK工程文件
   * Users：存放HAL库用户配置文件、main.c、中断处理文件以及分散加载文件

   拷贝/新建工程相关文件

2. 新建一个工程框架
   * 新建工程
   * 保存工程
   * 选择主控型号
   * 删除文件夹，新建工程后，删除MDK-ARM文件夹下的Listings和Objects文件夹

3. 添加文件
   * 设置工程名和分组名
   * 添加启动文件
   * 添加User源码
   * 添加SYSTEM源码
   * 添加STM32F1xx_HAL_Driver源码

4. 魔术棒设置

   			* target选项卡
		
   			* Output选项卡：设置Objects输出文件夹、生成hex文件、输出浏览信息
   			* Listing选项卡
   			* C/C++选项卡

   ![image-20240229145621162](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240229145621162.png)

      * Debug选项卡
      * Utilities选项卡
      * Linker选项卡

1. 添加main.c，并编写代码

**下载验证**

### STM32CubeMX

#### 新建STM32CubeMX工程步骤

1. 工程初步建立：选择芯片型号
2. 时钟模块配置：设置HSE、LSE、MCO

System Core——RCC——HSE、LSE

选择Crystal/Ceramic Resonator表示外部晶振作为它们的时钟源

3. 时钟系统配置：PLL、SYSCLK、AHB、APB1、APB2

进入Clock Configuration配置栏后会展现一个完整的STM32F1时钟系统框图。从这个时钟树配置图。配置的主要是外部晶振大小、分频系数、倍频系数以及选择器。

AHB、APB1、APB2总线时钟以及Systick时钟来源于系统时钟SYSCLK。

![image-20240229163755845](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240229163755845.png)

AHB总线时钟HCLK由SYSCLK经过AHB预分频器之后得到

得到HCLK后，按照同样方法依次配置Systick、APB1和APB分频系数分别为1、2和1

4. GPIO引脚配置

Pinout&Configuration，在搜索栏输入PB5后回车，可以在引脚图中显示位置，点击PB5，在弹出的下拉菜单中，选择IO口的功能为GPIO_Output。

配置完IO口功能之后，还要配置IO口的速度，上下拉等参数。这些参数我们通过System Core下的GPIO选项进行配置。

![image-20240229172935371](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240229172935371.png)

5. Cortex内核配置：SYS配置、NVIC（优先级分组）

6. 生成工程源码

7. 编写用户程序

STM32CubeMX生成的main.c文件中，有很多地方有`/* USER CODE BEGIN X */ `和 `/*USER CODE END X */`格式的注释，我们在这些注释之间编写代码，那么重新生成工程后，这些代码会保留而不会被覆盖。

### 时钟树

链接：系统时钟RCC详解http://t.csdnimg.cn/2Bl56

任意复杂的电路控制系统都可以经由门电路组成的组合电路实现。

由于时序电路的重要性，因此在MCU设计时就设计了专门用于控制时序的电路，在芯片设计中称为时钟树设计。

对于STM32F1系列的芯片，正常工作的主频可以达到72MHz，但并不是所有外设都需要系统时钟这么高的频率。同一个电路，时钟越快功耗越大，同时抗电磁干扰能力也会越弱，所以对于较为复杂的MCU一般都是采取多时钟源的方法来解决这些问题。

#### 认识时钟树

**时钟**

简单来说，时钟是具有周期性的脉冲信号，最常用的是占空比50%的方波。

下面针对一个简化的STM32F1时钟系统

**STM32F1时钟系统**

* 其他电路需要的输入源时钟信号；
* 特殊的振荡电路PLL，由几个部分构成；
* 系统时钟SYSCLK；
* AHB预分频器将SYSCLK分频或不分频后分发给其他外设进行处理；
* Cortex-M内核系统的时钟；
* 外设的时钟源APB1/APB2；
* STM32的时钟输出功能。

**时钟源**

对于STM32F1，输入时钟源主要包括HSI，HSE，LSI，LSE。其中，从**时钟频率**来分可以分为高速时钟源和低速时钟源，其中HSI、HSE高速时钟，LSI和LSE是低速时钟。从**来源**可分为外部时钟源和内部时钟源，外部时钟源就是从外部通过接晶振的方式获取时钟源，其中HSE和LSE是外部时钟源；其他是内部时钟源，芯片上电即可产生，不需要借助外部电路。

* 高速外部振荡器HSE(High Speed External Clock signal)
* 低速外部振荡器LSE(Low Speed External Clock signal)
* 高速内部振荡器HSI(High Speed Internal Clock signal)
* 低速内部振荡器LSI(Low Speed Internal Clock signal)

**系统时钟SYSCLK**

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240302223706522.png" alt="image-20240302223706522" style="zoom:50%;" />

系统时钟为整个芯片提供了时序信号。对于相同的稳定运行的电路，时钟频率越高，指令的执行速度越快，单位时间能处理的功能越多。

STM32的系统时钟是可配置的，**在STM32F1中，可以为内部高速时钟HSI、经过倍频的PLLCLK、外部高速时钟HSE中的一个**。

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240302223751105.png" alt="image-20240302223751105" style="zoom:50%;" />

AHB、APB1、APB2、内核时钟等时钟**通过系统时钟分频得到**。

**如何修改主频**

STM32F103默认的情况下使用是内部8M的HSI作为时钟源，所以不需要外部晶振也能够下载和运行代码。

72MHz是官方推荐使用的最高的稳定时钟频率

#### 配置系统时钟

系统时钟配置步骤

外设时钟使能和失能

```

```

sys_stm32_clock_init函数

### SYSTEM文件夹介绍

SYSTEM文件夹里面的代码由正点原子提供，是STM32F1xx系列的底层核心驱动函数。

SYSTEM文件夹下包含了delay、sys、usart等三个文件夹。分别包含了delay.c、sys.c、usart.c及其头文件。

这3个c文件提供了系统时钟设置、延时和串口1调试功能。

#### SysTick工作原理

SysTick，即系统滴答定时器，包含在Cortex内核里面，核心是一个24位置的递减计数器。

#### delay文件夹代码介绍

#### sys文件夹代码介绍

#### usart文件夹代码介绍

printf函数输出流程

1. 用户调用printf函数
2. printf函数由编译器提供的stdio.h解析
3. fputc最终实现输出——用户需要根据最终输出的硬件重新定义该函数，此过程称为：printf重定向

半主机模式

用于ARM目标的一种机制，可将来自应用程序代码的输入/输出请求传送至运行调试器的主机

简单说：就是通过仿真器实现开发板在电脑上的输入和输出

一般不使用半主机模式

### GPIO

STM32引脚类型

* 电源引脚
* 晶振引脚
* 复位引脚

* 下载引脚
* BOOT引脚
* GPIO引脚

#### GPIO基本结构

![img](https://pic4.zhimg.com/v2-81737c371e49ec78739ef5cb3014ea33_r.jpg)

* 保护二极管：用于防止引脚外部过高、过低的电压输入。
* 内部上下拉电阻
* P-MOS和N-MOS管：使GPIO具有推挽输出和开漏输出的模式。

MOS管是压控型元件，通过控制栅源电压来实现导通或关闭。

![image-20240304191959814](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240304191959814.png)

* 施密特触发器/TTL肖特基触发器：信号经过触发器后，模拟信号转化为0和1的数字信号。但是，当GPIO引脚作为ADC采集电压的输入通道时，用其模拟输入功能，此时信号不再经过触发器进行TTL电平转换。

施密特触发器就是一种整型电路，可以将非标准方波，整形成方波。

特点：

* 当输入电压高于正向阈值电压，输出为高
* 当输入电压低于负向阈值电压，输出为低
* 当输入在正负向阈值电压之间，输出不改变

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240304191711963.png" alt="image-20240304191711963" style="zoom: 67%;" />

#### GPIO八种工作模式分析

![image-20240304192116983](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240304192116983.png)

* 推挽输出：连接在输出控制电路里的数字器件，可以输出高电平与低电平。
* 开漏输出：只能输出低电平或者是高阻态。开漏负载能力较强，因为有上拉电阻，所以一般长时间的设备会用开漏输出。
* 推挽式复用功能：可输出高低电平，驱动能力强。由其他外设控制输出。
* 开漏式复用功能：不能输出高电平，必须有外部（或内部）上拉才能输出高电平。由其他外设控制输出。

F4/F7/H7系列和F1系列的GPIO差异点

* F1在输出模式，禁止使用内部上下拉；F4/F7/H7在输出模式，可以使用内部上下拉
* 不同系列IO翻转速度可能不同

#### GPIO配置步骤

**通用外设驱动模型**

1. 初始化：时钟设置、参数设置、IO设置、中断设置
2. 读函数：从外设读取数据
3. 写函数：往外设写入数据
4. 中断服务函数：根据中断标志，处理外设各种中断事务

**GPIO配置步骤**

1. 使能时钟：__HAL_RCC_GPIOx_CLK_ENABLE()
2. 设置工作模式：HAL_GPIO_Init()
3. 设置输出状态：HAL_GPIO_WritePin() HAL_GPIO_TogglePin()
4. 读取输入状态：HAL_GPIO_ReadPin()

### 中断

打断CPU执行正常的程序，转而处理紧急程序，然后返回原暂停的程序继续运行，就叫中断。

中断的作用和意义

* 实时控制：在确定时间内对相应事件作出响应，如温度监控
* 故障处理：检测到故障，需要第一时间处理，如电梯门夹人了
* 数据传输：不确定数据何时会来，如串口数据接收

中断的意义：高效处理紧急程序，不会一直占用CPU资源

STM32 GPIO外部中断简图

![image-20240304202201150](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240304202201150.png)

#### NVIC

**NVIC基本概念**

**中断向量表**

定义一块固定的内存，以4字节对齐，存放各个**中断服务函数**程序的首地址。

中断向量表定义在启动文件，当发生中断，CPU会根据中断类型（外部中断、定时器中断、串口中断等）自动执行对应的中断服务函数

**NVIC相关寄存器介绍**

* 中断使能寄存器
* 中断除能寄存器
* 应用程序中断及复位控制寄存器
* 中断优先级寄存器

**NVIC工作原理**

**STM32中断优先级基本概念**

* 抢占优先级：高抢占优先级可以打断正在执行的低抢占优先级中断
* 响应优先级：当抢占优先级相同时，响应优先级高的先执行，但是不能互相打断
* 自然优先级：中断向量表的优先级
* 抢占和响应优先级都相同的情况下，自然优先级越高的先执行
* 数值越小，表示优先级越高

**STM32中断优先级分组**

一个工程中，一般只设置一次中断优先级分组

**STM32 NVIC的使用**

* 设置中断分组：HAL_NVIC_SetPriorityGrouping
* 设置中断优先级：HAL_NVIC_SetPriority
* 使能中断：HAL_NVIC_EnableIRQ

如果设置中断分组为2的话，那么抢占优先级有4位，响应优先级也有4位。

#### EXTI

EXTI基本概念

External(Extended) interrupt/event Controller，外部（扩展）中断事件控制器

包含20个产生事件/中断请求的边沿检测器，即总共20条EXTI线

**中断和事件的理解**：

* 中断：要进入NVIC，有相应的中断服务函数，需要CPU处理
* 事件：不进入NVIC，仅用于内部硬件自动控制，如TIM、DMA、ADC

**EXTI主要特性**

每条EXTI线都可以单独配置：选择类型（中断或者事件）、触发方式（上升沿、下降沿或者双边沿触发）、支持软件触发、开启/屏蔽、有挂起状态位

**EXTI工作原理**

![image-20240305205016748](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240305205016748.png)

①边沿检测

②软件触发

③中断屏蔽/清除

④事件屏蔽

了解寄存器：

* EXTI_FTSR：上升沿触发选择寄存器
* EXTI_RTSR：下降沿触发选择寄存器
* EXTI_IMR：中断屏蔽寄存器
* EXTI_PR：挂起寄存器

#### EXTI和IO映射关系

EXTI与GPIO的引脚号对应，比如说EXTI0，就对应GPIOA0、GPIOB0等

如果说PA0与EXTI0的对应关系已经确定了，那么其他分组的引脚就不能与之相对应了

#### 如何使用中断

![image-20240305210447896](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240305210447896.png)

**GPIO外部中断配置步骤**

1. 使能GPIO时钟
2. 设置GPIO输入模式：上/下拉/浮空输入
3. 使能AFIO/SYSCFG时钟
4. 设置EXTI和IO对应关系
5. 设置EXTI屏蔽，上下沿
6. 设置NVIC：分3步，设置优先级分组、设置优先级、使能中断
7. 设计中断服务函数：编写对应中断的中断服务函数！清除中断标志

其中，步骤2-5可以使用HAL_GPIO_Init一步完成

使用HAL库设置步骤

1. 使能GPIO时钟
2. GPIO/AFIO/SYSCFG

STM32仅有：EXTI0~4、EXTI9_5和EXTI5_10，7个外部中断服务函数

#### 通用外设驱动模型

#### HAL库中断回调处理机制介绍

1. 使能GPIO时钟
2. GPIO/AFIO

### 数据通信

#### 数据通信的基础概念

按数据**通信方式**分类：串行/并行通信

* 串行通信：数据逐位按顺序依次传输
* 并行通信：数据各位通过多条线同时传输

按数据**传输方向**分类：单工/半双工/全双工通信

* 单工通信：数据只能沿一个方向传输
* 半双工通信：数据可以沿两个方向传输，但需要分时进行
* 全双工通信：数据可以同时进行双向传输

按数据**同步方式**分类：同步/异步通信

* 同步通信：共用同一时钟信号
* 异步通信：没有时钟信号，通过在数据信号中加入起始位或停止位等一些同步信号

波特率

常见的串行通信接口

* UART
* 1-wire
* IIC
* SPI

#### 串口（RS-232）

什么是串口：串行通信接口：指按位发送和接收的接口，如RS-232/422/485等

RS-232电平与COMS/TTL电平对比

* RS-232电平：逻辑1：-15V~3V，逻辑0：3V~15V
* COMS电平
* TTL电平

结论：**COMS/TTL电平不能与RS-232电平直接交换信息**

设备间的RS-232通信示意图

STM32串口与电脑USB口通信示意图：使用CH340C等USB/串口转换芯片

RS-232异步通信协议：

* 启动位：必须占1个位长，保持逻辑0电平
* 有效数据位：可选5、6、7、8、9个位长
* 校验位：可选占1个位长，也可以没有该位
* 停止位：必须有，可选0.5、1、1.5、2个位长，保持逻辑1电平

#### STM32的USART

**STM32的USART主要特征**

* 全双工异步通信
* 单线半双工通信
* 单独的发送器和接收器使能位
* 可配置使用DMA的多缓冲器通信
* 多个带标志的中断源

STM32F1/F4/F7的USART框图

![image-20240306214233688](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240306214233688.png)

设置USART/UART波特率（F1）
$$
baud = \frac{f_{ck}}{16*USARTDIV}
$$
其中$f_{ck}$是串口的时钟，如：USART1的时钟是PCLK2，其他串口都是PCLK1

设置USART/UART波特率（F4/F7）

#### USART寄存器介绍

* 控制寄存器1（CR1）
* 控制寄存器2（CR2）
* 控制寄存器3（CR3）
* 数据寄存器（DR）：设置好控制和波特率寄存器后，往该寄存器写入数值
* 状态寄存器（SR）：根据TC位可以知道能否发数据

#### HAL库外设初始化MSP回调机制

#### HAL库中断回调机制

#### USART/UART异步通信配置步骤

1. 配置串口工作参数：HAL_UART_Init()

2. 串口底层初始化：HAL_UART_MspInit()，配置GPIO NVIC CLOCK等

3. 开启串口异步接收中断：HAL_UART_Receive_IT()

```C
HAL_UART_Receive_IT(&huart7, (uint8_t *)&aRxBuffer, 1); // 调用一次中断函数
```

```C
uint8_t aRxBuffer;
```

aRxBuffer需要自行定义，为一次所接收的字符数。这个接收中断可以放在HAL_UART_Init函数中，也可以放在main函数中。

4. 设置优先级，使能中断：HAL_NVIC_SetPriority() HAL_NVIC_EnableIRQ()
5. 编写中断服务函数：USARTx_IRQHandler()、 UARTx_IRQHandler()
6. 串口数据发送：USART_DR， HAL_UART_Transmit()

HAL库相关函数介绍

```C
HAL_StatusTypeDef HAL_UART_Init(UART_HandleTypeDef *huart)
```

```C
HAL_StatusTypeDef HAL_UART_Receive_IT(UART_HandleTypeDef *huart, uint8_t *pData, uint16_t Size)
```

以中断的方式接收指定字节的数据

```
HAL_StatusTypeDef HAL_UART_Transmit(UART_HandleTypeDef *huart, uint8_t *pData, uint16_t Size, uint32_t Timeout)
```

以阻塞的方式发送指定字节的数据

#### IO引脚复用功能

#### 通过串口接收或者发送一个字符

相关定义：

```C
uint8_t g_rx_buffer[1];          /* HAL库使用的串口接收数据缓冲区 */
uint8_t g_usart1_rx_flag = 0;    /* 串口接收到数据标志 */

UART_HandleTypeDef g_uart1_handle;  /* UART句柄 */
```

1. 配置串口工作参数

```c
/* 串口1初始化函数 */
void usart_init(uint32_t baudrate)
{
    g_uart1_handle.Instance = USART1;
    g_uart1_handle.Init.BaudRate = baudrate;
    g_uart1_handle.Init.WordLength = UART_WORDLENGTH_8B;
    g_uart1_handle.Init.StopBits = UART_STOPBITS_1;
    g_uart1_handle.Init.Parity = UART_PARITY_NONE;
    g_uart1_handle.Init.HwFlowCtl = UART_HWCONTROL_NONE;
    g_uart1_handle.Init.Mode = UART_MODE_TX_RX;
    HAL_UART_Init(&g_uart1_handle);
    
    HAL_UART_Receive_IT(&g_uart1_handle, (uint8_t*)g_rx_buffer, 1);
}
```

2. 串口底层初始化

```c
void HAL_UART_MspInit(UART_HandleTypeDef *huart)
{
    GPIO_InitTypeDef gpio_init_struct;
    if(huart->Instance == USART1)                /* 如果是串口1，进行串口1 MSP初始化 */
    {
        __HAL_RCC_USART1_CLK_ENABLE();
        __HAL_RCC_GPIOA_CLK_ENABLE();

        gpio_init_struct.Pin = GPIO_PIN_9;
        gpio_init_struct.Mode = GPIO_MODE_AF_PP;            /* 推挽式复用输出 */
        gpio_init_struct.Speed = GPIO_SPEED_FREQ_HIGH;      /* 高速 */
        HAL_GPIO_Init(GPIOA, &gpio_init_struct);            /* 初始化串口1的TX引脚 */
        
        gpio_init_struct.Pin = GPIO_PIN_10;
        gpio_init_struct.Mode = GPIO_MODE_AF_INPUT;         /* 输入 */
        gpio_init_struct.Pull = GPIO_PULLUP;                /* 上拉 */
        HAL_GPIO_Init(GPIOA, &gpio_init_struct);            /* 初始化串口1的RX引脚 */
        
        HAL_NVIC_SetPriority(USART1_IRQn, 3, 3);
        HAL_NVIC_EnableIRQ(USART1_IRQn);
    }
}
```

3. 开启串口异步接收中断

```c
void USART1_IRQHandler(void)
{
    HAL_UART_IRQHandler(&g_uart1_handle);
    HAL_UART_Receive_IT(&g_uart1_handle, (uint8_t*)g_rx_buffer, 1);
}
```

HAL_UART_IRQHandler函数能够清除中断标志位，并且调用接收中断回调函数

4. 设置优先级，使能中断

```c
        HAL_NVIC_SetPriority(USART1_IRQn, 3, 3);
        HAL_NVIC_EnableIRQ(USART1_IRQn);
```

在串口底层初始化一步中已经配置完成。

5. 编写中断服务函数

```c
/* 串口数据接收完成回调函数 */
void HAL_UART_RxCpltCallback(UART_HandleTypeDef *huart)
{
    if(huart->Instance == USART1)
    {
        g_usart1_rx_flag = 1;
    }
}
```

6. 串口数据发送

```c
HAL_UART_Transmit(&g_uart1_handle, (uint8_t*)g_rx_buffer, 1, 1000);
```

在主函数中实现串口数据发送。

#### 串口实验

### 定时器

链接：http://t.csdnimg.cn/0GJ8O

#### 定时器概述

软件定时原理

使用纯软件（CPU死等）的方式实现定时（延时）功能

定时器定时原理

STM32定时器分类

STM32定时器特性表

STM32定时器常用功能

* 定时中断功能
* 内外时钟源选择
* 输入捕获
* 输出比较
* 编码器接口
* 主从触发模式

STM32基本、通用、高级定时器功能整体的区别

#### 定时器类型

##### 基本定时器

**基本定时器简介**

**基本定时器框图**

<img src="https://img-blog.csdnimg.cn/e0ffcf4d31194f638bac133ccf540bae.png#pic_ceter" alt="在这里插入图片描述" style="zoom:67%;" />

基本定时器拥有由**预分频器PSC**、**计数器CNT**、**自动重装寄存器ARR**组成的基本时基单元。

预分频器之前连接的是**基准时钟**的输入。由于基本定时器只能连接内部时钟，故可以直接认为预分频器的时钟输入CK_PSC就是连接到内部时钟CK_INT上的。内部时钟的来源是RCC_TIMxCLK，这里的频率一般都是系统的主频72MHz。所以基本定时器的基准时钟输入只能是72MHz。

**预分频器PSC**可以对基准时钟进行预分频。如果预分频器写0，就是不分频，或者说是1分频；如果预分频器写1，就是2分频。预分频器是16位的寄存器，故最大值可以写入65535，也就是65536分频。

**计数器CNT**可以对预分频后的计数时钟CK_CNT进行计数。计数时钟CN_CNT每来一个上升沿，计数器的值就加1。计数器也是16位的，它的值可以是0~65535。如果再加1，计数器就会回到0重新开始计数。

自动重装载寄存器ARR存入计数器的计数目标。计数器不断与重装载寄存器进行比较，当计数值等于自动重装载值时，就说明计时时间到，这时自动重装载寄存器就会输出一个中断信号，并且清零计数器，计数器自动开始下一次的计数计时。

图中折线向上的箭头，就代表产生的一个中断信号。UI意为Update Interrupt，即**更新中断**，它是计数值等于自动重装值得中断。更新中断会通往NVIC，只要配置昊NVIC得中断通道，那么定时器的更新中断就能得到CPU的响应。在图中折线向下的箭头，就代表产生的一个事件。这里的U意为Update，即**更新事件**。更新事件不会触发中断，但可触发其他内部电路的工作。

```
主从触发模式
  STM32的一大特色就是主从触发模式。它能让内部的硬件在不受程序的控制下实现自动运行，即实现硬件自动化。
  这里我的理解是：主模式，即作为信号的主人的模式，电路输出的信号能触发其他处于从模式的电路的响应。 正常来讲，在一个时刻只能执行一段代码，完成一个操作，如果能合理使用主从触发，就可以实现”一心二用“，将会极大地减少CPU运行负担（这里仅做简单了解即可，后续还会讲到）。
  以基本定时器主模式触发DAC为例：在我们使用DAC的时候，可能会用DAC输出一段波形，那就需要每隔一段时间来触发一次DAC，让它输出下一个电压点。如果按中断的思路，需要先设置一个定时器产生中断，每隔一段时间在中断程序中用代码手动触发一次DAC转换，然后DAC输出波形。这样操作没有错，但是这样会使主程序频繁处于被中断的状态，有可能会影响主程序的运行和其他中断的响应。所以定时器的主模式可以把定时器的更新事件U映射到触发输出TRGO（Trigger Out）的位置，再通过TRGO直接连接到DAC的触发转换引脚上。这样DAC转换就不需要定时器产生的中断来触发了，仅需要把更新事件U通过主模式映射到TRGO，TRGO自动触发DAC就可以实现。这里体现了主模式的作用：整个过程不需要软件的参与，实现了硬件的自动化。
```

##### 通用定时器

通用定时器拥有基本定时器的全部功能，并额外具有内外时钟源选择、输入捕获、输出比较、编码器接口、主从触发模式等功能。

主要特性：

* 16位递增、递减、中心对齐计数器
* 16位预分频器
* 可用于触发DAC、ADC
* 在更新事件、触发事件、输入捕获、输出比较时，会产生中断
* 4个**独立通道**，可用于：输入捕获、输出比较、输出PWM、单脉冲模式（通用定时器具有4个独立通道，这意味着它可以独立地控制和管理四个不同的计时任务。可以将这些通道理解为同一设备的四个不同部分，每个部分都可以单独设置并以自己的速率运行，互不干扰。）
* 使用外部信号控制定时器且可实现多个定时器互连的同步电路

**通用定时器框图**

<img src="https://img-blog.csdnimg.cn/a9161207b6ab4e23b652d6d5884d0fac.png#pic_ceter" alt="在这里插入图片描述" style="zoom: 80%;" />

通用定时器最基本的结构也是时基单元，与基本定时器相同。可以认为通用定时器就是在基本定时器的基础上扩展了许多功能得到的。它再时基单元模块与基本定时器的区别是：计数器的计数模式不止向上计数一种。除了与基本定时器相同的向上计数的模式外，它还拥有以下两种模式：

* 向下计数模式
* 中央对齐模式

结构图的上部分，为内外时钟源选择和主从触发模式的工作结构。

<img src="https://img-blog.csdnimg.cn/ac19b2017c2a42bdad2eaa283a2e8407.png#pic_center" alt="在这里插入图片描述" style="zoom:80%;" />

首先来看内外时钟源选择的工作原理。基本定时器只能选择来自芯片内部的内部时钟CK_INT，也就是系统频率72MHz。而通用定时器不仅可以选择内部时钟，还可以选择外部时钟。具体有以下三种：

* 来自TIMx_ETR引脚上的外部时钟ETR
* 来自其他定时器的信号ITR
* 来自TIMx_CH1的TI1_ED
* 来自TIMx_CH1的TI1FP1和来自TIMx_CH2的TI2FP2

计数器时钟源

* 内部时钟（CK_INT），来自外设总线APB提供的时钟——设置TIMx_SMCR的SMS=000
* 外部时钟模式1：外部输入引脚（TIx），来自定时器通道1或者通道2引脚的信号，设置TIMx_SMCR的SMS=111
* 外部时钟模式2：外部触发输入（ETR），来自可以复用为TIMx_ETR的IO引脚，设置TIMx_SMCR的ECE=1
* 内部触发输入（ITRx），用于与芯片内部其他通用/高级定时器级联

通用定时器结构图的右下角即为定时器的输出比较功能的结构。有四个输出通道，分别对应CH1到CH4的引脚，可以用来输出PWM波形，驱动电机。

<img src="https://img-blog.csdnimg.cn/839f02a9cc11498094b1be3746db8931.png#pic_center" alt="在这里插入图片描述" style="zoom:80%;" />



##### 高级定时器

高级定时器拥有通用定时器全部功能，并额外具有重复计数器、死区生成、互补输出、刹车输入等功能。

![在这里插入图片描述](https://img-blog.csdnimg.cn/b3d933fd290f43c48bd661216e953ecb.png#pic_center)

#### 定时中断及内外时钟源选择

![定时中断的基本结构](https://img-blog.csdnimg.cn/6e480b8daefc4b73b51fe4bf5edd12d4.png#pic_center)

在定时器中最核心的部分是时基单元。图中的运行控制就是控制寄存器的一些位，用来启动或停止计数器，配置向上向下计数方式等，操作这些寄存器就能控制时基单元的运行了。

计时时间到后，产生的中断信号会先在状态寄存器中置一个中断标志位，这个标志位会通过中断输出控制，到NVIC申请中断。这个中断输出控制存在的原因是：定时器模块有很多地方都要申请中断，如果需要该中断，就允许输出；如果不需要这个中断，就禁止输出。简单来说，中断输出控制就是中断输出的允许位。

##### 缓冲（影子）寄存器

为了保证能适用于多种多样的情况，故对时序运行过程中突然手动更改寄存器对时序的影响做了严谨的设计。这里引入缓冲（影子）寄存器，主要目的就是同步，即可以让寄存器设定的某些目标值的变化和更新事件同时发生，防止在运行途中更改造成错误。在定时器结构图中，有些寄存器的画法采用了方框下加阴影的方式，就说明该寄存器不是只有一个寄存器，而是有两个寄存器来形成缓冲机制。实际上，**真正使时序电路状态发生改变的都是影子寄存器**。

#### 定时器中断配置

1. 配置定时器基础工作参数：HAL_TIM_Base_Init()
2. 定时器基础Msp初始化：HAL_TIM_Base_MspInit()
3. 使能更新中断并启动计数器：HAL_TIM_Base_Start_IT
4. 设置优先级，使能中断：HAL_NVIC_SetPriority()、HAL_TIM_IRQHandler()
5. 编写中断服务函数：TIMx_IRQHandler()、HAL_TIM_IRQHandler()
6. 编写定时器更新中断回调函数：HAL_TIM_PeriodElapsedCallback()

关键结构体成员：

* Prescaler：预分频系数
* CounterMode：计数模式
* Period：自动重载值ARR
* ClockDivision：时钟分频因子
* RepetitionCounter：重复计数器寄存器的值
* AutoReloadPreload：自动重装载预装载使能

**定时器计数模式及溢出条件**

![image-20240311115554678](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240311115554678.png)

定时器中断实验相关寄存器

定时器溢出时间计算方法
$$
T_{out} = \frac{(ARR+1)*(PSC+1)}{F_t}
$$
ARR——自动重装载值，PSC——预分频系数

定时器中断实验配置步骤

1. 定时器中断初始化函数
2. 定时器基础MSP初始化
3. 定时器中断服务函数
4. 编写定时器溢出回调函数

#### 通用定时器PWM输出

通用定时器输出PWM原理

假设：递增计数模式

ARR：自动重装载寄存器的值

CCRx：捕获/比较寄存器x的值

当CNT<CCRx，IO输出0

当CNT>=CCRx，IO输出1

![image-20240406203953706](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240406203953706.png)

**总结：PWM波周期或频率由ARR决定，PWM波占空比由CCRx决定**

### DMA



### ADC

#### ADC简介

**什么是ADC**

**常见的ADC类型**

**并联比较型工作示意图**

**逐次逼近型工作示意图**

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240409100125431.png" alt="image-20240409100125431" style="zoom:50%;" />

特点：分辨率和采样速度相互矛盾，分辨率越高，采样速度越低

**ADC的特性参数**

**STM32各系列ADC的主要特性**

#### ADC工作原理

ADC框图简介

参考电压/模拟部分电压

输入通道

转换序列

触发源

转换时间

数据寄存器

中断

单次转换模式和连续转换模式

扫描模式

#### 单通道ADC采集实验

#### 单通道ADC采集（DMA读取）

#### 多通道ADC采集（DMA读取）

#### 单通道ADC过采样实验

#### 内部温度传感器实验

#### 光敏传感器实验

### RS485

#### RS485介绍

**梳理：串口、UART、TTL、RS232、RS422、RS485关系**

串口是一个泛称，UART、RS232、RS422、RS485都遵循类似的通信时序协议，被统称为串口。

UART是STM32的UART外设，由此产生串口时序，产生的电平为CMOS电平。

TTL、RS232、RS422、RS485是串行通信接口标准。简单来说，就是逻辑1和0对应的电平不同。

RS485是串行通信标准，使用差分信号传输，抗干扰能力强，常用于工控领域。

RS485具有强大的组网功能，在串口基础协议上还制定了MODBUS协议。

串口基础协议：仅指封装了基本数据包格式的协议（基于数据位）

MODBUS协议：使用基本数据包组合成通讯帧格式的高层应用协议（基于数据包或字节）

#### RS485相关HAL库驱动介绍

#### RS485配置步骤

1. 配置串口工作参数：HAL_UART_Init
2. 串口底层初始化：配置GPIO、NVIC、CLOCK等
3. 开启串口异步接收中断：__HAL_UART_ENABLE_IT()
4. 设置优先级，使能中断：HAL_NVIC_SetPriority
5. 编写中断服务函数：USARTx_IRQHandler
6. 串口数据发送：HAL_UART_Transmit



### CAN

#### CAN基础知识介绍

**CAN介绍**

CAN总线特点：

* 多主控制：每个设备都可以主动发送数据
* 系统的柔软性：没有类似地址的信息，添加设备不改变原来总线的状态
* 通信速度：速度快，距离远
* 错误检测&错误通知&错误恢复功能
* 故障封闭：判断故障类型，并且进行隔离
* 连接节点多：速度与数量找平衡

**CAN协议的基本概念**

![image-20240412093004982](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240412093004982.png)

![image-20240412093255969](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240412093255969.png)

**CAN物理层**

CAN物理层主要涉及定义CAN通信系统的电气特性以及物理信号传输。它是OSI模型中的第一层，负责处理实际的数据传输方式，内容包括：

* 媒体类型：物理层定义了CAN通信可以使用哪种类型的传输媒体，典型的是**双绞线**（双绞线是一种电缆类型，主要用于电信和网络设备中的数据和信号传输。它由一对绝缘的铜导线组成，两根导线互相绞合在一起形成一对。绞合能够减少电磁干扰和射频干扰，减少数据传输过程中的噪音和误差。由于两条导线紧密绞合，一根导线上的噪音或干扰可以被另一根导线上产生的相反干扰取消掉，这种现象称为**差分信号传输**）。
* 

CAN使用差分信号进行数据传输，根据CAN_H和CAN_L上的电位差来判断总线电平

总线电平分为显性电平（逻辑0）和隐性电平（逻辑1），二者必居其一。

显性电平具有**优先权**。发送方通过使总线电平发生变化，将消息发送给接收方。

![image-20240411200529304](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240411200529304.png)

位时序（Bit Timing）

位时序指定如何对数据位进行编码和解码的过程，这是确保网络上设备之间正确、可靠地通信的关键部分。位时序的设置影响到CAN总线上数据传输的质量和速度。

**CAN收发器芯片介绍**

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240411200757617.png" alt="image-20240411200757617" style="zoom:50%;" />

* D：CAN发送引脚
* R：CAN接收引脚
* Vref：参考电压输出
* CANL：低电位CAN电压输入输出端
* CANH：高电位CAN电压输入输出端
* RS：高速/静音模式选择

**CAN协议层**

CAN总线以帧形式进行通信。CAN协议定义了5种类型的帧：数据帧、遥控帧、错误帧、过载帧、间隔帧。

![image-20240411200959552](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240411200959552.png)

**数据帧**

数据帧由7个段构成

![image-20240412094935768](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240412094935768.png)

* 帧起始：表示数据帧开始的段
* 仲裁段：表示该帧优先级的段
* 控制段：表示数据的字节数及保留位的段
* 数据段：数据的内容，可发送0~8个字节的数据
* CRC段：检查帧的传输错误的段
* ACK段：表示确认正常接收的段
* 帧结束：表示数据帧结束的段

**CAN总线仲裁**

CAN总线处于空闲状态，最先开始发送消息的单元获得发送权

多个单元同时开始发送时，从仲裁段（报文ID）的第一位开始进行仲裁。连续输出显性电平最多的单元可继续发送，即首先出现隐性电平的单元失去对总线的占有权变为接收。

ID越小优先级越高

**遥控帧**

接收单元向发送单元请求发送数据所用的帧。遥控帧由6个段组成。遥控帧没有数据帧的数据段。

* 帧起始（SOF）：表示帧开始的段。
* 仲裁段：表示该帧优先级的段。可请求具有相同ID的数据帧。
* 控制段：表示数据的字节数及保留位的段。
* CRC段：检查帧的传输错误的段。
* ACK段：表示确认正常接收的段。
* 帧结束：表示遥控帧结束的段。

优先级的决定

* 在总线空闲态，最先开始发送消息的单元获得发送权。
* 多个单元同时开始发送时，各发送单元从仲裁段的第一位开始进行仲裁。连续输出显性电平最多的单元可继续发送。

#### 控制器、收发器、总线

原文链接：https://blog.csdn.net/Naisu_kun/article/details/132814079

CAN的电气连接主要分**控制器**、**收发器**、**总线**。控制器很多单片机内置有；收发器通常是外置的；总线有H、L两条差分信号线构成，通常总线的两端需要有两个终端电阻。

CAN的总线上可以挂载多个节点，节点并不分主从，想发数据发就行，CAN控制器会依据数据头部带的ID信息进行仲裁，优先级高的数据继续发送。大多数CAN控制器包含先进先出的发送和接收邮箱，可以设置发送失败后自动重发。CAN控制器可以设置接收消息ID过滤器，只有符合条件的ID并且CRC校验通过的数据（CAN的一条完整的数据是自带CRC校验的）才会存放到接收邮箱中。

CAN主要分为CAN2.0和CAN-FD。CAN2.0数据帧一帧最大可以传输8字节，最高波特率为1000kbps。CAN-FD可以向下兼容CAN2.0。最大的变化在于**数据段**，一帧最大可以传输64字节，并且数据段波特率可以和其他部分不一样，最大可以到8000kbps。

![img](https://img-blog.csdnimg.cn/40fc5a392922469cb13694c92058e274.png#pic_center)

#### STM32 CAN控制器介绍

#### STM32 CAN过滤器详解

链接：http://t.csdnimg.cn/RuLFm

**两种过滤模式（列表模式和掩码模式）**

列表模式：准备好一个列表，把我们所需要关注的所有CAN报文ID写上去。过滤的时候就只要对比这张表，如果接收到的报文ID与表上的相符，则通过，如果表上没有，则不通过。

掩码模式：准备好两个列表，一个写上屏蔽码，另一个写上验证码。屏蔽码上相应位位1时，表示此位需要与验证码对应位进行比较，反之则表示不需要。

![img](https://img-blog.csdn.net/20160825193756895)

这样一来，能通过的结果数量就完全取决于屏蔽码。设的宽则可以通过得多，设的窄则通过得少。

在bxCAN中，分别采用了两个寄存器（CAN_FiR1，CANFiR2）来存储屏蔽码与验证码，从而实现掩码模式的工作流程。

下面来对比列表模式和掩码模式这两种模式的优缺点：

| 模式     | 优点                                                         | 缺点                         |
| -------- | ------------------------------------------------------------ | ---------------------------- |
| 列表模式 | 能精确地过滤每个指定的CAN ID                                 | 有数量限制                   |
| 掩码模式 | 取决于屏蔽码，有时无法完全精确到每一个CAN ID，部分不期望的CAN ID有时也会收到 | 数量取决于屏蔽码，最多无上限 |

**标准CAN ID与扩展CAN ID**

标准CAN ID的基本格式：

![img](https://img-blog.csdn.net/20160825203229618)

* SOF：帧起始
* Identifier：仲裁段
* Control：控制段
* Data：数据段
* CRC
* ACK
* EOF：帧结束

扩展CAN ID的基本格式：

![img](https://img-blog.csdn.net/20160825203328649)

在仲裁段部分，扩展CAN报文的CAN ID包含了base identifier与extension identifier，即基本ID与扩展ID。

**bxCAN的过滤器的解决方案**

根据模式与CAN ID的设置，可以得到4种不同的组合：32位宽的列表模式、16位宽的列表模式、32位宽的掩码模式、16位宽的掩码模式，如下图所示：

![img](https://img-blog.csdn.net/20160825203724823)

在bxCAN种，每个过滤器都存在这么两个寄存器CAN_FxR1与CAN_FxR2，这两个寄存器都是32位的，他的定义并不是固定的，针对不同的工作模式组合它的定义是不一样的。

* 在**列表模式-32位宽模式**下，这两个寄存器的各位定义都是一样的，都用来存储某个具体的期望通过的CAN ID，这样就可以存入两个期望通过的CAN ID（标准CAN ID和扩展CAN ID均可）。
* 若在**掩码模式-32位宽模式**下时，则CAN_FxR1用作32位宽的验证码，而CAN_FxR2用作32位宽的屏蔽码（标准CAN ID和扩展CAN ID均可）。
* 在**列表模式-16位宽模式**下，CAN_FxR1与CAN_FxR2定义一样，且各自拆成两个，则总共可以写入4个标准CAN ID。
* 若在**掩码模式-16位宽模式**下，则可以当作2对验证码+屏蔽码组合使用，但它只能对标准CAN ID进行过滤。

**32位宽的列表模式**

![img](https://img-blog.csdn.net/20160825204257233)

如上图所示，在32位宽的列表模式下，CAN_FxR1与CAN_FxR2都用来存储希望通过的CAN ID。由于是32位宽的，因此既可以存储标准CAN ID，也可以存储扩展CAN ID。注意看上图最底下的各位定义，从右到左，首先最低位是没有用的，然后是RTR，表示是否为远程帧，接着IDE，扩展帧标志，然后才是EXID[0:17]这18位扩展ID，最后才是STID[0:10]这11位标准ID。

在进行配置的时候，将希望通过的CAN ID写入的时候，要注意各个位对号入座，即基本ID放到对应的STD[0:10]，扩展ID对应放到EXID[0:17]，若是扩展帧，则需要将IDE设为1，标准帧则为0，数据帧设RTR为0，远程帧设RTR为1。

在CubeMX中，CAN_FxR1与CAN_FxR2寄存器分别被拆分成两段，CAN_FxR1寄存器的高16位对应FilterIdHigh，低16位对应FilterIdLow，而CAN_FxR2寄存器的高16位对应着FilterMaskIdHigh，低16位对应着FilterMaskIdLow。**这4个16位的变量其具体含义取决于当前过滤器的工作模式**。

**16位宽的列表模式**

![img](https://img-blog.csdn.net/20160825204453544)

**32位宽的掩码模式**

![img](https://img-blog.csdn.net/20160825204624596)

32位宽模式下，FilterIdHigh与FilterIdLow合在一起表示CAN_FxR1寄存器，用来存放验证码，而FilterMaskIdHigh与FilterMaskIdLow合在一起表示CAN_FxR2寄存器，用来存放屏蔽码。在32位宽的掩码模式下，既可以过滤标准CAN ID，也可以过滤扩展CAN ID，甚至两者混合这来也是可以的，下面我们就这3中情况分别给出示例。

只针对标准CAN ID：

```C
static void CANFilterConfig_Scale32_IdMask_StandardIdOnly(void)  
{  
  CAN_FilterConfTypeDef  sFilterConfig;  
  uint16_t StdIdArray[10] ={0x7e0,0x7e1,0x7e2,0x7e3,0x7e4,  
                                0x7e5,0x7e6,0x7e7,0x7e8,0x7e9}; //定义一组标准CAN ID  
  uint16_t      mask,num,tmp,i;  
    
  sFilterConfig.FilterNumber = 2;               //使用过滤器2  
  sFilterConfig.FilterMode = CAN_FILTERMODE_IDMASK;     //配置为掩码模式  
  sFilterConfig.FilterScale = CAN_FILTERSCALE_32BIT;    //设置为32位宽  
  sFilterConfig.FilterIdHigh =(StdIdArray[0]<<5);     //验证码可以设置为StdIdArray[]数组中任意一个，这里使用StdIdArray[0]作为验证码  
  sFilterConfig.FilterIdLow =0;  
    
  mask =0x7ff;                      //下面开始计算屏蔽码  
  num =sizeof(StdIdArray)/sizeof(StdIdArray[0]);  
  for(i =0; i<num; i++)      //屏蔽码位StdIdArray[]数组中所有成员的同或结果  
  {  
    tmp =StdIdArray[i] ^ (~StdIdArray[0]);  //所有数组成员与第0个成员进行同或操作  
    mask &=tmp;  
  }  
  sFilterConfig.FilterMaskIdHigh =(mask<<5);  
  sFilterConfig.FilterMaskIdLow =0|0x02;        //只接收数据帧  
    
  sFilterConfig.FilterFIFOAssignment = 0;       //设置通过的数据帧进入到FIFO0中  
  sFilterConfig.FilterActivation = ENABLE;  
  sFilterConfig.BankNumber = 14;  
    
  if(HAL_CAN_ConfigFilter(&hcan1, &sFilterConfig) != HAL_OK)  
  {  
    Error_Handler();  
  }  
}  
```

对于验证码，任意一个期望通过的CAN ID都是可以设为验证码的，但屏蔽码，却是所有期望通过的CAN ID相互同或后的最终结果，这个即是屏蔽码。

只针对扩展CAN ID：

```c
static void CANFilterConfig_Scale32_IdMask_ExtendIdOnly(void)  
{  
  CAN_FilterConfTypeDef  sFilterConfig;  
  //定义一组扩展CAN ID用来测试  
uint32_t ExtIdArray[10] ={0x1839f101,0x1835f102,0x1835f113,0x1835f124,0x1835f105,  
                            0x1835f106,0x1835f107,0x1835f108,0x1835f109,0x1835f10A};  
  uint32_t      mask,num,tmp,i;  
    
  sFilterConfig.FilterNumber = 3;                   //使用过滤器3  
  sFilterConfig.FilterMode = CAN_FILTERMODE_IDMASK;         //配置为掩码模式  
  sFilterConfig.FilterScale = CAN_FILTERSCALE_32BIT;        //设为32位宽  
  sFilterConfig.FilterIdHigh =((ExtIdArray[0]<<3) >>16) &0xffff;//数组任意一个成员都可以作为验证码  
  sFilterConfig.FilterIdLow =((ExtIdArray[0]<<3)&0xffff) | CAN_ID_EXT;  
    
  mask =0x1fffffff;  
  num =sizeof(ExtIdArray)/sizeof(ExtIdArray[0]);  
  for(i =0; i<num; i++)              //屏蔽码位数组各成员相互同或的结果  
  {  
    tmp =ExtIdArray[i] ^ (~ExtIdArray[0]);  //都与第一个数据成员进行同或操作  
    mask &=tmp;  
  }  
  mask <<=3;                                  //对齐寄存器  
  sFilterConfig.FilterMaskIdHigh = (mask>>16)&0xffff;  
  sFilterConfig.FilterMaskIdLow = (mask&0xffff)|0x02;       //只接收数据帧  
  sFilterConfig.FilterFIFOAssignment = 0;  
  sFilterConfig.FilterActivation = ENABLE;  
  sFilterConfig.BankNumber = 14;  
    
  if(HAL_CAN_ConfigFilter(&hcan1, &sFilterConfig) != HAL_OK)  
  {  
    Error_Handler();  
  }  
}  
```

与之前的标准CAN ID相比，扩展CAN ID的验证码与屏蔽码放入到相对应的寄存器时所移动的位数与标准CAN ID时有所差别，其他的都一样。

标准CAN ID与扩展CAN ID混合过滤

```c
static void CANFilterConfig_Scale32_IdMask_StandardId_ExtendId_Mix(void)  
{  
  CAN_FilterConfTypeDef  sFilterConfig;  
  //定义一组标准CAN ID  
uint32_t StdIdArray[10] ={0x711,0x712,0x713,0x714,0x715,  
                          0x716,0x717,0x718,0x719,0x71a};  
  //定义另外一组扩展CAN ID  
uint32_t ExtIdArray[10] ={0x1900fAB1,0x1900fAB2,0x1900fAB3,0x1900fAB4,0x1900fAB5,  
                            0x1900fAB6,0x1900fAB7,0x1900fAB8,0x1900fAB9,0x1900fABA};  
  uint32_t      mask,num,tmp,i,standard_mask,extend_mask,mix_mask;  
    
  sFilterConfig.FilterNumber = 4;               //使用过滤器4  
  sFilterConfig.FilterMode = CAN_FILTERMODE_IDMASK;     //配置为掩码模式  
  sFilterConfig.FilterScale = CAN_FILTERSCALE_32BIT;    //设为32位宽  
  sFilterConfig.FilterIdHigh =((ExtIdArray[0]<<3) >>16) &0xffff;    //使用第一个扩展CAN  ID作为验证码  
  sFilterConfig.FilterIdLow =((ExtIdArray[0]<<3)&0xffff);  
    
  standard_mask =0x7ff;     //下面是计算屏蔽码  
  num =sizeof(StdIdArray)/sizeof(StdIdArray[0]);  
  for(i =0; i<num; i++)          //首先计算出所有标准CAN ID的屏蔽码  
  {  
    tmp =StdIdArray[i] ^ (~StdIdArray[0]);  
    standard_mask &=tmp;  
  }  
    
  extend_mask =0x1fffffff;  
  num =sizeof(ExtIdArray)/sizeof(ExtIdArray[0]);  
  for(i =0; i<num; i++)          //接着计算出所有扩展CAN ID的屏蔽码  
  {  
    tmp =ExtIdArray[i] ^ (~ExtIdArray[0]);  
    extend_mask &=tmp;  
  }  
  mix_mask =(StdIdArray[0]<<18)^ (~ExtIdArray[0]);    //再计算标准CAN ID与扩展CAN ID混合的屏蔽码  
  mask =(standard_mask<<18)& extend_mask &mix_mask;   //最后计算最终的屏蔽码  
  mask <<=3;                          //对齐寄存器  
  
  sFilterConfig.FilterMaskIdHigh = (mask>>16)&0xffff;  
  sFilterConfig.FilterMaskIdLow = (mask&0xffff);  
  sFilterConfig.FilterFIFOAssignment = 0;  
  sFilterConfig.FilterActivation = ENABLE;  
  sFilterConfig.BankNumber = 14;  
    
  if(HAL_CAN_ConfigFilter(&hcan1, &sFilterConfig) != HAL_OK)  
  {  
    Error_Handler();  
  }  
}  
```

在混合的情况下，只需稍微修改下屏蔽码的计算方式就可以了，其他的基本没有什么变化。

**16位宽掩码模式**

![img](https://img-blog.csdn.net/20161011104044062)

在16位宽的掩码模式下，CAN_FxR1的低16位是作为验证码，对应的16位屏蔽码为CAN_FxR1的高16位，同样的，CAN_FxR2的低16位是作为验证码，对应与CAN_FxR2的高16位为屏蔽码。示例代码如下：

```C
static void CANFilterConfig_Scale16_IdMask(void)  
{  
  CAN_FilterConfTypeDef  sFilterConfig;  
  uint16_t StdIdArray1[10] ={0x7D1,0x7D2,0x7D3,0x7D4,0x7D5, //定义第一组标准CAN ID  
                          0x7D6,0x7D7,0x7D8,0x7D9,0x7DA};  
  uint16_t StdIdArray2[10] ={0x751,0x752,0x753,0x754,0x755, //定义第二组标准CAN ID  
                          0x756,0x757,0x758,0x759,0x75A};  
  uint16_t      mask,tmp,i,num;  
    
  sFilterConfig.FilterNumber = 5;                   //使用过滤器5  
  sFilterConfig.FilterMode = CAN_FILTERMODE_IDMASK;         //配置为掩码模式  
  sFilterConfig.FilterScale = CAN_FILTERSCALE_16BIT;        //设为16位宽  
    
  //配置第一个过滤对  
  sFilterConfig.FilterIdLow =StdIdArray1[0]<<5;           //设置第一个验证码  
  mask =0x7ff;  
  num =sizeof(StdIdArray1)/sizeof(StdIdArray1[0]);  
  for(i =0; i<num; i++)                          //计算第一个屏蔽码  
  {  
    tmp =StdIdArray1[i] ^ (~StdIdArray1[0]);  
    mask &=tmp;  
  }  
  sFilterConfig.FilterMaskIdLow =(mask<<5)|0x10;    //只接收数据帧  
    
  //配置第二个过滤对  
  sFilterConfig.FilterIdHigh = StdIdArray2[0]<<5; //设置第二个验证码  
  mask =0x7ff;  
  num =sizeof(StdIdArray2)/sizeof(StdIdArray2[0]);  
  for(i =0; i<num; i++)                  //计算第二个屏蔽码  
  {  
    tmp =StdIdArray2[i] ^ (~StdIdArray2[0]);  
    mask &=tmp;  
  }  
  sFilterConfig.FilterMaskIdHigh = (mask<<5)|0x10;  //只接收数据帧  
    
   
  sFilterConfig.FilterFIFOAssignment = 0;       //通过的CAN 消息放入到FIFO0中  
  sFilterConfig.FilterActivation = ENABLE;  
  sFilterConfig.BankNumber = 14;  
    
if(HAL_CAN_ConfigFilter(&hcan1, &sFilterConfig) != HAL_OK)  
  {  
    Error_Handler();  
  }  
}  
```

#### FDCAN



 #### CAN相关寄存器介绍

#### CAN相关HAL库驱动介绍

![image-20240411212731006](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240411212731006.png)

#### CAN基本驱动步骤

1. CAN参数初始化：工作模式、波特率等，HAL_CAN_Init
2. 使能CAN时钟和初始化相关引脚：GPIO模式设为复用功能模式，HAL_CAN_MspInit
3. 设置过滤器：HAL_CAN_ConfigFilter完成过滤器的初始化
4. CAN数据接收和发送：HAL_CAN_AddTxMessage发送消息，HAL_CAN_GetRxMessage接收数据
5. 使能CAN相关中断/设置NVIC/编写中断服务函数：__HAL_CAN_ENABLE_IT

#### 编程实战

#### 注意事项

* 波特率

在CAN总线系统中，连入的所有设备必须以相同的波特率进行通信。如果网络上的节点有不同的波特率，那么它们将无法正确地交换信息，因为时序上的不同步会导致数据解析错误。

* 数据发送

如果要发送浮点类型的数据，需要通过一种称为数据封装或序列化的过程将浮点数转换为一系列字节，这样它们就可以放入CAN帧的数据字段中发送。

* 数据段长度

在CAN网络中，不同节点发送到总线上的帧的数据段长度是可以不同的。每个CAN帧的数据字段长度可以从0至8个字节（对于标准CAN 2.0A/B），并不需要所有节点发送相同长度的数据。

* 是否需要定义过滤器

如果CAN节点仅用于发送数据，并且不需要接收任何数据，那么理论上你不需要设置接收过滤器，因为接收过滤器的作用是确定哪些入站消息是对此节点有意义的，以便它们能被硬件接收和处理。

然而，在实际应用中，大多数的CAN控制器都至少需要一个接收过滤器设置，即使它可能永远不会处理接收到的消息。这是因为没有配置任何接收过滤器可能会导致控制器处于静默模式，也有可能由于也有可能由于其他硬件或规范的原因需要最小配置。

为了确认你的硬件是否需要至少设置一个过滤器，应当查看你所使用的硬件的CAN控制器的数据手册或参考HAL库的文档。一般而言，配置一个默认的过滤器，让所有消息都通过，然后在软件上忽略所有接收到的消息，是一种安全的做法：

```c
CAN_FilterTypeDef  sFilterConfig;
sFilterConfig.FilterBank = 0; // 使用第0个过滤器
sFilterConfig.FilterMode = CAN_FILTERMODE_IDMASK; // 掩码模式
sFilterConfig.FilterScale = CAN_FILTERSCALE_32BIT; // 32位过滤
sFilterConfig.FilterIdHigh = 0x0000; // 接收所有ID高位
sFilterConfig.FilterIdLow = 0x0000; // 接收所有ID低位
sFilterConfig.FilterMaskIdHigh = 0x0000; // 掩码设置为0
sFilterConfig.FilterMaskIdLow = 0x0000; // 掩码设置为0
sFilterConfig.FilterFIFOAssignment = CAN_RX_FIFO0; // 分配给FIFO 0
sFilterConfig.FilterActivation = ENABLE; // 激活过滤器

if(HAL_CAN_ConfigFilter(&hcan, &sFilterConfig) != HAL_OK) {
  // 过滤器配置出错的处理
}
```

* 发送帧结构体的初始化

在CAN通信中，发送帧的`TxHeader`结构体通常在发送消息之前被初始化。如果`TxHeader`结构体的某些值在每次发送时都不发生变化，可以在CAN初始化或者过滤器配置时进行一次设置，以避免在每次发送消息时重复进行相同的设置。然而，像数据长度（DLC）和扩展标识符（ExtId）这样的字段往往对于每个消息都是唯一的，可能需要在每次发送之前根据消息的不同而进行调整。

如果已经在发送函数内设置了`ExtId`和`DLC`值。而`IDE`（帧格式）、`RTR`（帧类型）和`TransmitGlobalTime` 在所有消息中都是相同的，则不需要在每次发送操作中都设置它们。因此可以在初始化过滤器函数中初始化这些固定值，如下例所示：

```c
void CAN_Filter_Init(void) {
    CAN_FilterTypeDef sFilterConfig;
    // ...配置过滤器参数...

    // 应用过滤器配置
    HAL_CAN_ConfigFilter(&hcan, &sFilterConfig);
    
    // 在这里初始化TxHeader的固定部分
    TxHeader.IDE = CAN_ID_EXT;
    TxHeader.RTR = CAN_RTR_DATA;
    TxHeader.TransmitGlobalTime = DISABLE;
    // DLC 和 ExtID 需要在发送消息时根据具体消息进行设置
}
```

最后需要保证在调用发送函数之前，`TxHeader`已经被正确初始化，无论是在CAN或过滤器初始化时，还是在发送函数内部。

#### 课堂总结



## STM32F103 精英开发指南

本书学习顺序：先通读一遍《精英V2硬件参考手册》，对开发板的硬件资源有个大概了解，然后从基础篇开始，再到入门篇，最后学习提高篇，循序渐进，逐一攻克。

### 精英V2硬件参考手册

精英V2硬件基本参数：

* CPU：STM32F103ZET6
* 引出IO：110个

### 启动过程分析

这里的启动过程指的是从STM32芯片上电复位执行的第一条指令开始，到执行用户编写的main函数这之间的过程。

事实上，main函数并非最先执行的，在此之前需要做一些准备工作，准备工作通过启动文件的程序来完成。

#### 启动模式

#### 启动文件分析

#### map文件分析

## STM32CubeMX

### 点灯

🔗：http://t.csdnimg.cn/FTwKU

配置时钟

![image-20240606104747396](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240606104747396.png)

使能LED相关引脚，设置为GPIO_Output

关于GPIO的配置：http://t.csdnimg.cn/3lQkI

![image-20240606105111011](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240606105111011.png)



### 外部中断配置

链接：http://t.csdnimg.cn/r13RO

**设置RCC**

**GPIO初始化**

A板上只有一个用户自定义按键，对应PB2，配置此端口为中断口。

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240305213223408.png" alt="image-20240305213223408" style="zoom:50%;" />

PB2应该是在EXTI2上。对EXTI配置选择类型（中断或事件）和相应的触发事件（上升沿触发、下降沿触发或边沿触发）。这里设置PB2为输入下拉、上升沿触发。

PG1为板上LED等，配置PG1为输出口，当中断发生时改变IO口极性。

**配置GPIO_EXTI**

随后可以在stm32f4xx_it.c中看到我们所配置的中断服务函数，并且可以看到GPIO的初始化分到了gpio.c里面

![image-20240305214336123](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240305214336123.png)

HAL_GPIO_EXTI_IRQHandler函数就是清除中断标志位，之后进入中断回调函数中。

在HAL库中，中断运行结束后不会立刻退出，而是会线进入相对应的中断回调函数，处理该函数中的代码之后才会退出中断。所以在HAL库中我们一般将中断需要处理的代码放在中断回调函数中。

设置IO口模式、触发条件、IO口与中断线的映射关系

**配置中断优先级（NVIC），并使能中断**

在main.c的MX_GPIO_Init中，设置好中断线和GPIO映射关系，然后又设置好了中断触发模式等初始化参数。既然是外部中断，涉及到中断我们还要设置NVIC中断优先级。

![image-20240306091053606](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240306091053606.png)

HAL_NVIC_SetPriority的中间0表示抢占优先级为0，最右边的0表示子优先级为0。

1. 抢占优先级比子优先级的优先权更高
2. 如果抢占优先级相同，那么就会比较子优先级
3. 当两个中断源的抢占优先级相同时，这两个中断没有嵌套关系

**中断服务函数**

配置完中断优先级后，接着要做的是编写中断服务函数。

在stm32f4xx_it.c中，程序开始执行EXTI2_IRQHandler函数，这个函数只是调用了另一个函数HAL_GPIO_EXTI_IRQHandler

![image-20240306092517342](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240306092517342.png)



在stm32f4xx_hal_gpio.c中，HAL_GPIO_EXTI_IRQHandler的实现非常简单，就是清除中断标志位，然后调用回调函数HAL_GPIO_EXTI_Callback实现控制逻辑。该函数需要在main.c文件中重写，通过判断是来自哪个IO口编写相应的中断服务控制逻辑

**HAL库GPIO函数库讲解**

HAL_GPIO_Init：GPIO初始化，在函数初始化之后的引脚恢复成默认的状态，即各个寄存器复位时的值

HAL_GPIO_ReadPin：读取引脚的电平状态，函数返回值为0或1

HAL_GPIO_WritePin：引脚写0或1

HAL_GPIO_TogglePin：翻转引脚的电平状态

HAL_GPIO_EXTI_IRQHandler：外部中断服务函数，清除中断标志位

HAL_GPIO_EXTI_Callback：中断回调函数，中断函数具体要响应的动作

### 按键中断配置

链接：http://t.csdnimg.cn/V43p7



### UART串口通信配置

链接：http://t.csdnimg.cn/DZdfw

#### 设置外部时钟源

设置高速外部时钟HSE选择外部时钟源

#### 设置串口

* 1点击USART1
* 2设置MODE为异步通信（Asynchronous）
* 3基础参数：波特率为115200Bits/s，传输数据长度为8Bit，奇偶检验无，停止位1，接收和发送都使能
* 4GPIO引脚设置USART1_RX/USART_TX
* 5NVIC Settings一栏使能接收中断

![img](https://img-blog.csdnimg.cn/20190810150549328.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FzNDgwMTMzOTM3,size_16,color_FFFFFF,t_70)

![img](https://img-blog.csdnimg.cn/20191011164320407.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FzNDgwMTMzOTM3,size_16,color_FFFFFF,t_70)

#### 设置时钟



HAL库UART函数

UART结构体定义

```C
UART_HandleTypeDef huart7;
```

发送函数

```C
HAL_UART_Transmit(UART_HandleTypeDef *huart, uint8_t *pData, uint16_t Size, uint32_t Timeout)
```

功能：串口发送指定长度的数据。如果超时没有发送完成，则不再发送，返回超时标志（HAL_TIMEOUT）。举例：

```C
HAL_UART_Transmit(&huart1, (uint8_t *)ZZX, 3, 0xffff);   //串口发送三个字节数据，最大传输时间0xffff
```

接收函数

```c
HAL_UART_Receive(UART_HandleTypeDef *huart, uint8_t *pData, uint16_t Size, uint32_t Timeout)
```

重新定义printf函数（未成功）

* 在stm32f4xx_hal.c中包含stdio.h

```C
#include "stm32f4xx_hal.h"
#include <stdio.h>
extern UART_HandleTypeDef huart7;   //声明串口
```

* 在stm32f4xx_hal.c中重写fget和fput函数

```C
/**
  * 函数功能: 重定向c库函数printf到DEBUG_USARTx
  * 输入参数: 无
  * 返 回 值: 无
  * 说    明：无
  */
int fputc(int ch, FILE *f)
{
  HAL_UART_Transmit(&huart1, (uint8_t *)&ch, 1, 0xffff);
  return ch;
}
 
/**
  * 函数功能: 重定向c库函数getchar,scanf到DEBUG_USARTx
  * 输入参数: 无
  * 返 回 值: 无
  * 说    明：无
  */
int fgetc(FILE *f)
{
  uint8_t ch = 0;
  HAL_UART_Receive(&huart1, &ch, 1, 0xffff);
  return ch;
}
```

参考链接：[嵌入式45——Msp回调函数的作用以及执行 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/92379957)

整个串口初始化的过程为：

1. 用户函数MX_UART_Init
2. HAL_UART_Init
3. HAL_UART_MspInit

为什么串口相关初始化不在HAL_UART_Init函数内部一次初始化而还要调用函数HAL_UART_MspInit的原因：这实际上是HAL库的一个优点，**它通过开放一个回调函数HAL_UART_MspInit，让用户自己去编写与串口相关的MCU级别的硬件初始化，而与MCU无关的串口参数相关的通用配置则放在HAL_UART_Init**

我们要初始化一个串口，首先要设置和MCU无关的东西，例如波特率、奇偶校验、停止位等，这些参数设置与MCU没有任何关系。

![image-20240306221210396](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240306221210396.png)

在STM32的HAL驱动中HAL_PPP_MspInit作为回调，被HAL_PPPInit函数所调用。当我们需要移植程序到其他MCU平台时，我们只需要修改HAL_PPP_MspInit函数内容而不需要修改HAL_PPP_Init入口参数内容。

![image-20240306221744596](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240306221744596.png)

#### UART接收中断

因为中断接收函数只能触发一次接收中断，所以我们需要在中断回调函数中再调用一次中断接收函数

具体流程:

1. 初始化串口
2. 在main中第一次调用接收中断函数
3. 进入接收中断，接收完数据，进入中断回调函数
4. 修改HAL_UART_RxCpltCallback中断回调函数，处理接收的数据
5. 回调函数中要再调用一次HAL_UART_Receive_IT函数，使得程序可以重新触发接收中断



### 看门狗（独立看门狗、窗口看门狗）

链接：http://t.csdnimg.cn/FNBnQ

出于对单片机运行状态进行实时监测的考虑，便产生了一种专门用于监测单片机程序运行状态的模块或者芯片。

看门狗的本质就是定时计数器，计数器使能之后一直累加，而喂狗就是重新写入计数器的值，定时计数器重新累加。如果一定时间内没有接收到喂狗信号，便实现处理器的自动复位重启。

STM32内置两个看门狗，提供了更高的安全性、时间的准确性和使用的灵活性。两个看门狗设备（独立看门狗、窗口看门狗）可以用来检测和解决由软件错误引起的故障。当计数器达到给定的超时值时，触发一个中断（仅适用于窗口看门狗）或者产生系统复位。

* 独立看门狗（IWDG）由专用的低速时钟驱动，即使主时钟发生故障时它仍有效。独立看门狗适合引用于需要看门狗作为一个在主程序之外，能够完全独立工作，并且对时间精度要求低的场合
* 窗口看门狗由从APB1时钟分频后得到时钟驱动。通过可配置的时间窗口来检测应用程序非正常的过迟或过早操作。窗口看门狗最适合那些要求看门狗在精确计时窗口起作用的程序。

![img](https://img-blog.csdnimg.cn/20190811092426727.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FzNDgwMTMzOTM3,size_16,color_FFFFFF,t_70)

配置步骤

1. 设置RCC
2. 设置IWDG

* IWDG时钟预分频系数：4分频
* 计数器重装载值：4095

3. 时钟源设置

### 定时器中断

链接：[【STM32】HAL库 STM32CubeMX教程六----定时器中断_hal_tim_irqhandler-CSDN博客](https://blog.csdn.net/as480133937/article/details/99201209)

STM32F1系列共有8个定时器：

* 高级定时器：TIM1、TIM8
* 通用定时器：TIM2、TIM3、TIM4、TIM5
* 基本定时器：TIM6、TIM7

STM32F4系列共有15个定时器：

* 高级定时器：TIM1、TIM8
* 通用定时器：TIM2、TIM3、TIM4、TIM5、TIM9~TIM14
* 基本定时器：TIM6、TIM7

计数时钟可由下列时钟源提供：

* 内部时钟：TIMx_CLK
* 外部时钟模式1：外部捕捉比较引脚（TIx）
* 外部时钟模式2：外部引脚输入（TIMx_ETR）

**定时器的主从模式**

定时器一般是通过软件设置而启动，STM32的每个定时器也可以通过外部信号触发而启动，还可以通过另外一个定时器的某一个条件被触发而启动。这里所谓某一个条件也可以是定时到时间、定时器超时、比较成功等许多条件。

这种通过一个定时器触发另一个定时器的工作方式称为定时器的同步，发出触发信号的定时器工作于**主模式**，接受触发信号而启动的定时器工作于**从模式**。

#### 工程创建步骤

1. 设置RCC

设置高速外部时钟HSE，选择外部时钟源

2. 设置时钟

![image-20240321192705622](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240321192705622.png)

这时候定时器的时钟频率为84MHz

3. 定时器设置

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240321193925651.png" alt="image-20240321193925651" style="zoom: 50%;" />

* Prescaler：定时器分频系数
* Counter Mode：计数模式
* Counter Period：自动重装载值
* CKD：时钟分频因子，可以选择二分频和四分频
* auto-reload-preload：自动重装载

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240321194239772.png" alt="image-20240321194239772" style="zoom: 67%;" />

这两个为定时器主从模式配置，很少用到，这里用不到全部关闭

使能定时器中断：

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240321194333709.png" alt="image-20240321194333709" style="zoom:67%;" />

定时器溢出时间：
$$
T_{out} = ((arr + 1) * (psc + 1)) / T_{clk}
$$
定时器中断处理函数在stm32f4xx_it.c的TIM2_IRQHandler定时器中断服务函数中

这个函数的具体作用是判断中断是否正常，然后判断产生的是哪一类定时器中断，然后进入相应的中断回调函数。

```c
void HAL_TIM_PeriodElapsedCallback(TIM_HandleTypeDef *htim)
```

这里定时器溢出时间为500ms，LED点亮延时500ms闪烁

在main函数上方初始化使能定时器2

```c
  /* USER CODE BEGIN 2 */
    /*使能定时器1中断*/
    HAL_TIM_Base_Start_IT(&htim2);
  /* USER CODE END 2 */
```

在main函数下方添加中断回调函数

```c
void HAL_TIM_PeriodElapsedCallback(TIM_HandleTypeDef *htim)
{
    static unsigned char ledState = 0;
    if (htim == (&htim2))
    {
        if (ledState == 0)
            HAL_GPIO_WritePin(GPIOE,GPIO_PIN_15,GPIO_PIN_RESET);
        else
            HAL_GPIO_WritePin(GPIOE,GPIO_PIN_15,GPIO_PIN_SET);
        ledState = !ledState;
    }
}
```

### RTC及制作时间戳

链接：[STM32CubeMX使用(六)之RTC及制作时间戳_stm32时间戳-CSDN博客](https://blog.csdn.net/u014448875/article/details/121808691?spm=1001.2101.3001.6650.5&utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~Rate-5-121808691-blog-80832894.235^v43^pc_blog_bottom_relevance_base7&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~Rate-5-121808691-blog-80832894.235^v43^pc_blog_bottom_relevance_base7&utm_relevant_index=10)

开启RTC外设，设置初始时间

![image-20240324112746764](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240324112746764.png)

开启低速外部时钟LSE，将RTC的时钟来源选择为外部的32.768晶振

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240324112544668.png" alt="image-20240324112544668" style="zoom:67%;" />

### PWM输出

链接：http://t.csdnimg.cn/Ge9lx

脉冲宽度调制（PWM），是英文“Pulse Width Modulation”的缩写，简称脉宽调制，是利用微处理器的数字输出来对模拟电路进行控制的一种非常有效的技术，广泛应用在测量、通信、功率控制与变换等领域中。

STM32的每个通用定时器都有独立的4个通道可以用来作为：输入捕获、输出比较、PWM输出、单脉冲输出等。

#### 工程创建步骤

1. 设置RCC：设置高速外部时钟HSE，选择外部时钟源
2. 设置定时器

* 选择TIM3
* 设置定时器时钟源为内部时钟源
* 设置定时器CH1为PWM模式
* 对应管脚自动设置为复用模式
* 可自行选择是否开启定时器中断

![image-20240406211622533](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240406211622533.png)

### 定时器输入捕获

### DMA

链接：http://t.csdnimg.cn/1h0V5

DMA，Direct Memory Access，直接存储器访问，DMA传输将一个地址空间复制到另一个地址空间，提供在外设和存储器之间或者存储器和存储器之间的高度数据传输。

转移数据，尤其是转移大量数据，是可以不需要CPU的参与。比如希望外设A的数据拷贝到外设B，只要给两种外设提供一条数据通路，直接让数据由A拷贝到B，不经过CPU的处理。

DMA的传输方式主要有四种，但本质上是一样的，都是从内存的某一区域传输到内存的另一区域（外设的数据寄存器本质上就是内存的一个存储单元）。四种情况的数据传输如下：

* 外设到内存
* 内存到外设
* 内存到内存
* 外设到外设

#### 配置流程

下面以USART1的DMA传输为例

1. 设置RCC：设置高速外部时钟HSE，选择外部时钟源
2. 设置串口：

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240409092041623.png" alt="image-20240409092041623" style="zoom: 50%;" />

3. 开启外设DMA

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240409092440297.png" alt="image-20240409092440297" style="zoom:50%;" />

Direction：DMA传输方向

四种传输方向：

* 外设到内存 Peripheral To Memory
* 内存到外设 Memory To Peripheral
* 内存到内存 Memory To Memory
* 外设到外设 Peripheral To Peripheral

DMA传输模式

* Normal：正常模式，当一次DMA数据传输完后，停止DMA传输，也就是只传输一次
* Circular：循环模式，传输完成后又重新开始继续传输，不断循环永不停止

DMA指针递增设置

* Src Memory表示外设地址寄存器，功能：设置传输数据的时候外设地址是不变还是递增。如果设置为递增，那么下一次传输的时候地址加Data Width个字节
* Dst Memory表示内存地址寄存器，功能：设置传输数据时候内存地址是否递增。如果设置为递增，那么下一次传输的时候地址加Data Width个字节

串口发送数据是将数据不断存进固定外设地址串口的发送数据寄存器，所以外设的地址是不递增。

而内存储器存储的是要发送的数据，所以地址指针要递增，保证数据依次被发出。

<img src="https://img-blog.csdnimg.cn/20200320183804745.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FzNDgwMTMzOTM3,size_16,color_FFFFFF,t_70" alt="在这里插入图片描述" style="zoom:50%;" />

4. 时钟源设置

#### 函数库介绍

串口DMA发送数据：

```c
 HAL_UART_Transmit_DMA(UART_HandleTypeDef *huart, uint8_t *pData, uint16_t Size)
```

串口DMA接收数据：

```c
HAL_UART_Receive_DMA(UART_HandleTypeDef *huart, uint8_t *pData, uint16_t Size)
```

串口DMA恢复函数：

```c
HAL_UART_DMAResume(&huart1)
```



### ADC

链接：http://t.csdnimg.cn/30YXC

ADC，Analog-to-Digital Converter的缩写，指模/数转换器，是指将连续的模拟信号转换为离散的数字信号的器件。

12位ADC是一种逐次逼近型模拟数字转换器，有3个ADC控制器，多达18个通道，可测量16个外部和2个内部信号源。各通道的A/D转换可以单次、连续、扫面或间断模式执行。ADC的结果可以左对齐或右对齐方式存储在16位数据寄存器中。

#### 模拟信号与数字信号

在传输的过程中，模拟信号容易受到噪音的干扰，这可能导致信号失真。相比之下，数字信号对噪音有更强的免疫力，因为只要信号的质量足够以区分0和1，数字信号就可以被准确地重建，即使在长距离传输或多次复制后也是如此。这就是为什么在现代电子和通讯系统中，数字信号通信比模拟信号通信更常见。

#### ADC的转换模式

* 单次转换模式：只执行一次转换。
* 连续转换模式：转换结束之后马上开始新的转换。
* 扫描模式：简单地说是一次对所有所选中的通道进行转换，比如开了ch0、ch1、ch4、ch5。ch0转换完以后就会自动转换通道1、4、5，知道转换完，这个过程不能被打断。如果开启了连续转换模式，则会在转换完ch5之后开始新一轮的转换。
* 间断模式：可以说是对扫描模式的一种补充。它可以把0、1、4、5这四个通道进行分组。也可以每个通道单独配置为一组。这样每一组转换之前都需要先触发一次。

#### ADC的工作框图

**ADC输入通道**

从ADCx_INT0-ADCx_INT15对应三个ADC的16个外部通道，进行模拟信号转换。此外，还有两个内部通道：温度检测或者内部电压检测。

选择对应通道后，便会选择对应GPIO引脚。

虽然每个通道都可以进行模数转换，但由于ADC资源是共享的，**每次只能有一个通道被转换**。

为此，使用规则通道和注入通道，可以为不同优先级的模数转换任务提供灵活的调度方式：

* **规则通道**通常用于非紧急任务，可以进行一般的连续扫描或单一转换，并且可以按照设定的顺序对通道列表进行普通测量
* **注入通道**则是为了应对需要紧急响应的模拟信号。当某个特定条件或事件发生时，可以**立即中断**规则通道的转换，优先进行注入通道的转换（对于某些STM32型号，注入通道确实会打断正在进行的规则通道的转换。但在不同的微控制器之间，这种行为可能会有所不同）。

**ADC时钟**

ADC预分频器的ADCCLK是ADC模块的时钟来源

**中断**

中断触发条件有三个，规则通道转换结束、注入通道转换结束或者模拟看门狗状态被设置时都能产生中断。

转换结束中断就是正常的ADC完成一次转换，进入中断。

当被ADC转换的模拟电压值低于低阈值或高于高阈值时，便会产生中断。这是为了防止读取到的电压值超过量程或低于量程。

DMA

ADC还支持DMA触发，规则和注入通道转换结束后会产生DMA请求，用于将转换好的数据传输到内存

#### 配置流程

1. 设置RCC：设置高速外部时钟HSE，选择外部时钟源
2. 设置时钟：
3. ADC配置

* ADCs_Common_Settings

​		独立模式意味着每个ADC将独立工作，互不影响

​		对照的是，多个ADC还可以配合工作，在双ADC或多ADC模式下，一起同步采样

* Clock Prescaler

​		用于设置ADC时钟的预分频值，这是因为ADC的工作时钟不能太高，需要通过预分频来降低从APB总线或是其他时钟源获得的时钟频率（ADC的工作时钟主要来源于内部的APB总线时钟，这是最常见的配置。然而不同的STM32系列微控制器可能会支持不同的时钟配置选项，例如在STM32L4系列中，ADC可以由异步时钟驱动，而不依赖于任何总线时钟）。

​		STM32不同系列和型号的微控制器有不同的最大ADC时钟频率要求，需要参照相应的参考手册。14MHz是一个相对通用的值，能够确保ADC既不会过慢影响采样率，也不会过快导致转换不准确。

* Data Alignment

​		数据对齐方式

* Scan Conversion Mode

​		如果只是用了一个通道的话，DISABLE；如果使用了多个通道的话，设置为ENABLE

* Continuous Conversion Mode

​		连续转换模式。设置为ENABLE，即连续转换；DISABLE则是单此转换。两者的区别在于连续转换直到所有的数据转换完之后才停止转换，而单次转换只转换一次数据就停止，要再次触发转换才可以进行转换。

* Number Of Conversion

​		转换通道数，用到几个通道就设置为几

* External Trigger Conversion Source

​		外部触发转换源

### CAN

链接：http://t.csdnimg.cn/2qvsh

CubeMX并不会帮我们生成过滤器配置相关函数，需要我们自己写

* 首先了解什么叫标准帧和扩展帧
* 其次是理解什么叫列表模式和掩码模式，列表模式简单说就是从已知库里面寻找匹配的对象，而掩码模式则是我只知道目标的局部特征，我想根据这个特征筛选出目标对象。比如掩码模式下，我只接收帧头ID位0x1800D8D0的数据，不是这个帧头的数据通通无视。

#### 配置流程

1. 时钟及相关配置
2. CAN通讯配置

CAN总线波特率计算方法：http://t.csdnimg.cn/ZAREw

![img](https://img.anfulai.cn/dz/attachment/forum/pw/Fid_29/29_58_e0402f49c6af8c3.png)

```C
/*
        CAN 波特率 = RCC_APB1Periph_CAN1 / Prescaler / (SJW + BS1 + BS2);
        
        SJW = synchronisation_jump_width
        BS = bit_segment
        
        设置CAN波特率为1 Mbps        
        CAN 波特率 = 42000000 / 2 / (1 + 12 + 8) / = 1 Mbps        
*/
CAN_InitStructure.CAN_SJW = CAN_SJW_1tq;
CAN_InitStructure.CAN_BS1 = CAN_BS1_12tq;
CAN_InitStructure.CAN_BS2 = CAN_BS2_8tq;
CAN_InitStructure.CAN_Prescaler = 2;
CAN_Init(CAN1, &amp;CAN_InitStructure);
```

波特率计算

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240412180954377.png" alt="image-20240412180954377" style="zoom:67%;" />

模式选择

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240412180911938.png" alt="image-20240412180911938" style="zoom: 67%;" />

使能CAN RX0中断，代表的是接受邮箱0的接收中断

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240412191619549.png" alt="image-20240412191619549" style="zoom:50%;" />

3. USART串口配置

用于调试输出数据

4. NVIC中断优先级确认
5. 生成工程目录
6. 程序编写

打开usrat.h，添加头文件#include "stdio.h"。在usart.c中重定义printf和getchar，便于用串口助手调试，添加如下两个函数：

```c
/* USER CODE BEGIN 1 */
 
//重定义printf和getchar，便于调试
int fputc(int ch, FILE *f)
{
  HAL_UART_Transmit(&huart2, (uint8_t *)&ch, 1, 0xffff);
  return ch;
}
 
int fgetc(FILE * f)
{
  uint8_t ch = 0;
  HAL_UART_Receive(&huart2,&ch, 1, 0xffff);
  return ch;
}
/* USER CODE END 1 */
```

打开can.h，添加两个宏定义，第一个是扩展帧接收的标识符，第二个是扩展帧发送的标识符。

```c
/* USER CODE BEGIN Private defines */
#define CAN_RxExtId 0x1800D8D0
#define CAN_TxExtId 0x1800D0D8
/* USER CODE END Private defines */
```

继续在can.h中添加两个函数，以及三个外部变量声明：

```c
/* USER CODE BEGIN Prototypes */
void CAN_Filter_Init(void);   //过滤器配置函数
uint8_t CAN_Send_Msg(uint8_t* msg,uint8_t len);  //数据发送函数
 
extern CAN_TxHeaderTypeDef	TxHeader;      //发送
extern CAN_RxHeaderTypeDef	RxHeader;      //接收
extern uint8_t	RxData[8];   //数据接收数组
/* USER CODE END Prototypes */
```

接下来我们开始编辑can.c文件，在顶部添加句柄，定义数组

```c
/* USER CODE BEGIN 0 */
CAN_TxHeaderTypeDef	TxHeader;      //发送
CAN_RxHeaderTypeDef	RxHeader;      //接收
 
uint8_t	RxData[8];  //数据接收数组，can的数据帧只有8帧
/* USER CODE END 0 */
```

我们需要自己编写3个函数，第一个是过滤器配置的函数，第二个是can发送数据函数，第三个是中断接收函数

```C
/*CAN过滤器初始化*/
void CAN_Filter_Init(void)
{
	CAN_FilterTypeDef sFilterConfig;
	
  sFilterConfig.FilterBank = 0;                    /* 过滤器组0 */
  sFilterConfig.FilterMode = CAN_FILTERMODE_IDMASK;  /* 屏蔽位模式 */
  sFilterConfig.FilterScale = CAN_FILTERSCALE_32BIT; /* 32位。*/
  
  sFilterConfig.FilterIdHigh         = (((uint32_t)CAN_RxExtId<<3)&0xFFFF0000)>>16;				/* 要过滤的ID高位 */
  sFilterConfig.FilterIdLow          = (((uint32_t)CAN_RxExtId<<3)|CAN_ID_EXT|CAN_RTR_DATA)&0xFFFF; /* 要过滤的ID低位 */
  sFilterConfig.FilterMaskIdHigh     = 0xFFFF;			/* 过滤器高16位每位必须匹配 */
  sFilterConfig.FilterMaskIdLow      = 0xFFFF;			/* 过滤器低16位每位必须匹配 */
  sFilterConfig.FilterFIFOAssignment = CAN_RX_FIFO0;           /* 过滤器被关联到FIFO 0 */
  sFilterConfig.FilterActivation = ENABLE;          /* 使能过滤器 */ 
  sFilterConfig.SlaveStartFilterBank = 14;
	
	if (HAL_CAN_ConfigFilter(&hcan, &sFilterConfig) != HAL_OK)
  {
		/* Filter configuration Error */
    Error_Handler();
  }
	
  if (HAL_CAN_Start(&hcan) != HAL_OK)
  {
    /* Start Error */
    Error_Handler();
  }
	
	  /*##-4- Activate CAN RX notification #######################################*/
  if (HAL_CAN_ActivateNotification(&hcan, CAN_IT_RX_FIFO0_MSG_PENDING) != HAL_OK)
  {
    /* Start Error */
    Error_Handler();
  }
	
	TxHeader.ExtId=CAN_TxExtId;        //扩展标识符(29位)
	TxHeader.IDE=CAN_ID_EXT;    //使用标准帧
	TxHeader.RTR=CAN_RTR_DATA;  //数据帧
	TxHeader.DLC=8; 
	TxHeader.TransmitGlobalTime = DISABLE;
}
```

```C
/*CAN发送数据，入口参数为要发送的数组指针，数据长度，返回0代表发送数据无异常，返回1代表传输异常*/
uint8_t CAN_Send_Msg(uint8_t* msg,uint8_t len)
{	
  uint8_t i=0;
	uint32_t TxMailbox;
	uint8_t message[8];
 
	TxHeader.ExtId=CAN_TxExtId;        //扩展标识符(29位)
	TxHeader.IDE=CAN_ID_EXT;    //使用扩展帧
	TxHeader.RTR=CAN_RTR_DATA;  //数据帧
	TxHeader.DLC=len;    
	
  for(i=0;i<len;i++)
  {
		message[i]=msg[i];
	}
	
  if(HAL_CAN_AddTxMessage(&hcan, &TxHeader, message, &TxMailbox) != HAL_OK)//发送
	{
		return 1;
	}
	while(HAL_CAN_GetTxMailboxesFreeLevel(&hcan) != 3) {}
    return 0;
}
```

```c
/*CAN接收中断函数*/
void HAL_CAN_RxFifo0MsgPendingCallback(CAN_HandleTypeDef *CanNum)
{
	uint32_t i;
	
	Rx_Flag =1;  //接收标志位
	HAL_CAN_GetRxMessage(&hcan, CAN_RX_FIFO0, &RxHeader, RxData);
	for(i=0;i<RxHeader.DLC;i++)  RxBuf[i]=RxData[i];  //用RxBuf转存RxData的数据
}
```

can采用的是中断接收，所以务必添加这个函数，否则无法接收数据。



## 开发板C工程文件（Keil）移植到VSCode（Makefile）下编译开发

链接：[从零开始制作RoboMaster步兵机器人-2.开发板C 工程文件（Keil）移植到Vscode（makefile）下编译开发步骤详解_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1td4y1277b/?spm_id_from=333.880.my_history.page.click&vd_source=ae7834082973f295d9d56373ae0e7e3e)

### Linux下开发板C工程移植

* 使用STM32CubeMX打开工程
* Project Manage——Toolchian/IDE设置为Makefile——GENERATE CODE
* 使用VSCode打开后新建运行文件
* 向Makefile文件中添加C文件

## 宇树电机

### 电机的控制

data结构体成员：

* Id：当前控制命令的目标电机ID
* mode：目标电机运行模式。（0=停止，1=FOC控制，2=电机标定）
* T：前馈力矩
* W：指定角速度
* Pos：指定角度位置
* K_P：位置刚度
* K_W：速度刚度（阻尼）

所有与电机通信的源码都在GO-M8010-6.c文件中，在移植到其他单片机平台时，必须包含hal库的底层通信头文件，电机通信头文件，CRC校验头文件（usart.h、motor）

用户需要将模块的线路连接到电源/485转接板上，

给电机发送的命令都是针对减速器之前的电机转子。所以在进行实际控制的过程中，一定要注意考虑电机的减速比。在GO-8010-6电机中，减速比为6.33

#### 位置模式

#### 速度模式

#### 

## Robomaster 开发板A型使用

开发板主控芯片为STM32F427IIH6

材料：《RoboMaster开发板用户手册》

板上外设：

* USB
* DBUS
* SWD：调试接口
* UART：串口通信
* GPIO：IO口

* CAN
* PWM



### ST-link调试

```C
HAL_GPIO_WritePin(GPIOG, GPIO_PIN_1, GPIO_PIN_RESET);
HAL_Delay(500);
HAL_GPIO_WritePin(GPIOG, GPIO_PIN_1, GPIO_PIN_SET);
HAL_Delay(500);
```

链接：http://t.csdnimg.cn/FkChV

使用STM32CubeMX对接口进行设置

## JY61P

链接：http://t.csdnimg.cn/Ardss

1. 串口初始化分为串口1初始化、串口2初始化。其中串口2初始化又多了一个串口2中断服务函数，这个函数用于接收JY61传过来的数据，然后放在数据缓存区。
2. while主循环包括数据解析和数据输出。数据解析负责把从串口2中断服务函数得到的数据进行数据的一个处理。然后从串口1把数据输出到PC。

### WIT私有协议

#### 读格式

* 数据按照16进制方式发送，不是ASCII码
* 每个数据分低字节和高字节依次传送，二者组合成一个有符号的short类型的数据。

##### 时间输出

![image-20240308195342383](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240308195342383.png)

##### 加速度输出

![image-20240308195404825](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240308195404825.png)

##### 角速度输出

##### 角度输出

![image-20240308195459705](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240308195459705.png)

### Keil工程

使用STM32CubeMX完成配置后，使用Keil打开工程，在魔术棒中设置好编译选项，编译。

首先复写printf函数。在`usart.c`文件中加入以下代码：

```C
/******************************************************************************************/
/* 加入以下代码, 支持printf函数, 而不需要选择use MicroLIB */

#if 1

#if (__ARMCC_VERSION >= 6010050)            /* 使用AC6编译器时 */
__asm(".global __use_no_semihosting\n\t");  /* 声明不使用半主机模式 */
__asm(".global __ARM_use_no_argv \n\t");    /* AC6下需要声明main函数为无参数格式，否则部分例程可能出现半主机模式 */

#else
/* 使用AC5编译器时, 要在这里定义__FILE 和 不使用半主机模式 */
#pragma import(__use_no_semihosting)

struct __FILE
{
    int handle;
    /* Whatever you require here. If the only file you are using is */
    /* standard output using printf() for debugging, no file handling */
    /* is required. */
};

#endif

/* 不使用半主机模式，至少需要重定义_ttywrch\_sys_exit\_sys_command_string函数,以同时兼容AC6和AC5模式 */
int _ttywrch(int ch)
{
    ch = ch;
    return ch;
}

/* 定义_sys_exit()以避免使用半主机模式 */
void _sys_exit(int x)
{
    x = x;
}

char *_sys_command_string(char *cmd, int len)
{
    return NULL;
}


/* FILE 在 stdio.h里面定义. */
FILE __stdout;

/* MDK下需要重定义fputc函数, printf函数最终会通过调用fputc输出字符串到串口 */
int fputc(int ch, FILE *f)
{
    while ((USART6->SR & 0X40) == 0);     /* 等待上一个字符发送完成 */

    USART6->DR = (uint8_t)ch;             /* 将要发送的字符 ch 写入到DR寄存器 */
    return ch;
}
#endif
/******************************************************************************************/
```

注意在`fputc`函数中使用的是USART6，如果不是使用这个串口，就需要更改。

在`usart.h`文件中加入头文件

```c
#include "stdio.h"
```



## 电子调速器

链接：

## 问题

### printf输出乱码

链接：http://t.csdnimg.cn/xQjY2

原因有两个：

* 波特率设置不对
* 时钟频率不正确

高速/低速外部晶振大小？

### HAL_Delay卡死

链接：http://t.csdnimg.cn/oss1j

仍未解决  

## PCB设计零基础入门课程

### 元器件的符号与封装

### PCB板的元素组成

* 导线
* 过孔
* 丝印：标记
* 焊盘

### PCB的生产过程

1. 开料、圆角、刨边

开料是把原始的覆铜板切割成能在生产线上制造的板子的过程，一般切割成40*50cm左右的工作板

2. 钻孔

这时候孔里面是没有铜的

3. 沉铜

钻孔后的PCB板在沉铜缸内发生氧化还原反应，形成铜层从而对孔进行孔金属化，使原来绝缘的基材表面沉积上铜

4. 压膜

压膜后的电路板上压了一层蓝色的干膜，干膜是一个载体，在电路工序中很重要，干膜制程也因它而得名

5. 曝光

先将线路菲林跟压好干膜的电路板对好位，然后放在曝光机上，进行曝光，干膜在曝光机灯管的能量，把线路菲林没有线路的地方进行充分曝光。

经过这步后，线路就转移到了干膜上，此时的状态是，干膜有线路的地方没有被曝光，没有线路的地方则被曝光

6. 显影

用显影机里的显影液把没有被曝光的部分给显影掉，显影液对被曝光的部分是不起反应的。所以最终做出来的图片是线路部分出现了黄色铜，而没有线路的部分则还是蓝色（被曝光过的干膜）

7. 电铜

把板子放进电铜设备里，有铜的部分被电上了铜，被干膜挡住的部分则没有反应

8. 电锡

去掉那部分被干膜保护的铜

9. 退膜

即退掉蓝色干膜。因为线路部分已经有锡了，只需用一种退膜液，对曝光过的干膜起反应，放在退膜机中，很容易干膜就退掉了

10. 蚀刻

未经曝光的干膜被显影液去除后会露出铜面，蚀刻就是用药水（对铜起反应，对锡没作用）腐蚀掉电路板中不要的铜，留下需要的部分

11. 退锡

退锡是用一种药水退掉线路上的锡，使线路回到本色——铜

12. 光学AOI线路扫描

13. 印阻焊油

将板子上所有地方都印上阻焊油（包括焊盘）

14. 阻焊曝光、显影

目的就是为了把焊盘等地方的阻焊油去掉。

15. 字符（烤板）

在电路板上印上器件的位置号、板名等字符

16. 表面处理
17. 锣边成型
18. 电测
19. FQC
20. 终检、抽测、包装

### GD32F103C8T6核心板实操工程

绘制引脚时灰色圆圈代表是与外界相连的，另一侧是与所绘制的器件相连接的。

引脚名称可以根据需要进行修改，但是引脚编码就不能改变。

导线与线是不同的，线是没有电气性能的。

原理图转为PCB的前提是每个元器件都绑定了封装。

顶层阻焊层就是要把这个区域内的绿油去掉。

如果是自己绘制的元器件，没有绑定封装，可以在封装管理器中根据位号对其进行封装的绑定。

布局的核心思想是模块化布局

预布局——把每个模块的位置确定下来

精细化布局——把每个模块内部的布局再完善

滤波电容按照先大后小排列，即使从VCC开始，先经过大电容再经过小电容

设置设计规则：

一般的信号线没有这么大的电流，线宽一般设置成6mil

差分信号线的长度应尽可能一致，如果是高速信号，还需要考虑间距

钝角走线，不允许出现直角和锐角

晶振周围需要包地，以隔绝外界对晶振的干扰，还可以在包地的基础上打一些过孔

线宽不能够超出焊盘的宽度

走线走底层是备选方案，能走顶层就走顶层

导线尽量横平竖直，斜的部分尽可能少一点

对于电源部分，所需要的导线宽度更宽，或者可以使用铺铜

对于铺铜，如果是手工焊接，选择十字连接，如果是机械焊接，选择全连接。因为全连接的话铺铜面积大，手工焊接不容易升温

在空余的地方打一些过孔，增强顶层与底层的连接

增加泪滴，即所有导线与焊盘的连接都添加了圆弧过渡

### 立创EDA使用技巧

布局——属性位置——中间



## 硬件基础

课程：

* [硬件基础课程（持续更新中......）_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1gu4y1b7RS/?spm_id_from=333.880.my_history.page.click&vd_source=ae7834082973f295d9d56373ae0e7e3e)
* [硬件工程师90天课程158合集_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1qc411v7Ns/?spm_id_from=333.788.recommend_more_video.0&vd_source=ae7834082973f295d9d56373ae0e7e3e)
* 

### 振荡器

## MDK5开发

### 调试

首先需要知道下面这7个标志的含义：

![image-20240607121622526](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240607121622526.png)

* 第1个图标是复位调试
* 第2个图标是全速运行
* 第3个图标是进入全速运行状态后，通过这个图标可以停止全速运行
* 第4个图标是是Step，单步调试，每次点击运行一行代码
* 第5个图标是Step Over，每次点击以函数为单位运行，不会进入函数内部
* 第6个图标是Step Out，点击后退出当前运行的函数，执行下一个函数
* 第7个图标是Run to Cursor Line，直接运行到用户设置的行

# 电子电路学习

🔗：[电子电路_Leung_ManWah的博客-CSDN博客](https://blog.csdn.net/qq_36347513/category_11309024.html)

## 滤波电容

### 电感滤波与电容滤波

电感的阻抗与频率成正比，电容的阻抗与频率成反比。所以，电感可以阻遏高频通过，电容可以阻遏低频通过。电容和电感的很多特性是恰恰相反的。二者适当组合，就可以过滤各种频率信号。如在整流电路中，将电容并在负载上或将电感串联在负载上，可滤去交流纹波。

* 电容滤波：属电压滤波，是直接存储脉动电压来平滑输出电压，输出电压高，接近交流电压峰值；适用于小电流，电流越小滤波效果越好。
* 电感滤波：属电流滤波，是靠通过电流产生电磁感应来平滑输出电流，输出电压低，低于交流电压有效值；适用于大电流，电流越大滤波效果越好。

## 晶振

晶振是数字电路的心脏，因为所有的数字电路都需要一个频率高度稳定的工作时钟信号，为电路的工作提供时序基准，使各个模块的工作能够有条不紊的进行下去。而LC振荡器稳定性较差，频率容易漂移（即产生的交流信号频率容易变化），所以最常见的就是用晶振解决。

在振荡器中采用一个特殊的元件——石英晶体，可以产生高度稳定的信号，这种采用石英晶体的振荡器称为晶体振荡器。

## 晶振电路的电容

### 匹配电容

无源晶振电路中不只是有一个晶振，为了满足谐振条件让晶振起振正常工作，通常还有两个电容，两个电容一般称为“匹配电容”或者“谐振电容”。一般外接的这两个电容是为了使晶振两端的等效电容等于或接近于负载电容（晶振的负载电容是已知的，在出厂时已经定下来了，一般是几十pF）。

要求高的场合还要考虑IC输入端的对地电容。一般晶振两端所接电容是所要求的负载电容的两倍。这样并联起来就接近负载电容了。

电容值的大小影响谐振频率（也就是会发生频偏），一般情况下，增大电容会使震荡频率下降，减小电容会使震荡频率升高。

### 负载电容

晶振有一个重要的参数，即负载电容CL，它是电路中跨接晶体两端的总的有效电容（不是晶振外接的匹配电容），主要影响负载谐振频率和等效负载谐振电阻，与晶体一起决定振荡器电路的工作频率，通过调整负载电容，就可以将振荡器的工作频率调到标称值。



# CAN通信学习

## CAN总线特点

🔗：[【经验分享】STM32中CAN总线接口发送和接收数据 - STM32团队 ST意法半导体中文论坛 (stmicroelectronics.cn)](https://shequ.stmicroelectronics.cn/thread-633794-1-1.html#:~:text=CAN通讯节点由一个CAN控制器及CAN收发器组成，控制器与收发器之间通过CAN_Tx及CAN_Rx信号线相连，收发器与CAN总线之间使用CAN_High及CAN_Low信号线相连。,其中CAN_Tx及CAN_Rx使用普通的类似TTL逻辑信号，而CAN_High及CAN_Low是一对差分信号线，使用比较特别的差分信号。 当CAN节点需要发送数据时，控制器把要发送的二进制编码通过CAN_Tx线发送到收发器，然后由收发器把这个普通的逻辑电平信号转化成差分信号，通过差分线CAN_High和CAN_Low线输出到CAN总线网络。)

* CAN总线网络是一种真正的多主机网络，在总线处于空闲状态时，任何一个节点单元都可以申请成为主机，向总线发送消息。其原则是：最先访问总线的节点单元可以获得总线的控制权；多个节点单元同时尝试获取总线的控制权时，将发生仲裁事件，具有高优先级的节点单元将获得总线控制权。
* CAN协议中，所有的消息都以固定的数据格式打包发送。两个以上的节点单元同时发送消息时，根据节点标识符（常称为ID，亦打包在固定的数据格式中）决定各自优先级关系，所以ID并非表示数据发送的目的地址，而是代表着各个节点访问总线的优先级。

🔗：江协科技CAN总线入门教程

## CAN硬件电路

* 每个设备通过CAN收发器挂载在CAN总线网络上
* CAN控制器引出的TX和RX与CAN收发器相连，CAN收发器引出的CAN_H和CAN_L分别与总线的CAN_H和CAN_L相连
* 高速CAN使用闭环网络，CAN_H和CAN_L两端添加120Ω的终端电阻
* 低速CAN使用开环网络，CAN_H和CAN_L其中一端添加2.2kΩ的终端电阻

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240623164224195.png" alt="image-20240623164224195" style="zoom: 67%;" />

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240623164356085.png" alt="image-20240623164356085" style="zoom:67%;" />

## CAN电平标准

* CAN总线采用差分信号，即两线电压差传输数据位
* 高速CAN规定：电压差为0V时表示逻辑1（隐性电平）；电压差为2V时表示逻辑0（显性电平）
* 低速CAN规定：电压差为-1.5V时表示逻辑1（隐性电平）；电压差为3V时表示逻辑0（显性电平）

## CAN总线帧格式

* 数据帧：发送设备主动发送数据（广播式）
* 遥控帧：接收设备主动请求数据（请求式）
* 错误帧：某个设备检测出错误时向其他设备通知错误
* 过载帧：接收设备通知其尚未做好接收准备
* 帧间隔：用于将数据帧及遥控帧与前面的帧分离开

![image-20240624111812621](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240624111812621.png)

注意：

* 并不是发送方把一段波形完整发出去，然后再接收应答的，而是，发送方和接收方共同完成一整个波形，发送方每发出一位，接收方就立刻收到这一位了。所以在这条时序的最后，整个数据帧还没结束，接收方其实已经收完了

数据帧各部分用途简介

* SOF：帧起始，表示后面一段波形为传输的数据位
* ID：标识符，区分功能，同时决定优先级
* RTR：远程请求位，区分数据帧和遥控帧
* IDE：扩展标志位，区分标准格式和扩展格式
* SRR：替代RTR，协议升级时留下的无意义位
* r0/r1：保留位，为后续协议升级留下空间
* DLC：数据长度，指示数据段有几个字节
* Data：数据段的1~8个字节有效数据
* CRC：循环冗余校验，检验数据是否正确
* ACK：应答位，判断数据有没有被接收方接收
* CRC/ACK界定符：为应答位前后发送方和接收方释放总线留下时间
* EOF：帧结束，表示数据位已经传输完毕

## 位填充

* 位填充规则：发送方每发送5个相同电平后，自动追加一个相反电平的填充位。接收方检测到填充位时，会自动移除填充位，恢复原始数据

位填充作用：

* 增加波形的定时信息，利用接收方执行“再同步”，防止波形长时间无变化，导致接收方不能精确掌握数据采样时机（长时间一样的波形，容易导致接收出错）
* 将正常数据流与“错误帧”和“过载帧”区分开，标志“错误帧”和“过载帧”的特异性
* 保持CAN总线在发送正常数据流时的活跃状态，防止被误认为总线空闲

## 接收方数据采样

* CAN总线没有时钟线，总线上的所有设备通过约定波特率的方式确定每一个数据位的时长
* 发送方以约定的位时长每隔固定时间输出一个数据位
* 接收方以约定的位时长每隔固定时间采样总线的电平，输入一个数据位
* 理想状态下，接收方能依次采样到发送方发出的每个数据位，且采样点位于数据位中心附近

接收方数据采样遇到的问题：

* 接收方以约定的位时长进行采样，但是采样点没有对齐数据位中心附近
* 接收方刚开始采样正确，但是时钟有误差，随着误差积累，采样点逐渐偏离

## 位时序

在一个数据位的波形中，采样点式处于两次跳变沿之间的，且采样点可以灵活地往前或者往后进行调整，这样才能满足我们同步时，调节采样点位置的需求。所以我们需要对一个数据位的时间进行进一步的细分。

为了灵活调整每个采样点的位置，使采样点对齐数据位中心附近，CAN总线对每一个数据位的时长进行了更细的划分，分为同步段（SS）、传播时间段（PTS）、相位缓冲段1（PBS1）和相位缓冲段2（PBS2），每个段又由若干个最小时间单位（Tq）构成。

## 硬同步

硬同步所要解决的问题就是使接收方第一个采样点与波形的第一位对齐

* 每个设备都有一个位时序计时周期，当某个设备（发送方）率先发送报文，其他所有设备（接受方）收到SOF的下降沿时，接收方会将自己的位时序计时周期拨到SS段的位置，与发送方的位时序计时周期保持同步
* 硬同步只在帧的第一个下降沿（SOF下降沿）有效
* 经过硬同步后，若发送方和接收方的时钟没有误差，则后续所有数据位的采样点必然都会对齐数据位中心附近

## 再同步

在实际情况中，每个设备的秒表可能都有误差，经过一次初始的对表后，时间久了难免会出现秒表旋转不同步的情况，就会导致采样点逐渐偏移的问题，而再同步的目的就是补偿误差。

* 若发送方或接收方的时钟有误差，随着误差积累，数据位边沿逐渐偏离SS段，则此时接收方根据再同步补偿宽度值通过加长PBS1段，或缩短PBS2段，以调整同步
* 再同步可以发生在第一个下降沿之后的每个数据位跳变边沿

## 仲裁

多设备同时发送遇到的问题：

* CAN总线只有一对差分信号线，同一时间只能有一个设备操作总线发送数据，若多个设备同时有发送需求，该如何分配总线资源？
* 解决问题的思路：制定资源分配规则，依次满足多个设备的发送需求，确保同一时间只有一个设备操作总线。

资源分配规则1——先占先得

* 若当前已经有设备正在操作总线发送数据帧/遥控帧，则其他任何设备不能再同时发送数据帧/遥控帧（可以发送错误帧/过载帧破坏当前数据）
* 任何设备检测到连续11个隐性电平，即认为总线空闲，只有在空闲时，设备才能发送数据帧/遥控帧
* 一旦有设备正在发送数据帧/遥控帧，总线就会变为活跃状态，必然不会出现连续11个隐性电平，其他设备自然也不会破坏当前发送
* 若总线活跃状态其他设备有发送需求，则需要等待总线变为空闲，才能执行发送需求。

资源分配规则2——非破坏性仲裁

* 若多个设备的发送需求同时到来或因等待而同时到来，则CAN总线协议会根据ID号（仲裁段）进行非破坏性仲裁，**ID号小的（优先级高）取到总线控制权，ID号大的（优先级低）仲裁失利后将转入接收状态**，等待下一次总线空闲时再尝试发送（ID号越小，其二进制数据的1出现的就越晚，ID号越大，1出现的就越早）
* 实现非破坏性仲裁需要两个要求：（1）线与特性：总线上任何一个设备发送显性电平0时，总线就会呈现显性电平0状态，只有当所有设备都发送隐性电平1时，总线才呈现隐性电平1状态；回读机制：每个设备发出一个数据位后，都会读回总线当前的电平状态，以确认自己发出的电平是否被真实地发送出去了，根据线与特性，发出0读回必然式0，发出1读回不一定是1

注意事项：

* 在仲裁场里，会执行位填充，位填充插入的位，也会参与仲裁，但是插入的这些填充位并不会影响仲裁，也不会改变原有ID号的优先级
* 数据帧和遥控帧ID号一样时，数据帧的优先级高于遥控帧
* 标准格式11位ID号和扩展格式29位ID号的高11位一样时，标准格式的优先级高于扩展格式（SRR必须始终为1，以保证此要求）

# 自动控制原理

## 学习路线

1. 基础理论学习：了解自动控制的基本概念，比如开环控制、闭环控制、稳定性、系统动态等。
2. 数学基础：自动控制算法通常设计复杂的数学，特别是微分方程和线性代数。
3. 经典控制理论：开始学习PID控制算法，这是最基本也是最常用的控制算法之一。
4. 现代控制理论：在掌握了经典控制理论之后，可以进一步学习状态空间表示、传递函数、能控性和能观测性等现代控制理论的概念。
5. 特定算法学习：在有了一定的基础之后，可以开始学习模糊控制、导纳控制、模型预测控制等更高级的控制算法。
6. 实践应用：理论知识需要通过实践来巩固。尝试在仿真软件中实现不同的控制算法，并观察它们在不同系统上的表现。
7. 案例研究：阅读和分析实际工程案例，了解这些控制算法是如何在实际应用中被设计和调整的。
8. 持续学习
9. 软件工具学习：熟悉一些常用的控制算法设计和仿真软件。
10. 项目经验：如果可能的话，参与实际的控制工程项目。

## PID算法入门

🔗：《DMF407电机控制专题教程》

PID算法是闭环控制系统中常用的算法，PID分别是比例、积分、微分的首字母缩写。它是一种结合比例、积分和微分三个环节于一体的闭环控制算法，具体的控制流程如下图所示：

![image-20240721234722906](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240721234722906.png)

我们将输入目标值和实际输出值进行偏差的计算，然后把计算结果输入到PID控制算法中，经过比例、积分和微分三个环节的运算，运算后的输出作用于执行器，从而让系统的实际值逐渐靠近目标值。

### 比例环节

比例环节可以成比例地反映控制系统的偏差信号，即输出于输入偏差成正比，可以用来减小系统的偏差。此环节的公式如下：
$$
u=K_p · e
$$
其中，$u$——输出，$K_p$——比例系数，$e$——偏差。

![image-20240722093031169](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240722093031169.png)

当$K_p$的值越大时，其对应的橙色曲线达到目标值的时间就越短，与此同时，橙色曲线出现了一定幅度的超调和振荡，这会使得系统的稳定性下降，因此，**我们在设置比例系数的时候，并不是越大越好，而是要兼顾消除偏差的时间以及整个系统的稳定性**。

然而，在实际的应用中，如果仅有比例环节的控制，可能会给系统带来一个问题：**静态误差**。静态误差是指系统控制过程趋于稳定时，目标值与实测值之间的偏差。

![image-20240722093349596](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240722093349596.png)

大家可能会想到，我们可以通过增大$K_p$来增大输出，以此消除偏差。在实际应用中，此方法的局限性很大，因为我们不能确定偏差的大小，它是在实时变化的，如果我们把$K_p$设置得太大，就会引入超调和振荡，让整个系统的稳定性变差。因此，为了消除静态误差，我们引入了积分环节。

### 积分环节

积分环节可以对偏差进行积分，只要存在偏差，积分环节就会不断起作用，主要用于消除静态误差，提高系统的无差度。引入积分环节后，比例+积分环节的公式如下：
$$
u = K_p · e + K_i · \sum e
$$
![image-20240722115007259](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240722115007259.png)

当$K_i$的值越大时，其对应的橙色曲线达到目标值的时间就越短，与此同时，橙色曲线出现了一定幅度的超调和振荡，这会使得系统的稳定性下降，因此，**我们在设置积分系数时，并不是越大越好，而是要兼顾消除静态误差的时间以及整个系统的稳定性**。

我们之前有说过，只要系统还存在偏差，积分环节就会不断地累积偏差。当系统偏差为0的时候，说明已经达到目标值，此时的累计偏差不再变化，但是积分环节依旧在发挥作用（此时往往作用最大），这就很容易产生超调的现象了。因此，我们需要引入微分环节，提前减弱输出，抑制超调的发生。

### 微分环节

微分环节可以反映偏差量的变化趋势，根据偏差的变化量提前作出相应控制，减小超调，克服振荡。引入微分环节后，比例+积分+微分的公式如下：
$$
u_k = K_p · e_k + K_i \sum_{j=0}^{k} e_j +K_d(e_k - e_{k-1})
$$
该公式是PID离散公式之一，除了离散公式之外，PID还有连续的公式，但是因为连续的公式不利于机器计算。

在实际的应用中，并不是每一个系统都需要PID三个环节参与控制的，有的系统只需要比例环节或积分环节就可以控制得很好。

### PID算法离散公式

#### 位置式PID公式

$$
u_k = K_p · e_k + K_i \sum_{j=0}^k e_j + K_d(e_k - e_{k-1})
$$

我们在上一小节中得到的PID离散公式称为位置式或全量式PID公式，**该公式的计算需要全部控制量参与，它的每一次输出都和过去的状态有关**。

#### 增量式PID公式

通过位置式的PID公式，我们只需两步即可推导出增量式PID公式：

* 第一步，将k=k-1代入位置式PID公式，得：

$$
u_{k-1} = K_p · e_{k-1} + K_i \sum_{j=0}^{k-1} e_j + K_d(e_{k-1} - e_{k-2})
$$

* 第二步，由$u_k - u_{k-1}$得：

$$
\Delta u_k = K_p (e_k - e_{k-1}) + K_i · e_k + K_d (e_k -2e_{k-1} +e_{k-2})
$$

至此，增量式PID公式就推导完了。从公式中可以看出，**增量式PID的计算并不需要一直累计偏差，它的输出与近三次的偏差有很大关系**。

#### 两种PID公式的优缺点

* 位置式：

优点：位置式PID是一种非递推式算法，带有积分作用，适用于不带积分部件的对象。

缺点：全量计算，计算错误影响很大；需要对偏差进行累加，运算量打。

* 增量式：

优点：只输出增量，计算错误影响小；不需要累计偏差，运算量少，实时性相对较好。

缺点：积分截断效应大，有稳态误差。

### 积分饱和问题

在位置式PID中，如果系统长时间无法达到目标值，累计偏差（积分）就会变得很大，此时系统的响应就很慢。

为了避免位置式PID中可能出现的积分饱和问题，可采取以下措施：

1. 优化PID曲线，系统越快达到目标值，累计的偏差就越小；
2. 限制目标值调节范围，规避可以预见的偏差；
3. 进行积分限幅，在调整好PID系数之后，根据实际系统来选择限幅范围。

### PID参数整定

#### 采样周期选择

采样周期指的是PID控制中实际值的采样时间间隔，其越短，效果就越趋于连续，但对硬件资源的占用也越高。在实际的应用中，我们可以使用理论或者经验方法来确定采样周期：

* 理论方法：香农采样定理。这个定理可以用来确定采样周期可选择的最大值，当采样周期超出了这个最大的允许范围，我们所得到的信号就会失真，也就无法较好地还原信号了。
* 经验方法：根据控制对象突变能力选择。假设电机当前转速为20RPM，我们需要提高它的转速到30RPM，此电机的转速在1s之内最大可以突变10RPM（即电机速度的突变能力），如果我们每1ms采集以此电机转速，那么每一次采集到的速度变化量最大为10RPM/1000=0.01RPM，很明显，此时最大的变化量远远小于当前的速度，这对于我们的PID控制效果并没有明显的提升，但是却占用了很多的硬件资源，因此，我们需要根据控制对象的突变能力来选择采样周期。

#### PID参数整定方法

我们了解一下PID各个系数调节的效果，这样才能做到在PID调参中有的放矢。

* 比例系数：调节作用快，系统一出现偏差，调节器立即将偏差放大输出。
* 积分系数：积分系数的调节会改变输入偏差对于系统输出的影响程度。积分系数越大，消除静差的时间就越短，但是过大的积分系数则会导致系统出现超调现象，这在具有惯性的系统中尤为明显。
* 微分系数：微分系数的调节是偏差变化量对于系统输出的影响程度。微分系数越大，系统对于偏差量的变化越敏感，越能提前响应，进而抑制超调，但是过大的微分系数则会让整个系统出现振荡。

# C语言语法

## 基本篇

### 基本语法

C程序由各种令牌（Token）组成，令牌可以是关键字、标识符、常量、字符串值，或者是一个符号。

C语言中有两种类型转换：

* 隐式类型转换：在表达式中自动发生的，无需进行任何明确的指令或函数调用。它通常是将一种较小的类型自动转换为较大的类型。隐式类型转换也可能会导致数据精度丢失或数据截断。
* 显式类型转换：显式类型转换需要使用强制类型转换运算符，它可以将一个数据类型的值强制转换为另一种数据类型的值。强制类型转换可以使程序员在必要时对数据类型进行更精确的控制，但也可能导致数据丢失或截断。

### 数据类型

🔗：http://t.csdnimg.cn/OnBq3

```c
stdint.h  // 这里放着C语言的标准表达方式
 
typedef   signed        char      int8_t; 
typedef   signed short  int       int16_t;
typedef   signed        int       int32_t;
typedef   signed      __int64     int64_t;
 
typedef unsigned           char       uint8_t;
typedef unsigned short     int        uint16_t;
typedef unsigned           int        uint32_t;
typedef unsigned         __int64      uint64_t;
 
stm32f10x.h 这个文件主要是为了兼容旧版本
 
typedef   uint32_t   u32;   ///32位
typedef   uint16_t   u16;   ///16位
typedef   uint8_t     u8;   ///8位
```

### 变量定义

变量定义就是高速编译器在何处创建变量的存储，以及如何创建变量的存储。

在C语言中，如果变量没有显式初始化，那么它的默认值将取决于该变量的类型和其所在的作用域。

对于全局变量和静态变量（在函数内部定义的静态变量和在函数外部定义的全局变量），它们的默认初始值为零

#### 全局变量与局部变量

链接：[C/C++ 中 static 的用法全局变量与局部变量 | 菜鸟教程 (runoob.com)](https://www.runoob.com/w3cnote/cpp-static-usage.html)

**static的作用**

* 在修饰变量时，static修饰的静态局部变量只执行初始化依次，而且延长了局部变量的生命周期，直到程序运行结束以后才释放。
* static修饰全局变量时，这个全局变量只能在本文件访问，不能在其他文件中访问，即便是用extern外部声明也不可以。
* static修饰一个函数，则这个函数只能在本文件中调用，不能被其他文件调用。static修饰的变量存放在全局数据区的静态变量区，包括全局静态变量和局部静态变量，都在全局数据区分配内存。初始化时自动初始化为0。
* 不想被释放的时候，可以使用static修饰。比如修饰函数中存放在栈空间的数组。如果不想让这个数组在函数调用结束释放可以使用static修饰。
* 考虑到数据安全性，当需要使用全局变量时应优先考虑使用static。

**全局变量与全局静态变量的区别**

* 全局变量是不显式用static修饰的全局变量，全局变量默认是有外部链接性的，作用域是整个工程，在一个文件内定义的全局变量，在另一个文件中通过extern全局变量名的声明，就可以使用全局变量。
* 全局静态变量是显式用static修饰的全局变量，**作用域是声明此变量所在的文件**，其他的文件即使用extern声明也不能使用。

### 常量定义

#### #define与const区别

#define与const这两种方式都可以用来定义常量，选择哪种方式取决于具体的需求和编程习惯。通常情况下，建议使用const关键字来定义常量，因为它具有类型检查和作用域的优势，而#define仅进行简单的文本替换，可能会导致一些意外的问题。

#define预处理指令和const关键字在定义常量时有一些区别：

* 替换机制：#define是进行简单的文本替换，而const是声明一个具有类型的常量。#define定义的常量在编译时会被直接替换为其对应的值，而const定义的常量在程序运行时会分配内存，并且具有类型信息。
* 类型检查：#define不进行类型检查。而const定义的产量具有类型信息，编译器可以对其进行类型检查。这可以帮助捕获一些潜在的类型错误。
* 作用域：#define定义的常量没有作用域限制，它在定义之后的整个代码中都有效。而const定义的常量具有块级作用域，只在其定义所在的作用域内有效。
* 调试和符号表：使用#define定义的常量在符号表中不会有相应的条目，因为它只是进行文本替换。而使用const定义的常量会在符号表中有相应的条目，有助于调试和可读性。

### 堆栈

栈（stack）空间，用于局部变量，函数调用时现场保护和返回地址，函数的形参等

堆（heap）空间，主要用于动态内存分配，也就是说用malloc，calloc，realloc等函数分配的变量空间是在堆上。

### 存储类

存储类定义C程序中变量/函数的存储位置、生命周期和作用域。

* auto
* register
* static
* extern
* 

### 弱定义

### volatile

链接：[C语言丨深入理解volatile关键字 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/343688629)

`volatile`是一个类型修饰符，它是被设计用来修饰被不同线程访问和修改的变量。

如果没有`volatile`，基本上会导致这样的结果：要么无法编写多线程程序，要么编译器失去大量优化的机会。

#### 原理作用

`volatile`提醒编译器它后面所定义的变量随时可能改变，因此编译后的程序每次需要存储或读取这个变量的时候，告诉编译器对该变量不做优化，都会直接从变量内存地址中读取数据，从而可以提供对特殊地址的稳定访问。

如果没有volatile关键字，则编译器可能优化读取和存储，可能暂时使用寄存器中的值，如果这个变量由别的程序更新了的话，将出现不一致的现象。

也就是说，**volatile关键词影响编译器编译的结果，用volatile声明的变量表示该变量随时可能发生变化，与该变量有关的运算，不要进行编译优化，以免出错**。

#### 一般用处



### memset

链接：http://t.csdnimg.cn/lBk2J

函数原型

```C
void *memset(void *str, int c, size_t n)
```

## 进阶篇

### 函数指针与指针函数

🔗：[C语言指针进阶（一）——深入详解“函数指针”与“指针函数”-CSDN博客](https://blog.csdn.net/qq_27825451/article/details/103081289)

所谓**函数指针**即定义一个指向函数的指针变量，定义的格式如下：

```c
int (*p)(int x, int y); // 注意这里的括号不能掉，因为括号的运算优先级比解引用运算符*高
```

我们一般可以这么使用，通过函数指针调用函数：

```c
int maxValue (int a, int b) {
    return a > b ? a : b;
}    
 
int (*p)(int, int) = NULL;  //定义一个与maxValue兼容的指针
p = maxValue;
p(20, 45);  //通过指针调用
```

**指针函数**指的是函数的返回值是一个指针，比如我的函数返回的是一个指向整数int的指针，定义格式如下：

```c
int *p(int a, int b); // 注意这里的*与p之间是没有括号的，所以含义是函数p(int, int)会返回一个(int *)
```

总结如下：

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240721103637017.png" alt="image-20240721103637017" style="zoom: 50%;" />

函数回调本质为函数指针作为函数参数，函数调用时传入函数地址，这使我们的代码变得更加灵活，可复用性更强。

函数指针作为函数参数很简单，我们只要能知道函数指针的类型即可，一般格式如下：

```c
void MyFunction(..., int (*p)(int,int),...)
```

###  __I、 __O、__IO的意义

🔗：[__I、 __O 、__IO是什么意思？怎么用？_寄存器中i是什么意思-CSDN博客](https://blog.csdn.net/qq_27312943/article/details/51273064)

这是ST库里面的宏定义，定义如下：

```c
#ifdef __cplusplus
  #define   __I     volatile             /*!< Defines 'read only' permissions */
#else
  #define   __I     volatile const       /*!< Defines 'read only' permissions */
#endif
#define     __O     volatile             /*!< Defines 'write only' permissions */
#define     __IO    volatile             /*!< Defines 'read / write' permissions */
```

显然，这三个宏定义都是用来替换成volatile和const的，所以我们先要了解这两个关键字的作用。

volatile简单来说，就是不让编译器进行优化，即每次读取或者修改值得时候，都必须重新从内存或者寄存器中读取或者修改。

一般来说，volatile用在如下的几个地方：

* 中断服务程序中修改的供其他程序检测的变量需要加volatile
* 多任务环境下各任务间共享的标志应该加volatile
* 存储器映射的硬件寄存器通常也要加volatile说明，因为每次对它的读写都可能有不同意义

### 内存四区

🔗：[C语言：内存四区_ram内存分区-CSDN博客](https://blog.csdn.net/qq_45396672/article/details/119155585)



### 动态内存的分配

🔗：[【C语言】动态内存的分配 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/462936499)

平常我们定义的数组，都是在栈区分配的空间，都是分配的空间都是固定的大小

这种分配固定大小的内存分配方法称之为静态内存分配

与静态内存相对的，就是可以控制内存的分配的动态内存分配

注意：这里动态内存分配的空间是在堆区申请的，不是在栈区申请的

![img](https://pic2.zhimg.com/80/v2-866cee81b090c424b2d9d374fcb4dfe9_720w.webp)

动态内存的优势：

* 可以控制内存的大小
* 可以多次利用这部分空间：静态内存分配利用的空间，不会主动释放，只有当这个程序结束后，才会主动归还给系统。而动态内存分配的空间，可以通过利用完，就可以free这块申请的空间。当再次用动态内存申请空间时，就可以再次利用这块空间。
* 不占用栈区的内存

# 数据处理

## 低通滤波、高通滤波以及带通滤波



# STM32基于HAL库

## GPIO

🔗：[STM32 GPIO详细篇（基于HAL库） - 东小东 - 博客园 (cnblogs.com)](https://www.cnblogs.com/dongxiaodong/p/14128088.html)

### 模式汇总

输入模式：

* 浮空输入：引脚电平是真实的外部连接器件，电平具有不确定性
* 上拉输入：默认通过电阻上拉到VCC，不接外部器件时可以读出高电平
* 下拉输入：默认通过电阻下拉到GND，不接外部器件时可以读出低电平
* 模拟输入：将外部信号直接传输到数模转换通道上

输出模式：

* 开漏输出：只能输出低电平，高电平由电阻上拉决定
* 开漏复用功能：用于外设功能使用
* 推挽式输出：可以输出强高和强低，通常使用该功能控制LED
* 推挽式复用功能：用于外设功能使用

## DMA

🔗：[STM32 | DMA配置和使用如此简单（超详细）_tc3xx dma数据错位-CSDN博客](https://blog.csdn.net/weixin_44524484/article/details/105671273)

STM32最多有2个DMA控制器（DMA2仅存在大容量产品中），12个独立的可配置的通道，DMA1有7个通道，DMA2有5个通道。

每个通道专门用来管理来自于一个或多个外设对存储器访问的请求。还有一个仲裁器来协调各个DMA请求的优先级。

DMA主要特征

* 每个通道都直接连接专用的硬件DMA请求，每个通道都同样支持软件触发

## RS485

**梳理**：串口、UART、TTL、RS232、RS422、RS485关系

串口是一个泛称，UART、RS232、RS422、RS485都遵循类似的通信时序协议，被统称为串口。

通信时序协议：

* 启动位
* 有效数据位
* 校验位
* 停止位

UART是STM32的外设，由此产生串口时序，产生的电平为CMOS电平。

TTL、RS232、RS422、RS485是串行通信接口标准。简单来说，就是逻辑1和0的表示不同。

RS485是串行通信标准，使用差分信号传输，抗干扰能力强，常用于工控领域。

RS485具有强大的组网功能，在串口基础协议之上还制定MODBUS协议。



## F4系列

## G4系列



## H7系列

🔗：《安富莱_STM32-V7开发板》

### 第1章 初学STM32H7的准备工作

#### H7和F1、F4系列的区别

* 最大的区别是H7读了一个L1 Cache一级缓存，这个缓存在为低速存储器带来加速的同时，也为程序设计带来了一些问题，其中最为主要的是数据一致性问题。
* STM32H7的自带外设比较之前的任何STM32型号都要生猛，算是大换血了，换了ADC，DMA，USART等重要外设，性能比之前要强劲很多。比如ADC换成了3.6Msps16位分辨率，DMA支持任意互联了，USART也支持波特率自适应。
* 到了STM32H7系列，ST官方仅提供了HAL库，没有再提供标准库，而对于F1，F4系列，标准库和HAL库都是有的。
* F1是M3内核，F4是M4内核，而STM32H7是M7内核，从编程的角度来说，几乎没有区别。

### 高速缓存Cache

🔗：[SDRAM、DRAM及DDR FLASH ROM概念详解_dram和sdram-CSDN博客](https://blog.csdn.net/as480133937/article/details/123455890?spm=1001.2014.3001.5502)

🔗：[STM32H7---高速缓存Cache(一)_stm32h7 cache-CSDN博客](https://blog.csdn.net/as480133937/article/details/123663197?spm=1001.2014.3001.5502)

存储器是用来存储程序和各种数据信息的记忆部件。

* 许多存储单元的集合，按单元号顺序排列。每个单元由若干二进制位构成，以表示存储单元中存放的数值，这种结构和数组的结构非常相似。
* 存储器的单元地址只有一个，固定不变，而存储在其中的信息是可以更换的。

存储器按其存储介质特性主要分为“易失性存储器”和“非易失性存储器”两大类。其中的“易失性存储器”是指存储器断电后，它存储的数据内容是否会丢失的特性。由于“易失性存储器”存取速度快，而“非易失性存储器”可长期保存数据，它们都在计算机中占据着重要角色。在计算机中“易失性存储器”最典型的代表是内存，“非易失性存储器”的代表则是硬盘。

<img src="https://i-blog.csdnimg.cn/blog_migrate/9ad44ecc9b73eb00aca04f70e86c4c20.png" alt="在这里插入图片描述" style="zoom: 67%;" />

RAM，随机存取存储器，也叫主存，是与CPU直接交换数据的内部存储器。它可以随时读写，而且速度很快，通常作为操作系统或其他正在运行中的程序的临时数据存储介质。

ROM，只读存储器，只能读出，无法写入信息。信息一旦写入后就固定下来，即使切断电源，信息也不会丢失，所以又称为固定存储器。

RAM又分为静态随机访问存储器（Static Random Access Memory，**SRAM**）和动态随机存取存储器（Dynamic Random Access Memory，**DRAM**）两种

SRAM利用双稳态电路进行存储。即使有干扰，对稳态电路也没有影响。静态是指只要不掉电，存储在SRAM中的数据就可以一直保存。只要有电，SRAM中的数据就不会有变化。

DRAM需要不断的刷新，才能保存数据。主要的作用原理是利用电容内存储电荷的多少来代表一个二进制比特是1还是0。有电荷代表1，无电荷代表0。



# 达妙MC02电机开发板使用

## STM32H723VGT6最小系统

该开发板采用STM32H723VGT6芯片，带DSP和FPU的高性能系列ARM Cortex-M7的MCU，具有1MByte Flash、564Kbytes、ART加速器。开发板晶振采用24MHz无源晶振，并通过MCO1（PA8）给外接摄像头提供24MHz时钟。

![image-20240821120712191](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240821120712191.png)

## CAN配置

🔗：[STM32H7系列FDCAN配置成经典CAN的经验教程和注意事项 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/714301640?utm_id=0)

# STM32电机控制应用

## DMF407电机控制专题教程

### 基础篇

#### 代码规范

几个规范的关键点：

* 所有函数/变量名字非特殊情况，一般使用小写字母
* 注释风格使用doxgen风格，除屏蔽外，一律使用/**/方式进行注释
* TAB键统一使用4个空格对齐，不使用默认的方式进行对齐
* 每两个函数之间，一般有且只有一个空行
* 相对独立的程序块之间，使用一个空行隔开
* 全局变量命名一般使用 g_ 开头，全局指针命名一般用 p_ 开头
* if for while do case switch default等语句单独占一行，一般无论有多少行执行语句，都要加花括号

#### 硬件平台简介

#### 电机基础知识

#### 电机控制相关的STM32外设

##### 电机控制与STM32定时器的关系

电机的控制与STM32定时器有着密不可分的关系：在直流有刷电机的控制中，我们常用脉冲宽度调制技术PWM来控制电压的大小，以此改变直流有刷电机的转速。对于步进电机而言，接收的脉冲个数决定了它的旋转位置，脉冲频率决定了它的旋转速度。

从上面的例子中可以得知，电机的控制本质上就是**脉冲的控制**，因此，我们引入了STM32定时器，以便对脉冲信号实现更高效的控制。

接下来，我们就开始学习STM32定时器的功能，包括定时器中断、PWM输出、互补输出带死区刹车、输入捕获等。

##### 基本定时器

定时器中断配置步骤：

1. 使能定时器时钟

```c
__HAL_RCC_TIMx_CLK_ENABLE();
```

2. 初始化定时器参数，设置自动重装载值，分频系数，计数方式等

```
HAL_TIM_Base_Init();
```

3. 使能定时器更新中断，开启定时器计数，配置定时器中断优先级

```c
HAL_TIM_Base_Start_IT(); //使能定时器中断和开启定时器计数
HAL_NVIC_EnableIRQ(); // 使能定时器中断
HAL_NVIC_SetPriority(); // 设置中断优先级
```

4. 编写中断服务函数

```
HAL_TIMx_IRQHandler(); //定时器中断通用处理函数
```



##### 高级定时器

##### ADC

##### DAC



### 电机专题篇

#### 直流有刷电机编码器测速

##### 编码器简介

编码器是一种能将直线位移、角位移数据转换为脉冲信号、二进制编码的设备。它本质上就是一个传感器，可以把角位移或直线位移转换成电信号，并反馈给控制器，使控制器知道当前机械运动的位置、角度等信息。

**编码器的分类**：编码器的分类方式有很多，我们这里列举两种分类方式：按检测原理和编码类型。

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240730192808655.png" alt="image-20240730192808655" style="zoom: 50%;" />

编码器按照检测原理可以分为光电式和磁电式：按照编码类型可分为增量式和绝对式。在实际的应用中，这四类编码器并不是相对独立的，它们经过组合后，就变成了光电绝对式、光电增量式、磁电绝对式和磁电增量式这四种编码器。

**磁电增量式**

原理：利用霍尔效应，将位移转换成计数脉冲，用脉冲个数计算位移和速度。

![image-20240730193113199](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240730193113199.png)

磁电增量式编码器的结构包含：磁盘、霍尔传感器以及信号转换电路3个部分，其中，磁盘是由一个个交替排布的S极和N极磁极组成；霍尔传感器可以把磁场的变化转换成电信号的变化，它通常由A、B两相，这两相的安装位置形成一定的夹角，这使得输出的A、B两相信号有90°的相位差；信号转换电路可以把电信号转换成脉冲信号。

**光电增量式**

原理：利用光电系统，将位移转换成计数脉冲，用脉冲个数计算位移和速度。

**光电绝对式**

原理：当码盘处于不同位置（角度）时，光敏元件根据受光与否转换出相应的电平信号，最后转换成二进制数输出。

##### 编码器测速原理

本章节中我们使用的是磁电增量式编码器，它安装在直流有刷电机的尾部：

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240801170356913.png" alt="image-20240801170356913" style="zoom:50%;" />

##### 编码器测速实现



#### 直流有刷电机速度环控制实现

速度环PID控制的原理非常简单，我们只需要把PID控制流程中的控制对象换成电机速度即可。

![image-20240726224934248](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240726224934248.png)

在图中，我们先设置目标转速，系统会计算出偏差e，然后将偏差输入到PID控制的三个环节中，PID计算后的输出值用于控制PWM的占空比，进而控制电机的速度。

**速度环PID控制的配置步骤**

1. 配置相关定时器：配置基础驱动、编码器测速相关的定时器
2. 初始化串口：开启串口接收中断，串口1在PID控制代码中用于上位机通信
3. 定义PID参数结构体变量：为了方便管理PID相关的控制量，我们需要定义一个PID参数结构体变量
4. 初始化PID参数：把PID控制系统的目标速度值、期望输出值、累计偏差等清零，然后配置PID系数
5. 初始化上位机调试：调用debug_init函数初始化所需内存，为上位机的调试做准备
6. 编写中断服务函数：在定时器6的更新中断回调函数里面进行速度环PID计算，计算后的结果用于控制PWM的占空比

**程序解析**

首先我们看串口1的代码，该串口在PID控制代码中用于上位机通信。串口1中断服务函数具体定义如下：

```c
void USART_UX_IRQHandler(void)
{ 
    uint8_t res;

    if ((__HAL_UART_GET_FLAG(&g_uart1_handle, UART_FLAG_RXNE) != RESET)) /* 接收到数据 */
    {
        HAL_UART_Receive(&g_uart1_handle, &res, 1, 1000);
        debug_handle(&res);
    } 
}
```

该函数非常简单，当上位机有数据下发时，我们直接调用debug_handle函数来解析上位机下发的数据。

PID初始化函数定义如下：

```c
void pid_init(void)
{
    g_speed_pid.SetPoint = 0;       /* 设定目标值 */
    g_speed_pid.ActualValue = 0.0;  /* 期望输出值 */
    g_speed_pid.SumError = 0.0;     /* 积分值 */
    g_speed_pid.Error = 0.0;        /* Error[1] */
    g_speed_pid.LastError = 0.0;    /* Error[-1] */
    g_speed_pid.PrevError = 0.0;    /* Error[-2] */
    g_speed_pid.Proportion = KP;    /* 比例常数 Proportional Const */
    g_speed_pid.Integral = KI;      /* 积分常数 Integral Const */
    g_speed_pid.Derivative = KD;    /* 微分常数 Derivative Const */ 
}
```

该函数主要是将PID控制系统的目标速度值、期望输出值、累计偏差等清零，然后配置PID系数。



### FOC篇



## 宇树GO-M8010-6

🔗：[宇树科技 文档中心 (unitree.com)](https://support.unitree.com/home/zh/Motor_SDK_Dev_Guide/overview)

### 电机的混合控制

宇树的关节电机包含以下5个控制指令：

1. 前馈力矩：$\tau$
2. 期望角度位置：$\ q_{des}$
3. 期望角速度：$\ dq_{des}$
4. 位置刚度：$\ kp$
5. 阻尼系数：$\ kd$

在关节电机的混合控制中，使用PD控制器将电机在输出位置的偏差反馈到力矩输出上。

## 伺泰威GIM6010-8

🔗：[大疆C板（STM32F4）控制关节电机GIM6010-8_伺泰威电机gm6010-CSDN博客](https://blog.csdn.net/qq_63057826/article/details/136300464)

### ODrivetool调试

环境配置过程省略，详情见使用手册。

电机上电且连接USB Type-C数据线后，在Shell中运行odrivetool：

![image-20240727173956411](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240727173956411.png)

指令示例：odrv0.axis0.controller.input_vel，odrv0代表当前连接的电机，默认第一个连接的电机叫odrv0，第二个叫odrv1，以此类推；axis0代表驱动器连接的第一个电机，目前的版本中只支持连接一个电机。这个指令的意思是查询驱动器当前速度控制目标值。

#### 设置关键门限

```python
odrv0.axis0.motor.config.current_lim=30
```

上述指令将电流门限设置为30A。请注意，此电流门限是指Q轴电流，而不是电源电流。这个门限值直接限制了输出扭矩。对于6010-8，请不要将此门限设置超过50A。

```python
odrv0.axis0.controller.config.vel_limit=30
```

系统全局速度限制，上述指令将其限制为30turn/s（转/秒）。请注意，默认情况下纯力矩模式下此速度限制不起作用，但可以打开下述开关来使能：

```python
odrv0.axis0.controller.config.enable_torque_vel_limit=1
```

#### PID调整

```python
odrv0.axis0.controller.config.pos_gain=20.0
odrv0.axis0.controller.config.vel_gain=0.16
odrv0.axis0.controller.config.vel_integrator_gain=0.32
```

下述过程可以为用户调节PID参数提供一个参考：

1. 设置PID初始值
2. 将vel_integrator_gain调为0

#### 上电校准

```python
odrv0.axis0.requested_state = AXIS_STATE_MOTOR_CALIBRATION
odrv0.axis0.requested_state = AXIS_STATE_ENCODER_OFFSET_CALIBRATION
odrv0.axis0.motor.config.pre_calibrated=1
odrv0.axis0.encoder.config.pre_calibrated=1
odrv0.save_configuration()
```

1. 电机参数自识别：测量电机的相电阻和相电感
2. 查看错误码: dump_errors(odrv0)
3. 编码器校准：对编码器进行校准，包括编码器的安装角度与电机机械角度的校准，以及编码器自身的校准。在这个校准过程中，电机会缓慢正转一个角度，再反转一个角度。如果只正转后的就停止，则说明有错误。
4. 查看错误码
5. 写入电机校准成功标志
6. 写入编码器校准成功标志
7. 存储校准结果并重启

#### 四种控制模式

经历上述准备工作和参数配置之后，就可以尝试控制电机进行不同模式的转动。6010-8支持位置控制、速度控制、力矩控制以及运动控制模式。

在**位置控制**模式中，支持滤波位置控制，梯形曲线位置控制，周期位置控制；

在**速度控制**模式中，支持直接速度控制，斜坡速度控制；

在**力矩控制**模式中，支持直接力矩控制，斜坡力矩控制；

**运动控制**模式是综合位置，速度和力矩的控制模式，通常用于需要瞬时爆发力强的场景，如机器人膝关节。

在所有后续的控制操作中，要让电机转动，都需要让电机进入闭环控制状态：

```python
odrv0.axis0.requested_state = 8
```

用户需要让电机停止运行，或希望修改参数及保存参数，都需要先让电机进入空闲状态：

```python
odrv0.axis0.requested_state = 1
```

##### 滤波位置控制

如果用户希望自己生成位置曲线，然后以一定频率来发送位置控制指令，则建议使用滤波位置控制，因为这种模式将这些指令平滑地衔接到一起执行。如果这种情况下采用梯形曲线位置控制，则有可能会让电机转动产生顿挫感或颗粒感。

##### 梯形曲线位置控制

这个模式可以让用户设置加速度，滑行速度和减速度，来控制电机从一个位置平滑移动到另一个位置。所谓梯形是指其速度曲线看起来是梯形。

##### 周期位置控制

##### 直接速度控制

```python
odrv0.axis0.controller.config.control_mode = 2
odrv0.axis0.controller.config.input_mode = 1
```

输入目标速度来进行控制：

```python
odrv0.axis0.controller.input_vel = 10
```

##### 斜坡速度控制

##### 直接力矩控制

```python
odrv0.axis0.controller.config.control_mode = 1
odrv0.axis0.controller.config.input_mode = 1
```

力矩控制的单位是Nm，而驱动器固件中电流单位是A，所以还需要设置力矩常数，以让驱动器能够将Nm转换为电流，从而按需求驱动电机输出力矩。

```python
odrv0.axis0.motor.config.torque_constant = 8.23/12.3
```

然后输入目标速度来进行控制：

```python
odrv0.axis0.controller.input_torque = 1.2
```

如果用户想限制力矩模式下的最大速度：

```python
odrv0.axis0.controller.config.enable_torque_mode_vel_limit = 1
odrv0.axis0.controller.config.vel_limit = 30
```

##### 斜坡力矩控制

##### 运动控制

运动控制模式通过综合控制位置、速度和力矩来控制电机运动到目标位置。

#### 常用指令列表

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240727223954019.png" alt="image-20240727223954019" style="zoom: 80%;" />

![image-20240727224033944](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240727224033944.png)

![image-20240727224107610](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240727224107610.png)

![image-20240727224136452](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240727224136452.png)

#### 图形化调测

### GM6020

🔗：[Robomaster电控组小白的学习经验分享（一）——用大疆C型开发板控制GM6020电机转动到既定角度_学习_STF故事-GitCode 开源社区 (csdn.net)](https://gitcode.csdn.net/65eed4191a836825ed79f180.html?dp_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6NDUwODUzLCJleHAiOjE3MjY3MTEzNTEsImlhdCI6MTcyNjEwNjU1MSwidXNlcm5hbWUiOiJYSWFuaGwifQ.Mf_-z_KZbugvQRJmA9HFuQ9_ytvzQS_X1C_nSHtmrJI&spm=1001.2101.3001.6650.5&utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-5-130696750-blog-136300464.235^v43^pc_blog_bottom_relevance_base7&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-5-130696750-blog-136300464.235^v43^pc_blog_bottom_relevance_base7&utm_relevant_index=6)



# 电机驱动

🔗：[SimpleFOC、ODrive和VESC 教程链接汇总_odrive和simplefoc哪个好-CSDN博客](https://blog.csdn.net/loop222/article/details/121201638)



# RTOS

🔗：[Linux 与 RTOS的主要区别到底是啥？_rtos与linux-CSDN博客](https://blog.csdn.net/KUNPLAYBOY/article/details/121897318)

🔗：[[野火\]FreeRTOS 内核实现与应用开发实战—基于STM32 — FreeRTOS内核实现与应用开发实战指南—基于STM32 文档 (embedfire.com)](https://doc.embedfire.com/rtos/freertos/zh/latest/index.html)

🔗：[2023年新版手把手教你学FreeRTOS — 正点原子资料下载中心 1.0.0 文档](http://47.111.11.73/docs/book-videos/zdyzshipin/4free/newfreertos.html)

🔗：[[野火\]RT-Thread 内核实现与应用开发实战—基于STM32 — [野火]RT-Thread内核实现与应用开发实战——基于STM32 文档 (embedfire.com)](https://doc.embedfire.com/rtos/rtthread/zh/latest/index.html)

## RTOS与裸机的区别

🔗：[实时操作系统Freertos开坑学习笔记：(一）：基础概念及代码移植_freertos移植到mips-CSDN博客](https://blog.csdn.net/qq_53092944/article/details/132513376)

RTOS（Real-Time Operating System，实时操作系统）是一种专门为实时应用程序设计的操作系统，而裸机是指直接在硬件上运行的程序，没有操作系统的支持。

RTOS的优点：

* 实时性：专门为实时应用程序设计，能够提供可预测的响应时间和任务调度
* 多任务支持：能够支持多任务并发执行，通过任务调度器实现任务切换
* 丰富的功能和服务：如任务管理、通信机制、内存管理、设备驱动等

RTOS的缺点：

* 复杂性：相比于裸机来说，具有更高的复杂性，需要学习和理解操作系统的概念和机制
* 资源占用：需要额外的资源支持，如内存、处理器时间等，可能会占用一定的系统资源
* 开发和调试难度：由于RTOS的复杂性，开发和调试RTOS应用程序可能会更加困难

裸机的优点：

* 简单性：裸机程序相对于RTOS来说更加简单，不需要学习和理解操作系统的概念和机制
* 资源效率：裸机程序不需要额外的资源支持，可以更好地利用系统资源
* 可定制性：裸机程序可以根据需求进行定制开发，不受RTOS的限制

裸机的缺点：

* 缺乏实时性：裸机程序无法提供实时性，无法保证任务的响应时间和调度
* 不支持多任务：裸机程序无法支持多任务并发执行，只能顺序执行任务
* 缺乏丰富的功能和服务：裸机程序无法提供像RTOS那样丰富的功能和服务，如任务管理、通信机制、内存管理、设备驱动等

综上所述，RTOS适用于对实时性能要求较高、需要多任务支持和丰富功能服务的应用，而裸机适用于对实时性能要求不高、对资源效率和可定制性有要求的应用。

### 裸机系统

🔗：[5. **裸机系统与多线程系统** — [野火\]RT-Thread内核实现与应用开发实战——基于STM32 文档 (embedfire.com)](https://doc.embedfire.com/rtos/rtthread/zh/latest/zero_to_one/multi_thread.html)

裸机系统通常分成**轮询系统**和**前后台系统**。

轮询系统即是在裸机编程的时候，先初始化好相关的硬件，然后让主程序在一个死循环里面不断循环，顺序地做各种事情。

轮询系统是一种非常简单的软件结构，通常只适用于那些只需要顺序执行代码且不需要外部事件来驱动就能完成的事情。

相比于轮询系统，前后台系统是在轮询系统的基础上加入了中断。外部事件的响应在中断里面完成，事件的处理还是回到轮询系统中完成，中断在这里我们称为前台，main函数里面的无线循环我们称为后台。

### 多线程系统

相比于前后台系统，多线程系统的事件响应也是在中断中完成的，但是事件的处理是在线程中完成的。在多线程系统中，线程跟中断一样，也具有优先级，优先级高的线程会被优先执行。当一个紧急的事件在中断被标记之后，如果事件对应的线程的优先级足够高，就会立马得到响应。

相比于前后台系统中后台顺序执行的程序主体，在多线程系统中，根据程序的功能，我们把程序主体分割成一个个独立的，无限循环且不能返回的小程序，这个小程序我们称之为线程。每个线程都是独立的，互补干扰的，且具备自身的优先级，它由操作系统调度管理。加入操作系统后，我们在编程的时候就不需要精心地去设计程序的执行流，不用担心每个功能模块之间是否存在干扰。加入了操作系统，我们的编程反而变得简单了。整个系统随之带来的额外开销就是操作系统占据的那一丁点的FLASH和RAM。现如今，单片机的FLASH和RAM越来越大，完全足以抵挡RTOS那点开销。

## FreeRTOS

🔗：[2. 初识FreeRTOS — FreeRTOS内核实现与应用开发实战指南—基于STM32 文档 (embedfire.com)](https://doc.embedfire.com/rtos/freertos/zh/latest/zero_to_one/first_sight.html)

### FreeRTOS的编程风格

#### 数据类型

在FreeRTOS中，使用的数据类型虽然都是标准C里面的数据类型，但是针对不同的处理器，对标准C的数据类型又进行了重定义，给它们取了一个新名字。

```c
#define portCHAR    char
#define portFLOAT   float
#define portDOUBLE    double
#define portLONG    long
#define portSHORT   short
#define portSTACK_TYPE  uint32_t
#define portBASE_TYPE long

typedef portSTACK_TYPE StackType_t;
typedeflong BaseType_t;
typedefunsigned long UBaseType_t;

#if( configUSE_16_BIT_TICKS == 1 )
typedefuint16_t TickType_t;
#define portMAX_DELAY ( TickType_t ) 0xffff
#else
typedefuint32_t TickType_t;
#define portMAX_DELAY ( TickType_t ) 0xffffffffUL
```



#### 变量名

在FreeRTOS中，定义变量的时候往往会把变量的类型当作前缀加在变量上，这样的好处是让用户一看到这个变量就知道该变量的类型

* char型变量的前缀是c
* short型变量的前缀是s
* long型变量的前缀是l
* portBASE_TYPE类型变量的前缀是x

如果一个变量是无符号型的那么会有一个前缀u，如果是一个指针变量则会有一个前缀p。因此，当我们定义一个无符号的char型变量的时候会加一个uc前缀，当定义一个char型的指针变量的时候会有一个pc前缀。

#### 函数名

函数名包含了函数返回值的类型、函数所在的文件名和函数的功能，如果是私有的函数则会加一个prv（private）的前 缀。特别的，在函数名中加入了函数所在的文件名，这大大的帮助了用户提高寻找函数定义的效率和了解函数作用的目 的，具体的举例如下：

- 1. vTaskPrioritySet()函数的返回值为void型，在task.c这个文件中定义。
- 1. xQueueReceive()函数的返回值为portBASE_TYPE型，在queue.c这个文件中定义。
- 1. vSemaphoreCreateBinary()函数的返回值为void型，在semphr.h这个文件中定义。

#### 宏

宏均是由大写字母表示，并配有小写字母的前缀，前缀用于表示该宏在哪个头文件定义，部分举例具体见下表。

表：FreeRTOS宏定义举例

| 前缀                               | 宏定义的文件     |
| ---------------------------------- | ---------------- |
| port (举例, portMAX_DELAY)         | portable.h       |
| task (举例, taskENTER_CRITICAL())  | task.h           |
| pd (举例, pdTRUE)                  | projdefs.h       |
| config(举例, configUSE_PREEMPTION) | FreeRTOSConfig.h |
| err (举例, errQUEUE_FULL)          | projdefs.h       |

这里有个地方要注意的是信号量的函数都是一个宏定义，但是它的函数的命名方法是遵循函数的命名方法而不是宏定义的方法。

在贯穿FreeRTOS的整个代码中，还有几个通用的宏定义我们也要注意下，都是表示0和1的宏，具体见下表。

表:FreeRTOS通用宏定义

| 宏      | 实际的值 |
| ------- | -------- |
| pdTRUE  | 1        |
| pdFALSE | 0        |
| pdPASS  | 1        |
| pdFAIL  | 0        |

#### 格式

一个tab键盘等于四个空格键。我们在编程的时候最好使用空格键而不是使用tab键，当两个编译器的tab键设置的大小不 一样的时候，代码移植的时候代码的格式就会变乱，而使用空格键则不会出现这种问题。

### 新建FreeRTOS工程——软件仿真

#### 调试配置

##### 设置软件仿真

为了方便，我们能全部代码都用软件仿真，即不需要开发板也不需要仿真器，只需要keil。

![image-20240828102003753](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240828102003753.png)

##### 修改时钟大小



### 裸机系统与多任务系统

轮询、前后台和多任务系统软件模型区别：

| 模型       | 事件响应 | 事件处理 | 特点                       |
| ---------- | -------- | -------- | -------------------------- |
| 轮询系统   | 主程序   | 主程序   | 轮询响应事件，轮询处理事件 |
| 前后台系统 | 中断     | 主程序   | 实时响应事件，轮询处理事件 |
| 多任务系统 | 中断     | 任务     | 实时响应事件，实时处理事件 |

### 数据结构——列表与列表项讲解

🔗：[6. 数据结构—列表与列表项讲解 — FreeRTOS内核实现与应用开发实战指南—基于STM32 文档 (embedfire.com)](https://doc.embedfire.com/rtos/freertos/zh/latest/zero_to_one/lists_and_list_items.html)

列表和列表项是直接从FreeRTOS源码的注释中的list和list item翻译过来的，其实就是对应C语言中的链表和节点。在后续的讲解中，我们说的链表就是列表，节点就是列表项。

#### 链表简介

##### 单向链表

##### 双向链表

##### 链表和数组的对比

链表是通过节点把离散的数据链接成一个表，通过对节点的插入和删除操作从而实现对数据的存取。而数组是通过开辟一段连续的内存来存储数据，这是数组和链表的最大区别。数组的每个成员对应链表的节点，成员和节点的数据类型可以是标准的C类型或者是用户自定义的结构体。数组有起始地址和结束地址，而链表是一个圈，没有头尾之分，但是为了方便节点的插入和删除会人为定义一个根节点。

#### FreeRTOS中链表的实现

##### 实现链表节点

```c
struct xLIST_ITEM
{
    TickType_t xItemValue;           /* 辅助值，用于帮助节点做顺序排列 */(1)
    struct xLIST_ITEM *  pxNext;     /* 指向链表下一个节点 */(2)
    struct xLIST_ITEM *  pxPrevious; /* 指向链表前一个节点 */(3)
    void * pvOwner;                 /* 指向拥有该节点的内核对象，通常是TCB */(4)
    void *  pvContainer;            /* 指向该节点所在的链表 */(5)
};
typedefstruct xLIST_ITEM ListItem_t; /* 节点数据类型重定义 */(6)
```

* （1）：一个辅助值，用于帮助节点做顺序排列
* （2）：用于指向链表下一个节点
* （3）：用于指向链表前一个节点
* （4）：用于指向该节点的拥有者，即该节点内嵌在哪个数据结构中，属于哪个数据结构的一个成员
* （5）：用于指向该节点所在的链表，通常指向链表的根节点
* （6）：节点数据类型重定义

##### 链表根节点初始化

```C
void vListInitialise( List_t * const pxList )
{
    /* 将链表索引指针指向最后一个节点 */(1)
    pxList->pxIndex = ( ListItem_t * ) &( pxList->xListEnd );

    /* 将链表最后一个节点的辅助排序的值设置为最大，确保该节点就是链表的最后节点 */(2)
    pxList->xListEnd.xItemValue = portMAX_DELAY;

    /* 将最后一个节点的pxNext和pxPrevious指针均指向节点自身，表示链表为空 */(3)
    pxList->xListEnd.pxNext = ( ListItem_t * ) &( pxList->xListEnd );
    pxList->xListEnd.pxPrevious = ( ListItem_t * ) &( pxList->xListEnd );

    /* 初始化链表节点计数器的值为0，表示链表为空 */(4)
    pxList->uxNumberOfItems = ( UBaseType_t ) 0U;
}
```

* （1）：将链表索引指针指向最后一个节点，即第一个节点，或者第零个节点更准确，因为这个节点不会算入节点计数器的值
* （2）：将链表最后（也可以理解为第一）一个节点的辅助排序的值设置为最大，确保该节点就是链表的最后节点（也可以理解为第一）
* （3）：将最后一个节点的pxNext和pxPrevious指针均指向节点自身，表示链表为空
* （4）：初始化链表节点计数器的值为0，表示链表为空

##### 将节点插入到链表的尾部

将节点插入到链表的尾部，就是将一个新的节点插入到一个空的链表。

##### 将节点按照升序排列插入到链表

将节点按照升序排列插入到链表，如果有两个节点的值相同，则新节点在旧节点的后面插入。

```c
void vListInsert( List_t * const pxList, ListItem_t * const pxNewListItem )
{
    ListItem_t *pxIterator;

    /* 获取节点的排序辅助值 */
    const TickType_t xValueOfInsertion = pxNewListItem->xItemValue;(1)

    /* 寻找节点要插入的位置 */(2)
    if ( xValueOfInsertion == portMAX_DELAY )
        {
            pxIterator = pxList->xListEnd.pxPrevious;
        }
    else
        {
    for ( pxIterator = ( ListItem_t * ) &( pxList->xListEnd );
                    pxIterator->pxNext->xItemValue <= xValueOfInsertion;
                    pxIterator = pxIterator->pxNext )
            {
                /* 没有事情可做，不断迭代只为了找到节点要插入的位置 */
            }
        }
        /* 根据升序排列，将节点插入 */(3)
        pxNewListItem->pxNext = pxIterator->pxNext;             ①
        pxNewListItem->pxNext->pxPrevious = pxNewListItem;    ②
        pxNewListItem->pxPrevious = pxIterator;                 ③
        pxIterator->pxNext = pxNewListItem;                      ④

        /* 记住该节点所在的链表 */
        pxNewListItem->pvContainer = ( void * ) pxList;        ⑤

        /* 链表节点计数器++ */
        ( pxList->uxNumberOfItems )++;                            ⑥
}
```

##### 将节点从链表删除

假设将一个有三个节点的链表中的中间节点删除。

```c
UBaseType_t uxListRemove( ListItem_t * const pxItemToRemove )
{
    /* 获取节点所在的链表 */
    List_t * const pxList = ( List_t * ) pxItemToRemove->pvContainer;
    /* 将指定的节点从链表删除*/
    pxItemToRemove->pxNext->pxPrevious = pxItemToRemove->pxPrevious;①
    pxItemToRemove->pxPrevious->pxNext = pxItemToRemove->pxNext;②

    /*调整链表的节点索引指针 */
    if ( pxList->pxIndex == pxItemToRemove )
        {
            pxList->pxIndex = pxItemToRemove->pxPrevious;
        }

    /* 初始化该节点所在的链表为空，表示节点还没有插入任何链表 */
    pxItemToRemove->pvContainer = NULL;                                   ③

    /* 链表节点计数器-- */
    ( pxList->uxNumberOfItems )--;                                         ④

    /* 返回链表中剩余节点的个数 */
    return pxList->uxNumberOfItems;
}
```



### 任务的定义与任务切换的实现

在这章中，我们会创建两个任务，并让这两个任务不断地切换，任务的主体都是让一个变量按照一定的频率翻转，通过Keil的软件仿真功能，在逻辑分析仪中观察变量的波形变化。

在多任务系统中，两个任务不断切换的效果应该像下图一样，即两个变量的波形是完全一样的，就好像CPU在同时干两件事一样，这才是多任务的意义。

#### 什么是任务

* 在裸机系统中，系统的主体就是main函数里面顺序执行的无线循环，这个无限循环里面CPU按照顺序完成各种事情。

* 在多任务系统中，根据功能的不同，把整个系统分割成一个个独立的且无法返回的函数，这个函数我们称为**任务**。

  ```c
  void task_entry (void *parg)
  {
      /* 任务主体，无限循环且不能返回 */
      for (;;)
      {
          /* 任务主体代码 */
      }
  }
  ```

#### 创建任务

我们先回想下，在一个裸机系统中，如果有全局变量，有子函数调用，有中断发生。那么系统在运行的时候，全局变量放在哪里，子函数调用时，局部变量放在哪里，中断发生时，函数返回地址放哪里。如果只是单纯的裸机编程，它们放哪里我们不用管，但是如果要写一个RTOS，这些种种环境参数，我们必须弄清楚他们是如何存储的。 在裸机系统中，他们统统放在一个叫**栈**的地方，栈是单片机RAM里面一段连续的内存空间，栈的大小一般在启动 文件或者链接脚本里面指定，最后由C库函数_main进行初始化。

* 栈的定义：是只允许在一端进行插入或删除的线性表。首先栈是一种线性表，但限定这种线性表只能在某一端进行插入和删除操作
* 栈顶（top）：线性表允许进行插入或删除的那一端
* 栈底（bottom）：固定的，不允许进行插入和删除的另一端
* 空栈：不含任何元素的空表

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d78e4450c71489a1189583c704543d13.png#pic_center)

但是，在多任务系统中，每个任务都是独立的，互不干扰的，所以要为每个任务都分配独立的栈空间，这个栈空间通常是一个预先定义好的全局数组，也可以是动态分配的一段内存空间，但它们都存在于RAM中。

##### 定义任务栈

我们先回想下，在一个裸机系统中，如果有全局变量，有子函数调用，有中断发生。那么系统在运行的时候，全局变量放在哪里，子函数调用时，局部变量放在哪里，中断发生时，函数返回地址放哪里。如果只是单纯的裸机 编程，它们放哪里我们不用管，但是如果要写一个RTOS，这些种种环境参数，我们必须弄清楚他们是如何存储的。 在裸机系统中，他们统统放在一个叫**栈**的地方，栈是单片机RAM里面一段连续的内存空间，栈的大小一般在启动文件或者链接脚本里面指定，最后由C库函数_main进行初始化。

但是，在多任务系统中，每个任务都是独立的，互不干扰的，所以要为每个任务都分配独立的栈空间，这个栈空间通常是一个预先定义好的全局数组，也可以是动态分配的一段内存空间，但它们都存在于RAM中。

本章我们要实现两个变量按照一定的频率轮流的翻转，每个变量对应一个任务，那么就需要定义两个任务栈，在多任务系统中，**有多少个任务就需要定义多少个任务栈**。

```c
#define TASK1_STACK_SIZE                    128(1)
StackType_t Task1Stack[TASK1_STACK_SIZE];(1)

#define TASK2_STACK_SIZE                    128
StackType_t Task2Stack[TASK2_STACK_SIZE];
```

任务栈其实就是一个预先定义好的全局数据，数据类型为StackType_t，大小由TASK1_STACK_SIZE这个宏来定义，默认为128，单位为字，即512字节，这也是FreeRTOS推荐的最小的任务栈。 在FreeRTOS中，凡是涉及数据类型的地方，FreeRTOS都会将标准的C数据类型用typedef 重新取一个类型名。 这些经过重定义的数据类型放在portmacro.h（rtdef.h第一次使用需要在include文件夹下面新建然后添加 到工程freertos/source这个组文件）这个头文件。

##### 定义任务函数

任务是一个独立的函数，函数主体无限循环且不能返回。本章我们在main.c中定义的两个任务。

```c
/* 软件延时 */
void delay (uint32_t count)
{
for (; count!=0; count--);
}
/* 任务1 */
void Task1_Entry( void *p_arg )(1)
{
for ( ;; )
    {
        flag1 = 1;
        delay( 100 );
        flag1 = 0;
        delay( 100 );
    }
}

/* 任务2 */
void Task2_Entry( void *p_arg )(2)
{
for ( ;; )
    {
        flag2 = 1;
        delay( 100 );
        flag2 = 0;
        delay( 100 );
    }
}
```

##### 定义任务控制块

在裸机系统中，程序的主体是CPU按照顺序执行的。而在多任务系统中，任务的执行是由系统调度的。系统为了顺利地调度任务，为每个任务都额外定义了一个**任务控制块**，这个任务控制块就相当于任务的身份证，里面存有任务的所有信息，比如任务的栈指针，任务名称，任务的形参等。有了这个任务控制块之后，以后系统对任务的全部操作都 可以通过这个任务控制块来实现。定义一个任务控制块需要一个新的数据类型，该数据类型在task.c这C头文件中声 明（为了tskTCB这个数据类型能在其他地方使用，讲解的时候我把这个任务控制块的声明放在了FreeRTOS.h这个头文件）。

```c
typedefstruct tskTaskControlBlock
{
volatile StackType_t    *pxTopOfStack;    /* 栈顶 */(1)

    ListItem_t              xStateListItem;   /* 任务节点 */(2)

    StackType_t             *pxStack;         /* 任务栈起始地址 */(3)
/* 任务名称，字符串形式 */(4)
char                    pcTaskName[ configMAX_TASK_NAME_LEN ];
} tskTCB;
typedef tskTCB TCB_t;(5)
```

在本章实验中，我们在main.c文件中为两个任务定义的任务控制块。

```c
/* 定义任务控制块 */
TCB_t Task1TCB;
TCB_t Task2TCB;
```

##### 实现任务创建函数

任务的**栈**，任务的**函数实体**，任务的**控制块**最终需要联系起来才能由系统进行统一调度。那么这个联系的工作就由**任务创建函数**xTaskCreateStatic()来实现，该函数在task.c（task.c第一次使用需要自行在文件夹freertos中 新建并添加到工程的freertos/source组）中定义，在task.h中声明，所有跟任务相关的函数都在这个文件定义。

#### 实现就绪列表

##### 定义就绪列表

任务创建好之后，我们需要把任务添加到就绪列表里面，表示任务已经就绪，系统随时可以调度。

```c
/* 任务就绪列表 */
List_t pxReadyTasksLists[ configMAX_PRIORITIES ];
```

就绪列表实际上就是一个List_t类型的数组，数组的大小由决定最大任务优先级的宏 configMAX_PRIORITIES决定，configMAX_PRIORITIES在FreeRTOSConfig.h中默认定义为5，最大支持256个优先级。数组的下标对应了任务的优先级，同一优先级的任务统一插入到就绪列表的同一条链表中。

##### 就绪列表初始化

就绪列表在使用前需要先初始化，就绪列表初始化的工作在函数prvInitialiseTaskLists()里面实现。

```c
void prvInitialiseTaskLists( void )
{
    UBaseType_t uxPriority;


for ( uxPriority = ( UBaseType_t ) 0U;
uxPriority < ( UBaseType_t ) configMAX_PRIORITIES;
uxPriority++ )
    {
        vListInitialise( &( pxReadyTasksLists[ uxPriority ] ) );
    }
}
```

##### 将任务插入到就绪列表

任务控制块里面有一个xStateListItem成员，数据类型为ListItem_t，我们将任务插入到就绪列表里面，就是通过 将任务控制块的xStateListItem这个节点插入到就绪列表中来实现的。

就绪列表的下标对应的是任务的优先级，但是目前我们的任务还不支持优先级，有关支持多优先级的知识点我们后面会 讲到，所以Task1和Task2任务在插入到就绪列表的时候，可以随便选择插入的位置。

#### 实现调度器

调度器是操作系统的核心，其主要功能就是实现任务的切换，即从就绪列表里面找到优先级最高的任务，然后去执行该 任务。从代码上来看，调度器无非也就是由几个全局变量和一些可以实现任务切换的函数组成，全部都在task.c文件中实现。

##### 启动调度器

调度器的启动由vTaskStartScheduler()函数来完成，该函数在task.c中定义。

```c
void vTaskStartScheduler( void )
{
/* 手动指定第一个运行的任务 */
    pxCurrentTCB = &Task1TCB;(1)

/* 启动调度器 */
if ( xPortStartScheduler() != pdFALSE )
    {
/* 调度器启动成功，则不会返回，即不会来到这里 */(2)
    }
}
```

* pxCurrentTCB是一个在task.c定义的全局指针，用于指向当前正在运行或者即将要运行 的任务的任务控制块。目前我们还不支持优先级，则手动指定第一个要运行的任务。
* 调用函数xPortStartScheduler()启动调度器，调度器启动成功，则不会返回。该函数 在port.c中实现。

prvStartFirstTask()函数用于开始第一个任务，主要做了两个动作，一个是更新MSP的值，二是产生SVC系统调用， 然后去到SVC的中断服务函数里面真正切换到第一个任务。

##### 任务切换

任务切换就是在就绪列表中寻找优先级最高的就绪任务，然后去执行该任务。但是目前我们还不支持优先级，仅实现两个任务轮流切换。

```c
/* 在task.h中定义 */
#define taskYIELD()                 portYIELD()

/* 在portmacro.h中定义 */
/* 中断控制状态寄存器：0xe000ed04
* Bit 28 PENDSVSET: PendSV 悬起位
*/
#define portNVIC_INT_CTRL_REG               (*(( volatile uint32_t *) 0xe000ed04))
#define portNVIC_PENDSVSET_BIT              ( 1UL << 28UL )

#define portSY_FULL_READ_WRITE              ( 15 )

#define portYIELD()
{
    /* 触发PendSV，产生上下文切换 */
    portNVIC_INT_CTRL_REG = portNVIC_PENDSVSET_BIT;(1)
    __dsb( portSY_FULL_READ_WRITE );
    __isb( portSY_FULL_READ_WRITE );
}
```

portYIELD的实现很简单，实际就是将PendSV的悬起位置1，当没有其他中断运行的 时候响应PendSV中断，去执行我们写好的PendSV中断服务函数，在里面实现任务切换。

PendSV中断服务函数是真正实现任务切换的地方。

### 临界段的保护

#### 什么是临界段

临界段用一句话概括就是一段在执行的时候不能被中断的代码段。在FreeRTOS里面，这个临界段最常出现的就是对全局变量的操作，全局变量就好像是一个枪把子，谁都可以对他开枪，但是我开枪的时候，你就不能开枪，否则就不知道是谁命中了靶子。

那么什么情况下临界段会被打断？一个是系统调度，还有一个就是外部中断。在FreeRTOS，系统调度，最终也是产生PendSV中断，在 PendSV Handler里面实现任务的切换，所以还是可以归结为中断。既然这样，FreeRTOS对临界段的保护最终还是回到对中断的开和关的控制。

**chatGPT**：

* 在FreeRTOS中，临界段（Critical Section）是指一段代码，它不能被中断或其他任务打断，以确保共享资源的安全访问。临界段通常用于多任务或中断环境中，避免资源竞争问题（例如数据竞争或资源死锁）。

* FreeRTOS中的临界段机制允许任务临时关闭中断或者禁止任务切换，以确保任务在访问共享资源时不被其他任务或中断打断。这可以防止由于上下文切换或中断导致的数据不一致。

使用临界段时的注意事项：

* 进入临界段的代码应尽量保持简短，因为在临界段期间中断被关闭，所有高优先级中断都无法执行，这可能影响系统的实时性能。
* FreeRTOS还提供了中断安全的方式来进入临界段，允许关闭一定优先级以下的中断，但保持高优先级中断依旧能执行。

#### Cortex内核快速关中断指令

为了快速地开关中断， Cortex-M内核专门设置了一条 CPS 指令，有 4 种用法

```
CPSID I ;PRIMASK=1     ;关中断
CPSIE I ;PRIMASK=0     ;开中断
CPSID F ;FAULTMASK=1   ;关异常
CPSIE F ;FAULTMASK=0   ;开异常
```

* PRIMASK和FAULTMAST是Cortex-M内核里面三个中断屏蔽寄存器中的两个，还有一个是BASEPRI
* 在FreeRTOS中，对中断的开和关是通过操作**BASEPRI**寄存器来实现的，即大于等于BASEPRI的值的中断会被屏蔽，小于BASEPRI的值的中断则 不会被屏蔽，不受FreeRTOS管理。用户可以设置BASEPRI的值来选择性的给一些非常紧急的中断留一条后路。

#### 关中断

FreeRTOS关中断的函数在portmacro.h中定义，分不带返回值和带返回值两种

```c
/* 不带返回值的关中断函数，不能嵌套，不能在中断里面使用 */(1)
#define portDISABLE_INTERRUPTS() vPortRaiseBASEPRI()

void vPortRaiseBASEPRI( void )
{
uint32_t ulNewBASEPRI = configMAX_SYSCALL_INTERRUPT_PRIORITY;(1)-1
    __asm
    {
        msr basepri, ulNewBASEPRI(1)-2
        dsb
        isb
    }
}

/* 带返回值的关中断函数，可以嵌套，可以在中断里面使用 */(2)
#define portSET_INTERRUPT_MASK_FROM_ISR() ulPortRaiseBASEPRI()
ulPortRaiseBASEPRI( void )
{
    uint32_t ulReturn, ulNewBASEPRI = configMAX_SYSCALL_INTERRUPT_PRIORITY;(2)-1
    __asm
    {
        mrs ulReturn, basepri(2)-2
        msr basepri, ulNewBASEPRI(2)-3
        dsb
        isb
    }
    return ulReturn;(2)-4
}
```

* **不带返回值的关中断函数，不能嵌套，不能在中断里面使用**。不带返回值的意思是：在往BASEPRI写入新的值的时候，不用先将BASEPRI的值保存起来，即不用管当前的中断状态是怎么样的，既然不用管当前的中断状态，也就意味着这样的函数不能在中断里面调用。
* **带返回值的关中断函数，可以嵌套，可以在中断里面使用**。带返回值的意思是：在往BASEPRI写入新的值的时候，先将BASEPRI的值保存起来，在更新完BASEPRI的值的时候，将之前保存好的BASEPRI的值返回，返回的值作为形参传入开中断函数。

#### 开中断

FreeRTOS开中断的函数在portmacro.h中定义

```
/* 不带中断保护的开中断函数 */
#define portENABLE_INTERRUPTS() vPortSetBASEPRI( 0 )(2)

/* 带中断保护的开中断函数 */
#define portCLEAR_INTERRUPT_MASK_FROM_ISR(x) vPortSetBASEPRI(x)(3)

void vPortSetBASEPRI( uint32_t ulBASEPRI )(1)
{
    __asm
    {
        msr basepri, ulBASEPRI
    }
}
```



#### 进入/退出临界段的宏

进入和退出临界段的宏在task.h中定义

```
#define taskENTER_CRITICAL()                portENTER_CRITICAL()
#define taskENTER_CRITICAL_FROM_ISR() portSET_INTERRUPT_MASK_FROM_ISR()

#define taskEXIT_CRITICAL()         portEXIT_CRITICAL()
#define taskEXIT_CRITICAL_FROM_ISR( x ) portCLEAR_INTERRUPT_MASK_FROM_ISR( x )
```

进入和退出临界段的宏分中断保护版本和非中断版本，但最终都是通过开/关中断来实现。有关开/光中断的底层代码我们已经讲解， 那么接下来的退出和进入临界段的代码配套注释来理解即可。

##### 进入临界段-不带中断保护版本，不能嵌套

```C
/* ==========进入临界段，不带中断保护版本，不能嵌套=============== */
/* 在task.h中定义 */
#define taskENTER_CRITICAL()                portENTER_CRITICAL()

/* 在portmacro.h中定义 */
#define portENTER_CRITICAL()                vPortEnterCritical()

/* 在port.c中定义 */
void vPortEnterCritical( void )
{
    portDISABLE_INTERRUPTS();
    uxCriticalNesting++;(1)

if ( uxCriticalNesting == 1 )(2)
    {
configASSERT( ( portNVIC_INT_CTRL_REG & portVECTACTIVE_MASK ) == 0 );
    }
}

/* 在portmacro.h中定义 */
#define portDISABLE_INTERRUPTS()    vPortRaiseBASEPRI()

/* 在portmacro.h中定义 */
static portFORCE_INLINE void vPortRaiseBASEPRI( void )
{
uint32_t ulNewBASEPRI = configMAX_SYSCALL_INTERRUPT_PRIORITY;

    __asm
    {
        msr basepri, ulNewBASEPRI
        dsb
        isb
    }
}
```



##### 进入临界段-带中断保护版本，可以嵌套

```c
/* ==========进入临界段，带中断保护版本，可以嵌套=============== */
/* 在task.h中定义 */
#define taskENTER_CRITICAL_FROM_ISR()  portSET_INTERRUPT_MASK_FROM_ISR()

/* 在portmacro.h中定义 */
#define portSET_INTERRUPT_MASK_FROM_ISR()           ulPortRaiseBASEPRI()

/* 在portmacro.h中定义 */
static portFORCE_INLINE uint32_t ulPortRaiseBASEPRI( void )
{
uint32_t ulReturn, ulNewBASEPRI = configMAX_SYSCALL_INTERRUPT_PRIORITY;

    __asm
    {
        mrs ulReturn, basepri
        msr basepri, ulNewBASEPRI
        dsb
        isb
    }

return ulReturn;
}
```



##### 退出临界段-不带中断保护版本，不能嵌套

```c
/* ==========退出临界段，不带中断保护版本，不能嵌套=============== */
/* 在task.h中定义 */
#define taskEXIT_CRITICAL()         portEXIT_CRITICAL()

/* 在portmacro.h中定义 */
#define portEXIT_CRITICAL()         vPortExitCritical()

/* 在port.c中定义 */
void vPortExitCritical( void )
{
    configASSERT( uxCriticalNesting );
    uxCriticalNesting--;
if ( uxCriticalNesting == 0 )
    {
        portENABLE_INTERRUPTS();
    }
}

/* 在portmacro.h中定义 */
#define portENABLE_INTERRUPTS()     vPortSetBASEPRI( 0 )

/* 在portmacro.h中定义 */
static portFORCE_INLINE void vPortSetBASEPRI( uint32_t ulBASEPRI )
{
    __asm
    {
        msr basepri, ulBASEPRI
    }
}
```



##### 退出临界段-带中断保护版本，可以嵌套

```c
/* ==========退出临界段，带中断保护版本，可以嵌套=============== */
/* 在task.h中定义 */
#define taskEXIT_CRITICAL_FROM_ISR( x ) portCLEAR_INTERRUPT_MASK_FROM_ISR( x )

/* 在portmacro.h中定义 */
#define portCLEAR_INTERRUPT_MASK_FROM_ISR(x)        vPortSetBASEPRI(x)

/* 在portmacro.h中定义 */
static portFORCE_INLINE void vPortSetBASEPRI( uint32_t ulBASEPRI )
{
    __asm
    {
        msr basepri, ulBASEPRI
    }
}
```



#### 临界段代码的应用

在FreeRTOS中，对临界段的保护出现在两种场合，一种是在中断场合一种是在非中断场合

```c
/* 在中断场合，临界段可以嵌套 */
{
uint32_t ulReturn;
/* 进入临界段，临界段可以嵌套 */
    ulReturn = taskENTER_CRITICAL_FROM_ISR();

/* 临界段代码 */

/* 退出临界段 */
    taskEXIT_CRITICAL_FROM_ISR( ulReturn );
}

/* 在非中断场合，临界段不能嵌套 */
{
/* 进入临界段 */
    taskENTER_CRITICAL();

/* 临界段代码 */

/* 退出临界段*/
    taskEXIT_CRITICAL();
}
```



### 空闲任务与阻塞延时的实现

在上一章节中，任务体内的延时使用的是软件延时，即还是让CPU空等来达到延时的效果。使用RTOS的很大优势就是榨干CPU的性能， 永远不能让它闲着，任务如果需要延时也就不能再让CPU空等来实现延时的效果。RTOS中的延时叫**阻塞延时**，即任务需要延时的时候， 任务会放弃CPU的使用权，CPU可以去干其他的事情，当任务延时时间到，重新获取CPU使用权，任务继续运行，这样就充分地利用了 CPU的资源，而不是干等着。

当任务需要延时，进入阻塞状态，那CPU又去干什么事情了？如果没有其他任务可以运行，RTOS都会为CPU创建一个空闲任务，这个时候CPU就运行**空闲任务**。在FreeRTOS中，**空闲任务是系统在【启动调度器】的时候创建的优先级最低的任务，空闲任务主体主要是做一些系统内存的清理工作**。但是为了简单起见，我们本章实现的空闲任务只是对一个全局变量进行计数。鉴于空闲任务的这种特性， 在实际应用中，当系统进入空闲任务的时候，可在空闲任务中让单片机进入休眠或者低功耗等操作。

#### 实现空闲任务

目前我们在创建任务时使用的栈和TCB都使用的是静态的内存，即需要预先定义好内存，空闲任务也不例外。有关空闲任务的栈和 TCB需要用到的内存空间均在main.c中定义。

##### 定义空闲任务的栈

空闲任务的栈在我们在main.c中定义

```c
/* 定义空闲任务的栈 */
#define configMINIMAL_STACK_SIZE    ( ( unsigned short ) 128 )(2)
StackType_t IdleTaskStack[configMINIMAL_STACK_SIZE];(1)
```



##### 定义空闲任务的任务控制块

任务控制块是每一个任务必须的，空闲任务的的任务控制块我们在main.c中定义，是一个全局变量

```c
/* 定义空闲任务的任务控制块 */
TCB_t IdleTaskTCB;
```



##### 创建空闲任务

当定义好空闲任务的栈，任务控制块后，就可以创建空闲任务。空闲任务在调度器启动函数vTaskStartScheduler()中创建

```c
extern TCB_t IdleTaskTCB;
void vApplicationGetIdleTaskMemory( TCB_t **ppxIdleTaskTCBBuffer,
                                    StackType_t **ppxIdleTaskStackBuffer,
uint32_t *pulIdleTaskStackSize );
void vTaskStartScheduler( void )
{
/*=======================创建空闲任务start=======================*/
    TCB_t *pxIdleTaskTCBBuffer = NULL;         /* 用于指向空闲任务控制块 */
    StackType_t *pxIdleTaskStackBuffer = NULL; /* 用于空闲任务栈起始地址 */
uint32_t ulIdleTaskStackSize;

/* 获取空闲任务的内存：任务栈和任务TCB */(1)
    vApplicationGetIdleTaskMemory( &pxIdleTaskTCBBuffer,
&pxIdleTaskStackBuffer,
&ulIdleTaskStackSize );
/* 创建空闲任务 */ (2)
    xIdleTaskHandle =
    xTaskCreateStatic( (TaskFunction_t)prvIdleTask,    /* 任务入口 */
                    (char *)"IDLE",             /* 任务名称，字符串形式 */
                    (uint32_t)ulIdleTaskStackSize ,  /* 任务栈大小，单位为字 */
                    (void *) NULL,                   /* 任务形参 */
                    (StackType_t *)pxIdleTaskStackBuffer, /* 任务栈起始地址 */
                    (TCB_t *)pxIdleTaskTCBBuffer ); /* 任务控制块 */
/* 将任务添加到就绪列表 */(3)
    vListInsertEnd( &( pxReadyTasksLists[0] ),
&( ((TCB_t *)pxIdleTaskTCBBuffer)->xStateListItem ) );
/*==========================创建空闲任务end=====================*/

/* 手动指定第一个运行的任务 */
    pxCurrentTCB = &Task1TCB;

/* 启动调度器 */
if ( xPortStartScheduler() != pdFALSE )
    {
/* 调度器启动成功，则不会返回，即不会来到这里 */
    }
}

```

将pxIdleTaskTCBBuffer和pxIdleTaskStackBuffer这两个接下来 要作为形参传到xTaskCreateStatic()函数的指针分别指向空闲任务的TCB和栈的起始地址，这个操作由函数vApplicationGe tIdleTaskMemory()来实现，该函数需要用户自定义，目前我们在main.c中实现

```c
void vApplicationGetIdleTaskMemory( TCB_t **ppxIdleTaskTCBBuffer,
StackType_t **ppxIdleTaskStackBuffer,
uint32_t *pulIdleTaskStackSize )
{
    *ppxIdleTaskTCBBuffer=&IdleTaskTCB;
    *ppxIdleTaskStackBuffer=IdleTaskStack;
    *pulIdleTaskStackSize=configMINIMAL_STACK_SIZE;
}
```



#### 实现阻塞延时

##### vTaskDelay()函数

阻塞延时的阻塞是指任务调用该延时函数后，任务会被剥离CPU使用权，然后进入阻塞状态，直到延时结束，任务重新获取CPU使用权才 可以继续运行。在任务阻塞的这段时间，CPU可以去执行其他的任务，如果其他的任务也在延时状态，那么CPU就将运行空闲任务。

```c
void vTaskDelay( const TickType_t xTicksToDelay )
{
    TCB_t *pxTCB = NULL;

/* 获取当前任务的TCB */
    pxTCB = pxCurrentTCB;(1)

/* 设置延时时间 */
    pxTCB->xTicksToDelay = xTicksToDelay;(2)

/* 任务切换 */
    taskYIELD();(3)
}
```

* （1）获取当前任务的任务控制块。pxCurrentTCB是一个在task.c定义的全局指针，用于指向当前正在运行或者即将要运行的任务的任务控制块。
* （2）xTicksToDelay是任务控制块的一个成员，用于记录任务需要延时的时间，单位为SysTick 的中断周期。比如我们本书当中SysTick的中断周期为10ms，调用vTaskDelay(2)则完成2*10ms的延时。



##### 修改vTaskSwitchContext()函数

任务切换。调用tashYIELD()会产生PendSV中断，在PendSV中断服务函数中会调用上下文切换 函数vTaskSwitchContext()，该函数的作用是寻找最高优先级的就绪任务，然后更新pxCurrentTCB。上一章我们只有两个任务，则 pxCurrentTCB不是指向任务1就是指向任务2，本章节开始我们多增加了一个空闲任务，则需要让pxCurrentTCB在这三个任务中切换， 算法需要改变。

```c
#if 0
void vTaskSwitchContext( void )
{/* 两个任务轮流切换 */
if ( pxCurrentTCB == &Task1TCB )
    {
        pxCurrentTCB = &Task2TCB;
    }
else
    {
        pxCurrentTCB = &Task1TCB;
    }
}
#else

void vTaskSwitchContext( void )
{
/* 如果当前任务是空闲任务，那么就去尝试执行任务1或者任务2，
看看他们的延时时间是否结束，如果任务的延时时间均没有到期，
那就返回继续执行空闲任务 */
if ( pxCurrentTCB == &IdleTaskTCB )(1)
    {
if (Task1TCB.xTicksToDelay == 0)
        {
            pxCurrentTCB =&Task1TCB;
        }
else if (Task2TCB.xTicksToDelay == 0)
        {
            pxCurrentTCB =&Task2TCB;
        }
else
        {
return;     /* 任务延时均没有到期则返回，继续执行空闲任务 */
        }
    }
else/* 当前任务不是空闲任务则会执行到这里 */(2)
    {
/*如果当前任务是任务1或者任务2的话，检查下另外一个任务,
如果另外的任务不在延时中，就切换到该任务
否则，判断下当前任务是否应该进入延时状态，
如果是的话，就切换到空闲任务。否则就不进行任何切换 */
if (pxCurrentTCB == &Task1TCB)
        {
if (Task2TCB.xTicksToDelay == 0)
            {
                pxCurrentTCB =&Task2TCB;
            }
else if (pxCurrentTCB->xTicksToDelay != 0)
            {
                pxCurrentTCB = &IdleTaskTCB;
            }
else
            {
return;     /* 返回，不进行切换，因为两个任务都处于延时中 */
            }
        }
else if (pxCurrentTCB == &Task2TCB)
        {
if (Task1TCB.xTicksToDelay == 0)
            {
                pxCurrentTCB =&Task1TCB;
            }
else if (pxCurrentTCB->xTicksToDelay != 0)
            {
                pxCurrentTCB = &IdleTaskTCB;
            }
else
            {
return;     /* 返回，不进行切换，因为两个任务都处于延时中 */
            }
        }
    }
}

#endif
```

* 如果当前任务是空闲任务，那么就去尝试执行任务1或者任务2，看看他们的延时时间是否结束，如果任务的延时时间均没有到期，那就返回继续执行空闲任务。
* 如果当前任务是任务1或者任务2的话，检查下另外一个任务，如果另外的任务不在延时中，就切换到该任务。否则，判断下当前任务是否应该进入延时状态，如果是的话，就切换到空闲任务，否则就不进行任何切换。

#### SysTick中断服务函数

在任务上下文切换函数vTaskSwitchContext()中，会判断每个任务的任务控制块中的延时成员xTicksToDelay的值是否为0，如果为0就要将对应的任务就绪，如果不为0就继续延时。如果一个任务要延时，一开始xTicksToDelay肯定不为0， 当xTicksToDelay变为0的时候表示延时结束，那么xTicksToDelay是以什么周期在递减？在哪里递减？在FreeRTOS中，这个周期由**SysTick中断**提供，操作系统里面的最小的时间单位就是SysTick的中断周期，我们称之为一个tick，SysTick中断服务函数在port.c.c中实现。

```c
void xPortSysTickHandler( void )
{
/* 关中断 */
    vPortRaiseBASEPRI();(1)

/* 更新系统时基 */
    xTaskIncrementTick();(2)

/* 开中断 */
    vPortClearBASEPRIFromISR();(3)
}
```

##### xTaskIncrementTick()函数

更新系统时基，该函数在task.c中定义

#### SysTick初始化函数

SysTick的中断服务函数要想被顺利执行，则SysTick必须先初始化。SysTick初始化函数在port.c中定义

### 支持多优先级

在FreeRTOS中，**数字优先级越小，逻辑优先级也越小**，这与隔壁的RT-Thread和μC/OS刚好相反。

#### 如何支持多优先级

就绪列表pxReadyTasksLists[ configMAX_PRIORITIES ]是一个数组，数组里面存的是就绪任务的TCB（准确来说是TCB里面的xStateListItem节点），数组的下标对应任务的优先级，优先级越低对应的数组下标越小。空闲任务的优先级最低，对应的是下标为0的链表。

任务在创建的时候，会根据任务的优先级将任务插入到就绪列表不同的位置。相同优先级的任务插入到就绪列表里面的同一条链表中，这就是我们下一章要讲解的支持时间片。

pxCurrenTCB是一个全局的TCB指针，用于指向优先级最高的就绪任务的TCB，即当前正在运行的TCB。那么我们要想让任务支持优先级，即只要解决**在任务切换（taskYIELD）的时候，让pxCurrenTCB指向最高优先级的就绪任务的TCB就可以**，前面的章节我们是手动地让pxCurrenTCB在任务1、任务2和空闲任务中轮转，现在我们要改成pxCurrenTCB在任务切换的时候指向最高优先级的就绪任务的TCB即可，那问题的关键就是：如果找到最高优先级的就绪任务的TCB。FreeRTOS提供了两套方法，一套是通用的，一套是根据特定的处理器优化过的，接下来我们重点讲解下这两个方法。

#### 讲解查找最高优先级的就绪任务相关任务

```c
/* 查找最高优先级的就绪任务：通用方法 */
#if ( configUSE_PORT_OPTIMISED_TASK_SELECTION == 0 )(1)
/* uxTopReadyPriority 存的是就绪任务的最高优先级 */
#define taskRECORD_READY_PRIORITY( uxPriority )\(2)
    {\
    if( ( uxPriority ) > uxTopReadyPriority )\
    {\
    uxTopReadyPriority = ( uxPriority );\
    }\
    }/* taskRECORD_READY_PRIORITY */

/*-----------------------------------------------------------*/

#define taskSELECT_HIGHEST_PRIORITY_TASK()\(3)
    {\
    UBaseType_t uxTopPriority = uxTopReadyPriority;\(3)-1
    /* 寻找包含就绪任务的最高优先级的队列 */\(3)-2
    while( listLIST_IS_EMPTY( &( pxReadyTasksLists[ uxTopPriority ] ) ) )\
    {\
    --uxTopPriority;\
    }\
    /* 获取优先级最高的就绪任务的TCB，然后更新到pxCurrentTCB */\
    listGET_OWNER_OF_NEXT_ENTRY(pxCurrentTCB, &(pxReadyTasksLists[ uxTopPriority ]));\(3)-3
    /* 更新uxTopReadyPriority */\
    uxTopReadyPriority = uxTopPriority;\(3)-4
    }/* taskSELECT_HIGHEST_PRIORITY_TASK */

/*-----------------------------------------------------------*/

/* 这两个宏定义只有在选择优化方法时才用，这里定义为空 */
#define taskRESET_READY_PRIORITY( uxPriority )
#define portRESET_READY_PRIORITY( uxPriority, uxTopReadyPriority )

/* 查找最高优先级的就绪任务：根据处理器架构优化后的方法 */
#else/* configUSE_PORT_OPTIMISED_TASK_SELECTION */(4)

#define taskRECORD_READY_PRIORITY( uxPriority ) \(5)
    portRECORD_READY_PRIORITY( uxPriority, uxTopReadyPriority )

/*-----------------------------------------------------------*/

#define taskSELECT_HIGHEST_PRIORITY_TASK()\(7)
    {\
    UBaseType_t uxTopPriority;\
    /* 寻找最高优先级 */\
    portGET_HIGHEST_PRIORITY( uxTopPriority, uxTopReadyPriority );\(7)-1
    /* 获取优先级最高的就绪任务的TCB，然后更新到pxCurrentTCB */\
listGET_OWNER_OF_NEXT_ENTRY( pxCurrentTCB, &( pxReadyTasksLists[ uxTopPriority ] ) );\(7)-2
    }/* taskSELECT_HIGHEST_PRIORITY_TASK() */

/*-----------------------------------------------------------*/
#if 0
#define taskRESET_READY_PRIORITY( uxPriority )\(注意)
    {\
    if(listCURRENT_LIST_LENGTH(&(pxReadyTasksLists[( uxPriority)]))==(UBaseType_t)0)\
    {\
    portRESET_READY_PRIORITY( ( uxPriority ), ( uxTopReadyPriority ) );\
    }\
    }
#else
#define taskRESET_READY_PRIORITY( uxPriority )\(6)
    {\
portRESET_READY_PRIORITY((uxPriority ), (uxTopReadyPriority));\
    }
#endif

#endif/* configUSE_PORT_OPTIMISED_TASK_SELECTION */
```

查找最高优先级的就绪任务有两种方法，具体由 configUSE_PORT_OPTIMISED_TASK_SELECTION这个宏控制，定义为0选择**通用方法**，定义为1选择**根据处理器优化的方法**，该宏默认在portmacro.h中定义为1，即使用优化过的方法，但是通用方法我们也讲解下。

##### 通用方法



##### 优化方法



#### 修改代码，支持多优先级

##### 修改任务控制块

在任务控制块中增加与优先级相关的成员。

```c
typedef struct tskTaskControlBlock
{
	volatile StackType_t    *pxTopOfStack;    /* 栈顶 */

	ListItem_t			    xStateListItem;   /* 任务节点 */
    
    StackType_t             *pxStack;         /* 任务栈起始地址 */
	                                          /* 任务名称，字符串形式 */
	char                    pcTaskName[ configMAX_TASK_NAME_LEN ];

    TickType_t xTicksToDelay;
    UBaseType_t			uxPriority;    
} tskTCB;
typedef tskTCB TCB_t;
```



##### 修改xTaskCreateStatic()函数

增加优先级形参，数值越大，优先级越高。

```c
TaskHandle_t xTaskCreateStatic(	TaskFunction_t pxTaskCode,           /* 任务入口 */
					            const char * const pcName,           /* 任务名称，字符串形式 */
					            const uint32_t ulStackDepth,         /* 任务栈大小，单位为字 */
					            void * const pvParameters,           /* 任务形参 */
                                UBaseType_t uxPriority,              /* 任务优先级，数值越大，优先级越高 */
					            StackType_t * const puxStackBuffer,  /* 任务栈起始地址 */
					            TCB_t * const pxTaskBuffer )         /* 任务控制块 */
{
	TCB_t *pxNewTCB;
	TaskHandle_t xReturn;

	if( ( pxTaskBuffer != NULL ) && ( puxStackBuffer != NULL ) )
	{		
		pxNewTCB = ( TCB_t * ) pxTaskBuffer; 
		pxNewTCB->pxStack = ( StackType_t * ) puxStackBuffer;

		/* 创建新的任务 */
		prvInitialiseNewTask( pxTaskCode, pcName, ulStackDepth, pvParameters,uxPriority, &xReturn, pxNewTCB);
        
		/* 将任务添加到就绪列表 */
		prvAddNewTaskToReadyList( pxNewTCB );

	}
	else
	{
		xReturn = NULL;
	}

	return xReturn;
}
```

**prvInitialiseNewTask()函数**

增加优先级形参和优先级初始化相关代码

```c
static void prvInitialiseNewTask( 	TaskFunction_t pxTaskCode,              /* 任务入口 */
									const char * const pcName,              /* 任务名称，字符串形式 */
									const uint32_t ulStackDepth,            /* 任务栈大小，单位为字 */
									void * const pvParameters,              /* 任务形参 */
                                    UBaseType_t uxPriority,                 /* 任务优先级，数值越大，优先级越高 */
									TaskHandle_t * const pxCreatedTask,     /* 任务句柄 */
									TCB_t *pxNewTCB )                       /* 任务控制块 */

{
	StackType_t *pxTopOfStack;
	UBaseType_t x;	
	
	/* 获取栈顶地址 */
	pxTopOfStack = pxNewTCB->pxStack + ( ulStackDepth - ( uint32_t ) 1 );
	//pxTopOfStack = ( StackType_t * ) ( ( ( portPOINTER_SIZE_TYPE ) pxTopOfStack ) & ( ~( ( portPOINTER_SIZE_TYPE ) portBYTE_ALIGNMENT_MASK ) ) );
	/* 向下做8字节对齐 */
	pxTopOfStack = ( StackType_t * ) ( ( ( uint32_t ) pxTopOfStack ) & ( ~( ( uint32_t ) 0x0007 ) ) );	

	/* 将任务的名字存储在TCB中 */
	for( x = ( UBaseType_t ) 0; x < ( UBaseType_t ) configMAX_TASK_NAME_LEN; x++ )
	{
		pxNewTCB->pcTaskName[ x ] = pcName[ x ];

		if( pcName[ x ] == 0x00 )
		{
			break;
		}
	}
	/* 任务名字的长度不能超过configMAX_TASK_NAME_LEN */
	pxNewTCB->pcTaskName[ configMAX_TASK_NAME_LEN - 1 ] = '\0';
    
    /* 初始化TCB中的xStateListItem节点 */
    vListInitialiseItem( &( pxNewTCB->xStateListItem ) );
    /* 设置xStateListItem节点的拥有者 */
	listSET_LIST_ITEM_OWNER( &( pxNewTCB->xStateListItem ), pxNewTCB );
	
    /* 初始化优先级 */
	if( uxPriority >= ( UBaseType_t ) configMAX_PRIORITIES )
	{
		uxPriority = ( UBaseType_t ) configMAX_PRIORITIES - ( UBaseType_t ) 1U;
	}
	pxNewTCB->uxPriority = uxPriority;
    
	/* 初始化任务栈 */
	pxNewTCB->pxTopOfStack = pxPortInitialiseStack( pxTopOfStack, pxTaskCode, pvParameters ); 
    
    /* 让任务句柄指向任务控制块 */
    if( ( void * ) pxCreatedTask != NULL )
	{		
		*pxCreatedTask = ( TaskHandle_t ) pxNewTCB;
	}
}
```

**prvAddNewTaskToReadyList()函数**

```c
static void prvAddNewTaskToReadyList( TCB_t *pxNewTCB )
{
	/* 进入临界段 */
	taskENTER_CRITICAL();
	{
		/* 全局任务计时器加一操作 */
        uxCurrentNumberOfTasks++;
        
        /* 如果pxCurrentTCB为空，则将pxCurrentTCB指向新创建的任务 */
		if( pxCurrentTCB == NULL )
		{
			pxCurrentTCB = pxNewTCB;

			/* 如果是第一次创建任务，则需要初始化任务相关的列表 */
            if( uxCurrentNumberOfTasks == ( UBaseType_t ) 1 )
			{
				/* 初始化任务相关的列表 */
                prvInitialiseTaskLists();
			}
		}
		else /* 如果pxCurrentTCB不为空，则根据任务的优先级将pxCurrentTCB指向最高优先级任务的TCB */
		{
				if( pxCurrentTCB->uxPriority <= pxNewTCB->uxPriority )
				{
					pxCurrentTCB = pxNewTCB;
				}
		}
		uxTaskNumber++;
        
		/* 将任务添加到就绪列表 */
        prvAddTaskToReadyList( pxNewTCB );

	}
	/* 退出临界段 */
	taskEXIT_CRITICAL();
}
```



##### 修改vTaskStartScheduler()函数

```c
void vTaskStartScheduler( void )
{
/*======================================创建空闲任务start==============================================*/     
    TCB_t *pxIdleTaskTCBBuffer = NULL;
    StackType_t *pxIdleTaskStackBuffer = NULL;
    uint32_t ulIdleTaskStackSize;
    
    /* 获取空闲任务的内存：任务栈和任务TCB */
    vApplicationGetIdleTaskMemory( &pxIdleTaskTCBBuffer, 
                                   &pxIdleTaskStackBuffer, 
                                   &ulIdleTaskStackSize );    
    
    xIdleTaskHandle = xTaskCreateStatic( (TaskFunction_t)prvIdleTask,              /* 任务入口 */
					                     (char *)"IDLE",                           /* 任务名称，字符串形式 */
					                     (uint32_t)ulIdleTaskStackSize ,           /* 任务栈大小，单位为字 */
					                     (void *) NULL,                            /* 任务形参 */
                                         (UBaseType_t) tskIDLE_PRIORITY,           /* 任务优先级，数值越大，优先级越高 */
					                     (StackType_t *)pxIdleTaskStackBuffer,     /* 任务栈起始地址 */
					                     (TCB_t *)pxIdleTaskTCBBuffer );           /* 任务控制块 */
    /* 将任务添加到就绪列表 */                                 
    //vListInsertEnd( &( pxReadyTasksLists[0] ), &( ((TCB_t *)pxIdleTaskTCBBuffer)->xStateListItem ) );
/*======================================创建空闲任务end================================================*/
                                         
    /* 手动指定第一个运行的任务 */
    //pxCurrentTCB = &Task1TCB;
    
    /* 启动调度器 */
    if( xPortStartScheduler() != pdFALSE )
    {
        /* 调度器启动成功，则不会返回，即不会来到这里 */
    }
}
```

* 创建空闲任务时，优先级配置为tskIDLE_PRIORITY，该宏在task.h中定义，默认为0，表示空闲任务的优先级为最低
* 刚刚我们修改了创建任务函数xTaskCreateStatic()，在创建任务时，就已经将任务添加到了就绪列表，这里将注释掉

##### 修改vTaskDelay()函数

增加了将任务从就绪列表移除的操作

```c
void vTaskDelay( const TickType_t xTicksToDelay )
{
    TCB_t *pxTCB = NULL;
    
    /* 获取当前任务的TCB */
    pxTCB = pxCurrentTCB;
    
    /* 设置延时时间 */
    pxTCB->xTicksToDelay = xTicksToDelay;
    
    /* 将任务从就绪列表移除 */
    //uxListRemove( &( pxTCB->xStateListItem ) );
    taskRESET_READY_PRIORITY( pxTCB->uxPriority );
    
    /* 任务切换 */
    taskYIELD();
}
```

* 将任务从就绪列表移除本应该完成两个操作：将任务从就绪列表移除本应该完成两个操作：1个是将任务从就绪列表移除， 由函数uxListRemove()来实现；另一个是根据优先级将优先级位图表uxTopReadyPriority中对应的位清零，由函 数taskRESET_READY_PRIORITY()来实现。但是鉴于我们目前的时基更新函数xTaskIncrementTick还是需要通过 扫描就绪列表的任务来判断任务的延时时间是否到期，所以不能将任务从就绪列表移除。

##### 修改vTaskSwitchContext()函数

在新的任务切换函数vTaskSwitchContext()中，不再是手动的让pxCurrentTCB指针在任务1、任务2和空闲任务中切换， 而是直接调用函数taskSELECT_HIGHEST_PRIORITY_TASK()寻找到优先级最高的就绪任务的TCB，然后更新到 pxCurrentTCB。

```c
void vTaskSwitchContext( void )
{
	/* 获取优先级最高的就绪任务的TCB，然后更新到pxCurrentTCB */
    taskSELECT_HIGHEST_PRIORITY_TASK();
}
```

##### 修改xTaskIncrementTick()函数

增加当延时时间到，将任务就绪的代码。

```c
void xTaskIncrementTick( void )
{
    TCB_t *pxTCB = NULL;
    BaseType_t i = 0;
    
    const TickType_t xConstTickCount = xTickCount + 1;
    xTickCount = xConstTickCount;

    
    /* 扫描就绪列表中所有线程的remaining_tick，如果不为0，则减1 */
	for(i=0; i<configMAX_PRIORITIES; i++)
	{
        pxTCB = ( TCB_t * ) listGET_OWNER_OF_HEAD_ENTRY( ( &pxReadyTasksLists[i] ) );
		if(pxTCB->xTicksToDelay > 0)
		{
			pxTCB->xTicksToDelay --;
            
            /* 延时时间到，将任务就绪 */
            if( pxTCB->xTicksToDelay ==0 )
            {
                taskRECORD_READY_PRIORITY( pxTCB->uxPriority );
            }
		}
	}
    
    /* 任务切换 */
    portYIELD();
}
```



#### main函数

```c
int main(void)
{	
    /* 硬件初始化 */
	/* 将硬件相关的初始化放在这里，如果是软件仿真则没有相关初始化代码 */ 

    
    /* 创建任务 */
    Task1_Handle = xTaskCreateStatic( (TaskFunction_t)Task1_Entry,   /* 任务入口 */
					                  (char *)"Task1",               /* 任务名称，字符串形式 */
					                  (uint32_t)TASK1_STACK_SIZE ,   /* 任务栈大小，单位为字 */
					                  (void *) NULL,                 /* 任务形参 */
                                      (UBaseType_t) 1,               /* 任务优先级，数值越大，优先级越高 */
					                  (StackType_t *)Task1Stack,     /* 任务栈起始地址 */
					                  (TCB_t *)&Task1TCB );          /* 任务控制块 */
    /* 将任务添加到就绪列表 */                                 
    //vListInsertEnd( &( pxReadyTasksLists[1] ), &( ((TCB_t *)(&Task1TCB))->xStateListItem ) );
                                
    Task2_Handle = xTaskCreateStatic( (TaskFunction_t)Task2_Entry,   /* 任务入口 */
					                  (char *)"Task2",               /* 任务名称，字符串形式 */
					                  (uint32_t)TASK2_STACK_SIZE ,   /* 任务栈大小，单位为字 */
					                  (void *) NULL,                 /* 任务形参 */
                                      (UBaseType_t) 2,               /* 任务优先级，数值越大，优先级越高 */                                          
					                  (StackType_t *)Task2Stack,     /* 任务栈起始地址 */
					                  (TCB_t *)&Task2TCB );          /* 任务控制块 */ 
    /* 将任务添加到就绪列表 */                                 
    //vListInsertEnd( &( pxReadyTasksLists[2] ), &( ((TCB_t *)(&Task2TCB))->xStateListItem ) );
                                      
    /* 启动调度器，开始多任务调度，启动成功则不返回 */
    vTaskStartScheduler();                                      
    
    for(;;)
	{
		/* 系统启动成功不会到达这里 */
	}
}
```

* 设置任务的优先级，数字优先级越高，逻辑优先级越高
* 将任务添加到就绪列表部分代码删除，因为在任务创建函数xTaskCreateStatic()中，已经调用函数prvAddNewTaskToReadyList()将任务插入到了就绪列表。

### 任务延时列表的实现

在本章之前，为了实现任务的阻塞延时，在任务控制块中内置了一个延时变量xTicksToDelay。每当任务需要延时的时候， 就初始化xTicksToDelay需要延时的时间，然后将任务挂起，这里的挂起只是将任务在优先级位图表uxTopReadyPriority 中对应的位清零，并不会将任务从就绪列表中删除。当每次时基中断（SysTick中断）来临时，就扫描就绪列表中的每个任 务的xTicksToDelay，如果xTicksToDelay大于0则递减一次，然后判断xTicksToDelay是否为0，如果为0则表示延时时间 到，将该任务就绪（即将任务在优先级位图表uxTopReadyPriority中对应的位置位），然后进行任务切换。这种延时的缺点是，在每个时基中断中需要对所有任务都扫描一遍，费时，优点是容易理解。之所以先这样讲解是为了慢慢地过度到 FreeRTOS任务延时列表的讲解。

* **FreeRTOS的任务**

在FreeRTOS中，任务的调度通过**优先级**和**状态**来管理。任务的状态可以是就绪、运行、挂起或延时。任务延时列表是用于管理处于延时状态的任务的机制。延时列表存储了那些调用延时函数（vTaskDelay）并进入阻塞状态的任务。

* **任务处于延时状态的原因**

1. 控制任务的执行频率
2. 等待时间或资源
3. 节省处理器资源
4. 轮询操作
5. 协同多任务运行

* **时间滴答定时器**

FreeRTOS 中的时间滴答计数器是一个无符号整数（通常是32位），它会随着系统时间的推进逐渐增加。在每次时间滴答中断时，该计数器会递增。当达到该整数的最大值时，时间滴答计数器会溢出，重新回到0。

#### 任务延时列表的工作原理

在FreeRTOS中，有一个任务延时列表（实际上有两个，为了方便讲解原理，我们假装合并为一个，其实两个的作用是一样的）， 当任务需要延时的时候，则先将任务挂起，即先将任务从就绪列表删除，然后插入到任务延时列表，同时更新下一个任务的 解锁时刻变量：xNextTaskUnblockTime的值。

xNextTaskUnblockTime的值等于系统时基计数器的值xTickCount加上任务需要延时的值xTicksToDelay。当系统时基计数 器xTickCount的值与xNextTaskUnblockTime相等时，就表示有任务延时到期了，需要将该任务就绪。与RT-Thread和μC/OS 在解锁延时任务时要扫描定时器列表这种时间不确定性的方法相比，FreeRTOS这个xNextTaskUnblockTime全局变量设计的非常巧妙。

任务延时列表表维护着一条双向链表，每个节点代表了正在延时的任务，节点按照延时时间大小做升序排列。当每次时基中断（SysTick中断）来临时，就拿系统时基计数器的值xTickCount与下一个任务的解锁时刻变量xNextTaskUnblockTime的 值相比较，如果相等，则表示有任务延时到期，需要将该任务就绪，否则只是单纯地更新系统时基计数器xTickCount的值， 然后进行任务切换。

#### 实现任务延时列表

##### 定义任务延时列表

```c
static List_t xDelayedTaskList1;
static List_t xDelayedTaskList2;
static List_t * volatile pxDelayedTaskList;
static List_t * volatile pxOverflowDelayedTaskList;
```

* FreeRTOS定义了两个任务延时列表，当系统时基计数器xTickCount没有溢出时，用一条列表，当xTickCount溢出后，用另外一条列表。
* 任务延时列表指针，指向xTickCount没有溢出时使用的那条列表。
* 任务延时列表指针，指向xTickCount溢出时使用的那条列表。
* 为什么需要两个延时列表？

使用两个延时列表的原因与**时间滴答计数器的溢出机制**直接相关。假设只有一个延时列表，并且任务被延时到的时间超过了当前时间滴答计数器的范围，就会出现问题：我们无法简单地判断一个任务的延时是否已经结束。通过使用两个列表，可以有效管理处于不同时间范围内的任务。

##### 任务延时列表初始化

任务延时列表属于任务列表的一种，在prvInitialiseTaskLists()函数中初始化

```c
void prvInitialiseTaskLists( void )
{
    UBaseType_t uxPriority;
    
    /* 初始化就绪列表 */
    for( uxPriority = ( UBaseType_t ) 0U; uxPriority < ( UBaseType_t ) configMAX_PRIORITIES; uxPriority++ )
	{
		vListInitialise( &( pxReadyTasksLists[ uxPriority ] ) );
	}
    
    vListInitialise( &xDelayedTaskList1 );
	vListInitialise( &xDelayedTaskList2 );
    
    pxDelayedTaskList = &xDelayedTaskList1;
	pxOverflowDelayedTaskList = &xDelayedTaskList2;
}
```

##### 定义xNextTaskUnblockTime

xNextTaskUnblockTime是一个在task.c中定义的静态变量，用于表示下一个任务的解锁时刻。xNextTaskUnblockTime的值等 于系统时基计数器的值xTickCount加上任务需要延时值xTicksToDelay。当系统时基计数器xTickCount的值与 xNextTaskUnblockTime相等时，就表示有任务延时到期了，需要将该任务就绪。

##### 初始化xNextTaskUnblockTime

```C
void vTaskStartScheduler( void )
{
/*======================================创建空闲任务start==============================================*/     
    TCB_t *pxIdleTaskTCBBuffer = NULL;
    StackType_t *pxIdleTaskStackBuffer = NULL;
    uint32_t ulIdleTaskStackSize;
    
    /* 获取空闲任务的内存：任务栈和任务TCB */
    vApplicationGetIdleTaskMemory( &pxIdleTaskTCBBuffer, 
                                   &pxIdleTaskStackBuffer, 
                                   &ulIdleTaskStackSize );    
    
    xIdleTaskHandle = xTaskCreateStatic( (TaskFunction_t)prvIdleTask,              /* 任务入口 */
					                     (char *)"IDLE",                           /* 任务名称，字符串形式 */
					                     (uint32_t)ulIdleTaskStackSize ,           /* 任务栈大小，单位为字 */
					                     (void *) NULL,                            /* 任务形参 */
                                         (UBaseType_t) tskIDLE_PRIORITY,           /* 任务优先级，数值越大，优先级越高 */
					                     (StackType_t *)pxIdleTaskStackBuffer,     /* 任务栈起始地址 */
					                     (TCB_t *)pxIdleTaskTCBBuffer );           /* 任务控制块 */
/*======================================创建空闲任务end================================================*/ 
    xNextTaskUnblockTime = portMAX_DELAY;
    xTickCount = ( TickType_t ) 0U;

    /* 启动调度器 */
    if( xPortStartScheduler() != pdFALSE )
    {
        /* 调度器启动成功，则不会返回，即不会来到这里 */
    }
}
```



#### 修改代码，支持任务延时列表

##### 修改xTaskDelay()函数

```c
void vTaskDelay( const TickType_t xTicksToDelay )
{
    TCB_t *pxTCB = NULL;
    
    /* 获取当前任务的TCB */
    pxTCB = pxCurrentTCB;
    
    /* 设置延时时间 */
    //pxTCB->xTicksToDelay = xTicksToDelay;
    
    /* 将任务插入到延时列表 */
    prvAddCurrentTaskToDelayedList( xTicksToDelay );
    
    /* 任务切换 */
    taskYIELD();
}
```

* 从本章开始，添加了任务的延时列表，延时的时候不用依赖任务TCB中内置的延时变量xTicksToDelay
* 将任务插入到延时列表。函数prvAddCurrentTaskToDelayedList()在task.c中定义。

**prvAddCurrentTaskToDelayedList()函数**

### 支持时间片

FreeRTOS中的时间片调度是指系统在多任务运行时，将CPU时间划分成若干小片段，每个任务分配一定的时间片进行运行，当一个任务运行到它的时间片耗尽时，操作系统会暂停该任务的执行，将CPU资源分配给其他同优先级的任务。这种机制能够让多个任务在同等优先级的情况下**轮流使用CPU资源**，从而实现任务的公平调度。

* **同优先级任务**：时间片调度只在相同优先级的任务之间生效。如果不同任务的优先级不同，FreeRTOS将执行高优先级任务，低优先级任务只能等到高优先级任务全部阻塞或结束后才能执行。
* **时间片大小**：FreeRTOS中的时间片是由滴答时钟决定的，通常每经过一个滴答时钟周期，操作系统会检查是否需要进行任务切换。如果多个相同优先级的任务处于就绪状态，那么FreeRTOS会在每个滴答时钟周期内轮流切换这些任务。
* **任务切换**：当一个任务的时间片耗尽后，FreeRTOS会触发任务切换，将CPU控制权交给下一个就绪的、相同优先级的任务。这种任务切换是通过操作系统内核管理的，不需要用户干预。
* **可配置性**：时间片调度的行为是可配置的。在FreeRTOS配置文件中，可以通过宏定义`configUSE_PREEMPTION`和`configUSE_TIME_SLICING`来启用或禁用时间片调度。`configUSE_TIME_SLICING`默认为启用状态。

* **滴答时钟配置**

假设在STM32微控制器上使用SysTick定时器，并且主时钟频率为72MHz，期望的滴答频率为1000Hz，则`FreeRTOSConfig.h`中的配置可能如下：

```c
#define configTICK_RATE_HZ			( ( TickType_t ) 1000 )
```

SysTick定时器的重载值将配置为71999，以确保每1ms触发一次滴答中断。

#### 时间片测试实验

假设目前系统中有三个任务就绪（算上空闲任务就是4个），任务1和任务2的优先级为2，任务3的优先级为3。为了方便在逻辑分析仪中地分辨出任务1和任务2使用的时间片大小，任务1和任务2的主体编写成一个无限循环函数， 不会阻塞，任务3的阻塞时间设置为1个tick。任务1和任务2的任务主体编写为一个无限循环，这就意味着，优先级 低于2的任务就会被饿死，得不到执行，比如空闲任务。在真正的项目中，并不会这样写，这里只是为了实验方便。

#### main函数

#### 实验现象

#### 原理分析

之所以在同一个优先级下可以有多个任务，最终还是得益于`taskRESET_READY_PRIORITY()`和 `taskSELECT_HIGHEST_PRIORITY_TASK()`这两个函函数的实现方法。接下来我们分析下这两个 函数是如何在同一个优先级下有多个任务的时候起作用的。

系统在任务切换的时候总会从就绪列表中寻找优先级最高的任务来执行，寻找优先级最高的任务这个功能 由`taskSELECT_HIGHEST_PRIORITY_TASK()`函数来实现

##### taskSELECT_HIGHEST_PRIORITY_TASK()函数

```c
#define taskSELECT_HIGHEST_PRIORITY_TASK()
{
    UBaseType_t uxTopPriority;
    /* 寻找就绪任务的最高优先级 */(1)
    portGET_HIGHEST_PRIORITY( uxTopPriority, uxTopReadyPriority );
    /* 获取优先级最高的就绪任务的TCB，然后更新到pxCurrentTCB */(2)
    listGET_OWNER_OF_NEXT_ENTRY( pxCurrentTCB,
    &( pxReadyTasksLists[ uxTopPriority ] ) );
}
```

* 寻找就绪任务的最高优先级。即根据优先级位图表uxTopReadyPriority找到就绪任 务的最高优先级，然后将优先级暂存在uxTopPriority。
* 获取优先级最高的就绪任务的TCB，然后更新到pxCurrentTCB。目前我们的实验是在 优先级2上有任务1和任务2，假设任务1运行了一个tick，那接下来再从对应优先级2的就绪列表上选择任务来运行 就应该是选择任务2？怎么选择，代码上怎么实现？奥妙就在listGET_OWNER_OF_NEXT_ENTRY()函数中，该函数 在list.h中定义

```c
#define listGET_OWNER_OF_NEXT_ENTRY( pxTCB, pxList )
{
    List_t * const pxConstList = ( pxList );
    /* 节点索引指向链表第一个节点调整节点索引指针，指向下一个节点，
如果当前链表有N个节点，当第N次调用该函数时，pxIndex则指向第N个节点 */
    ( pxConstList )->pxIndex = ( pxConstList )->pxIndex->pxNext;
    /* 当遍历完链表后，pxIndex回指到根节点 */\
    if( ( void * ) ( pxConstList )->pxIndex == ( void * ) &( ( pxConstList )->xListEnd ) )
    {
        ( pxConstList )->pxIndex = ( pxConstList )->pxIndex->pxNext;
    }
    /* 获取节点的OWNER，即TCB */
    ( pxTCB ) = ( pxConstList )->pxIndex->pvOwner;
}
```

##### taskRESET_READY_PRIORITY()函数

```c
#define taskRESET_READY_PRIORITY( uxPriority )
{
    if( listCURRENT_LIST_LENGTH( &( pxReadyTasksLists[ ( uxPriority ) ] ) )
                            == ( UBaseType_t ) 0 )
    {
        portRESET_READY_PRIORITY( ( uxPriority ),
                                ( uxTopReadyPriority ) );
    }
}
```

taskRESET_READY_PRIORITY()函数的妙处在于清除优先级位图表uxTopReadyPriority中相应的位时候，会先判断 当前优先级链表下是否还有其他任务，如果有则不清零。假设当前实验中，任务1会调用vTaskDelay()，会将自己挂起，只能是将任务1从就绪列表删除，不能将任务1在优先级位图表uxTopReadyPriority中对应的位清0，因为该优先 级下还有任务2，否则任务2将得不到执行。

#### 修改代码，支持优先级

##### xPortSysTickHandler()函数

### 移植FreeRTOS到STM32

🔗：[2. 移植FreeRTOS到STM32 — FreeRTOS内核实现与应用开发实战指南—基于STM32 文档 (embedfire.com)](https://doc.embedfire.com/rtos/freertos/zh/latest/application/porting_to_stm32.html)

#### 获取STM32的裸机工程模板

#### 下载FreeRTOS V9.0.0源码

🔗：http://www.freertos.org/

🔗：https://sourceforge.net/projects/freertos/files/FreeRTOS/

#### FreeRTOS文件夹内容简介

FreeRTOS文件夹下的 Source文件夹里面包含的是FreeRTOS内核的源代码，我们移植FreeRTOS的时候就需要这部分源代码；FreeRTOS文件夹下的Demo文件夹里面包含了F reeRTOS官方为各个单片机移植好的工程代码，FreeRTOS为了推广自己，会给各种半导体厂商的评估板写好完整的工程程序，这些程序就放在Demo这个目录下，这部分Demo非常有参考价值。我们把FreeRTOS到STM32的时候，FreeRTOSConfig.h这个头文件就是从这里拷贝过来的，下面我 们对FreeRTOS的文件夹进行分析说明。

##### FreeRTOS文件夹

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240829115510740.png" alt="image-20240829115510740" style="zoom:50%;" />

* portable文件夹内容

打开RVDS文件夹，下面包含了各种处理相关的文件夹。FreeRTOS是一个软件，单片机是一个硬件，FreeRTOS要想运行在一个单片机上，它们就必须关联在一起。这部分关联的文件叫做接口文件，通常由汇编和C联合编写。这些接口文件都是跟硬件密切相关的，不同的硬件接口文件是不一样的，但都大同小异。编写这些接口文件的过程我们就叫移植，移植的过程通常由FreeRTOS和mcu原厂的人来负责，移植好的这些接口文件就放在RVDS这个文件夹的目录下。

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240829115742485.png" alt="image-20240829115742485" style="zoom:50%;" />

FreeRTOS为我们提供了cortex-M0、M3、M4和M7等内核的单片机的接口文件，只要是使用了这些内核的MCU都可以使用里面的接口文件。port.c文件里面的内容是由FreeRTOS官方的技术人员为Cortex-M3内核的处理器写的接口文件，里面核心的上下文切换代码是由汇编语言编写而成。portmacro.h则是port.c对应的头文件，主要是一些数据类型和宏定义。

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240829224039536.png" alt="image-20240829224039536" style="zoom:50%;" />

MemMang文件夹下存放的是跟内存管理相关的，总共有五个heap文件以及一个readme说明文件，这五个heap文件在移植的时候必须使用一个，因为FreeRTOS在创建内核对象的时候使用的是动态分配内存，而这些动态内存分配的函数则在这几个文件里面实现，不同的分配算法会导致不同 的效率与结果，后面在内存管理中我们会讲解每个文件的区别，由于现在是初学，所以我们选用heap4.c即可。

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240829224300800.png" alt="image-20240829224300800" style="zoom:50%;" />



##### FreeRTOS-Plus文件夹

FreeRTOS-Plus文件夹里面包含的是第三方的产品，一般我们不需要使用，FreeRTOS-Plus的预配置演示项目组件（组件大多数都要收费），大多数演示项目都是在Windows环境中运行的，使用FreeRTOS windows模拟器，所以暂时不需要关注这个文件夹。

##### HTML文件

一些直接可以打开的网页文件，里面包含一些关于FreeRTOS的介绍，是FreeRTOS官方人员所写，所以都是英文的，有兴趣可以打开看看，具体相关内容可以看HTML文件名称。

#### 往裸机工程添加FreeRTOS源码

##### 提取FreeRTOS最简源码

下面是提取源码的操作过程：

1. 首先在我们的STM32裸机工程模板根目录下新建一个文件夹，命名为“FreeRTOS”，并且在FreeRTOS文件夹下新建两个空文件夹，分别命名为“src”与“port”，src文件夹用于保存FreeRTOS中的核心源文件，也就是我们常说的‘.c文件’，port文件夹用于保存内存管理以及处理器架构相关 代码，这些代码FreeRTOS官方已经提供给我们的，直接使用即可，在前面已经说了，FreeRTOS是软件，我们的开发版是硬件，软硬件必须有桥梁来连接，这些与处理器架构相关的代码，可以称之为RTOS硬件接口层，它们位于FreeRTOS/Source/Portable文件夹下。
2. 打开FreeRTOS V9.0.0源码，在“FreeRTOSv9.0.0FreeRTOSSource”目录下找到所有的‘.c文件’，将它们拷贝到我们新建的src文件夹中。
3. 打开FreeRTOS V9.0.0源码，在“FreeRTOSv9.0.0FreeRTOSSourceportable”目录下找到“MemMang”文件夹与“RVDS”文件夹，将它们拷贝到我们新建的port文件夹中。
4. 打开FreeRTOS V9.0.0源码，在“FreeRTOSv9.0.0\ FreeRTOSSource”目录下找到“include”文件夹，它是我们需要用到FreeRTOS的一些头文件，将它直接拷贝到我们新建的FreeRTOS文件夹中，完成这一步之后就可以看到我们新建的FreeRTOS文件夹已 经有3个文件夹，这3个文件夹就包含FreeRTOS的核心文件，至此，FreeRTOS的源码就提取完成。

##### 拷贝FreeRTOS到裸机工程根目录

鉴于FreeRTOS容量很小，我们直接将刚刚提取的整个FreeRTOS文件夹拷贝到我们的STM32裸机工程里面，让整个FreeRTOS跟随我们的工程一起发布，使用这种方法打包的FreeRTOS 工程，即使是将工程拷贝到一台没有安装FreeRTOS支持包（MDK中有FreeRTOS的支持包）的电脑上面都是可以直接使用的，因为工程已经包含了FreeRTOS的源码。

##### 拷贝FreeRTOSConfig.h文件到user文件夹

FreeRTOSConfig.h文件是FreeRTOS的工程配置文件，因为FreeRTOS是可以裁剪的实时操作内核，应用于不同的处理器平台，用户可以通过修改这个FreeRTOS内核的配置头文件来裁剪FreeRTOS的功能，所以我们把它拷贝一份放在user这个文件夹下面。

打开FreeRTOSv9.0.0源码，在“FreeRTOSv9.0.0FreeRTOSDemo”文件夹下面找到“CORTEX_STM32F103_Keil”这个文件夹，双击打开，在其根目录下找到这个“FreeRTOSConfig.h”文件，然后拷贝到我们工程的user文件夹下即可，等下我们需要对 这个文件进行修改。user文件夹，见名知义我们就可以知道里面存放的文件都是用户自己编写的。

##### 添加FreeRTOS源码到工程组文件夹

* 新建FreeRTOS/src和FreeRTOS/port组
* 指定FreeRTOS头文件的路径

至此，FreeRTOS的整体工程基本移植完毕，我们需要修改FreeRTOS配置文件，按照我们的需求来进行修改。

#### 修改FreeRTOSConfig.h

FreeRTOSConfig.h是直接从demo文件夹下面拷贝过来的，该头文件对裁剪整个FreeRTOS所需的功能的宏均做了定义，有些宏定义被使能，有些宏定义被失能，一开始我们只需要配置最简单的功能即可。要想随心所欲的配置FreeRTOS的功能，我们必须对这些宏定义的功能有所掌握，下面我们先简单的介 绍下这些宏定义的含义，然后再对这些宏定义进行修改。

注意：此FreeRTOSConfig.h文件内容与我们从demo移植过来的FreeRTOSConfig.h文件不一样，因为这是我们野火修改过的FreeRTOSConfig.h文件，并不会影响FreeRTOS的功能，我们只是添加了一些中文注释，并且把相关的头文件进行分类，方便查找宏定义已经阅读，仅此而 已。强烈建议使用我们修加工过的FreeRTOSConfig.h文件。

##### FreeRTOSConfig.h文件内容讲解

* `configUSE_PREEMPTION`：FreeRTOS使用抢占式调度器；置0：FreeRTOS使用协作式调度器（时间片）。抢占式调度：在这种调度方式中，系统总是选择优先级最高的任务进行调度，并且一旦高优先级的任务准备就绪之后，它就会马上被调度而不等待低优先级的任务主动放弃CPU，高优先级的任务抢占了低优先级任务的CPU使用权，这就是抢占，在实际操作系统中，这样子的方式往往是最适用的。而协作式调度则是由任务主动放弃CPU，然后才进行任务调度。
* `configUSE_TIME_SLICING`：使能时间片调度(默认式使能的)。当优先级相同的时候，就会采用时间片调度，这意味着RTOS调度器总是运行处于最高优先级的就绪任务，在每个FreeRTOS系统节拍中断时在相同优先级的多个任务间进行任务切换。如果宏`configUSE_TIME_SLICING`设置为0 ，FreeRTOS调度器仍然总是运行处于最高优先级的就绪任务，但是当RTOS 系统节拍中断发生时，相同优先级的多个任务之间不再进行任务切换，而是在执行完高优先级的任务之后才进行任务切换。一般来说，FreeRTOS默认支持32个优先级，很少情况会把32个优先级全用完，所以，官方建议采用抢占式调度。
* `configUSE_PORT_OPTIMISED_TASK_SELECTION`：FreeRTOS支持两种方法选择下一个要执行的任务：一个是软件方法扫描就绪链表，这种方法我们通常称为通用方法，`configUSE_PORT_OPTIMISED_TASK_SELECTION` 为 0 或者硬件不支持特殊方法，才使用通用方法获取下一个即将运行的任务 ，通用方法可以用于所有FreeRTOS支持的硬件平台，因为这种方法是完全用C语言实现，所以效率略低于特殊方法，但不强制要求限制最大可用优先级数目；另一个是硬件方式查找下一个要运行的任务，必须将`configUSE_PORT_OPTIMISED_TASK_SELECTION`设置为1，因为是必须依赖一个或 多个特定架构的汇编指令（一般是类似计算前导零[CLZ]指令，在M3、M4、M7内核中都有，这个指令是用来计算一个变量从最高位开始的连续零的个数），所以效率略高于通用方法，但受限于硬件平台，一般强制限定最大可用优先级数目为32，这也是FreeRTOS官方为什么推荐使用32位优先级的原因。
* `configUSE_TICKLESS_IDLE`：低功耗tickless模式。置1：使能低功耗tickless模式；置0：保持系统节拍（tick）中断一直运行，如果不是用于低功耗场景，我们一般置0即可。
* `configCPU_CLOCK_HZ`：配置CPU内核时钟频率，也就是CPU指令执行频率，通常称为Fclk ， Fclk为供给CPU内核的时钟信号，我们所说的cpu主频为 XX MHz，就是指的这个时钟信号，相应的，1/Fclk即为CPU时钟周期，在野火STM32霸道开发板上系统时钟为SystemCoreClock = SYSCLK_FREQ_72MHz，也就是72MHz。
* `configTICK_RATE_HZ`：FreeRTOS系统节拍中断的频率。表示操作系统每1秒钟产生多少个tick，tick即是操作系统节拍的时钟周期，时钟节拍就是系统以固定的频率产生中断（时基中断），并在中断中处理与时间相关的事件，推动所有任务向前运行。时钟节拍需要依赖于硬件定时器，在STM32 裸机程序中经常使用的SysTick 时钟是MCU的内核定时器，通常都使用该定时器产生操作系统的时钟节拍。在FreeRTOS中，系统延时和阻塞时间都是以tick为单位，配置`configTICK_RATE_HZ`的值可以改变中断的频率，从而间接改变了FreeRTOS的时钟周期（T=1/f）。我们设置为10 00，那么FreeRTOS的时钟周期为1ms，过高的系统节拍中断频率也意味着FreeRTOS内核占用更多的CPU时间，因此会降低效率，一般配置为100~1000即可。
* `configMAX_PRIORITIES`：可使用的最大优先级，默认为32即可，官方推荐的也是32。每一个任务都必须被分配一个优先级，优先级值从0~ （configMAX_PRIORITIES - 1）之间。低优先级数值表示低优先级任务。空闲任务的优先级为0（tskIDLE_PRIORITY），因此它是最低优先级任务。FreeRTOS调度器将确保处于就绪态的高优先级任务比同样处于就绪状态的低优先级任务优先获取处理器时间。换句话说，**FreeRTOS运行的永远是处于就绪态的高优先级任务**。**处于就绪状态的相同优先级任务使用时间片调度机制共享处理器时间**。
* `configMINIMAL_STACK_SIZE`：空闲任务默认使用的栈大小，默认为128字即可（在M3、M4、M7中为128*4字节），栈大小不是以字节为单位而是以字为单位的，比如在32位架构下，栈大小为100表示栈内存占用400字节的空间。
* `configMAX_TASK_NAME_LEN`：任务名字字符串长度，这个宏用来定义该字符串的最大长度。这里定义的长度包括字符串结束符’0’。
* `configUSE_16_BIT_TICKS`：系统节拍计数器变量数据类型，1表示为16位无符号整形，0表示为32位无符号整形，STM32是32位机器，所以默认使用为0即可，这个值位数的大小决定了能计算多少个tick，比如假设系统以1ms产生一个tick中断的频率计时，那么32位无符号整形的值则可以计算4 294967295个tick，也就是系统从0运行到4294967.295秒的时候才溢出，转换为小时的话，则能运行1193个小时左右才溢出，当然，溢出就会重置时间，这点完全不用担心；而假如使用16位无符号整形的值，只能计算65535个tick，在65.535秒之后就会溢出，然后重置。
* `configIDLE_SHOULD_YIELD`：控制任务在空闲优先级中的行为，空闲任务放弃CPU使用权给其他同优先级的用户任务。仅在满足下列条件后，才会起作用，1：启用抢占式调度；2：用户任务优先级与空闲任务优先级相等。一般不建议使用这个功能，能避免尽量避免，1：设置用户任务优先级比空闲任务优先级高，2：这个宏定义配置为0。
* `configUSE_QUEUE_SETS`：启用消息队列，消息队列是FreeRTOS的IPC通信的一种，用于传递消息。
* `configUSE_TASK_NOTIFICATIONS`：开启任务通知功能，默认开启。每个FreeRTOS任务具有一个32位的通知值，FreeRTOS任务通知是直接向任务发送一个事件，并且接收任务的通知值是可以选择的，任务通过接收到的任务通知值来解除任务的阻塞状态（假如因等待该任务通知而进入阻塞状态）。相对于队列、 二进制信号量、计数信号量或事件组等IPC通信，使用任务通知显然更灵活。官方说明：相比于使用信号量解除任务阻塞，使用任务通知可以快45%（使用GCC编译器，-o2优化级别），并且使用更少的RAM。
* `configUSE_MUTEXES`：使用互斥信号量。
* `configUSE_RECURSIVE_MUTEXES`：使用递归互斥信号量。
* `configUSE_COUNTING_SEMAPHORES`：使用计数信号量。
* `configQUEUE_REGISTRY_SIZE`：设置可以注册的信号量和消息队列个数，用户可以根据自己需要修改即可，RAM小的芯片尽量裁剪得小一些。
* `configUSE_APPLICATION_TASK_TAG`：支持动态分配申请，一般在系统中采用的内存分配都是动态内存分配。FreeRTOS同时也支持静态分配内存，但是常用的就是动态分配了。
* `configTOTAL_HEAP_SIZE`：FreeRTOS内核总计可用的有效的RAM大小，不能超过芯片的RAM大小，一般来说用户可用的内存大小会小于`configTOTAL_HEAP_SIZE`定义的大小，因为系统本身就需要内存。每当创建任务、队列、互斥量、软件定时器或信号量时，FreeRTOS内核会 为这些内核对象分配RAM，这里的RAM都属于`configTOTAL_HEAP_SIZE`指定的内存区。
* `configUSE_IDLE_HOOK`：配置空闲钩子函数，钩子函数是类似一种回调函数，在任务执行到某个点的时候，跳转到对应的钩子函数执行，这个宏定义表示是否启用空闲任务钩子函数，这个函数由用户来实现，但是FreeRTOS规定了函数的名字和参数：void vApplicationIdleHook(void)，我们自定义的钩子函数不允许出现阻塞的情况。
* `configUSE_MALLOC_FAILED_HOOK`
* `configCHECK_FOR_STACK_OVERFLOW`
* `configGENERATE_RUN_TIME_STATS`
* `configUSE_TRACE_FACILITY`
* `configUSE_STATS_FORMATTING_FUNCTIONS`

##### FreeRTOSConfig.h文件修改

FreeRTOSConfig.h头文件的内容修改的不多，具体是：修改与对应开发板的头文件，如果是使用野火STM32F1的开发板，则包含F1的头文件#include “stm32f10x.h”，同理是使用了其他系列的开发板，则包含与开发板对应的头文件即可，当然还需要包含我们的串口的头文件“bsp_usart.h”，因为在我们FreeRTOSConfig.h中实现了断言操作，需要打印一些信息。其他根据需求修改即可，具体见代码清单11‑2的加粗部分。

提示：虽然FreeRTOS中默认是打开很多宏定义的，但是用户还是要根据需要选择打开与关闭，因为这样子的系统会更适合用户需要，更严谨与更加节省系统资源。

#### 修改stm32f10x_it.c

SysTick中断服务函数是一个非常重要的函数，FreeRTOS所有跟时间相关的事情都在里面处理，SysTick就是FreeRTOS的一个心跳时钟，驱动着FreeRTOS的运行，就像人的心跳一样，假如没有心跳，我们就相当于“死了”，同样的，FreeRTOS没有了心跳，那么它就会卡死在某个地方，不能进行任务调度，不能运行任何的东西，因此我们需要实现一个FreeRTOS的心跳时钟，FreeRTOS帮我们实现了SysTick的启动的配置：在port.c文件中已经实现vPortSetupTimerInterrupt()函数，并且FreeRTOS通用的SysTick中断服务函数也实现了：在port.c文 件中已经实现xPortSysTickHandler()函数，所以移植的时候只需要我们在stm32f10x_it.c文件中实现我们对应（STM32）平台上的SysTick_Handler()函数即可。FreeRTOS为开发者考虑得特别多，PendSV_Handler()与SVC_Handler()这两 个很重要的函数都帮我们实现了，在在port.c文件中已经实现xPortPendSVHandler()与vPortSVCHandler()函数，防止我们自己实现不了，那么在stm32f10x_it.c中就需要我们注释掉PendSV_Handler()与SVC_Handler()这两个函数了。

#### 修改main.c

### 创建任务

🔗：[3. 创建任务 — FreeRTOS内核实现与应用开发实战指南—基于STM32 文档 (embedfire.com)](https://doc.embedfire.com/rtos/freertos/zh/latest/application/create_tasks.html)

这章开始我们将真正进入如何使用FreeRTOS的征程，先从最简单的创建任务开始，点亮一个LED。

#### 硬件初始化

为了方便以后统一管理板级外设的初始化，我们在main.c文件中创建一个BSP_Init()函数，专门用于存放板级外设初始化函数。

```c
static void BSP_Init(void)
{
	/*
	 * STM32中断优先级分组为4，即4bit都用来表示抢占优先级，范围为：0~15
	 * 优先级分组只需要分组一次即可，以后如果有其他的任务需要用到中断，
	 * 都统一用这个优先级分组，千万不要再分组，切忌。
	 */
	NVIC_PriorityGroupConfig( NVIC_PriorityGroup_4 );
	
	/* LED 初始化 */
	LED_GPIO_Config();

	/* 串口初始化	*/
	USART_Config();
  
}
```

执行到BSP_Init()函数的时候，操作系统完全都还没有涉及，即BSP_Init()函数所做的工作跟我们以前编写的裸机工程里面的硬件初始化工作是一模一样的。运行完BSP_Init ()函数，接下来才慢慢启动操作系统，最后运行创建好的任务。有时候任务创建好，整个系统跑起来了，可想要的实验现象就是出不来，比如LED不会亮，串口没有输出，LCD没有显示等等。如果是初学者，这个时候就会心急如焚，四处求救，那怎么办？这个时候如何排除是硬件的问题还是系统的问题，这里面有个小小的技巧，即在硬件初始化好之后，顺便测试下硬件，测试方法跟裸机编程一样。

```C
static void BSP_Init(void)
{
	/*
	 * STM32中断优先级分组为4，即4bit都用来表示抢占优先级，范围为：0~15
	 * 优先级分组只需要分组一次即可，以后如果有其他的任务需要用到中断，
	 * 都统一用这个优先级分组，千万不要再分组，切忌。
	 */
	NVIC_PriorityGroupConfig( NVIC_PriorityGroup_4 );
	
	/* LED 初始化 */
	LED_GPIO_Config();
    
    /* 其他硬件初始化和测试 */
    LED1_ON();
    
    /* 其他硬件初始化和测试 */

	/* 串口初始化	*/
	USART_Config();
  
}
```

#### 创建单任务-SRAM静态内存

这里，我们创建一个单任务，任务使用的栈和任务控制块都使用静态内存，即预先定义好的全局变量，这些预先定义好的全局变量都存在内部的SRAM中。

##### 定义任务函数

任务实际上就是一个无限循环且不带返回值的C函数。目前，我们创建一个这样的任务，让开发板上面的LED灯以500ms的频率闪烁。

```c
static void LED_Task(void* parameter)
{	
    while (1)
    {
        LED1_ON;
        vTaskDelay(500);   /* 延时500个tick */
        printf("LED_Task Running,LED1_ON\r\n");
        
        LED1_OFF;     
        vTaskDelay(500);   /* 延时500个tick */		 		
        printf("LED_Task Running,LED1_OFF\r\n");
    }
}
```

* 任务必须是一个死循环，否则任务将通过LR返回，如果LR指向了非法的内存就会产生HardFault_Handler，而FreeRTOS指向一个死循环，那么任务返回之后就在死循环中执行，这样子的任务是不安全的，所以避免这种情况，**任务一般都是死循环并且无返回值的**。我 们的AppTaskCreate任务，执行一次之后就进行删除，则不影响系统运行，所以，只执行一次的任务在执行完毕要记得及时删除。
* **任务里面的延时函数必须使用FreeRTOS里面提供的延时函数**，并不能使用我们裸机编程中的那种延时。这两种的延时的区别是FreeRTOS里面的延时是阻塞延时，即调用vTaskDelay()函数的时候，当前任务会被挂起，调度器会切换到其他就绪的任务，从而实现多任务 。如果还是使用裸机编程中的那种延时，那么整个任务就成为了一个死循环，如果恰好该任务的优先级是最高的，那么系统永远都是在这个任务中运行，比它优先级更低的任务无法运行，根本无法实现多任务。

##### 空闲任务与定时器任务栈函数实现

##### 定义任务栈

目前我们只创建了一个任务，**当任务进入延时的时候，因为没有另外就绪的用户任务，那么系统就会进入空闲任务**，空闲任务是FreeRTOS系统自己启动的一个任务，优先级最低。当整个系统都没有就绪任务的时候，系统必须保证有一个任务在运行，空闲任务就是为这个设计的。当用户任务延时到期，又会从空闲任务切换回用户任务 。

在FreeRTOS系统中，每一个任务都是独立的，他们的运行环境都单独的保存在他们的栈空间当中。那么在定义好任务函数之后，我们还要为任务定义一个栈，目前我们使用的是静态内存，所以任务栈是一个独立的全局变量，具体见代码清单12‑5。任务的栈占用的是MCU内部的RAM，当任务越多的时候，需要使用的栈空间就 越大，即需要使用的RAM空间就越多。一个MCU能够支持多少任务，就得看你的RAM空间有多少。

##### 定义任务控制块

定义好任务函数和任务栈之后，我们还需要为任务定义一个任务控制块，通常我们称这个任务控制块为任务的身份证。在C代码上，任务控制块就是一个结构体，里面有非常多的成员，这些成员共同描述了任务的全部信息。

##### 静态创建任务

##### 启动任务

##### main文件内容全貌

#### 创建单任务-SRAM动态内存

这里，我们创建一个单任务，任务使用的栈和任务控制块是在创建任务的时候FreeRTOS动态分配的，并不是预先定义好的全局变量。

##### 动态内存空间的堆从哪里来

在创建单任务—SRAM静态内存的例程中，任务控制块和任务栈的内存空间都是从内部的SRAM里面分配的，具体分配到哪个地址由编译器决定。现在我们开始使用动态内存，即堆，其实堆也是内存，也属于SRAM。FreeRTOS做法是在SRAM里面定义一个大数组，也就是堆内存，供FreeRTOS的动态内存分配函数使用，在第一次使用的时候，系统会将定义的堆内存进行初始化，这些代码在FreeRTOS提供的内存管理方案中实现。

##### 定义任务函数

使用动态内存的时候，任务的主体函数与使用静态内存时是一样的

##### 定义任务栈

使用动态内存的时候，任务栈在任务创建的时候创建，不用跟使用静态内存那样要预先定义好一个全局的静态的栈空间，动态内存就是按需分配内存，随用随取。

##### 定义任务控制块指针

使用动态内存时候，不用跟使用静态内存那样要预先定义好一个全局的静态的任务控制块空间。任务控制块是在任务创建的时候分配内存空间创建，任务创建函数会返回一个指针，用于指向任务控制块，所以要预先为任务栈定义一个任务控制块指针，也是我们常说的任务句柄。

##### 动态创建任务

使用静态内存时，使用xTaskCreateStatic()来创建一个任务，而使用动态内存的时，则使用xTaskCreate()函数来创建一个任务，两者的函数名不一样，具体的形参也有区别。

```c
static void AppTaskCreate(void)
{
  BaseType_t xReturn = pdPASS;/* 定义一个创建信息返回值，默认为pdPASS */
  
  taskENTER_CRITICAL();           //进入临界区
  
  /* 创建LED_Task任务 */
  xReturn = xTaskCreate((TaskFunction_t )LED_Task, /* 任务入口函数 */
                        (const char*    )"LED_Task",/* 任务名字 */
                        (uint16_t       )512,   /* 任务栈大小 */
                        (void*          )NULL,	/* 任务入口函数参数 */
                        (UBaseType_t    )2,	    /* 任务的优先级 */
                        (TaskHandle_t*  )&LED_Task_Handle);/* 任务控制块指针 */
  if(pdPASS == xReturn)
    printf("创建LED_Task任务成功!\r\n");
  
  vTaskDelete(AppTaskCreate_Handle); //删除AppTaskCreate任务
  
  taskEXIT_CRITICAL();            //退出临界区
}
```

* 任务入口函数，即任务函数的名称，需要我们自己定义并且实现
* 任务名字，字符串形式，最大长度由FreeRTOSConfig.h中定义的configMAX_TASK_NAME_LEN宏指定，多余部分会被自动截掉，这里任务名字最好要与任务函数入口名字一致，方便进行调试。
* 任务栈大小，单位为字，在32位的处理器下（STM32），一个字等于4个字节，那么任务大小就为128 * 4字节。
* 任务入口函数形参，不用的时候配置为0或者NULL即可。
* 任务的优先级。优先级范围根据FreeRTOSConfig.h中的宏configMAX_PRIORITIES决定，如果使能configUSE_PORT_OPTIMISED_TASK_SELECTION，这个宏定义，则最多支持32个优先级；如果不用特殊方法查找下 一个运行的任务，那么则不强制要求限制最大可用优先级数目。在FreeRTOS中，数值越大优先级越高，0代表最低优先级。
* 任务控制块指针，在使用内存的时候，需要给任务初始化函数xTaskCreateStatic()传递预先定义好的任务控制块的指针。在使用动态内存的时候，任务创建函数xTaskCreate()会返回一个指针指向任务控制块，该任务控制块是xTaskCreate()函数里面动态分配的一块内存。

##### 启动任务

当任务创建好后，是处于任务就绪（Ready），在就绪态的任务可以参与操作系统的调度。但是此时任务仅仅是创建了，还未开启任务调度器，也没创建空闲任务与定时器任务（如果使能了configUSE_TIMERS这个宏定义），那这两个任务就是在启动任务调度器中实现，每个操作系统，任务调度器只启动一次，之后就不会再次执行了，FreeRTOS中启动任务调度器的函数是vTaskStartScheduler()，并且启动任务调度器的时候就不会返回，从此任务管理都由FreeRTOS管理，此时才是真正进入实时操作系统中的第一步。

```c
/* 启动任务调度 */           
if(pdPASS == xReturn)
	vTaskStartScheduler();   /* 启动任务，开启调度 */
else
	return -1; 
```

##### main文件内容全貌



#### 创建多任务-SRAM动态内存

目前多任务我们只创建了两个，如果要创建3个、4个甚至更多都是同样的套路，容易忽略的地方是任务栈的大小，每个任务的优先级。大的任务，栈空间要设置大一点，重要的任务优先级要设置的高一点。

### FreeRTOS的启动流程

🔗：[4. FreeRTOS的启动流程 — FreeRTOS内核实现与应用开发实战指南—基于STM32 文档 (embedfire.com)](https://doc.embedfire.com/rtos/freertos/zh/latest/application/freertos_startup.html)

#### 万事俱备，只欠东风

这种方法是在main函数中将硬件初始化，RTOS系统初始化，所有任务的创建弄好，最后启动RTOS的调度器，开始多任务的调度。

#### 小心翼翼，十分谨慎

这种方法是在main函数中将硬件和RTOS系统初始化好，然后创建一个启动任务后就启动调度器，然后在启动任务里面创建各种应用任务，当所有任务都创建成功后，启动任务把自己删除。

#### 孰优孰劣

那有关这两种方法孰优孰劣？我暂时没发现，我个人还是比较喜欢使用第一种。LiteOS和ucos第一种和第二种都可以使用，由用户选择，RT-Thread和FreeRTOS则默认使用第二种。接下来我们详细讲解下FreeRTOS的启动流程。

#### FreeRTOS的启动流程

### 任务管理

#### 任务的基本概念

从系统的角度看，任务是竞争系统资源的最小运行单元。FreeRTOS是一个支持多任务的操作系统。在FreeRTOS中，任务可以使用或等待CPU、使用内存空间等系统资源，并独立于其他任务运行，任何数量的任务可以共享同一个优先级，如果宏configUSE_TIME_SLICING定义为1，处于就绪态的多个 相同优先级任务将会以时间片切换的方式共享处理器。

简而言之： FreeRTOS的任务可认为是一系列独立任务的集合。每个任务在自己的环境中运行。**在任何时刻，只有一个任务得到运行，FreeRTOS调度器决定运行哪个任务**。调度器会不断的启动、停止每一个任务，宏观看上去所有的任务都在同时在执行。**作为任务，不需要对调度器的活动有所了解，在任务切入切出时保存上下文环境（寄存器值、栈内容）是调度器主要的职责**。为了实现这点，每个FreeRTOS任务都需要有自己的栈空间。当任务切出时，它的执行环境会被保存在该任务的栈空间中，这样当任务再次运行时，就能从栈中正确的恢复上次的运行环境，任务越多，需要的栈空间就越大，而一个系统能运行多少个任务，取决于系统的可用的SRAM。

FreeRTOS的可以给用户提供多个任务单独享有独立的栈空间，系统可用决定任务的状态，决定任务是否可以运行，同时还能运用内核的IPC通信资源，实现了任务之间的通信，帮助用户管理业务程序流程。这样用户可以将更多的精力投入到业务功能的实现中。

FreeRTOS中的任务是**抢占式调度机制**，高优先级的任务可打断低优先级任务，低优先级任务必须在高优先级任务阻塞或结束后才能得到调度。同时FreeRTOS也支持时间片轮转调度方式，只不过时间片的调度是不允许抢占任务的CPU使用权。

任务通常会运行在一个死循环中，也不会退出，如果一个任务不再需要，可以调用FreeRTOS中的任务删除API函数接口显式地将其删除。

#### 任务调度器的基本概念

FreeRTOS中提供的任务调度器是基于优先级的全抢占式调度：在系统中除了中断处理函数、调度器上锁部分的代码和禁止中断的代码是不可抢占的之外，系统的其他部分都是可以抢占的。系统理论上可以支持无数个优先级(0 ～ N，优先级数值越小的任务优先级越低，0为最低优先级，分配给空闲任务使用，一般不建议用户来 使用这个优先级。假如使能了configUSE_PORT_OPTIMISED_TASK_SELECTION这个宏（在FreeRTOSConfig.h文件定义），一般强制限定最大可用优先级数目为32。在一些资源比较紧张的系统中，可以根据实际情况选择只支持8个或32个优先级的系统配置。在系统中，当有比当前 任务优先级更高的任务就绪时，当前任务将立刻被换出，高优先级任务抢占处理器运行。

一个操作系统如果只是具备了高优先级任务能够“立即”获得处理器并得到执行的特点，那么它仍然不算是实时操作系统。因为这个查找最高优先级任务的过程决定了调度时间是否具有确定性，例如一个包含n个就绪任务的系统中，如果仅仅从头找到尾，那么这个时间将直接和n相关，而下一个就绪任务抉择时间的长短将会极大的影响系统 的实时性。

FreeRTOS内核中采用两种方法寻找最高优先级的任务，第一种是通用的方法，在就绪链表中查找从高优先级往低查找uxTopPriority，因为在创建任务的时候已经将优先级进行排序，查找到的第一个uxTopPriority就是我们需要的任务，然后通过uxTopPriority获取对应的任务控制块。第二种方法则是特殊方法，利用计算前导零指令CLZ，直接在uxTopReadyPriority这个32位的变量中直接得出uxTopPriority，这样子就知道哪一个优先级任务能够运行，这种调度算法比普通方法更快捷，但受限于平台（在STM32中我们就使用这种方法）。

FreeRTOS内核中也允许创建相同优先级的任务。**相同优先级的任务采用时间片轮转方式进行调度**（也就是通常说的分时调度器），时间片轮转调度仅在当前系统中无更高优先级就绪任务存在的情况下才有效。为了保证系统的实时性，系统尽最大可能地保证高优先级的任务得以运行。任务调度的原则是一旦任务状态发生了改变，并且当前运行的任务优先级小于优先级队列组中任务最高优先级时，立刻进行任务切换（除非当前系统处于中断处理程序中或禁止任务切换的状态）。

#### 任务状态迁移

* 创建任务-就绪态：任务创建完成后进入就绪态，表明任务已准备就绪，随时可以运行，只等待调度器进行调度。
* 就绪态-运行态：发生任务切换时，就绪列表中最高优先级的任务被执行，从而进入运行态。
* 运行态-就绪态：有更高优先级任务创建或者恢复后，会发生任务调度，此刻就绪列表中最高优先级任务变为运行态，那么原先运行的任务由运行态变为就绪态，依然在就绪列表中，等待最高优先级的任务运行完毕继续运行原来的任务（可视作CPU使用权被更高优先级的任务抢占了）。
* 运行态-阻塞态：正在运行的任务发生阻塞（挂起、延时、读信号量等待）时，该任务就会从就绪列表中删除，任务状态由运行态变成阻塞态，然后发生任务切换，运行就绪列表中当前最高优先级任务。
* 阻塞态-就绪态：阻塞的任务被恢复后（任务恢复、延时时间超时、读信号量超时或读到信号量等），此时被恢复的任务会被加入就绪列表，从而由阻塞态变成就绪态；如果此时被恢复任务的优先级高于正在运行任务的优先级，则会发生任务切换，将该任务将再次转换任务状态，由就绪态变成运行态。
* 就绪态、阻塞态、运行态-挂起态：任务可以通过调用vTaskSuspend() API 函数都可以将处于任何状态的任务挂起，被挂起的任务得不到CPU的使用权，也不会参与调度，除非它从挂起态中解除。
* 挂起态-就绪态：把一个挂起状态的任务恢复的唯一途径就是调用 vTaskResume() 或vTaskResumeFromISR() API 函数，如果此时被恢复任务的优先级高于正在运行任务的优先级，则会发生任务切换，将该任务将再次转换任务状态，由就绪态变成运行态。

#### 任务状态的概念

FreeRTOS系统中的每一任务都有多种运行状态。系统初始化完成后，创建的任务就可以在系统中竞争一定的资源，由内核进行调度。

任务状态通常分为以下四种：

- 就绪（Ready）：该任务在就绪列表中，就绪的任务已经具备执行的能力，只等待调度器进行调度，新创建的任务会初始化为就绪态。
- 运行（Running）：该状态表明任务正在执行，此时它占用处理器，FreeRTOS调度器选择运行的永远是处于最高优先级的就绪态任务，当任务被运行的一刻，它的任务状态就变成了运行态。
- 阻塞（Blocked）：如果任务当前正在等待某个时序或外部中断，我们就说这个任务处于阻塞状态，该任务不在就绪列表中。包含任务被挂起、任务被延时、任务正在等待信号量、读写队列或者等待读写事件等。
- 挂起态(Suspended)：处于挂起态的任务对调度器而言是不可见的，让一个任务进入挂起状态的唯一办法就是调用 vTaskSuspend()函数；而把一个挂起状态的任务恢复的唯一途径就是调用 vTaskResume()或vTaskResumeFromISR()函数，我们可以这么理解挂起态与阻塞态的区别，当任务有较长的时间不允许运行的时候，我们可以挂起任务，这样子调度器就不会管这个任务的任何信息，直到我们调用恢复任务的API函数；而任务处于阻塞态的时候，系统还需要判断阻塞态的任务是否超时，是否可以解除阻塞。

#### 常用的任务函数

##### 任务挂起函数

* vTaskSuspend()：挂起指定任务。被挂起的任务绝不会得到CPU的使用权，不管该任务具有什么优先级。
* vTaskSuspendAll：将所有的任务都挂起，其实就是将调度器锁定

##### 任务恢复函数

* vTaskResume()：让挂起的任务重新进入就绪状态恢复的任务会保留挂起前的状态信息，在恢复的时候根据挂起时的状态继续运行。
* xTaskResumeFromISR()：xTaskResumeFromISR()与 vTaskResume()一样都是用于恢复被挂起的任务，不一样的是 xTaskResumeFromISR()专门用在中断服务程序中。无论通过调用一次或多次 vTaskSuspend()函数而被挂起的任务，也只需调用一次 xTaskResumeFromISR()函数即可解挂。要想使用该函数必须在FreeRTOSConfig.h 中把INCLUDE_vTaskSuspend 和INCLUDE_vTaskResumeFromISR 都定义为 1 才有效。任务还没有处于挂起态的时候，调用xTaskResumeFromISR()函数是没有任何意义的。
* xTaskResumeAll()：当调用了vTaskSuspendAll()函数将调度器挂起，想要恢复调度器的时候我们就需要调用xTaskResumeAll()函数。

##### 任务删除函数

* vTaskDelete()：vTaskDelete()用于删除一个任务。当一个任务删除另外一个任务时，形参为要删除任务创建时返回的任务句柄，如果是删除自身，则形参为 NULL。要想使用该函数必须在FreeRTOSConfig.h 中把 INCLUDE_vTaskDelete 定义为 1，删除的任务将从所有就绪，阻塞，挂起和事件列表中删除。

##### 任务延时函数

* vTaskDelay()：vTaskDelay()在我们任务中用得非常之多，每个任务都必须是死循环，并且是必须有阻塞的情况，否则低优先级的任务就无法被运行了。要想使用FreeRTOS中的vTaskDelay()函数必须在 FreeRTOSConfig.h 中把 INCLUDE_vTaskDelay 定义为 1 来使能。
* vTaskDelayUntil()：在FreeRTOS中，除了相对延时函数，还有绝对延时函数vTaskDelayUntil()，这个绝对延时常用于较精确的周期运行任务，比如我有一个任务，希望它以固定频率定期执行，而不受外部的影响，任务从上一次运行开始到下一次运行开始的时间间隔是绝对的，而不是相对的。

#### 任务的设计要点

作为一个嵌入式开发人员，要对自己设计的嵌入式系统要了如指掌，任务的优先级信息，任务与中断的处理，任务的运行时间、逻辑、状态等都要知道，才能设计出好的系统，所以，在设计的时候需要根据需求制定框架。在设计之初就应该考虑下面几点因素：任务运行的上下文环境、任务的执行时间合理设计。

FreeRTOS中程序运行的上下文包括：

- 中断服务函数。
- 普通任务。
- 空闲任务。

##### 中断服务函数

中断服务函数是一种需要特别注意的上下文环境，它运行在非任务的执行环境下（一般为芯片的一种特殊运行模式（也被称作特权模式）），在这个上下文环境中不能使用挂起当前任务的操作，不允许调用任何会阻塞运行的API函数接口。另外需要注意的是，**中断服务程序最好保持精简短小，快进快出，一般在中断服务函数中只做标记事件的发生，然后通知任务，让对应任务去执行相关处理，因为中断服务函数的优先级高于任何优先级的任务，如果中断处理时间过长，将会导致整个系统的任务无法正常运行**。所以在设计的时候必须考虑中断的频率、中断的处理时间等重要因素，以便配合对应中断处理任务的工作。

##### 任务

任务看似没有什么限制程序执行的因素，似乎所有的操作都可以执行。但是做为一个优先级明确的实时系统，如果一个任务中的程序出现了死循环操作（此处的死循环是指没有阻塞机制的任务循环体），那么比这个任务优先级低的任务都将无法执行，当然也包括了空闲任务，因为死循环的时候，任务不会主动让出CPU，低优先级的任务是不可能得到CPU的使用权的，而高优先级的任务就可以抢占CPU。这个情况在实时操作系统中是必须注意的一点，所以在任务中不允许出现死循环。如果一个任务只有就绪态而无阻塞态，势必会影响到其他低优先级任务的执行，所以在进行任务设计时，就应该保证任务在不活跃的时候，任务可以进入阻塞态以交出CPU使用权，这就需 要我们自己明确知道什么情况下让任务进入阻塞态，保证低优先级任务可以正常运行。在实际设计中，一般会将紧急的处理事件的任务优先级设置得高一些。

##### 空闲任务

空闲任务（idle任务）是FreeRTOS系统中没有其他工作进行时自动进入的系统任务。因为处理器总是需要代码来执行——所以至少要有一个任务处于运行态。FreeRTOS为了保证这一点，**当调用 vTaskStartScheduler()时，调度器会自动创建一个空闲任务，空闲任务是一个非常短小的循环。用户 可以通过空闲任务钩子方式，在空闲任务上钩入自己的功能函数**。通常这个空闲任务钩子能够完成一些额外的特殊功能，例如系统运行状态的指示，系统省电模式等。除了空闲任务钩子，FreeRTOS系统还把空闲任务用于一些其他的功能，比如当系统删除一个任务或一个动态任务运行结束时，在执行删除任务的时候，并不会释放任务 的内存空间，只会将任务添加到结束列表中，真正的系统资源回收工作在空闲任务完成，空闲任务是唯一一个不允许出现阻塞情况的任务，因为FreeRTOS需要保证系统永远都有一个可运行的任务。

##### 任务的执行时间

任务的执行时间一般是指两个方面，一是任务从开始到结束的时间，二是任务的周期。

在系统设计的时候这两个时间候我们都需要考虑，例如，对于事件A对应的服务任务Ta，系统要求的实时响应指标是10ms，而Ta的最大运行时间是1ms，那么10ms就是任务Ta的周期了，1ms则是任务的运行时间，简单来说任务Ta在10ms内完成对事件A的响应即可。此时，系统中还存在着以50ms为周期的另一任 务Tb，它每次运行的最大时间长度是100us。在这种情况下，即使把任务Tb的优先级抬到比Ta更高的位置，对系统的实时性指标也没什么影响，因为即使在Ta的运行过程中，Tb抢占了Ta的资源，等到Tb执行完毕，消耗的时间也只不过是100us，还是在事件A规定的响应时间内(10ms)，Ta能够安全完成对事件 A的响应。但是假如系统中还存在任务Tc，其运行时间为20ms，假如将Tc的优先级设置比Ta更高，那么在Ta运行的时候，突然间被Tc打断，等到Tc执行完毕，那Ta已经错过对事件A（10ms）的响应了，这是不允许的。所以在我们设计的时候，必须考虑任务的时间，一般来说处理时间更短的任务优先级应设置更高一些 。

#### 任务管理实验

### 消息队列

#### 消息队列的基本概念

队列又称消息队列，是一种用于任务间通信的数据结构，队列可以在任务与任务间、中断和任务间传递信息

全局变量的弊端：数据无保护，导致数据不安全，当多个任务同时堆该变量操作时，数据易受损

读写队列做好了保护，防止多任务同时访问，我们只需要直接调用API函数即可

在队列中可以存储数量有限、大小固定的数据。队列中的每一个数据叫做“队列项目”，队列能够存储“队列项目”的最大数量称为队列的长度

在队列中可以存储数量有限、大小固定的数据。队列中的每一个数据叫做“队列项目”，队列能够存储“队列项目”的最大数量称为队列的长度

#### 消息队列的运作机制

##### 数据入队出队方式

队列通常采用"先进先出"(FIFO)的数据存储缓冲机制,即先入队的数据会先从队列中被读取,FreeRTOS也可以配置为"后进先出".

##### 数据传递方式

FreeRTOS中队列采用实际值传递,即将数据拷贝到队列中进行传递,FreeRTOS采用拷贝数据传递也可以传递指针,所以在传递较大的数据的时候采用指针传递

##### 多任务访问

队列不属于某个任务,任何任务和中断都可以向队列发送/读取消息

#### 消息队列的阻塞机制

![image-20240907222707744](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240907222707744.png)

当多个任务写入消息给一个"满队列"时,这些任务都会进入阻塞状态,也就是说有多个任务在等待同一个队列的空间.那当队列中有空间时,哪个任务会进入就绪态?

* 优先级最高的任务
* 如果大家的优先级相同,那等待时间最久的任务会进入就绪态

#### 消息队列的应用场景

消息队列可以应用于发送不定长消息的场合，包括任务与任务间的消息交换，队列是FreeRTOS主要的任务间通信方式，可以在任务与任务间、中断和任务间传送信息，发送到队列的消息是通过拷贝方式实现的，这意味着队列存储的数据是原数据，而不是原数据的引用。

#### 消息队列控制块

#### 消息队列常用函数讲解

使用队列模块的典型流程如下：

* 创建消息队列
* 写队列操作
* 读队列操作
* 删除队列

##### 消息队列创建函数xQueueCreate

用于创建一个新的队列并返回可用于访问这个队列的队列句柄。队列句柄其实就是一个指向队列数据结构体类型的指针。

队列就是一个数据结构，用于任务间的数据的传递。每创建一个新的队列都需要为其分配RAM，一部分用于存储队列的状态，剩下的作为队列消息的存储区域。使用xQueueCreate创建队列时，使用的是**动态内存分配**，所以要想使用该函数必须在FreeRTOSConfig.h中把[configSUPPORT_DYNAMIC_ALLOCATION](http://www.freertos.org/a00110.html#configSUPPORT_DYNAMIC_ALLOCATION)定义为1来使能，这是个用于使能动态内存分配的宏，通常情况下，在FreeRTOS中，凡是创建任务，队列，信号量和互斥量等内核对象都需要使用动态内存分配，所以这个宏默认在FreeRTOS.h头文件中已经使能（即定义为1）。如果想使用静态内存，则可以使用[xQueueCreateStatic()](http://www.freertos.org/xQueueCreateStatic.html) 函数来创建一个队列。使用静态创建消息队列函数创建队列时需要的形参更多，需要的内存由编译的时候预先分配好，一般很少使用这种方法。

* 关于动态内存分配

在C语言中，所有内存需求都是在程序执行之前通过定义所需的变量来确定的。但是可能存在程序的内存需求只能在运行时确定的情况。例如，当需要的内存取决于用户输入。在这种情况下，程序需要动态分配内存。

* new关键字与malloc函数的区别

| new                                 | malloc                         |
| ----------------------------------- | ------------------------------ |
| new关键字是C++的一部分              | malloc是由C库提供的函数        |
| new以具体类型为单位进行内存分配     | malloc以字节为单位进行内存分配 |
| new在申请单个类型变量时可进行初始化 | malloc不具备内存初始化的特性   |

##### 消息队列静态创建函数xQueueCreateStatic

xQueueCreateStatic()用于创建一个新的队列并返回可用于访问这个队列的队列句柄。队列句柄其实就是一个指向队列数据结构类型的指针。

队列就是一个数据结构，用于任务间的数据的传递。每创建一个新的队列都需要为其分配RAM，一部分用于存储队列的状态，剩下的作为队列的存储区。使用xQueueCreateStatic()创建队列时，使用的是**静态内存分配**，所以要想使用该函数必须在FreeRTOSConfig.h中把configSUPPORT _STATIC_ALLOCATION定义为1来使能。这是个用于使能静态内存分配的宏，需要的内存在程序编译的时候分配好，由用户自己定义，其实创建过程与xQueueCreate()都是差不多的。

##### 消息队列删除函数vQueueDelete

队列删除函数是根据消息队列句柄直接删除的，删除之后这个消息队列的所有信息都会被系统回收清空，而且不能再次使用这个消息队列了，但是需要注意的是，如果某个消息队列没有被创建，那也是无法被删除的，动脑子想想都知道，没创建的东西就不存在，怎么可能被删除。xQueue是vQueueDelete()函数的形参， 是消息队列句柄，表示的是要删除哪个队列。

##### 向消息队列发送消息函数

任务或者中断服务程序都可以给消息队列发送消息，当发送消息时，如果队列未满或者允许覆盖入队，FreeRTOS会将消息拷贝到消息队列队尾，否则会根据用户指定的阻塞超时时间进行阻塞，在这段时间中，如果队列一直不允许入队，该任务将保持阻塞状态以等待队列允许入队。当其他任务从其等待的队列中读取入了数据（队列未满），该任务将自动由阻塞态转为就绪态。当任务等待的时间超过了指定的阻塞时间，即使队列中还不允许入队，任务也会自动从阻塞态转移为就绪态，此时发送消息的任务或者中断程序会收到一个错误码errQUEUE_FULL。

发送紧急消息的过程与发送消息几乎一样，唯一不同的是，当发送紧急消息时，发送的位置是消息队列队头而非队尾，这样，接收者就能够优先接收到紧急消息，从而及时进行消息处理。

* xQueueSend与xQueueSendToBack

xQueueSend()是一个宏，宏展开是调用函数xQueueGenericSend()，这个函数在后面会详细讲解其实现过程。该宏是为了向后兼容没有包含xQueueSendToFront()和xQueueSendToBack() 这两个宏的FreeRTOS版本。xQueueSend()等同于xQueueSendToBack()。

xQueueSend()用于向队列尾部发送一个队列消息。消息以拷贝的形式入队，而不是以引用的形式。该函数绝对不能在中断服务程序里面被调用，中断中必须使用带有中断保护功能的xQueueSendFromISR()来代替。

* xQueueSendFromISR与xQueueSendToBackFromISR

xQueueSendFromISR()是一个宏，宏展开是调用函数xQueueGenericSendFromISR()。该宏是xQueueSend()的中断保护版本，用于在中断服务程序中向队列尾部发送一个队列消息，等价于xQueueSendToBackFromISR()。

* xQueueSendToFront

xQueueSendToFron()是一个宏，宏展开也是调用函数xQueueGenericSend()。xQueueSendToFront()用于向队列队首发送一个消息。消息以拷贝的形式入队，而不是以引用的形式。该函数绝不能在中断服务程序里面被调用，而是必须使用带有中断保护功能的xQueueSendToFrontFromISR ()来代替。

* xQueueSendToFrontFromISR

xQueueSendToFrontFromISR()是一个宏，宏展开是调用函数xQueueGenericSendFromISR()。该宏是xQueueSendToFront()的中断保护版本，用于在中断服务程序中向消息队列队首发送一个消息。xQueueSendToFromISR()函数具体说明见表1 5‑6，使用方式与xQueueSendFromISR()函数一致。

* 通用消息队列发送函数xQueueGenericSend

上面看到的那些在任务中发送消息的函数都是xQueueGenericSend展开的宏定义，真正起作用的是xQueueGenericSend函数，根据指定的参数不一样，发送消息的结果就不一样。

* 消息队列发送函数xQueueGenericSendFromISR

既然有任务中发送消息的函数，当然也需要有在中断中发送消息函数，其实这个函数跟xQueueGenericSend()函数很像，只不过是执行的上下文环境是不一样的，xQueueGenericSendFromISR()函数只能用于中断中执行，是不带阻塞机制的。

##### 从消息队列读取消息函数

当任务试图读队列中的消息时，可以指定一个阻塞超时时间，当且仅当消息队列中有消息的时候，任务才能读取到消息。在这段时间中，如果队列为空，该任务将保持阻塞状态以等待队列数据有效。当其他任务或中断服务程序往其等待的队列中写入了数据，该任务将自动由阻塞态转为就绪态。当任务等待的时间超过了指定的阻塞时间，即使队列中尚无有效数据，任务也会自动从阻塞态转移为就绪态。

* xQueueReceive与xQueuePeek

xQueueReceive()是一个宏，宏展开是调用函数xQueueGenericReceive()。xQueueReceive()用于从一个队列中接收消息并把消息从队列中删除。接收的消息是以拷贝的形式进行的，所以我们必须提供一个足够大空间的缓冲区。具体能够拷贝多少数据到缓冲区，这个在队列创建的时候已经设定。该函数绝不能在中断服务程序里面被调用，而是必须使用带有中断保护功能的xQueueReceiveFromISR()来代替。

有人就问了如果我接收了消息不想删除怎么办呢？其实，你能想到的东西，FreeRTOS看到也想到了，如果不想删除消息的话，就调用xQueuePeek()函数。

其实这个函数与xQueueReceive()函数的实现方式一样，连使用方法都一样，只不过xQueuePeek()函数接收消息完毕不会删除消息队列中的消息而已。

* xQueueReceiveFromISR与xQueuePeekFromISR

xQueueReceiveFromISR()是xQueueReceive ()的中断版本，用于在中断服务程序中接收一个队列消息并把消息从队列中删除；xQueuePeekFromISR()是xQueuePeek()的中断版本，用于在中断中从一个队列中接收消息，但并不会把消息从队列中移除。

说白了这两个函数只能用于中断，是不带有阻塞机制的，并且是在中断中可以安全调用。

#### 消息队列使用注意事项

在使用FreeRTOS提供的消息队列函数的时候，需要了解以下几点：

1. 使用xQueueSend()、xQueueSendFromISR()、xQueueReceive()等这些函数之前应先创建需消息队列，并根据队列句柄进行操作。
2. 队列读取采用的是先进先出（FIFO）模式，会先读取先存储在队列中的数据。当然也FreeRTOS也支持后进先出（LIFO）模式，那么读取的时候就会读取到后进队列的数据。
3. 在获取队列中的消息时候，我们必须要定义一个存储读取数据的地方，并且该数据区域大小不小于消息大小，否则，很可能引发地址非法的错误。
4. 无论是发送或者是接收消息都是以拷贝的方式进行，如果消息过于庞大，可以将消息的地址作为消息进行发送、接收。
5. 队列是具有自己独立权限的内核对象，并不属于任何任务。所有任务都可以向同一队列写入和读出。一个队列由多任务或中断写入是经常的事，但由多个任务读出倒是用的比较少。

### 信号量

#### 信号量基本概念

信号量（Semaphore）是一种实现任务间通信的机制，可以实现任务之间同步或临界资源的互斥访问，常用于协助一组相互竞争的任务来访问临界资源。在多任务系统中，各任务之间需要同步或互斥实现临界资源的保护，信号量功能可以为用户提供这方面的支持。

抽象的来讲，信号量是一个非负整数，所有获取它的任务都会将该整数减一（获取它当然是为了使用资源），当该整数值为零时，所有试图获取它的任务都将处于阻塞状态。通常一个信号量的计数值用于对应有效的资源数，表示剩下的可被占用的互斥资源数。其值的含义分两种情况：

- 0：表示没有积累下来的释放信号量操作，且有可能有在此信号量上阻塞的任务。
- 正值，表示有一个或多个释放信号量操作。

##### 二值信号量

二值信号量既可以用于临界资源访问也可以用于同步功能

二值信号量和互斥信号量（以下使用互斥量表示互斥信号量）非常相似，但是有一些细微差别：互斥量有优先级继承机制，二值信号量则没有这个机制。这使得二值信号量更偏向应用于同步功能（任务与任务间的同步或任务和中断间同步），而互斥量更偏向应用于临界资源的访问。

用作同步时，信号量在创建后应被置为空，任务1获取信号量而进入阻塞，任务2在某种条件发生后，释放信号量，于是任务1获得信号量得以进入就绪态，如果任务1的优先级是最高的，那么就会立即切换任务，从而达到了两个任务间的同步。同样的，在中断服务函数中释放信号量，任务1也会得到信号量，从而达到任务与中断间的同步 。

还记得我们经常说的中断要快进快出吗，在裸机开发中我们经常是在中断中做一个标记，然后在退出的时候进行轮询处理，这个就是类似我们使用信号量进行同步的，当标记发生了，我们再做其他事情。在 FreeRTOS中我们用信号量用于同步，任务与任务的同步，中断与任务的同步，可以大大提高效率。

**可以将二值信号量看作只有一个消息的队列，因此这个队列只能为空或满（因此称为二值）**，我们在运用的时候只需要知道队列中是否有消息即可，而无需关注消息是什么。

##### 计数信号量

二进制信号量可以被认为是长度为1的队列，而计数信号量则可以被认为长度大于1的队列，信号量使用者依然不必关心存储在队列中的消息，只需关心队列是否有消息即可。

顾名思义，计数信号量肯定是用于计数的，在实际的使用中，我们常将计数信号量用于事件计数与资源管理。每当某个事件发生时，任务或者中断将释放一个信号量（信号量计数值加1），当处理被事件时（一般在任务中处理），处理任务会取走该信号量（信号量计数值减1），**信号量的计数值则表示还有多少个事件没被处理**。此外，系统还有很多资源，我们也可以使用计数信号量进行资源管理，信号量的计数值表示系统中可用的资源数目，任务必须先获取到信号量才能获取资源访问权，当信号量的计数值为零时表示系统没有可用的资源，但是要注意，在使用完资源的时候必须归还信号量，否则当计数值为0的时候任务就无法访问该资源了。

计数型信号量允许多个任务对其进行操作，但限制了任务的数量。比如有一个停车场，里面只有100个车位，那么能停的车只有100辆，也相当于我们的信号量有100个，假如一开始停车场的车位还有100个，那么每进去一辆车就要消耗一个停车位，车位的数量就要减一，对应的，我们的信号量在使用之后也需要减一，当停车场停 满了100辆车的时候，此时的停车位为0，再来的车就不能停进去了，否则将造成事故，也相当于我们的信号量为0，后面的任务对这个停车场资源的访问也无法进行，当有车从停车场离开的时候，车位又空余出来了，那么，后面的车就能停进去了，我们信号量的操作也是一样的，当我们释放了这个资源，后面的任务才能对这个资源进行访问。

##### 互斥信号量

互斥信号量其实是特殊的二值信号量，由于其特有的**优先级继承机制**从而使它更适用于简单互锁，也就是保护临界资源（什么是优先级继承在后续相信讲解）。

用作互斥时，信号量创建后可用信号量个数应该是满的，任务在需要使用临界资源时，（临界资源是指任何时刻只能被一个任务访问的资源），先获取互斥信号量，使其变空，这样其他任务需要使用临界资源时就会因为无法获取信号量而进入阻塞，从而保证了临界资源的安全。

在操作系统中，我们使用信号量的很多时候是为了给临界资源建立一个标志，信号量表示了该临界资源被占用情况。这样，当一个任务在访问临界资源的时候，就会先对这个资源信息进行查询，从而在了解资源被占用的情况之后，再做处理，从而使得临界资源得到有效的保护。

##### 递归信号量

递归信号量，见文知义，递归嘛，就是可以重复获取调用的，本来按照信号量的特性，每获取一次可用信号量个数就会减少一个，但是递归则不然，对于已经获取递归互斥量的任务可以重复获取该递归互斥量，该任务拥有递归信号量的所有权。任务成功获取几次递归互斥量，就要返还几次，在此之前递归互斥量都处于无效状态，其他任务无法获取，只有持有递归信号量的任务才能获取与释放。

#### 二值信号量应用场景

在嵌入式操作系统中二值信号量是任务间、任务与中断间同步的重要手段，信号量使用最多的一般都是二值信号量与互斥信号量（互斥信号量在下一章讲解）。为什么叫二值信号量呢？因为信号量资源被获取了，信号量值就是 0，信号量资源被释放，信号量值就是 1，把这种只有0和1两种情况的信号量称之为二值信号量。

在多任务系统中，我们经常会使用这个二值信号量，比如，某个任务需要等待一个标记，那么任务可以在轮询中查询这个标记有没有被置位，但是这样子做，就会很消耗CPU资源并且妨碍其他任务执行，更好的做法是任务的大部分时间处于阻塞状态（允许其他任务执行），直到某些事件发生该任务才被唤醒去执行。可以使用二进制信号量 实现这种同步，当任务取信号量时，因为此时尚未发生特定事件，信号量为空，任务会进入阻塞状态；当事件的条件满足后，任务/中断便会释放信号量，告知任务这个事件发生了，任务取得信号量便被唤醒去执行对应的操作，任务执行完毕并不需要归还信号量，这样子的CPU的效率可以大大提高，而且实时响应也是最快的。

再比如某个任务使用信号量在等中断的标记的发生，在这之前任务已经进入了阻塞态，在等待着中断的发生，当在中断发生之后，释放一个信号量，也就是我们常说的标记，当它退出中断之后，操作系统会进行任务的调度，如果这个任务能够运行，系统就会把等待这个任务运行起来，这样子就大大提高了我们的效率。

二值信号量在任务与任务中同步的应用场景：假设我们有一个温湿度的传感器，假设是1s采集一次数据，那么我们让他在液晶屏中显示数据出来，这个周期也是要1s一次的，如果液晶屏刷新的周期是100ms更新一次，那么此时的温湿度的数据还没更新，液晶屏根本无需刷新，只需要在1s后温湿度数据更新的时候刷新即可，否则CPU就是白白做了多次的无效数据更新，CPU的资源就被刷新数据这个任务占用了大半，造成CPU资源浪费，如果液晶屏刷新的周期是10s更新一次，那么温湿度的数据都变化了10次，液晶屏才来更新数据，那拿这个产品有啥用，根本就是不准确的，所以，还是需要同步协调工作，在温湿度采集完毕之后，进行液晶屏数据的刷新， 这样子，才是最准确的，并且不会浪费CPU的资源。

同理，二值信号量在任务与中断同步的应用场景：我们在串口接收中，我们不知道啥时候有数据发送过来，有一个任务是做接收这些数据处理，总不能在任务中每时每刻都在任务查询有没有数据到来，那样会浪费CPU资源，所以在这种情况下使用二值信号量是很好的办法，当没有数据到来的时候，任务就进入阻塞态，不参与任务的调度， 等到数据到来了，释放一个二值信号量，任务就立即从阻塞态中解除，进入就绪态，然后运行的时候处理数据，这样子系统的资源就会很好的被利用起来。

#### 二值信号量运作机制

创建信号量时，系统会为创建的信号量对象分配内存，并把可用信号量初始化为用户自定义的个数，二值信号量的最大可用信号量个数为1。

二值信号量获取，任何任务都可以从创建的二值信号量资源中获取一个二值信号量，获取成功则返回正确，否则任务会根据用户指定的阻塞超时时间来等待其他任务/中断释放信号量。在等待这段时间，系统将任务变成阻塞态，任务将被挂到该信号量的阻塞等待列表中。

在二值信号量无效的时候，假如此时有任务获取该信号量的话，那么任务将进入阻塞状态。

假如某个时间中断/任务释放了信号量，其过程具体见图16‑2，那么，由于获取无效信号量而进入阻塞态的任务将获得信号量并且恢复为就绪态。

#### 计数信号量运作机制

计数信号量可以用于资源管理，允许多个任务获取信号量访问共享资源，但会限制任务的最大数目。访问的任务数达到可支持的最大数目时，会阻塞其他试图获取该信号量的任务，直到有任务释放了信号量。这就是计数型信号量的运作机制，虽然计数信号量允许多个任务访问同一个资源，但是也有限定，比如某个资源限定只能有3个任务访问，那么第4个任务访问的时候，会因为获取不到信号量而进入阻塞，等到有任务（比如任务1）释放掉该资源的时候，第4个任务才能获取到信号量从而进行资源的访问。

#### 信号量控制块

信号量API函数实际上都是宏，它使用现有的队列机制，这些宏定义在semphr.h文件中，如果使用信号量或者互斥量，需要包含semphr.h头文件。所以FreeRTOS的信号量控制块结构体与消息队列结构体是一模一样的，只不过结构体中某些成员变量代表的含义不一样而已

#### 常用信号量函数接口讲解

##### 创建信号量函数

* 创建二值信号量xSemaphoreCreateBinary
* 创建计数信号量xSemaphoreCreateCounting

##### 信号量删除函数vSemaphoreDelete

vSemaphoreDelete()用于删除一个信号量，包括二值信号量，计数信号量，互斥量和递归互斥量。

##### 信号量释放函数

与消息队列的操作一样，信号量的释放可以在任务、中断中使用，所以需要有不一样的API函数在不一样的上下文环境中调用。

在前面的讲解中，我们知道，当信号量有效的时候，任务才能获取信号量，那么，是什么函数使得信号量变得有效？其实有两个方式，一个是在创建的时候进行初始化，将它可用的信号量个数设置一个初始值；在二值信号量中，该初始值的范围是0~1（旧版本的FreeRTOS中创建二值信号量默认是有效的，而新版本则默认是无效） ，假如初始值为1个可用的信号量的话，被申请一次就变得无效了，那就需要我们释放信号量，FreeRTOS提供了信号量释放函数，每调用一次该函数就释放一个信号量。但是有个问题，能不能一直释放？很显然，这是不能的，无论是你的信号量是二值信号量还是计数信号量，都要注意可用信号量的范围，当用作二值信号量的时候， 必须确保其可用值在0~1范围内；而用作计数信号量的话，其范围是由用户在创建时指定uxMaxCount，其最大可用信号量不允许超出uxMaxCount，这代表我们不能一直调用信号量释放函数来释放信号量，其实一直调用也是无法释放成功的，在写代码的时候，我们要注意代码的严谨性罢了。

* xSemaphoreGive

xSemaphoreGive()是一个用于释放信号量的宏，真正的实现过程是调用消息队列通用发送函数，xSemaphoreGive()函数原型具体见代码清单16‑8。释放的信号量对象必须是已经被创建的，可以用于二值信号量、计数信号量、互斥量的释放，但不能释放由函数xSemaphoreCreateRec ursiveMutex()创建的递归互斥量。此外该函数不能在中断中使用

* xSemaphoreGiveFromISR

用于释放一个信号量，带中断保护。被释放的信号量可以是二进制信号量和计数信号量。和普通版本的释放信号量API函数有些许不同，它不能释放互斥量，这是因为互斥量不可以在中断中使用，互斥量的优先级继承机制只能在任务中起作用，而在中断中毫无意义。带中断保护的信号量释放其实也是一个宏，真正调用的函数是xQueueGiveFromISR()

##### 信号量获取函数

与消息队列的操作一样，信号量的获取可以在任务、中断（中断中使用并不常见）中使用，所以需要有不一样的API函数在不一样的上下文环境中调用。

与释放信号量对应的是获取信号量，我们知道，当信号量有效的时候，任务才能获取信号量，当任务获取了某个信号量的时候，该信号量的可用个数就减一，当它减到0的时候，任务就无法再获取了，并且获取的任务会进入阻塞态（假如用户指定了阻塞超时时间的话）。如果某个信号量中当前拥有1个可用的信号量的话，被获取一次就变得 无效了，那么此时另外一个任务获取该信号量的时候，就会无法获取成功，该任务便会进入阻塞态，阻塞时间由用户指定。

* xSemaphoreTake

xSemaphoreTake()函数用于获取信号量，不带中断保护。获取的信号量对象可以是二值信号量、计数信号量和互斥量，但是递归互斥量并不能使用这个API函数获取。其实获取信号量是一个宏，真正调用的函数是xQueueGenericReceive ()。该宏不能在中断使用，而是必须由具体中断保护功能的xQueueReceiveFromISR()版本代替。

* xSemaphoreTakeFromISR

xSemaphoreTakeFromISR()是函数xSemaphoreTake()的中断版本，用于获取信号量，是一个不带阻塞机制获取信号量的函数，获取对象必须由是已经创建的信号量，信号量类型可以是二值信号量和计数信号量，它与xSemaphoreTake()函数不同，它不能用于获取互斥量，因为互斥量 不可以在中断中使用，并且互斥量特有的优先级继承机制只能在任务中起作用，而在中断中毫无意义。

#### 信号量实验

##### 二值信号量同步实验

信号量同步实验是在FreeRTOS中创建了两个任务，一个是获取信号量任务，一个是释放互斥量任务，两个任务独立运行，获取信号量任务是一直在等待信号量，其等待时间是portMAX_DELAY，等到获取到信号量之后，任务开始执行任务代码，如此反复等待另外任务释放的信号量。

释放信号量任务在检测按键是否按下，如果按下则释放信号量，此时释放信号量会唤醒获取任务，获取任务开始运行，然后形成两个任务间的同步，因为如果没按下按键，那么信号量就不会释放，只有当信号量释放的时候，获取信号量的任务才会被唤醒，如此一来就达到任务与任务的同步，同时程序的运行会在串口打印出相关信息。

* 创建互斥信号量：

```c
BinarySem_Handle = xSemaphoreCreateBinary();	 
if(NULL != BinarySem_Handle)
	printf("BinarySem_Handle二值信号量创建成功!\r\n");
```

* 创建获取信号量任务：

```c
static void Receive_Task(void* parameter)
{	
  BaseType_t xReturn = pdPASS;/* 定义一个创建信息返回值，默认为pdPASS */
  while (1)
  {
    //获取二值信号量 xSemaphore,没获取到则一直等待
		xReturn = xSemaphoreTake(BinarySem_Handle,/* 二值信号量句柄 */
                              portMAX_DELAY); /* 等待时间 */
    if(pdTRUE == xReturn)
      printf("BinarySem_Handle二值信号量获取成功!\n\n");
		LED1_TOGGLE;
  }
}
```

* 创建释放互斥量任务：

```c
static void Send_Task(void* parameter)
{	 
  BaseType_t xReturn = pdPASS;/* 定义一个创建信息返回值，默认为pdPASS */
  while (1)
  {
    /* K1 被按下 */
    if( Key_Scan(KEY1_GPIO_PORT,KEY1_GPIO_PIN) == KEY_ON )
    {
      xReturn = xSemaphoreGive( BinarySem_Handle );//给出二值信号量
      if( xReturn == pdTRUE )
        printf("BinarySem_Handle二值信号量释放成功!\r\n");
      else
        printf("BinarySem_Handle二值信号量释放失败!\r\n");
    } 
    /* K2 被按下 */
    if( Key_Scan(KEY2_GPIO_PORT,KEY2_GPIO_PIN) == KEY_ON )
    {
      xReturn = xSemaphoreGive( BinarySem_Handle );//给出二值信号量
      if( xReturn == pdTRUE )
        printf("BinarySem_Handle二值信号量释放成功!\r\n");
      else
        printf("BinarySem_Handle二值信号量释放失败!\r\n");
    }
    vTaskDelay(20);
  }
}
```

##### 计数信号量实验

计数型信号量实验是模拟停车场工作运行。在创建信号量的时候初始化5个可用的信号量，并且创建了两个任务：一个是获取信号量任务，一个是释放信号量任务，两个任务独立运行，获取信号量任务是通过按下KEY1按键进行信号量的获取，模拟停车场停车操作，其等待时间是0，在串口调试助手输出相应信息。

释放信号量任务则是信号量的释放，释放信号量任务也是通过按下KEY2按键进行信号量的释放，模拟停车场取车操作，在串口调试助手输出相应信息。

* 创建计数信号量：

```c
CountSem_Handle = xSemaphoreCreateCounting(5,5);	
if(NULL != CountSem_Handle)
  printf("CountSem_Handle计数信号量创建成功!\r\n");
```

* 创建获取信号量任务：

```c
static void Take_Task(void* parameter)
{	
  BaseType_t xReturn = pdTRUE;/* 定义一个创建信息返回值，默认为pdPASS */
  /* 任务都是一个无限循环，不能返回 */
  while (1)
  {
    //如果KEY1被单击
		if( Key_Scan(KEY1_GPIO_PORT,KEY1_GPIO_PIN) == KEY_ON )       
		{
			/* 获取一个计数信号量 */
      xReturn = xSemaphoreTake(CountSem_Handle,	/* 计数信号量句柄 */
                             0); 	/* 等待时间：0 */
			if ( pdTRUE == xReturn ) 
				printf( "KEY1被按下，成功申请到停车位。\n" );
			else
				printf( "KEY1被按下，不好意思，现在停车场已满！\n" );							
		}
		vTaskDelay(20);     //每20ms扫描一次		
  }
}
```

* 创建释放信号量任务：

```c
static void Give_Task(void* parameter)
{	 
  BaseType_t xReturn = pdTRUE;/* 定义一个创建信息返回值，默认为pdPASS */
  /* 任务都是一个无限循环，不能返回 */
  while (1)
  {
    //如果KEY2被单击
		if( Key_Scan(KEY2_GPIO_PORT,KEY2_GPIO_PIN) == KEY_ON )       
		{
			/* 获取一个计数信号量 */
      xReturn = xSemaphoreGive(CountSem_Handle);//给出计数信号量                  
			if ( pdTRUE == xReturn ) 
				printf( "KEY2被按下，释放1个停车位。\n" );
			else
				printf( "KEY2被按下，但已无车位可以释放！\n" );							
		}
		vTaskDelay(20);     //每20ms扫描一次	
  }
}
```

### 互斥量

#### 互斥量基本概念

互斥量又称互斥信号量（本质是信号量），是一种特殊的二值信号量，它和信号量不同的是，它支持互斥量所有权、递归访问以及防止优先级翻转的特性，用于实现对临界资源的独占式处理。任意时刻互斥量的状态只有两种，开锁或闭锁。当互斥量被任务持有时，该互斥量处于闭锁状态，这个任务获得互斥量的所有权。当该任务释放这个互斥量时，该互斥量处于开锁状态，任务失去该互斥量的所有权。当一个任务持有互斥量时，其他任务将不能再对该互斥量进行开锁或持有。持有该互斥量的任务也能够再次获得这个锁而不被挂起，这就是递归访问，也就是递归互斥量的特性，这个特性与一般的信号量有很大的不同，在信号量中，由于已经不存在可用的信号量，任务递归获取 信号量时会发生主动挂起任务最终形成死锁。

如果想要用于实现同步（任务之间或者任务与中断之间），二值信号量或许是更好的选择，虽然互斥量也可以用于任务与任务、任务与中断的同步，但是互斥量更多的是用于保护资源的互锁。

用于互锁的互斥量可以充当保护资源的令牌，当一个任务希望访问某个资源时，它必须先获取令牌。当任务使用完资源后，必须还回令牌，以便其他任务可以访问该资源。是不是很熟悉，在我们的二值信号量里面也是一样的，用于保护临界资源，保证多任务的访问井然有序。当任务获取到信号量的时候才能开始使用被保护的资源，使用完就释放信号量，下一个任务才能获取到信号量从而可用使用被保护的资源。但是信号量会导致的另一个潜在问题，那就是**任务优先级翻转**（具体会在下文讲解）。而FreeRTOS提供的互斥量可以通过优先级继承算法，可以降低优先级翻转问题产生的影响，所以，**用于临界资源的保护一般建议使用互斥量**。

#### 互斥量的优先级继承机制

在FreeRTOS操作系统中为了降低优先级翻转问题利用了优先级继承算法。优先级继承算法是指，暂时提高某个占有某种资源的低优先级任务的优先级，使之与在所有等待该资源的任务中优先级最高那个任务的优先级相等，而当这个低优先级任务执行完毕释放该资源时，优先级重新回到初始设定值。因此，继承优先级的任务避免了系统资源被任何中间优先级的任务抢占。

互斥量与二值信号量最大的不同是：互斥量具有优先级继承机制，而信号量没有。也就是说，某个临界资源受到一个互斥量保护，如果这个资源正在被一个低优先级任务使用，那么此时的互斥量是闭锁状态，也代表了没有任务能申请到这个互斥量，如果此时一个高优先级任务想要对这个资源进行访问，去申请这个互斥量，那么高优先级任务 会因为申请不到互斥量而进入阻塞态，那么系统会将现在持有该互斥量的任务的优先级临时提升到与高优先级任务的优先级相同，这个优先级提升的过程叫做优先级继承。这个优先级继承机制确保高优先级任务进入阻塞状态的时间尽可能短，以及将已经出现的“优先级翻转”危害降低到最小。

没有理解？没问题，结合过程示意图再说一遍。我们知道任务的优先级在创建的时候就已经是设置好的，高优先级的任务可以打断低优先级的任务，抢占CPU的使用权。但是在很多场合中，某**些资源只有一个，当低优先级任务正在占用该资源的时候，即便高优先级任务也只能乖乖的等待低优先级任务使用完该资源后释放资源**。这里高优先级任务无法运行而低优先级任务可以运行的现象称为“优先级翻转”。

为什么说优先级翻转在操作系统中是危害很大？因为在我们一开始创造这个系统的时候，我们就已经设置好了任务的优先级了，越重要的任务优先级越高。但是发生优先级翻转，对我们操作系统是致命的危害，会导致系统的高优先级任务阻塞时间过长。

举个例子，现在有3个任务分别为H任务（High）、M任务（Middle）、L任务（Low），3个任务的优先级顺序为H任务>M任务>L任务。正常运行的时候H任务可以打断M任务与L任务，M任务可以打断L任务，假设系统中有一个资源被保护了，此时该资源被L任务正在使用中，某一刻，H任务需要使用该资源，但是L任务还没使用完，H任务则因为申请不到资源而进入阻塞态，L任务继续使用该资源，此时已经出现了“优先级翻转”现象，高优先级任务在等着低优先级的任务执行，如果在L任务执行的时候刚好M任务被唤醒了，由于M任务优先级比L任务优先级高，那么会打断L任务，抢占了CPU的使用权，直到M任务执行完，再把CPU使用权归 还给L任务，L任务继续执行，等到执行完毕之后释放该资源，H任务此时才从阻塞态解除，使用该资源。这个过程，本来是最高优先级的H任务，在等待了更低优先级的L任务与M任务，其阻塞的时间是M任务运行时间+L任务运行时间，这只有3个任务的系统，假如很多个这样子的任务打断最低优先级的任务，那这个系统最高优先级任务岂不是崩溃了，这个现象是绝对不允许出现的，高优先级的任务必须能及时响应。所以，没有优先级继承的情况下，使用资源保护，其危害极大。

假如有优先级继承呢？那么，在H任务申请该资源的时候，由于申请不到资源会进入阻塞态，那么系统就会把当前正在使用资源的L任务的优先级临时提高到与H任务优先级相同，此时M任务被唤醒了，因为它的优先级比H任务低，所以无法打断L任务，因为此时L任务的优先级被临时提升到H，所以当L任务使用完该资源了，进行释放， 那么此时H任务优先级最高，将接着抢占CPU的使用权， H任务的阻塞时间仅仅是L任务的执行时间，此时的优先级的危害降到了最低，看！这就是优先级继承的优势。

但是使用互斥量的时候一定需要注意：在获得互斥量后，请尽快释放互斥量，同时需要注意的是在任务持有互斥量的这段时间，不得更改任务的优先级。FreeRTOS的优先级继承机制不能解决优先级反转，只能将这种情况的影响降低到最小，硬实时系统在一开始设计时就要避免优先级反转发生。

#### 互斥量应用场景

互斥量的使用比较单一，因为它是信号量的一种，并且它是以锁的形式存在。在初始化的时候，互斥量处于开锁的状态，而被任务持有的时候则立刻转为闭锁的状态。互斥量更适合于：

- 可能会引起优先级翻转的情况。

递归互斥量更适用于：

- 任务可能会多次获取互斥量的情况下。这样可以避免同一任务多次递归持有而造成死锁的问题。

多任务环境下往往存在多个任务竞争同一临界资源的应用场景，互斥量可被用于对临界资源的保护从而实现独占式访问。另外，互斥量可以降低信号量存在的优先级翻转问题带来的影响。

比如有两个任务需要对串口进行发送数据，其硬件资源只有一个，那么两个任务肯定不能同时发送啦，不然导致数据错误，那么，就可以用互斥量对串口资源进行保护，当一个任务正在使用串口的时候，另一个任务则无法使用串口，等到任务使用串口完毕之后，另外一个任务才能获得串口的使用权。

另外需要注意的是互斥量不能在中断服务函数中使用，因为其特有的优先级继承机制只在任务起作用，在中断的上下文环境毫无意义。

#### 互斥量运作机制

多任务环境下会存在多个任务访问同一临界资源的场景，该资源会被任务独占处理。其他任务在资源被占用的情况下不允许对该临界资源进行访问，这个时候就需要用到FreeRTOS的互斥量来进行资源保护，那么互斥量是怎样来避免这种冲突？

用互斥量处理不同任务对临界资源的同步访问时，任务想要获得互斥量才能进行资源访问，如果一旦有任务成功获得了互斥量，则互斥量立即变为闭锁状态，此时其他任务会因为获取不到互斥量而不能访问这个资源，任务会根据用户自定义的等待时间进行等待，直到互斥量被持有的任务释放后，其他任务才能获取互斥量从而得以访问该临界资源，此时互斥量再次上锁，如此一来就可以确保每个时刻只有一个任务正在访问这个临界资源，保证了临界资源操作的安全性。

#### 互斥量控制块

互斥量的API函数实际上都是宏，它使用现有的队列机制，这些宏定义在semphr.h文件中，如果使用互斥量，需要包含semphr.h头文件。所以FreeRTOS的互斥量控制块结构体与消息队列结构体是一模一样的，只不过结构体中某些成员变量代表的含义不一样而已。

#### 互斥量函数接口讲解

##### 互斥量创建函数xSemaphoreCreateMutex

xSemaphoreCreateMutex()用于创建一个互斥量，并返回一个互斥量句柄。该句柄的原型是一个void 型的指针，在使用之前必须先由用户定义一个互斥量句柄。要想使用该函数必须在FreeRTOSConfig.h中把宏[configSUPPORT_DYNAMIC_ALLOCATION](http://www.freertos.org/a00110.html#configSUPPORT_DYNAMIC_ALLOCATION)定义为1，即开启动态内存分配，其实该宏在FreeRTOS.h中默认定义为1，即所有FreeRTOS的对象在创建的时候都默认使用动态内存分配方案，同时还需在FreeRTOSConfig.h中把configUSE_MUTEXES宏定义打开，表示使用互斥量。

##### 递归互斥量创建函数xSemaphoreCreateRecursiveMutex

xSemaphoreCreateRecursiveMutex()用于创建一个递归互斥量，不是递归的互斥量由函数xSemaphoreCreateMutex() 或xSemaphoreCreateMutexStatic()创建（我们只讲解动态创建），且只能被同一个任务获取一次，如果同一个任务想再次获取则会失败。递归信号量则相反，它可以被同一个任务获取很多次，获取多少次就需要释放多少次。递归信号量与互斥量一样，都实现了优先级继承机制，可以减少优先级反转的反生。

##### 互斥量删除函数vSemaphoreDelete

互斥量的本质是信号量，直接调用vSemaphoreDelete()函数进行删除即可

##### 互斥量获取函数xSemaphoreTake

我们知道，当互斥量处于开锁的状态，任务才能获取互斥量成功，当任务持有了某个互斥量的时候，其他任务就无法获取这个互斥量，需要等到持有互斥量的任务进行释放后，其他任务才能获取成功，任务通过互斥量获取函数来获取互斥量的所有权。任务对互斥量的所有权是独占的，任意时刻互斥量只能被一个任务持有，如果互斥量处于开锁状态，那么获取该互斥量的任务将成功获得该互斥量，并拥有互斥量的使用权；如果互斥量处于闭锁状态，获取该互斥量的任务将无法获得互斥量，任务将被挂起，在任务被挂起之前，会进行优先级继承，如果当前任务优先级比持有互斥量的任务优先级高，那么将会临时提升持有互斥量任务的优先级。互斥量的获取函数是一个宏定义，实际调用的函数就是xQueueGenericReceive()。

##### 递归互斥量获取函数xSemaphoreTakeRecursive

xSemaphoreTakeRecursive()是一个用于获取递归互斥量的宏，与互斥量的获取函数一样，xSemaphoreTakeRecursive()也是一个宏定义，它最终使用现有的队列机制，实际执行的函数是xQueueTakeMutexRecursive()。互斥量之前必须由xSemaphor eCreateRecursiveMutex()这个函数创建。要注意的是该函数不能用于获取由函数xSemaphoreCreateMutex()创建的互斥量。要想使用该函数必须在头文件FreeRTOSConfig.h 中把宏configUSE_RECURSIVE_MUTEXES定义为1。

##### 互斥量释放函数xSemaphoreGive

任务想要访问某个资源的时候，需要先获取互斥量，然后进行资源访问，在任务使用完该资源的时候，必须要及时归还互斥量，这样别的任务才能对资源进行访问。在前面的讲解中，我们知道，当互斥量有效的时候，任务才能获取互斥量，那么，是什么函数使得信号量变得有效呢？FreeRTOS给我们提供了互斥量释放函数xSema phoreGive()，任务可以调用xSemaphoreGive()函数进行释放互斥量，表示我已经用完了，别人可以申请使用，互斥量的释放函数与信号量的释放函数一致，都是调用xSemaphoreGive()函数，但是要注意的是，**互斥量的释放只能在任务中，不允许在中断中释放互斥量**。

使用该函数接口时，只有已持有互斥量所有权的任务才能释放它，当任务调用xSemaphoreGive()函数时会将互斥量变为开锁状态，等待获取该互斥量的任务将被唤醒。如果任务的优先级被互斥量的优先级翻转机制临时提升，那么当互斥量被释放后，任务的优先级将恢复为原本设定的优先级

##### 递归互斥量释放函数xSemaphoreGiveRecursive

xSemaphoreGiveRecursive()函数用于释放一个递归互斥量。已经获取递归互斥量的任务可以重复获取该递归互斥量。**使用xSemaphoreTakeRecursive() 函数成功获取几次递归互斥量，就要使用xSemaphoreGiveRecursive()函数返还几次**，在此之前递归互斥 量都处于无效状态，别的任务就无法获取该递归互斥量。使用该函数接口时，只有已持有互斥量所有权的任务才能释放它，每释放一次该递归互斥量，它的计数值就减1。当该互斥量的计数值为0时（即持有任务已经释放所有的持有操作），互斥量则变为开锁状态，等待在该互斥量上的任务将被唤醒。如果任务的优先级被互斥量的优先级翻 转机制临时提升，那么当互斥量被释放后，任务的优先级将恢复为原本设定的优先级。

#### 互斥量实验

##### 模拟优先级翻转实验

模拟优先级翻转实验是在FreeRTOS中创建了三个任务与一个二值信号量，任务分别是高优先级任务，中优先级任务，低优先级任务，用于模拟产生优先级翻转。低优先级任务在获取信号量的时候，被中优先级打断，中优先级的任务执行时间较长，因为低优先级还未释放信号量，那么高优先级任务就无法取得信号量继续运行，此时就 发生了优先级翻转，任务在运行中，使用串口打印出相关信息。

##### 互斥量实验

互斥量实验是基于优先级翻转实验进行修改的，目的是为了测试互斥量的优先级继承机制是否有效。

* 创建互斥量：

```c
MuxSem_Handle = xSemaphoreCreateMutex();	 
if(NULL != MuxSem_Handle)
	printf("MuxSem_Handle互斥量创建成功!\r\n");
```

### 事件

#### 事件的基本概念

事件是一种实现任务间通信的机制，主要用于实现多任务间的同步，但**事件通信只能是事件类型的通信，无数据传输**。与信号量不同的是，它可以实现一对多，多对多的同步。即一个任务可以等待多个事件的发生：可以是任意一个事件发生时唤醒任务进行事件处理；也可以是几个事件都发生后才唤醒任务进行事件处理。同样，也可以是多个任务同步多个事件。

每一个事件组只需要很少的RAM空间来保存事件组的状态。事件组存储在一个EventBits_t类型的变量中，该变量在事件组结构体中定义。如果宏[configUSE_16_BIT_TICKS](http://www.freertos.org/a00110.html#configUSE_16_BIT_TICKS) 定义为1，那么变量uxEventBits就是16位的，其中有8个位用来存储事件组；而如果宏[configUSE_16_BIT_TICKS](http://www.freertos.org/a00110.html#configUSE_16_BIT_TICKS) 定义为0，那么变量uxEventBits就是32位的，其中有24个位用来存储事件组。**在STM32中，我们一般将[configUSE_16_BIT_TICKS](http://www.freertos.org/a00110.html#configUSE_16_BIT_TICKS) 定义为0，那么uxEventBits是32位的，有24个位用来实现事件标志组。每一位代表一个事件，任务通过“逻辑与”或“逻辑或”与一个或多个事件建立关联，形成一个事件组。**事件的“逻辑 或”也被称作是**独立型同步**，指的是任务感兴趣的所有事件任一件发生即可被唤醒；事件“逻辑与”则被称为是**关联型同步**，指的是任务感兴趣的若干事件都发生时才被唤醒，并且事件发生的时间可以不同步。

多任务环境下，任务、中断之间往往需要同步操作，一个事件发生会告知等待中的任务，即形成一个任务与任务、中断与任务间的同步。事件可以提供一对多、多对多的同步操作。一对多同步模型：一个任务等待多个事件的触发，这种情况是比较常见的；多对多同步模型：多个任务等待多个事件的触发。

任务可以通过设置事件位来实现事件的触发和等待操作。FreeRTOS的事件仅用于同步，不提供数据传输功能。

FreeRTOS提供的事件具有如下特点：

- 事件只与任务相关联，事件相互独立，一个32位的事件集合（EventBits_t类型的变量，实际可用与表示事件的只有24位），用于标识该任务发生的事件类型，其中每一位表示一种事件类型（0表示该事件类型未发生、1表示该事件类型已经发生），一共24种事件类型。
- 事件仅用于同步，不提供数据传输功能。
- 事件无排队性，即多次向任务设置同一事件(如果任务还未来得及读走)，等效于只设置一次。
- 允许多个任务对同一事件进行读写操作。
- 支持事件等待超时机制。

在FreeRTOS事件中，每个事件获取的时候，用户可以选择感兴趣的事件，并且选择读取事件信息标记，它有三个属性，分别是逻辑与，逻辑或以及是否清除标记。当任务等待事件同步时，可以通过任务感兴趣的事件位和事件信息标记来判断当前接收的事件是否满足要求，如果满足则说明任务等待到对应的事件，系统将唤醒等待的任 务；否则，任务会根据用户指定的阻塞超时时间继续等待下去。

#### 事件的应用场景

FreeRTOS的事件用于事件类型的通信，无数据传输，也就是说，我们可以用事件来做标志位，判断某些事件是否发生了，然后根据结果做处理，那很多人又会问了，为什么我不直接用变量做标志呢，岂不是更好更有效率？非也非也，若是在裸机编程中，用全局变量是最为有效的方法，这点我不否认，但是在操作系统中，使用全局变量就要考虑以下问题了：

- 如何对全局变量进行保护呢，如何处理多任务同时对它进行访问？
- 如何让内核对事件进行有效管理呢？使用全局变量的话，就需要在任务中轮询查看事件是否发送，这简直就是在浪费CPU资源啊，还有等待超时机制，使用全局变量的话需要用户自己去实现。

所以，在操作系统中，还是使用操作系统给我们提供的通信机制就好了，简单方便还实用。

在某些场合，可能需要多个时间发生了才能进行下一步操作，比如一些危险机器的启动，需要检查各项指标，当指标不达标的时候，无法启动，但是检查各个指标的时候，不能一下子检测完毕啊，所以，需要事件来做统一的等待，当所有的事件都完成了，那么机器才允许启动，这只是事件的其中一个应用。

事件可使用于多种场合，它能够在一定程度上替代信号量，用于任务与任务间，中断与任务间的同步。一个任务或中断服务例程发送一个事件给事件对象，而后等待的任务被唤醒并对相应的事件进行处理。但是它与信号量不同的是，事件的发送操作是不可累计的，而信号量的释放动作是可累计的。事件另外一个特性是，接收任务可等待多种 事件，即多个事件对应一个任务或多个任务。同时按照任务等待的参数，可选择是“逻辑或”触发还是“逻辑与”触发。这个特性也是信号量等所不具备的，信号量只能识别单一同步动作，而不能同时等待多个事件的同步。

**各个事件可分别发送或一起发送给事件对象，而任务可以等待多个事件，任务仅对感兴趣的事件进行关注。当有它们感兴趣的事件发生时并且符合感兴趣的条件，任务将被唤醒并进行后续的处理动作**。

#### 事件运作机制

接收事件时，可以根据感兴趣的参事件类型接收事件的单个或者多个事件类型。事件接收成功后，必须使用xClearOnExit选项来清除已接收到的事件类型，否则不会清除已接收到的事件，这样就需要用户显式清除事件位。用户可以自定义通过传入参数xWaitForAllBits选择读取模式，是等待所有感兴趣的事件还 是等待感兴趣的任意一个事件。

设置事件时，对指定事件写入指定的事件类型，设置事件集合的对应事件位为1，可以一次同时写多个事件类型，设置事件成功可能会触发任务调度。

清除事件时，根据入参数事件句柄和待清除的事件类型，对事件对应位进行清0操作。事件不与任务相关联，事件相互独立，一个32位的变量（事件集合，实际用于表示事件的只有24位），用于标识该任务发生的事件类型，其中每一位表示一种事件类型（0表示该事件类型未发生、1表示该事件类型已经发生），一共24种事件类型

#### 事件控制块

事件标志组存储在一个EventBits_t类型的变量中，该变量在事件组结构体中定义，具体见代码清单18‑1加粗部分。如果宏[configUSE_16_BIT_TICKS](http://www.freertos.org/a00110.html#configUSE_16_BIT_TICKS) 定义为1，那么变量uxEventBits就是16位的，其中有8个位用来存储事件组，如果宏[configUSE_16_BIT_TICKS](http://www.freertos.org/a00110.html#configUSE_16_BIT_TICKS) 定义为0，那么变量uxEventBits就是32位的，其中有24个位用来存储事件组，每一位代表一个事件的发生与否，利用逻辑或、逻辑与等实现不同事件的不同唤醒处理。在STM32中，uxEventBits是3 2位的，所以我们有24个位用来实现事件组。除了事件标志组变量之外，FreeRTOS还使用了一个链表来记录等待事件的任务，所有在等待此事件的任务均会被挂载在等待事件列表xTasksWaitingForBits。

#### 事件函数接口讲解

##### 事件创建函数xEventGroupCreate

xEventGroupCreate()用于创建一个事件组，并返回对应的句柄。要想使用该函数必须在头文件FreeRTOSConfig.h定义宏[configSUPPORT_DYNAMIC_ALLOCATION](http://www.freertos.org/a00110.html#configSUPPORT_DYNAMIC_ALLOCATION) 为1（在FreeRTOS.h中默认定义为1）且需要把FreeRTOS/source/event_groups.c 这个C文件添加到工程中。

每一个事件组只需要很少的RAM空间来保存事件的发生状态。如果使用函数xEventGroupCreate()来创建一个事件，那么需要的RAM是动态分配的。如果使用函数[xEventGroupCreateStatic](http://www.freertos.org/xEventGroupCreateStatic.html)()来创建一个事件，那么需要的RAM是静态分配的。我们暂时不讲解静态创建函数[xEventGroupCreateStatic](http://www.freertos.org/xEventGroupCreateStatic.html)()。

事件创建函数，顾名思义，就是创建一个事件，与其他内核对象一样，都是需要先创建才能使用的资源，FreeRTOS给我们提供了一个创建事件的函数xEventGroupCreate()，当创建一个事件时，系统会首先给我们分配事件控制块的内存空间，然后对该事件控制块进行基本的初始化，创建成功返回事件句柄；创建 失败返回NULL。所以，在使用创建函数之前，我们需要先定义有个事件的句柄。

##### 事件删除函数vEventGroupDelete

在很多场合，某些事件只用一次的，就好比在事件应用场景说的危险机器的启动，假如各项指标都达到了，并且机器启动成功了，那这个事件之后可能就没用了，那就可以进行销毁了。想要删除事件怎么办？FreeRTOS给我们提供了一个删除事件的函数——vEventGroupDelete()，使用它就能将事件进行删除了。 当系统不再使用事件对象时，可以通过删除事件对象控制块来释放系统资源。

##### 事件组置位函数xEventGroupSetBits

xEventGroupSetBits()用于置位事件组中指定的位，当位被置位之后，阻塞在该位上的任务将会被解锁。使用该函数接口时，通过参数指定的事件标志来设定事件的标志位，然后遍历等待在事件对象上的事件等待列表，判断是否有任务的事件激活要求与当前事件对象标志值匹配，如果有，则唤醒该任务。简单来说，就 是设置我们自己定义的事件标志位为1，并且看看有没有任务在等待这个事件，有的话就唤醒它。

##### 事件组置位函数xEventGroupSetBitsFromISR

xEventGroupSetBitsFromISR()是xEventGroupSetBits()的中断版本，用于置位事件组中指定的位。置位事件组中的标志位是一个不确定的操作，因为阻塞在事件组的标志位上的任务的个数是不确定的。FreeRTOS是不允许不确定的操作在中断和临界段中发生的，所以xEvent GroupSetBitsFromISR()给FreeRTOS的守护任务发送一个消息，让置位事件组的操作在守护任务里面完成，守护任务是基于调度锁而非临界段的机制来实现的。

需要注意的地方：正如上文提到的那样，在中断中事件标志的置位是在守护任务（也叫软件定时器服务任务）中完成的。因此FreeRTOS的守护任务与其他任务一样，都是系统调度器根据其优先级进行任务调度的，但守护任务的优先级必须比任何任务的优先级都要高，保证在需要的时候能立即切换任务从而达到快速处理的目的，因为 这是在中断中让事件标志位置位，其优先级由FreeRTOSConfig.h中的宏[configTIMER_TASK_PRIORITY](http://www.freertos.org/Configuring-a-real-time-RTOS-application-to-use-software-timers.html) 来定义。

其实xEventGroupSetBitsFromISR()函数真正调用的也是xEventGroupSetBits()函数，只不过是在守护任务中进行调用的，所以它实际上执行的上下文环境依旧是在任务中。

要想使用该函数，必须把configUSE_TIMERS 和 INCLUDE_xTimerPendFunctionCall 这些宏在FreeRTOSConfig.h中都定义为1，并且把FreeRTOS/source/event_groups.c 这个C文件添加到工程中编译。

##### 等待事件函数xEventGroupWaitBits

既然标记了事件的发生，那么我怎么知道他到底有没有发生，这也是需要一个函数来获取事件是否已经发生，FreeRTOS提供了一个等待指定事件的函数——xEventGroupWaitBits()，通过这个函数，任务可以知道事件标志组中的哪些位，有什么事件发生了，然后通过“逻辑与”、“逻辑或”等操作对感兴趣的 事件进行获取，并且这个函数实现了等待超时机制，当且仅当任务等待的事件发生时，任务才能获取到事件信息。在这段时间中，如果事件一直没发生，该任务将保持阻塞状态以等待事件发生。当其他任务或中断服务程序往其等待的事件设置对应的标志位，该任务将自动由阻塞态转为就绪态。当任务等待的时间超过了指定的阻塞时间，即使 事件还未发生，任务也会自动从阻塞态转移为就绪态。这样子很有效的体现了操作系统的实时性，如果事件正确获取（等待到）则返回对应的事件标志位，由用户判断再做处理，因为在事件超时的时候也会返回一个不能确定的事件值，所以需要判断任务所等待的事件是否真的发生。

EventGroupWaitBits()用于获取事件组中的一个或多个事件发生标志，当要读取的事件标志位没有被置位时任务将进入阻塞等待状态。要想使用该函数必须把FreeRTOS/source/event_groups.c 这个C文件添加到工程中。

##### 事件组清除函数

xEventGroupClearBits()与xEventGroupClearBitsFromISR()都是用于清除事件组指定的位，如果在获取事件的时候没有将对应的标志位清除，那么就需要用这个函数来进行显式清除，xEventGroupClearBits()函数不能在中断中使用，而是由具有中断保护功能 的[xEventGroupClearBitsFromISR()](http://www.freertos.org/xEventGroupSetBitsFromISR.html) 来代替，中断清除事件标志位的操作在守护任务（也叫定时器服务任务）里面完成。守护进程的优先级由FreeRTOSConfig.h中的宏[configTIMER_TASK_PRIORITY](http://www.freertos.org/Configuring-a-real-time-RTOS-application-to-use-software-timers.html) 来定义。要想使用该函数必须把FreeRTOS/source/event_groups.c 这个C文件添加到工程中。

#### 事件实验

事件标志组实验是在FreeRTOS中创建了两个任务，一个是设置事件任务，一个是等待事件任务，两个任务独立运行，设置事件任务通过检测按键的按下情况设置不同的事件标志位，等待事件任务则获取这两个事件标志位，并且判断两个事件是否都发生，如果是则输出相应信息，LED进行翻转。等待事件任务的等待时间是port MAX_DELAY，一直在等待事件的发生，等待到事件之后清除对应的事件标记位。

* 创建事件组：

```c
 Event_Handle = xEventGroupCreate();	 
 if(NULL != Event_Handle)
   printf("Event_Handle 事件创建成功!\r\n");
```

* 创建设置事件任务：

```c
static void KEY_Task(void* parameter)
{	 
    /* 任务都是一个无限循环，不能返回 */
  while (1)
  {
    if( Key_Scan(KEY1_GPIO_PORT,KEY1_GPIO_PIN) == KEY_ON )       //如果KEY2被单击
		{
      printf ( "KEY1被按下\n" );
			/* 触发一个事件1 */
			xEventGroupSetBits(Event_Handle,KEY1_EVENT);  					
		}
    
		if( Key_Scan(KEY2_GPIO_PORT,KEY2_GPIO_PIN) == KEY_ON )       //如果KEY2被单击
		{
      printf ( "KEY2被按下\n" );	
			/* 触发一个事件2 */
			xEventGroupSetBits(Event_Handle,KEY2_EVENT); 				
		}
		vTaskDelay(20);     //每20ms扫描一次		
  }
}
```

* 创建等待事件任务：

```C
static void LED_Task(void* parameter)
{	
  EventBits_t r_event;  /* 定义一个事件接收变量 */
  /* 任务都是一个无限循环，不能返回 */
  while (1)
	{
    /*******************************************************************
     * 等待接收事件标志 
     * 
     * 如果xClearOnExit设置为pdTRUE，那么在xEventGroupWaitBits()返回之前，
     * 如果满足等待条件（如果函数返回的原因不是超时），那么在事件组中设置
     * 的uxBitsToWaitFor中的任何位都将被清除。 
     * 如果xClearOnExit设置为pdFALSE，
     * 则在调用xEventGroupWaitBits()时，不会更改事件组中设置的位。
     *
     * xWaitForAllBits如果xWaitForAllBits设置为pdTRUE，则当uxBitsToWaitFor中
     * 的所有位都设置或指定的块时间到期时，xEventGroupWaitBits()才返回。 
     * 如果xWaitForAllBits设置为pdFALSE，则当设置uxBitsToWaitFor中设置的任何
     * 一个位置1 或指定的块时间到期时，xEventGroupWaitBits()都会返回。 
     * 阻塞时间由xTicksToWait参数指定。          
      *********************************************************/
    r_event = xEventGroupWaitBits(Event_Handle,  /* 事件对象句柄 */
                                  KEY1_EVENT|KEY2_EVENT,/* 接收线程感兴趣的事件 */
                                  pdTRUE,   /* 退出时清除事件位 */
                                  pdTRUE,   /* 满足感兴趣的所有事件 */
                                  portMAX_DELAY);/* 指定超时事件,一直等 */
                        
    if((r_event & (KEY1_EVENT|KEY2_EVENT)) == (KEY1_EVENT|KEY2_EVENT)) 
    {
      /* 如果接收完成并且正确 */
      printf ( "KEY1与KEY2都按下\n");		
      LED1_TOGGLE;       //LED1	反转
    }
    else
      printf ( "事件错误！\n");	
  }
}
```

### 软件定时器

#### 软件定时器的基本概念

定时器，是指从指定的时刻开始，经过一个指定时间，然后触发一个超时事件，用户可以自定义定时器的周期与频率。类似生活中的闹钟，我们可以设置闹钟每天什么时候响，还能设置响的次数，是响一次还是每天都响。

定时器有**硬件定时器**和**软件定时器**之分：

硬件定时器是芯片本身提供的定时功能。一般是由外部晶振提供给芯片输入时钟，芯片向软件模块提供一组配置寄存器，接受控制输入，到达设定时间值后芯片中断控制器产生时钟中断。硬件定时器的精度一般很高，可以达到纳秒级别，并且是中断触发方式。

软件定时器，软件定时器是由操作系统提供的一类系统接口，它构建在硬件定时器基础之上，使系统能够提供不受硬件定时器资源限制的定时器服务，它实现的功能与硬件定时器也是类似的。

使用硬件定时器时，每次在定时时间到达之后就会自动触发一个中断，用户在中断中处理信息；而使用软件定时器时，需要我们在创建软件定时器时指定时间到达后要调用的函数（也称超时函数/回调函数，为了统一，下文均用回调函数描述），在回调函数中处理信息。

注意：软件定时器回调函数的上下文是任务，下文所说的定时器均为软件定时器。

软件定时器在被创建之后，当经过设定的时钟计数值后会触发用户定义的回调函数。定时精度与系统时钟的周期有关。一般系统利用SysTick作为软件定时器的基础时钟，软件定时器的回调函数类似硬件的中断服务函数，所以，回调函数也要快进快出，而且回调函数中不能有任何阻塞任务运行的情况（软件定时器回调函数的上下文环境是任务），比如vTaskDelay()以及其他能阻塞任务运行的函数，两次触发回调函数的时间间隔xTimerPeriodInTicks叫定时器的定时周期。

FreeRTOS操作系统提供软件定时器功能，软件定时器的使用相当于扩展了定时器的数量，允许创建更多的定时业务。FreeRTOS软件定时器功能上支持：

- 裁剪：能通过宏关闭软件定时器功能。
- 软件定时器创建。
- 软件定时器启动。
- 软件定时器停止。
- 软件定时器复位。
- 软件定时器删除。

FreeRTOS提供的软件定时器支持单次模式和周期模式，单次模式和周期模式的定时时间到之后都会调用软件定时器的回调函数，用户可以在回调函数中加入要执行的工程代码。

单次模式：当用户创建了定时器并启动了定时器后，定时时间到了，只执行一次回调函数之后就将该定时器删除，不再重新执行。

周期模式：这个定时器会按照设置的定时时间循环执行回调函数，直到用户将定时器删除。

FreeRTOS 通过一个prvTimerTask任务（也叫守护任务Daemon）管理软定时器，它是在启动调度器时自动创建的，为了满足用户定时需求。prvTimerTask任务会在其执行期间检查用户启动的时间周期溢出的定时器，并调用其回调函数。只有设置 FreeRTOSConfig.h 中的宏定义configUSE_TIMERS设置为1 ，将相关代码编译进来，才能正常使用软件定时器相关功能。

#### 软件定时器应用场景

在很多应用中，我们需要一些定时器任务，硬件定时器受硬件的限制，数量上不足以满足用户的实际需求，无法提供更多的定时器，那么可以采用软件定时器来完成，由软件定时器代替硬件定时器任务。但需要注意的是软件定时器的精度是无法和硬件定时器相比的，因为在软件定时器的定时过程中是极有可能被其他中断所打断，因为软件定时器的执行上下文环境是任务。所以，**软件定时器更适用于对时间精度要求不高的任务**，一些辅助型的任务。

#### 软件定时器的精度

在操作系统中，通常软件定时器以系统节拍周期为计时单位。系统节拍是系统的心跳节拍，表示系统时钟的频率，就类似人的心跳，1s能跳动多少下，系统节拍配置为configTICK_RATE_HZ，该宏在FreeRTOSConfig.h中有定义，默认是1000。那么系统的时钟节拍周期就为1ms（1s跳动1000 下，每一下就为1ms）。软件定时器的所定时数值必须是这个节拍周期的整数倍，例如节拍周期是10ms，那么上层软件定时器定时数值只能是10ms，20ms，100ms等，而不能取值为15ms。由于节拍定义了系统中定时器能够分辨的精确度，系统可以根据实际系统CPU的处理能力和实时性需求设置合适的数值，系统节拍周期的值越小，精度越高，但是系统开销也将越大，因为这代表在1秒中系统进入时钟中断的次数也就越多。

#### 软件定时器的运作机制

软件定时器是可选的系统资源，在创建定时器的时候会分配一块内存空间。当用户创建并启动一个软件定时器时，FreeRTOS会根据当前系统时间及用户设置的定时确定该定时器唤醒时间，并将该定时器控制块挂入软件定时器列表，FreeRTOS中采用两个定时器列表维护软件定时器，pxCurrentTimerList与 pxOverflowTimerList是列表指针，在初始化的时候分别指向xActiveTimerList1与xActiveTimerList2。

同时，FreeRTOS的软件定时器还有采用消息队列进行通信，利用“定时器命令队列”向软件定时器任务发送一些命令，任务在接收到命令就会去处理命令对应的程序，比如启动定时器，停止定时器等。假如定时器任务处于阻塞状态，我们又需要马上再添加一个软件定时器的话，就是采用这种消息队列命令的方式进行添加，才能唤醒处于等待状态的定时器任务，并且在任务中将新添加的软件定时器添加到软件定时器列表中，所以，在定时器启动函数中，FreeRTOS是采用队列的方式发送一个消息给软件定时器任务，任务被唤醒从而执行接收到的命令。

例如：系统当前时间xTimeNow值为0，注意：xTimeNow其实是一个局部变量，是根据xTaskGetTickCount()函数获取的，实际它的值就是全局变量xTickCount的值，下文都采用它表示当前系统时间。在当前系统中已经创建并启动了1个定时器Timer1；系统继续运行，当系统的时间xT imeNow为20的时候，用户创建并且启动一个定时时间为100的定时器Timer2，此时Timer2的溢出时间xTicksToWait就为定时时间+系统当前时间（100+20=120），然后将Timer2按xTicksToWait升序插入软件定时器列表中；假设当前系统时间xTimeNow为40的时候 ，用户创建并且启动了一个定时时间为50的定时器Timer3，那么此时Timer3的溢出时间xTicksToWait就为40+50=90，同样安装xTicksToWait的数值升序插入软件定时器列表中，在定时器链表中插入过程具体见图19‑2。同理创建并且启动在已有的两个定时器中间的定时器也是一样的

那么系统如何处理软件定时器列表？系统在不断运行，而xTimeNow（xTickCount）随着SysTick的触发一直在增长（每一次硬件定时器中断来临，xTimeNow变量会加1），在软件定时器任务运行的时候会获取下一个要唤醒的定时器，比较当前系统时间xTimeNow是否大于或等于下一个定时器唤醒时 间xTicksToWait，若大于则表示已经超时，定时器任务将会调用对应定时器的回调函数，否则将软件定时器任务挂起，直至下一个要唤醒的软件定时器时间到来或者接收到命令消息。以图19‑3为例，讲解软件定时器调用回调函数的过程，在创建定Timer1并且启动后，假如系统经过了50个tick，xTimeNo w从0增长到50，与Timer1的xTicksToWait值相等，这时会触发与Timer1对应的回调函数，从而转到回调函数中执行用户代码，同时将Timer1从软件定时器列表删除，如果软件定时器是周期性的，那么系统会根据Timer1下一次唤醒时间重新将Timer1添加到软件定时器列表中，按照xTick sToWait的升序进行排列。同理，在xTimeNow=40的时候创建的Timer3，在经过130个tick后（此时系统时间xTimeNow是40，130个tick就是系统时间xTimeNow为170的时候），与Timer3定时器对应的回调函数会被触发，接着将Timer3从软件定时器列表中删除，如果 是周期性的定时器，还会按照xTicksToWait升序重新添加到软件定时器列表中。

> 使用软件定时器时候要注意以下几点：

- 软件定时器的回调函数中应快进快出，绝对不允许使用任何可能引软件定时器起任务挂起或者阻塞的API接口，在回调函数中也绝对不允许出现死循环。
- 软件定时器使用了系统的一个队列和一个任务资源，软件定时器任务的优先级默认为configTIMER_TASK_PRIORITY，为了更好响应，该优先级应设置为所有任务中最高的优先级。
- 创建单次软件定时器，该定时器超时执行完回调函数后，系统会自动删除该软件定时器，并回收资源。
- 定时器任务的栈大小默认为configTIMER_TASK_STACK_DEPTH个字节。

#### 软件定时器控制块

软件定时器虽然不属于内核资源，但是也是FreeRTOS核心组成部分，是一个可以裁剪的功能模块，同样在系统中由一个控制块管理其相关信息，软件定时器的控制块中包含没用过创建的软件定时器基本信息，在使用定时器前我们需要通过xTimerCreate()/xTimerCreateStatic()函数创建一个软件定时器，在函数中，FreeRTOS将向系统管理的内存申请一块软件定时器控制块大小的内存用于保存定时器的信息。

#### 软件定时器函数接口讲解

软件定时器的功能是在定时器任务（或者叫定时器守护任务）中实现的。软件定时器的很多API函数通过一个名字叫“定时器命令队列”的队列来给定时器守护任务发送命令。该定时器命令队列由RTOS内核提供，且应用程序不能够直接访问，其消息队列的长度由宏configTIMER_QUEUE_LENGTH定义，下面就讲 解一些常用的软件定时器函数接口。

##### 软件定时器创建函数xTimerCreate

软件定时器与FreeRTOS内核其他资源一样，需要创建才允许使用的，FreeRTOS为我们提供了两种创建方式，一种是动态创建软件定时器xTimerCreate()，另一种是静态创建方式xTimerCreateStatic()，因为创建过程基本差不多，所以在这里我们只讲解动态创建方式。

xTimerCreate()用于创建一个软件定时器，并返回一个句柄。要想使用该函数函数必须在头文件FreeRTOSConfig.h中把宏configUSE_TIMERS 和[configSUPPORT_DYNAMIC_ALLOCATION](http://www.freertos.org/a00110.html#configSUPPORT_DYNAMIC_ALLOCATION) 均定义为1（[configSUPPORT_DYNAMIC_ALLOCATION](http://www.freertos.org/a00110.html#configSUPPORT_DYNAMIC_ALLOCATION)在FreeRTOS.h中默认定义为1），并且需要把FreeRTOS/source/times.c 这个C文件添加到工程中。

每一个软件定时器只需要很少的RAM空间来保存其的状态。如果使用函数xTimeCreate()来创建一个软件定时器，那么需要的RAM是动态分配的。如果使用函数[xTimeCreateStatic](http://www.freertos.org/xEventGroupCreateStatic.html)()来创建一个事件组，那么需要的RAM是静态分配的。

软件定时器在创建成功后是处于休眠状态的，可以使用[xTimerStart()](http://www.freertos.org/FreeRTOS-timers-xTimerStart.html)、[xTimerReset()](http://www.freertos.org/FreeRTOS-timers-xTimerReset.html)、[xTimerStartFromISR()](http://www.freertos.org/FreeRTOS-timers-xTimerStartFromISR.html)、[xTimerResetFromISR()](http://www.freertos.org/FreeRTOS-timers-xTimerResetFromISR.html)、 [xTimerChangePeriod()](http://www.freertos.org/FreeRTOS-timers-xTimerChangePeriod.html) 和[xTimerChangePeriodFromISR()](http://www.freertos.org/FreeRTOS-timers-xTimerChangePeriodFromISR.html)这些函数将其状态转换为活跃态。

##### 软件定时器启动函数

* xTimerStart

如果是认真看上面xTimerCreate()函数使用实例的同学应该就发现了，这个软件定时器启动函数xTimerStart()在上面的实例中有用到过，前一小节已经说明了，软件定时器在创建完成的时候是处于休眠状态的，需要用FreeRTOS的相关函数将软件定时器活动起来，而xTimerStart()函数就 是可以让处于休眠的定时器开始工作。

我们知道，在系统开始运行的时候，系统会帮我们自动创建一个软件定时器任务（prvTimerTask），在这个任务中，如果暂时没有运行中的定时器，任务会进入阻塞态等待命令，而我们的启动函数就是通过“定时器命令队列”向定时器任务发送一个启动命令，定时器任务获得命令就解除阻塞，然后执行启动软件定时器命令。

* xTimerStartFromISR

当然除在任务启动软件定时器之外，还有在中断中启动软件定时器的函数xTimerStartFromISR()。xTimerStartFromISR()是函数xTimerStart()的中断版本，用于启动一个先前由函数[xTimerCreate()](http://www.freertos.org/FreeRTOS-timers-xTimerCreate.html) /xTimerCreateStatic()创建的软件定时器。

##### 软件定时器停止函数

* xTimerStop

xTimerStop() 用于停止一个已经启动的软件定时器，该函数的实现也是通过“定时器命令队列”发送一个停止命令给软件定时器任务，从而唤醒软件定时器任务去将定时器停止。要想使函数xTimerStop()必须在头文件FreeRTOSConfig.h中把宏configUSE_TIMERS定义为1。

* xTimerStopFromISR

xTimerStopFromISR()是函数xTimerStop()的中断版本，用于停止一个正在运行的软件定时器，让其进入休眠态，实现过程也是通过“定时器命令队列”向软件定时器任务发送停止命令。

##### 软件定时器任务

我们知道，软件定时器回调函数运行的上下文环境是任务，那么软件定时器任务是在干什么的呢？如何创建的呢？下面跟我一步步来分析软件定时器的工作过程。

软件定时器任务是在系统开始调度（vTaskStartScheduler()函数）的时候就被创建的，前提是将宏定义configUSE_TIMERS开启，具体见代码清单19‑12加粗部分，在xTimerCreateTimerTask()函数里面就是创建了一个软件定时器任务，就跟我们创建任务一样，支持动态 与静态创建，我们暂时看动态创建的即可。

软件定时器任务的处理很简单，如果当前有软件定时器在运行，那么它大部分的时间都在等待定时器到期时间的到来，或者在等待对软件定时器操作的命令，而如果没有软件定时器在运行，那定时器任务的绝大部分时间都在阻塞中等待定时器的操作命令。

软件定时器是一个任务，在下一个定时器到了之前的这段时间，系统要把任务状态转移为阻塞态，让其他的任务能正常运行，这样子就使得系统的资源能充分利用。

##### 软件定时器删除函数xTimerDelete

xTimerDelete()用于删除一个已经被创建成功的软件定时器，删除之后就无法使用该定时器，并且定时器相应的资源也会被系统回收释放。要想使函数xTimerDelete()必须在头文件FreeRTOSConfig.h中把宏configUSE_TIMERS定义为1。

#### 软件定时器实验

软件定时器实验是在FreeRTOS中创建了两个软件定时器，其中一个软件定时器是单次模式，5000个tick调用一次回调函数，另一个软件定时器是周期模式，1000个tick调用一次回调函数，在回调函数中输出相关信息

* 定义软件定时器句柄：

```c
static TimerHandle_t Swtmr1_Handle =NULL;   /* 软件定时器句柄 */
static TimerHandle_t Swtmr2_Handle =NULL;   /* 软件定时器句柄 */
```

* 创建定时器1：

```c
  Swtmr1_Handle=xTimerCreate((const char*		)"AutoReloadTimer",
                            (TickType_t			)1000,/* 定时器周期 1000(tick) */
                            (UBaseType_t		)pdTRUE,/* 周期模式 */
                            (void*				  )1,/* 为每个计时器分配一个索引的唯一ID */
                            (TimerCallbackFunction_t)Swtmr1_Callback);
```

* 创建定时器2：

```c
	Swtmr2_Handle=xTimerCreate((const char*			)"OneShotTimer",
                             (TickType_t			)5000,/* 定时器周期 5000(tick) */
                             (UBaseType_t			)pdFALSE,/* 单次模式 */
                             (void*					  )2,/* 为每个计时器分配一个索引的唯一ID */
                             (TimerCallbackFunction_t)Swtmr2_Callback); 
```

* 定义定时器1的回调函数：

```c
static void Swtmr1_Callback(void* parameter)
{		
  TickType_t tick_num1;

  TmrCb_Count1++;						/* 每回调一次加一 */

  tick_num1 = xTaskGetTickCount();	/* 获取滴答定时器的计数值 */
  
  LED1_TOGGLE;
  
  printf("Swtmr1_Callback函数执行 %d 次\n", TmrCb_Count1);
  printf("滴答定时器数值=%d\n", tick_num1);
}
```

* 定义定时器2的回调函数：

```c
static void Swtmr2_Callback(void* parameter)
{	
  TickType_t tick_num2;

  TmrCb_Count2++;						/* 每回调一次加一 */

  tick_num2 = xTaskGetTickCount();	/* 获取滴答定时器的计数值 */

  printf("Swtmr2_Callback函数执行 %d 次\n", TmrCb_Count2);
  printf("滴答定时器数值=%d\n", tick_num2);
}
```

### 任务通知

#### 任务通知的基本概念

FreeRTOS 从V8.2.0版本开始提供任务通知这个功能，每个任务都有一个32位的通知值，在大多数情况下，任务通知可以替代二值信号量、计数信号量、事件组，也可以替代长度为1的队列（可以保存一个32位整数或指针值）。

相对于以前使用FreeRTOS内核通信的资源，必须创建队列、二进制信号量、计数信号量或事件组的情况，使用任务通知显然更灵活。按照 FreeRTOS 官方的说法，使用任务通知比通过信号量等ICP通信方式解除阻塞的任务要快 45%，并且更加省RAM内存空间（使用GCC编译器，-o2优化级别），任务通知的使用无需创建队列。想要使用任务通知，必须将FreeRTOSConfig.h中的宏定义configUSE_TASK_NOTIFICATIONS设置为1，其实FreeRTOS默认是为1的，所以任务通知是默认使能的。

FreeRTOS 提供以下几种方式发送通知给任务：

- 发送通知给任务，如果有通知未读，不覆盖通知值。
- 发送通知给任务，直接覆盖通知值。
- 发送通知给任务，设置通知值的一个或者多个位，可以当做事件组来使用。
- 发送通知给任务，递增通知值，可以当做计数信号量使用。

**通过对以上任务通知方式的合理使用，可以在一定场合下替代FreeRTOS的信号量，队列、事件组等**。

当然，凡是都有利弊，不然的话FreeRTOS还要内核的IPC通信机制干嘛，消息通知虽然处理更快，RAM开销更小，但也有以下限制：

- 只能有一个任务接收通知消息，因为必须指定接收通知的任务。
- 只有等待通知的任务可以被阻塞，发送通知的任务，在任何情况下都不会因为发送失败而进入阻塞态。

#### 任务通知的运作机制

顾名思义，任务通知是属于任务中附带的资源，所以在任务被创建的时候，任务通知也被初始化的，而在分析队列和信号量的章节中，我们知道在使用队列、信号量前，必须先创建队列和信号量，目的是为了创建队列数据结构。比如使用xQueueCreate()函数创建队列，用xSemaphoreCreateBinary() 函数创建二值信号量等等。再来看任务通知，**由于任务通知的数据结构包含在任务控制块中，只要任务存在，任务通知数据结构就已经创建完毕，可以直接使用**，所以使用的时候很是方便。

**任务通知可以在任务中向指定任务发送通知，也可以在中断中向指定任务发送通知，FreeRTOS的每个任务都有一个32位的通知值，任务控制块中的成员变量ulNotifiedValue就是这个通知值**。只有在任务中可以等待通知，而不允许在中断中等待通知。如果任务在等待的通知暂时无效，任务会根据用户指定的阻塞超时时间进入阻塞状态，我们可以将等待通知的任务看作是消费者；其他任务和中断可以向等待通知的任务发送通知，发送通知的任务和中断服务函数可以看作是生产者，当其他任务或者中断向这个任务发送任务通知，任务获得通知以后，该任务就会从阻塞态中解除，这与FreeRTOS中内核的其他通信机制一致。

#### 任务通知的数据结构

从前文我们知道，任务通知是任务控制块的资源，那它也算任务控制块中的成员变量，包含在任务控制块中。

#### 任务通知的函数接口讲解

##### 发送任务通知函数xTaskGenericNotify

我们先看一下发送通知API函数。这类函数比较多，有6个。但仔细分析会发现它们只能完成3种操作，每种操作有两个API函数，分别为带中断保护版本和不带中断保护版本。FreeRTOS将API细分为带中断保护版本和不带中断保护版本是为了节省中断服务程序处理时间，提升性能。通过前面通信机制的学习，相信大家都了 解了FreeRTOS的风格，这里的任务通知发送函数也是利用宏定义来进行扩展的，所有的函数都是一个宏定义，在任务中发送任务通知的函数均是调用xTaskGenericNotify()函数进行发送通知。

* xTaskNotifyGive

xTaskNotifyGive()是一个宏，宏展开是调用函数xTaskNotify( ( xTaskToNotify ), ( 0 ), eIncrement )，即向一个任务发送通知，并将对方的任务通知值加1。该函数可以作为二值信号量和计数信号量的一种轻量型的实现，速度更快，在这种情况下对象任务在等待任务通知的时候应该是使用函数 [ulTaskNotifyTake()](http://www.freertos.org/ulTaskNotifyTake.html) 而不是[xTaskNotifyWait()](http://www.freertos.org/xTaskNotifyWait.html) 。xTaskNotifyGive()不能在中断里面使用，而是使用具有中断保护功能的[vTaskNotifyGiveFromISR()](http://www.freertos.org/vTaskNotifyGiveFromISR.html)来代替。

* vTaskNotifyGiveFromISR

vTaskNotifyGiveFromISR()是vTaskNotifyGive()的中断保护版本。用于在中断中向指定任务发送任务通知，并更新对方的任务通知值（加1操作），在某些场景中可以替代信号量操作，因为这两个通知都是不带有通知值的。

* xTaskNotify

FreeRTOS每个任务都有一个32位的变量用于实现任务通知，在任务创建的时候初始化为0。这个32位的通知值在任务控制块TCB里面定义，具体见代码清单20‑6。xTaskNotify()用于在任务中直接向另外一个任务发送一个事件，接收到该任务通知的任务有可能解锁。如果你想使用任务通知来实现二值信号量 和计数信号量，那么应该使用更加简单的函数[xTaskNotifyGive()](http://www.freertos.org/xTaskNotifyGive.html) ，而不是使用xTaskNotify()，xTaskNotify()函数在发送任务通知的时候会指定一个通知值，并且用户可以指定通知值发送的方式。

注意：该函数不能在中断里面使用，而是使用具体中断保护功能的版本函数[xTaskNotifyFromISR()](http://www.freertos.org/xTaskNotifyFromISR.html)。

* xTaskNotifyFromISR

xTaskNotifyFromISR()是xTaskNotify()的中断保护版本，真正起作用的函数是中断发送任务通知通用函数xTaskGenericNotifyFromISR()，而xTaskNotifyFromISR()是一个宏定义，具体见代码清单20‑8，用于在中断中向指定的任务发送一个任务通 知，该任务通知是带有通知值并且用户可以指定通知的发送方式，不返回上一个任务在的通知值。

* 中断中发送任务通知通用函数xTaskGenericNotifyFromISR

xTaskGenericNotifyFromISR()是一个在中断中发送任务通知的通用函数，xTaskNotifyFromISR()、xTaskNotifyAndQueryFromISR()等函数都是以其为基础，采用宏定义的方式实现。

* xTaskNotifyAndQuery

xTaskNotifyAndQuery()与xTaskNotify()很像，都是调用通用的任务通知发送函数xTaskGenericNotify()来实现通知的发送，不同的是多了一个附加的参数pulPreviousNotifyValue用于回传接收任务的上一个通知值，函数原型具体见代码清单20‑11。 xTaskNotifyAndQuery()函数不能用在中断中，而是必须使用带中断保护功能的xTaskNotifyAndQuery()FromISR来代替。

* xTaskNotifyAndQueryFromISR

xTaskNotifyAndQueryFromISR()是xTaskNotifyAndQuery ()的中断版本，用于向指定的任务发送一个任务通知，并返回对象任务的上一个通知值，该函数也是一个宏定义，真正实现发送通知的是xTaskGenericNotifyFromISR()。

##### 获取任务通知函数

既然FreeRTOS中发送任务的函数有那么多个，那么任务怎么获取到通知呢？我们说了，任务通知在某些场景可以替代信号量、消息队列、事件等。**获取任务通知函数只能用在任务中，没有带中断保护版本**，因此只有两个API函数：ulTaskNotifyTake()和xTaskNotifyWait ()。前者是为代替二值信号量和计数信号量而专门设计的，它和发送通知API函数xTaskNotifyGive()、vTaskNotifyGiveFromISR()配合使用；后者是全功能版的等待通知，可以根据不同的参数实现轻量级二值信号量、计数信号量、事件组和长度为1的队列。

所有的获取任务通知API函数都带有指定阻塞超时时间参数，当任务因为等待通知而进入阻塞时，用来指定任务的阻塞时间，这些超时机制与FreeRTOS的消息队列、信号量、事件等的超时机制一致。

* ulTaskNotifyTake

ulTaskNotifyTake()作为二值信号量和计数信号量的一种轻量级实现，速度更快。**如果FreeRTOS中使用函数xSemaphoreTake() 来获取信号量，这个时候则可以试试使用函数ulTaskNotifyTake()来代替**。

对于这个函数，任务通知值为0，对应信号量无效，如果任务设置了阻塞等待，任务被阻塞挂起。当其他任务或中断发送了通知值使其不为0后，通知变为有效，等待通知的任务将获取到通知，并且在退出时候根据用户传递的第一个参数xClearCountOnExit选择清零通知值或者执行减一操作。

xTaskNotifyTake()在退出的时候处理任务的通知值的时候有两种方法，一种是在函数退出时将通知值清零，这种方法适用于实现二值信号量；另外一种是在函数退出时将通知值减1，这种方法适用于实现计数信号量。

当一个任务使用其自身的任务通知值作为二值信号量或者计数信号量时，其他任务应该使用函数xTaskNotifyGive()或者xTaskNotify( ( xTaskToNotify ), ( 0 ), eIncrement )来向其发送信号量。如果是在中断中，则应该使用他们的中断版本函数。

与获取二值信号量和获取计数信号量的函数相比，ulTaskNotifyTake()函数**少了很多调用子函数开销、少了很多判断、少了事件列表处理、少了队列上锁与解锁处理等等**，因此ulTaskNotifyTake()函数相对效率很高。

* xTaskNotifyWait

xTaskNotifyWait()函数用于实现全功能版的等待任务通知，根据用户指定的参数的不同，可以灵活的用于实现轻量级的消息队列队列、二值信号量、计数信号量和事件组功能，并带有超时等待。

纵观整个任务通知的实现，我们不难发现它比消息队列、信号量、事件的实现方式要简单很多。它可以实现轻量级的消息队列、二值信号量、计数信号量和事件组，并且使用更方便、更节省RAM、更高效。

至此，任务通知的函数基本讲解完成，但是我们有必要说明一下，任务通知并不能完全代替队列、二值信号量、计数信号量和事件组，使用的时候需要用户按需处理，此外，再提一次任务通知的局限性：

- 只能有一个任务接收通知事件。
- 接收通知的任务可以因为等待通知而进入阻塞状态，但是发送通知的任务即便不能立即完成发送通知，也不能进入阻塞状态。

#### 任务通知实验

##### 任务通知代替消息队列

任务通知代替消息队列是在FreeRTOS中创建了三个任务，其中两个任务是用于接收任务通知，另一个任务发送任务通知。三个任务独立运行，发送消息任务是通过检测按键的按下情况来发送消息通知，另两个任务获取消息通知，在任务通知中没有可用的通知之前就一直等待消息，一旦获取到消息通知就把消息打印在串口调试助手里 。

* 定义接收任务通知任务：

```c
static void Receive1_Task(void* parameter)
{	
  BaseType_t xReturn = pdTRUE;/* 定义一个创建信息返回值，默认为pdPASS */
#if USE_CHAR
  char *r_char;
#else
  uint32_t r_num;
#endif
  while (1)
  {
    /* BaseType_t xTaskNotifyWait(uint32_t ulBitsToClearOnEntry, 
                                  uint32_t ulBitsToClearOnExit, 
                                  uint32_t *pulNotificationValue, 
                                  TickType_t xTicksToWait ); 
     * ulBitsToClearOnEntry：当没有接收到任务通知的时候将任务通知值与此参数的取
       反值进行按位与运算，当此参数为Oxfffff或者ULONG_MAX的时候就会将任务通知值清零。
     * ulBits ToClearOnExit：如果接收到了任务通知，在做完相应的处理退出函数之前将
       任务通知值与此参数的取反值进行按位与运算，当此参数为0xfffff或者ULONG MAX的时候
       就会将任务通知值清零。
     * pulNotification Value：此参数用来保存任务通知值。
     * xTick ToWait：阻塞时间。
     *
     * 返回值：pdTRUE：获取到了任务通知。pdFALSE：任务通知获取失败。
     */
    //获取任务通知 ,没获取到则一直等待
		xReturn=xTaskNotifyWait(0x0,			//进入函数的时候不清除任务bit
                            ULONG_MAX,	  //退出函数的时候清除所有的bit
#if USE_CHAR
                            (uint32_t *)&r_char,		  //保存任务通知值
#else
                            &r_num,		  //保存任务通知值
#endif                        
                            portMAX_DELAY);	//阻塞时间
    if( pdTRUE == xReturn )
#if USE_CHAR
      printf("Receive1_Task 任务通知消息为 %s \n",r_char);                      
#else
      printf("Receive1_Task 任务通知消息为 %d \n",r_num);                      
#endif  
     
    
		LED1_TOGGLE;
  }
}
```

* 定义发送任务通知任务：

```c
static void Send_Task(void* parameter)
{	 
  BaseType_t xReturn = pdPASS;/* 定义一个创建信息返回值，默认为pdPASS */
#if USE_CHAR
  char test_str1[] = "this is a mail test 1";/* 邮箱消息test1 */
  char test_str2[] = "this is a mail test 2";/* 邮箱消息test2 */
#else
  uint32_t send1 = 1;
  uint32_t send2 = 2;
#endif
  

  
  while (1)
  {
    /* KEY1 被按下 */
    if( Key_Scan(KEY1_GPIO_PORT,KEY1_GPIO_PIN) == KEY_ON )
    {
      /* 原型:BaseType_t xTaskNotify( TaskHandle_t xTaskToNotify, 
                                      uint32_t ulValue, 
                                      eNotifyAction eAction ); 
       * eNoAction = 0，通知任务而不更新其通知值。
       * eSetBits，     设置任务通知值中的位。
       * eIncrement，   增加任务的通知值。
       * eSetvaluewithoverwrite，覆盖当前通知
       * eSetValueWithoutoverwrite 不覆盖当前通知
       * 
       * pdFAIL：当参数eAction设置为eSetValueWithoutOverwrite的时候，
       * 如果任务通知值没有更新成功就返回pdFAIL。
       * pdPASS: eAction 设置为其他选项的时候统一返回pdPASS。
      */
      xReturn = xTaskNotify( Receive1_Task_Handle, /*任务句柄*/
#if USE_CHAR 
                             (uint32_t)&test_str1, /* 发送的数据，最大为4字节 */
#else
                              send1, /* 发送的数据，最大为4字节 */
#endif
                             eSetValueWithOverwrite );/*覆盖当前通知*/
      
      if( xReturn == pdPASS )
        printf("Receive1_Task_Handle 任务通知消息发送成功!\r\n");
    } 
    /* KEY2 被按下 */
    if( Key_Scan(KEY2_GPIO_PORT,KEY2_GPIO_PIN) == KEY_ON )
    {
      xReturn = xTaskNotify( Receive2_Task_Handle, /*任务句柄*/
#if USE_CHAR 
                             (uint32_t)&test_str2, /* 发送的数据，最大为4字节 */
#else
                              send2, /* 发送的数据，最大为4字节 */
#endif
                             eSetValueWithOverwrite );/*覆盖当前通知*/
      /* 此函数只会返回pdPASS */
      if( xReturn == pdPASS )
        printf("Receive2_Task_Handle 任务通知消息发送成功!\r\n");
    }
    vTaskDelay(20);
  }
}
```

##### 任务通知代替二值信号量

任务通知代替消息队列是在FreeRTOS中创建了三个任务，其中两个任务是用于接收任务通知，另一个任务发送任务通知。三个任务独立运行，发送通知任务是通过检测按键的按下情况来发送通知，另两个任务获取通知，在任务通知中没有可用的通知之前就一直等待任务通知，获取到通知以后就将通知值清0，这样子是为了代替二值 信号量，任务同步成功则继续执行，然后在串口调试助手里将运行信息打印出来。

* 定义接收任务通知任务：

```c
static void Receive1_Task(void* parameter)
{	
  while (1)
  {
    /* uint32_t ulTaskNotifyTake( BaseType_t xClearCountOnExit, TickType_t xTicksToWait ); 
     * xClearCountOnExit：pdTRUE 在退出函数的时候任务任务通知值清零，类似二值信号量
     * pdFALSE 在退出函数ulTaskNotifyTakeO的时候任务通知值减一，类似计数型信号量。
     */
    //获取任务通知 ,没获取到则一直等待
    ulTaskNotifyTake(pdTRUE,portMAX_DELAY);
    
    printf("Receive1_Task 任务通知获取成功!\n\n");
    
		LED1_TOGGLE;
  }
}
```

* 定义发送任务通知任务：

```c
static void Send_Task(void* parameter)
{	 
  BaseType_t xReturn = pdPASS;/* 定义一个创建信息返回值，默认为pdPASS */
  while (1)
  {
    /* KEY1 被按下 */
    if( Key_Scan(KEY1_GPIO_PORT,KEY1_GPIO_PIN) == KEY_ON )
    {
      /* 原型:BaseType_t xTaskNotifyGive( TaskHandle_t xTaskToNotify ); */
      xReturn = xTaskNotifyGive(Receive1_Task_Handle);
      /* 此函数只会返回pdPASS */
      if( xReturn == pdTRUE )
        printf("Receive1_Task_Handle 任务通知发送成功!\r\n");
    } 
    /* KEY2 被按下 */
    if( Key_Scan(KEY2_GPIO_PORT,KEY2_GPIO_PIN) == KEY_ON )
    {
      xReturn = xTaskNotifyGive(Receive2_Task_Handle);
      /* 此函数只会返回pdPASS */
      if( xReturn == pdPASS )
        printf("Receive2_Task_Handle 任务通知发送成功!\r\n");
    }
    vTaskDelay(20);
  }
}
```

##### 任务通知代替计数信号量

任务通知代替计数信号量是基于计数型信号量实验修改而来，模拟停车场工作运行。并且在FreeRTOS中创建了两个任务：一个是获取任务通知，一个是发送任务通知，两个任务独立运行，获取通知的任务是通过按下KEY1按键获取，模拟停车场停车操作，其等待时间是0；发送通知的任务则是通过检测KEY2按键按下进行通知 的发送，模拟停车场取车操作，并且在串口调试助手输出相应信息。

* 定义获取任务通知任务：

```c
static void Take_Task(void* parameter)
{	
  uint32_t take_num = pdTRUE;/* 定义一个创建信息返回值，默认为pdPASS */
  /* 任务都是一个无限循环，不能返回 */
  while (1)
  {
    //如果KEY1被单击
		if( Key_Scan(KEY1_GPIO_PORT,KEY1_GPIO_PIN) == KEY_ON )       
		{
      /* uint32_t ulTaskNotifyTake( BaseType_t xClearCountOnExit, TickType_t xTicksToWait ); 
       * xClearCountOnExit：pdTRUE 在退出函数的时候任务任务通知值清零，类似二值信号量
       * pdFALSE 在退出函数ulTaskNotifyTakeO的时候任务通知值减一，类似计数型信号量。
       */
      //获取任务通知 ,没获取到则不等待
      take_num=ulTaskNotifyTake(pdFALSE,0);//
      if(take_num > 0)
        printf( "KEY1被按下，成功申请到停车位，当前车位为 %d \n", take_num - 1);
			else
        printf( "KEY1被按下，车位已经没有了，请按KEY2释放车位\n" );  
		}
		vTaskDelay(20);     //每20ms扫描一次		
  }
}
```

* 定义发送任务通知任务：

```c
static void Give_Task(void* parameter)
{	 
  BaseType_t xReturn = pdPASS;/* 定义一个创建信息返回值，默认为pdPASS */
  /* 任务都是一个无限循环，不能返回 */
  while (1)
  {
    //如果KEY2被单击
		if( Key_Scan(KEY2_GPIO_PORT,KEY2_GPIO_PIN) == KEY_ON )       
		{
      /* 原型:BaseType_t xTaskNotifyGive( TaskHandle_t xTaskToNotify ); */
			/* 释放一个任务通知 */
      xTaskNotifyGive(Take_Task_Handle);//发送任务通知
      /* 此函数只会返回pdPASS */
			if ( pdPASS == xReturn ) 
				printf( "KEY2被按下，释放1个停车位。\n" );
		}
		vTaskDelay(20);     //每20ms扫描一次	
  }
}
```

##### 任务通知代替事件组

任务通知代替事件组实验是在事件标志组实验基础上进行修改，实验任务通知替代事件实现事件类型的通信，该实验是在FreeRTOS中创建了两个任务，一个是发送事件通知任务，一个是等待事件通知任务，两个任务独立运行，发送事件通知任务通过检测按键的按下情况设置不同的通知值位，等待事件通知任务则获取这任务通知值， 并且根据通知值判断两个事件是否都发生，如果是则输出相应信息，LED进行翻转。等待事件通知任务的等待时间是portMAX_DELAY，一直在等待事件通知的发生，等待获取到事件之后清除对应的任务通知值的位。

* 定义发送事件通知任务：

```c
static void KEY_Task(void* parameter)
{	 
    /* 任务都是一个无限循环，不能返回 */
  while (1)
  {
    if( Key_Scan(KEY1_GPIO_PORT,KEY1_GPIO_PIN) == KEY_ON )       
		{
      printf ( "KEY1被按下\n" );
      /* 原型:BaseType_t xTaskNotify( TaskHandle_t xTaskToNotify, 
                                      uint32_t ulValue, 
                                      eNotifyAction eAction ); 
       * eNoAction = 0，通知任务而不更新其通知值。
       * eSetBits，     设置任务通知值中的位。
       * eIncrement，   增加任务的通知值。
       * eSetvaluewithoverwrite，覆盖当前通知
       * eSetValueWithoutoverwrite 不覆盖当前通知
       * 
       * pdFAIL：当参数eAction设置为eSetValueWithoutOverwrite的时候，
       * 如果任务通知值没有更新成功就返回pdFAIL。
       * pdPASS: eAction 设置为其他选项的时候统一返回pdPASS。
      */
			/* 触发一个事件1 */
			xTaskNotify((TaskHandle_t	)LED_Task_Handle,//接收任务通知的任务句柄
                  (uint32_t		)KEY1_EVENT,			//要触发的事件
                  (eNotifyAction)eSetBits);			//设置任务通知值中的位
									
		}
    
		if( Key_Scan(KEY2_GPIO_PORT,KEY2_GPIO_PIN) == KEY_ON )       
		{
      printf ( "KEY2被按下\n" );	
			/* 触发一个事件2 */
			xTaskNotify((TaskHandle_t	)LED_Task_Handle,//接收任务通知的任务句柄
                  (uint32_t		)KEY2_EVENT,			//要触发的事件
                  (eNotifyAction)eSetBits);			//设置任务通知值中的位				
		}
		vTaskDelay(20);     //每20ms扫描一次		
  }
}
```

* 定义等待事件通知任务：

```c
static void LED_Task(void* parameter)
{	
  uint32_t r_event = 0;  /* 定义一个事件接收变量 */
  uint32_t last_event = 0;/* 定义一个保存事件的变量 */
  BaseType_t xReturn = pdTRUE;/* 定义一个创建信息返回值，默认为pdPASS */
  /* 任务都是一个无限循环，不能返回 */
  while (1)
	{
    /* BaseType_t xTaskNotifyWait(uint32_t ulBitsToClearOnEntry, 
                                  uint32_t ulBitsToClearOnExit, 
                                  uint32_t *pulNotificationValue, 
                                  TickType_t xTicksToWait ); 
     * ulBitsToClearOnEntry：当没有接收到任务通知的时候将任务通知值与此参数的取
       反值进行按位与运算，当此参数为Oxfffff或者ULONG_MAX的时候就会将任务通知值清零。
     * ulBits ToClearOnExit：如果接收到了任务通知，在做完相应的处理退出函数之前将
       任务通知值与此参数的取反值进行按位与运算，当此参数为0xfffff或者ULONG MAX的时候
       就会将任务通知值清零。
     * pulNotification Value：此参数用来保存任务通知值。
     * xTick ToWait：阻塞时间。
     *
     * 返回值：pdTRUE：获取到了任务通知。pdFALSE：任务通知获取失败。
     */
    //获取任务通知 ,没获取到则一直等待
		xReturn = xTaskNotifyWait(0x0,			//进入函数的时候不清除任务bit
                              ULONG_MAX,	  //退出函数的时候清除所有的bitR
                              &r_event,		  //保存任务通知值                    
                              portMAX_DELAY);	//阻塞时间
    if( pdTRUE == xReturn )
    { 
      last_event |= r_event;
      /* 如果接收完成并且正确 */      
      if(last_event == (KEY1_EVENT|KEY2_EVENT)) 
      {
        last_event = 0;     /* 上一次的事件清零 */
        printf ( "Key1与Key2都按下\n");		
        LED1_TOGGLE;       //LED1	反转 
      }
      else  /* 否则就更新事件 */
        last_event = r_event;   /* 更新上一次触发的事件 */
    }
    
  }
}
```

### 内存管理

#### 内存管理的基本概念

在计算系统中，变量、中间数据一般存放在系统存储空间中，只有在实际使用时才将它们从存储空间调入到中央处理器内部进行运算。通常存储空间可以分为两种：内部存储空间和外部存储空间。内部存储空间访问速度比较快，能够按照变量地址随机地访问，也就是我们通常所说的RAM（随机存储器），或电脑的内存；而外部存储空间内 所保存的内容相对来说比较固定，即使掉电后数据也不会丢失，可以把它理解为电脑的硬盘。在这一章中我们主要讨论**内部存储空间（RAM）的管理**——内存管理。

FreeRTOS操作系统将内核与内存管理分开实现，操作系统内核仅规定了必要的内存管理函数原型，而不关心这些内存管理函数是如何实现的，所以在FreeRTOS中提供了多种内存分配算法（分配策略），但是上层接口（API）却是统一的。这样做可以增加系统的灵活性：用户可以选择对自己更有利的内存管理策略，在不同 的应用场合使用不同的内存分配策略。

在嵌入式程序设计中内存分配应该是根据所设计系统的特点来决定选择使用动态内存分配还是静态内存分配算法，一些可靠性要求非常高的系统应选择使用静态的，而普通的业务系统可以使用动态来提高内存使用效率。静态可以保证设备的可靠性但是需要考虑内存上限，内存使用效率低，而动态则是相反。

FreeRTOS内存管理模块管理用于系统中内存资源，它是操作系统的核心模块之一。主要包括内存的初始化、分配以及释放。

很多人会有疑问，什么不直接使用C标准库中的内存管理函数呢？在电脑中我们可以用 malloc()和 free()这两个函数动态的分配内存和释放内存。但是，**在嵌入式实时操作系统中，调用malloc()和free()却是危险的**，原因有以下几点：

- 这些函数在小型嵌入式系统中并不总是可用的，小型嵌入式设备中的RAM不足。
- 它们的实现可能非常的大，占据了相当大的一块代码空间。
- 他们几乎都不是安全的。
- 它们并不是确定的，每次调用这些函数执行的时间可能都不一样。
- 它们有可能产生碎片。
- 这两个函数会使得链接器配置得复杂。
- 如果允许堆空间的生长方向覆盖其他变量占据的内存，它们会成为debug的灾难。

在一般的实时嵌入式系统中，由于实时性的要求，很少使用虚拟内存机制。所有的内存都需要用户参与分配，直接操作物理内存，所分配的内存不能超过系统的物理内存，所有的系统栈的管理，都由用户自己管理。

同时，在嵌入式实时操作系统中，对内存的分配时间要求更为苛刻，分配内存的时间必须是确定的。一般内存管理算法是根据需要存储的数据的长度在内存中去寻找一个与这段数据相适应的空闲内存块，然后将数据存储在里面。而寻找这样一个空闲内存块所耗费的时间是不确定的，因此对于实时系统来说，这就是不可接受的，**实时系统必须要保证内存块的分配过程在可预测的确定时间内完成，否则实时任务对外部事件的响应也将变得不可确定**。

而在嵌入式系统中，内存是十分有限而且是十分珍贵的，用一块内存就少了一块内存，而在分配中随着内存不断被分配和释放，整个系统内存区域会产生越来越多的碎片，因为在使用过程中，申请了一些内存，其中一些释放了，导致内存空间中存在一些小的内存块，它们地址不连续，不能够作为一整块的大内存分配出去，所以一定会在某个时间，系统已经无法分配到合适的内存了，导致系统瘫痪。其实系统中实际是还有内存的，但是因为小块的内存的地址不连续，导致无法分配成功，所以我们需要一个优良的**内存分配算法**来避免这种情况的出现。

不同的嵌入式系统具有不同的内存配置和时间要求。所以单一的内存分配算法只可能适合部分应用程序。因此，FreeRTOS将内存分配作为可移植层面（相对于基本的内核代码部分而言），FreeRTOS有针对性的提供了不同的内存分配管理算法，这使得应用于不同场景的设备可以选择适合自身内存算法。

FreeRTOS对内存管理做了很多事情，FreeRTOS的V9.0.0版本为我们提供了5种内存管理算法，分别是heap_1.c、heap_2.c、heap_3.c、heap_4.c、heap_5.c，源文件存放于FreeRTOSSourceportableMemMang路径下，在使用的时候选择 其中一个添加到我们的工程中去即可。

FreeRTOS的内存管理模块通过对内存的申请、释放操作，来管理用户和系统对内存的使用，使内存的利用率和使用效率达到最优，同时最大限度地解决系统可能产生的内存碎片问题。

#### 内存管理的应用场景

首先，在使用内存分配前，必须明白自己在做什么，这样做与其他的方法有什么不同，特别是会产生哪些负面影响，在自己的产品面前，应当选择哪种分配策略。

内存管理的主要工作是动态划分并管理用户分配好的内存区间，主要是在用户需要使用大小不等的内存块的场景中使用，当用户需要分配内存时，可以通过操作系统的内存申请函数索取指定大小内存块，一旦使用完毕，通过动态内存释放函数归还所占用内存，使之可以重复使用（heap_1.c的内存管理除外）。

例如我们需要定义一个float型数组：floatArr[];

但是，在使用数组的时候，总有一个问题困扰着我们：数组应该有多大？在很多的情况下，你并不能确定要使用多大的数组，可能为了避免发生错误你就需要把数组定义得足够大。即使你知道想利用的空间大小，但是如果因为某种特殊原因空间利用的大小有增加或者减少，你又必须重新去修改程序，扩大数组的存储范围。这种分配固定大小的内存分配方法称之为**静态内存分配**。这种内存分配的方法存在比较严重的缺陷，在大多数情况下会浪费大量的内存空间，在少数情况下，当你定义的数组不够大时，可能引起下标越界错误，甚至导致严重后果。

我们用动态内存分配就可以解决上面的问题。**所谓动态内存分配就是指在程序执行的过程中动态地分配或者回收存储空间的分配内存的方法。动态内存分配不象数组等静态内存分配方法那样需要预先分配存储空间，而是由系统根据程序的需要即时分配，且分配的大小就是程序要求的大小**。

#### 内存管理方案详解

FreeRTOS规定了内存管理的函数接口，具体见，但是不管其内部的内存管理方案是怎么实现的，所以，FreeRTOS可以提供多个内存管理方案，下面，就一起看看各个内存管理方案的区别。

* void *pvPortMalloc( size_t xSize ); //内存申请函数

* void vPortFree( void *pv ); //内存释放函数

* void vPortInitialiseBlocks( void ); //初始化内存堆函数

* size_t xPortGetFreeHeapSize( void ); //获取当前未分配的内存堆大小

* size_t xPortGetMinimumEverFreeHeapSize( void ); //获取未分配的内存堆历史最小值

FreeRTOS提供的内存管理都是从内存堆中分配内存的。从前面学习的过程中，我们也知道，创建任务、消息队列、事件等操作都使用到分配内存的函数，这是系统中默认使用内存管理函数从内存堆中分配内存给系统核心组件使用。

对于heap_1.c、heap_2.c和heap_4.c这三种内存管理方案，内存堆实际上是一个很大的数组，定义为static uint8_t ucHeap[ configTOTAL_HEAP_SIZE]，而宏定义configTOTAL_HEAP_SIZE则表示系统管理内存大小，单位为字，在FreeRTOSConfig.h中由用户设定。

对于heap_3.c这种内存管理方案，它封装了C标准库中的malloc()和free()函数，封装后的malloc()和free()函数具备保护，可以安全在嵌入式系统中执行。因此，用户需要通过编译器或者启动文件设置堆空间。

heap_5.c方案允许用户使用多个非连续内存堆空间，每个内存堆的起始地址和大小由用户定义。这种应用其实还是很大的，比如做图形显示、GUI等，可能芯片内部的RAM是不够用户使用的，需要外部SDRAM，那这种内存管理方案则比较合适。

##### heap_1.c

heap_1.c管理方案是FreeRTOS提供所有内存管理方案中最简单的一个，**它只能申请内存而不能进行内存释放，并且申请内存的时间是一个常量**，这样子对于要求安全的嵌入式设备来说是最好的，因为不允许内存释放，就不会产生内存碎片而导致系统崩溃，但是也有缺点，那就是内存利用率不高，某段内存只能用于内存申请 的地方，即使该内存只使用一次，也无法让系统回收重新利用。

实际上，大多数的嵌入式系统并不会经常动态申请与释放内存，一般都是在系统完成的时候，就一直使用下去，永不删除，所以这个内存管理方案实现简洁、安全可靠，使用的非常广泛。

heap1.c方案具有以下特点：

1. 用于从不删除任务、队列、信号量、互斥量等的应用程序（实际上大多数使用FreeRTOS的应用程序都符合这个条件）。
2. 函数的执行时间是确定的并且不会产生内存碎片。

* 内存申请函数pvPortMalloc

内存申请函数就是用于申请一块用户指定大小的内存空间，当系统管理的内存空间满足用户需要的大小的时候，就能申请成功，并且返回内存空间的起始地址。

其实heap_1.c方案还有一些其他函数，只不过基本没啥用，就简单说说，vPortFree()这个函数其实上面都没做，因为heap_1.c采用的内存管理算法中不支持释放内存。vPortInitialiseBlocks()仅仅将静态局部变量xNextFreeByte设置为0，表示内存没有被申请。xPo rtGetFreeHeapSize()则是获取当前未分配的内存堆大小，这个函数通常用于检查我们设置的内存堆是否合理，通过这个函数可以估计出最坏情况下需要多大的内存堆，以便合理的节省内存资源。

##### heap_2.c

heap_2.c方案与heap_1.c方案采用的内存管理算法不一样，它采用一种**最佳匹配算法**(best fit algorithm)，比如我们申请100字节的内存，而可申请内存中有三块对应大小200字节， 500字节和 1000字节大小的内存块，按照算法的最佳匹配，这时候系统会把200字节大小的内存块进行分割并返回申请内存的起始地址，剩余的内存则插回链表留待下次申请。Heap_2.c方案**支持释放申请的内存，但是它不能把相邻的两个小的内存块合成一个大的内存块**，对于每次申请内存大小都比较固定的，这个方式是没有问题的，**而对于每次申请并不是固定内存大小的则会造成内存碎片**，后面要讲解的heap_4.c方案采用的内存管理算法能解决内存碎片的问题，可以把这些释放的相邻的小的内存块合并成一个大的内存块。

同样的，内存分配时需要的总的内存堆空间由文件FreeRTOSConfig.h中的宏configTOTAL_HEAP_SIZE配置，单位为字。通过调用函数xPortGetFreeHeapSize() 我们可以知道还剩下多少内存没有使用，但是并不包括内存碎片，这样一来我们可以实时的调整和优化config TOTAL_HEAP_SIZE的大小。

heap_2.c方案具有以下特点：

1. 可以用在那些反复的删除任务、队列、信号量、等内核对象且不担心内存碎片的应用程序。
2. 如果我们的应用程序中的队列、任务、信号量、等工作在一个不可预料的顺序，这样子也有可能会导致内存碎片。
3. 具有不确定性，但是效率比标准C库中的malloc函数高得多
4. 不能用于那些内存分配和释放是随机大小的应用程序。

heap_2.c方案与 heap_1方案在内存堆初始化的时候操作都是一样的，在内存中开辟了一个静态数组作为堆的空间，大小由用户定义，然后进行字节对齐处理。

heap_2.c方案采用链表的数据结构记录空闲内存块，将所有的空闲内存块组成一个空闲内存块链表。

* 内存申请函数pvPortMalloc

heap_2.c内存管理方案采用最佳匹配算法管理内存，系统会先从内存块空闲链表头开始进行遍历，查找符合用户申请大小的内存块（**内存块空闲链表按内存块大小升序排列，所以最先返回的的块一定是最符合申请内存大小，所谓的最匹配算法就是这个意思来的**）。当找到内存块的时候，返回该内存块偏移heapSTRUCT_S IZE 个字节后的地址，因为在每块内存块前面预留的节点是用于记录内存块的信息，用户不需要也不允许操作这部分内存。

在申请内存成功的同时系统还会判断当前这块内存是否有剩余（大于一个链表节点所需内存空间），这样子就表示剩下的内存块还是能存放东西的，也要将其利用起来。如果有剩余的内存空间，系统会将内存块进行分割，在剩余的内存块头部添加一个内存节点，并且完善该空闲内存块的信息，然后将其按内存块大小插入内存块空闲链表中， 供下次分配使用，其中 prvInsertBlockIntoFreeList() 这个函数就是把节点按大小插入到链表中。

* 内存释放函数vPortFree

分配内存的过程简单，那么释放内存的过程更简单，只需要向内存释放函数中传入要释放的内存地址，那么系统会自动向前索引到对应链表节点，并且取出这块内存块的信息，将这个节点插入到空闲内存块链表中，将这个内存块归还给系统。

从内存的申请与释放看来，heap_2.c方案采用的内存管理算法虽然是高效但还是有缺陷的，由于在释放内存时不会将相邻的内存块合并，所以这可能造成内存碎片，当然并不是说这种内存管理算法不好，只不过对使用的条件比较苛刻，要求用户每次创建或释放的任务、队列等必须大小相同如果分配或释放的内存是随机的，绝对不可 以用这种内存管理策略；如果申请和释放的顺序不可预料，那也很危险。举个例子，假设用户先申请128字节内存，然后释放，此时系统释放的128字节内存可以重复被利用；如果用户再接着申请64k的字节内存，那么一个本来128字节的大块就会被分为两个64字节的小块，如果这种情况经常发生，就会**导致每个空闲块都可能很小**，最终在申请一个大块时就会因为没有合适的空闲内存块而申请失败，这并不是因为总的空闲内存不足，而是无法申请到连续可以的大块内存。

##### heap_3.c

heap_3.c方案只是简单的封装了标准C库中的malloc()和free()函数，并且能满足常用的编译器。重新封装后的malloc()和free()函数具有保护功能，采用的封装方式是操作内存前挂起调度器、完成后再恢复调度器。

heap_3.c方案具有以下特点：

1. 需要链接器设置一个堆，malloc()和free()函数由编译器提供。
2. 具有不确定性。
3. 很可能增大RTOS内核的代码大小。

要注意的是在使用heap_3.c方案时，FreeRTOSConfig.h文件中的configTOTAL_HEAP_SIZE宏定义不起作用。在STM32系列的工程中，这个由编译器定义的堆都在启动文件里面设置，单位为字节。

##### heap_4.c

heap_4.c方案与heap_2.c方案一样都采用最佳匹配算法来实现动态的内存分配，但是不一样的是heap_4.c方案还包含了一种**合并算法**，能把相邻的空闲的内存块合并成一个更大的块，这样可以减少内存碎片。heap_4.c方案特别适用于移植层中可以直接使用pvPortMalloc()和 vPortFree()函数来分配和释放内存的代码。

内存分配时需要的总的堆空间由文件FreeRTOSConfig.h中的宏configTOTAL_HEAP_SIZE配置，单位为字。通过调用函数xPortGetFreeHeapSize() 我们可以知道还剩下多少内存没有使用，但是并不包括内存碎片。[这样一来我们可以实时的调整和优化configTOTAL_](https://doc.embedfire.com/rtos/freertos/zh/latest/application/memory_management.html#id19) HEAP_SIZE的大小。

heap_4.c方案的空闲内存块也是以单链表的形式连接起来的，BlockLink_t类型的局部静态变量xStart表示链表头，但heap_4.c内存管理方案的链表尾部则保存在内存堆空间最后位置，并使用BlockLink_t指针类型局部静态变量pxEnd指向这个区域（而heap_2.c内存管理方案则使 用BlockLink_t类型的静态变量xEnd表示链表尾）

heap_4.c内存管理方案的空闲块链表不是以内存块大小进行排序的，而是以**内存块起始地址大小排序，内存地址小的在前，地址大的在后**，因为heap_4.c方案还有一个内存合并算法，在释放内存的时候，假如相邻的两个空闲内存块在地址上是连续的，那么就可以合并为一个内存块，这也是为了适应合并算法而作的改变。

heap_4.c方案具有以下特点：

1、可用于重复删除任务、队列、信号量、互斥量等的应用程序

2、可用于分配和释放随机字节内存的应用程序，但并不像heap2.c那样产生严重的内存碎片。

3、具有不确定性，但是效率比标准C库中的malloc函数高得多。

* 内存申请函数pvPortMalloc

heap_4.c方案的内存申请函数与heap_2.c方案的内存申请函数大同小异，同样是从链表头xStart开始遍历查找合适的内存块，如果某个空闲内存块的大小能容得下用户要申请的内存，则将这块内存取出用户需要内存空间大小的部分返回给用户，剩下的内存块组成一个新的空闲块，按照空闲内存块起始地址大小顺序插 入到空闲块链表中，内存地址小的在前，内存地址大的在后。在插入到空闲内存块链表的过程中，系统还会执行合并算法将地址相邻的内存块进行合并：判断这个空闲内存块是相邻的空闲内存块合并成一个大内存块，如果可以则合并，合并算法是heap_4.c内存管理方案和heap_2.c内存管理方案最大的不同之处，这样一来， 会导致的内存碎片就会大大减少，内存管理方案适用性就很强，能一样随机申请和释放内存的应用中，灵活性得到大大的提高。

* 内存释放函数vPortFree

heap_4.c内存管理方案的内存释放函数vPortFree()也比较简单，根据传入要释放的内存块地址，偏移之后找到链表节点，然后将这个内存块插入到空闲内存块链表中，在内存块插入过程中会执行合并算法，这个我们已经在内存申请中讲过了（而且合并算法多用于释放内存中）。最后是将这个内存块标志为“空闲”（内 存块节点的xBlockSize成员变量最高位清0）、再更新未分配的内存堆大小即可。

##### heap_5.c

heap_5.c方案在实现动态内存分配时与heap4.c方案一样，采用最佳匹配算法和合并算法，并且**允许内存堆跨越多个非连续的内存区**，也就是允许在不连续的内存堆中实现内存分配，比如用户在片内RAM中定义一个内存堆，还可以在外部SDRAM再定义一个或多个内存堆，这些内存都归系统管理。

heap_5.c方案通过调用vPortDefineHeapRegions()函数来实现系统管理的内存初始化，在内存初始化未完成前不允许使用内存分配和释放函数。如创建FreeRTOS对象（任务、队列、信号量等）时会隐式的调用pvPortMalloc()函数，因此必须注意：使**用heap_5.c内存管理方案创建任何对象前，要先调用vPortDefineHeapRegions()函数将内存初始化**。

#### 内存管理的实验

内存管理实验使用heap_4.c方案进行内存管理测试，创建了两个任务，分别是LED任务与内存管理测试任务，内存管理测试任务通过检测按键是否按下来申请内存或释放内存，当申请内存成功就像该内存写入一些数据，如当前系统的时间等信息，并且通过串口输出相关信息；LED任务是将LED翻转，表示系统处于运行状态。 在不需要再使用内存时，注意要及时释放该段内存，避免内存泄露。

* 定义内存管理测试任务：

```C
static void Test_Task(void* parameter)
{	 
  uint32_t g_memsize;
  while (1)
  {
    if( Key_Scan(KEY1_GPIO_PORT,KEY1_GPIO_PIN) == KEY_ON )
    {
      /* KEY1 被按下 */
      if(NULL == Test_Ptr)
      {
                  
        /* 获取当前内存大小 */
        g_memsize = xPortGetFreeHeapSize();
        printf("系统当前内存大小为 %d 字节，开始申请内存\n",g_memsize);
        Test_Ptr = pvPortMalloc(1024);
        if(NULL != Test_Ptr)
        {
          printf("内存申请成功\n");
          printf("申请到的内存地址为%#x\n",(int)Test_Ptr);

          /* 获取当前内剩余存大小 */
          g_memsize = xPortGetFreeHeapSize();
          printf("系统当前内存剩余存大小为 %d 字节\n",g_memsize);
                  
          //向Test_Ptr中写入当数据:当前系统时间
          sprintf((char*)Test_Ptr,"当前系统TickCount = %d \n",xTaskGetTickCount());
          printf("写入的数据是 %s \n",(char*)Test_Ptr);
        }
      }
      else
      {
        printf("请先按下KEY2释放内存再申请\n");
      }
    } 
    if( Key_Scan(KEY2_GPIO_PORT,KEY2_GPIO_PIN) == KEY_ON )
    {
      /* KEY2 被按下 */
      if(NULL != Test_Ptr)
      {
        printf("释放内存\n");
        vPortFree(Test_Ptr);	//释放内存
        Test_Ptr=NULL;
        /* 获取当前内剩余存大小 */
        g_memsize = xPortGetFreeHeapSize();
        printf("系统当前内存大小为 %d 字节，内存释放完成\n",g_memsize);
      }
      else
      {
        printf("请先按下KEY1申请内存再释放\n");
      }
    }
    vTaskDelay(20);/* 延时20个tick */
  }
}
```

### 中断管理

#### 异常与中断的基本概念

异常是导致处理器脱离正常运行转向执行特殊代码的任何事件，如果不及时进行处理，轻则系统出错，重则会导致系统毁灭性瘫痪。所以正确地处理异常，避免错误的发生是提高软件鲁棒性（稳定性）非常重要的一环，对于实时系统更是如此。

异常是指任何打断处理器正常执行，并且迫使处理器进入一个由有特权的特殊指令执行的事件。异常通常可以分成两类：**同步异常**和**异步异常**。**由内部事件（像处理器指令运行产生的事件）引起的异常称为同步异常**，例如造成被零除的算术运算引发一个异常，又如在某些处理器体系结构中，对于确定的数据尺寸必须从内存的偶数地址进行读和写操作。从一个奇数内存地址的读或写操作将引起存储器存取一个错误事件并引起一个异常（称为校准异常）。

**异步异常主要是指由于外部异常源产生的异常**，是一个由外部硬件装置产生的事件引起的异步异常。同步异常不同于异步异常的地方是事件的来源，同步异常事件是由于执行某些指令而从处理器内部产生的，而异步异常事件的来源是外部硬件装置。例如按下设备某个按钮产生的事件。**同步异常与异步异常的区别还在于，同步异常触发后，系统必须立刻进行处理而不能够依然执行原有的程序指令步骤；而异步异常则可以延缓处理甚至是忽略，例如按键中断异常，虽然中断异常触发了，但是系统可以忽略它继续运行**（同样也忽略了相应的按键事件）。

中断，**中断属于异步异常**。所谓中断是指中央处理器CPU正在处理某件事的时候，外部发生了某一事件，请求CPU迅速处理，CPU暂时中断当前的工作，转入处理所发生的事件，处理完后，再回到原来被中断的地方，继续原来的工作，这样的过程称为中断。

中断能打断任务的运行，无论该任务具有什么样的优先级，因此中断一般用于处理比较紧急的事件，而且只做简单处理，例如标记该事件，在使用FreeRTOS系统时，一般建议使用信号量、消息或事件标志组等标志中断的发生，将这些内核对象发布给处理任务，处理任务再做具体处理。

通过中断机制，在外设不需要CPU介入时，CPU可以执行其他任务，而当外设需要CPU时通过产生中断信号使CPU立即停止当前任务转而来响应中断请求。这样可以使CPU避免把大量时间耗费在等待、查询外设状态的操作上，因此将大大提高系统实时性以及执行效率。

此处读者要知道一点，FreeRTOS源码中有许多处临界段的地方，临界段虽然保护了关键代码的执行不被打断，但也会影响系统的实时，任何使用了操作系统的中断响应都不会比裸机快。比如，某个时候有一个任务在运行中，并且该任务部分程序将中断屏蔽掉，也就是进入临界段中，这个时候如果有一个紧急的中断事件被触发，这个 中断就会被挂起，不能得到及时响应，必须等到中断开启才可以得到响应，如果屏蔽中断时间超过了紧急中断能够容忍的限度，危害是可想而知的。所以，**操作系统的中断在某些时候会有适当的中断延迟，因此调用中断屏蔽函数进入临界段的时候，也需快进快出**。当然FreeRTOS也能允许一些高优先级的中断不被屏蔽掉，能够及时做出响应，不过这些中断就不受系统管理，也不允许调用FreeRTOS中与中断相关的任何API函数接口。

FreeRTOS的中断管理支持：

- 开/关中断。
- 恢复中断。
- 中断使能。
- 中断屏蔽。
- 可选择系统管理的中断优先级。

##### 中断的介绍

与中断相关的硬件可以划分为三类：**外设**、**中断控制器**、**CPU**本身。

外设：当外设需要请求CPU时，产生一个中断信号，该信号连接至中断控制器。

中断控制器：中断控制器是CPU众多外设中的一个，它一方面接收其他外设中断信号的输入，另一方面，它会发出中断信号给CPU。可以通过对中断控制器编程实现对中断源的优先级、触发方式、打开和关闭源等设置操作。在Cortex-M系列控制器中常用的中断控制器是NVIC（内嵌向量中断控制器Nested Vectored Interrupt Controller）。

CPU：CPU会响应中断源的请求，中断当前正在执行的任务，转而执行中断处理程序。NVIC最多支持240个中断，每个中断最多256个优先级。

##### 和中断相关的名词解释

* 中断号：每个中断请求信号都会有特定的标志，使得计算机能够判断是哪个设备提出的中断请求，这个标志就是中断号。

* 中断请求：“紧急事件”需向CPU提出申请，要求CPU暂停当前执行的任务，转而处理该“紧急事件”，这一申请过程称为中断请求。

* 中断优先级：为使系统能够及时响应并处理所有中断，系统根据中断时间的重要性和紧迫程度，将中断源分为若干个级别，称作中断优先级。

* 中断处理程序：当外设产生中断请求后，CPU暂停当前的任务，转而响应中断申请，即执行中断处理程序。

* 中断触发：中断源发出并送给CPU控制信号，将中断触发器置“1”，表明该中断源产生了中断，要求CPU去响应该中断，CPU暂停当前任务，执行相应的中断处理程序。

* 中断触发类型：外部中断申请通过一个物理信号发送到NVIC，可以是电平触发或边沿触发。

* 中断向量：中断服务程序的入口地址。

* 中断向量表：存储中断向量的存储区，中断向量与中断号对应，中断向量在中断向量表中按照中断号顺序存储。

* 临界段：代码的临界段也称为临界区，一旦这部分代码开始执行，则不允许任何中断打断。为确保临界段代码的执行不被中断，在进入临界段之前须关中断，而临界段代码执行完毕后，要立即开中断。

#### 中断管理的运作机制

当中断产生时，处理机将按如下的顺序执行：

1. 保存当前处理机状态信息
2. 载入异常或中断处理函数到PC寄存器
3. 把控制权转交给处理函数并开始执行
4. 当处理函数执行完成时，恢复处理器状态信息
5. 从异常或中断中返回到前一个程序执行点

中断使得CPU可以在事件发生时才给予处理，而不必让CPU连续不断地查询是否有相应的事件发生。通过两条特殊指令：关中断和开中断可以让处理器不响应或响应中断，**在关闭中断期间，通常处理器会把新产生的中断挂起，当中断打开时立刻进行响应，所以会有适当的延时响应中断，故用户在进入临界区的时候应快进快出**。

中断发生的环境有两种情况：**在任务的上下文中**，**在中断服务函数处理上下文中**。

- 任务在工作的时候，如果此时发生了一个中断，无论中断的优先级是多大，都会打断当前任务的执行，从而转到对应的中断服务函数中执行。
- 在执行中断服务例程的过程中，如果有更高优先级别的中断源触发中断，由于当前处于中断处理上下文环境中，根据不同的处理器构架可能有不同的处理方式，比如新的中断等待挂起直到当前中断处理离开后再行响应；或新的高优先级中断打断当前中断处理过程，而去直接响应这个更高优先级的新中断源。后面这种情况，称之为中断嵌套。在硬实时环境中，前一种情况是不允许发生的，不能使响应中断的时间尽量的短。而在软件处理（软实时环境）上，FreeRTOS允许中断嵌套，即在一个中断服务例程期间，处理器可以响应另外一个优先级更高的中断。

#### 中断延迟的概念

即使操作系统的响应很快了，但对于中断的处理仍然存在着中断延迟响应的问题，我们称之为**中断延迟**(Interrupt Latency) 。

中断延迟是指从硬件中断发生到开始执行中断处理程序第一条指令之间的这段时间。也就是：系统接收到中断信号到操作系统作出响应，并完成换到转入中断服务程序的时间。也可以简单地理解为：（外部）硬件（设备）发生中断，到系统执行中断服务子程序（ISR）的第一条指令的时间。

中断的处理过程是：外界硬件发生了中断后，CPU到中断处理器读取中断向量，并且查找中断向量表，找到对应的中断服务子程序（ISR）的首地址，然后跳转到对应的ISR去做相应处理。这部分时间，我称之为：识别中断时间。

在允许中断嵌套的实时操作系统中，中断也是基于优先级的，允许高优先级中断抢断正在处理的低优先级中断，所以，如果当前正在处理更高优先级的中断，即使此时有低优先级的中断，也系统不会立刻响应，而是等到高优先级的中断处理完之后，才会响应。而在不支持中断嵌套的实时操作系统中，即中断是没有优先级的，中断是不允许被中断的，所以，如果当前系统正在处理一个中断，而此时另一个中断到来了，系统也是不会立即响应的，而只是等处理完当前的中断之后，才会处理后来的中断。此部分时间，我称其为：等待中断打开时间。

在操作系统中，很多时候我们会主动进入临界段，系统不允许当前状态被中断打断，故而在临界区发生的中断会被挂起，直到退出临界段时候打开中断。此部分时间，我称其为：关闭中断时间。

中断延迟可以定义为，从中断开始的时刻到中断服务例程开始执行的时刻之间的时间段。中断延迟 = 识别中断时间 + [等待中断打开时间] + [关闭中断时间]。

注意：“[ ]”的时间是不一定都存在的，此处为最大可能的中断延迟时间。

#### 中断管理的应用场景

中断在嵌入式处理器中应用非常之多，没有中断的系统不是一个好系统，因为有中断，才能启动或者停止某件事情，从而转去做另一间事情。我们可以举一个日常生活中的例子来说明，假如你正在给朋友写信，电话铃响了，这时你放下手中的笔去接电话，通话完毕再继续写信。这个例子就表现了中断及其处理的过程：电话铃声使你暂时中止 当前的工作，而去处理更为急需处理的事情——接电话，当把急需处理的事情处理完毕之后，再回过头来继续原来的事情。在这个例子中，电话铃声就可以称为“中断请求”，而你暂停写信去接电话就叫作“中断响应”，那么接电话的过程就是“中断处理”。由此我们可以看出，在计算机执行程序的过程中，由于出现某个特殊情况(或称为 “特殊事件”)，使得系统暂时中止现行程序，而转去执行处理这一特殊事件的程序，处理完毕之后再回到原来程序的中断点继续向下执行。

为什么说没有中断的系统不是好系统呢？我们可以再举一个例子来说明中断的作用。假设有一个朋友来拜访你，但是由于不知何时到达，你只能在门口等待，于是什么事情也干不了；但如果在门口装一个门铃，你就不必在门口等待而可以在家里去做其他的工作，朋友来了按门铃通知你，这时你才中断手中的工作去开门，这就避免了不必要的等待。CPU也是一样，如果时间都浪费在查询的事情上，那这个CPU啥也干不了，要他何用。**在嵌入式系统中合理利用中断，能更好利用CPU的资源**。

#### 中断管理讲解

ARM Cortex-M 系列内核的中断是由硬件管理的，而FreeRTOS是软件，它并不接管由硬件管理的相关中断（接管简单来说就是，所有的中断都由RTOS的软件管理，硬件来了中断时，**由软件决定是否响应**，可以挂起中断，延迟响应或者不响应），只支持简单的开关中断等，所以FreeRTOS中的中断使用其实跟裸机差不多的，需要我们自己配置中断，并且使能中断，编写中断服务函数，在中断服务函数中使用内核IPC通信机制，一般建议使用信号量、消息或事件标志组等标志事件的发生，将事件发布给处理任务，等退出中断后再由相关处理任务具体处理中断。

用户可以自定义配置系统可管理的最高中断优先级的宏定义configLIBRARY_MAX_SYSCALL_INTERRUPT_PRIORITY，它是用于配置内核中的basepri寄存器的，当basepri设置为某个值的时候，NVIC不会响应比该优先级低的中断，而优先级比之更高的中断则不受影响。就是说当这个宏定义配置为5的时候，**中断优先级数值在0、1、2、3、4的这些中断是不受FreeRTOS屏蔽的**，也就是说即使在系统进入临界段的时候，这些中断也能被触发而不是等到退出临界段的时候才被触发，当然，这些中断服务函数中也不能调用FreeRTOS提供的API函数接口，而中断优先级在5到15的这些中断是可以被屏蔽的，也能安全调用FreeRTOS提供的API函数接口。

ARM Cortex-M NVIC支持中断嵌套功能：当一个中断触发并且系统进行响应时，处理器硬件会将当前运行的部分上下文寄存器自动压入中断栈中，这部分的寄存器包括PSR，R0，R1，R2，R3以及R12寄存器。当系统正在服务一个中断时，如果有一个更高优先级的中断触发，那么处理器同样的会打断当前运行的 中断服务例程，然后把老的中断服务例程上下文的PSR，R0，R1，R2，R3和R12寄存器自动保存到中断栈中。这些部分上下文寄存器保存到中断栈的行为完全是硬件行为，这一点是与其他ARM处理器最大的区别（以往都需要依赖于软件保存上下文）。

另外，在ARM Cortex-M系列处理器上，所有中断都采用中断向量表的方式进行处理，即当一个中断触发时，处理器将直接判定是哪个中断源，然后直接跳转到相应的固定位置进行处理。而在ARM7、ARM9中，一般是先跳转进入IRQ入口，然后再由软件进行判断是哪个中断源触发，获得了相对应的中断服务例程入口地址 后，再进行后续的中断处理。ARM7、ARM9的好处在于，所有中断它们都有统一的入口地址，便于OS的统一管理。而ARM Cortex- M系列处理器则恰恰相反，每个中断服务例程必须排列在一起放在统一的地址上（这个地址必须要设置到NVIC的中断向量偏移寄存器中）。中断向量表一般由一个数组定义（或在起始代码中给出），在STM32上，默认采用起始代码给出。

#### 中断管理实验

中断管理实验是在FreeRTOS中创建了两个任务分别获取信号量与消息队列，并且定义了两个按键KEY1与KEY2的触发方式为中断触发，其触发的中断服务函数则跟裸机一样，在中断触发的时候通过消息队列将消息传递给任务，任务接收到消息就将信息通过串口调试助手显示出来。而且中断管理实验也实现了一个串口的DMA 传输+空闲中断功能，当串口接收完不定长的数据之后产生一个空闲中断，在中断中将信号量传递给任务，任务在收到信号量的时候将串口的数据读取出来并且在串口调试助手中回显。

* 配置按键中断：

```c
void EXTI_Key_Config(void)
{
	GPIO_InitTypeDef GPIO_InitStructure; 
	EXTI_InitTypeDef EXTI_InitStructure;

	/*开启按键GPIO口的时钟*/
	RCC_APB2PeriphClockCmd(KEY1_INT_GPIO_CLK,ENABLE);
												
	/* 配置 NVIC 中断*/
	NVIC_Configuration();
	
/*--------------------------KEY1配置-----------------------------*/
	/* 选择按键用到的GPIO */	
  GPIO_InitStructure.GPIO_Pin = KEY1_INT_GPIO_PIN;
  /* 配置为浮空输入 */	
  GPIO_InitStructure.GPIO_Mode = GPIO_Mode_IN_FLOATING;
  GPIO_Init(KEY1_INT_GPIO_PORT, &GPIO_InitStructure);

	/* 选择EXTI的信号源 */
  GPIO_EXTILineConfig(KEY1_INT_EXTI_PORTSOURCE, KEY1_INT_EXTI_PINSOURCE); 
  EXTI_InitStructure.EXTI_Line = KEY1_INT_EXTI_LINE;
	
	/* EXTI为中断模式 */
  EXTI_InitStructure.EXTI_Mode = EXTI_Mode_Interrupt;
	/* 上升沿中断 */
  EXTI_InitStructure.EXTI_Trigger = EXTI_Trigger_Rising;
  /* 使能中断 */	
  EXTI_InitStructure.EXTI_LineCmd = ENABLE;
  EXTI_Init(&EXTI_InitStructure);
	
  /*--------------------------KEY2配置-----------------------------*/
	/* 选择按键用到的GPIO */	
  GPIO_InitStructure.GPIO_Pin = KEY2_INT_GPIO_PIN;
  /* 配置为浮空输入 */	
  GPIO_InitStructure.GPIO_Mode = GPIO_Mode_IN_FLOATING;
  GPIO_Init(KEY2_INT_GPIO_PORT, &GPIO_InitStructure);

	/* 选择EXTI的信号源 */
  GPIO_EXTILineConfig(KEY2_INT_EXTI_PORTSOURCE, KEY2_INT_EXTI_PINSOURCE); 
  EXTI_InitStructure.EXTI_Line = KEY2_INT_EXTI_LINE;
	
	/* EXTI为中断模式 */
  EXTI_InitStructure.EXTI_Mode = EXTI_Mode_Interrupt;
	/* 下降沿中断 */
  EXTI_InitStructure.EXTI_Trigger = EXTI_Trigger_Falling;
  /* 使能中断 */	
  EXTI_InitStructure.EXTI_LineCmd = ENABLE;
  EXTI_Init(&EXTI_InitStructure);
}
```

* 定义按键中断服务函数：

```c
void KEY1_IRQHandler(void)
{
	BaseType_t pxHigherPriorityTaskWoken;
  //确保是否产生了EXTI Line中断
  uint32_t ulReturn;
  /* 进入临界段，临界段可以嵌套 */
  ulReturn = taskENTER_CRITICAL_FROM_ISR();
  
	if(EXTI_GetITStatus(KEY1_INT_EXTI_LINE) != RESET) 
	{
    /* 将数据写入（发送）到队列中，等待时间为 0  */
		xQueueSendFromISR(Test_Queue, /* 消息队列的句柄 */
											&send_data1,/* 发送的消息内容 */
											&pxHigherPriorityTaskWoken);
		
		//如果需要的话进行一次任务切换
		portYIELD_FROM_ISR(pxHigherPriorityTaskWoken);
		
		//清除中断标志位
		EXTI_ClearITPendingBit(KEY1_INT_EXTI_LINE);     
	}  
  
  /* 退出临界段 */
  taskEXIT_CRITICAL_FROM_ISR( ulReturn );
}

void KEY2_IRQHandler(void)
{
	BaseType_t pxHigherPriorityTaskWoken;
  uint32_t ulReturn;
  /* 进入临界段，临界段可以嵌套 */
  ulReturn = taskENTER_CRITICAL_FROM_ISR();
  
  //确保是否产生了EXTI Line中断
	if(EXTI_GetITStatus(KEY2_INT_EXTI_LINE) != RESET) 
	{
    /* 将数据写入（发送）到队列中，等待时间为 0  */
		xQueueSendFromISR(Test_Queue, /* 消息队列的句柄 */
											&send_data2,/* 发送的消息内容 */
											&pxHigherPriorityTaskWoken);
		
		//如果需要的话进行一次任务切换
		portYIELD_FROM_ISR(pxHigherPriorityTaskWoken);
		
		//清除中断标志位
		EXTI_ClearITPendingBit(KEY2_INT_EXTI_LINE);     
	}  
  
  /* 退出临界段 */
  taskEXIT_CRITICAL_FROM_ISR( ulReturn );
}
```

### CPU使用率统计

#### CPU利用率的基本概念

CPU使用率其实就是系统运行的程序占用的CPU资源，表示机器在某段时间程序运行的情况，如果这段时间中，程序一直在占用CPU的使用权，那么可以人为CPU的利用率是100%。CPU的利用率越高，说明机器在这个时间上运行了很多程序，反之较少。利用率的高低与CPU强弱有直接关系，就像一段一模一样的程序，如果 使用运算速度很慢的CPU，它可能要运行1000ms，而使用很运算速度很快的CPU可能只需要10ms，那么在1000ms这段时间中，前者的CPU利用率就是100%，而后者的CPU利用率只有1%，因为1000ms内前者都在使用CPU做运算，而后者只使用10ms的时间做运算，剩下的时间CPU可以做其他事情 。

FreeRTOS是多任务操作系统，对CPU都是分时使用的：比如A任务占用10ms，然后B任务占用30ms，然后空闲60ms，再又是A任务占10ms，B任务占30ms，空闲60ms；如果在一段时间内都是如此，那么这段时间内的利用率为40%，因为整个系统中只有40%的时间是CPU处理数据的时间。

#### CPU利用率的作用

一个系统设计的好坏，可以使用CPU使用率来衡量，一个好的系统必然是能完美响应急需的处理，并且系统的资源不会过于浪费（性价比高）。举个例子，假设一个系统的CPU利用率经常在90%~100%徘徊，那么系统就很少有空闲的时候，这时候突然有一些事情急需CPU的处理，但是此时CPU都很可能被其他任务在占用了， 那么这个紧急事件就有可能无法被相应，即使能被相应，那么占用CPU的任务又处于等待状态，这种系统就是不够完美的，因为资源处理得太过于紧迫；反过来，假如CPU的利用率在1%以下，那么我们就可以认为这种产品的资源过于浪费，搞一个那么好的CPU去干着没啥意义的活（大部分时间处于空闲状态），使用，作为产品的设计，**既不能让资源过于浪费，也不能让资源过于紧迫，这种设计才是完美的**，在需要的时候能及时处理完突发事件，而且资源也不会过剩，性价比更高。

#### CPU利用率统计

FreeRTOS是一个很完善很稳定的操作系统，当然也给我们提供测量各个任务占用CPU时间的函数接口，我们可以知道系统中的每个任务占用CPU的时间，从而得知系统设计的是否合理，出于性能方面的考虑，有的时候，我们希望知道CPU的使用率为多少，进而判断此CPU的负载情况和对于当前运行环境是否能够“胜任工作 ”。所以，在调试的时候很有必要得到当前系统的CPU利用率相关信息，但是在产品发布的时候，就可以把CPU利用率统计这个功能去掉，因为使用任何功能的时候，都是需要消耗系统资源的，FreeRTOS 是使用一个外部的变量进行统计时间的，并且消耗一个高精度的定时器，其用于定时的精度是系统时钟节拍的10-20倍 ，比如当前系统时钟节拍是1000HZ，那么定时器的计数节拍就要是10000-20000HZ。而且FreeRTOS进行CPU利用率统计的时候，也有一定缺陷，因为它没有对进行CPU利用率统计时间的变量做溢出保护，我们使用的是 32 位变量来系统运行的时间计数值，而按20000HZ的中断频率计算，每进入一中断就是50us，变量加一，最大支持计数时间：2^32 * 50us / 3600s =59.6 分钟，运行时间超过了 59.6 分钟后统计的结果将不准确，除此之外整个系统一直响应定时器50us一次的中断会比较影响系统的性能。

用户想要使用使用CPU利用率统计的话，需要自定义配置一下，首先在FreeRTOSConfig.h配置与系统运行时间和任务状态收集有关的配置选项，并且实现portCONFIGURE_TIMER_FOR_RUN_TIME_STATS()与portGET_RUN_TIME_COUNTER_VALUE()这 两个宏定义。

#### CPU利用率统计实验

CPU利用率实验是是在FreeRTOS中创建了三个任务，其中两个任务是普通任务，另一个任务用于获取CPU利用率与任务相关信息并通过串口打印出来。

* 定义CPU利用率统计任务：

```c
static void CPU_Task(void* parameter)
{	
  uint8_t CPU_RunInfo[400];		//保存任务运行时间信息
  
  while (1)
  {
    memset(CPU_RunInfo,0,400);				//信息缓冲区清零
    
    vTaskList((char *)&CPU_RunInfo);  //获取任务运行时间信息
    
    printf("---------------------------------------------\r\n");
    printf("任务名      任务状态 优先级   剩余栈 任务序号\r\n");
    printf("%s", CPU_RunInfo);
    printf("---------------------------------------------\r\n");
    
    memset(CPU_RunInfo,0,400);				//信息缓冲区清零
    
    vTaskGetRunTimeStats((char *)&CPU_RunInfo);
    
    printf("任务名       运行计数         使用率\r\n");
    printf("%s", CPU_RunInfo);
    printf("---------------------------------------------\r\n\n");
    vTaskDelay(1000);   /* 延时500个tick */		
  }
}
```



### CubeMX使用FreeRTOS编程指南

🔗：[CubeMX使用FreeRTOS编程指南_cubemx freertos-CSDN博客](https://blog.csdn.net/qq_45396672/article/details/120877303)

#### 开发前言

将时基源改为TIM4或其他不使用的定时器，因为SysTick要用作FreeRTOS的时基定时

![image-20240902215512494](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240902215512494.png)

#### 配置界面

开启FreeRTOS之后，可以看到配置项主要分为以下几个部分：

![image-20240902214315859](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240902214315859.png)

* Tasks and Queues：任务与队列，用于配置任务体以及消息队列；
* Timers and Semaphores：软件定时器与信号量，用于配置内核对象（软件定时器和信号量）；
* Mutexes：互斥量，用于配置内核对象
* Events：事件，配置内核对象
* FreeRTOS Heap Usage：查看用户任务和系统任务的堆占用
* Config Parameters：系统的参数配置
* Include Parameters：系统的功能裁剪
* Advanced Settings：CubeMX 生成代码预配置项
* User Constants：用户常量定义

#### 系统设置

参数功能表：

| 参数                                                      | 功能                                   |
| --------------------------------------------------------- | -------------------------------------- |
| **API**                                                   | 显示 FreeRTOS API 接口版本             |
| **Version**                                               | 显示 FreeRTOS 内核版本 显示 CMSIS 版本 |
| **Kernel Setting**                                        | FreeRTOS 调度内核设置                  |
| **Memory management setting**                             | 内存管理设置                           |
| **Hook function related definitions**                     | 钩子函数有关定义                       |
| **Run time and task stats gathering related definitions** | 系统运行时的参数收集配置               |
| **Co-routine related definitions**                        | 协程配置                               |
| **Software timer definitons**                             | 软件定时器任务配置                     |
| **Interrupt nesting behaviour configuration**             | 中断优先级配置                         |

API 和 Version 不过多解释，显示版本信息

##### 调度内核设置

`Kernel Setting`是FreeRTOS的调度内核配置，展开后有下面的配置项，使用时一般保持默认，也可以根据需要修改

![20211006182448](https://i-blog.csdnimg.cn/blog_migrate/d00b7ef05fa75a0e5dc37f5e99a7a3e5.png)

* USE_PREEMPTION
* CPU_CLOCK_HZ
* TICK_RATE_HZ
* MAX_PRIORITIES

FreeRTOS任务的最高优先级设置，默认56级，一般来说一个优先级表是32位，这里用了两个，对应64位，其中8位用于系统任务的优先级处理

* MINIMAL_STACK_SIZE

设置分配给空闲任务的堆栈大小，该值是用字（32位）指定的，而不是字节，默认为128字，如果修改过空闲任务，则根据实际情况修改

* MAX_TASK_NAME_LEN

设置任务名称的最大字符数

* USE_16_BIT_TICKS

存放Tick周期的计数器的数字位宽

* IDLE_SHOULD_YIELD

如果设置为0，则空闲任务永远不会让位于另一个任务，只在被抢占时才会离开运行状态。

如果设置为1，那么当有另一个空闲优先级任务处于就绪状态时，空闲任务将不会执行它定义的功能的不止一次迭代，而不会让位于另一个任务。这确保当应用程序任务处于空闲状态时，在空闲任务中花费的时间最少，即同在空闲优先级下，空闲任务优先级更高，不会被抢占，不会以时间片运行。

##### 内存管理设置

内存管理可以看到三个配置参数：

![20211006224158](https://i-blog.csdnimg.cn/blog_migrate/76585a90b8aec4ceb3ff757ba5e23aae.png)

* Memory Allocation

内存分配方式，此处默认动态和静态都可以

* TOTAL_HEAP_SIZE

内存堆的分配大小，堆本质上就是一个数组，此处是设置堆数组的大小，设置时要考虑最小要满足所有任务的使用要求，最大不要超过系统的分配上线。

* Memory Management scheme

内存分配方式，有heap_1.c, heap_2.c, heap_3.c, heap_4.c and heap5.c 5种，其中1、2、4、5都是先建立一个堆数组，从数组中申请，用完再释放，与C语言中molloc和free使用链表的方式不同，该方式在 MCU 中更安全稳定，此处默认使用的方式4，具体申请释放方式可以在heap4.c中阅读到

##### 钩子函数配置

* USE_IDLE_HOOK

使能后，系统生成一个空回调函数，由用户编写函数主体

```c
void vApplicationIdleHook(void)
```

每当空闲任务执行一次，钩子函数都会被执行一次

* USE_TICK_HOOK

使能后，系统生成一个空回调函数，由用户编写函数主体

```c
void vApplicationTickHook(void)
```

每个TICK周期，钩子函数都会执行一次

* USE_MALLOC_FAILED_HOOK

使能后，系统生成一个空回调函数，由用户编写函数主体

```c
void vApplicationMallocFailedHook(void)
```

当申请动态内存失败时，钩子函数会执行一次

* USE_DAEMON_TASK_STARTUP_HOOK

使能后，系统生成一个空回调函数，由用户编写函数主体

```c
void vApplicationDaemonTaskStartupHook(void)
```

任务刚启动时，钩子函数会执行一次

* CHECK_FOR_STACK_OVERFLOW

使能后，系统生成一个空回调函数，由用户编写函数主体

```c
void vApplicationStackOverflowHook( xTaskHandle xTask, signed char *pcTaskName )
```

任务栈溢出时，钩子函数会执行一次，传入任务 TCB 和任务名称

##### 任务运行追踪配置

![20211007081447](https://i-blog.csdnimg.cn/blog_migrate/6cf405c5a10ed591a52f566776112561.png)

* GENERATE_RUN_TIME_STATS

开启时间统计功能，在调用vTaskGetRunTimeStats函数时，将任务运行时间信息保存到可读列表中

* USE_TRACE_FACILITY

使能后会包含额外的结构成员和函数以帮助执行可视化和跟踪，默认开启，方便MDK软件工具调试使用

* USE_STATS_FORMATTING_FUNCTIONS

使能后会生成vTaskList和vTaskGetRunTimeStats函数用于获取任务运行状态

##### 协程配置

Co-routine related definitions 是协程的配置项，两个选项用来配置协程是否开启，以及协程的优先级，开启后，需要用户手动创建协程，在协程几乎很少用到了，是 FreeRTOS目前还没有把协程移除的计划，但 FreeRTOS是不会再更新和维护协程了，因此了解一下就行

协程特点：

* 堆栈使用：所有的协程使用同一个堆栈，这样比使用任务消耗更少的RAM
* 调度器和优先级：协程使用合作式的调度器，但是可以在使用抢占式的调度器中使用协程
* 宏实现：协程式通过宏定义来实现的
* 使用限制：为了降低对RAM的消耗做了很多的限制

##### 软件定时器配置

![20211007084642](https://i-blog.csdnimg.cn/blog_migrate/b11299c8e377959b404b6fd3efcb4e9b.png)

这四个配置项主要与软件定时器处理任务有关，软件定时器任务属于系统任务（守护线程），开启软件定时器后用于维护软件定时器

* USE_TIMERS

默认开启软件定时器任务

* TIMER_TASK_PRIORITY

软件定时器任务优先级

* TIMER_QUEUE_LENGTH

定时器任务队列长度，FreeRTOS 是通过队列来发送控制命令给定时器任务，叫做定时器命令队列，此处设置队列长度

* TIMER_TASK_STACK_DEPTH

软件定时器任务堆栈大小

##### 中断优先级配置

* LIBRARY_LOWEST_INTERRUPT_PRIORITY

此宏是用来设置最低优先级，FreeRTOS 使用的4位优先级，对应16位优先级，对应的最低优先级为15

* LIBRARY_MAX_SYSCALL_INTERRUPT_PRIORITY

设置FreeRTOS 系统可管理的最大优先级，也就是设置阈值优先级，这个大家可以自由设置，这里设置为5，也就是高于5 的优先级(优先级数小于5)不归 FreeRTOS 管理

#### 内核剪裁

Include Parameters 下的选项应用于内核裁剪，裁剪不必要的功能，精简系统功能，减少资源占用，主要有以下几个选项：

![20211007095602](https://i-blog.csdnimg.cn/blog_migrate/cd675f22b3a82b26aee0c648dac42299.png)

配置项可裁剪的函数功能如下：

#### 创建任务与队列

##### 任务的创建与配置

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240911195630586.png" alt="image-20240911195630586" style="zoom:50%;" />

* Task Name：任务名称，保存在TCB结构体中，设置时自己起名字
* Priority：任务优先级，任务的调度等级，根据自己创建任务的紧急程度设定
* Stack Size：设定给任务分配的内存大小，单位是字
* Entry Function：任务实体，即任务的运行函数名
* Code Generation：代码生成模式。
* Parameter：传入的参数，保持默认就行
* Allocation：内存分配方式，静态方式是直接在RAM占据一个静态空间；动态方式则是在初始配置的内存池大小数组中动态申请、释放空间

创建任务对应代码：

```c
  xReturn = xTaskCreate((TaskFunction_t )LED_Task, /* 任务入口函数 */
                        (const char*    )"LED_Task",/* 任务名字 */
                        (uint16_t       )512,   /* 任务栈大小 */
                        (void*          )NULL,	/* 任务入口函数参数 */
                        (UBaseType_t    )2,	    /* 任务的优先级 */
                        (TaskHandle_t*  )&LED_Task_Handle);/* 任务控制块指针 */
```

但需要注意Task Name和Entry Function需要是不同的名字

设置完成后点击OK，配置就完成了，之后生成代码，使用MDK进一步配置任务的具体信息

在生成的代码中，我们打开freertos.c文件可以在代码中看到任务的配置信息

##### 队列的创建与配置

🔗：[STM32CubeMX学习笔记（29）——FreeRTOS实时操作系统使用（消息队列）_cubemx的sys里的timebase source-CSDN博客](https://leung-manwah.blog.csdn.net/article/details/122187066)

队列，又称为消息队列，用于任务间的数据通信，传输数据，在操作系统里面，直接使用全局变量传输数据十分危险，看似正常运行，但不知道什么时候就会因为寄存器或者内存等原因引起崩溃，所以引入消息队列的概念，任务发送数据到队列，需要接收消息的任务挂起在队列的挂起列表，等待消息的到来。使用CubeMX创建队列的步骤如下：

1. 先点击Add添加队列

![image-20240912221515725](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240912221515725.png)

* Queue Name：队列名称
* Queue Size：队列能够存储的最大单元数目，即队列深度
* Item Size：队列中数据单元的长度，以字节为单位
* Allocation：内存分配方式
* Buffer Name：缓冲区名称
* Buffer Size：缓冲区大小
* Control Block Name：控制块名称

创建队列相关API说明：

```c
osMessageQDef(TestQueue, 16, uint32_t);
TestQueueHandle = osMessageCreate(osMessageQ(TestQueue), NULL);
```

消息发送与接收相关API说明：



#### 创建定时器和信号量

#### 创建互斥量

#### 创建事件标志组

#### 用户常量

#### 任务通知

#### 系统内核配置

### 确定使用栈的大小

🔗：[RTOS中如何确定使用栈的大小-云社区-华为云 (huaweicloud.com)](https://bbs.huaweicloud.com/blogs/427997)

🔗：[STM32CubeMX FreeRTOS堆栈分配、调试技巧-腾讯云开发者社区-腾讯云 (tencent.com)](https://cloud.tencent.com/developer/article/1801393)

在裸机编程中：

* 系统堆HEAP：当我们使用malloc函数申请内存时，就是从这里申请的，它必须由程序员提前定义好大小，如果空间不足，malloc会申请失败。
* 系统栈STACK：用来存储临时变量、函数的参数等等，当我们进行函数嵌套时，进入函数前，是要进行保存现场的工作的，等执行完函数跳回到原来位置时，需要恢复现场，而保存现场所使用的内存，就是从系统栈中获取的，如果系统栈不足，就会出现常说的栈溢出，导致程序跑飞。与系统堆不同的是，系统栈可以不提前规定大小，不影响程序运行。
* 全局区：用来存储全局变量、静态变量

### FreeRTOS实时内核使用指南

#### 任务管理

任务是由C语言函数实现的。唯一特别的只是任务的函数原型，其必须返回void，而且带有一个void指针参数。

任务从非运行态转移到运行态被称为“切换入或切入”或“交换入”。相反，任务从运行态转移到非运行态被称为“切换出或切出”或“交换出”。FreeRTOS的调度器是能让任务切入切出的唯一实体。



### STM32CubeMX实战

#### 任务管理

🔗：[STM32CubeMX学习笔记（28）——FreeRTOS实时操作系统使用（任务管理）_stm32 rtos 任务固定时间运行-CSDN博客](https://leung-manwah.blog.csdn.net/article/details/122037092)

* RCC配置

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240921193739062.png" alt="image-20240921193739062" style="zoom: 80%;" />

* SYS配置

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240921193630984.png" alt="image-20240921193630984" style="zoom:50%;" />

在基于STM32 HAL的项目中，一般需要维护的时基主要有2个：

1. HAL的时基，SYS Timebase Source
2. OS的时基

而这些“时基”该如何去维护，主要分为两种情况考虑：

* 裸机运行

​	可以通过`SysTick`或`TIMx`的方式来维护`SYS Timebase Source`，也就是HAL库中的`uwTick`，这是HAL库中维护的一个全局变量。在裸机运行的情况下，我们一般选择默认的`SysTick`方式，也就是直接放在`SysTick_Handler`中断服务函数中来维护。

* 带OS运行

​	前面提到的SYS Timebase Source是STM32的HAL库中的新增部分，主要用于实现HAL_Delay以及作为各种timeout的时钟基准。

​	在使用了操作系统之后，操作系统的运行也需要一个时钟基准，来对任务和时间等进行管理。而操作系统的这个时基一般也都是通过`SysTick`来维护的，这时就需要考虑HAL的时基和OS的时基是否要共用`SysTick`了。

##### 创建任务相关API说明

* osThreadId：任务ID。例如，对osThreadCreate的调用返回。
* osThreadCreate：使用动态/静态内存的方法创建一个任务。
* osThreadTerminate：删除任务。任务被删除后就不复存在，也不会再进入运行态。
* osKernelStart：在创建完任务的时候，我们需要开启调度器，因为创建仅仅是把任务添加到系统中，还没真正调度，并且空闲任务也没实现，定时器任务也没实现，这些都是在开启调度函数函数中实现的。为什么要空闲任务？因为FreeRTOS一旦启动，就必须要保证系统中每时每刻都有一个任务处于运行态，并且空闲任务不可以被挂起与删除，空闲任务的优先级是最低的，以便系统中其他任务能随时抢占空闲任务的CPU使用权。

#### 消息队列

🔗：[STM32CubeMX学习笔记（29）——FreeRTOS实时操作系统使用（消息队列）_cubemx的sys里的timebase source-CSDN博客](https://leung-manwah.blog.csdn.net/article/details/122187066)

##### 创建队列相关API说明

* osMessageQId
* osMessageCreate：使用动态内存的方式创建一个新的队列
* osMessageDelete：队列删除函数是根据消息队列ID直接删除的，删除之后这个消息队列的所有信息都会被系统回收清空，而且不能再次使用这个消息队列

生成代码后有关队列的定义都在`MX_FREERTOS_Init`中：

```C
void MX_FREERTOS_Init(void) {
  /* USER CODE BEGIN Init */

  /* USER CODE END Init */

  /* USER CODE BEGIN RTOS_MUTEX */
  /* add mutexes, ... */
  /* USER CODE END RTOS_MUTEX */

  /* USER CODE BEGIN RTOS_SEMAPHORES */
  /* add semaphores, ... */
  /* USER CODE END RTOS_SEMAPHORES */

  /* USER CODE BEGIN RTOS_TIMERS */
  /* start timers, add new ones, ... */
  /* USER CODE END RTOS_TIMERS */

  /* Create the queue(s) */
  /* definition and creation of TestQueue */
  osMessageQDef(TestQueue, 16, uint32_t);
  TestQueueHandle = osMessageCreate(osMessageQ(TestQueue), NULL);

  /* USER CODE BEGIN RTOS_QUEUES */
  /* add queues, ... */
  /* USER CODE END RTOS_QUEUES */

  /* Create the thread(s) */
  /* definition and creation of defaultTask */
  osThreadDef(defaultTask, StartDefaultTask, osPriorityNormal, 0, 128);
  defaultTaskHandle = osThreadCreate(osThread(defaultTask), NULL);

  /* definition and creation of Receive */
  osThreadDef(Receive, ReceiveTask, osPriorityIdle, 0, 128);
  ReceiveHandle = osThreadCreate(osThread(Receive), NULL);

  /* definition and creation of Send */
  osThreadDef(Send, SendTask, osPriorityIdle, 0, 128);
  SendHandle = osThreadCreate(osThread(Send), NULL);

  /* USER CODE BEGIN RTOS_THREADS */
  /* add threads, ... */
  /* USER CODE END RTOS_THREADS */

}
```

注意事项：

* 设置里面的Micro Lib需要勾选上，否则无法读取串口数据

#### 信号量

🔗：[五、深入了解信号量机制（大彻大悟篇）内附经典生产者消费者等线程同步问题_生产者和消费者同步信号量-CSDN博客](https://blog.csdn.net/weixin_44205087/article/details/119742972)

信号量其实就是一个变量（可以是一个整数，也可以是更复杂的记录型变量），可以用一个信号量来表示系统中某种资源的数量，比如系统中只有一台打印机，就可以设置一个初值为1的信号量。

用户进程可以通过使用操作系统提供的一对原语来对信号量进行操作，从而很方便地实现了进程互斥、进程同步。



🔗：[STM32CubeMX学习笔记（30）——FreeRTOS实时操作系统使用（信号量）_ossemaphorecreate-CSDN博客](https://leung-manwah.blog.csdn.net/article/details/122211879)

##### 创建信号量Semaphore

创建二值信号量Binary Semaphore

![image-20240922095610728](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240922095610728.png)

* Semaphore Name：信号量名称
* Allocation：分配方式
* Control Block Name：控制块名称

创建计数信号量Counting Semaphore

要想使用计数信号量必须在`Config parameters`中把`USE_COUNTING_SEMAPHORES`选择`Enabled`来使能

![image-20240922100037130](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240922100037130.png)

##### 创建信号量相关API说明

* osSemaphoreCreate：用于创建一个二值信号量，并返回一个ID
* osSemaphoreDelete：用于删除一个信号量，包括二值信号量，计数信号量，互斥量和递归互斥量
* osSemaphoreRelease：用于释放信号量的宏。释放的信号量必须是已经被创建的，可以用于二值信号量、计数信号量、互斥量的释放，但不能释放由函数xSemaphoreCreateRecursiveMutex创建的递归互斥量。可用在中断服务程序中。
* osSemaphoreWait：用于获取信号量，不带中断保护。获取的信号量对象可以是二值信号量、计数信号量和互斥量，但是递归互斥量并不能使用这个API函数获取。可用在中断服务程序中。

获取信号量代码：

```C
void ReceiveTask(void const * argument)
{
  /* USER CODE BEGIN ReceiveTask */
  osStatus xReturn = osErrorValue;
  /* Infinite loop */
  for(;;)
  {
    xReturn = osSemaphoreWait(BinarySemHandle, /* 二值信号量句柄 */ 
                               osWaitForever); /* 等待时间 */ 
    if(osOK == xReturn) 
    {
        printf("BinarySem get!\n\n");
    }
  }
  /* USER CODE END ReceiveTask */
}
```

释放二值信号量代码：

```c
void SendTask(void const * argument)
{
  /* USER CODE BEGIN SendTask */
  osStatus xReturn;
  /* Infinite loop */
  for(;;)
  {
    // 按下按键进行任务与任务间的同步
    if(HAL_GPIO_ReadPin(KEY1_GPIO_Port, KEY1_Pin) == GPIO_PIN_SET) 
    { 
        xReturn = osSemaphoreRelease(BinarySemHandle);//给出二值信号量 
        if(osOK == xReturn)
        {
            printf("release!\r\n"); 
        }
        else 
        {
            printf("BinarySem release fail!\r\n"); 
        }
    } 
    osDelay(100);
  }
  /* USER CODE END SendTask */
}
```

#### 互斥量

🔗：[STM32CubeMX学习笔记（31）——FreeRTOS实时操作系统使用(互斥量)_学习cube freertc 互锁-CSDN博客](https://leung-manwah.blog.csdn.net/article/details/122230132)

互斥量又称互斥信号量，是一种特殊的二值信号量，它和信号量不同的是，它支持互斥量所有权、递归访问以及防止优先级翻转的特性，用于实现对临界资源的独占式处理。

任意时刻互斥量的状态只有两种，开锁或闭锁。当互斥量被任务持有时，该互斥量处于闭锁状态，这个任务获得互斥量的所有权。当该任务释放这个互斥量时，该互斥量处于开锁状态，任务失去该互斥量的所有权。当一个任务持有互斥量时，其他任务将不能再对该互斥量进行开锁或持有。

如果想要用于实现同步（任务之间或者任务与中断之间），二值信号量或许是更好的选择，虽然互斥量也可以用于任务与任务、任务与中断的同步，但是互斥量更多的是用于保护资源的互锁。

互斥量与递归互斥量：

* 互斥量更适合于可能会引起优先级翻转的情况
* 递归互斥量更适用于任务可能会多次获取互斥量的情况下。这样可以避免同一任务递归持有而造成死锁的问题

##### 相关API说明

* osMutexCreate：用于创建一个互斥量，并返回一个ID
* osRecursiveMutexCreate：用于创建一个递归互斥量，不是递归的互斥量由函数osMutexCreate创建，且只能被同一个任务获取一次，如果同一个任务想再次获取则会失效。递归信号则相反，它可以被同一个任务获取很多次，获取多少次就需要释放多少次。递归信号量与互斥量一样，都实现了优先级继承机制，可以减少优先级翻转的发生。要使用该函数必须在`Config parameters`中把`USE_RECURSIVE_MUTEXES`选择`Enabled`使能。
* osMutexDelete：
* osMutexWait：
* osRecursiveMutexWait：
* osMutexRelease：
* osRecursiveMutexRelease：

#### 中断管理

#### CPU使用率统计

🔗：[基于FreeRTOS的CPU利用率计算教程详解（STM32版）_freertos cpu占用率-CSDN博客](https://blog.csdn.net/black_sneak/article/details/130474124?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-0-130474124-blog-122477986.235^v43^pc_blog_bottom_relevance_base7&spm=1001.2101.3001.4242.1&utm_relevant_index=3)

FreeRTOS是使用一个外部的变量进行统计时间的，并且消耗一个高精度的定时器，其用于定时的精度是系统时钟节拍的10-20倍。而且FreeRTOS进行CPU利用率统计的时候，也有一定缺陷，因为它没有对进行CPU利用率统计时间的变量做溢出保护。

要想获得CPU使用率必须在`Config parameters`中把`GENERATE_RUN_TIME_STATS`、`USE_TRACE_FACILITY`、`USE_STATS_FORMATTING_FUNCTIONS`选择`Enabled`来使能。

![img](https://i-blog.csdnimg.cn/blog_migrate/f92193decb8b2813f3dfc1da9117e7ad.png)

### FreeRTOS提高

🔗：[【导航】FreeRTOS学习专栏目录 【快速跳转】 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/555088851)



# FPGA

零基础学习路线：[FPGA：我的零基础学习路线（2022秋招已上岸）持续更新中~_fpga 学习路线-CSDN博客](https://blog.csdn.net/m0_46830519/article/details/127855773)



# 项目

## 压力鞋垫IMU数据采集

采集主板芯片：STM32F405RGT6

设置高速外部时钟HSE，选择外部时钟源

![image-20240606111951672](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240606111951672.png)



**ADC**

模拟/数字转换器：将连续变量的模拟信号转换为离散的数字信号

**ADC的转换模式**

* 单次转换模式：ADC只执行一次转换
* 连续转换模式：转换结束后马上开始新的转换
* 扫描模式：ADC扫描被规则通道和注入通道选中的所有通道，在每个组的每个通道上执行单次转换
* 间断模式

ADC输入通道

在模拟至数字转换器中有两个通道，注入通道和规则通道。

* 规则通道相当于正常运行的程序
* 注入通道可以打断规则通道，如果在规则通道转换过程中，有注入通道进行转换，那么就要先转换为注入通道，等注入通道转换完成后，再回到规则通道的转换流程

只有设置了ADC的引脚，才能够设置ADC的时钟分频

### ADC转换时间

🔗：[ADC定义、工作原理、模式和基本参数详解_adc如何理解使用-CSDN博客](https://blog.csdn.net/m0_72952662/article/details/136063831)

ADC输入时钟ADC_CLK由PCLK2经过分频产生，最大值是36MHz，即最大工作时钟不能超过36MHz，典型值为30MHz。对于STM32F4，一般设置PCLK2=HCLK/2=84MHz，最少需要4分频。

ADC的总转换时间Tconv=采样时间+12个周期（转换时间），采样时间最少不小于3个ADC_CLK，转换时间一般就是12个ADC_CLK，如果对时间没有太过苛刻的要求，应当把采样时间设置得稍长一些，这样得到得结果才会更加准确。

### ADC采样滤波

🔗：[基于STM32的ADC采样及各式滤波实现（HAL库，含VOFA+教程）_数据采集滤波算法stm32-CSDN博客](https://blog.csdn.net/black_sneak/article/details/129629485)

* 算术平均滤波

方法：连续取N个采样值进行算术平均运算

N值较大时：信号平滑度较高，但灵敏度较低

N值较小时：信号平滑度低，但灵敏度较高

N值的选取：一般流量：N=12；压力：N=4

优点：适用于对一般具有随机干扰的信号进行滤波。这种信号的特点是有一个平均值，信号在某一数值范围附近上下波动。

缺点：测量速度较慢或要求数据计算较快的实时控制不适用。

### ADC采样时间

🔗：[【经验分享】STM32的ADC采样时间 - STM32团队 ST意法半导体中文论坛 (stmicroelectronics.cn)](https://shequ.stmicroelectronics.cn/thread-633249-1-1.html)

STM32的ADC采样时间与其ADC的时钟频率密不可分。

例：STM32F103系列的ADC的时钟是在APB2（最大72MHZ）上。我们可以对其分频：

RCC_PCLK2_Div2: ADC clock = PCLK2/2  //72/2=36MHz

RCC_PCLK2_Div4: ADC clock = PCLK2/4  //72M/4=18MHz

RCC_PCLK2_Div6: ADC clock = PCLK2/6 //72M/6=12MHz

RCC_PCLK2_Div8: ADC clock = PCLK2/8 //72M/8=9MHz

对ADC的通道设置不同的采样周期，所对应的采样时间也会不同：

ADC_SampleTime_1Cycles5: Sample time equal to 1.5 cycles 采样时间等于1.5个周期
ADC_SampleTime_7Cycles5: Sample time equal to 7.5 cycles 采样时间等于7.5个周期( o2 G& C! |( j$ I9 y
ADC_SampleTime_13Cycles5: Sample time equal to 13.5 cycles 采样时间等于13.5个周期1 r6 j+ t& x, ~: M& P
ADC_SampleTime_28Cycles5: Sample time equal to 28.5 cycles 采样时间等于28.5个周期- l- k. Y5 [ o, E) k
ADC_SampleTime_41Cycles5: Sample time equal to 41.5 cycles 采样时间等于41.5个周期
ADC_SampleTime_55Cycles5: Sample time equal to 55.5 cycles 采样时间等于55.5个周期
ADC_SampleTime_71Cycles5: Sample time equal to 71.5 cycles 采样时间等于71.5个周期
ADC_SampleTime_239Cycles5: Sample time equal to 239.5 cycles 采样时间等于239.5个周期

ADC的采样时间=采样周期/ADC的时钟频率      ADC的转换时间=ADC的采样时间+12.5周期 (12.5是采集12位AD时间是固定的周期)

### 通道切换

🔗：[基于传感阵列的足底压力扫描系统设计研究 (pku.edu.cn)](https://xbna.pku.edu.cn/fileup/0479-8023/HTML/2018-6-1159.html)

对于电阻式阵列压力传感器, 相邻行列之间的连接除导通电阻外, 还有并联电容的作用, 如图4所示。

在传感单元选通时, 并联电容储存电荷, 当切换到另一个传感单元时, 该单元对应的电容电荷需要时间泄放, 泄放时间由电阻电容组成的RC网络确定。

对于电阻式薄膜压力传感器, 并联电容约为500pF。当足底压力作用时, 电阻式传感器的阻值为kΩ量级, 估计时间常数约为
$$
\tau = RC = 10 k \Omega \times 500 pF = 5 \mu s
$$
即切换通道的时间间隔应大于此时间, 才能使并联电容中的电荷及时泄放, 否则会干扰相邻传感通道的数据采集, 引起压力图像模糊、轮廓不清晰等问题。在实际应用中, 为保证图像的清晰显示, 相邻通道切换时间间隔应至少大于10倍时间常数。

为了在切换通道时能够完全泄放电容电荷，而又尽可能减小对采样频率的影响，需要设置微秒级的延时。而HAL库自带的延时函数只能够实现毫秒级的延时，因此需要自定义一个微秒级的延时函数，这里参考CSDN，使用定时器设计了一个微秒级的延时函数。

🔗：[HAL库中同时实现微秒级us以及毫秒级ms延时_hal库设置两毫秒中断-CSDN博客](https://blog.csdn.net/qq_29506411/article/details/109070558)

基本思想是设置基础定时器，通过轮询的方式实现微秒级延时（如果通过中断方式实现会导致过于频繁进入中断，从而干扰其他中断的及时响应）。

```C
/* USER CODE BEGIN 1 */
void Delay_us(uint16_t us)
{
//	uint16_t counter= us & 0xffff;
 
  HAL_TIM_Base_Start(&htim6);
  __HAL_TIM_SetCounter(&htim6,0);       // 对上次延时产生的计数清零
 
  us = (us > 4)?(us-2):1;    // 对counter的改变是为了让短时长的延时更精确（通过示波器校正过，timer的时钟是72M）
 
  while( us > __HAL_TIM_GetCounter(&htim6) ) {};		
 
  HAL_TIM_Base_Stop(&htim6);
}
/* USER CODE END 1 */
```

这里通过该函数实现200us的延时。

## ADC多通道扫描模式电压采集实验（启用DMA传输数据）

链接：http://t.csdnimg.cn/gaNBL

### 实验步骤

通过设置ADC1的三个通道采样顺序并且开启DMA相对应的通道，对数据寄存器当中每一次的采样值（对应每个通道的外部电压转换值）进行收集，并传递到CPU的内部寄存器中，再对电压值进行串口输出。



## 维特智能IMU配置

使用维特智能的上位机配置IMU的带宽、通讯速率以及回传速率

* 带宽配置为98Hz
* 通讯速率配置为115200
* 回传速率配置为200Hz

## A板定时器中断配置

🔗：[【STM32】HAL库 STM32CubeMX教程六----定时器中断_stm32 hal定时器中断-CSDN博客](https://blog.csdn.net/as480133937/article/details/99201209)

STM32F1系列共有8个定时器：

* 高级定时器：TIM1、TIM8
* 通用定时器：TIM2、TIM3、TIM4、TIM5
* 基本定时器：TIM6、TIM7

STM32F4系列共有15个定时器：

* 高级定时器：TIM1、TIM8
* 通用定时器：TIM2、TIM3、TIM4、TIM5、TIM9~TIM14
* 基本定时器：TIM6、TIM7

基本定时器功能：

* 16位向上、向下、向上/下自动装载计数器
* 16位可编程预分频器
* 触发DAC的同步电路
* 位于APB1总线上

通用定时器功能：

* 16位向上、向下、向上/下自动装载计数器
* 16位可编程预分频器
* 4个独立通道（TIMx_CH1~4）可以用作：测量输入信号的脉冲长度（输入捕获）；输出比较；单脉冲模式输出；PWM输出
* 支持针对定位的增量（正交）编码器和霍尔传感器电路
* 如下事件发生时产生中断DMA：更新；触发事件；输入捕获；输出比较
* 位于APB1总线上

高级定时器功能：

* 高级定时器具有基本、通用定时器的所有功能
* 还具有控制交直流电机所有的功能
* 输出6路互补带死区的信号，刹车功能等
* 位于APB2总线上

定时器频率计算：

定时时间 = 定时器频率 / 倍频 / 装载周期

对于72MHz的频率，500ms中断一次，这两个参数设置如下：

* TIM_Prescaler = 7199
* TIM_Period = 4999

* T = (arr + 1) * (PSC + 1) / Tck
* f = Tck / (PSC + 1) * (arr + 1)

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240625151354614.png" alt="image-20240625151354614" style="zoom:67%;" />

总结：基本定时器就是单纯的定时计数器，通用定时器多了四个通道，相对应的增加了功能，高级定时器具有基本、通用定时器的所有功能，并且添加了其他功能。

相关函数：

```c
HAL_TIM_IRQHandler(&htim2);
```

定时器中断处理函数的作用是判断中断是否正常，然后判断产生的是哪一类定时器中断，然后进入相应的中断回调函数中

```c
void HAL_TIM_PeriodElapsedCallback(TIM_HandleTypeDef *htim)
```

在HAL库中，每进行完一个中断，并不会立刻退出，而是会进入到中断回调函数中

```c
HAL_TIM_Base_Start_IT(&htim2);
```

使能定时器中断

## A板串口DMA发送

🔗：[STM32_HAL库_CubeMx串口DMA通信（DMA发送+DMA空闲接收不定长数据）_hal库+cubemx实现stm32串口不定长接收-CSDN博客](https://blog.csdn.net/qq_30267617/article/details/118877845)

STM32串口通信包括三种方式，阻塞模式、中断模式与DMA模式。库里面相关函数如下：

```c
HAL_StatusTypeDef HAL_UART_Transmit(UART_HandleTypeDef *huart, uint8_t *pData, uint16_t Size, uint32_t Timeout);
HAL_StatusTypeDef HAL_UART_Receive(UART_HandleTypeDef *huart, uint8_t *pData, uint16_t Size, uint32_t Timeout);
HAL_StatusTypeDef HAL_UART_Transmit_IT(UART_HandleTypeDef *huart, uint8_t *pData, uint16_t Size);
HAL_StatusTypeDef HAL_UART_Receive_IT(UART_HandleTypeDef *huart, uint8_t *pData, uint16_t Size);
HAL_StatusTypeDef HAL_UART_Transmit_DMA(UART_HandleTypeDef *huart, uint8_t *pData, uint16_t Size);
HAL_StatusTypeDef HAL_UART_Receive_DMA(UART_HandleTypeDef *huart, uint8_t *pData, uint16_t Size);

```

一般来说，我们使用阻塞模式的发送与中断方式的接收，即`HAL_UART_Transmit`与`HAL_UART_Receive_IT`函数。这种方式原理简单，只要按照协议解析即可，但是需要频繁进入中断。DMA方式直接开辟内存与外设之间的数据传输通道，可以减轻CPU的负担，增加数据处理速度。

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240728110940465.png" alt="image-20240728110940465" style="zoom:50%;" />

串口DMA发送函数：

```c
HAL_UART_Transmit_DMA(UART_HandleTypeDef *huart, uint8_t *pData, uint16_t Size)
```

其中huart为句柄，代表调用的串口名称，pData为数组的指针，Size为要发送的数据大小。

**关于重定义**

极度不推荐在使用DMA的时候按照传统的方式进行重定义



## A板CAN通信配置

配置STM32CubeMX

选择A板芯片型号：STM32F427IIH6

打开外部高速时钟，外部晶振为12MHz

![image-20240625094248161](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240625094248161.png)

配置CAN：

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240625094506345.png" alt="image-20240625094506345" style="zoom:50%;" />

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240625094525821.png" alt="image-20240625094525821" style="zoom:50%;" />

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240707094253449.png" alt="image-20240707094253449" style="zoom:50%;" />

设置波特率为500kHz，CAN1的IO为上拉，开启接收中断

**中断设置**：

🔗：[【HAL库】STM32F407----CAN通信----中断详解_can发送中断和接收中断-CSDN博客](https://blog.csdn.net/MQ0522/article/details/130422992)

STM32F4的CAN通信一共有四个专用中断，分别是：

* 发送中断
* FIFO0接收中断
* FIFO1接收中断
* 错误中断

<img src="https://img-blog.csdnimg.cn/36c0ece3569f467f9abcbdf89901d779.png" alt="在这里插入图片描述" style="zoom: 50%;" />

启动中断具体代码：

```C
//启动CAN发送中断
HAL_CAN_ActivateNotification(&hcan1, CAN_IT_TX_MAILBOX_EMPTY);

//启动CAN接收中断-FIFO0接收新消息
HAL_CAN_ActivateNotification(&hcan1, CAN_IT_RX_FIFO0_MSG_PENDING);
//启动CAN发送中断-FIFO0接收满
HAL_CAN_ActivateNotification(&hcan1, CAN_IT_RX_FIFO0_FULL);
//启动CAN发送中断-FIFO0接收上溢
HAL_CAN_ActivateNotification(&hcan1, CAN_IT_RX_FIFO0_OVERRUN);
//启动CAN接收中断-FIFO1接收新消息
HAL_CAN_ActivateNotification(&hcan1, CAN_IT_RX_FIFO1_MSG_PENDING);
//启动CAN发送中断-FIFO1接收满
HAL_CAN_ActivateNotification(&hcan1, CAN_IT_RX_FIFO1_FULL);
//启动CAN发送中断-FIFO1接收上溢
HAL_CAN_ActivateNotification(&hcan1, CAN_IT_RX_FIFO1_OVERRUN);

//启动CAN-唤醒中断
HAL_CAN_ActivateNotification(&hcan1, CAN_IT_WAKEUP);
//启动CAN-睡眠中断
HAL_CAN_ActivateNotification(&hcan1, CAN_IT_SLEEP_ACK);
//启动CAN-错误告警中断
HAL_CAN_ActivateNotification(&hcan1, CAN_IT_ERROR_WARNING);
//启动CAN-错误被动中断
HAL_CAN_ActivateNotification(&hcan1, CAN_IT_ERROR_PASSIVE);
//启动CAN-总线关闭中断
HAL_CAN_ActivateNotification(&hcan1, CAN_IT_BUSOFF);
//启动CAN-上一个错误代码中断
HAL_CAN_ActivateNotification(&hcan1, CAN_IT_LAST_ERROR_CODE);
//启动CAN-错误中断
HAL_CAN_ActivateNotification(&hcan1, CAN_IT_ERROR);

```

中断回调函数：

```C
//CAN通信-发送完成回调函数
void HAL_CAN_TxMailbox0CompleteCallback(CAN_HandleTypeDef *hcan);
void HAL_CAN_TxMailbox1CompleteCallback(CAN_HandleTypeDef *hcan);
void HAL_CAN_TxMailbox2CompleteCallback(CAN_HandleTypeDef *hcan);
//CAN通信-发送取消回调函数
void HAL_CAN_TxMailbox0AbortCallback(CAN_HandleTypeDef *hcan);
void HAL_CAN_TxMailbox1AbortCallback(CAN_HandleTypeDef *hcan);
void HAL_CAN_TxMailbox2AbortCallback(CAN_HandleTypeDef *hcan);

//CAN通信-FIFO0接收新消息回调函数
void HAL_CAN_RxFifo0MsgPendingCallback(CAN_HandleTypeDef *hcan);
//CAN通信-FIFO0接收满回调函数
void HAL_CAN_RxFifo0FullCallback(CAN_HandleTypeDef *hcan);
//CAN通信-FIFO1接收新消息回调函数
void HAL_CAN_RxFifo1MsgPendingCallback(CAN_HandleTypeDef *hcan);
//CAN通信-FIFO1接收满回调函数
void HAL_CAN_RxFifo1FullCallback(CAN_HandleTypeDef *hcan);

//CAN通信-休眠回调函数
void HAL_CAN_SleepCallback(CAN_HandleTypeDef *hcan);
//CAN通信-唤醒回调函数
void HAL_CAN_WakeUpFromRxMsgCallback(CAN_HandleTypeDef *hcan);
//CAN通信-错误回调函数
void HAL_CAN_ErrorCallback(CAN_HandleTypeDef *hcan);

```

🔗：[最新CubeMX配置CAN通讯教程，避免踩坑，附全套工程文件_cubemx can-CSDN博客](https://blog.csdn.net/prolop87/article/details/122671441)

**注意事项**：

* A板上的CAN1需要外接24V电源供电
* A板上的CAN1和CAN2的IO与CubeMX中默认的不相同
* 更改了波特率后调试器上位机也需要进行修改
* 主机在初始化过程中可能有一些延迟，例如，它可能需要一些时间来配置硬件，或者加载和启动软件。这可能导致主机在一开始的时候不能按照预期的频率发送消息。确保主机硬件在发送消息之前达到稳定的工作状态，可以在主机上电后，设置一段延迟时间，然后再开始发送消息。这段时间可以让硬件（包括电源、振荡器、CAN模块等）有足够时间稳定下来。
* 如果主机发送消息的频率过高，可能会导致一些问题。首先，如果CAN总线的带宽有限，那么过高的发送频率可能会导致总线饱和，从而阻止其他设备发送消息。这可能导致从机无法发送响应，或者导致其他主机无法发送消息。其次，如果你的从机的处理能力有限，那么过高的发送频率可能会导致从机无法及时处理所有的消息。这可能导致从机丢失一些消息，或者导致从机的响应延迟。
* 关于过滤器的设置，CubeMX并不会帮我们生成过滤器相关配置函数，需要我们自己写。首先需要了解什么叫标准帧和扩展帧，简单点理解就是扩展帧比标准帧可定义的范围更大；其次是理解什么叫列表模式和掩码模式，列表模式简单说就是从已知库里面寻找匹配的对象（范围窄），而掩码模式则是我只知道目标的局部特征（范围广），我想根据这个特征筛选出目标对象；最后是过滤器的设置，过滤器是由Filter和Mask组合形成的，假设你的Filter设置了捕捉的目标ID，当Mask设置成0x0000时，你设置的Filter将形同虚设，不起作用；当Mask设置成0xFFFF时，只有当数据的每一位都要和你的Filter匹配，才会接收。
* 关于接收中断，如果是用中断接收CAN数据，千万不要使用HAL_CAN_GetRxFifoFillLevel(&hcan, CAN_RX_FIFO0) != 1这个判断，不然一旦接收到数据后，就触发里面设置的Return了。

## A板CAN通信优化

目前的数据采集方式是通过主机定期发送请求消息，从机接收到请求后发送数据，主机再根据接收到的数据进行处理并继续发送请求。这种方式可以确保数据的有序采集，但也可能会因为频繁的请求-响应操作而导致效率问题。

### 关于CAN一次性发送消息的数量

在CAN总线上一次性发送消息的数量取决于多个因素，包括CAN总线的带宽、消息的优先级、总线上其他节点活动以及节点的发送缓冲区大小。为了确定不出现堵塞的情况下最多能一次性发送多少消息，可以考虑以下几个方面：

* CAN总线带宽和传输速率：决定了在一定时间内能传输多少消息。每条CAN消息的长度会影响传输时间。
* 节点的发送缓冲区大小：CAN控制器通常有一个发送缓冲区，用于存储待发送的消息。如果发送缓冲区已满，新的消息将无法进入缓冲区，导致发送失败或等待。
* 总线上的其他节点活动：总线上的其他节点活动也会影响消息的发送。如果总线非常繁忙，发送大量消息可能会导致堵塞。

实验和监控：最好的方法是通过实验和监控来确定最多能一次性发送多少消息而不会出现堵塞。你可以逐步增加一次性发送的消息数量，并通过监控总线的状态和发送成功率来确定最佳数量。



### A板CAN+DMA

如果一次需要接收的数据量过大，可能会导致采集频率过低，这时候可以考虑使用DMA。

直接存储器存取（DMA）用来提供在外设和存储器之间或者存储器和存储器之间的高速数据传输，无需CPU干预，节省了CPU的资源来做其他操作。

针对STM32F4芯片的注意事项：

🔗：[这么多年了，才发现STM32F4系列使用DMA1的大坑，只有DMA2才是完全体 - STM32F429 - 硬汉嵌入式论坛 - Powered by Discuz! (armbbs.cn)](https://www.armbbs.cn/forum.php?mod=viewthread&tid=97900)

* DMA1仅支持APB1下的外设，而DMA2都支持，含APB1，APB2，AHB1，AHB2

### 增加CAN接收数据的缓冲区大小

* 使用多个FIFO

STM32F4的CAN控制器有两个接收FIFO，每个FIFO默认可以容纳3个消息。你可以通过配置CAN硬件寄存器，使用两个FIFO来增加接收容量。

* 软件环形缓冲区（软件FIFO）

由于硬件FIFO的容量有限，可以在接收中断中，将接收到的数据存入一个更大的软件缓冲区（比如一个环形缓冲区），从而提高总的缓冲能力。

* 增加硬件过滤器数量

通过增加或优化CAN硬件过滤器的配置，可以确保重要消息被更有效地捕获，减少不必要的消息进入FIFO，从而减轻硬件FIFO的负担。

## A板PWM输出及仿真

🔗：[第五章-PWM控制电机 开源stm32循迹小车详细制作过程（附加完全版代码）-openmv视觉循迹、红外循迹、避障跟随、超声波跟随、蓝牙遥控 m32f103c8t6、stm32cubemx_循迹小车开源代码-CSDN博客](https://blog.csdn.net/qq_46187594/article/details/138195241?spm=1001.2014.3001.5502)

## 发送机（STM32F103C8T6）CAN通信配置

配置SYS Mode为Serial Wire

🔗：[STM32开发（五）STM32F103 通信 —— CAN通信编程详解_stm32f103 can-CSDN博客](https://blog.csdn.net/weixin_43564241/article/details/128588155)

由于CAN在APB1时钟线上，APB1时钟配置为36MHz

![image-20240620115732914](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240620115732914.png)

配置CAN参数

* 开启主CAN配置
* 位时序配置

位时序顾名思义就是传输一个位的时序。位时序结构：同步段（SYNC_SEG）、时间段1(BS1)、时间段2(BS2)

![在这里插入图片描述](https://img-blog.csdnimg.cn/8b342558d67f460dbe3f02cf032d3e65.png)

将系统时间36M进行4分频，则36M/4=9M

位时序中同步段固定1Tq；STM32时间段1包含两部分：传播时间段和相位缓冲时间段1，可以分配11Tq；时间段2包含相位缓冲时间段2，可以分配6Tq。这样1位由18个Tq构成，则9M/18=500K

按照以上配置可以实现CAN 500K通信。

![image-20240620120232092](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240620120232092.png)



* 基本模式配置

![在这里插入图片描述](https://img-blog.csdnimg.cn/80f08aa92dac432d89250f34ce664a59.png)

自动重发数据：若使能，数据出错了可以重新发送数据

接收FIFO锁定模式：若使能，FIFO数据不可以重叠，更替

发送FIFO优先级：若关闭，就按照邮箱的优先级来发送数据；若使能，就按照自己设定的优先级发送

这里不需要直接全部disable

* CAN工作模式配置

模式选择：正常模式、静默模式、环回模式和环回静默模式

实验选用正常模式、环回模式测试CAN通信

* 中断模式配置
* 设置中断优先级
* 

## 发送机（STM32F405RGT6）CAN通信配置

## 双CAN配置及注意事项（STM32F406ZGT6）

🔗：[STM32CubeMX | STM32 F4系列HAL库使用双CAN配置及注意事项_stm32 hal库 can接口 标准帧配置-CSDN博客](https://blog.csdn.net/qq153471503/article/details/104167800)

对于本实验芯片，该单片机具有两个CAN接口，CAN1为主机CAN，CAN2为从机CAN，CAN2是和CAN1有关联的，要想使用CAN2必须先使能CAN1的时钟。

CAN外设是挂载在APB1_PCLK1时钟上的，APB1_PCLK1是42M，CAN的最大速率是1MHz，本实验配置为500kHz。波特率配置方法：

* CAN波特率 = APB1_PCLK1 / 分频 / (tq1 + tq2 + ss)

使能CAN接收中断

设置CAN的IO为上拉，否则HAL库函数MX_CAN_Init初始化会失败。（？）

相关配置代码：

```C

#define CAN1_FILTER_MODE_MASK_ENABLE 1	///< CAN1过滤器模式选择：=1：屏蔽位模式  =0：屏蔽列表模式
#define CAN2_FILTER_MODE_MASK_ENABLE 1  ///< CAN2过滤器模式选择：=1：屏蔽位模式  =0：屏蔽列表模式

#define CAN1_BASE_ID  0x10F00266		///< 主CAN过滤ID
#define CAN2_BASE_ID  0x10F0F126		///< 从CAN过滤ID

#define CAN1_FILTER_BANK  0             ///< 主CAN过滤器组编号
#define CAN2_FILTER_BANK  14            ///< 从CAN过滤器组编号

/// CAN过滤器寄存器位宽类型定义
typedef union
{
    __IO uint32_t value;
    struct
    {
        uint8_t REV : 1;			///< [0]    ：未使用
        uint8_t RTR : 1;			///< [1]    : RTR（数据帧或远程帧标志位）
        uint8_t IDE : 1;			///< [2]    : IDE（标准帧或扩展帧标志位）
        uint32_t EXID : 18;			///< [21:3] : 存放扩展帧ID
        uint16_t STID : 11;			///< [31:22]: 存放标准帧ID
    } Sub;
} CAN_FilterRegTypeDef;

// CAN_FMR寄存器位宽类型定义
typedef union 
{
	__IO uint32_t value;
	struct
	{
		uint8_t FINIT : 1;
		uint8_t RESERVER_0 : 7;
		uint8_t CAN2SB : 6;
		uint32_t RESERVER_1 : 18;
	}Sub;
}FMR_TypeDef;

/// 设置CAN1的过滤器（主CAN）
static void CAN1_Filter_Config(void)
{
	CAN_FilterTypeDef sFilterConfig;
    CAN_FilterRegTypeDef IDH = {0};
    CAN_FilterRegTypeDef IDL = {0};

	IDH.Sub.IDE  = 0;								// 标准帧
	IDH.Sub.STID = 0;								// 标准帧ID值
    IDH.Sub.EXID = (CAN1_BASE_ID >> 16) & 0xFFFF;	// 扩展帧高16位ID值
	
	IDL.Sub.IDE  = 1;								// 扩展帧
	IDL.Sub.STID = 0;								// 标准帧ID值
    IDL.Sub.EXID = (CAN1_BASE_ID & 0xFFFF);			// 扩展帧低16位ID值

	sFilterConfig.FilterBank           = CAN1_FILTER_BANK;								// 设置过滤器组编号
#if CAN1_FILTER_MODE_MASK_ENABLE
    sFilterConfig.FilterMode           = CAN_FILTERMODE_IDMASK;							// 屏蔽位模式
#else
	sFilterConfig.FilterMode           = CAN_FILTERMODE_IDLIST;							// 列表模式
#endif
    sFilterConfig.FilterScale          = CAN_FILTERSCALE_32BIT;							// 32位宽
    sFilterConfig.FilterIdHigh         = IDH.value;										// 标识符寄存器一ID高十六位，放入扩展帧位
    sFilterConfig.FilterIdLow          = IDL.value;										// 标识符寄存器一ID低十六位，放入扩展帧位
    sFilterConfig.FilterMaskIdHigh     = IDH.value;										// 标识符寄存器二ID高十六位，放入扩展帧位
    sFilterConfig.FilterMaskIdLow      = IDL.value;										// 标识符寄存器二ID低十六位，放入扩展帧位
    sFilterConfig.FilterFIFOAssignment = CAN_RX_FIFO0;									// 过滤器组关联到FIFO0
    sFilterConfig.FilterActivation     = ENABLE;										// 激活过滤器
    sFilterConfig.SlaveStartFilterBank = CAN2_FILTER_BANK;								// 设置CAN2的起始过滤器组（对于单CAN的CPU或从CAN此参数无效；对于双CAN的CPU此参数为从CAN的起始过滤器组编号）
    if (HAL_CAN_ConfigFilter(&hcan1, &sFilterConfig) != HAL_OK)
    {
        Error_Handler();
    }
	{
		FMR_TypeDef regval = {0};
		regval.value = hcan1.Instance->FMR;
		printf("------ CAN1:> FMR:0x%0X  CAN2SB:0x%X  \r\n", regval.value, regval.Sub.CAN2SB);
	}
}

/// 设置CAN2的过滤器（从CAN）
static void CAN2_Filter_Config(void)
{
	CAN_FilterTypeDef sFilterConfig;
    CAN_FilterRegTypeDef IDH = {0};
    CAN_FilterRegTypeDef IDL = {0};

	IDH.Sub.IDE  = 0;
	IDH.Sub.STID = 0;
    IDH.Sub.EXID = (CAN2_BASE_ID >> 16) & 0xFFFF;
	
	IDL.Sub.IDE  = 1;
	IDL.Sub.STID = 0;
    IDL.Sub.EXID = (CAN2_BASE_ID & 0xFFFF);

    sFilterConfig.FilterBank           = CAN2_FILTER_BANK;								// 设置过滤器组编号
#if CAN2_FILTER_MODE_MASK_ENABLE
    sFilterConfig.FilterMode           = CAN_FILTERMODE_IDMASK;							// 屏蔽位模式
#else
	sFilterConfig.FilterMode           = CAN_FILTERMODE_IDLIST;							// 列表模式
#endif
    sFilterConfig.FilterScale          = CAN_FILTERSCALE_32BIT;							// 32位宽
    sFilterConfig.FilterIdHigh         = IDH.value;										// 标识符寄存器一ID高十六位，放入扩展帧位
    sFilterConfig.FilterIdLow          = IDL.value;										// 标识符寄存器一ID低十六位，放入扩展帧位
    sFilterConfig.FilterMaskIdHigh     = IDH.value;										// 标识符寄存器二ID高十六位，放入扩展帧位
    sFilterConfig.FilterMaskIdLow      = IDL.value;										// 标识符寄存器二ID低十六位，放入扩展帧位
    sFilterConfig.FilterFIFOAssignment = CAN_RX_FIFO0;									// 过滤器组关联到FIFO0
    sFilterConfig.FilterActivation     = ENABLE;										// 激活过滤器
    sFilterConfig.SlaveStartFilterBank = 28;											// 无效
    if (HAL_CAN_ConfigFilter(&hcan2, &sFilterConfig) != HAL_OK)
    {
        Error_Handler();
    }
	{
		FMR_TypeDef regval = {0};
		regval.value = hcan2.Instance->FMR;
		printf("------ CAN2:> FMR:0x%0X  CAN2SB:0x%X  \r\n", regval.value, regval.Sub.CAN2SB);
	}
}

/// CAN初始化
void CAN_Init(void)
{
    MX_CAN1_Init();																		// 初始化CNA1
    CAN1_Filter_Config();																// 初始化CNA1过滤器
    HAL_CAN_Start(&hcan1);																// 启动CAN1
    HAL_CAN_ActivateNotification(&hcan1, CAN_IT_RX_FIFO0_MSG_PENDING);					// 激活CAN1 FIFO0

    MX_CAN2_Init();
    CAN2_Filter_Config();
    HAL_CAN_Start(&hcan2);
    HAL_CAN_ActivateNotification(&hcan2, CAN_IT_RX_FIFO0_MSG_PENDING);
}

/**
 * CAN数据传输
 * @param  buf    待发送的数据
 * @param  len    数据长度
 * @param  number CAN编号，=0：CAN1，=1：CAN2
 * @return        0：成功  other：失败
 */
uint8_t CAN_Transmit(const void* buf, uint32_t len, uint8_t number)
{
    uint32_t txmailbox = 0;
    uint32_t offset = 0;
    CAN_TxHeaderTypeDef hdr;

    hdr.IDE = CAN_ID_EXT;													// ID类型：扩展帧
    hdr.RTR = CAN_RTR_DATA;													// 帧类型：数据帧
    hdr.StdId = 0;															// 标准帧ID,最大11位，也就是0x7FF
    hdr.ExtId = number == 0 ? CAN1_BASE_ID : CAN2_BASE_ID;					// 扩展帧ID,最大29位，也就是0x1FFFFFFF
    hdr.TransmitGlobalTime = DISABLE;

    while (len != 0)
    {
        hdr.DLC = len > 8 ? 8 : len;			// 数据长度
        if (HAL_CAN_AddTxMessage(number == 0 ? &hcan1 : &hcan2, &hdr, ((uint8_t *)buf) + offset, &txmailbox) != HAL_OK)
            return 1;
        offset += hdr.DLC;
        len -= hdr.DLC;
    }
    return 0;
}

uint8_t CAN1_RX_STA = 0;		///< CAN1数据接收标志：[7]:数据 [6:0]:未使用
uint8_t CAN2_RX_STA = 0;		///< CAN2数据接收标志：[7]:数据 [6:0]:未使用

uint8_t CAN1_RX_BUF[8];			///< CAN1数据接收缓存
uint8_t CAN2_RX_BUF[8];			///< CAN2数据接收缓存

uint8_t CAN1_TX_BUF[8];			///< CAN1数据发送缓存
uint8_t CAN2_TX_BUF[8];			///< CAN2数据发送缓存

/**
 * CAN FIFO0 数据接收中断回调函数
 * @param hcan CAN句柄
 */
void HAL_CAN_RxFifo0MsgPendingCallback(CAN_HandleTypeDef *hcan)
{
    static CAN_RxHeaderTypeDef CAN_RX_HDR;

    // CAN1数据接收
    if (hcan->Instance == hcan1.Instance)
    {
        // 数据已经处理
        if ((CAN1_RX_STA & 0x80) == 0)
        {
            // 清空缓存
            memset(CAN1_RX_BUF, 0, 8);

            // 接收数据
            if (HAL_CAN_GetRxMessage(hcan, CAN_RX_FIFO0, &CAN_RX_HDR, CAN1_RX_BUF) == HAL_OK)		// 获得接收到的数据头和数据
            {
                CAN1_RX_STA |= 0x80;																// 标记接收到数据
                HAL_CAN_ActivateNotification(hcan, CAN_IT_RX_FIFO0_MSG_PENDING);					// 再次使能FIFO0接收中断
            }
        }
    }

    // CAN2数据接收
    else if (hcan->Instance == hcan2.Instance)
    {
        // 数据已经处理
        if ((CAN2_RX_STA & 0x80) == 0)
        {
            // 清空缓存
            memset(CAN2_RX_BUF, 0, 8);

            // 接收数据
            if (HAL_CAN_GetRxMessage(hcan, CAN_RX_FIFO0, &CAN_RX_HDR, CAN2_RX_BUF) == HAL_OK)		// 获得接收到的数据头和数据
            {
                CAN2_RX_STA |= 0x80;																// 标记接收到数据
                HAL_CAN_ActivateNotification(hcan, CAN_IT_RX_FIFO0_MSG_PENDING);					// 再次使能FIFO0接收中断
            }
        }
    }
}

///< CAN数据处理函数
inline void CAN_RecvHandler(void)
{
    // CAN1有数据收到
    if (CAN1_RX_STA & 0x80)
    {
		int i = 0;
		memcpy(CAN1_TX_BUF, CAN1_RX_BUF, sizeof(CAN1_RX_BUF));		// 拷贝出数据
		CAN1_RX_STA = 0;											// 重置CAN1接收状态
		for(i = 0; i != 8; i++)
		{
			printf("CAN1_TX_BUF[%d]:0x%X\r\n", i, CAN1_TX_BUF[i]);
		}
		printf("\r\n\r\n");
    }

    // CAN2有数据收到
    if (CAN2_RX_STA & 0x80)
    {
		int i = 0;
		memcpy(CAN2_TX_BUF, CAN2_RX_BUF, sizeof(CAN2_RX_BUF));		// 拷贝出数据
		CAN2_RX_STA = 0;											// 重置CAN1接收状态
		for(i = 0; i != 8; i++)
		{
			printf("CAN2_TX_BUF[%d]:0x%X\r\n", i, CAN2_TX_BUF[i]);
		}
		printf("\r\n\r\n");
    }
}


```



## CAN通信消息ID设置

第一个IMU：

![image-20240621093246388](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240621093246388.png)

第二个IMU：

![image-20240621093420492](C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240621093420492.png)

## 压力鞋垫标定

row1：100g：5000，200g：10000，500g：12000

## 宇树GO-M8010-6使用

🔗：[宇树科技 文档中心 (unitree.com)](https://support.unitree.com/home/zh/Motor_SDK_Dev_Guide/line_connection)

宇树科技目前所有生产的电机均采用RS485总线通信。

### RS485总线协议

RS485通讯可以理解为是一个半双工（收发不可同时进行）的串口通信链路，非隔离的RS485信号线缆一般是有3根：A/B/GND。

![img](https://doc-cdn.unitree.com/static/2023/12/28/7152569c05a34103813a01796c90d27b_834x280.png)

### 电机线路连接

RS485利用两线之间的电位差来传输数字电平。

GO-M8010-6电机最大支持一条总线上15个电机（ID 0~14），总线上不得有相同ID的电机，否则整条总线通讯都会异常。

为了将运动控制指令发送给宇树科技制造的关节电机，我们需要通过串口将指令下发。电机通过 RS-485 接口与上位机进行通信，固定波特率 (Baud Rate)为：**4Mbps**。

![img](https://doc-cdn.unitree.com/static/2023/12/21/c080832a36f14c558e54015aefce3c73_3319x1129.png)

如上图所示。提供给用户的接口使用C（XT30(2+2)线缆），连接至B（XT30(2+2)转接板），并通过D（GH1.25-3线缆）连接到A（485转USB模块）并连接到电脑上。

## 伺泰威GIM6010-8使用

🔗：官方使用手册：《GIM6010-8使用手册》

```python
odrv0.axis0.motor.config.current_lim = 30
```

上述指令将电流门限设置为30A。请注意，此电流门限是指Q轴电流，而不是电源电流。这个门限值直接限制了输出扭矩。对于6010-8，请不要将此门限设置超过50A

用户第一次使用微电机时，需要对电机以及编码器进行校准。在校准之前，请固定好电机，或用手握紧，输出轴空载，校准过程如下：

```PYTHON
odrv0.axis0.requested_state = AXIS_STATE_MOTOR_CALIBRATION
dump_errors(odrv0)
odrv0.axis0.requested_state = AXIS_STATE_ENCODER_OFFSET_CALIBRATION
dump_errors(odrv0)
odrv0.axis0.motor.config.pre_calibrated = 1
odrv0.axis0.encoder.config.pre_calibrated = 1
odrv0.save_configuration()
```

在任何参数修改过后，请务必存储，否则所做更改将在断电或重启后失效。存储参数后驱动器将重启。

```python
odrv0.save_configuration()
```

### 四种控制模式

6010-8支持位置模式、速度控制、力矩控制以及运动控制模式。

在位置控制模式中，支持滤波位置控制，梯形曲线位置控制，周期位置控制。

在速度控制模式中，支持直接速度控制，斜坡速度控制。

在力矩控制模式中，支持直接力矩控制，斜坡力矩控制。

### odrive库移植

🔗：[ODrive3.4固件（keil移植版）_odrive移植,odrive代码keil资源-CSDN文库](https://download.csdn.net/download/weixin_44793491/15727953?utm_medium=distribute.pc_relevant_download.none-task-download-2~default~baidujs~default-0-15727953-download-88779779.257^v16^pc_dl_relevant_base1_b&depth_1-utm_source=distribute.pc_relevant_download.none-task-download-2~default~baidujs~default-0.257^v16^pc_dl_relevant_base1_b&dest=https%3A%2F%2Fdownload.csdn.net%2Fdownload%2Fweixin_44793491%2F15727953&spm=1003.2020.3001.6616.3)



## STM32最小开发板绘制

### PCB布局

**看懂原理图**

* 把电路按照模拟电路和数字电路进行区分
* 把模拟/数字电路进行低速、中速以及高速进行区分
* 把电路中的一些发热器件、易干扰器件标注出来

**模块化布局**

* 模块化布局建立在看懂原理图的基础上
* 首先建立原理图与PCB的连接，然后从原理图中把各个模块的电路选中，最后把各个模块的电路捉取到各个区域进行区分
* 

对于并联电容的排布的要求：电流先流进大电容再流经小电容

起振电容要放在芯片和晶振之间

布线先从线比较多的地方开始

走线不允许锐角存在

晶振需要包地处理

线宽的最大宽度不能够超过焊盘的宽度

芯片焊盘出线不要从侧面出线

Shift+S可以看到导线的连接情况

对于单层板而言，导线走底层是备选方案，能不走底层就不走底层



## 电机PID控制

🔗：[使用stm32实现电机的PID控制_stm32pid控制电机-CSDN博客](https://blog.csdn.net/weixin_43811044/article/details/127956227)

## 基于STM32的ADC采样及各式滤波实现（HAL库，含VOFA+）

🔗：[基于STM32的ADC采样及各式滤波实现（HAL库，含VOFA+教程）_数据采集滤波算法stm32-CSDN博客](https://blog.csdn.net/black_sneak/article/details/129629485)

### VOFA+使用

VOFA+的数据协议引擎有3种：FireWater、JustFloat、RawData。每种数据协议引擎都有自己特殊的使用效果。

* FireWater协议是CSV风格的字符串流，直观简洁。但由于字符串解析消耗更多的运算资源（无论是在上位机还是下位机），建议仅在通道数量不多、发送频率不高的时候使用。

## RTC配置

🔗：[【STM32】RTC实时时钟，步骤超细详解，一文看懂RTC_rtc模块-CSDN博客](https://blog.csdn.net/as480133937/article/details/105026033?login=from_csdn)

🔗：[【STM32】HAL库 STM32CubeMX教程十三---RTC时钟_Z小旋-GitCode 开源社区 (csdn.net)](https://gitcode.csdn.net/65ea88e31a836825ed79435a.html?dp_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6NDUwODUzLCJleHAiOjE3MjM1MzcwNjgsImlhdCI6MTcyMjkzMjI2OCwidXNlcm5hbWUiOiJYSWFuaGwifQ.PkO4BCgq2MJfYU4V0QjLSOY4b56nkFWgm1FR68AK4oM)

RTC（Real Time Clock），实时时钟，是一个独立的定时器。RTC模块拥有一个连续计数的计数器，在相应的软件配置下，可以提供时钟日历的功能。修改计数器的值可以重新设置当前时间和日期。RTC还包含用于管理低功耗模式的自动唤醒单元。

**在断电情况下，RTC仍可以独立运行，只要芯片的备用电源一直供电，RTC上的时间会一直走**（如果没有备用电源，RTC将在电源断电时停止运行，并且其时间会丢失。当系统重新上电时，RTC需要重新初始化并重新设置时间。这意味着在这种情况下，你无法保证时间戳的连续性和准确性。如果应用对事件的连续性要求不高，则可以考虑不使用备用电源）。

RTC实质是一个掉电后还可以继续运行的定时器，从定时器的角度来看，相对于通用定时器TIM外设，它的功能十分简单，只有计时功能（也可以触发中断）。但其高级之处也就在于掉电后还可以正常运行。

## C板使用

🔗：[【RoboMaster】从零开始控制RM电机（2）-CAN通信原理及电调通信协议_can通讯 同步触发控制电机-CSDN博客](https://blog.csdn.net/weixin_54448108/article/details/125881138?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-4-125881138-blog-124350747.235^v43^pc_blog_bottom_relevance_base7&spm=1001.2101.3001.4242.3&utm_relevant_index=7)

## 斯巴拓力传感器使用

### 变送器数字标定教程

1. 当我们按住回车键2秒以上，当屏幕出现(CAL1)时松手，这时我们进入了砝码标定程序

2. 再按确认键，屏幕出现(DIU)，这是分度值设置，再按确认键，屏幕上的字符开始闪烁，我们按向上和向下键，调整到我们想要的分度值，调整好后，我们按确认键，保存并进入下一个参数设置
3. 这时屏幕显示(CAP)，表示设置最大量程，我们再按确认键进入修改状态，并把它修改为传感器的最大量程，可以在传感器的表面标签，或者信号线上的黄色标签找到这个参数。修改好后，我们按确认键，保存并切换到下一个参数设置
4. 此时，屏幕上显示(ZERO)，表示标定零点。这时，传感器要空载，并且不要有多余的震动。按确认键，此时屏幕显示当时零点数值，此零点数值是上次标定的参数，再按确认键，进入修改状态，当字符闪烁时，我们把它调为0，按确认键，保存零点并切换到下一个参数设置。
5. 屏幕上显示(SPRN)，表示进入标定增益，这时我们把准备好的砝码放在传感器上的正中间，如果是拉力传感器，砝码就吊在传感器下方受理点，并保持传感器和砝码静止。按确认键，屏幕上显示上次标定的值，再按确认键，进入修改状态，我们把屏幕数字修改为砝码重量。

# 元器件

## 芯片一脚

🔗：http://t.csdnimg.cn/XmrSc

有些芯片上有两个点，小的那个点就对应一脚

# STM32Cube高效开发教程

## STM32Cube开发方式

🔗：《轻松玩转STM32Cube》

我们把基于STM32Cube生态系统的开发方式称为STM32Cube开发方式，这种开发方式的主要特点如下。

* 使用STM32CubeMX对STM32器件的系统资源、外设和中间件进行图形化配置，生成STM32CubeIDE项目的外设初始化代码和项目框架
* 使用STM32CubeIDE在外设初始化代码和项目程序框架的基础上进一步添加用户功能代码，实现应用功能
* 在开发过程中，用户可以使用STM32CubeMX重新配置STM32器件，重新生成外设初始化代码，并且不影响用户自己编写的代码
* 如果有需要，用户可以使用STM32CubeMonitor进行变量监测
* STM32CubeProgrammer是STM32程序烧录工具，可以对片上flash及片外的存储器进行擦除和编程，支持ST-LINK调试接口以及UART/USBDFU bootloader接口

## CubeIDE使用

视频🔗：[【正点原子】手把手教你学STM32CubeIDE开发_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1Wp42127Cx/?spm_id_from=333.880.my_history.page.click&vd_source=ae7834082973f295d9d56373ae0e7e3e)

🔗：[FreeRTOS 从入门到精通3--千呼万唤始出来，你好世界 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/115010977)



## Cube Monitor使用

🔗：[STM32CubeMonitor 介绍（一）基本介绍 & 例程一：基本的数据采... (stmicroelectronics.cn)](https://shequ.stmicroelectronics.cn/thread-626119-1-1.html)

🔗：[STM32CubeMonitor 介绍（二）例程二：实时波形检测 (stmicroelectronics.cn)](https://shequ.stmicroelectronics.cn/forum.php?mod=viewthread&tid=626121)

🔗：[STM32CubeMonitor 介绍（三）例程三：利用公有云平台进行远程... (stmicroelectronics.cn)](https://shequ.stmicroelectronics.cn/forum.php?mod=viewthread&tid=626141)

STM32CubeMonitor有两种工作模式：设计模式和Dashboard模式。设计模式即是编辑模式，打开软件后默认是处于该模式下。在Dashboard模式下，我们可以看到设计模式下编辑的“流”运行的结果，看到我们之前设计的界面，通过这个界面去检测或者控制变量的值。

STM32CubeMonitor基于Node-RED，Node-RED是一个基于“流（Flow）”的开发工具。那么何为“流”?Node-RED提供了很多功能节点，这些节点可以分为输入节点，输出节点和功能节点。把这些节点连接起来就是一个”流”。多个“流”的组合，我们也把它叫做“流”。比如在设计模式下的标签页面我们也称作“流”，它里面实际会包含多个不同功能的单个“流”。

![st-img](https://shequ.stmicroelectronics.cn/data/attachment/forum/202007/27/163141uu1ale5sq1qqo51k.png)

上图是通过STM32CubeMonitor进行远程监测的连接示意图。如我们前面所说，将STM32开发板通过ST-LINK连接到本地电脑，STM32CubeMonitor可以在本地电脑（Host PC）上运行，同时也可以在其他的电脑，平板或手机上通过浏览器访问host PC的IP地址（端口号1880）打开STM32CubeMonitor的界面，进行编辑或者查看Dashboard(需要在同一个局域网）。

### 基本数据采集

🔗：[STM32CubeMonitor 介绍（一）基本介绍 & 例程一：基本的数据采... (stmicroelectronics.cn)](https://shequ.stmicroelectronics.cn/thread-626119-1-1.html)

在第一个例程中，MCU程序中定义了一个全局变量（current_var），该变量在设定好的最大值（var_max）与最小值（var_min）之间以步长1，连续变化。现在我们要用CubeMonitor去实时监测这三个变量，并且还要实时改变最大值和最小值的限值。

通过这个例子，我们将学会：

•    如何搭建一个基本的“流”

•    了解“流”节点之间传递消息的基本数据结构

•    调试节点的使用

•    如何保存及导入“流”

•    如何调整Dashboard布局

节点配置

* acq_out节点：定义或者选择一个ST-LINK配置（通信协议、频率等），打开或者关闭连接，向选择的ST-LINK发送命令等；
* acq_in节点：定义或者选择一个ST-LINK配置，并接收ST-LINK发来的数据；

在开始配置前，我们会发现这两个节点的右上方分别有一个红色的三角形和蓝色的圆点。红色的三角形表示该节点还未配置，蓝色的圆点表示该节点更新后还未部署。

下面进行myProbe_Out和myProbe_In这两个节点的配置：

在配置这两个节点前，先连接ST-link到PC。然后按照图中的步骤进行配置：

1.双击节点，打开编辑窗口，点击“ProbeConfig”编辑按钮

2.在下拉菜单中选择可用的ST-LINK（如果没有连接任何st-link，就会看到“No results found”）

3.点击Add，添加ST-Link

4.点击Done，完成配置，编辑窗口自动关闭

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240708175500514.png" alt="image-20240708175500514" style="zoom:50%;" />

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240708175518784.png" alt="image-20240708175518784" style="zoom:50%;" />

### 实时波形监测

🔗：[STM32CubeMonitor 介绍（二）例程二：实时波形检测 (stmicroelectronics.cn)](https://shequ.stmicroelectronics.cn/forum.php?mod=viewthread&tid=626121)

### 利用共有云平台进行远程数据监控

🔗：[STM32CubeMonitor 介绍（三）例程三：利用公有云平台进行远程... (stmicroelectronics.cn)](https://shequ.stmicroelectronics.cn/forum.php?mod=viewthread&tid=626141)



# GitHub

🔗：[Github入门教程，适合新手学习（非常详细）_github教程-CSDN博客](https://blog.csdn.net/black_sneak/article/details/139600633)

## 项目库创建

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240910115322417.png" alt="image-20240910115322417" style="zoom:50%;" />

在创建完库后，下面就要让自己的电脑克隆一个自己所创建的库，方便自己电脑上的代码同步到GitHub你所创建的库当中。为了实现，就需要安装一个软件Git Bash。

## GitBash



<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240910124050956.png" alt="image-20240910124050956" style="zoom:50%;" />

按路径进入 .ssh，里面存储的是两个 **ssh key** 的秘钥，***\*id_rsa.pub\**** 文件里面存储的是公钥，**id_rsa** 文件里存储的是私钥，不能告诉别人。**打开 id_rsa.pub 文件，复制里面的内容。**

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240910124521568.png" alt="image-20240910124521568" style="zoom:50%;" />

## 使用Git将代码提交到GitHub

该过程需要使用经常的接触的两个 Git 命令，包括：**`push`**和 **`pull`**

* `push`：该单词直译过来就是 “推” 的意思，如果我们本地的代码有了更新，为了保持本地与远程的代码同步，我们就需要把本地的代码推到远程的仓库，代码示例：

```
git push origin master
```

* `pull`：该单词直译过来就是 “拉” 的意思，如果我们远程仓库的代码有了更新，同样为了保持本地与远程的代码同步，我们就需要把远程的代码拉到本地，代码示例：

```
git pull origin master
```

### 克隆仓库

将我们的库克隆下来到本地电脑中，方便以后进行代码上传

点进仓库之后点击 Code，点击 ssh 会看到一串网址（http也可以），这个地址就是代码地址，git clone 命令会用的到

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240910125130763.png" alt="image-20240910125130763" style="zoom: 67%;" />

接下来我们就开始选择文件存储地方了，在本地电脑中找到存储文件的地方，然后右键选择`Git Bash Here`

在终端输入git clone 地址（这个地址就是刚刚库那个code上的代码地址）

<img src="C:\Users\harlab\AppData\Roaming\Typora\typora-user-images\image-20240922114343639.png" alt="image-20240922114343639" style="zoom: 67%;" />

然后在指定目录已经存在了我们的库文件

### 上传代码

假设在该文件夹下新建了一个文件

在这个文件夹里面右键git bash进终端，git add我们新增的文件

```
git add '文件夹名字或者文件名字'
```

之后输入然后 git commit -m “测试是否成功” 引号内的内容可以随意改动，这个语句的意思是 给你刚刚上传的文件一个备注，方便查找

```
git commit -m "test"
```

接着输入push指令：

```
git push origin main
```

## Git常用命令

![img](https://img-blog.csdnimg.cn/direct/f4f6f57e35a849dfaf24b2984e18dca2.png)

## 问题：使用 Git pull 失败的 “Couldn’t find remote ref xxx” 错误

🔗：[Git 使用 Git pull 失败的 “Couldn’t find remote ref xxx” 错误|极客教程 (geek-docs.com)](https://geek-docs.com/git/git-questions/30_git_fail_to_use_git_pull_couldnt_find_remote_ref_xxx.html)

当我们在使用 [ Git](https://geek-docs.com/git/git-questions/30_git_fail_to_use_git_pull_couldnt_find_remote_ref_xxx.html#) 进行代码管理时，有时会遇到使用 `git pull` 命令时出现 “Couldn’t find remote ref xxx” 错误的情况。这个错误提示通常表示 Git 在远程仓库中找不到指定的分支或引用。

出现这个错误的主要原因是：

1. 远程分支或引用不存在；
2. 本地分支和远程分支之间存在冲突；
3. Git配置中指定的远程仓库不正确。

接下来，我们将分别讨论这些原因，并提供相应的解决方案。

### 远程分支不存在

第一种情况可能发生在远程仓库被重命名、删除或者修改分支结构之后。

解决这个问题的方法是，首先确定远程分支或引用是否存在。可以通过使用以下命令查看远程分支的列表：

```
git branch -r
```

或者查看远程引用的列表：

```
git show-ref --heads
```

如果发现所需的分支或引用确实不存在，可以尝试更新远程仓库信息并重新拉取：

```
git remote update
git pull
```

这样通常可以更新本地Git仓库的远程分支信息，并解决找不到远程分支的错误。

## 问题：Please enter a commit message to explain why this merge is necessary

有时候直接在github仓库里面修改了文件并递交了commit，这时候再通过git bash push新文件就会弹出这个，可以不管直接下面3，4步，如果要输入解释的话就需要：

1. 按键盘字母i进入insert模式
2. 修改最上面那行黄色合并信息，可以不修改
3. 按键盘左上角ESC
4. 输入“:wq”，按回车即可

# VSCode配置

🔗：[在window下使用 VScode 搭建 ARM 开发环境—— 详细版_抛弃ide — 在window下使用vscode搭建arm开发环境-CSDN博客](https://blog.csdn.net/weixin_42328389/article/details/119823834)



# CLion



# 脑残操作

* 在使用一块新板子之前最好看一下板子的使用手册

* 通信芯片所要电压，如果电压过低芯片不工作

* 检查IO口是否冲突

* 任务都放在回调函数中，如果一些放在回调函数，一些放在主循环里面，可能串口会造成干扰

* 注意外部时钟源频率是多少，然后在CubeMX中的时钟树的HSE也要设置成对应的
* 检查时钟设置中的外部晶振频率是否正确，如果不正确直接把代码烧录进去会导致程序跑飞
* 
