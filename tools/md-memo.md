
**Markdown 备忘小贴士**

---

- [符号](#符号)
- [链接](#链接)
- [锚点](#锚点)
- [公式](#公式)
- [语法高亮](#语法高亮)
- [+HTML](#+html)
- [Github Flavored Markdown](#gfm)
- [Pandoc](#pandoc)

## 符号

在 Word 中，输入 Unicode 码，再按 `alt + x` 即可输出对应符号。

- 空格 white space
    + **[en](https://codepoints.net/U+2002)**: 是 **em** 的一半，UTF8 `U+2002 (8194)`、HTML `&nbsp;`。
    + **[em](https://codepoints.net/U+2003)**: m 宽不换行空格，UTF8 `U+2003 (8195)`、HTML `&emsp;`。示例：` `
    + `0020` Space
    + `00A0` No-breaking Space
    + `2004` Three-per-em Space; thick space
    + `2006` Six-per-em Space
- [连接号](https://zh.wikipedia.org/zh/%E7%A0%B4%E6%8A%98%E5%8F%B7) dash 
    + 连字符 Hyphen `‐`，UTF8 `U+2010 (8208)`
    + **en dash**: UTF8 `U+2013 (8211)`、HTML `&ndash`。示例：`–`
        * 表示数字、日期、时间等连续范围
        * 表示对比的数值或相关的两件事物
        * 两侧一般不加空格，除非为了避免混淆或外观丑陋
        * 用来表示两个不同词之间的关系
    + **em dash**: UTF8 `U+2014 (8212)`、HTML `&mdash;`。示例：`—`
        * 表示语气转折
        * 用于说话被打断或情绪激昂到无法继续讲话的情况中
    + 破折号，两个 **em dash**。`──`
    + 减号 minus `−`，UTF8 `U+2212 (8722)`
    + 平常我们电脑直接打 `0` 和 `=` 号之间的键，输出的是连字及减号符 `-`，即相当于 `002D alt+x`，在一些无衬线字体中，不同符号字形差别大，建议区别开来使用。

## 链接

对于同一网站下的 HTML 页面及其链接指向的资源：

- 如果指向的资源位置不变，HTML 页面位置可变，则使用忽略协议和域名的绝对链接；
- 如果指向的资源和 HTML 页面的位置关系不变，访问地址的子路径可变，则使用相对链接；

    ```markdown
    # 完整链接
    [a full path](https://www.example.com/figures/fig1.png)
    
    # 网站内：忽略协议 https 和域名 www.example.com
    [a absolute path](/figures/fig1.png) # 前导斜杠表示网站的根目录
    
    # 网站内：相对链接
    [a relative path](../figures/fig1.png) # .. 表上一级目录
    ```

在 Github 中一般使用相对路径，便于仓库克隆，并可使用相对链接操作符：

- `./` 当前目录
- `../` 上级目录
- `../../` 上上级目录

## 锚点

每一个标题都是一个锚点，引用格式为：`[引用文本处](#标题名)`。注意，标题中的英文字母都被转化为小写字母了。

## 公式

- [Cmd Markdown 公式指导手册](https://www.zybuluo.com/codeep/note/163962)

## 语法高亮

- [代码支持列表](https://github.com/github/linguist)

## +HTML

注意不同平台对 Markdown 的渲染/解析工具不一定都支持混合以下 HTML 标记！

* 强制换行 `<br/>`
* [预定义格式文本](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/pre)，保留原格式，包括空格等
    
    ```html
    <pre>
    ...
    </pre>
    ```

* 在引用时，作者/来源右对齐
    
    ```html
    > quote
    > [—— Author, Year]{style="float:right"}
    ```

* 文本居中
    
    ```html
    <p style="text-align:center;"> ~ ~ ~ ~ ~ (:３っ)כּ ~ ~ ~ ~ ~ </p>
    <div align='center'> ~ ~ ~ </div>
    ```

* [脚注](https://github.com/seamusdemora/seamusdemora.github.io/blob/master/GFM_FootnotesWithReturnFeature.md)
    
    ```
    <sup id="a1">[1](#f1)</sup>
    
    <b id="f1">1</b> ... [↩](#a1)
    ```

## GFM

- [官方教程](https://github.github.com/gfm/)
- [基本撰写和格式语法](https://docs.github.com/cn/free-pro-team@latest/github/writing-on-github/basic-writing-and-formatting-syntax)
- [表情符号](https://www.webfx.com/tools/emoji-cheat-sheet/)
- [README文件语法解读，即Github Flavored Markdown语法介绍](https://github.com/guodongxiaren/README)
- [Markdown Cheatsheet 中文版](https://gist.github.com/billy3321/1001749662c370887c63bb30f26c9e6e)
- [[译] GitHub 风格的 Markdown 语法](https://github.com/baixing/FE-Blog/issues/6)
- [[译] GitHub 上的书写方式](https://github.com/baixing/FE-Blog/issues/5)

## Pandoc

- [官方教程](https://pandoc.org/MANUAL.html)
