HBM 

Overview

NoC的设计是可扩展的，由一系列的HNoC和VNoC路径组成，支持客户自定义组合。为了满足时序、速度和逻辑资源需求，硬件实现组件可以配置为不同的方式；垂直和水平的NoC是高速、高带宽设计专用集成的模块，不消耗PL资源；

NoC components：

- NMU: NoC master units
- NSU:  NoC slave units
- NPS:  NoC packet switches
- NIDB: NoC Inter-Die-Brige

NMU 是流量入口点；NSU 是流量出口点。所有的IP都是由NMU和NSU连接。NIDB 将两个超级逻辑区域 (SLR) 连接在一起，在die之间提供高带宽。NPS 是交叉开关，用于构建完整NoC网络。

Performance

OT: Outstanding Transactions 未完成的传输；

AXI ID（Transaction ID，事务 ID） 是 AXI 地址通道（AW/AR）和响应通道（W/R/B）中的关键字段（通常 4-16 位宽），其主要作用是标识和区分并发事务，以支持高性能的乱序（Out-of-Order）执行和多主设备场景

由于响应延迟是非零的，因此必须有多个 OT。事实上，所需的 OT 数量是从设备延迟的函数。如果从设备的延迟小于或等于主设备的最大 OT，则可以实现全吞吐量。

OT（Outstanding Transactions）管理：如之前讨论，ID 帮助跟踪多个未完成事务（OT），防止重叠。

每个HBM 栈有八个通道，每个通道有两个伪通道！每个伪通道位宽是64bit，一个完整的时钟周期内数据翻转两次（DDR）；

每个栈理论带宽：

64bits * 2 * 8 *1600*2= 409600MB/s

一共两个栈：总共409600*2=819200MB/s=819GB/s

用户侧：一个stack有32个HBM_NMU（256bits）端口，400M时钟下理论带宽：

256*32*400/8=409600MB/s



NoC HBM simulation

NoC和HBM控制器行为仿真：

- SystemVerilog(RTL in GUI)：sv model仿真用于性能分析（带宽和延迟）
- SystemC(TLM in GUI)： systemC model用于功能验证

使用sv model仿真的性能分析与跑在硬件板卡上的误差在+-5%以内；



test



- 芯片外设引脚约束（物理约束）
- 时钟约束（时序约束）
- 自动化流程（可选）

主要参考：UG 835, UG894




