# 张凯 - 个人能力与经验档案

---

## 一、职业概况

| 项目 | 内容 |
|------|------|
| **工作年限** | 5年汽车电子软件开发经验 |
| **当前职位** | 中央计算平台集成主管工程师 |
| **当前公司** | 沃尔沃汽车（亚太）投资控股有限公司 |
| **核心领域** | AUTOSAR CP架构、智能座舱MCU软件开发 |

---

## 二、核心技能矩阵

### 2.1 AUTOSAR开发能力

| 技能领域 | 具体能力 | 掌握程度 |
|----------|----------|----------|
| **SWC应用层开发** | Runnable实体设计、Data Type定义、Sender-Receiver/Client-Server接口配置、RTE接口连接和代码生成 | 精通 |
| **SWC模块开发** | 基于C语言的SWC模块开发（Auth安全认证、NvmManager存储管理）、基于MATLAB Stateflow的SWC开发（内灯模块） | 有经验 |
| **BSW基础软件配置** | SOME/IP相关模块（SoAd, SD, BswM, SomeIpTp, ComM, TcpIp, EthIf, PduR）、诊断模块（UDS/Dcm, DoIP） | 精通 |
| **软件架构设计** | SWC模块划分、RTE接口设计、OS时序规划、架构方案设计 | 精通 |

### 2.2 BSW模块配置经验

| 模块类别 | 具体模块 | 配置经验 |
|----------|----------|----------|
| **SOME/IP相关模块** | SoAd, SD, BswM, SomeIpTp, ComM, TcpIp, EthIf, PduR | 精通 |
| **诊断模块** | Dcm (UDS), DoIP, DEM | 精通 |

### 2.3 SOME/IP模块配置详情

| 模块 | 全称 | 主要配置内容 |
|------|------|--------------|
| **SoAd** | Socket Adapter | Socket连接配置（TCP/UDP）、端口绑定、消息路由 |
| **SD** | Service Discovery | 服务发布/订阅配置、服务实例、事件组 |
| **BswM** | Basic Software Mode Manager | SOME/IP模块状态机、模式切换规则 |
| **SomeIpTp** | SOME/IP Transport Protocol | 消息分段重组配置 |
| **ComM** | Communication Manager | 通信通道状态管理 |
| **TcpIp** | TCP/IP Stack | IP地址、子网掩码、网关配置 |
| **EthIf** | Ethernet Interface | 以太网接口配置 |
| **PduR** | PDU Router | PDU路由配置（连接SomeIpTp和其他模块） |

### 2.4 工具链能力

| 工具类别 | 工具名称 | 使用能力 |
|----------|----------|----------|
| **AUTOSAR工具** | Vector DaVinci Developer | 精通 |
| | Vector DaVinci Configurator | 精通 |
| | ETAS, EB (了解) | 了解 |
| **测试工具** | Vector CANoe | 精通 |
| | Vector vTESTstudio | 精通 |
| | VN5650以太网测试设备 | 有经验 |
| **调试工具** | Lauterbach Trace32 | 精通 |
| | iSYSTEM winIDEA | 精通 |
| **版本控制** | Git, Gerrit, Smart SVN | 精通 |
| **CI/CD工具** | Jenkins, Groovy, Gradle | 有经验 |

### 2.5 编程语言能力

| 语言 | 能力描述 |
|------|----------|
| **C** | SWC模块开发（Auth安全认证、NvmManager存储管理），有经验 |
| **Python** | 自动化工具开发（yaml2arxml、SWC配置管理、CAPL生成），精通 |
| **MATLAB Stateflow** | SWC应用层开发（内灯模块），有经验 |
| **Groovy** | Jenkins Pipeline脚本开发，有经验 |
| **Java/Kotlin** | 静态代码检查工具配置（ktlint, detekt），了解 |

---

## 三、项目经验详细

### 3.1 沃尔沃汽车 (2023年11月 - 至今)

#### SPA3/GPA 高性能计算平台集成

| 项目要素 | 详情 |
|----------|------|
| **项目名称** | SPA3/GPA HI Integration |
| **硬件平台** | ZC: NVIDIA Orin \| HI: Infineon Tc397 (Aurix) |
| **职位角色** | 智能座舱MCU集成负责人 |

**主要工作内容：**

#### (1) 集成工具开发
- **stakeholder_build_template**: 管理各SWC的配置，生成ECUextract和.c/.h框架代码
- **yaml2arxml**: 替代DaVinci Developer的自动化配置转换工具

#### (2) 配置消错与验证
- ECUExtract_Unflattened.arxml check
- DaVinci Developer配置消错
- DaVinci Configurator配置消错

#### (3) SOME/IP服务配置和测试
- SOME/IP服务在DaVinci Configurator中的配置（SoAd, SD, BswM）
- 使用CANoe配合VN5650设备进行以太网测试
- 使用PuTTY访问Linux系统
- 使用劳德巴赫进行断点调试Debug C代码

