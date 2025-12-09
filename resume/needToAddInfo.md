我自2023年11月入职沃尔沃. 我在沃尔沃主要负责的事项如下:
-2025年7月11

SPA3/GPA HI Integration

    ZC：Orin

    HI: Tc 397

集成工具开发

    stakeholder_build_template

        管理各SWC的配置

        生成ECUextract和.c .h框架代码

    yaml2arxml

        替代Davinci Developer

ECUExtract_Unflattened.arxml check

    Davinci Developer配置消错

    Davinci Configurator配置消错

SOME/IP服务配置和测试

    SOME/IP服务在Davinci Congifurator中的配置

    使用CANoe配合VN5650设备进行测试

    使用PuTTy访问Linux系统

    使用劳德巴赫进行断点调试Debug C代码

2025年8月至今:

    Java APP代码门禁pipeline架构设计,优化和实施:

        业务仓通过Git上传Gerrit的patchset触发Jenkins Job进行代码检查

        Jenkins Job 基于groovy脚本

        在groovy脚本中配合gradle的ktlint detekt进行静态代码检查

        使用主从Job的形式实现静态代码检查和Build的并发

        使用mongoDB数据库实现check result的分批记录和集中仲裁

        使用changelog展示相关Report和编译log

    CI-Pipeline脚本自动化测试系统架构设计,优化和实施:

        解决共享库的动态加载问题

        解决相同Job依据Trigger来源的不同拉取不同版本的pipeline脚本问题

        设计测试框架yaml,实现可配置的自动化测试触发

我接触过车载以太网SOME/IP相关配置 配置过Davinci COnfigurator中的SoAd SD和BswM相关部分， TSN我接触过EthTSyn的配置：The Ethernet
Time Synchronization module implements a protocol for time synchronization over Ethernet. It is developed according to AUTOSAR
specification which is based on IEEE802.1As ((g)PTP) with some modifications.
#Ethernet #TimeSync #AVB
#AUTOSAR， DDS没有在项目中实际接触过 但是了解过其原理