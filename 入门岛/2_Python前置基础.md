# 2_Python前置基础

## 概览

|         | 关卡名称                | 资料                                                                                                                                                                                                       | 闯关激励   |
| :------ | :--------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- |
| 第 1 关 | Linux 前置基础          | [任务](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/linux/task.md)、[文档](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/linux)、[视频](https://www.bilibili.com/video/BV13U1VYmEUr)   | 50元算力点 |
| 第 2 关 | Python 前置基础         | [任务](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/Python/task.md)、[文档](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/Python)、[视频](https://www.bilibili.com/video/BV1u61jYSExg) | 50元算力点 |
| 第 3 关 | Git 前置基础            | [任务](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/git/task.md)、[文档](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/git/)、[视频](https://www.bilibili.com/video/BV15MShYkEgg)      | 50元算力点 |
| 第 4 关 | 玩转「HF/魔搭/魔乐」平台 | [任务](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/maas/task.md)、[文档](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/maas)、[视频](https://www.bilibili.com/video/BV1XxStYYEH1/)    | 50元算力点 |

## 任务

### 任务概览

| 任务类型 | 任务内容 | 预计耗时 |
| --- |---| ---|
|闯关任务|Leetcode 383(笔记中提交代码与leetcode提交通过截图)| 20mins|
|闯关任务| Vscode连接InternStudio debug笔记 | 10mins|
|可选任务| pip安装到指定目录 | 10mins|

作业总共分为三个任务，两个闯关任务均完成视作闯关成功。
请将作业发布到知乎、CSDN等任一社交媒体，将作业链接提交到以下问卷，助教老师批改后将获得 50 算力点奖励！！！

提交地址：<https://aicarrier.feishu.cn/share/base/form/shrcnUqshYPt7MdtYRTRpkiOFJd>

### 任务一

完成[Leetcode 383](https://leetcode.cn/problems/ransom-note/description/), 笔记中提交代码与leetcode提交通过截图

### 任务二

下面是一段调用书生浦语API实现将非结构化文本转化成结构化json的例子，其中有一个小bug会导致报错。请大家自行通过debug功能定位到报错原因并做修正。

注意：

- **提交代码时切记删除自己的api_key！** 本段demo为了方便大家使用debug所以将api_key明文写在代码中，这是一种极其不可取的行为!

- 作业提交时需要有debug过程的图文笔记，以及修改过后的代码。

```python
from openai import OpenAI
import json
def internlm_gen(prompt,client):
    '''
    LLM生成函数
    Param prompt: prompt string
    Param client: OpenAI client 
    '''
    response = client.chat.completions.create(
        model="internlm2.5-latest",
        messages=[
            {"role": "user", "content": prompt},
      ],
        stream=False
    )
    return response.choices[0].message.content

api_key = ''
client = OpenAI(base_url="https://internlm-chat.intern-ai.org.cn/puyu/api/v1/",api_key=api_key)

content = """
书生浦语InternLM2.5是上海人工智能实验室于2024年7月推出的新一代大语言模型，提供1.8B、7B和20B三种参数版本，以适应不同需求。
该模型在复杂场景下的推理能力得到全面增强，支持1M超长上下文，能自主进行互联网搜索并整合信息。
"""
prompt = f"""
请帮我从以下``内的这段模型介绍文字中提取关于该模型的信息，要求包含模型名字、开发机构、提供参数版本、上下文长度四个内容，以json格式返回。
`{content}`
"""
res = internlm_gen(prompt,client)
res_json = json.loads(res)
print(res_json)
```

### 任务三(可选)

使用VScode连接开发机后使用`pip install -t`命令安装一个numpy到看开发机`/root/myenvs`目录下，并成功在一个新建的python文件中引用。

## 文档

### 1. Conda虚拟环境

Conda 是一个流行的开源包管理系统和环境管理器，主要用于安装、运行和更新来自不同语言（主要是Python）的软件包。它最初是为Python程序设计的，但也可以打包和分发R、Ruby、Lua、Scala、Java、JavaScript、C/C++、Fortran等语言的软件。

> 其它python包管理器: pdm, rye, uv等

```bash
# 创建环境（--prefix或-p 可选参数 指定环境安装路径）
conda create -n myenv python=3.9
conda create [--prefix /root/envs/myenv] python=3.9
# 激活环境
conda activate myenv
# 安装软件包
conda install numpy pandas
# 列出环境
conda env list
# 退出环境
conda deactivate
# 更新软件包
conda update numpy
# 卸载软件包
conda remove numpy
# 卸载环境
conda env remove -n myenv
```

### 2. pip安装Python三方依赖包

pip 是 Python 的包安装程序，用于从 Python 包索引（PyPI）安装和管理软件包。它是 Python 官方推荐的包管理工具，用于安装和管理 Python 库和框架。

```bash
# 安装包
pip install package_name
# 安装特定版本的包
pip install package_name>=1.19,<2.0
pip install package_name==1.0.4
# 卸载包
pip uninstall package_name
# 列出已安装的包
pip list
# 升级包
pip install --upgrade package_name
# 查看包信息
pip show package_name
# 搜索包
pip search search_query
# 从要求文件安装
pip install -r requirements.txt
# 检查包的兼容性
pip check
# 冻结当前环境的包列表
pip freeze
# 下载包但不安装
pip download package_name
```

> pip可以使用--target或-t参数来指定安装目录

```bash
pip install <somepackage> --target /root/myenvs
pip install -r requirements.txt --target /root/myenvs
```

要使用安装在指定目录的python包，可以在python脚本开头临时动态地将该路径加入python环境变量中去

```python
import sys  
  
# 你要添加的目录路径  
your_directory = '/root/myenvs'  
  
# 检查该目录是否已经在 sys.path 中  
if your_directory not in sys.path:  
    # 将目录添加到 sys.path  
    sys.path.append(your_directory)  
  
# 现在你可以直接导入该目录中的模块了  
# 例如：import your_module
```

### 3. vscode进行python debug

调试（Debugging）是软件开发中一个重要的过程，旨在识别和修复程序中的错误或缺陷。调试可以帮助开发者理解代码的执行流程，检查变量的状态，以及定位和解决问题。

#### 1. 安装Python扩展

打开VSCode，点击左侧扩展栏，搜索Python，并安装。

#### 2. 配置debug

- 首次debug需要配置以下，点击“create a launch.json file”，选择python debugger后选择“Python File” config。
- 可以直接编辑生成的launch.json文件，配置调试参数，比如添加config（Add Configuration）等

#### 3. 设置断点

在代码行号旁边点击，可以添加一个红点，这就是断点

#### 4. 启动debug

点击绿色箭头（开始调试）按钮，或者按F5键。

#### 5. 查看变量

当代码在断点处停下来时，你可以查看和修改变量的值。在“Run and Debug”侧边栏的“Variables”（变量）部分，你可以看到当前作用域内的所有变量及其值。

#### 6. 执行调试

debug面板各按钮功能介绍：

1. continue: 继续运行到下一个断点。

2. step over: 单步跳过，可以理解为运行当前行代码，不进入具体的函数或者方法。

3. step into: 单步进入。如果当前行代码存在函数调用，则进入该函数内部。如果当前行代码没有函数调用，则等价于step over。

4. step out: 单步退出函数，返回到调用该函数的上一层代码。

5. restart: 重新启动调试。

6. stop: 终止调试。

#### 不同的断点

在调试过程中，确实可以通过设置不同类型的断点来更好地控制和理解程序的执行过程。以下是一些常见的断点类型及其在VSCode中的使用方法：

##### 1. 普通断点 (Standard Breakpoint)

这是最基本的断点类型，只需点击代码行号旁边的空白区域或使用快捷键（通常是F9）即可设置。当程序执行到达该行时，会自动暂停。

##### 2. 条件断点 (Conditional Breakpoint)

条件断点只在满足特定条件时才会触发。这在处理循环或大量数据时非常有用，可以避免不必要的暂停。

> 设置方法：
在VSCode中，右键点击代码行号旁边的空白区域，选择“Add Conditional Breakpoint...”。
输入条件表达式，例如 x > 10 或 data.length == 0。

##### 3. 日志点 (Log Point)

日志点不会使程序暂停，而是在命中该点时输出一条指定的日志消息。这对于不需要暂停程序但需要记录某些信息的情况非常有用。

设置方法：
在VSCode中，右键点击代码行号旁边的空白区域，选择“Add Log Point...”。
输入要输出的日志消息，可以包含变量，例如 console.log('Value of x:', x)。

##### 4. 函数断点 (Function Breakpoint)

函数断点在特定函数被调用时触发。这对于调试复杂的函数调用链非常有用。

设置方法：
在VSCode中，可以在“Run and Debug”侧边栏中选择“Breakpoints”视图，然后点击“+”按钮并选择“Function Breakpoint”。
输入要打断点的函数名。

##### 5. 数据断点 (Data Breakpoint)

数据断点在特定变量的值发生变化时触发。这对于调试涉及复杂状态变化的程序非常有用。

设置方法：
目前VSCode对数据断点的支持有限，主要依赖于底层调试器的能力。对于C++等语言，可以使用LLDB或GDB提供的数据断点功能。
在VSCode中，可以在“Run and Debug”侧边栏中选择“Watch”视图，添加要监控的变量，然后在调试过程中观察其变化。

##### 6. 异常断点 (Exception Breakpoint)

异常断点在程序抛出异常时触发。这对于捕获和调试异常非常有用。

设置方法：
在VSCode中，可以在“Run and Debug”侧边栏中选择“Breakpoints”视图，然后点击“+”按钮并选择“Exception Breakpoints”。
选择要捕获的异常类型，例如所有已知的异常或特定类型的异常。

### 4. Python调用InternLM api

#### 1. 获取token

前往书生浦语的API文档,登陆后点击API tokens。初次使用可能会需要先填写邀请码。然后创建一个新的api token。

#### 2. 使用InternLM api

```python
#./internlm_test.py
from openai import OpenAI
import os
def internlm_gen(prompt,client):
    '''
    LLM生成函数
    Param prompt: prompt string
    Param client: OpenAI client 
    '''
    response = client.chat.completions.create(
        model="internlm2.5-latest",
        messages=[
            {"role": "user", "content": prompt},
      ],
        stream=False
    )
    return response.choices[0].message.content

api_key = os.getenv('api_key')
#api_key = "" #也可以明文写在代码内，不推荐
client = OpenAI(base_url="https://internlm-chat.intern-ai.org.cn/puyu/api/v1/",api_key=api_key)
prompt = '''你好！你是谁？'''
response = internlm_gen(prompt,client)
print(response)
```

## 作业

### 闯关任务 Leetcode 383(笔记中提交代码与leetcode提交通过截图)

### 闯关任务 Vscode连接InternStudio debug笔记

### 可选任务 pip安装到指定目录

## 小结

1. conda,pip用法
2. debug技巧（多种断点使用）
3. api的调用
