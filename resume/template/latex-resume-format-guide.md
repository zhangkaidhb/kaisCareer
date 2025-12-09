# 汽车行业技术工程师LaTeX简历格式指南

## 📋 基于 ctexart 的自定义模板要求

### 1. 文档类和基本设置

#### 推荐文档类
```latex
\documentclass[11pt,a4paper]{ctexart}
```

#### 页面布局设置
```latex
\usepackage[margin=2cm]{geometry}  % 页面边距
\geometry{left=1.8cm, right=1.8cm, top=2cm, bottom=2cm}
```

#### 中文字体配置
```latex
\usepackage{ctex}
\setCJKmainfont{SimSun}[BoldFont=SimHei, ItalicFont=KaiTi]
\setCJKsansfont{SimHei}
\setCJKmonofont{FangSong}
```

### 2. 页眉页脚设置

#### 专业页眉页脚
```latex
\usepackage{fancyhdr}
\pagestyle{fancy}
\fancyhf{}  % 清除默认设置
\fancyfoot[C]{\thepage}  % 页码居中
\renewcommand{\headrulewidth}{0pt}  % 无页眉线
```

### 3. 章节标题格式

#### 标题样式设置
```latex
\usepackage{titlesec}
\usepackage{xcolor}

% 一级标题设置
\titleformat{\section}
  {\Large\bfseries\sffamily\color{blue!70!black}}
  {}
  {0em}
  {}
  [{\titlerule[0.5pt]\color{blue!50!black}}]

% 二级标题设置
\titleformat{\subsection}
  {\large\bfseries\sffamily\color{black}}
  {}
  {0em}
  {}

% 标题间距
\titlespacing{\section}{0pt}{12pt}{8pt}
\titlespacing{\subsection}{0pt}{8pt}{6pt}
```

### 4. 列表环境设置

#### 专业列表格式
```latex
\usepackage{enumitem}
\setlist{
  leftmargin=0pt,
  itemsep=4pt,
  parsep=0pt,
  topsep=4pt,
  labelsep=10pt,
  font=\bfseries
}

% 自定义符号
\usepackage{pifont}
\newcommand{\solidcheckmark}{\ding{51}}
\newcommand{\circledbullet}{\ding{108}}
```

### 5. 颜色和强调设置

#### 专业配色方案
```latex
\usepackage{xcolor}
\definecolor{primary}{RGB}{0,82,147}      % 汽车蓝
\definecolor{secondary}{RGB}{102,102,102} % 灰色
\definecolor{accent}{RGB}{220,20,60}      % 强调红
\definecolor{techblue}{RGB}{0,114,188}    % 技术蓝

% 强调命令
\newcommand{\highlight}[1]{\textcolor{primary}{\textbf{#1}}}
\newcommand{\tech}[1]{\textcolor{techblue}{\texttt{#1}}}
```

### 6. 完整示例模板

