# 使用LaTex制作简历

从overleaf上选择一个简历模板，我选择的是[中文简历模板](https://www.overleaf.com/latex/templates/chinese-resume-template-zhong-wen-jian-li-mo-ban/fbdypsjmgwbb)，将overleaf中的所有内容都下载到本地。采用XeTEX来编译


## 个人信息

不喜欢名字与个人信息居中，我将个人信息做成表格形式：

```latex
% 我在这里填写上了一个超链接，则需要加上这个包
\usepackage{hyperref}
\begin{tabular}{ll}
XX:XX&XX:XX\\
YY:YY&YY:YY\\
ZZ:ZZ&ZZ:ZZ\\
\href{https://xxx}{https://xxx}:xxx&ss:ss\\
\end{tabular}
```

&nbsp;&nbsp;&nbsp;&nbsp;这里"XX:XX"、"YY:YY"、"ZZ:ZZ"表示自己的个人信息，`&`表示分隔符，`\\`表示换行，超链接第一个括号是将用户访问的内容分，第二个是在简历上展示的内容，`tabular`后面的`ll`表示两列都向左靠齐。其他的`tabular`参数还有`c`和`r`，`c`表示中间靠齐、`r`表示向右靠齐。

## 教育背景

这里的样式我也不太喜欢，还是将其改成表格的形式：

```latex
% 注意需要引入这个包
\usepackage{tabularx}
\begin{tabularx}{\textwidth}{XlXXl}
SSS&SSS&SSS&SSS&\;\;\;\;SSS\\
SSS&SSS&SSS&SSS&SSS\\
\end{tabularx}
```

这里采用tabularx是为了能占满正一行，一共有`X`、`l`、`c`、`r`参数，\;表示弹性填充，这里的`\;`表示空格，我这里是为了将每一行数据间隔相同。

## 其他部分

这里也是像"教育背景"一样，也是上半部分的：时间-项目名称-职责，按照表格是形式做出来，下本部分的具体内容按照列表的形式做出来。

列表：

```latex
\begin{itemize}
\item[*]{xxxxx}
\end{itemize}
```

这里的`[*]`是可以根据自己的需求更改的。

## 设置icon

在tex文件中添加`\usepackage{fontawesome}`，查看[官方文档](https://github.com/srikanthy/faXeTeX)，将链接中的[字体文件](https://github.com/srikanthy/faXeTeX/blob/master/fontawesome.tex)下载下来放在fonts文件中，看[PDF](https://github.com/srikanthy/faXeTeX/blob/master/fontawesome.pdf)中的名称即可直接使用。

## 设置颜色

在tex文件中添加`\usepackage[dvipsnames]{xcolor}`，可以使用颜色，也能给icon加颜色。颜色的具体使用方法是：

```latex
\usepackage[dvipsnames]{xcolor}
\color{颜色}{icon或者文字等内容}
```

颜色的具体可选择的是：[https://mirrors.bfsu.edu.cn/CTAN/macros/latex/contrib/xcolor/xcolor.pdf](https://mirrors.bfsu.edu.cn/CTAN/macros/latex/contrib/xcolor/xcolor.pdf)，注意我这里引入的是xcolor，只能用xcolor所提供的英文颜色。

## 最后

LaTex的学习手册：[http://mirrors.zju.edu.cn/CTAN/info/lshort/chinese/lshort-zh-cn.pdf](http://mirrors.zju.edu.cn/CTAN/info/lshort/chinese/lshort-zh-cn.pdf)

## 附上简历的tex文件

```latex
\documentclass{resume}
\usepackage{zh_CN-Adobefonts_external} 
\usepackage{linespacing_fix}
\usepackage{cite}
\begin{document}
\pagenumbering{gobble}



%***"%"后面的所有内容是注释而非代码，不会输出到最后的PDF中
%***使用本模板，只需要参照输出的PDF，在本文档的相应位置做简单替换即可
%***修改之后，输出更新后的PDF，只需要点击Overleaf中的“Recompile”按钮即可
%**********************************姓名********************************************
\name{方鸿渐}
%**********************************联系信息****************************************
%第一个括号里写手机号，第二个写邮箱
\contactInfo{(+86) 1234567890}{test@test.test}
%**********************************其他信息****************************************
%在大括号内填写其他信息，最多填写4个，但是如果选择不填信息，
%那么大括号必须空着不写，而不能删除大括号。
%\otherInfo后面的四个大括号里的所有信息都会在一行输出
%如果想要写两行，那就用两次这个指令（\otherInfo{}{}{}{}）即可
\otherInfo{性别：男}{籍贯：江南}{}{}
\otherInfo{来历：钱钟书《围城》}{}{}{}
%*********************************照片**********************************************
%照片需要放到images文件夹下，名字必须是you.jpg，如果不需要照片可以不添加此行命令
%0.15的意思是，照片的宽度是页面宽度的0.15倍，调整大小，避免遮挡文字
\yourphoto{0.15}
%**********************************正文**********************************************


%***大标题，下面有横线做分割
%***一般的标题有：教育背景，实习（项目）经历，工作经历，自我评价，求职意向，等等
\section{教育背景}


%***********一行子标题**************
%***第一个大括号里的内容向左对齐，第二个大括号里的内容向右对齐
%***\textbf{}括号里的字是粗体，\textit{}括号里的字是斜体
\datedsubsection{\textbf{克莱登大学}，克莱登实验班，\textit{博士}}{1926.09 - 1930.06}


%***********列举*********************
%***可添加多个\item，得到多个列举项，类似的也可以用\textbf{}、\textit{}做强调
\begin{itemize} [parsep=1ex]
  \item \textbf{证书来源}：购买自爱尔兰商人
\end{itemize}


\datedsubsection{\textbf{北平某大学}，实验班，\textit{本科}}{1922.09 - 1926.06}
\begin{itemize} [parsep=1ex]
  \item \textbf{土木工程系}：不喜欢，转系
  \item \textbf{社会学系}：不喜欢，转系
  \item \textbf{中国文学系}：从此毕业
\end{itemize}

\section{职业经历}

\datedsubsection{\textbf{点金银行}，职员}{1930.09}
\begin{itemize}[parsep=0.5ex]
  \item 高中订婚的未婚妻的父亲的公司
\end{itemize}

\datedsubsection{\textbf{三闾大学}，副教授}{1931.09 - 1934.6}
\begin{itemize}[parsep=0.5ex]
  \item 同事：李梅亭、顾尔谦、孙柔嘉、赵辛楣
\end{itemize}

\datedsubsection{\textbf{上海某报社}，职员}{1934.09 -}
\begin{itemize}[parsep=0.5ex]
  \item 生活不如意
\end{itemize}

\section{情感经历}

\datedsubsection{\textbf{鲍小姐}，一夜情}{1930.06}
\begin{itemize}[parsep=0.5ex]
  \item \textbf{地点}：回国船上
\end{itemize}

\datedsubsection{\textbf{苏文纨}，单恋}{1930.08 - 1931.08}
\begin{itemize}[parsep=0.5ex]
  \item \textbf{地点}：上海
  \item 苏小姐一直钟情于方鸿渐，也错以为方鸿渐对其有意
  \item 方鸿渐在月夜下情境所迫，吻了苏小姐，第二日不得不告诉苏小姐自己所爱并非她
\end{itemize}

\datedsubsection{\textbf{唐晓芙}，热恋}{1930.08 - 1931.08}
\begin{itemize}[parsep=0.5ex]
  \item \textbf{地点}：上海
  \item 闲暇之余经常去苏小姐家探望，由此结识了苏小姐的表妹唐晓芙唐小姐
  \item 由于苏小姐挑拨，唐小姐也与方鸿渐一刀两断
\end{itemize}

\datedsubsection{\textbf{孙柔嘉}，妻子}{1934.08 -}
\begin{itemize}[parsep=0.5ex]
  \item \textbf{订婚地点}：三闾大学
  \item 方、孙二人在赵辛楣家中遇上苏文纨，神情谈吐间遭到苏小姐的讽刺
  \item 二人回到上海，因工作、父母、亲戚妯娌等多方面问题又多次激发矛盾
\end{itemize}

\section{简历写作注意事项}

写作时不要泛泛而谈太笼统，要应用STAR原则，即Situation（情景）、Task（任务）、Action（行动）和Result（结果）四个英文单词的首字母组合。

\begin{itemize}[parsep=0.5ex]
  \item S指的是situation，事情是在什么情况下发生
  \item T指的是task，你是如何明确你的目标的
  \item A指的是action，针对这样的情况分析，你采用了什么行动方式
  \item R指的是result，结果怎样，在这样的情况下你学习到了什么
\end{itemize}

\end{document}

```