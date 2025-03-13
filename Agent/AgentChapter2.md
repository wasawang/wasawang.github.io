1. Message
   Message是Agent之间以及与用户交互的接口， Camel提供了同意的Message format能够同时支持文本， 图像， 以及视频。
   定义message的时候除了内容外， role_name被用来提高可读性， role_type可以被Agent使用。
2. Prompt Engineering
   Camel提供的各种Task Agent(TaskSpecifyAgent, TaskPlannerAgent本质上就是不同的template model, 用户可以定义自己的模版，
   CoT的使用一般需要满足以下条件： 大的模型， 复杂的问题， 有联系的训练数据
3. Memory
   用来实现session的管理， 对于多人同时操作来说， 可能需要管理多个block, Camel比较好的把Agent和Memory关联上， 感觉有点自动做RAG的感觉
4. Tool
   Tool可以用来实现一些实时性比较高的问题， 或者一些大模型现在还不能很好的解决的问题。 这块需要看看源码才能更好的理解它的实现原理
