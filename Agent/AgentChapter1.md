CAMEL AI 作为一个多Agent的架构的基础库， 能够帮助AI开发者很容易处理多Agent的开发。 第一章主要讲了以下几点：
1. 安装的问题， 这个很简单， 基本就是pip install camel-ai, 如果需要安装所有依赖， 需要 pip install camel-ai[all]
2. 使用api和大模型的交互主要分为以下几步：
   a. 创建一个Model, 这可以通过ModelFactory.create来做。 里面需要定义model的平台（如果是OpenAI, 则用OPENAI, 其他的有OPENAI_COMPATIBLE_MODEL，
       model_type（不同的model 类型， GPT_4_O_MINI, GPT_3_5_TURBO之类）， url(对OPENAI不需要提供， 其他默认参照供应商），
       api_key(openai可以通过设环境变量。 为了安全， 可以用dotenv库
       model_config_dict:模型的配置参数， 比如可以指定top_p, temperature之类的）
   b. 利用模型创建一个Agent， 参考类ChatAgent. 这是可以指定#a定义的模型， output_language(这个是作为prompt输入， 所以没有固定格式，en, chinese,中文 ...),
      system_message(系统级的prompt)
   c.利用Agent的step函数与之交互。 step(message) -> response

3.roleplay session的使用： 例子实现两个不同的role相互交流来完成一个任务， 主要有一个ai assistant role和一个user_role. 每个role可以定义不同的model. 基本上可以理解为user_role是可以知道ai
  assistant role进行工作的， 可以基于assistant role的response做出下一步的反馈。 基本流程留下：
  a. 初始化： init_chat  -> input_msg.
  b. Loop n times:
    1). call step to execute: step(input_msg)
    2). If response has terminal information(from any role), stop the program.
    3). If reponse has CAMEL_TASK_DONE, stop the program
    4). assign the assistant_response to the input_msg, and go back to 1).

  基本上每个step就做两件事： 分析assistant_response, 决定下一步任务， 执行下一步任务， 返回assistant_response.

一个无关的问题是基本上cursor生成的camel的代码都是错的， 不知道是不是免费版的问题。
      
