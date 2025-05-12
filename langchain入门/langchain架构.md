LangChain 是一个基于大型语言模型（LLMs）的应用程序开发框架。

LangChain 简化了 LLM 应用全流程的每个环节：

- 通过 LangChain 的开源组件和第三方集成来开发您的应用程序。利用 LangGraph 构建具有一流流式处理和人工参与支持的状态化智能体。
- 生产化：利用 LangSmith 检查、监控和评估您的应用程序，从而实现持续优化并自信部署。
- 部署：通过 LangGraph 平台，将您的 LangGraph 应用程序转变为可用于生产环境的 API 和助手。
![Diagram outlining the hierarchical organization of the LangChain framework, displaying the interconnected parts across multiple layers.](https://python.langchain.com/svg/langchain_stack_112024.svg "LangChain Framework Overview")

LangChain 为大型语言模型及相关技术（例如嵌入模型和向量存储）提供了标准接口，并且与数百个供应商进行了集成。更多信息请访问集成页面。

```python
model.invoke("Hello, world!")
```

## 架构设计

LangChain 框架包含多个开源库。更多详情请参阅架构页面。

- `langchain-core`: 聊天模型及其他组件的基础抽象。
- 重要集成已拆分为轻量级包，由 LangChain 团队和集成开发者共同维护。
- 构成应用程序认知架构的链、代理和检索策略。
- 社区维护的第三方集成。
- "一个编排框架，用于将 LangChain 组件组合成具备持久化、流式传输等关键特性的生产就绪应用程序。详情请参阅 LangGraph 文档。"

## 指南

### 教程

如果你希望构建特定项目或更偏向于动手实践，不妨看看我们的教程部分。这里是最适合入门的地方。

这些是入门的最佳选择：

- [[开发一个基础的 LLM 应用]]
- [[建立一个聊天机器人]]
- [[建立一个代理]]
- [[LangGraph 入门介绍]]
