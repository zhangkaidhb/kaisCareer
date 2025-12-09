# 基于 ctexart 的汽车行业求职简历 LaTeX 模板（格式要求 + 示例）

本 Markdown 文件提供一份基于 **`ctexart`** 的中文简历 LaTeX 模板的**格式规范**与**完整示例代码**，适用于汽车行业岗位（整车 / 底盘 / 动力总成 / 电驱 / 智能驾驶 / 质量等）的技术类求职简历。

> 建议使用 **XeLaTeX** 编译，并导出为 PDF 供网申或邮件投递使用。

---

## 1. 模板总体说明

- **文档类**：`ctexart`（原生支持中文，结构灵活，适合自定义专业简历）  
- **编译引擎**：`XeLaTeX`（可直接调用系统字体，支持中英文混排）  
- **纸张与页数**：A4；0–5 年经验建议控制在 1 页，5 年以上最多 2 页  
- **布局风格**：单栏为主，顶部抬头简洁，适度使用“伪两栏”（如 tabularx 左右信息）  
- **字体策略**：中英文统一采用无衬线体系（如 思源黑体 + Source Sans Pro），更适合屏幕和打印阅读  
- **输出格式**：首选 PDF，避免在不同设备上因 Office 版本差异导致排版错乱  
- **适用岗位**：整车集成、底盘开发、动力总成、电驱、电池、智能驾驶、测试/验证、质量/体系等技术岗位

---

## 2. 版式与格式要求一览

| 项目           | 建议设置                                          | 说明 |
|----------------|---------------------------------------------------|------|
| 编译引擎       | XeLaTeX                                           | 支持系统字体与中英文混排 |
| 文档类         | `ctexart` + `11pt,a4paper`                        | 简历场景下版式自由度高 |
| 纸张           | A4                                                | 符合国内外招聘标准 |
| 页边距         | `margin=2cm`                                     | 内容偏多时可微调为 1.6–1.8cm |
| 中文主字体     | 思源黑体 / 冬青黑体 / 微软雅黑等                  | 确保为无衬线中文字体，显示清晰 |
| 英文主字体     | Source Sans Pro / Segoe UI / Arial 等            | 与中文无衬线风格统一 |
| 正文字号       | 10–11pt                                           | 汽车技术简历信息量大，11pt 兼顾可读性与密度 |
| 一级标题字号   | `\large` 或约 14–16pt                             | 用于“职业概述”“工作经历”等栏目 |
| 二级标题字号   | `\normalsize` + 加粗                              | 用于公司名 / 岗位名 / 项目名 |
| 行距           | 1.1–1.2 倍                                        | 保持紧凑且不拥挤 |
| 段前/段后间距  | 2–4pt 左右                                        | 通过命令控制整体紧凑 |
| 列表样式       | `itemize` + 小圆点                                | 配合 `enumitem` 控制缩进与行间距 |
| 强调色         | 深蓝（如 `#005B99`）或墨绿                        | 仅用于栏目标题与少量强调文字 |
| 链接样式       | 与强调色一致或黑色                               | 通过 `hyperref` 设置 `urlcolor` |
| 页眉页脚       | 一般不显示页眉页脚                                | 使用 `\pagestyle{empty}` |

---

## 3. 结构与自定义命令约定

为方便统一样式并简化书写，模板中约定以下自定义命令与环境：

### 3.1 自定义命令

```latex
\newcommand{\cvsection}[1]{%
  \vspace{0.9em}%
  {\large\bfseries\color{Accent} #1}\par
  \vspace{0.25em}%
  {\color{Accent}\rule[2pt]{\linewidth}{0.6pt}}%
  \vspace{0.2em}%
}

\newcommand{\cvsubsection}[2]{%
  \textbf{#1} \hfill {\small\color{LightGray} #2}\par
}
```

- `\cvsection{}`：一级栏目标题（如“职业概述”“关键能力”“工作经历”“代表项目”等）  
- `\cvsubsection{左侧标题}{右侧信息}`：栏目内的小节标题（如“某某汽车集团｜底盘开发工程师” + “2019.07 -- 至今，上海”）。

### 3.2 列表环境

```latex
\newenvironment{cvitems}{
  \begin{itemize}
}{
  \end{itemize}
}
```

配合：

```latex
\setlist[itemize]{nosep,leftmargin=1.4em,label=\textbullet}
```

实现：列表项目紧凑、统一使用小圆点、左缩进适中。

### 3.3 推荐结构层级

