## CPU基础知识
- 处理器==CPU
  一个完整的Soc，包含了处理器内核和其他外设和储存器，如蜂鸟E203Soc
- 处理器核==Core
  处理器内部最核心的部位，如蜂鸟E203Core

RICSC-V特点：
开放性，先进性，简洁性，模块化，扩展性


## JLINK
JTAG(Joint Test Action Group ，联合测试行动小组 ) 是一种国际标准测试协议

MCU J16 pin顺序
   1 MCU_TCK     UART0_TX 2
   3 MCU_TDO     VCC3V3   4
   5 MCU_TMS     RST      6
   7 DIR         UART0_RX 8
   9 MCU_TDI     GND      10


> TMS——测试模式选择 test mode select
> TCK——时钟
> TDI——数据输入
> TDO——数据输出
> TRST——测试复位，输入引脚，低电平有效


## 各类缩写
接入UART_TX和UART_RX即可串口显示结果打印

ULP MCU:Ultra-Low Power MCU超低功耗MCU

NMSIS:  SIS software interface standard
ILM:
pin:引脚
IO pad即芯片输入输出的管腿，是一个芯片管脚处理模块，即可以将芯片管脚的信号经过处理送给芯片内部，又可以将芯片内部输出的信号经过处理送到芯片管脚。输入信号处理包含时钟信号，复位信号等，输出信号包含观察时钟、中断等。IO pad模块可以控制输入输出信号的电平、驱动电流等，同时还包含了检测功能。

AHB:Advanced High Performance Bus
APB:Advanced Peripheral Bus

MOFF是Most-Off的简称，即芯片中除了Always-On Domain之外的所有其他主体部分

MSB是Most Significant Bit的缩写，指最高有效位
LSB:least significant bit，中文义最低有效位。
SPEC （软件规格说明书）Software Requirement Specification
USART通用异步收发传输器 Universal  Synchronous/Asynchronous Receiver/Transmitter

fsdb：Fast Signal Database 

ilm：指令储存器
dlm：数据储存器 
POR(Power-On Reset)为单片机的上电复位
LDO即low dropout regulator，是一种低压差线性稳压器
PVD(Programmable Voltage Detector)，即可编程电压监测器。应用于STM32ARM芯片中，作用是监视供电电压，在供电电压下降到给定的阀值以下时，产生一个中断，通知软件做紧急处理。


VCC：C=circuit 表示电路的意思, 即接入电路的电压；
VDD：D=device 表示器件的意思, 即器件内部的工作电压；
VSS：S=series 表示公共连接的意思，通常指电路公共接地端电压；
VEE：负电压供电；
VPP：编程/擦除电压。

vdd,英文全称为Virtual Device Driver(虚拟设备驱动)或Voltage Drain Drain(漏极电源电压),用作虚拟设备驱动时,可以看作为某一芯片内部的工作电压;用作漏极电源电压时,是指用于MOS晶体管电路,一般是指正电源;
vcc,英文全称为Voltage To Current Converter(电路电压)或Voltage Collector Collector (集电极电源电压),用作电路电压时,表示接入电路的电压;用作集电极电源电压,一般用于双极性晶体管,是晶体管的正电源;此外,vcc中的c还可以解读为circuit(电路),同样表示电路电压.所以vdd, vcc出自电路级，但是沿用到了系统级。例如说给PA供电，统一由VDD（来自电源）去供，然后在芯片内部再分成vdd（给drain）和vcc(给collector)。
vss的话，系统工程师和电路工程师也都能达成一致。前者知道是ground，后者知道接source，电路上source也一般接ground。


四个时钟源，具体为HSE(高速外部时钟)、LSE(低速外部时钟)、HSI(高速内部时钟)、LSI(低速内部时钟)。其中，HSE由外部晶振提供，一般作为STM32主时钟；内部时钟（HSI&&LSI）均由内部RC振荡器产生，HSI一般为8MHz，STM32启动时默认使用HSI；LSI主要给看门狗提供时钟源，一般是40KHz；LSE一般给RTC模块（实时时钟）提供时钟源，频率为32.768KHz。


PLL(Phase Locked Loop)： 为锁相回路或锁相环，用来统一整合时钟信号，使高频器件正常工作，如内存的存取资料等。PLL用于振荡器中的反馈技术。 许多电子设备要正常工作，通常需要外部的输入信号与内部的振荡信号同步。一般的晶振由于工艺与成本原因，做不到很高的频率，而在需要高频应用时，由相应的器件VCO，实现转成高频，但并不稳定，故利用锁相环路就可以实现稳定且高频的时钟信号。

