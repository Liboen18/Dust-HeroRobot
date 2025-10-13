---
### 修改日志
1.使用stm32cubemx添加can.c/.h，将bsp_can中的fdcan改成can形式以及去掉fdcan3
> 1. can_filter_mask_config函数需要检查
> 2. can.c仅使用stm32cubemx更改为50Kbps波特率
> 3. 附带添加Algorithm整个文件夹，以及Middlewares/ThirdParty/ARM/DSP/Inc/arm_math.h

2.添加supercap.cpp/h
> 使用stm32cubemx添加FreeRTOS_CMSIS_RTOS_V2
> 修改supercap.h中 #ifndef DEVICE_SUPERCAP_H_ 为 SUPERCAP_H_（头文件保护宏不匹配）

3.添加Interaction文件夹
> 注释了Init.cpp 69行can3初始化函数（f4只有can1、2）
> 注释了Robot.cpp 34行超级电容初始化函数（理由同上）
> 注释了app_gimbal.cpp 16 17行电机初始化函数（理由同上）

4.仅使用stm32cubemx添加can外设
> 未更改stm32cubemx自动生成的路径，考虑到后续需要使用cubemx配置其他外设

5.dvc_motor_cm.h
> 从dvc_motor_dm.h移植，仅将DM改成CM，其余未变
> app_gimbal.h同样

6.步兵dev编译会有个警告
> warning: Dust_InfantryRobotChassis.elf has a LOAD segment with RWX permissions
> 需要在STM32H723VGTX_FLASH.ID中的函数（）加上READONLY