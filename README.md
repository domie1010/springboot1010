# springboot+vue

#### 介绍
java毕业设计，毕业设计系统开发
#### 3000多套系统，需要联系
抠：3565014707
微：a13424421017

#### 软件架构
##### 整体架构模式
这是一个 高校毕业设计管理系统，采用 前后端分离架构，包含以下模块：

管理后台（src/main/resources/admin）：基于 Vue.js + ElementUI 的 SPA 应用，供教务管理员和指导教师使用。

用户端（src/main/resources/front）：基于传统前端技术（如 Layui/jQuery），供学生进行选题、提交材料、查看成绩等操作。

后端服务（src/main/java/com）：基于 Spring Boot + MyBatis 的 Java 服务，提供 RESTful API 和核心业务逻辑。

##### 分层架构设计
后端分层：

Controller层：controller 包（如 ChengjiController）处理 HTTP 请求，返回 JSON 数据。

Service层：service 包（如 ChengjiService）实现业务逻辑（如成绩计算、选题审核）。

DAO层：dao 包（如 ChengjiDao）通过 MyBatis XML 文件（ChengjiDao.xml）操作数据库。

实体与数据模型：

entity 包定义数据库实体（如 ChengjiEntity 成绩实体、KetiEntity 课题实体）；

vo（值对象）和 view（视图模型）用于接口数据传输和复杂查询结果封装。

前端分层：

管理后台（Vue.js）：

视图层：views/modules 定义页面（如 keti 课题管理页、chengji 成绩管理页）。

组件层：components 封装可复用组件（如 BreadCrumbs 面包屑导航）。

状态管理：通过 Vuex（store.js）管理全局状态（如用户权限、课题审核状态）。

用户端（传统前端）：

动态交互：通过 jQuery 或 Layui 实现页面交互（如选题申请、材料上传）。

##### 关键技术特性
权限控制：

后端通过 AuthorizationInterceptor 拦截器和 @APPLoginUser 注解实现接口权限校验；

前端管理后台通过路由（router-static.js）限制页面访问权限（如仅教师可审核选题）。

流程管理：

课题生命周期管理（发布→选题申请→审核→任务分配→成绩录入）；

审核状态通过数据字典（dictionaryKetiYesno）定义（如“待审核/通过/驳回”）。

文件管理：

static/upload 存储毕业设计材料（如开题报告、论文终稿、代码附件）。

#### 核心功能模块解析
##### 课题管理模块
课题发布与审核：

keti（课题信息）：教师发布课题（名称、描述、要求），教务管理员审核课题合理性；

dictionaryKetiYesno（课题审核状态）：控制课题是否对学生可见。

选题申请：

xuantishenqing（选题申请）：学生提交选题申请，教师审核并分配任务；

支持多轮申请和冲突检测（如课题人数已满）。
##### 任务与进度管理
任务分配：

ketirenwu（课题任务）：教师拆解课题为阶段性任务（如开题、中期检查、论文提交），设置截止时间；

学生提交任务成果，教师评分并反馈。

进度跟踪：

可视化展示任务完成进度（如甘特图），自动提醒超时任务。

##### 成绩管理模块
成绩录入与统计：

chengji（成绩管理）：教师录入答辩成绩、论文成绩、任务评分，系统自动计算总评成绩；

按班级、学院统计成绩分布（如优秀率、及格率）。

成绩公示：

学生端查看成绩详情和教师评语，支持成绩申诉流程。

##### 用户与权限模块
多角色体系：

yonghu（学生）：选题、提交材料、查看成绩；

jiaoshi（教师）：发布课题、审核选题、分配任务、录入成绩；

users（管理员）：管理用户、维护数据字典、处理异常流程。

数据字典：

dictionaryXueyuan（学院字典）、dictionaryBanji（班级字典）维护基础信息；

dictionaryKetirenwuYesno（任务审核状态）管理任务验收结果。

##### 通知与文档管理
系统公告：

news（新闻公告）：发布毕业设计相关通知（如答辩安排、材料提交截止时间）。

文档上传：

支持多格式文件上传（如 PDF、Word、ZIP），自动校验文件大小和类型。