#### 汽车技术工程师简历模板
```latex
\documentclass[11pt,a4paper]{ctexart}

% ============ 基础包 ============
\usepackage[margin=2cm]{geometry}
\usepackage{ctex}
\usepackage{fancyhdr}
\usepackage{titlesec}
\usepackage{enumitem}
\usepackage{graphicx}
\usepackage{hyperref}
\usepackage{xcolor}
\usepackage{tabularx}
\usepackage{array}
\usepackage{multirow}
\usepackage{pifont}

% ============ 页面设置 ============
\geometry{left=1.8cm, right=1.8cm, top=2cm, bottom=2cm}
\pagestyle{fancy}
\fancyhf{}
\fancyfoot[C]{\thepage}
\renewcommand{\headrulewidth}{0pt}

% ============ 颜色定义 ============
\definecolor{primary}{RGB}{0,82,147}
\definecolor{secondary}{RGB}{102,102,102}
\definecolor{accent}{RGB}{220,20,60}
\definecolor{techblue}{RGB}{0,114,188}
\definecolor{lightgray}{RGB}{240,240,240}

% ============ 标题格式 ============
\titleformat{\section}
  {\Large\bfseries\sffamily\color{primary}}
  {}
  {0em}
  {}
  [{\titlerule[0.5pt]\color{primary!30!black}}]

\titleformat{\subsection}
  {\large\bfseries\sffamily}
  {}
  {0em}
  {}

\titlespacing{\section}{0pt}{12pt}{8pt}
\titlespacing{\subsection}{0pt}{8pt}{6pt}

% ============ 列表设置 ============
\setlist{
  leftmargin=0pt,
  itemsep=3pt,
  parsep=0pt,
  topsep=3pt,
  labelsep=8pt
}

% ============ 自定义命令 ============
\newcommand{\highlight}[1]{\textcolor{primary}{\textbf{#1}}}
\newcommand{\tech}[1]{\textcolor{techblue}{\texttt{#1}}}
\newcommand{\skillitem}[2]{\item[\circledbullet] \textbf{#1}: #2}

% ============ 超链接设置 ============
\hypersetup{
  colorlinks=true,
  urlcolor=techblue,
  linkcolor=primary,
  citecolor=secondary
}

\begin{document}

% ============ 个人信息 ============
\begin{center}
  {\Huge\bfseries\sffamily 张凯} \\[8pt]
  {\large\texttt{电话：+86 15122986177} | \texttt{邮箱：15122986177@163.com}} \\[6pt]
  {\large\texttt{LinkedIn：linkedin.com/in/yourprofile}} \\[4pt]
  {\normalsize\color{secondary}汽车电子软件架构师 | AUTOSAR专家}
\end{center}

\vspace{10pt}
{\color{primary}\hrule}
\vspace{12pt}

% ============ 专业技能 ============
\section*{专业技能}

\begin{itemize}
  \skillitem{AUTOSAR架构}{精通AUTOSAR CP标准架构，熟悉Adaptive AUTOSAR和ARA服务}
  \skillitem{开发语言}{Python、C/C++、MATLAB、Java、Shell脚本}
  \skillitem{车载通信}{CAN、CAN-FD、LIN、FlexRay、车载以太网、SOME/IP}
  \skillitem{工具链}{Vector DaVinci、CANoe、vTESTstudio、Sourcetrace}
  \skillitem{操作系统}{Linux（Ubuntu/CentOS）、嵌入式RTOS}
\end{itemize}

% ============ 工作经验 ============
\section*{工作经验}

\subsection*{沃尔沃汽车（亚太）投资控股有限公司}
\textbf{汽车电子软件架构师} \hfill \textit{2023年11月 - 至今} \\[4pt]

\begin{itemize}
  \item[\solidcheckmark] \highlight{主导}高性能计算平台的AUTOSAR架构集成，开发yaml2arxml转换工具
  \item[\solidcheckmark] 负责\tech{SOME/IP}服务配置和车载以太网TSN网络调度优化
  \item[\solidcheckmark] 设计CI/CD流水线，实现代码质量门禁，提升开发效率\textbf{30\%}
  \item[\solidcheckmark] 系统集成调试，确保\tech{IEEE 802.1AS gPTP}时间同步精度达到\textbf{±1μs}
\end{itemize}

\subsection*{科世达(上海)机电有限公司}
\textbf{车身域控制器开发工程师} \hfill \textit{2020年12月 - 2023年11月} \\[4pt]

\begin{itemize}
  \item[\solidcheckmark] 负责\tech{AUTOSAR CP}架构下的车身控制器集成开发
  \item[\solidcheckmark] 主导自动化测试平台开发，基于\tech{Python}和\tech{CAPL}脚本
  \item[\solidcheckmark] 集成测试验证，确保系统符合\tech{ISO 26262 ASIL-B}功能安全要求
  \item[\solidcheckmark] 跨团队技术协调，推动\textbf{5个}客户项目按时交付
\end{itemize}

% ============ 项目经验 ============
\section*{项目经验}

\subsection*{SPA3高性能计算平台集成项目}
\textbf{技术负责人} \hfill \textit{2023年11月 - 2025年7月}

\begin{itemize}
  \item[\solidcheckmark] \textbf{STAR法则应用}：
  \begin{itemize}
    \item \textbf{情境}：支持新一代智能座舱系统的高性能计算需求
    \item \textbf{任务}：设计分布式软件架构，实现多域控制器协同
    \item \textbf{行动}：开发自动化工具链，建立持续集成流水线
    \item \textbf{结果}：缩短系统集成周期\textbf{40\%}，提升代码质量
  \end{itemize}
\end{itemize}

% ============ 教育背景 ============
\section*{教育背景}

\begin{itemize}
  \item \textbf{德国卡尔斯鲁厄理工学院(KIT)} \hfill
    \textit{机电一体化及信息技术硕士} \hfill
    \textit{2017-2020}
  \begin{itemize}
    \item 专业方向：工业自动化、机器人技术
    \item 优秀毕业设计：基于深度学习的动态眼球追踪系统优化
  \end{itemize}

  \item \textbf{河北工业大学(211)} \hfill
    \textit{机械设计制造及其自动化学士} \hfill
    \textit{2012-2016}
  \begin{itemize}
    \item 优秀毕业设计：人体工程学自动调节座椅
  \end{itemize}
\end{itemize}

% ============ 专业认证 ============
\section*{专业认证}

\begin{itemize}
  \item \highlight{AUTOSAR基础认证} \hfill \textit{2023年}
  \item \highlight{Vector工具链专家认证} \hfill \textit{2022年}
  \item \highlight{功能安全ISO 26262培训认证} \hfill \textit{2021年}
  \item \tech{PMP}项目管理专业人士认证 \hfill \textit{2024年}
\end{itemize}

% ============ 语言能力 ============
\section*{语言能力}

\begin{itemize}
  \item \textbf{中文}：母语
  \item \textbf{英语}：流利（雅思6.5）
  \item \textbf{德语}：流利（TestDaF 16/C1）
\end{itemize}

\end{document}
```

