安装所需模块：

```shell
uv add langchain langchain-deepseek
```

本文旨在利用大模型实现一个简单的翻译功能。

基本流程包括：提示词  | 大模型 | 解析输出

首先，定义一个获取API密钥的函数：

```jupyter
import os,getpass


def get_api_key(key):
    """获取API密钥"""
    if not os.environ.get(key):
         os.environ[key] = getpass.getpass("请输入你的API密钥：")
```

然后，获取DEEPSEEK_API_KEY,LANGSMITH_API_KEY。

```jupyter
os.environ["LANGSMITH_TRACING"] = "true"  # **启用 LangSmith 的追踪功能**，它会将应用程序的调用链（如 LLM 请求、工具调用等）记录到 LangSmith 平台，便于调试和分析。

get_api_key("DEEPSEEK_API_KEY")

get_api_key("LANGSMITH_API_KEY")
```

导入所需模块：

```jupyter
from langchain_deepseek import ChatDeepSeek
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.output_parsers import StrOutputParser
from langchain_core.messages import HumanMessage, SystemMessage
```

实例化一个大模型：

```jupyter
model = ChatDeepSeek(
    model = "deepseek-chat", # 还有其他的一些参数，比如base_url和api_key
    temperature = 0.7
)
```

构建提示词：

```jupyter
system_template = "你是一个世界顶级的翻译大师，可以将{text}在兼顾上下文语境的情况下翻译为{language}。"

prompt = ChatPromptTemplate(
    [("system", system_template), ("user", "{text}")]
)
```

解析输出的内容：

```jupyter
parser = StrOutputParser()
```

创建链式调用：

```jupyter
chain = prompt | model | parser
```

最后实现流式输出：

```jupyter
async for chunk in chain.astream({"text" : "欢迎来到AI世界！","language" : "English"}):
    print(chunk,end = "",flush=True)
```

结果如下：

```markdown
Welcome to the world of AI!  

（注：这里采用"world of AI"的表述既保持了原文的简洁有力，又符合英文科技语境中常见的表达方式。惊叹号保留了原文的热情语气，整体翻译在技术准确性和情感传达上达到了平衡。如果是更正式的科技场景，也可译为"Welcome to the Artificial Intelligence realm"，但当前版本更普适且富有感染力。）
```