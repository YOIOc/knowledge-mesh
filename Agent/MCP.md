## 1.MCP是什么
MCP（Model Context Protocol，**模型上下文协议**）是由Anthropic于2024年底推出的一项开放标准协议。**MCP是定义在\[AI应用（MCP客户端宿主）]和\[外部数据源/工具（MCP服务器）]之间的标准化通信协议**。让AI模型能统一调用外部世界的接口和数据

我们可以让SpringBoot项目实现MCP协议（项目变成一个实现MCP协议的MCP服务器），这样AI应用就可以直接调用SpringBoot项目中的业务接口，实现**自然语言驱动**的系统操作
## MCP客户端
