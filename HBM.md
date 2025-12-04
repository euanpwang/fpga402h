HBM 

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


