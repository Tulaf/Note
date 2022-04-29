1. 管脚复用iof I2C_Config()
2. 配置I2C_PRE寄存器 I2C_Init()
        > I2C peripheral clock configured & enabled（I2C工作时不允许修改时间配置）
        > 配置SETUP寄存器ENABLE I2C
        ![init](../doc/pic/initial.png)

3. 软件复位


USART_ctest开发流程

1. iomux_config 管脚复用
2. USART_StructInit
   > 波特率
   > 字长
   > 停止位1
   > 奇偶校验disen
   > TX\RX enable
   > 硬件流控
