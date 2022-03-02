# Todo Tree 校对 ✔ [![translate-svg]][translate-list]

<!-- [![explain]][source] -->

[explain]: http://llever.com/explain.svg
[source]: https://github.com/chinanf-boy/Source-Explain
[translate-svg]: http://llever.com/translate.svg
[translate-list]: https://github.com/chinanf-boy/chinese-translate-list
[size-img]: https://packagephobia.now.sh/badge?p=Name
[size]: https://packagephobia.now.sh/result?p=Name

<!-- doc-templite START generated -->
<!-- repo = 'Gruntfuggly/todo-tree' -->
<!-- commit = '8eab71fc96b2467b4ba8a1424b30d0ca28eb05a7' -->
<!-- time = '2022-1-13' -->

| 翻译的原文 | 与日期       | 最新更新 | 更多                       |
| ---------- | ------------ | -------- | -------------------------- |
| [commit]   | ⏰ 2022-1-13 | ![last]  | [中文翻译][translate-list] |

[last]: https://img.shields.io/github/last-commit/Gruntfuggly/todo-tree.svg
[commit]: https://github.com/Gruntfuggly/todo-tree/tree/8eab71fc96b2467b4ba8a1424b30d0ca28eb05a7

<!-- doc-templite END generated -->

[![Build Status](https://travis-ci.org/Gruntfuggly/todo-tree.svg?branch=master)](https://travis-ci.org/Gruntfuggly/todo-tree)

此扩展可以快速搜索（使用[ripgrep](https://github.com/BurntSushi/ripgrep)）您的工作区，将那些 `TODO` 和 `FIXME` 等注释标记，并在活动栏的树视图中，显示它们。

> 可以从 活动栏 拖到 终端旁边（或您希望它位于的任何其他位置）。

单击树中的 **TODO** 将打开文件，并将光标放在包含 **TODO** 的行上。

找到的 TODOs 也会高亮显示。

_请看[wiki 英文](https://github.com/Gruntfuggly/todo-tree/wiki/Configuration-Examples) | [wiki 中文](./todo-tree.wiki/Configuration-Examples.zh.md) 有关配置示例。_

- [ ] TODO: 添加 wiki 中文

![screenshot](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/screenshot.png)

_注意了：_

- _用户的_ `rg.conf` _文件会被忽略。_

# 目录

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Todo Tree 校对 ✔ [![translate-svg]][translate-list]](#todo-tree-校对--translate-svgtranslate-list)
- [目录](#目录)
  - [Highlighting](#highlighting)
  - [安装](#安装)
    - [源代码](#源代码)
  - [头部操作](#头部操作)
  - [右键菜单](#右键菜单)
  - [命令](#命令)
    - [Tags](#tags)
    - [导出](#导出)
    - [切换范围](#切换范围)
  - [配置](#配置)
    - [多行 TODOs](#多行-todos)
    - [排除文件和目录](#排除文件和目录)
    - [Markdown 支持](#markdown-支持)
  - [Known Issues](#known-issues)
  - [Donate](#donate)
    - [Credits](#credits)
      - [Translations](#translations)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 译者示例

> vscode setting.json

```json
"todo-tree.highlights.defaultHighlight": {
    "icon": "alert",
    "background": "#caa4a43a",
    "foreground": "#df6f14",
    "opacity": 50
  },
  "todo-tree.highlights.customHighlight": {
    "TODO": {
      "background": "#caa4a43a",
      "foreground": "#df6f14"
    },
    "unsafe": {
      "background": "#f6f7f6",
      "foreground": "rgb(255,128,0)"
    },
    "BUG": {
      "icon": "bug"
    },
    "HACK": {
      "icon": "tools"
    },
    "FIXME": {
      "icon": "flame"
    },
    "XXX": {
      "icon": "$(close)"
    },
    "[ ]": {
    //   "background": "#ff000080"
    },
    "[x]": {
      "foreground": "#00ff0080"
    }
  },
  "todo-tree.general.tags": [
    "BUG",
    "unsafe",
    "HACK",
    "FIXME",
    "TODO",
    "XXX",
    "[ ]",
    "[x]"
  ],
```

## Highlighting

> *信息！：*如果您只想为标记（tags）设置不同的颜色，现在可以启用`todo-tree.highlights.useColourScheme`。这将应用一组颜色（可以更改），按照标记定义的顺序设置。

高亮配置: 使用`defaultHighlight`为所有标记设置高亮。如果需要以不同的方式配置各个标记，请使用`customHighlight`。如果未在`customHighlight`中指定设置，默认使用`defaultHighlight`。

还可以为子标记（如果使用）指定自定义高亮。

<sup>_注：`defaultHighlight`不适用于子标记。_</sup>

---

`defaultHighlight`和`customHighlight`都允许进行以下设置：

`foreground` —— 前景色。

`background` —— 背景色。

<sup>_注：前景色和背景色可使用[HTML/CSS colour names](https://en.wikipedia.org/wiki/Web_colors)（例如"Salmon"）、RGB 十六进制值（例如`#80FF00`）、RGB CSS 样式值（例如，`rgb(255,128,0)`或当前主题的颜色，例如。`peekViewResult.background`。查看[Theme Color](https://code.visualstudio.com/api/references/theme-color)，有关详细信息。十六进制和 RGB 值也可以指定 alpha，例如`#ff800080`或`rgba(255,128,0,0.5)`。_</sup>

---

`opacity` —— 与背景色一起使用的百分比值。100%将产生不透明的背景，这将让选择和其他装饰变得模糊起来。

<sup>_注：仅当使用十六进制或 RGB 颜色时，才能指定不透明度。_</sup>

---

`fontWeight`, `fontStyle`, `textDecoration` —— 可以使用标准 CSS 值设置高亮显示的样式。

`borderRadius` —— 用于设置高亮背景的边框半径。

`icon` —— 用于在树状视图中，设置不同的图标。必须是有效的八位图标（请参阅<https://octicons.github.com>)或 codicon（参见<https://microsoft.github.io/vscode-codicons/dist/codicon.html>)。如果使用 codicon 图标，请以"$(_icon_)"格式中指定它们。如果图标无效，则默认为勾号。"活动"视图展示的图标，也可以使用"todo-tree"或"todo-tree-filled"设置。

`iconColour` —— 用于设置树中，图标的颜色。如果未指定，它将尝试使用前景色或背景色。颜色可以根据前景色和背景色来指定，但请参见下面的注释。

<sup>_注意：只有在使用 codicon 图标时，才支持主题颜色。只有在使用八位图标或默认图标时，才支持十六进制、RGB 和 HTML 颜色。_</sup>

---

`gutterIcon` —— 设置为 true 可在编辑器栏中，显示图标。

<sup>_注意：不幸的是，只有八位图标和 todo 树图标可以显示。_</sup>

---

`rulerColour` —— 用于设置 overview ruler 中，标记的颜色。如果未指定，则默认使用前景色。颜色可根据前景色和背景色指定。

`rulerOpacity` —— 用于设置 ruler markers 的不透明度。

<sup>_注：仅适用于十六进制和 RGB 颜色设置。_</sup>

---

`rulerLane` —— 用于在 overview ruler 中，设置标记的车道。如果未指定，它将默认为右侧车道。使用`left`, `center`, `right`, or `full`选项之一。也可以使用 `none`禁用 ruler markers。

`type` —— 用于控制编辑器中高亮显示的内容。有效值为：

- `tag` —— 只是标记
- `text` —— 高亮显示 tag 和 tag 后的任何文本
- `tag-and-comment` —— 高亮显示注释字符（或匹配的开始）和 tag
- `tag-and-subTag` —— 如上所述，但允许子标记也高亮显示（颜色在自定义高亮显示中定义）
- `text-and-comment` —— 高亮显示注释字符（或匹配的开始）、tag 和 tag 后的文本
- `line` —— 高亮显示包含 tag 的整行
- `whole-line` —— 将包含 tag 的整行，高亮显示到编辑器的全宽
- `capture-groups:n,m...` —— 高亮显示正则表达式中的捕获组，其中`n`是正则表达式的索引
- `none` —— 在文档中禁用高亮显示

`hideFromTree` —— 用于从树中，移除 tag ，但仍在文件中，高亮显示

`hideFromStatusBar` —— 防止 tag 包含在状态栏计数中

例子：

```json
"todo-tree.highlights.defaultHighlight": {
    "icon": "alert",
    "type": "text",
    "foreground": "red",
    "background": "white",
    "opacity": 50,
    "iconColour": "blue"
},
"todo-tree.highlights.customHighlight": {
    "TODO": {
        "icon": "check",
        "type": "line"
    },
    "FIXME": {
        "foreground": "black",
        "iconColour": "yellow",
        "gutterIcon": true
    }
}
```

<sup>_注意：高亮显示配置与搜索设置是分开的。在`customHighlight`中添加设置，不会自动将 tag 添加到`todo-tree.general.tags`._</sup>

---

<sup>_注意：使用`capture-groups`开始`type`可能会对大文件的性能产生影响。_</sup>

---

## 安装

您可以通过 Visual Studio Marketplace 安装最新版本的扩展，[here](https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.todo-tree)。

或者，打开 Visual Studio Code，按`Ctrl+P`或`Cmd+P`和类型：

```bash
ext install Gruntfuggly.todo-tree
```

### 源代码

源代码可在 GitHub 上获得，[here](https://github.com/Gruntfuggly/todo-tree)。

## 头部操作

树状视图的头部操作栏，可以包含以下按钮：

![collapse](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/collapse.png) —— 折叠所有树节点</br>
![expand](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/expand.png) —— 展开所有树节点</br>
![flat](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/flat.png) —— 以平面列表的形式显示树视图，其中包含每个 TODO 的完整文件名</br>
![tags](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/tags.png) —— 将视图显示为标记列表</br>
![tree](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/tree.png) —— 将树视图显示为一棵树，每个文件夹都有可展开的节点（默认）</br>
![tag](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/tag.png) —— 按标记将树中的 todo 分组</br>
![notag](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/notag.png) —— 按文件组织 todo（默认）</br>
![filter](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/filter.png) —— 仅显示树中与输入的过滤文本匹配的项目</br>
![clear-filter](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/clear-filter.png) —— 卸下任何有过滤器</br>
![refresh](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/refresh.png) —— 重建这棵树</br>
![scan-open-files](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/scan-open-files.png) —— 仅显示打开文件中的标记</br>
![scan-current-file](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/scan-current-file.png) —— 显示当前文件中的标记</br>
![scan-workspace](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/scan-workspace-only.png) —— 仅显示工作区中的标记</br>
![scan-workspace](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/scan-workspace.png) —— 显示工作区和打开文件中的标记</br>
![reveal](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/reveal.png) —— 在树中显示当前文件</br>
![export](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/export.png) —— 将树内容导出到文件</br>

## 右键菜单

在树状视图中，单击鼠标右键将显示一个菜单，其中包含以下选项：

- **隐藏此文件夹/隐藏此文件** —— 从树中，移除文件夹或文件</br>
- **仅显示此文件夹** —— 从树中，移除所有其他文件夹和子文件夹</br>
- **仅显示此文件夹及其子文件夹** —— 从树中，移除其他文件夹，但保留子文件夹</br>
- **重置文件夹过滤器** —— 使用上述方法重置之前过滤的所有文件夹</br>
- **拨动徽章** —— 启用/禁用 SCM 装饰</br>
- **切换压缩文件夹** —— 启用/禁用压缩文件夹名称</br>
- **切换项目计数** —— 启用/禁用标记计数</br>
- **只扫描打开的文件** —— 显示 VSCode 中打开的文件中的 TODO（无搜索）</br>
- **仅扫描当前文件** —— 仅显示当前打开文件中的 TODO</br>
- **扫描工作区并打开文件** —— 显示工作区中的 todo 和所有打开的文件</br>
- **仅扫描工作区** —— 仅从工作区显示 TODO（需要手动引用或使用文件查看器）</br>
- **展开树/折叠树** —— 扩展或折叠整棵树</br>
- **显示树状视图/显示平面视图/仅显示标记视图** —— 更改树视图样式</br>
- **按标记分组/按标记取消分组** —— 按标记切换项目分组</br>
- **按子标记分组/按子标记取消分组** —— 按子标记切换项目分组</br>
- **导出树** —— 将树内容转储到文件中</br>
- **在树中显示当前文件** —— 在树中显示当前编辑器文件（如果存在）</br>

<sup>_注意：当前过滤器显示在调试日志中。此外，通过右键单击 **什么也没找到** 项目，那么过滤会重置。如果你的树变得不可见，因为所有的东西都被过滤，和`hideTreeWhenEmpty`设置为 true 时，可以按 **F1** 重置过滤器，或是选择 **Todo Tree：重置所有过滤器** 命令_</sup>

---

## 命令

### Tags

为便于配置标记，有两个可用命令：

- **Todo Tree：Add Tag** —— 输入新标记进行搜索

- **Todo Tree：Remove Tag** —— 显示可选择删除的当前标记列表

<sup>_注意：Remove Tag 命令可用于显示当前标记 —— 只需按 Escape 或 Enter 键，不选任何键，即可将其关闭。_</sup>

---

### 导出

可以使用**Todo Tree: Switch Scope**，导出树的内容。`todo-tree.general.exportPath`指定导出的路径，但文件仅是可读的，使用**File: Save As...** 保存文件。 _注：目前**File: Save As...**不起作用，这似乎是一个 VSCode 错误（请参阅<https://github.com/microsoft/vscode/issues/101952>)。_

### 切换范围

- **Todo Tree：Switch Scope** —— 显示可选择的已配置作用域的列表

## 配置

可按如下方式自定义扩展名（括号中的默认值）：

- **todo-tree.general.debug** (`false`)</br>在输出视图中，显示调试通道。

- **todo-tree.general.enableFileWatcher** (`false`)</br>设为 true，创建、更改或删除工作区中的文件时，将自动更新。

- **todo-tree.general.exportPath** (`~/todo-tree-%Y%m%d-%H%M.txt`)</br>导出树时，要使用的路径。环境变量将被填充，例如`${HOME}`路径通过 strftime（参见<https://github.com/samsonjs/strftime>）。设为`.json`能导出为 JSON 记录。

- **todo-tree.general.rootFolder** (`""`)</br>默认情况下，任何打开的工作空间都会在视图中有一棵树。使用此选项可以强制另一个文件夹成为树的根目录。可以包括环境变量，也可以使用`${workspaceFolder}`。例如</br>
  `"todo-tree.general.rootFolder": "${workspaceFolder}/test"`</br>或</br> `"todo-tree.general.rootFolder": "${HOME}/project"`。</br>

<sup>_注意：其他打开的文件（根文件夹之外）将显示（打开状态），其完整路径在括号中。_</sup>

---

- **todo-tree.general.schemes** (`['file','ssh','untitled']`)</br>查找 TODOs 的方案。例如，要在设置文件中查找 TODO，请添加`vscode-userdata`或者输出窗口，添加`output`。

- **todo-tree.general.tags** (`["TODO","FIXME","BUG"]`)</br>这定义了识别为 TODO 的标记。此列表将自动插入正则表达式。

> 译者： 比如说 rust 的 unsafe 关键字，就可以用这个添加。

- **todo-tree.general.tagGroups** (`{}`)</br>此设置允许将多个标记视为单个组。例子：

```json
    "todo-tree.general.tagGroups": {
        "FIXME": [
            "FIXME",
            "FIXIT",
            "FIX",
        ]
    },
```

将`FIXME`, `FIXIT`或`FIX`，像`FIXME`一样对待。当树按标记分组时，所有这些都将显示在`FIXME`节点。这也意味着，自定义高亮将应用于组，而不是每个标记类型。

<sup>_注意：组中的所有标记也应在`todo-tree.general.tags`存在。_</sup>

---

- **todo-tree.general.revealBehaviour** (`start of todo`)</br>更改‘双击’树中的 todo 时，光标的行为。您可以选择：

  - `start of todo`（将光标移动到 todo 的开头）
  - `end of todo`（将光标移动到 todo 的末尾）
  - `start of line`（将光标移动到行首）

- **todo-tree.general.statusBar** (`none`)</br>在状态栏中显示什么

  - 无(`none`)，
  - 总数(`total`)，
  - 每个标记的计数(`tags`)，
  - 算作前三个标记(`top three`)或
  - 仅对当前文件计数(`current file`）。

- **todo-tree.general.statusBarClickBehaviour** (`reveal`)</br>单击状态栏, 显示格式:

  - 圆循环(`cycle`)，
  - 露出那棵树(`reveal`)或者
  - 切换高亮(`toggle highlights`）。

- **todo-tree.filtering.includeGlobs** (`[]`)</br>包含型的 glob 模式，例如。

`[\"**/unit-tests/*.js\"]`只是为了展示。单元测试子文件夹中的 js 文件。[Globs help](https://code.visualstudio.com/api/references/vscode-api#GlobPattern）。

<sup>_注意：全局路径是绝对路径，而不是相对于当前工作区。_</sup>

---

- **todo-tree.filtering.excludeGlobs** (`["**/node_modules"]`)</br>排除型的 glob 模式（在**includeGlobs**之后使用)，例如。`[\"**/*.txt\"]`忽视一切的 txt 文件。

<sup>_注：默认情况下, `node_modules`不包括。_</sup>

---

- **todo-tree.filtering.includedWorkspaces** (`[]`)</br>树中的根工作区名称列表（可以使用通配符）。空数组包含所有工作区文件夹。

- **todo-tree.filtering.excludedWorkspaces** (`[]`)</br>排除的, 树中的根工作区名称列表（可以使用通配符）。

- **todo-tree.filtering.passGlobsToRipgrep** (`true`)</br>设为 false, 会在搜索*之后*应用这个 glob（遗留行为）。

- **todo-tree.filtering.useBuiltInExcludes** (`none`)</br>设为使用 VSCode 的内置文件或搜索排除。是其中之一:

  - `none`,
  - `file excludes`（使用文件：排除），
  - `search excludes`（使用搜索：排除）或
  - `file and search excludes`（两者都使用）。

- **todo-tree.filtering.ignoreGitSubmodules** (`false`)</br>设为 true，搜索时, 任何包含`.git`将被忽略。

- **todo-tree.filtering.includeHiddenFiles** (`false`)</br>设为 true，以（`.`）开头的文件将包括在内。

- **todo-tree.highlights.enabled** (`true`)</br>设为 false , 可关闭高亮显示。

- **todo-tree.highlights.highlightDelay** (`500`)</br>高亮显示前的延迟（毫秒）。

- **todo-tree.highlights.defaultHighlight** (`{}`)</br>设置默认高亮。例子：

```json
{
  "foreground": "white",
  "background": "red",
  "icon": "check",
  "type": "text"
}
```

- **todo-tree.highlights.customHighlight** (`{}`)</br>设置每个标记（或标记组）的高亮。例子：

```json
{
  "TODO": {
    "foreground": "white",
    "type": "text"
  },
  "FIXME": {
    "icon": "beaker"
  }
}
```

- **todo-tree.highlights.useColourScheme** (`false`)</br>简单的颜色方案

<sup>_注：颜色方案优先于_ `todo-tree.highlights.defaultHighlight` 中定义的颜色, _不优于_ `todo-tree.highlights.customHighlight`\_\_</sup>

---

- **todo-tree.highlights.backgroundColourScheme** (`["red","orange","yellow","green","blue","indigo","violet"]`)</br>与`todo-tree.highlights.useColourScheme`结合。颜色的定义方式与其他颜色相同（例如十六进制代码、主题名称等）。如果标记多于颜色，则重复。

- **todo-tree.highlights.foreroundColourScheme** (`["white","black","black","white","white","white","black"]`)</br>与`todo-tree.highlights.backgroundColourScheme`结合。应该与背景色有明显的对比度。

- **todo-tree.regex.enableMultiLine** (`false`)</br>通常，多行支持是通过检测`\n`在正则表达式中。设为`true`，启用多行支持。可以使用`[\s\S]`作为匹配任何字符（包括换行符）的替代方法。

- **todo-tree.regex.regex** (<tt>
  &#x28;&#x2f;&#x2f;&#x7c;&#x23;&#x7c;&#x3c;&#x21;&#x2d;&#x2d;&#x7c;&#x3b;&#x7c;&#x2f;&#x5c;&#x5c;\*&#x7c;&#x5e;&#x7c;&#x5e;&#x5b;&#x20;&#x5c;&#x5c;&#x74;&#x5d;\*&#x28;&#x2d;&#x7c;&#x5c;&#x5c;&#x64;&#x2b;&#x2e;&#x29;&#x29;&#x5c;&#x5c;&#x73;\*&#x28;&#x24;&#x54;&#x41;&#x47;&#x53;&#x29;</tt>)</br>

这定义了用于定位 TODO 的正则表达式。默认情况下，它会在以<tt>&#47;&#47;</tt>, <tt>#</tt>, <tt>;</tt>, <tt>&lt;!--</tt> 或 <tt>&#47;\*</tt> 开头的注释中, 搜索标记, 同时定位 todo 列表。这应该涵盖大多数语言。但是，如果您想对其进行优化，请确保<tt>($TAGS)</tt> 占位符, 因为 <tt>($TAGS)</tt>将替换为展开的标记列表。记住, 你应该保留原本基础的正则表达式.

<sup>_注：这是一个[Rust regex 箱子的表达式语法](https://docs.rs/regex/1.0.0/regex)</a>，而不是 javascript。_</sup>

---

- **todo-tree.regex.subTagRegex** 这是一个正则表达式，用于处理标记右侧的文本，例如

  - 提取子标记, 或删除不需要的字符。
  - 正则表达式匹配的任何内容都将从文本中删除。
  - 如果包含捕获组，则将内容提取到子标记中，该子标记将在树中, 对类似标记进行分组。
  - 子标记也可以用作`todo-tree.tree.subTagClickUrl`和`todo-tree.tree.labelFormat`的占位符.
  - 子标记也可以通过在`todo-tree.highlights.customHighlights`中指定节来高亮显示。背景要高亮显示子标记本身，请在标记的自定义高亮显示中, 将"type"设置为"tag and subTag"。

例子：

- `"^:\s*"`可以用来删除标记后面的冒号。

- `"^\s*\((.*)\)"`提取标记后括号中的任何内容，并将其用作子标记。

- **todo-tree.regex.regexCaseSensitive** (`true`)</br>设置为 false，不考虑大小写。

- **todo-tree.ripgrep.ripgrep** (`""`)</br>通常情况下，扩展将在需要时定位 ripgrep 本身。如果您想使用 ripgrep 的替代版本，请将其设置为指向安装它的位置。

- **todo-tree.ripgrep.ripgrepArgs** (`"--max-columns=1000"`)</br>使用此选项将其他参数传递给 ripgrep。例如，`"-i"`使搜索不区分大小写。_小心使用！_

- **todo-tree.ripgrep.ripgrepMaxBuffer** (`200`)</br>默认情况下，ripgrep 进程的缓冲区为 200KB。然而，对于所有你可能想看到的标记来说，有时是不够的。可相应地增加缓冲区大小。

- **todo-tree.ripgrep.usePatternFile** (`true`)</br>默认情况下，模式文件与 ripgrep 一起使用。如果您在删除模式文件时遇到问题，请将其设置为 false，以使用向 ripgrep 提供正则表达式的传统方法。

- **todo-tree.tree.hideTreeWhenEmpty** (`true`)</br>通常，如果未找到任何内容，则会从资源管理器视图中删除该树。将其设置为 false 以保持视图的存在。

- **todo-tree.tree.filterCaseSensitive** (`false`)</br>如果需要过滤区分大小写，请使用此选项。

<sup>_注意：这不适用于搜索_.</sup>

---

- **todo-tree.tree.trackFile** (`true`)</br>不跟踪树视图中打开的文件，请将其设置为 false。

- **todo-tree.tree.showBadges** (`true`)</br>设置为 false 可禁用树中的 SCM 状态和徽章\*

<sup>_注意：不幸的是，这也会关闭主题图标。_</sup>

---

- **todo-tree.tree.expanded<sup>\*</sup>** (`false`)</br>展开新视图，请设置为 true。

- **todo-tree.tree.flat<sup>\*</sup>** (`false`)</br>平面视图，请设置为 true。

- **todo-tree.tree.grouped<sup>\*</sup>** (`false`)</br>视图分组，请设置为 true。

- **todo-tree.tree.tagsOnly<sup>\*</sup>** (`false`)</br>仅使用标记的新视图，请设置为 true。

- **todo-tree.tree.sortTagsOnlyViewAlphabetically** (`false`)</br>在"仅标记"视图中，按字母顺序排序项目，而不是按标记列表的顺序排序。

- **todo-tree.tree.showCountsInTree** (`false`)</br>设置为 true 可显示树中的 todo 计数。

- **todo-tree.tree.labelFormat** (`${tag} ${after}`)</br>todo 标记的格式。可用的占位符包括

  - `${line}`,
  - `${column}`,
  - `${tag}`,
  - `${before}`（标记前的文字），
  - `${after}`（标记后面的文本），
  - `${filename}`,
  - `${filepath}`和
  - `${afterOrBefore}`

如果 after 为空，则使用"after"文本或"before"文本。使用`${tag}`或`${subTag}`时，您还可以使用"大写"、"小写"或"大写"（"uppercase", "lowercase" or "capitalize"）来转换文本，例如：`${tag:lowercase}`。

- **todo-tree.tree.scanMode** (`workspace`)</br>默认情况下，扩展扫描整个工作区(`workspace`)。使用此选项可将搜索限制为

  - 仅打开文件(`open files`)或者
  - 只显示当前文件(`current file`）。

- **todo-tree.tree.showScanModeButton** (`false`)</br>在树状视图标题上，显示一个按钮以切换扫描模式（见上文）。

- **todo-tree.tree.hideIconsWhenGroupedByTag** (`false`)</br>按标记分组时隐藏项目图标。

- **todo-tree.tree.sort** (`true`)</br>ripgrep 搜索使用多个线程来提高性能。树在填充时进行排序，以便保持稳定。如果要使用 ripgrep 自己的排序参数，请将其设置为 false。

<sup>_注意：根据您选择的扫描模式，您可能还希望在不排序时，禁用自动刷新，否则树可能仍然不稳定。_</sup>

---

- **todo-tree.tree.disableCompactFolders** (`false`)</br>树通常会遵循 VSCode 的`explorer.compactFolders`设置。如果要禁用 todo 树中的折叠文件夹，请将其设置为 true。

- **todo-tree.tree.tooltipFormat** (`${filepath}, ${line}`)</br>树上的工具提示的格式。使用与`todo-tree.tree.labelFormat`相同的占位符（见上文）。

- **todo-tree.tree.subTagClickUrl**</br>一个 URL（可以包含占位符），当点击树中的子标记时，它将被打开，例如。`https://github.com/${subTag}`，如果子标记提取用户名，则可以使用。

- **todo-tree.tree.buttons.reveal** (`true`)</br>在树状视图标题栏的按钮，显示当前项目（仅当未启用"track file"时）。

- **todo-tree.tree.buttons.scanMode** (`false`)</br>在树状视图标题栏的按钮，更改扫描模式设置。

- **todo-tree.tree.buttons.viewStyle** (`true`)</br>在树状视图标题栏的按钮，更改视图样式（仅限，tree, flat or tags）。

- **todo-tree.tree.buttons.groupByTag** (`true`)</br>在树状视图标题栏的一个按钮，按标记分组。

- **todo-tree.tree.buttons.groupBySubTag** (`false`)</br>在树状视图标题栏的一个按钮，按子标记分组。

<sup>_注意：只有在树中，找到子标记并存在子标记时，此按钮才可见。_</sup>

---

- **todo-tree.tree.buttons.filter** (`true`)</br>在树状视图标题栏的一个按钮，允许通过输入一些文本来过滤树。

- **todo-tree.tree.buttons.refresh** (`true`)</br>在树状视图标题栏的刷新按钮。

- **todo-tree.tree.buttons.expand** (`true`)</br>在树状视图标题栏的按钮，展开或折叠整个树。

- **todo-tree.tree.buttons.export** (`false`)</br>在树状视图标题栏的按钮，以创建显示树内容的文本文件。

<sup>**仅适用于新工作区。在工作区中更改视图后，将存储当前状态**</sup>

---

- **todo-tree.scopes** (`{}`)</br>定义一组文件作用域，可以通过*todo-tree.switchScope*命令，来使用。

这是一个复杂的配置属性，只能通过配置 JSON 文件进行配置。例如

```json
"todo-tree.scopes": [
    {
        "name": "Production ",
        "excludeGlobs": [
             "**/tests/**"
        ]
    },
    {
        "name": "Tests",
        "includeGlobs": [
            "**/tests/**"
        ]
    },
    {
        "name": "All"
    }
]
```

### 多行 TODOs

如果正则表达式包含`\n`，则多行 TODOs 会被启用。在这种模式下，搜索结果的处理方式略有不同。如果发现结果不包含来自`todo-tree.general.tags`的任何标记，假设它们属于之前的结果，该结果确实有标记。例如，如果将正则表达式设置为：

```json
"todo-tree.regex.regex": "(//)\\s*($TAGS）。*(\\n\\s*//\\s{2,}.*)*"
```

这将匹配多行 TODO，其中额外的行，在注释字符和 TODO 项之间至少有两个空格。例如

```json
// TODO multiline example
//  second line
//  third line
```

如果你想在 C++风格的多行注释块中，匹配多行 TODOs，你需要一些类似的东西：

```json
"todo-tree.regex.regex": "(/\\*)\\s*($TAGS）。*(\\n\\s*(//|/\\*|\\*\\*)\\s{2,}.*)*"
```

应该匹配：

```json
/* TODO multiline example
**  second line
**  third line
*/
```

<sup>_注意：如果使用设置 GUI，则无需转义每个反斜杠。_</sup>

---

- **警告：多行 TODOs 不能与 markdown TODOs 一起使用，可能会产生其他意外结果。性能也可能会降低。**

### 排除文件和目录

要限制搜索的文件目录，可以定义`todo-tree.filtering.includeGlobs`。这是一个全局数组，搜索结果与之匹配。如果结果与任何一个 globs 匹配，则将显示它们。默认情况下，数组为空，与所有内容匹配。[here](https://code.visualstudio.com/api/references/vscode-api#GlobPattern)有更多信息。

<sup>_注意：globs 路径是绝对路径，而不是相对于当前工作区。_</sup>

---

要从搜索中，排除文件夹/文件，可以定义`todo-tree.filtering.excludeGlobs`。如果搜索结果与这些 globs 匹配，则将忽略这些结果。

还可以在树视图中，使用右键菜单，移除和排除文件夹。此文件夹过滤器是单独应用的。

<sup>_注意：默认情况下，ripgrep 会忽略您`.gitignore`或`.ignore`定义的文件和文件夹。如果要包含这些文件，请设置_ `todo-tree.ripgrep.ripgrepArgs` _为_ ` —— -no-ignore`。</sup>

---

### Markdown 支持

在第一次编写扩展时，仅仅是在默认正则表达式中，添加一个模式，给了个非常基本的 markdown 支持` —— [ ]`"。处理 markdown TODOs 的更好方法是将"`(-|\d+.)`"，添加到正则表达式第一部分的"注释"列表中，再将"`[ ]`"和"`[x]`"，添加到"`settings.json`的标记列表，例如：

```json
"todo-tree.regex.regex": "(//|#|<!--|;|/\\*|^|^\\s*(-|\\d+.))\\s*($TAGS)"
"todo-tree.general.tags": [
        "BUG",
        "HACK",
        "FIXME",
        "TODO",
        "XXX",
        "[ ]",
        "[x]"
    ]
```

<sup>*注意：如果通过 GUI 修改设置，请在在正则表达式设置中，将`\\`*替换为\_`\`。</sup>

---

这将匹配以下所有条件：

```markdown
- [ ] Do something
- [x] Something I've done

1. [ ] Do this first
2. [ ] Followed by this
```

这还允许应用自定义高亮显示，例如。

```json
"todo-tree.highlights.customHighlight": {
    "[ ]": {
        "background": "#ff000080"
    },
    "[x]": {
        "background": "#00ff0080"
    }
}
```

它将把 **代办** 染成红色，将 **完成** 染成绿色。

最后，方便按标记（和子标记）进行分组，且在状态栏中，显示计数时效果更好。

<sup>_注意：默认正则表达式将在将来某个时候更新哦。_<sup>

## Known Issues

仅当您的配置使用`todo-tree.general.tags`时，按标记分组才会工作。todo-tree 扩展的旧版本会直接在`todo-tree.regex.regex`定义标记，而现在，regex 将 **$TAGS**内容 ，通过`todo-tree.general.tags`替换。

按标记分组不适用于 markdown 任务列表项，因为没有可用于分组的标记。该树将显示标记组旁边的文件。

按标记分组时，在树状图中跟踪的文件，将显示找到的第一个标记。

当没有当前工作区时，默认图标将显示在树中。

## Donate

如果你觉得这个扩展很有用，请随时捐款，[here](https://paypal.me/Gruntfuggly)谢谢

### Credits

使用的是[ripgrep-js](https://www.npmjs.com/package/ripgrep-js）。

主要图标最初由[Freepik](http://www.freepik.com)制造。来自[www.flaticon.com](https://www.flaticon.com/)，协议是[CC 3.0 BY](http://creativecommons.org/licenses/by/3.0/)

Tree view 图标由[Vaadin](https://www.flaticon.com/authors/vaadin)制造。来自[www.flaticon.com](https://www.flaticon.com/)，协议是[CC 3.0 BY](http://creativecommons.org/licenses/by/3.0/)

Tag 图标由[Dave Gandy](https://www.flaticon.com/authors/dave-gandy)制造。来自[www.flaticon.com](https://www.flaticon.com/)，协议是[CC 3.0 BY](http://creativecommons.org/licenses/by/3.0/)

Tags 图标由[Vectors Market](https://www.flaticon.com/authors/vectors-market)制造。来自[www.flaticon.com](https://www.flaticon.com/)，协议是[CC 3.0 BY](http://creativecommons.org/licenses/by/3.0/)

Reveal 图标由[Gregor Cresnar](https://www.flaticon.com/authors/gregor-cresnar)制造。来自[www.flaticon.com](https://www.flaticon.com/)

很多图标现在都被更新了[johnletey](https://github.com/johnletey)以匹配新的 VS 代码 1.37.0 GUI。非常感谢！

#### Translations

vscode 命令 的简体中文翻译[loniceras](https://github.com/loniceras)。
reamde.md 的简体中文翻译[chinanf-boy](https://github.com/chinanf-boy)。
