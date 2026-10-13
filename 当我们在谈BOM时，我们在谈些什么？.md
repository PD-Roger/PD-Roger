---
title: "当我们在谈BOM时，我们在谈些什么？"
author: "Roger Yang"
account: "Roger硬件产品开发实战"
date: "2025-07-04 13:05"
url: "https://mp.weixin.qq.com/s/REbhBhM78Txq9v_wDob9IA"
original: true
digest: "不少企业在推ERP、做精益、搞数智化的过程中，常常被一个基础但关键的问题绊住脚：BOM到底有几种？能不能只用一张？"
---

# 当我们在谈BOM时，我们在谈些什么？

> 原创 · Roger Yang · Roger硬件产品开发实战 · 2025-07-04 13:05

> [原文链接](https://mp.weixin.qq.com/s/REbhBhM78Txq9v_wDob9IA)

**不少企业在推ERP****、做精益、搞数智化的过程中，常常被一个基础但关键的问题绊住脚：BOM****到底有几种？能不能只用一张？**

**我们今天不讲太多概念，也不搞专业名词廛解，就用一篇实打实的干货，厘清BOM****的三种典型形态——****工程BOM****（EBOM****）、制造BOM****（MBOM****）、成本BOM****（CBOM****），以及它们在系统中的定位和配合方式。**

**一、BOM****不是只有一张清单**

**BOM****（Bill of Materials****，物料清单）的基本作用，是描述一个产品所需的全部零部件、组件、材料，以及它们之间的结构关系。**

**但在实际业务中，不同的角色对产品“****结构”****的理解侧重点不同，因此就衍生出了多个版本的BOM****：**

-   设计人员关心
    
    “产品组成是什么” → 工程BOM（EBOM）
    
-   工艺人员关心
    
    “怎么生产最合理” → 制造BOM（MBOM）
    
-   财务人员关心
    
    “成本构成和盈利能力” → 成本BOM（CBOM）
    
-     

**这三种BOM****有明确分工，不能混用，否则系统数据会严重错位，计划排不出、采购下错单、财务算不准利润，都会变成常态问题。**

**二、工程BOM****（EBOM****）：设计视角的产品结构**

**EBOM****（Engineering BOM****）是由设计/****研发部门生成，用于描述产品从设计角度的组成结构。**

**EBOM** **的特点：**

-   **以产品设计结构树为核心；**
-   **通常生成于CAD/PDM/PLM****系统；**
-   **每个组件关联图纸、型号、材质、技术参数等；**
-   **不包含工艺路径、替代料、工时等制造信息。**

**举例：**

**设计一款智能门锁，EBOM****中会包括：**

-   **控制主板（含MCU****、Wi-Fi****模块）**
-   **传动机构（伺服电机+****齿轮组）**
-   **指纹识别模组**
-   **面板（CNC****加工铝合金+****涂装）**
-   **电池仓、螺钉、线材等**

**EBOM** **是设计变更、版本控制、标准件管理等的基础，但不能直接驱动制造系统，因为它缺少工序、装配、路径等信息。**

**三、制造BOM****（MBOM****）：生产视角的装配方案**

**MBOM****（Manufacturing BOM****）是制造/****工艺部门基于EBOM****结构扩展生成的，是实际指导生产的清单。**

**MBOM** **的特点：**

-   **包含****工序、工艺路线、工位编号****等信息；**
-   **可能存在****替代料、并行工艺路径；**
-   **多用于ERP****系统、MES****系统****中的排产与投料；**
-   **支撑MRP****（物料需求计划）、APS****（高级计划排程）等功能。**

**举例说明：**

**仍以智能门锁为例，MBOM****会将“****控制主板”****拆解为：**

-   **SMT****装配工序（焊接IC****、电阻、电容等）**
-   **插装工序（手动焊接接插件）**
-   **功能测试工序**
-   **包装前组装节点**

**这张BOM****会被用于：**

-   **下工单（Production Order****）**
-   **配置投料清单（Pick List****）**
-   **定义物料领用节点**
-   **设置返工流程路径**
-   

**四、成本BOM****（CBOM****）：财务视角的核算模型**

**CBOM****（Costing BOM****）****是在制造路径明确后，由财务部门负责生成，用于核算单位成本、分析盈利能力。**

**CBOM****的构成通常包括：**

-   **材料成本（按标准价格或实时采购价）**
-   **加工费（人工工时 ×** **工时费率）**
-   **制造费用（折旧、能耗、检验等分摊）**
-   **税费、运输费、损耗率等附加项**

**CBOM****不关注装配细节，仅以MBOM****结构为基础，合并各种费用因素得出产品单位成本。**

**实际作用：**

-   **新品定价评估；**
-   **产品毛利计算；**
-   **成本波动监控（如铜价上涨对PCBA****的影响）；**
-   **多品种配置比价分析（Cost Roll-up****）**

**五、三种BOM****如何在系统中协同？**

**为了实现高效的数据闭环，三种BOM****应遵循“****一个源头、逐层衍生”****的架构：**

研发设计 → EBOM（在PLM系统中维护）

↓

工艺制造 → MBOM（在ERP或MES中配置）

↓

成本核算 → CBOM（由财务模块生成）

**各部门分别维护自己的BOM****版本，并在系统中建立映射与更新机制。比如：**

-   **设计变更后，PLM****系统自动生成EBOM****新版本，通知工艺更新MBOM****；**
-   **MBOM****结构调整，自动触发CBOM****重新估算成本；**
-   **CBOM****中可以进行不同BOM****版本的比价分析。**
-   

**六、总结建议**

1.  **不要把BOM****当“****万能表格”****用，三种版本各有职责。**
2.  **PLM****、ERP****、MES****、财务系统之间必须数据打通，形成闭环。**
3.  **设置BOM****变更审批流程，明确版本生效时间与责任人。**
4.  **定期开展BOM****审计与清洗，排查系统冗余与逻辑冲突。**

**写在最后**

**BOM****看似基础，实则牵动整个产品生命周期。没有一套科学清晰的BOM****管理体系，ERP****系统再先进，也只能是“****高配跑低效”****。**

**所以，BOM****的第一步，不是填表，而是厘清业务角色，重构信息逻辑。**

**如果你正准备做智能制造、引入MES****或APS****，那就先问自己一句：**

**我们的三张BOM****，是不是还在混用？**

**往期精彩文章：**

**[产品最核心的竞争力来源于成本----硬件研发老司机真实经历 × 成本优化方法论 × 戳心反思× 干货爆棚](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247485072&idx=1&sn=bf12d9aa5d929287f0df5cf9577c9c3e&scene=21#wechat_redirect)**

**[一个长度尺寸引发的生产线风暴——工程总监的灵魂发飙](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247485065&idx=1&sn=a54dc28d04d43993b480b481e42666d2&scene=21#wechat_redirect)**

**[KISS原则在DFMA中的运用](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247485039&idx=1&sn=dfa6a7708c69c7988d9e0d8223b6461a&scene=21#wechat_redirect)**

**[那些年工作时遇到的奇葩经历——每个人每天都在翻越不同的山，但终究成为自己](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247484994&idx=1&sn=c68e5d728874cf54cc3810e05571001b&scene=21#wechat_redirect)**

**[产品设计师需要掌握的材料知识——不懂材料的设计师，就像拿着螺丝刀修主板](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247484986&idx=1&sn=64da74482433ad358fab20946eb3b5d3&scene=21#wechat_redirect)**

**[不懂APQP，你还敢谈新产品开发？——一套古今通杀的防坑法宝，别再让项目死在路上](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247484972&idx=1&sn=490742d347d6ebbbc5deaf3417dc5989&scene=21#wechat_redirect)**

**[一个结构工程师的20年：南方打工故事](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247484948&idx=1&sn=58501fa49f4b43457b58105189cb60e1&scene=21#wechat_redirect)**

**[以“工程师”的角度来聊一聊：什么才是技术？](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247484958&idx=1&sn=d249d4ab2301e80cad848f76e01d8320&scene=21#wechat_redirect)**

**[产品设计师需要掌握的材料知识——不懂材料的设计师，就像拿着螺丝刀修主板](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247484986&idx=1&sn=64da74482433ad358fab20946eb3b5d3&scene=21#wechat_redirect)**

**[一文看懂 CPK、CMK、PPK：制程能力也就这回事，别再靠感觉了！](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247484939&idx=1&sn=8b4589792d875615ca9fb342aa452c9e&scene=21#wechat_redirect)**

**[新产品导入的前世今生：从作坊炼丹术，到数字化“特种部队”](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247484929&idx=1&sn=a04e112ecc3e269c9adab0f5d19fa295&scene=21#wechat_redirect)**

**[一文看懂DOE：一个高级工程师的自我修养](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247484913&idx=1&sn=ca98ce866c92c1b4fe46e8af08e45add&scene=21#wechat_redirect)**

**[当你在谈PPAP时，你在谈些什么？深度解析PPAP通关大考](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247484907&idx=1&sn=a71a4f54812fb0f76365039b3e4b8787&scene=21#wechat_redirect)**

**[保姆级教程塑胶产品DFM指南：攻城狮的自救手册](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247484900&idx=1&sn=e271fa6a7779a302973e438804fdb1e6&scene=21#wechat_redirect)**

**[技术管理如何从蒙圈走向开挂](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247484871&idx=1&sn=c66845c932e9e3d747c72d8382973505&scene=21#wechat_redirect)**

**[你真的了解你的量具吗？MSA中的GRR、Cg、Cgk全解析！](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247484881&idx=1&sn=d136c9a6ccb394111fe20c9bd9245e25&scene=21#wechat_redirect)**

**[【深度干货】装配才是制造业真正的生死线！](https://mp.weixin.qq.com/s?__biz=MzI2NDUwOTM2Ng==&mid=2247484866&idx=1&sn=8eed9a45063702d0cd40075cade4312c&scene=21#wechat_redirect)**
