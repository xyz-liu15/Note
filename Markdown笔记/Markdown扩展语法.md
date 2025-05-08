---
title: Extended Syntax | Markdown Guide
source: https://www.markdownguide.org/extended-syntax/
author: Matt Cone
published: 2025/05/08
created: 2025-05-08
description: Advanced features that build on the basic Markdown syntax.
tags:
  - clippings
---
## 扩展语法

高级功能建立在Markdown基础语法之上。

## 概述

原始 Markdown 设计文档中概述的基本语法添加了许多日常所需元素，但这并不足以满足某些人的需求。这就是扩展语法发挥作用的地方。 [基本语法](https://www.markdownguide.org/basic-syntax/)

许多人和组织主动扩展了基本语法，通过添加表格、代码块、语法高亮、URL 自动链接和脚注等元素。这些元素可以通过使用一种基于基本 Markdown 语法的轻量级标记语言来启用，或者通过向兼容的 Markdown 处理器添加扩展。

## 可用性

并非所有 Markdown 应用都支持扩展语法元素。您需要检查您所使用的轻量级标记语言是否支持您想要使用的扩展语法元素。如果它不支持，您可能仍然可以在您的 Markdown 处理器中启用扩展。

### 轻量级标记语言

有几种轻量级标记语言是 Markdown 的 *超集* 。它们包括基本语法，并通过添加额外的元素（如表格、代码块、语法高亮、URL 自动链接和脚注）来扩展它。许多最流行的 Markdown 应用使用以下一种轻量级标记语言：

- [CommonMark](https://commonmark.org/)
- [GitHub 风格的 Markdown (GFM)](https://github.github.com/gfm/)
- [Markdown Extra](https://michelf.ca/projects/php-markdown/extra/)
- [多重 Markdown](https://fletcherpenney.net/multimarkdown/)
- [R 标记语言](https://rmarkdown.rstudio.com/)

### Markdown 处理器

有 [数十种 Markdown 处理器](https://github.com/markdown/markdown.github.com/wiki/Implementations) 可用。其中许多允许您添加扩展以启用扩展语法元素。请查阅您的处理器的文档以获取更多信息。

## 表格

要添加表格，使用三个或更多连字符 (`---`) 来创建每列的标题，并使用管道 (`|`) 来分隔每列。为了兼容性，您还应在行的两端各添加一个管道。

渲染后的输出看起来像这样：

| 语法 | 描述 |
| --- | --- |
| 标题 | 标题 |
| 段落 | 文本 |

单元格宽度可以不同，如下所示。渲染后的输出看起来会一样。

### 对齐

您可以通过在表头行的短横线左侧、右侧或两侧添加冒号（`:`）来将文本在列中对齐到左、右或居中。

渲染后的输出看起来像这样：

| 语法 | 描述 | 测试文本 |
| --- | --- | --- |
| 标题 | 标题 | 这里是这个 |
| 段落 | 文本 | 更多 |

### 表格中的文本格式化

您可以在表格内格式化文本。例如，您可以添加 [链接](https://www.markdownguide.org/basic-syntax/#links) 、 [代码](https://www.markdownguide.org/basic-syntax/#code-1) （仅限反引号(`` ` ``)中的单词或短语，不包括 [代码块](https://www.markdownguide.org/basic-syntax/#code-blocks) ），以及 [强调](https://www.markdownguide.org/basic-syntax/#emphasis) 。

你不能使用标题、引用块、列表、水平规则、图像或大多数 HTML 标签。

### 转义表格中的管道字符

您可以通过使用其 HTML 字符代码（ `|` ）在表格中显示管道符（ `|` ）。

## 代码块

基本的 Markdown 语法允许你通过将行缩进四个空格或一个制表符来创建 [代码块](https://www.markdownguide.org/basic-syntax/#code-blocks) 。如果你觉得不方便，可以尝试使用围栏代码块。根据你的 Markdown 处理器或编辑器，你会在代码块前后使用三个反引号（ ` ``` ` ）或三个波浪号（ `~~~` ）。最棒的是？你不需要缩进任何行！

```
\`\`\`
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
\`\`\`
```

渲染后的输出看起来像这样：

```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

### 语法高亮

许多 Markdown 处理器支持围栏代码块的语法高亮。此功能允许您为您的代码所写的任何语言添加颜色高亮。要添加语法高亮，请在围栏代码块前的反引号旁边指定一种语言。

```
\`\`\`json
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
\`\`\`
```

渲染后的输出看起来像这样：

```json
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

## 脚注

Footnotes allow you to add notes and references without cluttering the body of the document. When you create a footnote, a superscript number with a link appears where you added the footnote reference. Readers can click the link to jump to the content of the footnote at the bottom of the page.

To create a footnote reference, add a caret and an identifier inside brackets (`[^1]`). Identifiers can be numbers or words, but they can’t contain spaces or tabs. Identifiers only correlate the footnote reference with the footnote itself — in the output, footnotes are numbered sequentially.

Add the footnote using another caret and number inside brackets with a colon and text (`[^1]: My footnote.`). You don’t have to put footnotes at the end of the document. You can put them anywhere except inside other elements like lists, block quotes, and tables.

```
Here's a simple footnote,[^1] and here's a longer one.[^bignote]

[^1]: This is the first footnote.

[^bignote]: Here's one with multiple paragraphs and code.

    Indent paragraphs to include them in the footnote.

    \`{ my code }\`

    Add as many paragraphs as you like.
```

渲染后的输出看起来像这样：

这里有一个简单的脚注 [^1] ，这里还有一个较长的脚注 [^2] 。

## 标题 ID

许多 Markdown 处理器支持自定义的标题 ID，例如 [标题](https://www.markdownguide.org/basic-syntax/#headings) —— 一些 Markdown 处理器会自动添加它们。添加自定义 ID 允许你直接链接到标题，并用 CSS 修改它们。要添加自定义标题 ID，请在同一行将自定义 ID 用花括号括起来。

```
### My Great Heading {#custom-id}
```

HTML 看起来像这样：

```html
<h3 id="custom-id">My Great Heading</h3>
```

### 链接到标题 ID

您可以通过创建一个带有井号（ `#` ）后跟自定义标题 ID 的标准链接来链接到文件中的标题。这些通常被称为 *锚链接* 。

| Markdown | HTML | 渲染输出 |
| --- | --- | --- |
| `[标题 ID](#标题-id)` | ` <a href="#heading-ids">Heading IDs</a>` | [标题 ID](https://www.markdownguide.org/extended-syntax/#heading-ids) |

其他网站可以通过在网页的完整 URL 中添加自定义标题 ID 来链接到该标题（例如， `[Heading IDs](https://www.markdownguide.org/extended-syntax#heading-ids)` ）。

## 定义列表

一些 Markdown 处理器允许你创建 *术语定义列表* ，以及它们相应的定义。要创建一个定义列表，在第一行输入术语。在下一行输入一个冒号后跟一个空格和定义。

```
First Term
: This is the definition of the first term.

Second Term
: This is one definition of the second term.
: This is another definition of the second term.
```

HTML 看起来像这样：

```html
<dl>
  <dt>First Term</dt>
  <dd>This is the definition of the first term.</dd>
  <dt>Second Term</dt>
  <dd>This is one definition of the second term. </dd>
  <dd>This is another definition of the second term.</dd>
</dl>
```

渲染后的输出看起来像这样：

第一个术语

这是第一个术语的定义。

第二个术语

这是第二个术语的一个定义。

这是第二个术语的另一个定义。

## 删除线

您可以通过在单词中间划一条水平线来删除文字。结果看起来 ~~像这样~~ 。这个功能允许您指示某些单词是错误而不是包含在文档中的。要删除文字，请在单词前后使用两个波浪号（ `~~` ）。

```
~~The world is flat.~~ We now know that the world is round.
```

渲染后的输出看起来像这样：

~~世界是平的。~~ 我们现在知道世界是圆的。

## 任务列表

任务列表（也称为 *复选框列表* 和 *待办事项列表* ）允许您创建带有复选框的列表。在支持任务列表的 Markdown 应用程序中，复选框将显示在内容旁边。要创建任务列表，请在任务列表项前添加短横线（ `-` ）和带空格的方括号（ `[ ]` ）。要选中复选框，请在方括号（ `[x]` ）之间添加一个 `x` 。

```
- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media
```

渲染后的输出看起来像这样：

![Markdown task list](https://www.markdownguide.org/assets/images/tasklist.png)

## 表情符号

向 Markdown 文件中添加表情符号有两种方法：将表情符号复制并粘贴到你的 Markdown 格式化的文本中，或者输入 *表情符号简码* 。

### 复制和粘贴表情符号

在大多数情况下，你可以直接从像 [Emojipedia](https://emojipedia.org/) 这样的来源复制表情符号并将其粘贴到你的文档中。许多 Markdown 应用程序将自动在 Markdown 格式化的文本中显示表情符号。你从 Markdown 应用程序导出的 HTML 和 PDF 文件应该显示表情符号。

### 使用 Emoji 短代码

一些 Markdown 应用程序允许您通过输入表情符号简码来插入表情符号。这些简码以冒号开头和结尾，并包含一个表情符号的名称。

```
Gone camping! :tent: Be back soon.

That is so funny! :joy:
```

渲染后的输出看起来像这样：

去露营了！⛺ 很快回来。

太搞笑了！😂

## 突出显示

这并不常见，但某些 Markdown 处理器允许你突出显示文本。结果看起来像 ==这样== 。要突出显示词语，请在词语前后各使用两个等号（ `==` ）。

```
I need to highlight these ==very important words==.
```

渲染后的输出看起来像这样：

我需要突出显示这些 ==非常重要的话== 。

或者，如果你的 Markdown 应用程序支持 [HTML](https://www.markdownguide.org/basic-syntax/#html) ，你可以使用 `mark` HTML 标签。

```html
I need to highlight these <mark>very important words</mark>.
```

## 下标

这并不常见，但某些 Markdown 处理器允许你使用 *下标* 将一个或多个字符稍微置于正常文本行的下方。要创建下标，请在字符前后各使用一个波浪号（ `~` ）。

```
H~2~O
```

渲染后的输出看起来像这样：

H <sub>2</sub> O

或者，如果你的 Markdown 应用支持 [HTML](https://www.markdownguide.org/basic-syntax/#html) ，你可以使用 `sub` HTML 标签。

```html
H<sub>2</sub>O
```

## 上标

这并不常见，但某些 Markdown 处理器允许你使用 *上标* 将一个或多个字符稍微置于正常文本行的上方。要创建上标，在字符前后使用一个尖括号符号(`^`)。

```
X^2^
```

渲染后的输出看起来像这样：

X <sup>2</sup>

或者，如果你的 Markdown 应用程序支持 [HTML](https://www.markdownguide.org/basic-syntax/#html) ，你可以使用 `sup` HTML 标签。

```html
X<sup>2</sup>
```

## 自动链接 URL

许多 Markdown 处理器会自动将 URL 转换为链接。这意味着如果你输入 http://www.example.com，你的 Markdown 处理器会自动将其转换为链接，即使你没有使用尖括号 [尖括号](https://www.markdownguide.org/basic-syntax/#links) 。

```
http://www.example.com
```

渲染后的输出看起来像这样：

[http://www.example.com](http://www.example.com/)

## 禁用自动链接 URL

如果您不希望 URL 自动链接，可以通过使用反引号将 URL 标记为代码来删除链接。 [使用反引号将 URL 标记为代码](https://www.markdownguide.org/basic-syntax/#code) 。

```
\`http://www.example.com\`
```

渲染后的输出看起来像这样：

`http://www.example.com`

[![Markdown Guide book cover](https://mdg.imgix.net/assets/images/book-cover.jpg)](https://www.markdownguide.org/book/)

###### 想了解更多 Markdown 吗？

[^1]: 这是第一个脚注。

[^2]: 这里有一个包含多个段落和代码的例子。

将段落缩进以包含它们在脚注中。

`{ my code }`

可以添加任意多的段落。