### 7. 编译和输出设置

#### 编译命令
```bash
# 推荐：使用 XeLaTeX 编译（更好的中文支持）
xelatex resume.tex

# 或使用 LuaLaTeX
lualatex resume.tex

# 传统方式（需要中文支持环境）
pdflatex resume.tex
```

#### PDF优化设置
```latex
\usepackage{hyperref}
\hypersetup{
  pdftitle={张凯 - 汽车电子软件架构师简历},
  pdfauthor={张凯},
  pdfsubject={汽车电子AUTOSAR架构师求职简历},
  pdfkeywords={AUTOSAR,汽车电子,软件架构,车载网络},
  colorlinks=true,
  urlcolor=blue,
  linkcolor=black,
  pdfpagemode=UseOutlines
}
```

### 8. 版本控制和文件管理

#### 推荐文件结构
```
resume/
├── resume.tex           # 主简历文件
├── content/             # 内容文件
│   ├── personal.tex     # 个人信息
│   ├── experience.tex   # 工作经验
│   ├── skills.tex       # 技能清单
│   └── education.tex    # 教育背景
├── style/               # 样式文件
│   ├── colors.sty       # 颜色定义
│   ├── commands.sty     # 自定义命令
│   └── layout.sty       # 布局设置
├── assets/              # 资源文件
│   ├── logo.pdf         # 个人标识
│   └── qr-code.pdf      # 二维码
└── output/              # 输出文件
    ├── resume.pdf
    └── resume-print.pdf  # 打印版本（黑白）
```

### 9. 常见问题和解决方案

#### 中文字体问题
```latex
% 如果遇到字体错误，使用fallback设置
\usepackage{ctex}
\setCJKfallbackfamilysong{SimHei}
```

#### 页面溢出
```latex
% 调整行间距
\renewcommand{\baselinestretch}{0.98}

% 调整列表间距
\setlist[itemize]{itemsep=2pt,topsep=2pt}
```

#### 打印优化
```latex
% 创建打印版本
\usepackage[monochrome]{xcolor}
\definecolor{primary}{RGB}{0,0,0}  % 黑白打印
```

### 10. 最佳实践建议

#### 内容优化
- ✅ **量化成果**：使用具体数字展示成就
- ✅ **关键词优化**：包含行业术语和技能关键词
- ✅ **STAR法则**：结构化描述项目经验
- ✅ **技术栈展示**：突出核心技术能力

#### 格式优化
- ✅ **一页原则**：5年以下经验控制在1页，5-10年经验最多2页
- ✅ **字体统一**：中文使用宋体/黑体，英文使用Arial/Helvetica
- ✅ **间距合理**：避免过于拥挤或过于稀疏
- ✅ **层次清晰**：使用统一的标题和列表格式

#### 技术优化
- ✅ **ctexart文档类**：专门优化中文LaTeX排版
- ✅ **现代编译**：推荐XeLaTeX或LuaLaTeX编译
- ✅ **PDF优化**：设置合适的PDF元数据和书签
- ✅ **版本管理**：使用Git跟踪简历版本变更