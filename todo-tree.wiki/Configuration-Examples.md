# Regexs for various languages

If you are modifying the settings directly in `settings.json` you'll need to escape the backslashes, as shown in these examples. If you are using the setting GUI, you only need one backslash.

*Note: I haven't personally tested all of these, so you may need to make further tweaks. <https://regex101.com/> is a useful website for experimenting.*

## COBOL

```json
"todo-tree.regex.regex": "(//|#|<!--|;|/\\*|\\*>|^......\\*)\\s*($TAGS)"
```

or in the settings GUI:

Todo Tree: Regex: Regex: **`(//|#|<!--|;|/\*|\*>|^......\*)\s*($TAGS)`**

## Fortran

```json
"todo-tree.regex.regex": "(//|#|<!--|;|/\\*|!|^|^[ \\t]*(-|\\d+.))\\s*($TAGS)"
```

or in the settings GUI:

Todo Tree: Regex: Regex: **`(//|#|<!--|;|/\*|!|^|^[ \t]*(-|\d+.))\s*($TAGS)`**

## Haskell

```json
"todo-tree.regex.regex": "((--\\s*($TAGS))|\\{-\\s($TAGS).*(\\n.*)*-})"
```

or in the settings GUI:

Todo Tree: Regex: Regex **`((--\s*($TAGS))|\{-\s($TAGS).*(\n.*)*-})`**

## JavaDoc 

```json
"todo-tree.regex.regex": "(//|#|<!--|/\\*|^\\s*\\*)\\s*($TAGS)"
```

or in the settings GUI:

Todo Tree: Regex: Regex: **`(//|#|<!--|/\*|^\s*\*)\s*($TAGS)`**

It will match
- `//`
- `#`
- `<!--`
- `/*`, 
- `* `(for JSDoc)

Also works with JS, BASH, PHP, HTML, CSS, MD, JSON, XML.

## LaTeX

```json
"todo-tree.regex.regex": "((//|#|<!--|;|/\\*|^|%|\\\\)\\s*($TAGS)\\{*|^\\s*- \\[ \\])",
```

or in the settings GUI:

Todo Tree: Regex: Regex: **`((//|#|<!--|;|/\*|^|%|\\)\s*($TAGS)\{*|^\s*- \[ \])`**

*Note: For LaTeX, you will probably also want to add the tag `todo` (lowercase), or set `todo-tree.regex.regexCaseSensitive` to false.*

## Markdown

The following config is useful if you want to highlight incomplete/complete TODOs.

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

or in the settings GUI:

Todo Tree: Regex: Regex: **`(//|#|<!--|;|/\*|^|\(\*)\s*($TAGS)`**


## PQSL

```json
"todo-tree.regex.regex": "(//|#|<!--|;|/\\*|^|\\(\\*|--)\\s*($TAGS)"
```

or in the settings GUI:

Todo Tree: Regex: Regex: **`(//|#|<!--|;|/\*|^|\(\*|--)\s*($TAGS)`**

## PHP

To match standard `@todo` tags:

```json
"todo-tree.regex.regex": "(//|#|<!--|;|/?\\*|^|^[ \\t]*(-|\\d+.))\\s*($TAGS)",
"todo-tree.general.tags": [
    "@todo",
    "TODO",
    "FIXME"
  ]
```

## Rust

To also match standard `todo!()` macros:

```json
"todo-tree.regex.regex": "((//|#|<!--|;|/\\*|^)\\s*($TAGS)|($TAGS)!.*)",
"todo-tree.regex.regexCaseSensitive": false,
```

## Add PUG, BAT, and Markdown files

- PUG comments: `//- TODO: PUG EXAMPLE` (`\/\/-|`)
- BAT comments: `REM TODO: BAT example` (`REM|`)
- Markdown list: `  - TODO: Markdown Example` (`-|`)

```json
"todo-tree.regex.regex": "((\/\/|\/\/-|#|<!--|;|REM|\/\\*|^|-)\\s*($TAGS))"
```

or in the settings GUI:

Todo Tree: Regex: Regex: **`((\/\/|\/\/-|#|<!--|;|REM|\/\*|^|-)\s*($TAGS))`**

## Generic Catchall

As long as your annotations end with a `:` you can try: `"todo-tree.regex.regex": "((\\s|^)($TAGS):)"`

or in the settings GUI:

Todo Tree: Regex: Regex: **`((\s|^)($TAGS):)`**

# Multiline regexs

These get quite complex, so you can try the following to see if they work for you...

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

or in the settings GUI:

Todo Tree: Regex: Regex: **`(?:(?://|#|<!--|;|/\*\*?|\*)\s*($TAGS)|^\s*- \[ \])`**

Todo Tree: Regex: Regex: **`((//|#|;|\*)[ ]*($TAGS)[^\n]*)|(/\*(\*?\s*)*($TAGS)(.|\n|\r)*?\*/)|(<!--\s*($TAGS)(.|\n|\r)*?-->)`**

Todo Tree: Regex: Regex: **`((//|#|;)[ ]*($TAGS)[^\n]*)|(/\*(\*?\s*)*($TAGS)(.|\n|\r)*?\*/)|(<!--\s*($TAGS)(.|\n|\r)*?-->)`**

Todo Tree: Regex: Regex: **`(//|\*|#|<!--|;|/\*|^|^[ \t]*(-|\d+.))\s*($TAGS)`**

# Globs

A useful exclude globs list:

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