AON always-on clock：AON是Always-on clock的缩写，是一种常驻的时钟，可以用来提供系统的时钟，也可以用来提供外部设备的时钟。


WFI(Wait for interrupt)
WFE(Wait for event)
一个是中断（int）唤醒，一个是事件（event）唤醒

BKP:
   备份寄存器是42个16位的寄存器，可用来存储84个字节的用户应用程序数据。他们处在备份域里，当VDD电源被切断，他们仍然由VBAT维持供电。当系统在待机模式下被唤醒，或系统复位或电源复位时，他们也不会被复位。

HART(Highway Addressable Remote Transducer)，可寻址远程传感器高速通道的开放通信协议

POR 上电复位 (Power On Reset)：复位后，系统进入待机模式，等待外部中断唤醒。
PDR 掉电复位  (Power Down Reset)：复位后，系统进入待机模式，等待外部中断唤醒。
当电压低于阈值VPOR或者VPDR时，自动保持复位状态

PUDC：Pull-Up During Configuration (bar)
> 配置期间的上拉 (bar) 低电平有效 PUDC_B 输入在上电后和配置期间启用 SelectIO 引脚上的内部上拉电阻。
> 当PUDC_B 为低电平时，每个SelectIO 引脚上启用内部上拉电阻。
> 当PUDC_B 为高电平时，每个SelectIO 引脚上的内部上拉电阻被禁用。
> PUDC_B 必须直接连接，或者通过 ≤ 1kΩ 连接到 VCCO_14 或 GND。
> 警告！在配置之前和配置期间不要让该引脚悬空。

PVD(Programmable Voltage Detector)可编程电压检测器，当电压低于阈值时，自动唤醒。

pulse 脉冲

CSR，全称为：Control and Status Register “指令指针寄存器”，“标志寄存器”，“机器状态字”，“程序计数器”等等，各种处理器/微机上的叫法有点差别，而且控制的功能也不一定相同，但都是用于控制处理器的操作。大多数这类寄存器对用户是不可见的。操作系统用CSR来区分每个设备。

prescaler预制分频器

setup time是指在时钟有效沿（下图为上升沿）之前，数据输入端信号必须保持稳定的最短时间。
hold time是指在时钟有效沿（下图为上升沿）之后，数据输入端信号必须保持稳定的最短时间。hold time时序检查确保新数据不会在触发器稳定输出初始数据之前过早到达D端而覆盖其初始数据。


总线仲裁？
多个主设备同时竞争主线控制权时，以某种方式选择一个主设备优先获得总线控制权称为总线仲裁。
为什么需要总线仲裁？
为解决多个主设备同时竞争总线控制权的问题，应当采用总线仲裁部件，以某种方式选择一个主设备优先获得总线控制权。只有获得了总线控制权的设备，才能开始传送数据


UPF Unified Power Format (UPF) 

XIP 是WINCE XIP KERNEL，是CE核心部分，为eXecute In Place的缩写，在微软的CE定义中，这块区域存放的是以非压缩格式存放，不需加载，由Bootloader直接调用执行的代码。

PADMA: Peripheral ** Direct Memory Access


AMBA (Advanced Microcontroller Bus Architecture) 高级微处理器总线架构
定义了高性能嵌入式微控制器的通信标准，可以将RISC处理器（精简指令集处理器）集成在其他IP芯核和外设中，它是有效连接IP核的“数字胶”，并且是ARM复用策略的重要组件；它不是芯片与外设之间的接口，而是ARM内核与芯片上其他元件进行通信的接口。比如Xilinx公司的Zynq芯片，就是ARM与FPGA之间的连接通路 .主要包括：
AHB (Advanced High-performance Bus) 高级高性能总线
ASB (Advanced System Bus) 高级系统总线----用的很少
APB (Advanced Peripheral Bus) 高级外围总线
AXI (Advanced eXtensible Interface) 高级可拓展接口
这些内容加起来就定义出一套为了高性能SoC而设计的片上通信的标准；
AHB主要是针对高效率、高频宽及快速系统模块所设计的总线，它可以连接如微处理器、芯片上或芯片外的内存模块和DMA等高效率模块；
APB主要用在低速且低功率的外围，可针对外围设备作功率消耗及复杂接口的最佳化；APB在AHB和低带宽的外围设备之间提供了通信的桥梁，所以APB是AHB或ASB的二级拓展总线 ；
AXI：高速度、高带宽，管道化互联，单向通道，只需要首地址，读写并行，支持乱序，支持非对齐操作，有效支持初始延迟较高的外设，连线非常多；

NMI(NonMaskableInterrupt)

UPF: Unified Power Format
PPA: Porformance power Architecture(Area) 芯片三个指标