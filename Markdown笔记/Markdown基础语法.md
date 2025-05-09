---
title: Basic Syntax | Markdown Guide
source: https://www.markdownguide.org/basic-syntax/
author: Matt Cone
published: 2025/05/08
created: 2025-05-08
description: The Markdown elements outlined in the original design document.
tags:
  - clippings
---
## 基本语法

原始设计文档中概述的 Markdown 元素。

## 概述

几乎所有 Markdown 应用都支持原始 Markdown 设计文档中概述的基本语法。Markdown 处理器之间存在一些细微的差异和出入——只要有可能，这些差异和出入都会在文中注明。基础语法之后还有[[Markdown扩展语法]]

## 标题

要创建标题，请在单词或短语前添加数字符号（\`#\`）。您使用的数字符号的数量应与标题级别对应。例如，要创建三级标题（\`

### \`），请使用三个数字符号（例如，\`### 我的标题\`）。

| Markdown | HTML | 渲染输出 |
| --- | --- | --- |
| `# 一级标题` | `<h1> 一级标题</h1>` | ## 一级标题 |
| `## 二级标题` | `<h2> 二级标题</h2>` | ## 二级标题 |
| `### 三级标题` | `<h3> 三级标题</h3>` | ### 三级标题 |
| `##### 四级标题` | `<h4> 四级标题</h4>` | #### 标题等级 4 |
| `###### 标题等级 5` | `<h5> 标题等级 5</h5>` | ##### 标题等级 5 |
| `######六级标题` | `<h6> 六级标题</h6>` | ###### 六级标题 |

### 替换语法

或者，在文本下方添加任意数量的 \`==\` 字符创建一级标题，或添加任意数量的 \`--\` 字符创建二级标题。

| Markdown | HTML | 渲染输出 |
| --- | --- | --- |
| `Heading level 1   ===============` | `<h1> 一级标题</h1>` | ## 一级标题 |
| `Heading level 2   ---------------` | `<h2> 二级标题</h2>` | ## 二级标题 |

### 标题最佳实践

Markdown 应用程序对于编号标签（ `#` ）和标题名称之间是否缺少空格的处理方式并不统一。为了兼容性，始终在编号标签和标题名称之间添加空格。

| ✅ 做这个                                           | ❌ 不要这样做                                   |
| ----------------------------------------------- | ----------------------------------------- |
| `            # Here's a Heading               ` | `            #Here's a Heading          ` |


你还应该在标题前后添加空行以保持兼容性。

| ✅ 做这个 | ❌ 不要这样做 |
| --- | --- |
| `          Try to put a blank line before...               # Heading               ...and after a heading.          ` | `          Without blank lines, this might not look right.           # Heading           Don't do this!          ` |

## 段落

要创建段落，请使用空行分隔一个或多个文本行。

| Markdown | HTML | 渲染输出 |
| --- | --- | --- |
| `            I really like using Markdown.                 I think I'll use it to format all of my documents from now on.          ` | `<p>I really like using Markdown.</p>               <p>I think I'll use it to format all of my documents from now on.</p>` | 我真的很喜欢使用 Markdown。  我想我会用它来格式化我所有的文档。 |

### 段落最佳实践

如果段落不在列表中，不要用空格或制表符缩进段落。

| ✅ 做这个 | ❌ 不要这样做 |
| --- | --- |
| `            Don't put tabs or spaces in front of your paragraphs.                 Keep lines left-aligned like this.               ` | `              This can result in unexpected         formatting problems.                 Don't add tabs or spaces in front of paragraphs.          ` |

## 换行

要创建换行或新行（ `<br>` ），在行尾输入两个或多个空格，然后按回车键。

| Markdown | HTML | 渲染输出 |
| --- | --- | --- |
| `            This is the first line.               And this is the second line.          ` | `<p>This is the first line.<br>            And this is the second line.</p>` | 这是第一行。   这是第二行。 |

### 换行最佳实践

