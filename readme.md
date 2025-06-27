# 旅游短视频研究 — 叙事引兴→观看意向子课题多模态数据预处理与特征提取

本仓库收录了“叙事引兴→观看意向”子研究中各项多模态数据预处理与特征提取的 Jupyter Notebook 源代码。

> **说明**：本项目仅提供核心代码，无完整文档与演示。这些内容源于我博士毕业论文的一个子课题——第一次尝试此类研究，如有不够完善的地方还请批评指正!

---

## 仓库结构

text
NarrativeHook2Intent/
├── aesthetic.ipynb              # 封面视觉审美感知 (Python 3.13.3)
├── Comentropy.ipynb             # 封面信息复杂指数 (Python 3.10.9)
├── Cover_emotion.ipynb          # 封面情感唤起强度 (Python 3.7.16)
├── matching.ipynb               # 图文匹配相似度 (Python 3.9.22)
├── sentiment analysis.ipynb     # 标题情感值计算 (Python 3.9.22)
├── time.ipynb                   # 相对发布时间差计算 (Python 3.9.22)
├── Title classification.ipynb   # 价值导向分类 (Python 3.9.22)


---

## 环境依赖

建议使用 Python 3.9+，并安装以下常用库：

```bash
pip install pandas numpy torch torchvision pillow transformers tqdm openpyxl tensorflow joblib baidu-aip opencv-python requests
```

如有额外需求，请参照各 Notebook 开头的 `环境配置` 注释自行安装。

---

## 使用方法

1. 克隆仓库并进入目录：

   ```bash
   git clone https://github.com/AgnesZSY/NarrativeHook2Intent.git
   cd NarrativeHook2Intent
   ```


2. 打开相应 Notebook（.ipynb），根据顶部说明修改输入/输出路径，逐个运行所有单元格。

3. 结果文件会按 Notebook 中指定路径保存为 Excel 或 CSV 格式，如 `情感值计算.xlsx`、`time2.xlsx` 等。

---

### 各 Notebook 概述

- **aesthetic.ipynb**

  - 功能：基于预训练 MobilenetV2 模型，预测视频封面审美评分与分布
  - 环境：Python 3.13.3；依赖 `torch`, `torchvision`, `Pillow`, `pandas`
  - 操作：设置 `image_folder` 与 `output_excel` 后运行全量处理。

- **Comentropy.ipynb**

  - 功能：调用百度云图像识别 API，计算封面信息复杂度（多主体检测结果汇总）
  - 环境：Python 3.10.9；依赖 `requests`, `pandas`
  - 操作：在脚本顶端填写 `API_KEY` 与 `SECRET_KEY`，确保 `image_dir` 路径正确，运行即可生成 Excel。

- **Cover\_emotion.ipynb**

  - 功能：构建并训练（或加载）强化版情感检测模型，对视频封面提取多维情绪分值与一致性指标
  - 环境：Python 3.7.16；依赖 `tensorflow`, `opencv-python`, `PIL`
  - 操作：若有训练数据，自动训练并保存模型；无训练数据时使用预构建模型，批量预测并输出 CSV。

- **matching.ipynb**

  - 功能：基于`OFA-Sys/chinese-clip-vit-base-patch16`模型，计算标题与封面图像的 CLIP 相似度
  - 环境：Python 3.9.22；依赖 `transformers`, `torch`, `Pillow`, `pandas`
  - 操作：设置 `image_dir` 与 `text_excel_path`，运行后保存相似度结果到 Excel。

- **sentiment analysis.ipynb**

  - 功能：利用 Hugging Face 文本分类管道，对视频标题进行情感值打分（0–100）
  - 环境：Python 3.9.22；依赖 `transformers`, `torch`, `pandas`, `tqdm`
  - 操作：修改 `INPUT` 与 `OUTPUT` 路径，运行 `process_data` 函数生成情感值表格。

- **time.ipynb**

  - 功能：计算每个视频发布时间相对某基准日期（如 2025‑04‑20）的天数差值
  - 环境：Python 3.9.22；依赖 `pandas`
  - 操作：调整 `file_path` 与 `base_time`，运行后输出含 `t` 列的 Excel。

- **Title classification.ipynb**

  - 功能：结合情感分析与关键词匹配，判别短视频价值导向（情感享乐性 vs. 信息实用性）
  - 环境：Python 3.9.22；依赖 `transformers`, `torch`, `pandas`, `joblib`
  - 操作：修改输入 Excel 路径，运行批量处理并导出分类结果。

---

## 项目声明

此仓库为本人博士毕业论文“第五章(即子研究二)”之核心代码存档，侧重展示多模态数据处理思路与实验脚本。 

- 完整图片数据下载链接：
链接：https://pan.quark.cn/s/5c4d2ef6b4a7?pwd=zbL2
提取码：zbL2

- 完整封面-标题下载链接：
链接：https://pan.quark.cn/s/7e38d40aeb3c?pwd=9LGG
提取码：9LGG

感谢关注，欢迎一起分享交流！

