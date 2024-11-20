# 4_玩转「HF-魔搭-魔乐」平台

## 概览

|         | 关卡名称                | 资料                                                                                                                                                                                                       | 闯关激励   |
| :------ | :--------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- |
| 第 1 关 | Linux 前置基础          | [任务](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/linux/task.md)、[文档](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/linux)、[视频](https://www.bilibili.com/video/BV13U1VYmEUr)   | 50元算力点 |
| 第 2 关 | Python 前置基础         | [任务](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/Python/task.md)、[文档](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/Python)、[视频](https://www.bilibili.com/video/BV1u61jYSExg) | 50元算力点 |
| 第 3 关 | Git 前置基础            | [任务](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/git/task.md)、[文档](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/git/)、[视频](https://www.bilibili.com/video/BV15MShYkEgg)      | 50元算力点 |
| 第 4 关 | 玩转「HF/魔搭/魔乐」平台 | [任务](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/maas/task.md)、[文档](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/maas)、[视频](https://www.bilibili.com/video/BV1XxStYYEH1/)    | 50元算力点 |

## 任务  

| 任务 | 描述 | 时间 |
| --- | --- | --- |
| [模型下载](https://huggingface.co/internlm/internlm2-chat-1_8b) | 使用Hugging Face平台、魔搭社区平台（可选）和魔乐社区平台（可选）下载文档中提到的模型（至少需要下载config.json文件、model.safetensors.index.json文件），请在必要的步骤以及结果当中截图。 | 20min |
| 模型上传（可选） | 将我们下载好的config.json文件（也自行添加其他模型相关文件）上传到对应HF平台和魔搭社区平台，并截图。 | 10min |
| Space上传（可选） | 在HF平台上使用Spaces并把intern_cobuild部署成功，关键步骤截图。 | 10min |

## 文档

### 1. HF 平台

#### 1.1 简介

Hugging Face 最初专注于开发聊天机器人服务。尽管他们的聊天机器人项目并未取得预期的成功，但他们在GitHub上开源的Transformers库却意外地在机器学习领域引起了巨大轰动。如今，Hugging Face已经发展成为一个拥有超过100,000个预训练模型和10,000个数据集的平台，被誉为机器学习界的GitHub。

> Hugging Face 的主要特点包括：

1. Transformers 库：这是 Hugging Face 最著名的项目之一，提供了一套强大的预训练模型，涵盖了从文本分类到问答等众多 NLP 任务。Transformers 库支持多种框架，如 PyTorch 和 TensorFlow，使得开发者能够轻松地加载、训练和使用这些模型。
Model Hub：Hugging Face 提供了一个模型中心，用户可以在这里找到并分享各种预训练模型。这个平台极大地促进了研究者之间的交流与合作，加速了 NLP 领域的发展。
2. Spaces：除了模型之外，Hugging Face 还推出了 Spaces，这是一个允许开发者部署和分享应用程序的平台。通过 Spaces，用户可以创建和共享基于机器学习的应用，如文本生成、语音识别等。
3. Research and Development：Hugging Face 不仅是一个技术平台，也是一个活跃的研究机构。公司经常发布最新的研究成果，并且积极参与到学术界的各种会议和活动中。
4. Community：Hugging Face 拥有一个庞大的社区，包括开发者、研究人员和爱好者。社区成员通过论坛、社交媒体等多种渠道交流想法，共同推动技术进步。

#### 1.2 InternLM模型下载

[internlm2_5-1_8b地址](https://huggingface.co/internlm/internlm2_5-1_8b)

#### 1.3 GitHub CodeSpace的使用

> - 因为网络和磁盘有限的原因，强烈不建议在 InternStudio 运行，因此这里使用CodeSpace  
> - CodeSpace平台上默认的用户权限不是root权限
> - 个人GitHub CodeSpace硬盘空间有限（32GB可用）

[codespaces](https://github.com/codespaces)

Github CodeSpace是Github推出的线上代码平台，提供了一系列templates，我们这里选择Jupyter Notebook进行创建环境。创建好环境后，可以进入网页版VSCode的界面，这就是CodeSpace提供给我们的在线编程环境。

```bash
# 安装transformers
pip install transformers==4.38
pip install sentencepiece==0.1.99
pip install einops==0.8.0
pip install protobuf==5.27.2
pip install accelerate==0.33.0
```

##### 1.3.1 载internlm2_5-7b-chat的配置文件

以下载模型的配置文件为例，先新建一个hf_download_josn.py 文件

```bash
touch hf_download_josn.py
```

```py
import os
from huggingface_hub import hf_hub_download

# 指定模型标识符
repo_id = "internlm/internlm2_5-7b"

# 指定要下载的文件列表
files_to_download = [
    {"filename": "config.json"},
    {"filename": "model.safetensors.index.json"}
]

# 创建一个目录来存放下载的文件
local_dir = f"{repo_id.split('/')[1]}"
os.makedirs(local_dir, exist_ok=True)

# 遍历文件列表并下载每个文件
for file_info in files_to_download:
    file_path = hf_hub_download(
        repo_id=repo_id,
        filename=file_info["filename"],
        local_dir=local_dir
    )
    print(f"{file_info['filename']} file downloaded to: {file_path}")
```

从Hugging Face上下载了相应配置文件

```bash
|internlm2_5-7b
|--- .cache
|---config.json
|---model.safetensors.index.json
```

> InternStudio平台 的 /root/share 目录下已经提供了InterLM2.5系列的模型，可以找到它们作为model_name_or_path进行使用，如

`/root/share/new_models/Shanghai_AI_Laboratory/internlm2_5-7b-chat`

##### 1.3.2 下载internlm2_5-chat-1_8b并打印示例输出

创建一个python文件用于下载internlm2_5-1_8B模型并运行。下载速度跟网速和模型参数量大小相关联，如果网速较慢的小伙伴可以只尝试下载1.8b模型对应的config.json文件以及其他配置文件。

`touch hf_download_1_8_demo.py`

> CodeSpace平台上是没有GPU资源

我们Python代码中只使用CPU进行推理，我们需要修改跟CUDA有关的API，在hf_download_1_8_demo.py文件中粘贴以下内容

```py
import torch
from transformers import AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("internlm/internlm2_5-1_8b", trust_remote_code=True)
model = AutoModelForCausalLM.from_pretrained("internlm/internlm2_5-1_8b", torch_dtype=torch.float16, trust_remote_code=True)
model = model.eval()

inputs = tokenizer(["A beautiful flower"], return_tensors="pt")
gen_kwargs = {
    "max_length": 128,
    "top_p": 0.8,
    "temperature": 0.8,
    "do_sample": True,
    "repetition_penalty": 1.0
}

# 以下内容可选，如果解除注释等待一段时间后可以看到模型输出
# output = model.generate(**inputs, **gen_kwargs)
# output = tokenizer.decode(output[0].tolist(), skip_special_tokens=True)
# print(output)
```

等待几分钟后，会在控制台返回模型生成的结果（解除注释后）

这里以“A beautiful flower”开头，模型对其进行“续写”，InternLM的模型拥有强大的数学方面的能力。这边它输出的文本似乎是关于一个数学问题，具体是关于一个花朵的花瓣数量。

#### 1.4 Hugging Face Spaces的使用

Hugging Face Spaces 是一个允许我们轻松地托管、分享和发现基于机器学习模型的应用的平台。Spaces 使得开发者可以快速将我们的模型部署为可交互的 web 应用，且无需担心后端基础设施或部署的复杂性。 首先访问以下链接，进入Spaces。在右上角点击Create new Space进行创建：[spaces](https://huggingface.co/spaces)

在创建页面中，输入项目名为intern_cobuild，并选择Static应用进行创建

创建成功后会自动跳转到一个默认的HTML页面。创建好项目后，回到我们的CodeSpace，接着clone项目。

> 注意这里请替换你自己的username

```bash
cd /workspaces/codespaces-jupyter
# 请将<your_username>替换你自己的username
git clone https://huggingface.co/spaces/<your_username>/intern_cobuild
cd /workspaces/codespaces-jupyter/intern_cobuild
```

找到该目录文件夹下的index.html文件，修改我们的html代码

```html
<!doctype html>
<html>
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width" />
  <title>My static Space</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      height: 100%;
    }
    body {
      display: flex;
      justify-content: center;
      align-items: center;
    }
    iframe {
      width: 430px;
      height: 932px;
      border: none;
    }
  </style>
</head>
<body>
  <iframe src="https://colearn.intern-ai.org.cn/cobuild" title="description"></iframe>
</body>
</html>
```

保存后就可以push到远程仓库上了，它会自动更新页面

```bash
git add .
git commit -m "update: colearn page"
git push
```

再次进入Space界面，就可以看到我们实战营的共建活动捏~

#### 1.5 模型上传
>
> 通过CLI上传 Hugging Face同样是跟Git相关联，通常大模型的模型文件都比较大，因此我们需要安装git lfs，对大文件系统支持。

```bash
curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash
# sudo apt-get install git-lfs # CodeSpace里面可能会有aptkey冲突且没有足够权限
git lfs install # 直接在git环境下配置git LFS
pip install huggingface_hub
```

使用huggingface-cli login命令进行登录，登录过程中需要输入用户的Access Tokens，获取时，需要先验证email

完成验证后，点击create new token，创建一个类型为“Write”的token，**并请复制好token后要存储在合适的地方**

接着可以在CodeSpace里面，使用

```bash
git config --global credential.helper store
huggingface-cli login
```

命令进行登录，这时需要输入刚刚的token

创建项目

```bash
cd /workspaces/codespaces-jupyter

#intern_study_L0_4就是model_name
huggingface-cli repo create intern_study_L0_4

# 克隆到本地 your_github_name 注意替换成你自己的
git clone https://huggingface.co/{your_github_name}/intern_study_L0_4
```

克隆好之后，刷新文件目录可以看到克隆好的intern_study_L0_4文件夹。

我们可以把训练好的模型保存进里面，这里考虑到网速问题，只上传我们刚刚下载好的config.json，把它复制粘贴进这个文件夹里面，还可以写一个README.md文件，比如可以粘贴以下内容：

```md
# 书生浦语大模型实战营camp4
- hugging face模型上传测试
- 更多内容请访问 https://github.com/InternLM/Tutorial/tree/camp4
```

现在可以用git提交到远程仓库

```bash
cd intern_study_L0_4
git add .
git commit -m "add:intern_study_L0_4"
git push
```

> 注意，如果git push 报错，可能是第一次上传时需要验证，请使用以下命令，注意替换<>里面的内容，然后再次git push一下就可以了

```bash
git remote set-url origin https://<user_name>:<token>@huggingface.co/<repo_path>

# 如 git remote set-url origin https://blank:hf_xxxxxxxxxxx@huggingface.co/blank/intern_study_L0_4

# 这里blank和hf_xxxxxxxxxxxx只是示例 请替换为你的username和之前申请的access token

git pull origin
```

现在可以在Hugging Face的个人profile里面看到这个model，也可以直接将下面的Url输入到浏览器网址栏上

`https://huggingface.co/<user_name>/intern_study_L0_4`

### 2 魔搭社区平台

ModelScope 是一个“模型即服务”(MaaS)平台，由阿里巴巴集团的达摩院推出和维护。它旨在汇集来自AI社区的最先进的机器学习模型，并简化在实际应用中使用AI模型的流程。通过ModelScope，用户可以轻松地探索、推理、微调和部署各种AI模型。

注册登录ModelScope平台，进入导航栏模型库，搜索 internlm2_5-chat-1_8b，下载1.8b的对话模型

#### 2.1 创建开发机

选择 10% 的开发机，镜像选择为 Cuda-12.2。在输入开发机名称后，点击创建开发机。

#### 2.2 环境配置

为ms_demo创建一个可用的conda虚拟环境，可以和其他环境区分开来

```bash
# 激活环境
conda activate /root/share/pre_envs/pytorch2.1.2cu12.1

# 安装 modelscope
pip install modelscope -t /root/env/maas
pip install numpy==1.26.0  -t /root/env/maas
pip install packaging -t /root/env/maas
```

> 注意：为了保证能够找到我们每次装的依赖，每次新建一个终端之后都需要导出path 如果不改变终端，导出一次就够了

```bash
export PATH=$PATH:/root/env/maas/bin
export PYTHONPATH=/root/env/maas:$PYTHONPATH
```

创建我们的demo目录

`mkdir -p /root/ms_demo`

#### 2.3 下载指定多个文件

internlm2_5-7b-chat 考虑到7B的模型文件比较大，这里我们先采用modelscope的cli工具（当然hugging face也有）来下载指定文件，在命令行输入以下命令

```bash
modelscope download \
    --model 'Shanghai_AI_Laboratory/internlm2_5-7b-chat' \
    tokenizer.json config.json model.safetensors.index.json \
    --local_dir '/root/ms_demo'
```

刷新一下文件目录，就能看到在ms_demo中下载了指定的json文件。

internlm2_5-1_8b-chat

```bash
modelscope download \
    --model 'Shanghai_AI_Laboratory/internlm2_5-1_8b-chat' \
    tokenizer.json config.json model.safetensors.index.json \
    --local_dir '/root/ms_demo'
```

#### 2.4 上传模型

魔搭社区类似HF，也有一套创建模型的界面。不同的是，它具有审核机制，当符合它的社区规范时才会被公开。那么当上传正常的模型文件后，审核一般就会通过了。

上传文件的方法可以直接通过平台添加文件，也可以通过git下载模型后进行修改和上传文件

```bash
#Git模型下载
git clone https://www.modelscope.cn/<your_username>/<your_model>
```

### 3 魔乐社区平台

魔乐社区（Modelers）是一个提供多样化、开源模型的平台，旨在促进开发者和研究人员在最先进的模型和流行应用上进行协作。

#### 3.1 下载internlm2_5-chat-1_8b模型

```bash
cd /
mkdir ml_demo
cd ml_demo
```

下载该模型

```bash
# 确保安装git-lfs 保证大文件的正常下载
apt-get install git-lfs
git lfs install
# clone 仓库
git clone https://modelers.cn/Intern/internlm2_5-1_8b-chat.git
```

刷新一下文件夹，即可在ml_demo中找到下载好的模型文件，在魔乐社区中，还推荐了一个新的深度学习开发套件openMind Library，除了常用的Transforms的API，也可以探索如何使用openMind来加载模型

```py
# 确保按指南安装好openmind后
from openmind import AutoModel
model = AutoModel.from_pretrained("Intern/internlm2_5-1_8b-chat", trust_remote_code="True")
```

> penMind Library是一个深度学习开发套件，通过简单易用的API支持模型预训练、微调、推理等流程。 openMind Library通过一套接口兼容PyTorch和MindSpore等主流框架，同时原生支持昇腾NPU处理器。

#### 3.2 上传模型

在魔乐社区一般有两种方法，第一种是安装好openmid后使用openmind的API来上传文件，另一个就是用git命令来推送文件，跟一般的git工作流相类似。可参考[上传文件 | 魔乐社区](https://modelers.cn/docs/zh/openmind-hub-client/basic_tutorial/upload.html)

## 作业

### 模型下载

### 模型上传（可选）

### Space上传（可选）

## 小结
