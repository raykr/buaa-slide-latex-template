# 北京航空航天大学幻灯片Latex模板

北京航空航天大学幻灯片Latex非官方模板。

本模板修改自<a href="https://github.com/dryangyq/ouc-slide-latex-template" target="_blank">中国海洋大学幻灯片Latex模板</a>模板。在原有模板基础上进行了适配北航标准色修改。

模板主要使用北航官方公布的标准色，包括北航蓝、星空蓝、天空蓝、中国红、品质灰、专金、专银。

此外，使用了大量的信息框来增加模板的活力。

# 文件结构

模板中的文件主要包括:

1. slide.tex：主文件，编写的演示文稿内容主要存放在该文件当中。
2. buaaslide.sty：模板的样式文件。
3. font:字体文件夹，所有编译需要用到的字体。默认字体使用的是华为鸿蒙字体。
4. theme:主题文件夹。
    1. beamercolorthemeBUAASlide.sty：颜色定义文件。
    2. beamerfontthemeBUAASlide.sty：字体定义文件。
    3. beamerinnerthemeBUAASlide.sty：内部元素定义文件。
    4. beamerouterthemeBUAASlide.sty：整体布局定义文件。
    5. beamerthemeBUAASlide.sty：主题定义文件。
5. logos：模板中使用的Logo存放文件夹。
6. figs：插入的图片文件夹。
7. fontawesome.pdf：图标使用说明文件。

# 使用方法
1. 从git上clone项目到本地。
2. 安装Tex编译器，推荐使用<a href="https://tug.org/texlive/" target="_blank">TexLive</a>，安装成功后，可以使用自带的TeXworks打开目录下的tex文件进行编译。
3. 可以安装其他的IDE工具进行Tex文件的编写和修改，推荐使用<a href="https://code.visualstudio.com/" target="_blank">Visual Studio Code</a>。
4. 编译时，请选择XeLaTex，有时候，可能需要连续编译两次，以得到正确的页码和图表编号。

# 元素介绍
## 基本信息
Tex文件的开头，是基本信息部分，可以根据需要添加`\title`{标题}、`\subtitle`{子标题}、`\author`{作者}、`\date`{\today}、`\institute`{所属机构}。

![首页](/figs/slides_1.png)

`\newcommand{\last}{敬请批评指正！}` 的作用是为了制作最后一页致谢页面而单独设置的，可以修改为任何致谢语句。

## 特殊页面

模板中有三个特殊的页面，分别是：标题页（首页）、目录页和结尾页。这三个页面由于其特殊性，不能使用frame的常规模板，因此，为它们创建了三个命令进行生成：

```
\maketitle
\makeoutline
\makelast
```
使用者三个命令后，将会自动创建首页、目录页和结尾页。

首页和结尾页，使用的是基本信息中的数据，而目录页的内容，将根据`\section`进行填充。

![目录](/figs/slides_2.png)

## 使用分节

本模板使用分节进行整体规划，章节共三级，对应的关键字分别是：
```
\section
\subsection
\subsubsection
```
其中，`\section` 会有单独的页面进行显示。如下图所示。而且，section还将会出现在目录页面中。
![section](/figs/slides_3.png )
`\subsection` 和 `\subsubsection`都没有单独的页面相对应，他们会出现在对应章节的frame中，作为标题进行呈现，并且加入了自动编号的效果。需要说明的是，`\subsection`是必须的，而 `\subsubsection` 却可有可无。他们呈现出的最终的效果，如下图所示。
![subsection](/figs/slides_4.png)
**需要注意的是，虽然frame的标题，是由subsection和subsubsection自动生成的，但是frame中的frametitle仍然是必须的，否则没有frametitle这个元素，标题无法自动填充。**

## 使用Frame
章节确定好后，就可以增加Frame来编写幻灯片。使用代码:
```
\begin{frame}
    \frametitle{测试}
\end{frame}
```
就可以插入一张幻灯片。

需要注意的是：如果幻灯片中使用了代码块，则需要加入关键字`fragile`。这样，引入的代码才能保持它们原有的样子，如下所示：
```
\begin{frame}[fragile]
    \frametitle{测试}
\end{frame}
```
当然，也可以使用定义的特殊的frame模板来达到这种效果。
```
\begin{fragileframe}
    \frametitle{测试}
\end{fragileframe}
```
他们的效果是一样的。

## 字体
模板使用的默认字体是<a href="https://developer.harmonyos.com/cn/docs/design/font-0000001157868583" target="_blank">华为鸿蒙字体 (HarmonyOS Sans)</a>。该字体可以免费商用。

如果对字体不满意，可下载其他字体，放入fonts文件夹，并在`beamerfontthemeBUAASlide.sty`文件中修改。

推荐的字体包括:<a href="https://github.com/adobe-fonts/source-han-sans" target="_blank">思源黑体</a>、<a href="https://alibabafont.taobao.com/wow/alibabafont/act/alifont" target="_blank">阿里普惠字体</a>、<a href="https://www.thosefree.com/oppo-sans" target="_blank">OPPO字体</a>、<a href="https://web.vip.miui.com/page/info/mio/mio/detail?postId=33935854" target="_blank">小米字体</a>。这些字体基本上都可以免费商用，并且效果都很不错。关于他们是否能够继续免费商用的政策，请查阅其官方网站以得到最准确的信息。

## 颜色
![color](/figs/slides_9.png)

## 颜色等级
为了显示更丰富的色彩，定义的北航视觉系统标准色，每一种颜色，都有九个等级，等级越低，颜色越浅。例如：对于北航蓝，其等级颜色从buaablue90-buaablue20不等，分成9个等级。

## 信息框
信息框使用边框的形式，提升幻灯片的表现力。

主要的信息框包括：列表框(`vcolorbox`)、提示框(`notebox`、`importantbox`)、信息框(`titlebox`)、要点框(`pointbox`)、块(`block`、`exampleblock`、`alertblock`)、标题框(`headbox`)和文本框(`textbox`)。它们的效果，如下图所示。

![列表框](/figs/slides_12.png)
![提示框](/figs/slides_13.png)
![信息框](/figs/slides_14.png)
![要点框](/figs/slides_15.png)
![标题框和文本框](/figs/slides_16.png)
![块](/figs/slides_17.png)


## 代码
模板可以插入代码块，使用`lstlisting`即可。
![代码](/figs/slides_18.png)

## 公式
模板中可以直接插入公式，和LaTex中没有什么区别。
![公式](/figs/slides_20.png)

## 分栏
![分栏](/figs/slides_21.png)

## 脚注
可以在任何地方使用脚注。即便是在各种信息框中也可以。
![脚注](/figs/slides_22.png)
