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


NMSIS: nuclei mcu software interface standard  
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

verification 前端验证
validation   硅后(silicon)验证

DUT （Design under Test）
> simulation
> checkers
> coverage
DUV（Design under Verification）

kickoff 启动
milestone 里程碑

Fabless指的只从事芯片设计与销售，不从事生产的公司，这样的企业被成为“无厂化企业”，手机厂商中的华为、苹果和小米，还有高通和联发科，都属于 Fabless

IDM 就是指既能够自行设计、也能够自行生产的芯片厂商，世界上有这种能力的不多，我们熟知的只有三星和英特尔。

Foundry 是能够自行完成芯片制造，但是没有设计能力的厂商，就是我们所熟知的代工厂。


FPGA（Field Programmable Gate Array）是在PAL （可编程阵列逻辑）、GAL（通用阵列逻辑）等可编程器件的基础上进一步发展的产物。它是作为专用集成电路（ASIC）领域中的一种半定制电路而出现的，既解决了定制电路的不足，又克服了原有可编程器件门电路数有限的缺点。

ASIC(Application Specific Integrated Circuit)即专用集成电路，是指应特定用户要求和特定电子系统的需要而设计、制造的集成电路。 用CPLD（复杂可编程逻辑器件）和 FPGA（现场可编程逻辑门阵列）来进行ASIC设计是最为流行的方式之一，它们的共性是都具有用户现场可编程特性，都支持边界扫描技术，但两者在集成度、速度以及编程方式上具有各自的特点。

barematel 裸机 （bare metal）

block 阻塞

PLIC  external interrupts 
在riscv中一共定义了三种状态中断，对于hart层面，hart包含local中断源和global中断源。而local中断只有Timer和Software中断两种，而global中断则称为external interrupts。只有global中断源可以被PLIC core响应，通常为I/O device。

eclic enhanced CORE LOCAL INTERRUPT  增强的内核中断控制器

一般来说，timer和software是通过CLINT(CORE LOCAL INTERRUPT)，而外部中断通过PLIC处理。

UT = Unit Test 单元测试
IT = System Integration Test 集成测试
ST = System Test 系统测试
UAT = User Acceptance Test 用户接受测试(俗称:验收测试)


spyglass 早期检查 （小型望远镜）

meeting minutes 会议纪要

signoff，签发。
后端所说的signoff，是指将设计数据交给芯片制造厂商生产之前，对设计数据进行复检，确认设计数据达到交付标准，这些检查和确认统称为signoff。

JEDEC 联合电子设备工程委员会（Joint Electron Device Engineering Council，JEDEC）.1999年，JEDEC独立成为行业协会，抛弃了原来名称中缩写的含义，目前的名称为JEDEC固态技术协会（JEDEC Solid State Technology Association）

SMP: Symmetrical Multi-Processor  
AMP: Asymmetrical Multi-Processor 异步多处理器

spi:serial peripheral interface 串行外设接口
Standard SPI、Dual SPI和Queued SPI三种协议接口，分别对应3-wire, 4-wire, 6-wire 

MISO（ Master Input Slave Output）：主设备数据输入，从设备数据输出；
MOSI（Master Output Slave Input）：主设备数据输出，从设备数据输入；
SCLK（Serial Clock）：时钟信号，由主设备产生；
CS/SS（Chip Select/Slave Select）：从设备使能信号，由主设备控制，一主多从时，CS/SS是从芯片是否被主芯片选中的控制信号，只有片选信号为预先规定的使能信号时（高电位或低电位），主芯片对此从芯片的操作才有效。


XIP eXecute In Place 就地执行
时钟频率
时钟极性 CKP(cpol) Clock Polarity       CPOL=0 低电平为IDLE CPOL=1 高电平为idle
时钟相位 CKE(cpha) Clock Phase (Edge)   CPHA=0 第一个跳变采样点为时钟边沿 CPHA=1 第二个跳变采样点为时钟边沿

(1) BK1_nCS：片选输出（低电平有效），适用于 FLASH 1。如果 QSPI 始终在双闪存模式下工作，则其也可用于 FLASH 2从设备选择信号线。QSPI通讯以BK1_nCS线置低电平为开始信号，以BK1_nCS线被拉高作为结束信号。
(2) CLK：时钟输出，适用于两个存储器，用于通讯数据同步。它由通讯主机产生，决定了通讯的速率，不同的设备支持的最高时钟频率不一样，如STM32的QSPI时钟频率最大为fpclk/2，两个设备之间通讯时，通讯速率受限于低速设备。
(3) BK1_IO0：在双线 / 四线模式中为双向 IO，单线模式中为串行输出，适用于FLASH 1。
(4) BK1_IO1：在双线 / 四线模式中为双向 IO，单线模式中为串行输入，适用于FLASH 1。
(5) BK1_IO2：在四线模式中为双向 IO，适用于 FLASH 1。
(6) BK1_IO3：在四线模式中为双向 IO，适用于 FLASH 1。

FAT:File Allocation Table 文档分配表
NTFS (New Technology File System)
Windows NT 操作环境和 Windows NT 高级服务器网络操作系统环境的文件系统

磁盘容量 = 盘面数x柱面数x扇面数x512字节

扇区：512 bytes 最小存储单元
簇---文件管理的最小单元

FAT32分区空间大小
分区空间大小        每个簇的扇区             簇空间大小
    <8GB                8                    4k
    8-16GB              16                  8k
    16-32GB             32                  16k
    32GB                64                  32k
