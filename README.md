# 抽水蓄能项目前期评审 AI Agent Demo

这是一个面向 **抽水蓄能项目前期评审、政策研究和竞价策略分析** 的轻量级 AI Agent 示例项目。

项目目标是解决抽水蓄能项目前期工作中常见的问题：

- 项目资料体量大；
- 政策链条长；
- 前期风险分散在可研、用地、环保、移民、接入系统、电价机制等多个环节；
- 人工审查耗时长，且容易遗漏关键风险点。

本 Demo 采用多 Agent 协同架构，包括：

1. **政策检索 Agent**  
   解析能源、电力市场、用地环保等政策文本，提取政策要点与约束条件。

2. **项目审查 Agent**  
   读取项目资料、可研摘要、投资测算信息，提取装机容量、建设周期、接入系统、用地生态、收益机制等关键指标。

3. **风险识别 Agent**  
   按照用地、建设、造价、电价、市场交易、合规六个维度生成风险清单。

4. **竞价策略 Agent**  
   结合电价预测、抽水蓄能运行约束和市场规则，生成日前/实时交易策略及收益测算思路。

5. **总控 Orchestrator**  
   汇总多个 Agent 的结果，输出项目前期评审报告。

## 项目结构

```text
pumped-storage-agent-github-demo/
├── main.py
├── requirements.txt
├── .env.example
├── data/
│   ├── project.txt
│   └── policy.txt
└── src/
    ├── agents.py
    ├── llm.py
    └── prompts.py
```

## 快速开始

安装依赖：

```bash
pip install -r requirements.txt
```

复制环境变量文件：

```bash
cp .env.example .env
```

填写你的模型接口信息：

```bash
LLM_BASE_URL=https://your-model-endpoint/v1
LLM_API_KEY=your-api-key
LLM_MODEL=your-model-name
```

运行：

```bash
python main.py
```

## 说明

本项目默认使用 OpenAI-compatible Chat Completions 接口风格。后续如果接入 MiMo API，只要接口兼容该格式，通常只需修改 `.env` 中的模型地址、API Key 和模型名称。

如果暂时没有模型接口，可以在 `.env` 中设置：

```bash
USE_MOCK_LLM=true
```

此时程序会使用内置模拟结果，便于 GitHub 项目展示。