在几乎所有的 Markdown 应用中，你可以使用两个或多个空格（通常被称为“尾随空格”）来换行，但这存在争议。在编辑器中很难看到尾随空格，许多人会不小心或有意地在每个句子后加上两个空格。因此，你可能希望使用除尾随空格以外的其他方式来换行。如果你的 Markdown 应用 [支持 HTML](https://www.markdownguide.org/basic-syntax/#html) ，你可以使用 `<br>` HTML 标签。

为了兼容性，在行尾使用尾随空格或 `<br>` HTML 标签。

有两个其他选项我不推荐使用。CommonMark 和其他一些轻量级标记语言允许你在行的末尾输入反斜杠（\` `\` \`），但并非所有 Markdown 应用都支持这一点，所以从兼容性角度来看，这不是一个很好的选项。而且至少有两种轻量级标记语言不需要在行的末尾输入任何内容——只需输入回车，它们就会创建一个换行符。

| ✅ 做这个 | ❌ 不要这样做 |
| --- | --- |
| `            First line with two spaces after.               And the next line.                 First line with the HTML tag after.<br>             And the next line.               ` | `          First line with a backslash after.\           And the next line.               First line with nothing after.           And the next line.               ` |

## 强调

您可以通过将文本加粗或斜体来添加强调。

### 粗体

要加粗文本，在单词或短语前后添加两个星号或下划线。要强调单词中间的部分，在字母周围不添加空格地添加两个星号。

| Markdown | HTML | 渲染输出 |
| --- | --- | --- |
| `我真的很喜欢**粗体文本**。` | `I just love <strong>bold text</strong>.` | 我就是喜欢 **粗体文字** 。 |
| `我只是喜欢__粗体文本__。` | `I just love <strong>bold text</strong>.` | 我就是喜欢 **粗体文字** 。 |
| `爱是勇敢` | `爱**是**勇敢` | 爱 **是** 粗体 |

#### 粗体最佳实践

Markdown 应用程序对于如何处理单词中间的下划线并不一致。为了兼容性，使用星号来加粗单词中间的部分以强调。

| ✅ 做这个 | ❌ 不要这样做 |
| --- | --- |
| `            Love**is**bold          ` | `            Love__is__bold          ` |

### 斜体

要斜体化文本，请在单词或短语前后各加一个星号或下划线。要在单词中间加斜体以强调，请在不加空格的情况下加一个星号。

| Markdown | HTML | 渲染输出 |
| --- | --- | --- |
| `Italicized text is the *cat's meow*.` | `Italicized text is the <em>cat's meow</em>.` | 斜体文本是 *猫的叫声* 。 |
| `Italicized text is the _cat's meow_.` | `Italicized text is the <em>cat's meow</em>.` | 斜体文本是 *猫的叫声* 。 |
| `一只*猫*喵` | `一只*猫*喵` | 一 *只* 猫喵 |

#### 斜体最佳实践

Markdown 应用程序对于如何处理单词中间的下划线并不一致。为了兼容性，使用星号来强调单词中间的部分。

| ✅ 做这个 | ❌ 不要这样做 |
| --- | --- |
| `            A*cat*meow          ` | `            A_cat_meow          ` |

### 粗体和斜体

要同时强调文本的粗体和斜体，请在单词或短语前后添加三个星号或下划线。要强调单词中间的部分，请在字母周围不添加空格地添加三个星号。

| Markdown | HTML | 渲染输出 |
| --- | --- | --- |
| `This text is ***really important***.` | `This text is <em><strong>really important</strong></em>.` | 这段文字是 ***非常重要*** 。 |
| `This text is ___really important___.` | `This text is <em><strong>really important</strong></em>.` | 这段文字是 ***非常重要*** 。 |
| `This text is __*really important*__.` | `This text is <em><strong>really important</strong></em>.` | 这段文字是 ***非常重要*** 。 |
| `This text is **_really important_**.` | `This text is <em><strong>really important</strong></em>.` | 这段文字是 ***非常重要*** 。 |
| `This is really***very***important text.` | `This is really<em><strong>very</strong></em>important text.` | 这段文字非常重要 ***非常*** 。 |

#### 粗体和斜体最佳实践

Markdown 应用程序对于如何处理单词中间的下划线并不一致。为了兼容性，请使用星号来强调单词中间的部分进行粗体和斜体。

| ✅ 做这个 | ❌ 不要这样做 |
| --- | --- |
| `            This is really***very***important text.          ` | `            This is really___very___important text.          ` |

## 引用块

要创建一个引用块，在段落前添加一个 `>` 。

```
> Dorothy followed her through many of the beautiful rooms in her castle.
```

渲染后的输出看起来像这样：

> 多萝西跟着她穿过城堡里许多美丽的房间。

### 多段落引用块

引用块可以包含多个段落。在段落之间的空白行上添加一个 `>` 。

```
> Dorothy followed her through many of the beautiful rooms in her castle.
>
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

渲染后的输出看起来像这样：

> 多萝西跟着她穿过城堡里许多美丽的房间。
> 
> 那个女巫让她擦洗锅和壶，打扫地板，并给炉火添柴。

### 嵌套引用块

引用块可以嵌套。在要嵌套的段落前加上 `>>` 。

```
> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

渲染后的输出看起来像这样：

> 多萝西跟着她穿过城堡里许多美丽的房间。
> 
> > 那个女巫让她擦洗锅和壶，打扫地板，并给炉火添柴。

### 包含其他元素的引用块

引用块可以包含其他 Markdown 格式的元素。并非所有元素都可以使用——你需要尝试看看哪些元素有效。

```
> #### The quarterly results look great!
>
> - Revenue was off the chart.
> - Profits were higher than ever.
>
>  *Everything* is going according to **plan**.
```

渲染后的输出看起来像这样：

> #### 每季度结果看起来很棒！
> 
> - 收入创下了新高。
> - 利润比以往任何时候都要高。
> 
> *一切* 都按照 **计划** 进行。

### 引用块最佳实践

为了兼容性，在引用块前后添加空行。

| ✅ 做这个 | ❌ 不要这样做 |
| --- | --- |
| `          Try to put a blank line before...               > This is a blockquote               ...and after a blockquote.          ` | `          Without blank lines, this might not look right.           > This is a blockquote           Don't do this!          ` |

## 列表

您可以将项目组织成有序和无序列表。

### 有序列表

要创建有序列表，请添加带有数字和句点的行项目。数字不必按数字顺序排列，但列表应从数字一开始。

| Markdown | HTML | 渲染输出 |
| --- | --- | --- |
| `          1. First item           2. Second item           3. Third item           4. Fourth item        ` | `          <ol>               <li>First item</li>               <li>Second item</li>               <li>Third item</li>               <li>Fourth item</li>           </ol>        ` | 1. 第一个项目 2. 第二个项目 3. 第三项 4. 第四项 |
| `            1. First item             1. Second item             1. Third item             1. Fourth item          ` | `            <ol>                 <li>First item</li>                 <li>Second item</li>                 <li>Third item</li>                 <li>Fourth item</li>             </ol>          ` | 1. 第一个项目 2. 第二个项目 3. 第三项 4. 第四项 |
| `            1. First item             8. Second item             3. Third item             5. Fourth item          ` | `            <ol>                 <li>First item</li>                 <li>Second item</li>                 <li>Third item</li>                 <li>Fourth item</li>             </ol>          ` | 1. 第一个项目 2. 第二个项目 3. 第三项 4. 第四项 |
| `            1. First item             2. Second item             3. Third item                 1. Indented item                 2. Indented item             4. Fourth item          ` | `            <ol>                 <li>First item</li>                 <li>Second item</li>                 <li>Third item                     <ol>                         <li>Indented item</li>                         <li>Indented item</li>                     </ol>                 </li>                 <li>Fourth item</li>             </ol>          ` | 1. 第一个项目 2. 第二个项目 3. 第三项 	1. 缩进项目 	2. 缩进项目 4. 第四项 |

#### Ordered List Best Practices

CommonMark and a few other lightweight markup languages let you use a parenthesis (`)`) as a delimiter (e.g., `1) First item`), but not all Markdown applications support this, so it isn’t a great option from a compatibility perspective. For compatibility, use periods only.

| ✅ 做这个 | ❌ 不要这样做 |
| --- | --- |
| `            1. First item             2. Second item          ` | `            1) First item             2) Second item          ` |

### 无序列表

要创建无序列表，在行项目前添加短横线（ `-` ）、星号（ `*` ）或加号（ `+` ）。缩进一个或多个项目以创建嵌套列表。

| Markdown | HTML | 渲染输出 |
| --- | --- | --- |
| `            - First item             - Second item             - Third item             - Fourth item          ` | `            <ul>                 <li>First item</li>                 <li>Second item</li>                 <li>Third item</li>                 <li>Fourth item</li>             </ul>          ` | - 第一个项目 - 第二个项目 - 第三项 - 第四项 |
| `            * First item             * Second item             * Third item             * Fourth item          ` | `            <ul>                 <li>First item</li>                 <li>Second item</li>                 <li>Third item</li>                 <li>Fourth item</li>             </ul>          ` | - 第一个项目 - 第二个项目 - 第三项 - 第四项 |
| `            + First item             + Second item             + Third item             + Fourth item          ` | `            <ul>                 <li>First item</li>                 <li>Second item</li>                 <li>Third item</li>                 <li>Fourth item</li>             </ul>          ` | - 第一个项目 - 第二个项目 - 第三项 - 第四项 |
| `            - First item             - Second item             - Third item                 - Indented item                 - Indented item             - Fourth item          ` | `            <ul>                 <li>First item</li>                 <li>Second item</li>                 <li>Third item                     <ul>                         <li>Indented item</li>                         <li>Indented item</li>                     </ul>                 </li>                 <li>Fourth item</li>             </ul>          ` | - 第一个项目 - 第二个项目 - 第三项 	- 缩进项目 	- 缩进项目 - 第四项 |

#### 以数字开头无序列表项目

如果您需要在无序列表项目前以数字后跟句点开头，可以使用反斜杠（ `\` ）来转义句点。

| Markdown | HTML | 渲染输出 |
| --- | --- | --- |
| `            - 1968\. A great year!             - I think 1969 was second best.          ` | `            <ul>                 <li>1968. A great year!</li>                 <li>I think 1969 was second best.</li>             </ul>          ` | - 1968年，真是个伟大的年份！ - 我觉得1969年第二好。 |

#### 无序列表最佳实践

Markdown 应用程序对于如何处理同一列表中的不同分隔符并不一致。为了兼容性，不要在同一列表中混合使用不同的分隔符——选择一个并坚持使用它。

| ✅ 做这个 | ❌ 不要这样做 |
| --- | --- |
| `            - First item             - Second item             - Third item             - Fourth item          ` | `            + First item             * Second item             - Third item             + Fourth item          ` |

### 在列表中添加元素

要在列表中添加另一个元素并保持列表的连续性，请将元素缩进四个空格或一个制表符，如下面的示例所示。

#### 段落

```
* This is the first list item.
* Here's the second list item.

    I need to add another paragraph below the second list item.

* And here's the third list item.
```

渲染后的输出看起来像这样：

- 这是列表的第一项。
- 这是第二个列表项。
	我需要在第二个列表项下方添加另一个段落。
- 这是第三个列表项。

#### 引用块

```
* This is the first list item.
* Here's the second list item.

    > A blockquote would look great below the second list item.

* And here's the third list item.
```

渲染后的输出看起来像这样：

- 这是列表的第一项。
- 这是第二个列表项。
	> 在第二个列表项下方，一个引用块看起来会很棒。
- 这是第三个列表项。

#### 代码块

[代码块](https://www.markdownguide.org/basic-syntax/#code-blocks) 通常缩进四个空格或一个制表符。当它们在列表中时，缩进八个空格或两个制表符。

```
1. Open the file.
2. Find the following code block on line 21:

        <html>
          <head>
            <title>Test</title>
          </head>

3. Update the title to match the name of your website.
```

渲染后的输出看起来像这样：

1. 打开文件。
2. 在第21行找到以下代码块：
	```
	<html>
	   <head>
	     <title>Test</title>
	   </head>
	```
3. 将标题更新为与您的网站名称匹配。

#### 图片

```
1. Open the file containing the Linux mascot.
2. Marvel at its beauty.

    ![Tux, the Linux mascot](/assets/images/tux.png)

3. Close the file.
```

渲染后的输出看起来像这样：

1. 打开包含 Linux 吉祥物的文件。
2. 欣赏它的美丽。
	![Tux, the Linux mascot](https://mdg.imgix.net/assets/images/tux.png)
3. 关闭文件。

#### 列表

你可以将无序列表嵌套在有序列表中，反之亦然。

```
1. First item
2. Second item
3. Third item
    - Indented item
    - Indented item
4. Fourth item
```

渲染后的输出看起来像这样：

1. 第一个项目
2. 第二个项目
3. 第三项
	- 缩进项目
	- 缩进项目
4. 第四项

## 代码

要表示代码，请将单词或短语用反引号（ `` ` `` ）括起来。

| Markdown | HTML | 渲染输出 |
| --- | --- | --- |
| ``At the command prompt, type `nano`.`` | `At the command prompt, type <code>nano</code>. ` | 在命令提示符下，输入 `nano` 。 |

### 转义反引号

如果您要表示的代码包含一个或多个反引号，可以通过将单词或短语用双反引号（ ` `` ` ）括起来来转义。

| Markdown | HTML | 渲染输出 |
| --- | --- | --- |
| ``` ``Use `code` in your Markdown file.`` ``` | ``<code>Use `code` in your Markdown file.</code>`` | ``Use `code` in your Markdown file.`` |

### 代码块

要创建代码块，请将块中的每一行缩进至少四个空格或一个制表符。

```
<html>
      <head>
      </head>
    </html>
```

渲染后的输出看起来像这样：

```
<html>
  <head>
  </head>
</html>
```

## 水平线

要创建水平线，请在单独一行上使用三个或更多的星号（ `***` ）、短横线（ `---` ）或下划线（ `___` ）。

```
***

---

_________________
```

所有三个的渲染输出看起来都一样：

---

### 水平线最佳实践

为了兼容性，在水平线前后放置空行。

| ✅ 做这个 | ❌ 不要这样做 |
| --- | --- |
| `          Try to put a blank line before...               ---               ...and after a horizontal rule.          ` | `          Without blank lines, this would be a heading.           ---           Don't do this!          ` |

## 链接

要创建链接，将链接文本放在括号内（例如， `[Duck Duck Go]` ），然后立即在后面跟上 URL（例如， `(https://duckduckgo.com)` ）。

```
My favorite search engine is [Duck Duck Go](https://duckduckgo.com).
```

渲染后的输出看起来像这样：

我最喜欢的搜索引擎是 [Duck Duck Go](https://duckduckgo.com/) 。

### 添加标题

您可以可选地为链接添加标题。当用户将鼠标悬停在链接上时，该标题将作为工具提示显示。要添加标题，请在 URL 后用引号括起来。

渲染后的输出看起来像这样：

我最喜欢的搜索引擎是 [Duck Duck Go](https://duckduckgo.com/ "The best search engine for privacy") 。

### URL 和电子邮件地址

快速将 URL 或电子邮件地址转换为链接，将其括在尖括号中。

```
<https://www.markdownguide.org>
<fake@example.com>
```

渲染后的输出看起来像这样：

[https://www.markdownguide.org](https://www.markdownguide.org/)  
[fake@example.com](https://www.markdownguide.org/basic-syntax/)

### 格式化链接

要强调链接，请在方括号和括号前后添加星号。要表示代码链接，请在方括号中添加反引号。 [强调](https://www.markdownguide.org/basic-syntax/#emphasis) 链接，请在方括号和括号前后添加星号。要表示 [代码](https://www.markdownguide.org/basic-syntax/#code) 链接，请在方括号中添加反引号。

```
I love supporting the **[EFF](https://eff.org)**.
This is the *[Markdown Guide](https://www.markdownguide.org)*.
See the section on [\`code\`](#code).
```

渲染后的输出看起来像这样：

我喜欢支持 [电子前沿基金会](https://eff.org/) （ **[EFF](https://eff.org/)** ）。  
这是 [*Markdown 指南*](https://www.markdownguide.org/) 。  
查看关于 [`代码`](https://www.markdownguide.org/basic-syntax/#code) 的部分。

### 引用式链接

引用式链接是一种特殊的链接，它使 Markdown 中的 URL 更容易显示和阅读。引用式链接由两部分组成：一部分是与文本保持内联的部分，另一部分是存储在文件的其他位置以保持文本易于阅读的部分。

#### 格式化链接的第一部分

引用式链接的第一部分使用两组方括号进行格式化。第一组方括号包围应显示为链接的文本。第二组方括号显示用于指向文档中存储在其他地方的链接的标签。

虽然不是必需的，但在第一组和第二组方括号之间可以包含一个空格。第二组方括号中的标签不区分大小写，可以包含字母、数字、空格或标点符号。

这意味着以下示例格式在链接的第一部分大致等效：

- `[霍比特洞][1]`
- `[霍比特洞] [1]`

#### 格式化链接的第二部分

参考样式链接的第二部分使用以下属性进行格式化：

1. 标签用括号括起来，后面紧跟一个冒号和至少一个空格（例如， `[标签]: `）。
2. 链接的 URL，你可以选择性地用尖括号括起来。
3. 链接的可选标题，你可以用双引号、单引号或括号括起来。

这意味着以下示例格式对于链接的第二部分都是大致等效的。

- `[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle`
- `[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle "Hobbit lifestyles"`
- `[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle 'Hobbit lifestyles'`
- `[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle (Hobbit lifestyles)`
- `[1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> "Hobbit lifestyles"`
- `[1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> 'Hobbit lifestyles'`
- `[1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> (Hobbit lifestyles)`

你可以将链接的第二部分放在 Markdown 文档中的任何位置。有些人会在它们出现的段落后面立即放置它们，而另一些人则会在文档的末尾放置它们（就像尾注或脚注一样）。

#### 一个将各部分放在一起示例

假设你在段落中添加了一个 [标准 URL 链接](https://www.markdownguide.org/basic-syntax/#links)

```
In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends
of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to
eat: it was a [hobbit-hole](https://en.wikipedia.org/wiki/Hobbit#Lifestyle "Hobbit lifestyles"), and that means comfort.
```

尽管它可能指向有趣的其他信息，但显示的 URL 除了让文本更难阅读外，并没有给现有的原始文本增加多少内容。要解决这个问题，你可以这样格式化 URL：

```
In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends
of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to
eat: it was a [hobbit-hole][1], and that means comfort.

[1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> "Hobbit lifestyles"
```

在上述两个例子中，渲染的输出将是相同的：

> 在地洞里住着一个霍比特人。不是个又脏又湿、满是蚯蚓头和黏糊糊气味的洞，也不是个干燥、空旷、沙土飞扬、既不能坐也不能吃的洞：它是一个 [霍比特人的洞](https://en.wikipedia.org/wiki/Hobbit#Lifestyle "Hobbit lifestyles") ，这意味着舒适。

以及链接的 HTML 代码将是：

```
<a href="https://en.wikipedia.org/wiki/Hobbit#Lifestyle" title="Hobbit lifestyles">hobbit-hole</a>
```

### 链接最佳实践

Markdown 应用在处理 URL 中间的空格上并不统一。为了兼容性，建议使用 `%20` 对空格进行 URL 编码。或者，如果你的 Markdown 应用 [支持 HTML](https://www.markdownguide.org/basic-syntax/#html) ，你也可以使用 `a` HTML 标签。

| ✅ 做这个 | ❌ 不要这样做 |
| --- | --- |
| `          [link](https://www.example.com/my%20great%20page)               <a href="https://www.example.com/my great page">link</a>               ` | `          [link](https://www.example.com/my great page)               ` |

URL 中间的括号也可能存在问题。为了兼容性，建议使用 `(`)与 `%28` 对左括号进行 URL 编码，以及使用 `)` 与 `%29` 对右括号进行 URL 编码。或者，如果你的 Markdown 应用 [支持 HTML](https://www.markdownguide.org/basic-syntax/#html) ，你也可以使用 `a` HTML 标签。

| ✅ 做这个 | ❌ 不要这样做 |
| --- | --- |
| `          [a novel](https://en.wikipedia.org/wiki/The_Milagro_Beanfield_War_%28novel%29)               <a href="https://en.wikipedia.org/wiki/The_Milagro_Beanfield_War_(novel)">a novel</a>               ` | `          [a novel](https://en.wikipedia.org/wiki/The_Milagro_Beanfield_War_(novel))          ` |

## 图片

要添加图片，请添加感叹号（\`!\`），然后括号内输入替代文本，括号内输入图片资源路径或 URL。您可以在路径或 URL 后用引号添加可选的标题。

```
![The San Juan Mountains are beautiful!](/assets/images/san-juan-mountains.jpg "San Juan Mountains")
```

渲染后的输出看起来像这样：

![The San Juan Mountains are beautiful!](https://mdg.imgix.net/assets/images/san-juan-mountains.jpg "San Juan Mountains")

### 链接图片

要在图像中添加链接，将图像的 Markdown 代码括起来，然后在括号中添加链接。

```
[![An old rock in the desert](/assets/images/shiprock.jpg "Shiprock, New Mexico by Beau Rogers")](https://www.flickr.com/photos/beaurogers/31833779864/in/photolist-Qv3rFw-34mt9F-a9Cmfy-5Ha3Zi-9msKdv-o3hgjr-hWpUte-4WMsJ1-KUQ8N-deshUb-vssBD-6CQci6-8AFCiD-zsJWT-nNfsgB-dPDwZJ-bn9JGn-5HtSXY-6CUhAL-a4UTXB-ugPum-KUPSo-fBLNm-6CUmpy-4WMsc9-8a7D3T-83KJev-6CQ2bK-nNusHJ-a78rQH-nw3NvT-7aq2qf-8wwBso-3nNceh-ugSKP-4mh4kh-bbeeqH-a7biME-q3PtTf-brFpgb-cg38zw-bXMZc-nJPELD-f58Lmo-bXMYG-bz8AAi-bxNtNT-bXMYi-bXMY6-bXMYv)
```

渲染后的输出看起来像这样：

[![An old rock in the desert](https://mdg.imgix.net/assets/images/shiprock.jpg "Shiprock, New Mexico by Beau Rogers")](https://www.flickr.com/photos/beaurogers/31833779864/in/photolist-Qv3rFw-34mt9F-a9Cmfy-5Ha3Zi-9msKdv-o3hgjr-hWpUte-4WMsJ1-KUQ8N-deshUb-vssBD-6CQci6-8AFCiD-zsJWT-nNfsgB-dPDwZJ-bn9JGn-5HtSXY-6CUhAL-a4UTXB-ugPum-KUPSo-fBLNm-6CUmpy-4WMsc9-8a7D3T-83KJev-6CQ2bK-nNusHJ-a78rQH-nw3NvT-7aq2qf-8wwBso-3nNceh-ugSKP-4mh4kh-bbeeqH-a7biME-q3PtTf-brFpgb-cg38zw-bXMZc-nJPELD-f58Lmo-bXMYG-bz8AAi-bxNtNT-bXMYi-bXMY6-bXMYv)

## 转义字符

要在 Markdown 文档中显示一个原本用于格式化文本的字符，请在该字符前加上反斜杠（ `\` ）。

```
\* Without the backslash, this would be a bullet in an unordered list.
```

渲染后的输出看起来像这样：

\* 如果不加反斜杠，这将是一个无序列表中的项目符号。

### 可以转义的字符

你可以使用反斜杠来转义以下字符。

| 字符   | 名称                                                                                                     |
| ---- | ------------------------------------------------------------------------------------------------------ |
| \\   | 反斜杠                                                                                                    |
| \`   | 反引号（另见 [代码中转义反引号](https://www.markdownguide.org/basic-syntax/#escaping-backticks) ）                    |
| \*   | 星号                                                                                                     |
| \_   | 下划线                                                                                                    |
| { }  | 大括号                                                                                                    |
| 空方括号 | 括号                                                                                                     |
| 尖括号  | 角括号                                                                                                    |
| ( )  | 括号                                                                                                     |
| #    | **#**号                                                                                                 |
| +    | 加号                                                                                                     |
| \-   | 减号（连字符）                                                                                                |
| .    | 点号                                                                                                     |
| !    | 感叹号                                                                                                    |
| \|   | 管道符（另见 [表格中转义管道符](https://www.markdownguide.org/extended-syntax/#escaping-pipe-characters-in-tables) ） |

## HTML

许多 Markdown 应用程序允许您在 Markdown 格式的文本中使用 HTML 标签。如果您更喜欢某些 HTML 标签而不是 Markdown 语法，这会很有帮助。例如，有些人发现使用 HTML 标签来插入图片更容易。使用 HTML 在您需要更改元素属性时也很有帮助，比如指定 [文本的颜色](https://www.markdownguide.org/hacks/#color) 或更改图片的宽度。

要使用 HTML，请将标签放置在您的 Markdown 格式化文件中。

```
This **word** is bold. This <em>word</em> is italic.
```

渲染后的输出看起来像这样：

这个 **词** 是粗体的。这个 *词* 是斜体的。

### HTML 最佳实践

由于安全原因，并非所有 Markdown 应用程序都支持在 Markdown 文档中使用 HTML。如有疑问，请查阅您所使用的 Markdown 应用程序的文档。有些应用程序仅支持 HTML 标签的子集。

使用空行将块级 HTML 元素，如 `<div>` 、 `<table>` 、 `<pre>` 和 `<p>` ，与周围内容分开。尽量不要用制表符或空格缩进标签——这可能会干扰格式。

您不能在块级 HTML 标签内使用 Markdown 语法。例如， `<p> 斜体和**粗体**</p>` 将不起作用。

[![Markdown Guide book cover](https://mdg.imgix.net/assets/images/book-cover.jpg)](https://www.markdownguide.org/book/)