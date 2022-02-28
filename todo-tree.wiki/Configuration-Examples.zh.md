# Regexs for various languages

<!-- doc-templite START generated -->
<!-- repo = 'Gruntfuggly/todo-tree.wiki' -->
<!-- commit = '70ee9d2b7cb1fc9067f67c9cc843d3b5709e1585' -->
<!-- time = '2021-10-25' -->

| 翻译的原文 | 与日期      | 最新更新 | 更多                       |
| ---------- | ----------- | -------- | -------------------------- |
| [commit]   | ⏰ 2021-10-25 | ![last]  | [中文翻译][translate-list] |

[last]: https://img.shields.io/github/last-commit/Gruntfuggly/todo-tree.wiki.svg
[commit]: https://github.com/Gruntfuggly/todo-tree.wiki/tree/70ee9d2b7cb1fc9067f67c9cc843d3b5709e1585

<!-- doc-templite END generated -->


如果直接在中修改设置`settings.json`您需要避开反斜杠，如以下示例所示。如果使用的是设置GUI，则只需一个反斜杠。

*注意：我还没有亲自测试所有这些，所以你可能需要做进一步的调整。<https://regex101.com/>是一个有用的实验网站。*

## COBOL

```json
"todo-tree.regex.regex": "(//|#|<!--|;|/\\*|\\*>|^......\\*)\\s*($TAGS)"
```

或者在设置GUI中：

待办事项树：正则表达式：正则表达式：**`(//|#|<!--|;|/\*|\*>|^......\*)\s*($TAGS)`**

## Fortran

```json
"todo-tree.regex.regex": "(//|#|<!--|;|/\\*|!|^|^[ \\t]*(-|\\d+.))\\s*($TAGS)"
```

或者在设置GUI中：

待办事项树：正则表达式：正则表达式：**`(//|#|<!--|;|/\*|!|^|^[ \t]*(-|\d+.))\s*($TAGS)`**

## Haskell

```json
"todo-tree.regex.regex": "((--\\s*($TAGS))|\\{-\\s($TAGS).*(\\n.*)*-})"
```

或者在设置GUI中：

待办事项树：正则表达式：正则表达式**`((--\s*($TAGS))|\{-\s($TAGS).*(\n.*)*-})`**

## JavaDoc

```json
"todo-tree.regex.regex": "(//|#|<!--|/\\*|^\\s*\\*)\\s*($TAGS)"
```

或者在设置GUI中：

待办事项树：正则表达式：正则表达式：**`(//|#|<!--|/\*|^\s*\*)\s*($TAGS)`**

它会匹配的

-   `//`
-   `#`
-   `<!--`
-   `/*`, 
-   `*`（适用于JSDoc）

也适用于JS、BASH、PHP、HTML、CSS、MD、JSON、XML。

## LaTeX

```json
"todo-tree.regex.regex": "((//|#|<!--|;|/\\*|^|%|\\\\)\\s*($TAGS)\\{*|^\\s*- \\[ \\])",
```

或者在设置GUI中：

待办事项树：正则表达式：正则表达式：**`((//|#|<!--|;|/\*|^|%|\\)\s*($TAGS)\{*|^\s*- \[ \])`**

*注意：对于LaTeX，您可能还需要添加标签`todo`（小写）或set`todo-tree.regex.regexCaseSensitive`这是假的。*

## Markdown

如果要突出显示未完成/完成的待办事项，以下配置非常有用。

```json
"todo-tree.regex.regex": "((//|#|<!--|;|/\\*|^)\\s*($TAGS)|^//\\s*\\[x\\]|^//\\s*\\[ \\])",
"todo-tree.general.tags": [
  "TODO",
  "[x]",
  "[ ]",
],
"todo-tree.highlights.customHighlight": {
  "[x]":{
    "foreground": "#64dd17",
    "background":"#008800"
  },
  "[ ]":{
    "foreground": "#f44336",
    "background": "#592c2c",
  },
}
```

## Ocaml (and other ML languages using `(* comment *)` style comments)

```json
"todo-tree.regex.regex": "(//|#|<!--|;|/\\*|^|\\(\\*)\\s*($TAGS)"
```

或者在设置GUI中：

待办事项树：正则表达式：正则表达式：**`(//|#|<!--|;|/\*|^|\(\*)\s*($TAGS)`**

