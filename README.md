# E9apiAiPrompt
泛微E9流程表单前端JS生成 - AI提示词

####　分为两个 `prompt`，分别用于生成API ID和生成代码块。该方案为 API 调用食用，以节省调用成本。
#### 如果你想要直接提问方式使用，你可以直接使用第二个Prompt，引用apis.json文件即可。

当然，如果你是GPT PLUS用户，你可以直接使用我制作的GPTs: /g/g-ljFBLdpIe-wan-zi-de-fan-wei-e9liu-cheng-biao-dan-qian-duan-jssheng-cheng

![onesGpts](/reademe/Ones_GPTs.png)

### 第一个Prompt：
```plaintext
###
现在有以下 API：
[插入apilist.json的内容]
###
表单字段:{[字段名称,字段类型,字段描述],...}
我现在需要:[description的内容]
请根据以上内容判断我实现需求所有需要用到的 API 的 id
你的回答必须满足以下要求!：
1. 用到的 API，只能在我提供 API 列表中
2. 仅告诉我需要用 API 的 id 数字, 使用","分割
3. 你的回答以数字开头, 数字结束
4. 回答中不要有任何 API 数字外的任何文字、代码块、注释信息等!
```

### 第二个Prompt：
```plaintext
###
现在有以下 API：
[API ID].{"id": "[API ID]", "name": "[API Name]", "description": "[API Description]", "example": ["[Example Code]"]}...
###
表单字段:{[字段名称,字段类型,字段描述],...}
我现在需要:[description的内容]
请根据给出的 API 列表，使用其中一个或多个 API，实现我的需求，并返回代码块。
仅返回代码块即可，不要返回多余的文字，代码块中包含必要注释。
```

### 提问逻辑概述：
- **第一个Prompt**：通过给定API列表和用户需求，让AI从中挑选出符合需求的API ID。
- **第二个Prompt**：基于AI选出的API ID，生成具体的实现代码，并返回纯代码块。

该prompt应用案例：
![E9API](/reademe/E9API.png)