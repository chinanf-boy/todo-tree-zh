# Todo Tree 校对 🀄

<div style="font-size: 100px;text-align: center,width: 100%;">
    Vs Code 扩展
</div>
<!-- doc-templite START generated -->
<!-- repo = 'Gruntfuggly/todo-tree' -->
<!-- commit = '8eab71fc96b2467b4ba8a1424b30d0ca28eb05a7' -->
<!-- time = '2022-1-13' -->

| 翻译的原文 | 与日期      | 最新更新 | 更多                       |
| ---------- | ----------- | -------- | -------------------------- |
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

## Highlighting

> *信息！：*如果您只想为标签（tags）设置不同的颜色，现在可以启用`todo-tree.highlights.useColourScheme`。这将应用一组颜色（可以更改），按照标签定义的顺序设置。

高亮显示标签是可配置的。使用`defaultHighlight`为所有标记设置高亮。如果需要以不同的方式配置各个标记，请使用`customHighlight`。如果未在中指定设置`customHighlight`，从`defaultHighlight`被使用了。

还可以为子标记（如果使用）指定自定义高亮。

<sup>_注：`defaultHighlight`不适用于子标记。_</sup>

二者都`defaultHighlight`和`customHighlight`允许进行以下设置：

`foreground`-用于在编辑器中设置高亮的前景色，在标尺中设置标记。

`background`-用于在编辑器中设置高亮的背景色。

