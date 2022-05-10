# 工作汇总
window环境下使用vscode bash shell调试C语言
- 下载git并安装， 更新gcc，并将vscode默认终端设置为git bash（并修改git风格）
- 安装make命令插件（git自带为阉割版bash，不包含make），并设置环境变量
可参考：
1. windows下git_bash，make: command not found[^link1]
2. windows下使用vscode畅快的调试bash[^link2]

##  gitall 
gitall --info --version=<version> --dev  查看各个仓的信息
gitall --discard  --dev  删除各个仓的信息
gitall --sync --version=<version> --dev  同步各个仓的信息(不加version默认当前版本)

## makefile
make -f sim.makefile  <规则>  *******
make kill  同上规则   //关闭线程
## verdi
drive 谁赋值过来（等于双击）
load 给谁赋值

## 编译参数
make -ncrun TASTNAME=***** //只运行，不编译nc notcompile

## 仿真
仿真文件路径 tests/corei/system_test/* 有*.dump和*.verilog文件即可


## testbench 文件路径
源文件：PROJ_SRC_ROOT/soc_driver_ctest/SOC/testbench/tb_pad_defines/scm600_tb_pad_defines.vpp
生成文件：PROJ_SRC_ROOT/PROJ_NAME/testbench/tb_pad_defines.v


[^link1]:https://blog.csdn.net/IOT_victor/article/details/89330953
[^link2]:https://www.yisu.com/zixun/48750.html


蜂鸟debuger调试MCU
- 蜂鸟调试器[下载对应驱动](https://www.nucleisys.com/developboard.php)
- vivado扫描串口，烧bit(右键芯片，program device)
- 编译烧录调试
  > make SOC=ns DOWNLOAD=ilm
  > make SOC=ns DOWNLOAD=ilm upload
  > make SOC=ns DOWNLOAD=ilm debug

调试：
openocd连接：make SOC=demosoc run_openocd
gdb连接：make SOC=demosoc clean all run_gdb
或者openocd有问题
## ide调试流程
![ide](../pic/ide.png)
![ide](../pic/ide1.png)
![ide](../pic/ide2.png)
![ide](../pic/ide3.png)
![ide](../pic/ide4.png)

JLink调试MCU

PROJ_SRC_ROOT/PROJ_NAME
查看iomux ：soffice iomux_cfg.cvg

which 命令
脚本工具路径：/home/share/tools/share_env/usr/bin/

## 文件结构
路径：PROJ_SRC_ROOT/PROJ_NAME 
configs/ 配置文件 源文件soc_config.v
ctest.list 仿真文件汇总
soc-temp.yaml soc各个ip的基础属性
iomux_ls_cfg.csv iomux配置文件(ls低速)

# 问题
0. 配置环境变量NUCLEI_TOOL_ROOT=/mnt/d/work/linux_nuclei_tools，(wslPATH)（因为bash已经设置，可以不管）
   bash 使用的是window的环境变量不是Linux
   NUCLEI_TOOL_ROOT="/d/work/toolchain" (已配置到.bash_profile)

1. liblto_plugin.so: file too short
动态库提示file too short，说明你的库有问题。一般都是ln软链接设置错的问题。

> rm liblto_plugin.so  //删除源文件
> ln -s liblto_plugin.so.0.0.0 liblto_plugin.so  /生成新的软链接文件

2. riscv-nuclei-elf-gcc :Commond not found  环境变量没设置好，查看PATH

gitlab liuxiaohan@nucleisys.com  xl123456


# 计划
vscode调试环境搭建
vpp学习
python学习
verilog学习
**verdi学习**
[yaml了解](https://zhuanlan.zhihu.com/p/145173920)
i2c等协议学习


## pad 对应全过程
1. 找到pad号
2. PROJ_SRC_ROOT/PROJ_NAME/fpga/mcu200t/constrs/nuclei-master-xdc 约束文件找到对应的pad及连接管脚
3. 根据连接管脚号在Nuclei_MCU200T.pdf中找到对应的pad及连接管脚
4. 再根据对应连接找到对应单板
5. 在单板上找到对应的地方
example:
[iomuxcode](../pic/iomuxcode.png)
[v20](../pic/v20.png)
[gpio18](../pic/gpio18.png)
[j78_2](../pic/j78_2.png)