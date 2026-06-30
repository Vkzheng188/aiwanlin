Multi-Agent Skill Hub｜多智能体技能共享中心
A standardized, pluggable skill ecosystem for multi-agent collaboration, enabling skill definition, distribution, scheduling and cross-agent reuse.
📌 项目简介
本仓库是面向多智能体系统的可复用 Skill 技能共享与调度底座，解决传统多 Agent 项目能力耦合、技能无法沉淀、调用逻辑混乱、难以跨智能体复用的痛点。
将各类工具能力、业务流程、任务步骤封装为标准化独立 Skill
支持总控 Agent 自动路由匹配技能、分配子智能体执行
提供统一技能注册、加载、校验、权限、版本管理机制
开放社区共建模式，任何人可提交自定义技能合并入库，实现技能开源共享
✨ 核心特性
标准化 Skill 规范
统一 SKILL.yaml/SKILL.md 定义模板，包含技能名称、触发条件、入参、执行逻辑、依赖、权限、示例调用，适配 AutoGen、LangGraph、CrewAI、Qwen-Agent、DeepSeek-Agent 等主流多智能体框架。
多智能体协同调度
协调中心：任务拆解 + 技能匹配 + 智能体指派
角色隔离：不同 Agent 绑定专属可用技能，避免权限越界
串行 / 并行 / 分支执行模式，支持复杂长链路任务编排
热插拔 & 动态管理
无需重启系统即可新增 / 禁用 / 更新技能；支持本地技能、仓库远程拉取技能双模式，一键导入复用。
技能共享与社区共建
分类收纳通用工具类、开发类、数据分析类、办公类、垂直业务类技能
提供 PR 提交模板、技能校验 CI 流水线，规范化贡献流程
技能索引检索、标签分类、调用样例文档，快速查找复用
可靠性保障
参数校验、调用超时熔断、执行日志追踪、异常捕获回滚、调用频次限流，适配生产环境部署。
📂 仓库目录结构
plaintext
multi-agent-skill-hub/
├── skills/                  # 公共共享技能库（社区可提交新增）
│   ├── tool/                # 通用工具技能（搜索、文件、接口、计算等）
│   ├── dev/                 # 开发运维技能（代码生成、测试、Git、部署）
│   ├── data/                # 数据处理、解析、可视化技能
│   ├── office/              # 文档、表格、总结、邮件处理技能
│   ├── custom-template/     # 自定义技能模板（新建技能参考）
│   └── skill-registry.json  # 全局技能注册表
├── src/
│   ├── skill_loader.py       # 技能加载、解析、校验引擎
│   ├── agent_orchestrator.py# 多智能体调度核心
│   ├── router.py            # 意图-技能匹配路由
│   └── utils/               # 工具、日志、权限、版本工具
├── examples/                # 多智能体调用技能示例代码
├── docs/                    # 技能编写规范、接入文档、贡献指南
├── tests/                   # 技能单元测试
├── .github/workflows/       # CI：技能格式校验、自动测试、合并检查
└── README.md
🚀 快速接入示例
python
运行
from src.agent_orchestrator import MultiAgentOrchestrator

# 初始化调度器，加载全部共享技能
orchestrator = MultiAgentOrchestrator(skill_path="./skills")

# 下发任务，自动匹配对应技能并分配智能体协作执行
result = orchestrator.run_task("整理CSV数据并生成可视化图表")
print(result)
🤝 技能贡献与共享方式
Fork 本仓库，基于 custom-template 创建你的自定义 Skill 文件夹
补全 SKILL.yaml 配置、调用示例、说明文档
本地自测通过后提交 Pull Request
仓库自动 CI 校验格式与可用性，审核合并后纳入公共技能库，供所有使用者一键引用
🧩 适配框架
CrewAI / AutoGen / LangGraph
LlamaIndex Agent、LangChain Agent
通义千问、DeepSeek、Claude、GPT 系列自研多智能体系统
📄 License
MIT License，允许个人 / 商业自由使用、修改、分发，欢迎持续共建多智能体技能生态。