## PQSL

```json
"todo-tree.regex.regex": "(//|#|<!--|;|/\\*|^|\\(\\*|--)\\s*($TAGS)"
```

或者在设置GUI中：

待办事项树：正则表达式：正则表达式：**`(//|#|<!--|;|/\*|^|\(\*|--)\s*($TAGS)`**

## PHP

符合标准`@todo`标签：

```json
"todo-tree.regex.regex": "(//|#|<!--|;|/?\\*|^|^[ \\t]*(-|\\d+.))\\s*($TAGS)",
"todo-tree.general.tags": [
    "@todo",
    "TODO",
    "FIXME"
  ]
```

## Rust

也符合标准`todo!()`宏：

```json
"todo-tree.regex.regex": "((//|#|<!--|;|/\\*|^)\\s*($TAGS)|($TAGS)!.*)",
"todo-tree.regex.regexCaseSensitive": false,
```

## Add PUG, BAT, and Markdown files

-   帕格评论：`//- TODO: PUG EXAMPLE` (`\/\/-|`)
-   BAT评论：`REM TODO: BAT example` (`REM|`)
-   降价清单：`- TODO: Markdown Example` (`-|`)

```json
"todo-tree.regex.regex": "((\/\/|\/\/-|#|<!--|;|REM|\/\\*|^|-)\\s*($TAGS))"
```

或者在设置GUI中：

待办事项树：正则表达式：正则表达式：**`((\/\/|\/\/-|#|<!--|;|REM|\/\*|^|-)\s*($TAGS))`**

## Generic Catchall

只要你的注释以`:`你可以试试：`"todo-tree.regex.regex": "((\\s|^)($TAGS):)"`

或者在设置GUI中：

待办事项树：正则表达式：正则表达式：**`((\s|^)($TAGS):)`**

# Multiline regexs

这些都很复杂，所以你可以尝试下面的方法，看看它们是否适合你。。。

```json
"todo-tree.regex.regex": "(?:(?://|#|<!--|;|/\\*\\*?|\\*)\\s*($TAGS)|^\\s*- \\[ \\])"
```

```json
"todo-tree.regex.regex": "((//|#|;|\\*)[ ]*($TAGS)[^\\n]*)|(/\\*(\\*?\\s*)*($TAGS)(.|\\n|\\r)*?\\*/)|(<!--\\s*($TAGS)(.|\\n|\\r)*?-->)"
```

```json
"todo-tree.regex.regex": "((//|#|;)[ ]*($TAGS)[^\\n]*)|(/\\*(\\*?\\s*)*($TAGS)(.|\\n|\\r)*?\\*/)|(<!--\\s*($TAGS)(.|\\n|\\r)*?-->)"
```

```json
"todo-tree.regex.regex": "(//|\\*|#|<!--|;|/\\*|^|^[ \\t]*(-|\\d+.))\\s*($TAGS)"
```

或者在设置GUI中：

待办事项树：正则表达式：正则表达式：**`(?:(?://|#|<!--|;|/\*\*?|\*)\s*($TAGS)|^\s*- \[ \])`**

待办事项树：正则表达式：正则表达式：**`((//|#|;|\*)[ ]*($TAGS)[^\n]*)|(/\*(\*?\s*)*($TAGS)(.|\n|\r)*?\*/)|(<!--\s*($TAGS)(.|\n|\r)*?-->)`**

待办事项树：正则表达式：正则表达式：**`((//|#|;)[ ]*($TAGS)[^\n]*)|(/\*(\*?\s*)*($TAGS)(.|\n|\r)*?\*/)|(<!--\s*($TAGS)(.|\n|\r)*?-->)`**

待办事项树：正则表达式：正则表达式：**`(//|\*|#|<!--|;|/\*|^|^[ \t]*(-|\d+.))\s*($TAGS)`**

# Globs

一个有用的排除全局列表：

```json
"todo-tree.filtering.excludeGlobs": [
        "**/vendor/**",
        "**/node_modules/**",
        "**/dist/**",
        "**/bower_components/**",
        "**/build/**",
        "**/.vscode/**",
        "**/.github/**",
        "**/_output/**",
        "**/*.min.*",
        "**/*.map"
    ]
```
