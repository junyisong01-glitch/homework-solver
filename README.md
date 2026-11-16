# homework-solver

> 把一份数学作业文件（.md / .pdf / .docx）一键转成带解题步骤、可直接提交的答案文档（.tex / .pdf）。

一个「本体驱动 + 检索增强」的本地作业求解器。它把「领域知识」和「题目实例」分开存放：会解什么题，取决于它**知道什么**，而不是写了多少代码——想解更多题，就扩充领域知识库，而不是改代码。

## 一句话说明

给一个作业文件路径，输出一份分步骤、可复核、可排版成 PDF 的解答文档。

## 安装步骤

```bash
# 1. 克隆仓库
git clone https://github.com/junyisong01-glitch/homework-solver.git
cd homework-solver

# 2. 安装依赖（仅需 sympy 和 pyyaml）
pip install -r requirements.txt
```

要求 Python 3.10+。全程本地运行，不联网、不上传题目。

## 使用示例

```bash
# 用内置示例跑一遍（5 分钟内可完成）
python scripts/pipeline.py examples/sample_homework.md output/

# 求解自己的作业
python scripts/pipeline.py 你的作业.md output/ --course "线性代数" --student "张三"

# 生成 PDF（需要本机安装 LaTeX）
python scripts/pipeline.py 你的作业.md output/ --compile
```

输出文件：

| 文件 | 内容 |
|------|------|
| `1_ingested.json` | 原文摄入与分段 |
| `2_parsed.json` | 结构化题目与分类 |
| `3_solutions.json` | 带步骤、答案和求解状态的解答 |
| `homework.tex` | 排版好的 LaTeX 文档 |

## 项目结构

```
├── scripts/                  ← 5 阶段流水线（摄入→解析→求解→渲染→编译）
│   ├── pipeline.py           ← 一键入口
│   ├── ingest.py             ← Stage 1 文档摄入
│   ├── parse_problems.py     ← Stage 2 题目解析
│   ├── classify.py           ← 题目分类
│   ├── retrieve.py           ← 知识检索
│   ├── solve.py              ← Stage 3 自动求解
│   └── render_latex.py       ← Stage 4/5 LaTeX 生成与 PDF 编译
├── domain_skills/            ← 领域知识（calculus_limits.yaml）
├── solver_templates/         ← 参数化 SymPy / 模板求解器
├── oracles/                  ← 知识来源文档（教材/讲义/示例）
├── test_cases/               ← 验证用例（含求解率）
├── examples/                 ← 示例输入输出
├── references/               ← LaTeX 模板 + SymPy 速查
├── requirements.txt          ← 依赖清单
├── SKILL.md                  ← 技能说明与调用方式
├── AI_LOG.md                 ← AI 协作日志
├── ATTRIBUTION.md            ← 素材来源与署名
└── LICENSE                   ← MIT
```

## 验证结果

在 `test_cases/` 三个用例上复现：

| 用例 | 领域 | 求解率 |
|------|------|--------|
| test1_tangent_epsilon_delta | 切线 & ε-δ 记号 | 8/8 = 100% |
| test2_limits | 极限 | 9/10 = 90% |
| test3_linear_algebra | 线性代数 | 10/12 = 83% |

> 求解率取决于领域知识覆盖度。超出已知领域（如进阶物理、组合数学）的题目需要先扩充 `domain_skills/` 才能解，这是设计使然，不是 bug。

## License

MIT — 见 `LICENSE`。
