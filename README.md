# 电赛设计报告模板

这是一份面向全国大学生电子设计竞赛的中文设计报告模板，提供 LaTeX 和 Word 两种选择。仓库保留了完整的参赛报告源码、项目图片和成品 PDF，可直接作为排版参考，也可以在现有内容上修改。

## 选择版本

- **LaTeX 版：** 来自 2025 年 E 题设计报告。编辑 `src/Template.tex`，成品预览为 `src/Template.pdf`。适合需要稳定排版、公式和图表编号的用户。
- **Word 版：** 编辑 `24H-Report/24H.docx`，对应预览为 `24H-Report/24H.pdf`。该文件为 2024 年 H 题设计报告，适合直接使用 Microsoft Word 或 WPS 修改。

## 作者的话

本人曾获 2024 年省赛一等奖和 2025 年国赛一等奖。将这两份设计报告整理开源，是希望大家能够减少在报告格式和排版上的重复工作，把更多时间投入到方案设计、系统调试和比赛本身。

祝大家比赛顺利，取得理想成绩！

## 模板特点

- 基于 `ctexart`，支持中文标题、摘要、正文和参考文献。
- 已配置 A4 页面、页眉页脚、章节编号、公式、图表、代码块和 TikZ 流程图。
- 保留完整项目实例，便于对照实际报告学习排版。
- 使用 XeLaTeX 编译，兼容 Windows、Linux、macOS 和 Overleaf。
- 提供 GitHub Actions，推送后可自动检查编译并生成 PDF 构件。

## 目录结构

```text
.
├── .github/workflows/build.yml  # GitHub 自动编译
├── 24H-Report/
│   ├── 24H.docx                 # 2024 年 H 题 Word 版
│   └── 24H.pdf                  # Word 版对应 PDF 预览
├── pic/                         # 报告使用的图片素材
├── src/
│   ├── Template.tex             # LaTeX 主文件
│   └── Template.pdf             # LaTeX 版最终 PDF
├── CONTRIBUTING.md              # 贡献指南
├── LICENSE                      # MIT 许可证
└── NOTICE                       # 来源及保留说明
```

LaTeX 编译过程中产生的 `.aux`、`.log`、`.fls` 等临时文件仍可保留在本地，但不会加入新的 Git 提交。

## 环境要求

推荐安装以下任一 LaTeX 发行版：

- [TeX Live](https://tug.org/texlive/)
- [MiKTeX](https://miktex.org/)
- [MacTeX](https://tug.org/mactex/)

编辑器可使用 VS Code 配合 LaTeX Workshop，也可直接使用 Overleaf。请确认环境中存在 `xelatex` 和 `latexmk`。

## 编译

在仓库根目录执行：

```bash
latexmk -cd -xelatex src/Template.tex
```

生成文件位于 `src/Template.pdf`。清理编译临时文件：

```bash
latexmk -cd -c src/Template.tex
```

若没有 `latexmk`，可以进入 `src` 目录连续运行两次：

```bash
xelatex Template.tex
xelatex Template.tex
```

连续编译用于更新交叉引用、图表编号和超链接。

## 修改 LaTeX 报告

1. 在 `src/Template.tex` 中修改标题、摘要、章节正文、表格和参考文献。
2. 将系统框图、电路图、流程图和实物图放入 `pic/`。
3. 使用相对路径插入图片，例如：

   ```latex
   \includegraphics[width=0.8\linewidth]{../pic/your-image.png}
   ```

4. 编译并检查页数、匿名要求、图片清晰度和当年赛题规定。

不同年份、不同赛区的格式要求可能变化，请以当届官方通知为准。

## 修改 Word 报告

1. 打开 `24H-Report/24H.docx`。
2. 使用 Microsoft Word 或 WPS 替换标题、正文、图片和测试数据。
3. 导出 PDF 后，对照 `24H.pdf` 检查分页、公式、图片和表格位置。
4. 提交前检查当届竞赛的页数、匿名和文件命名要求。

## 上传到 GitHub

目录简称为 ECR（Electrical Competition Report）。本目录已整理为独立仓库内容，首次上传可执行：

```bash
git init -b main
git add .
git commit -m "Initial open-source release"
git remote add origin https://github.com/zeitvex/ECR-Template.git
git push -u origin main
```

## 来源与许可证

本项目最初版本来自 [SandOcean-ovo/Template-for-Electrical-Competition-Report](https://github.com/SandOcean-ovo/Template-for-Electrical-Competition-Report)，完整保留项目实例以方便学习和复用。

项目采用 [MIT License](LICENSE) 开源。复用和分发时请保留许可证及原作者版权声明。