1. 顶部抬头：使用 `tabularx` 实现左右布局（左姓名与岗位，右联系方式/照片等）；  
2. `\cvsection{职业概述}`：3–5 行文字概括方向、经验和关键成果；  
3. `\cvsection{关键能力（汽车方向）}`：使用 `tabularx` 做两列（左模块名，右能力描述）；  
4. `\cvsection{工作经历}`：下含多个 `\cvsubsection` + `cvitems`；  
5. `\cvsection{代表项目}`：按项目组织，突出背景、难点和个人贡献；  
6. `\cvsection{教育背景}` 与 `\cvsection{证书与其他}`：简明列出相关信息。

---

## 4. 完整 LaTeX 示例模板（可直接编译）

> 使用前请根据当前系统/环境安装情况，修改字体名称。需要照片时，替换 `photo.jpg` 并取消注释对应行；不需要照片则保持注释。编译方式建议选择 **XeLaTeX**。

```latex
% !TEX program = xelatex
\documentclass[11pt,a4paper]{ctexart}

% ---------- 基本版式 ----------
\usepackage[margin=2cm]{geometry}
\usepackage{fontspec,xunicode,xltxtra}
\usepackage{setspace}
\usepackage{enumitem}
\usepackage{tabularx}
\usepackage{array}
\usepackage{graphicx}
\usepackage{hyperref}
\usepackage[dvipsnames]{xcolor}

% ---------- 字体设置（按需替换为你本机字体） ----------
% 英文字体
\setmainfont{Source Sans Pro}[
  UprightFont    = *-Regular,
  BoldFont       = *-SemiBold,
  ItalicFont     = *-It,
  BoldItalicFont = *-SemiBoldIt
]
% 中文字体
\setCJKmainfont{Source Han Sans SC}
\setCJKsansfont{Source Han Sans SC}
\setCJKmonofont{Source Han Sans SC}

% ---------- 颜色与链接 ----------
\definecolor{Accent}{HTML}{005B99}
\definecolor{LightGray}{gray}{0.3}
\hypersetup{
  colorlinks = true,
  urlcolor   = Accent,
  linkcolor  = Accent
}

% ---------- 列表样式 ----------
\setlist[itemize]{nosep,leftmargin=1.4em,label=\textbullet}

% ---------- 自定义命令 ----------
\newcommand{\cvsection}[1]{%
  \vspace{0.9em}%
  {\large\bfseries\color{Accent} #1}\par
  \vspace{0.25em}%
  {\color{Accent}\rule[2pt]{\linewidth}{0.6pt}}%
  \vspace{0.2em}%
}

\newcommand{\cvsubsection}[2]{%
  \textbf{#1} \hfill {\small\color{LightGray} #2}\par
}

\newenvironment{cvitems}{
  \begin{itemize}
}{
  \end{itemize}
}

% ---------- 文档开始 ----------
\begin{document}
\pagestyle{empty} % 去页眉页脚

% ===== 顶部抬头 =====
\begin{tabularx}{\textwidth}{@{}Xr@{}}
  {\bfseries\LARGE 张凯（Kai Zhang）} &
  % 如需照片，取消下一行注释并提供本地图片
  % \multirow{3}{*}{\includegraphics[width=2.5cm]{photo.jpg}}
  \\
  \textcolor{Accent}{\large 底盘开发工程师｜乘用车/新能源} & \\
  \vspace{0.2em} & \\
  \small
  上海 \quad 手机：+86-138-0000-0000 \quad
  邮箱：\href{mailto:zhangkaid6@example.com}{zhangkaid6@example.com} \quad
  GitHub：\href{https://github.com/zhangkaid6}{github.com/zhangkaid6}
  &
\end{tabularx}

\vspace{0.8em}

% ===== 职业概述 =====
\cvsection{职业概述}
\small
具有 5 年乘用车底盘开发与整车集成经验，覆盖从方案设计、仿真分析到试制试验与量产验证。
主导 2 款 A 级平台车型的转向与悬架性能优化，高速操稳主观评分提升至 4.3/5，
转向响应时间缩短约 12\%。熟悉整车开发流程（含 APQP）、IATF 16949 相关要求，
可配合跨部门完成平台化、轻量化和成本优化目标。
\normalsize

% ===== 关键能力 =====
\cvsection{关键能力（汽车方向）}
\begin{tabularx}{\textwidth}{@{}p{3.2cm}X@{}}
  整车与系统集成 &
  整车性能目标分解、布置评估，操稳/舒适性/安全性指标平衡，平台化与车型派生规划
  \\
  底盘系统 &
  前/后悬架、转向、制动系统方案设计与匹配，K\&C 试验，主观评价与性能优化
  \\
  CAE 与仿真 &
  ADAMS/CarSim 车辆动力学仿真，结构强度与刚度分析，参数灵敏度与 DOE 优化
  \\
  试验与验证 &
  台架试验方案制定，高环和道路试验（含鱼钩、蛇形、紧急变线），问题分析与闭环
  \\
  体系与质量 &
  IATF 16949、APQP、PPAP 流程，DFMEA，8D 问题解决，供应商技术沟通与质量提升
  \\
  工具链 &
  CATIA/UG、MATLAB/Simulink、CarSim、INCA、CANoe，Office/LaTeX 文档与报告撰写
\end{tabularx}

% ===== 工作经历 =====
\cvsection{工作经历}

\cvsubsection{某某汽车集团股份有限公司｜底盘开发工程师}{2019.07 -- 至今，上海}

\small
\textit{部门：整车工程院 底盘与操稳性能开发部}
\begin{cvitems}
  \item 负责 A 级平台车型前后悬架与转向系统方案设计、参数匹配以及整车操稳性能目标达成。
  \item 主导 XX 车型高速稳定性改善项目，通过转向刚度与前束特性优化，使 100km/h 双移线
        主观评分从 3.4 提升至 4.2/5，转向响应速度提升约 15\%。
  \item 牵头 K\&C 试验与道路评价，建立主客观相关性模型，为后续派生车型提供参数设计窗口。
  \item 在平台化开发中推动底盘零部件通用化与轻量化方案，实现单车成本降低约 350 元。
\end{cvitems}
\normalsize

\vspace{0.4em}

\cvsubsection{某某汽车工程技术有限公司｜车辆动力学工程师（实习）}{2018.03 -- 2019.06，北京}

\small
\begin{cvitems}
  \item 参与电动 SUV 项目车辆动力学仿真，搭建 CarSim 车辆模型并完成关键参数标定。
  \item 协助完成直线制动、转向梯度等性能仿真，对标国际同级车型并输出优化建议。
\end{cvitems}
\normalsize

% ===== 代表项目 =====
\cvsection{代表项目}

\cvsubsection{A 级平台转向响应优化项目｜项目负责人}{2021.01 -- 2022.06}

\small
\textbf{项目简介：} 面向中国市场的 A 级平台三款车型，用户反馈高速转向“粘滞、响应慢”，
且 ESC 介入过早影响舒适性。

\textbf{主要工作与成果：}
\begin{cvitems}
  \item 基于现有车辆试验数据与主观评价，识别转向系统刚度不足、前束特性不合理为主要问题。
  \item 通过 CAE 仿真与参数 DOE，提出转向刚度提升 10--15\%、前束特性优化的设计建议。
  \item 组织台架/道路验证，最终实现转向响应提升约 12\%，高速蛇形试验主观评分从 3.5 提升至 4.3/5。
\end{cvitems}
\normalsize

% ===== 教育背景 =====
\cvsection{教育背景}

\cvsubsection{某某大学｜车辆工程（本科）}{2015.09 -- 2019.06}

\small
主修课程：汽车构造、汽车理论、汽车设计、车辆动力学、汽车电器与电子技术等。\\
绩点：3.6/4.0（专业前 10\%）。毕业设计方向：电动乘用车悬架系统参数匹配与操稳性能分析。
\normalsize

% ===== 证书与其他 =====
\cvsection{证书与其他}

\small
\begin{cvitems}
  \item 英语六级（CET-6），可流利阅读英语技术文档。
  \item 参加 ISO 26262 功能安全基础培训、IATF 16949 质量管理体系内部培训。
  \item 大学生方程式赛车（FSAE）底盘组成员，负责转向系统设计与路试数据采集。
\end{cvitems}
\normalsize

\end{document}
```

---

## 5. Xmind 结构概览（模板设计）

可将以下大纲复制到 Xmind 或任意大纲工具中，用于理解和二次定制本模板：

```text
ctexart汽车简历模板
    模板目标
        适配中文汽车行业技术简历
        单页或双页A4布局
        便于导出PDF并在线投递
    版式规范
        文档类与编译引擎
        纸张与页边距
        字体与字号
        行距与段落间距
        颜色与链接样式
    结构与命令
        cvsection 一级栏目标题
        cvsubsection 公司/项目+时间信息
        cvitems 列表条目环境
    示例内容
        顶部抬头
        职业概述
        关键能力
        工作经历
        代表项目
        教育背景
        证书与其他
```

你可以直接在此 Markdown 的基础上修改 LaTeX 模板中的颜色、字体和栏目标题，以适配不同岗位（如智能驾驶、电驱控制、质量工程等）。
