# ATTRIBUTION — 素材来源与署名

本项目的代码与文档在 AI 协助下完成，所用外部素材与工具如下，均按各自许可使用。

## 知识来源（oracles/）

| 文件 | 来源 / 性质 | 用途 |
|------|------------|------|
| `01_textbook_stewart.md` | Stewart《Calculus》教材内容 | 极限/切线领域的知识底稿 |
| `02_study_guide.md` | 学习指南 | 领域知识整理 |
| `03_instructor_guide.md` | 教师讲义 | 分类规则依据 |
| `04_pedagogy_guide.md` | 教学法指南 | 分步解答的依据 |
| `05_exemplars.md` | 范例集 | 求解模板参考 |

## 测试用例（test_cases/）

- `test1_tangent_epsilon_delta`、`test2_limits`：源自 Berkeley Math 1A 工作表 3–4。
- `test3_linear_algebra`：线性代数教材标准题（非某人的真实作业，仅作验证用）。

## 第三方依赖

| 依赖 | 用途 | 许可 |
|------|------|------|
| SymPy | 符号计算求解 | BSD |
| PyYAML | 解析领域知识 YAML | MIT |
| XeLaTeX + Noto Sans CJK SC | 中文 PDF 排版（可选） | 各自许可 |

## AI 工具署名

- 本项目的架构设计、代码生成、文档草拟与代码审查，由 AI 助手（本地与云端模型）协助完成。
- 关键判断（选题方向、领域边界、诚实标注「非真实作业」、验收）由项目作者 **宋俊毅** 本人完成。

## 项目作者

- 宋俊毅（GitHub: junyisong01-glitch）

若你发现某处素材的署名或来源标注有误，请提 issue 或 pull request 指正。
