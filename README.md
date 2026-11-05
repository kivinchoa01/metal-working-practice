# 金工实习课件（冷加工 · 热加工）

西北工业大学《金工实习》课程教学幻灯片，Beamer 16:9 版式，XeLaTeX 编译。

- **作者**：周计明（zhoujm@nwpu.edu.cn）
- **学期**：2026 年秋
- **规模**：73 帧，成品 PDF 共 85 页（含各章导航页）

## 内容结构

### 第一部分：冷加工（32 帧）

| 章节 | 幻灯片 | 主要内容 |
|---|---:|---|
| 切削加工概述 | 1 | 切削加工的定义；车、钻、镗、刨、铣、磨等机械加工方法与钳工等手工方法 |
| 划线 | 5 | 划线的作用与精度说明；基准（Datum）；划线工具；V 型块与划针盘；划线染料 |
| 钳工 | 9 | 工作场地与夹具；锯削（锯条选择、操作要领）；锉削（锉刀种类、平面与曲面锉削） |
| 切削刀具 | 5 | 切削速度；前角与后角；不同刀具的角度；车刀几何角度 |
| 车削 | 7 | 车削工作范围；车床结构与溜板箱、刀架；零件装夹（前后顶尖、跟刀架与中心架、花盘装夹） |
| 铣削 | 5 | 卧式与立式铣床；铣刀及铣削工作；分度头；顺铣与逆铣 |

### 第二部分：热加工（38 帧）

| 章节 | 幻灯片 | 主要内容 |
|---|---:|---|
| 工程材料及热处理 | 8 | 工程材料分类与性能；典型材料性能对比；铁碳合金与钢铁牌号；热处理；加热温度范围；回火温度与硬度关系 |
| 铸造 | 12 | 砂型铸造原理与步骤；模样、型砂、型芯；真空铸造（V 法）；熔模铸造及改进工艺；消失模铸造；壳型铸造；压铸；常见铸造缺陷 |
| 锻造 | 10 | 锻造温度范围；自由锻工具与工序；闭式模锻；锤上模锻与压力机上模锻；轧制、挤压、拉拔等压力加工方法 |
| 冲压加工 | 8 | 落料与排样；冲孔；落料冲孔凸凹模尺寸计算；弯曲；拉深；变薄拉深 |

### 其他

| 内容 | 幻灯片 | 说明 |
|---|---:|---|
| Outline | 1 | 目录导航 |
| 参考教材 | 1 | 课程参考书目 |
| 课件网址 | 1 | Gitee 仓库链接与二维码 |

## 目录与文件说明

```
metalWorkingPractice/
├── metalworkingpractice.org     # 主源文件（Emacs Org-mode，Beamer 导出）
├── metalworkingpractice.tex     # 由 .org 导出的 LaTeX 源文件
├── metalworkingpractice.pdf     # 编译成品（当前版本）
├── metalworkingpractice.bbl     # BibTeX 输出（空文件，已忽略）
├── beamerthemeAUTheme.sty       # 侧边栏 Beamer 主题（Auburn 主题改版）
├── beamerAppera.sty             # 字体配置：\fHei、\fKai 等
├── figures/                     # 插图目录（29 个文件，正文引用 15 个）
├── WorkshopProcesses.pdf        # 英文教材 Workshop Processes… 扫描件
├── metalijxie.pdf               # 冷加工教材扫描件
├── metaljixiehot.pdf            # 热加工教材扫描件
├── npupractice.pdf              # 西工大金工实习教材扫描件
├── manufactextbook.pdf          # 机械制造基础教材扫描件
└── npulogolib.pdf               # 校徽等素材（当前未引用）
```

### 关于插图

- 正文图片多数来自扫描教材页，通过 `\includegraphics[page=..., viewport=..., clip]` 按页裁剪引用，并非直接插入图片，修改时需调整页码与视口坐标。
- `figures/` 中的 `file-*.png` 为从课件/网页截取的插图；另有 14 个文件当前未被正文引用，可后续整理。
- 文中嵌有 B 站教学视频链接及其二维码。

## 编译方法

必须使用 **XeLaTeX**（源码使用了 `fontspec`、`xeCJK`，不能用 pdfLaTeX），连续编译两次以生成目录：

```bash
xelatex -interaction=nonstopmode metalworkingpractice.tex
xelatex -interaction=nonstopmode metalworkingpractice.tex
```

依赖：

- 字体：Times New Roman（西文），STSong（正文中文），SimHei（标题/强调），KaiTi（注释）
- 宏包：`beamer`、`fontspec`、`xeCJK`、`tikz`、`tcolorbox`、`qrcode`、`bloques`、`xpinyin`、`subfigure`、`threeparttable`、`mathrsfs`、`caption`

编辑流程：一般修改 `metalworkingpractice.org`，在 Emacs 中用 Org Beamer 导出为 `.tex` 后再编译；直接修改 `.tex` 的内容在下次导出时会被覆盖。

## 参考教材

1. 耿俊浩（译），机械制造基础及实践（Workshop Processes, Practices and Materials, 5th Edition），北京：机械工业出版社，2023.
2. 黄明宇，金属实习（下册·冷加工，第 3 版），北京：机械工业出版社，2025.
3. 柳秉毅，金工实习（上册·热加工，第 2 版），北京：机械工业出版社，2009.
4. 北航、西工大合编，金工实习，北京：国防工业出版社，1984.6.

## 版本管理

- 远程仓库：`git@gitee.com:zhou-jiming/metal-working-practice.git`
- 分支：`master`
- `.gitignore` 已忽略 LaTeX 编译中间文件（`*.aux`、`*.log`、`*.nav`、`*.snm`、`*.toc`、`*.bbl`、`*.blg`、`*.fls`、`*.fdb_latexmk`、`*.synctex.gz` 等）及 `*~`、`*.bak` 等备份文件。
- 源文件、图片与 PDF 均纳入版本管理。

## 使用说明

本课件仅用于课程教学。扫描教材页面的版权归原出版社及作者所有，请勿公开传播或用于商业用途。
