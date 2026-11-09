# 刘家瑞 · Jiarui Liu

**机器人嵌入式开发 / 机器人电控 / 运动控制 / 机器人底层软件**
河北科技大学 · 电气工程及其自动化（本科，2025.09 – 2029.06 预计）

做机器人下位机：STM32 固件、电机驱动、通信协议、实时控制回路。
工程经验主要来自 ROBOCON 竞赛机器人——四舵轮底盘、排球机器人、六足机器人。

---

## 🛠️ Tech Stack

| 方向 | 技术 | 说明 |
|---|---|---|
| **嵌入式（主方向）** | STM32F407 / H743、C、HAL + CubeMX、FreeRTOS、Keil MDK / ARM GCC、DMA、PWM、外部中断、USB CDC、DMA + IDLE 不定长串口接收 | 主力 |
| **通信** | CAN（双总线并行、帧 ID 规划、电流帧打包、FIFO 分流）、RS485、UART、USB CDC；自定义帧协议（帧头 + 命令字 + 长度 + CRC16）、心跳看门狗与断连保护 | 主力 |
| **电机与控制** | M3508 / C620、M2006、VESC、RobStride（MIT 力位混合）、Unitree GoMotor、MG996R 舵机；串级 PID、位置 / 速度闭环、三轮全向与四舵轮运动学、IMU 航向闭环 | 主力 |
| **机器人软件** | Linux / Ubuntu、C++、ROS 2 Humble（colcon、自定义 msg / srv、launch、RViz、TF）、KDL、YAML、gtest | 使用中 |
| **工具链** | Git、VS Code、J-Link、Ozone、CMake | 日常 |
| **了解** | Gazebo、MuJoCo、ros2_control | 学习中 |

---

## 🤖 Featured Projects

### 1. 四舵轮全向底盘（BR 底盘）· 嵌入式电控（独立开发）
STM32F407 + FreeRTOS + 双 CAN；2 ms 控制周期三级嵌套闭环（轮速环 → 舵向位置环 → 偏航角速度环）；四舵轮逆解 + 90° 最优解轮 + cos³ 轮速补偿；USB CDC 上位机协议 v1.4（CRC16 + 1 ms 心跳 + 600 ms 无帧自动停车）。
`STM32F407` `FreeRTOS` `CAN ×2` `M2006/C620` `VESC` `Kinematics` `PID`
→ [项目说明](https://github.com/LjiaruiAT/robotics-embedded-portfolio/tree/main/projects/swerve-drive) · 代码 Private

### 2. ROBOCON 排球机器人 · 电机驱动 / 应用层
三全向轮力控底盘 + 双级弹射；负责 RobStride / VESC / Unitree GoMotor 三类电机驱动接入；RobStride MIT 力位混合驱动（扩展帧 ID 编码）；F407 主控 + H743 击球子板双板分工；`HAL_UARTEx_ReceiveToIdle_DMA` 解决遥控包粘包丢包。
`STM32F407/H743` `CAN` `RS485` `MIT Control` `DMA IDLE`
→ [项目说明](https://github.com/LjiaruiAT/robotics-embedded-portfolio/tree/main/projects/robocon-volleyball) · [volley_2027](https://github.com/LjiaruiAT/volley_2027) · [volleyball](https://github.com/LjiaruiAT/volleyball) · [volley_hit](https://github.com/LjiaruiAT/volley_hit) · [fire_stm32h7](https://github.com/LjiaruiAT/fire_stm32h7)

### 3. ROS 2 六足机器人 · 软件 / 电控 / 控制（个人项目）
ROS 2 Humble 工作区 6 个包；`/spider/cmd_vel` → 步态相位 → 六腿足端轨迹 → 单腿逆解（KDL，正解回代校验）→ 18 路舵机 → 42 字节串口帧；tripod / ripple / wave 三种步态；gtest 覆盖逆解、相位、轨迹与限位。
`ROS2 Humble` `C++` `KDL` `Leg IK` `Gait` `gtest` · **Status: 仿真完整 + 单腿实机验证通过，整机调试中**
→ [spider_upper](https://github.com/LjiaruiAT/spider_upper) · [spider_lower](https://github.com/LjiaruiAT/spider_lower) · [项目说明](https://github.com/LjiaruiAT/robotics-embedded-portfolio/tree/main/projects/hexapod)

### 4. 排球击球机器人 v1 · 底盘控制与机构时序
3 × M3508 + C620 全向轮底盘；JY61 陀螺仪打滑补偿（低通 + 滑移量提取 + 自适应 PID + 三级死区 + 按接地压力比分配）；6 路电磁阀分时驱动规避电流浪涌；200 ms 遥测超时保护。
`STM32F407` `CAN` `JY61` `IMU` `State Machine`
→ [volley_hit](https://github.com/LjiaruiAT/volley_hit) · [项目说明](https://github.com/LjiaruiAT/robotics-embedded-portfolio/tree/main/projects/robocon-volleyball)

### 5. 其他探索
- **排球视觉追踪**：参与视觉结果到机器人运动的对接与上下位机通信（开发中，代码 Private）
- **六轴机械臂**：运动控制与强化学习相关方法的学习与初步尝试（早期阶段）
- 六轴机械臂：[Arm_six](https://github.com/LjiaruiAT/Arm_six)

---

## 🏆 Awards

**第二十五届全国大学生机器人大赛 ROBOCON（2026）** · 河北科技大学 武林探秘-1-队

| 赛项 | 奖项 |
|---|---|
| "武林探秘"机器人挑战赛 + "九宫藏宝"技能赛 | **一等奖** |
| "武林探秘"机器人挑战赛 · 竞技赛 | 二等奖 |
| "武林探秘"机器人挑战赛 + "崇武探幽"技能赛 | 二等奖 |

> 获奖证书署名本人（刘家瑞）。竞赛为团队赛制，本人负责电控 / 嵌入式方向：下位机固件、电机驱动、通信协议与整机联调。

---

## 📚 Currently Learning
- 运动控制整定与系统辨识
- ROS 2 导航栈与 ros2_control
- 嵌入式 Linux
- 机器人动力学

---

## 🎯 Engineering Philosophy

Understand the whole chain — 从寄存器、外设、驱动，一直推到整机控制回路。

**Build it. Test it. Understand it. Improve it.**

---

## 📫 Contact

- Email：3499682469@qq.com
- GitHub：https://github.com/LjiaruiAT
- 现居：石家庄
- Portfolio：https://github.com/LjiaruiAT/robotics-embedded-portfolio
- 方向：机器人嵌入式 / 电控 / 运动控制 / 底层软件（实习 · 技术合作）