#### (4) 车载以太网配置
- **SoAd**: Socket Adapter配置
- **SD**: Service Discovery服务发现配置
- **BswM**: 模式管理器配置
- **EthTSyn**: 以太网时间同步模块（基于IEEE802.1AS/gPTP）

#### (5) CI/CD系统架构设计 (2025年8月至今)

**Java APP代码门禁Pipeline架构设计、优化和实施：**
- 业务仓通过Git上传Gerrit的patchset触发Jenkins Job进行代码检查
- Jenkins Job基于Groovy脚本
- 配合Gradle的ktlint、detekt进行静态代码检查
- 使用主从Job的形式实现静态代码检查和Build的并发
- 使用MongoDB数据库实现check result的分批记录和集中仲裁
- 使用changelog展示相关Report和编译log

**CI-Pipeline脚本自动化测试系统架构设计、优化和实施：**
- 解决共享库的动态加载问题
- 解决相同Job依据Trigger来源的不同拉取不同版本的pipeline脚本问题
- 设计测试框架yaml，实现可配置的自动化测试触发

---

### 3.2 科世达 (2020年12月 - 2023年11月)

#### 车身域控制器集成负责人

**核心职责：**
- 集成测试软硬件环境的搭建
- 编译软件、烧入硬件、集成测试
- 设计科世达产线终检程序
- 设计硬件所需EMC上位机和EMC测试软件
- 定位集成测试和系统测试出现的问题
- 软件放行给客户及后期维护

#### 具体项目经验

| 客户 | 项目 | 角色 | 时间 |
|------|------|------|------|
| **长城汽车** | 欧拉好猫系列KBCM | ASw软件架构负责人、集成开发负责人、诊断/IO/NVM模块开发 | 2022/02 - 2023/08 |
| **长城汽车** | 欧拉黑猫系列KBCM | 集成开发负责人、BLE/TBOX/VCU/ESCL认证模块开发 | 2021/01 - 2021/12 |
| **理想汽车** | 车和家系列KBCM | 集成开发负责人 | 2022/03 - 2022/10 |
| **江西五十铃** | PEPS无钥匙进入系统 | 集成开发负责人 | 2022/03 - 2023/03 |
| **江西五十铃** | ESCL电子转向柱锁 | 集成开发负责人 | 2022/03 - 2023/03 |
| **宇通客车** | KBCM车身控制器 | 内灯模块软件开发工程师 | 2022/08 - 2023/08 |

#### 软件架构负责人职责详情
- **SWC设计**: 根据软件架构原则划分SWC components
- **接口设计**: 根据软件功能规范和架构原则为不同SWC设计不同的接口
- **ARXML文档生成**: 在Developer中配置相关SWC和接口，将ARXML文件提供给软件工程师用于MATLAB开发
- **RTE生成**: 生成RTE保证接口传递有效性，确保编译通过

#### 自动化测试平台开发 (2023/01 - 2023/06)
- 利用Python基于客户CAN/LIN/IO Matrix生成CANoe CAPL脚本和vTESTstudio配置文件
- 构建vTESTstudio自动化测试工程
- 基于客户功能规范编写自动化测试用例
- 将自动化测试用例导入到CANoe中进行自动化测试

---

## 四、通信协议经验

| 协议 | 经验描述 |
|------|----------|
| **CAN** | 总线通信开发应用，有经验 |
| **LIN** | 总线通信开发应用，有经验 |
| **UDS** | 诊断协议配置（Dcm模块），精通 |
| **DoIP** | 以太网诊断协议配置，精通 |
| **NM** | 网络管理协议，有经验 |
| **SOME/IP** | 服务配置和测试，精通 |
| **TSN (gPTP)** | EthTSyn时间同步配置，有经验 |
| **DDS** | 了解原理，无项目经验 |

---

## 五、教育背景

| 学校 | 学位 | 专业 | 时间 |
|------|------|------|------|
| **德国卡尔斯鲁厄理工学院 (KIT)** | 工学硕士 | 机电一体化及信息技术 | 2017/04 - 2020/10 |
| **河北工业大学 (211)** | 工学学士 | 机械设计制造及其自动化 | 2012/09 - 2016/07 |

**硕士深化方向：**
- 工业自动化
- 机器人技术

**毕业设计：**
- 硕士：基于Python和深度学习的动态眼球追踪系统数据质量优化
- 本科：人体工程学自动调节座椅（优秀毕业设计）

---

## 六、语言能力

| 语言 | 水平 |
|------|------|
| **英语** | 雅思 6.5 |
| **德语** | TestDaf 16 / C1 |
| **中文** | 母语 |

---

## 七、荣誉与特殊经历

- 科世达2022年度优秀员工
- 科世达AE电子开发部颁奖大会(2022)及年会(2023)主持人
- 上海防疫期间驻守公司保障项目交付

---

*最后更新: 2025年*
