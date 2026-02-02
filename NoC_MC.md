# NoC DDR Memory Controller

The integrated DDR Memory Controllers (DDRMCs) support both DDR4 and LPDDR4/4X memory interfaces。

> VCK 190 DDR4 & LPDDR4类型：DIMM、LPDDR4 Component

![Screenshot 2026-02-02 at 23.43.07](/Users/yunpengwang/Project/fpga402h/assets/Screenshot 2026-02-02 at 23.43.07.png)

DDR控制器接口包含四个专用的NSU控制器，DDR控制器使用NoC IP向导进行配置。

> [!IMPORTANT]
>
> NoC结构支持多个物理DDR控制器（两个或四个）交错控制！NMU 处理 DDR 内存控制器交错所需的切割和排序。



![image-20260203000114918](/Users/yunpengwang/Project/fpga402h/assets/image-20260203000114918.png)

![Screenshot 2026-02-03 at 00.01.34](/Users/yunpengwang/Project/fpga402h/assets/Screenshot 2026-02-03 at 00.01.34.png)

## DDR 控制器结构

![image-20260203000703217](/Users/yunpengwang/Project/fpga402h/assets/image-20260203000703217.png)

如上图所示：有四个NoC Slave接口可以直接访问DDR控制器。控制器可以配置为两个独立的存储通道，每个通道的数据位宽为 32 位。

> The VCK190 board, for example, uses one of these controllers for DDR4 memory running at 3200 MT/s, and two controllers for LPDDR4 memory running at 3933 MT/s. Each of these LPDDR4 interfaces is configured as 2x32, for a total of four independent 32-bit channels. 

> [!CAUTION]
>
> 也即：VCK 190使用一个控制器作为DDR 控制器，两个控制器作为LPDDR控制器；芯片本身有四个内存控制器，但vck190评估板只使用了三个！！！