<sup>_注：前景色和背景色可使用[HTML/CSS colour names](https://en.wikipedia.org/wiki/Web_colors)（例如“鲑鱼”）、RGB 十六进制值（例如“#80FF00”）、RGB CSS 样式值（例如“RGB（255128,0）”或当前主题的颜色，例如。`peekViewResult.background`看见[Theme Color](https://code.visualstudio.com/api/references/theme-color)详细信息。十六进制和 RGB 值也可以指定 alpha，例如“#ff800080”或“rgba（255128,0,0.5）”。_</sup>

`opacity`-与背景色一起使用的百分比值。100%将产生不透明的背景，这将模糊选择和其他装饰。

<sup>_注：仅当使用十六进制或 RGB 颜色时，才能指定不透明度。_</sup>

`fontWeight`, `fontStyle`, `textDecoration`-可以使用标准 CSS 值设置高亮显示的样式。

`borderRadius`-用于设置高亮背景的边框半径。

`icon`-用于在树状视图中设置不同的图标。必须是有效的八位图标（请参阅<https://octicons.github.com>)或 codicon（参见<https://microsoft.github.io/vscode-codicons/dist/codicon.html>).如果使用密码图标，请在格式中指定它们“$(_偶像_)“。如果图标无效，则默认为勾号。如果要从“活动”视图中使用图标，也可以使用“todo树”或“todo树已填充”。

`iconColour`-用于设置树中图标的颜色。如果未指定，它将尝试使用前景色或背景色。颜色可以根据前景色和背景色来指定，但请参见下面的注释。

<sup>_注意：只有在使用密码图标时才支持主题颜色。只有在使用八位图标或默认图标时，才支持十六进制、RGB 和 HTML 颜色。_</sup>

`gutterIcon`-设置为 true 可在编辑器栏中显示图标。

<sup>_注意：不幸的是，只有八位图标和todo树图标可以显示在排水沟中。_</sup>

`rulerColour`-用于设置概览标尺中标记的颜色。如果未指定，则默认使用前景色。颜色可根据前景色和背景色指定。

`rulerOpacity`-用于设置标尺标记的不透明度。

<sup>_注：仅适用于十六进制和 RGB 颜色设置。_</sup>

`rulerLane`-用于在概览标尺中设置标记的车道。如果未指定，它将默认为右侧车道。使用“左”、“中”、“右”或“全”选项之一。也可以使用“无”禁用标尺标记。

`type`-用于控制编辑器中高亮显示的内容。有效值为：

- `tag`-只是标签
- `text`-高亮显示标记和标记后的任何文本
- `tag-and-comment`-高亮显示注释字符（或匹配的开始）和标记
- `tag-and-subTag`-如上所述，但允许子标签也高亮显示（颜色在自定义高亮显示中定义）
- `text-and-comment`-高亮显示注释字符（或匹配的开始）、标记和标记后的文本
- `line`-高亮显示包含标记的整行
- `whole-line`-将包含标记的整行高亮显示到编辑器的全宽
- `capture-groups:n,m...`-高亮显示正则表达式中的捕获组，其中“n”是正则表达式的索引
- `none`-在文档中禁用高亮显示

`hideFromTree`-用于从树中隐藏标记，但仍在文件中高亮显示

`hideFromStatusBar`-防止标记包含在状态栏计数中

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

<sup>_注意：高亮显示配置与搜索设置是分开的。在中添加设置`customHighlight`不会自动将标记添加到`todo-tree.general.tags`._</sup>

<sup>\*注意：使用`capture-groups`开始`type`可能会对大文件的性能产生影响。

## Installing

您可以通过 Visual Studio Marketplace 安装最新版本的扩展[here](https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.todo-tree).

或者，打开 Visual Studio 代码，按`Ctrl+P`或`Cmd+P`和类型：

> ext 安装非常糟糕。todo树

### Source Code

源代码可在 GitHub 上获得[here](https://github.com/Gruntfuggly/todo-tree).

## Controls

树状视图标题可以包含以下按钮：

![collapse](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/collapse.png)-折叠所有树节点</br>
![expand](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/expand.png)-展开所有树节点</br>
![flat](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/flat.png)-以平面列表的形式显示树视图，其中包含每个 TODO 的完整文件名</br>
![tags](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/tags.png)-将视图显示为标记列表</br>
![tree](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/tree.png)-将树视图显示为一棵树，每个文件夹都有可展开的节点（默认）</br>
![tag](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/tag.png)-按标签将树中的todo分组</br>
![notag](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/notag.png)-按文件组织todo（默认）</br>
![filter](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/filter.png)-仅显示树中与输入的筛选文本匹配的项目</br>
![clear-filter](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/clear-filter.png)-卸下任何有源滤波器</br>
![refresh](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/refresh.png)-重建这棵树</br>
![scan-open-files](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/scan-open-files.png)-仅显示打开文件中的标记</br>
![scan-current-file](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/scan-current-file.png)-显示当前文件中的标记</br>
![scan-workspace](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/scan-workspace-only.png)-仅显示工作区中的标记</br>
![scan-workspace](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/scan-workspace.png)-显示工作区和打开文件中的标记</br>
![reveal](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/reveal.png)-在树中显示当前文件</br>
![export](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/button-icons/export.png)-将树内容导出到文件</br>

## Folder Filter Context Menu

在树状视图中单击鼠标右键将显示一个上下文菜单，其中包含以下选项：

**隐藏此文件夹/隐藏此文件**-从树中删除文件夹或文件</br>
**仅显示此文件夹**-从树中删除所有其他文件夹和子文件夹</br>
**仅显示此文件夹及其子文件夹**-从树中删除其他文件夹，但保留子文件夹</br>
**重置文件夹过滤器**-使用上述方法重置之前筛选的所有文件夹</br>
**拨动徽章**-启用/禁用 SCM 装饰</br>
**切换压缩文件夹**-启用/禁用压缩文件夹名称</br>
**切换项目计数**-启用/禁用标签计数</br>
**只扫描打开的文件**-显示 VSCode 中打开的文件中的 TODO（无搜索）</br>
**仅扫描当前文件**-仅显示当前打开文件中的 TODO</br>
**扫描工作区并打开文件**-显示工作区中的todo和所有打开的文件</br>
**仅扫描工作区**-仅从工作区显示 TODO（需要手动引用或使用文件查看器）</br>
**展开树/折叠树**-扩展或折叠整棵树**显示树状视图/显示平面视图/仅显示标记视图**-更改树视图样式**按标记分组/按标记取消分组**-按标记切换项目分组**按子标记分组/按子标记取消分组**-按子标记切换项目分组**导出树**-将树内容转储到文件中**在树中显示当前文件**-在树中显示当前编辑器文件（如果存在）

<sup>_注意：当前过滤器显示在调试日志中。此外，通过右键单击**什么也没找到**树上的项目。如果你的树变得不可见，因为所有的东西都被过滤和`hideTreeWhenEmpty`设置为 true 时，可以按重置过滤器**一层楼**以及选择**todo树：重置文件夹筛选器**命令_</sup>

## Commands

### Tags

为便于配置标记，有两个可用命令：

**todo树：添加标记**-允许输入新标签进行搜索

**todo树：删除标记**-显示可选择删除的当前标记列表

<sup>_注意：Remove Tag 命令可用于显示当前标记-只需按 Escape 或 Enter 键，不选择任何键即可将其关闭。_</sup>

### Export

可以使用导出树的内容**todo树：导出树**。将使用指定的路径创建只读文件`todo-tree.general.exportPath`。可以使用**文件：另存为。。。**. _注：目前**文件：保存**不起作用，这似乎是一个 VSCode 错误（请参阅<https://github.com/microsoft/vscode/issues/101952>)._

### Switch Scope

**todo树：切换范围**-显示可选择的已配置作用域的列表

## Configuration

可按如下方式自定义扩展名（括号中的默认值）：

**todo树。全体的调试** (`false`)</br>在输出视图中显示调试通道。

**todo树。全体的 enableFileWatcher** (`false`)</br>将此设置为 true，以在创建、更改或删除工作区中的文件时启用自动更新。

**todo树。全体的导出路径** (`~/todo-tree-%Y%m%d-%H%M.txt`)</br>导出树时要使用的路径。环境变量将被扩展，例如`${HOME}`路径通过 strftime（参见<https://github.com/samsonjs/strftime>).将分机设置为`.json`导出为 JSON 记录。

**todo树。全体的根文件夹** (`""`)</br>默认情况下，任何打开的工作空间都会在视图中有一棵树。使用此选项可以强制另一个文件夹成为树的根目录。可以包括环境变量，也可以使用${workspaceFolder}。例如</br>
`"todo-tree.general.rootFolder": "${workspaceFolder}/test"`</br>或</br> `"todo-tree.general.rootFolder": "${HOME}/project"`.</br>

<sup>_注意：其他打开的文件（根文件夹之外）将显示（打开时），其完整路径在括号中。_</sup>

**todo树。全体的计划** (`['file','ssh','untitled']`)</br>编辑器计划在中查找todo。例如，要在设置文件中查找 TODO，请添加`vscode-userdata`或者对于输出窗口，添加`output`.

**todo树。全体的标签** (`["TODO","FIXME","BUG"]`)</br>这定义了识别为 TODO 的标签。此列表将自动插入正则表达式。

**todo树。全体的标记群** (`{}`)</br>此设置允许将多个标记视为单个组。例子：

```json
    "todo-tree.general.tagGroups": {
        "FIXME": [
            "FIXME",
            "FIXIT",
            "FIX",
        ]
    },
```

这对任何人都有好处`FIXME`, `FIXIT`或`FIX`像`FIXME`。当树按标记分组时，所有这些都将显示在`FIXME`节点。这也意味着自定义高亮将应用于组，而不是每个标记类型。

<sup>_注意：组中的所有标记也应显示在`todo-tree.general.tags`._</sup>

**todo树。全体的报复行为** (`start of todo`)</br>更改双击树中的todo时光标的行为。您可以选择：`start of todo`（将光标移动到 todo 的开头），`end of todo`（将光标移动到 todo 的末尾）或`start of line`（将光标移动到行首）。

**todo树。全体的状态栏** (`none`)</br>在状态栏中显示什么-无(`none`)，总数(`total`)，每个标签的计数(`tags`)，算作前三个标签(`top three`)或仅对当前文件计数(`current file`).

**todo树。全体的状态栏点击行为** (`reveal`)</br>将单击状态栏的行为设置为在状态栏显示格式之间循环(`cycle`)，露出那棵树(`reveal`)或者切换高亮(`toggle highlights`).

**todo树。过滤。includeGlobs** (`[]`)</br>用于通过包含限制搜索结果的 glob，例如。`[\"**/unit-tests/*.js\"]`只是为了展示。单元测试子文件夹中的 js 文件。[Globs help](https://code.visualstudio.com/api/references/vscode-api#GlobPattern).

<sup>_注意：全局路径是绝对路径，而不是相对于当前工作区。_</sup>

**todo树。过滤。排除球** (`["**/node_modules"]`)</br>用于通过排除限制搜索结果的 Globs（在**includeGlobs**)，例如。`[\"**/*.txt\"]`忽视一切。txt 文件。

<sup>_注：`node_modules`默认情况下不包括。_</sup>

**todo树。过滤。包含的工作区** (`[]`)</br>要作为根包含在树中的工作区名称列表（可以使用通配符）。空数组包含所有工作区文件夹。

**todo树。过滤。排除工作空间** (`[]`)</br>要在树中作为根排除的工作区名称列表（可以使用通配符）。

**todo树。过滤。passGlobsToRipgrep** (`true`)</br>将此设置为 false 以应用全局*之后*搜索（遗留行为）。

**todo树。过滤。UseBuiltinex 包括** (`none`)</br>将此设置为使用 VSCode 的内置文件或搜索排除。可能是其中之一`none`, `file excludes`（使用文件：排除），`search excludes`（使用搜索：排除）或`file and search excludes`（两者都使用）。

**todo树。过滤。ignoreGitSubmodules** (`false`)</br>如果为 true，则任何包含`.git`搜索时将忽略文件。

**todo树。过滤。includeHidden 文件** (`false`)</br>如果为 true，则以句点（.）开头的文件将包括在内。

**todo树。亮点。启用** (`true`)</br>将此设置为 false 可关闭高亮显示。

**todo树。亮点。强光延迟** (`500`)</br>高亮显示前的延迟（毫秒）。

**todo树。亮点。默认高亮显示** (`{}`)</br>设置默认高亮。例子：

```json
{
  "foreground": "white",
  "background": "red",
  "icon": "check",
  "type": "text"
}
```

**todo树。亮点。定制亮点** (`{}`)</br>设置每个标记（或标记组）的高亮。例子：

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

**todo树。亮点。使用颜色方案** (`false`)</br>使用简单的方案为高亮着色。这将简单地按照标签定义的相同顺序应用颜色列表。使用此选项可以更简单地为每个标记设置自定义高亮。

<sup>_注：颜色方案优先于中定义的颜色_ `todo-tree.highlights.defaultHighlight` _但不是_ `todo-tree.highlights.customHighlight`_._</sup>

**todo树。亮点。背景配色方案** (`["red","orange","yellow","green","blue","indigo","violet"]`)</br>定义与应用程序结合使用的颜色`todo-tree.highlights.useColourScheme`给亮点上色。颜色的定义方式与其他颜色相同（例如十六进制代码、主题名称等）。如果标签多于颜色，则重复序列。

**todo树。亮点。前景方案** (`["white","black","black","white","white","white","black"]`)</br>定义与应用程序结合使用的颜色`todo-tree.highlights.backgroundColourScheme`给亮点上色。这些颜色应与背景色互补。

**todo树。正则表达式。启用多行** (`false`)</br>通常，多行支持是通过检测`\n`在正则表达式中。将此设置为`true`，默认情况下启用多行支持。这允许使用`[\s\S]`作为匹配任何字符（包括换行符）的替代方法。

**todo树。正则表达式。正则表达式** (<tt>
(//\|#\|\<!--\|;\|/\\\\\*\|^\|^\[ \\\\t]\*(-\|\\\\d+.))\\\\s\*($TA.GS)</tt>)</br>

这定义了用于定位 TODO 的正则表达式。默认情况下，它会在以开头的注释中搜索标记<tt>//</tt>, <tt>#</tt>, <tt>;</tt>, <tt>\<!--</tt>或<tt>/\*</tt>，并降低todo列表。这应该涵盖大多数语言。但是，如果您想对其进行优化，请确保<tt>（$TAGS）</tt>保存为<tt>（$TAGS）</tt>将替换为扩展的标记列表。为了让一些扩展功能发挥作用，<tt>（$TAGS）</tt>但是，如果需要显式扩展标记列表，则基本功能仍应有效。

<sup>_注：这是一个[Rust regular expression](https://docs.rs/regex/1.0.0/regex)</a>，而不是 javascript。_</sup>

**todo树。正则表达式。亚农业**这是一个正则表达式，用于处理标记右侧的文本，例如提取子标记或删除不需要的字符。正则表达式匹配的任何内容都将从文本中删除。如果包含捕获组，则将内容提取到子标记中，该子标记将在树中用于对类似标记进行分组。子标记也可以用作中的占位符`todo-tree.tree.subTagClickUrl`和`todo-tree.tree.labelFormat`.子标记也可以通过在中指定节来高亮显示`todo-tree.highlights.customHighlights`背景要高亮显示子标记本身，请在标记的自定义高亮显示中将“type”设置为“tag and subTag”。

例如：

`"^:\s*"`可以用来删除标签后面的冒号。

`"^\s*\((.*)\)"`可用于提取标记后括号中的任何内容，并将其用作子标记。

**todo树。正则表达式。正则表达式敏感** (`true`)</br>设置为 false 以允许标记匹配，而不考虑大小写。

**todo树。激流。激流** (`""`)</br>通常情况下，扩展将在需要时定位 ripgrep 本身。如果您想使用 ripgrep 的替代版本，请将其设置为指向安装它的位置。

**todo树。激流。里格雷帕格斯** (`"--max-columns=1000"`)</br>使用此选项将其他参数传递给 ripgrep。例如`"-i"`使搜索不区分大小写。_小心使用！_

**todo树。激流。里普格雷普马斯布弗** (`200`)</br>默认情况下，ripgrep 进程的缓冲区为 200KB。然而，对于所有你可能想看到的标签来说，这有时是不够的。此设置可用于相应地增加缓冲区大小。

**todo树。激流。使用模式文件** (`true`)</br>默认情况下，模式文件与 ripgrep 一起使用。如果您在删除模式文件时遇到问题，请将其设置为 false，以使用向 ripgrep 提供正则表达式的传统方法。

**todo树。树隐秘的** (`true`)</br>通常，如果未找到任何内容，则会从资源管理器视图中删除该树。将其设置为 false 以保持视图的存在。

**todo树。树滤镜敏感** (`false`)</br>如果需要筛选区分大小写，请使用此选项。

<sup>_注意：这不适用于搜索_.</sup>

**todo树。树轨迹文件** (`true`)</br>如果要防止跟踪树视图中打开的文件，请将其设置为 false。

**todo树。树展示徽章** (`true`)</br>设置为 false 可禁用树中的 SCM 状态和徽章\*

<sup>_注意：不幸的是，这也会关闭主题图标。_</sup>

**todo树。树扩大<sup>\*</sup>** (`false`)</br>如果希望默认情况下展开新视图，请设置为 true。

**todo树。树平的<sup>\*</sup>** (`false`)</br>如果希望新视图在默认情况下为平面视图，请设置为 true。

**todo树。树分组<sup>\*</sup>** (`false`)</br>如果希望在默认情况下对新视图进行分组，请设置为 true。

**todo树。树塔格森利<sup>\*</sup>** (`false`)</br>如果希望默认情况下仅使用标记的新视图，请设置为 true。

**todo树。树 sortTagsOnlyViewAlphabetically** (`false`)</br>在“仅标记”视图中，按字母顺序排序项目，而不是按标记列表的顺序排序。

**todo树。树 showCountsInTree** (`false`)</br>设置为 true 可显示树中的todo计数。

**todo树。树标签格式** (`${tag} ${after}`)</br>todo标签的格式。可用的占位符包括`${line}`, `${column}`, `${tag}`, `${before}`（标签前的文字），`${after}`（标签后面的文本），`${filename}`, `${filepath}`和`${afterOrBefore}`（如果 after 为空，则使用“after”文本或“before”文本）。使用时`${tag}`或`${subTag}`您还可以使用“大写”、“小写”或“大写”来转换文本，例如：。`${tag:lowercase}`.

**todo树。树扫描模式** (`workspace`)</br>默认情况下，扩展扫描整个工作区(`workspace`)。使用此选项可将搜索限制为仅打开文件(`open files`)或者只显示当前文件(`current file`).

**todo树。树 ShowScanMode 按钮** (`false`)</br>在树状视图标题上显示一个按钮以切换扫描模式（见上文）。

**todo树。树 hideIconsWhenGroupedByTag** (`false`)</br>按标签分组时隐藏项目图标。

**todo树。树分类** (`true`)</br>ripgrep 搜索使用多个线程来提高性能。树在填充时进行排序，以便保持稳定。如果要使用 ripgrep 自己的排序参数，请将其设置为 false。

<sup>_注意：根据您选择的扫描模式，您可能还希望在禁用排序时禁用自动刷新，否则树可能仍然不稳定。_</sup>

**todo树。树禁用压缩文件夹** (`false`)</br>树通常会尊重 VSCode 的`explorer.compactFolders`背景如果要禁用todo树中的压缩文件夹，请将其设置为 true。

**todo树。树工具提示格式** (`${filepath}, ${line}`)</br>树项工具提示的格式。使用与相同的占位符`todo-tree.tree.labelFormat`（见上文）。

**todo树。树子地址**</br>一个 URL（可以包含占位符），当点击树中的子标签时，它将被打开，例如。`https://github.com/${subTag}`如果子标记提取用户名，则可以使用。

**todo树。树按钮。揭示** (`true`)</br>在树状视图标题栏中显示按钮以显示当前项目（仅当未启用“轨迹文件”时）。

**todo树。树按钮。扫描模式** (`false`)</br>在树状视图标题栏中显示按钮以更改扫描模式设置。

**todo树。树按钮。视图样式** (`true`)</br>在树状视图标题栏中显示按钮以更改视图样式（仅限树状、平面或标记）。

**todo树。树按钮。groupByTag** (`true`)</br>在树状视图标题栏中显示一个按钮，以启用按标记对项目进行分组。

**todo树。树按钮。groupBySubTag** (`false`)</br>在树状视图标题栏中显示一个按钮，以启用按子标记对项目进行分组。

<sup>_注意：只有在树中找到子标记并存在子标记时，此按钮才可见。_</sup>

**todo树。树按钮。滤器** (`true`)</br>在树状视图标题栏中显示一个按钮，允许通过输入一些文本来过滤树。

**todo树。树按钮。刷新** (`true`)</br>在树状视图标题栏中显示刷新按钮。

**todo树。树按钮。扩大** (`true`)</br>在树状视图标题栏中显示按钮以展开或折叠整个树。

**todo树。树按钮。出口** (`false`)</br>在树状视图标题栏中显示按钮，以创建显示树内容的文本文件。

<sup>*</sup>*仅适用于新工作区。在工作区中更改视图后，将存储当前状态\*

**todo树。范围** (`{}`)</br>定义一组文件作用域，可以使用*todo树。开关示波器*命令

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

### Multiline TODOs

如果正则表达式包含`\n`，则将启用多行 TODO。在这种模式下，搜索结果的处理方式略有不同。如果发现结果不包含来自的任何标记`todo-tree.general.tags`假设它们属于之前的结果，该结果确实有标签。例如，如果将正则表达式设置为：

```json
"todo-tree.regex.regex": "(//)\\s*($TAGS).*(\\n\\s*//\\s{2,}.*)*"
```

这将匹配多行 TODO，其中额外的行在注释字符和 TODO 项之间至少有两个空格。例如

```json
// TODO multiline example
//  second line
//  third line
```

如果你想在 C++风格的多行注释块中匹配 multiline TODOs，你需要一些类似的东西：

```json
"todo-tree.regex.regex": "(/\\*)\\s*($TAGS).*(\\n\\s*(//|/\\*|\\*\\*)\\s{2,}.*)*"
```

哪个应该匹配：

```json
/* TODO multiline example
**  second line
**  third line
*/
```

<sup>_注意：如果使用设置 GUI 修改设置，则无需转义每个反斜杠。_</sup>

**警告：多行 TODO 不能与降价 TODO 一起使用，可能会产生其他意外结果。性能也可能会降低。**

### Excluding files and folders

要限制搜索的文件夹集，可以定义`todo-tree.filtering.includeGlobs`.这是一个全局数组，搜索结果与之匹配。如果结果与任何一个球体匹配，则将显示它们。默认情况下，数组为空，与所有内容匹配。看见[here](https://code.visualstudio.com/api/references/vscode-api#GlobPattern)更多关于地球仪的信息。

<sup>_注意：全局路径是绝对路径，而不是相对于当前工作区。_</sup>

要从搜索中排除文件夹/文件，可以定义`todo-tree.filtering.excludeGlobs`。如果搜索结果与这些全局匹配，则将忽略这些结果。

还可以使用关联菜单从树中包括和排除文件夹。此文件夹筛选器单独应用于包含/排除全局。

<sup>_注意：默认情况下，ripgrep 会忽略您数据库中的文件和文件夹`.gitignore`或`.ignore`文件夹。如果要包含这些文件，请设置_ `todo-tree.ripgrep.ripgrepArgs` _到_ `--no-ignore`.</sup>

### Markdown Support

在第一次编写扩展时，只需在默认正则表达式中添加一个模式，即可添加非常基本的降价支持`- [ ]`“.处理降价todo的更好方法是添加”`(-|\d+.)`“添加到正则表达式第一部分的“注释”列表中，然后添加”`[ ]`“和”`[x]`“转到中的标签列表”`settings.json`，例如：

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

<sup>_注意：如果通过 GUI 修改设置，请替换_ `\\` _在正则表达式设置中_ `\`.</sup>

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

它将把todo染成红色，完成todo染成绿色。

最后，它将允许按标签（和子标签）进行分组，并且在状态栏中显示计数时效果更好。

<sup>_注意：默认正则表达式将在将来某个时候更新以反映这些更改。_<sup>

## Known Issues

仅当您的配置使用`todo-tree.general.tags`背景旧版本的扩展直接在`todo-tree.regex.regex`而现在，正则表达式取代了**$TAGS**内容包括`todo-tree.general.tags`.

按标记分组不适用于降价任务列表项，因为没有可用于分组的标记。该树将显示标记组旁边的文件。

按标记分组时，在树状图中跟踪文件将显示找到的第一个标记。

当没有当前工作区时，默认图标将显示在树中。

## Donate

如果你觉得这个扩展很有用，请随时捐款[here](https://paypal.me/Gruntfuggly)谢谢

### Credits

使用的是[ripgrep-js](https://www.npmjs.com/package/ripgrep-js).

主要图标最初由[Freepik](http://www.freepik.com)从…起[www.flaticon.com](https://www.flaticon.com/)是由[CC 3.0 BY](http://creativecommons.org/licenses/by/3.0/)

树视图图标由[Vaadin](https://www.flaticon.com/authors/vaadin)从…起[www.flaticon.com](https://www.flaticon.com/)是由[CC 3.0 BY](http://creativecommons.org/licenses/by/3.0/)

标签图标由[Dave Gandy](https://www.flaticon.com/authors/dave-gandy)从…起[www.flaticon.com](https://www.flaticon.com/)是由[CC 3.0 BY](http://creativecommons.org/licenses/by/3.0/)

标签图标由[Vectors Market](https://www.flaticon.com/authors/vectors-market)从…起[www.flaticon.com](https://www.flaticon.com/)是由[CC 3.0 BY](http://creativecommons.org/licenses/by/3.0/)

展示由[Gregor Cresnar](https://www.flaticon.com/authors/gregor-cresnar)从…起[www.flaticon.com](https://www.flaticon.com/)

很多图标现在都被更新了[johnletey](https://github.com/johnletey)以匹配新的 VS 代码 1.37.0 GUI。非常感谢！

#### Translations

简体中文翻译[loniceras](https://github.com/loniceras).
