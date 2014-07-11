## taboo.vim

Taboo aims to ease the way you set the vim tabline. In addition, Taboo provides fews useful utilities for renaming tabs.

### Installation

Install either with [Vundle](https://github.com/gmarik/vundle), [Pathogen](https://github.com/tpope/vim-pathogen) or [Neobundle](https://github.com/Shougo/neobundle.vim).

**NOTE**: tabs look different in terminal vim than in gui versions. If you wish having terminal style tabs even in gui versions you have to add the following line to your .vimrc file
```vim
set guioptions-=e
```

Taboo is able to remeber custom tab names when you save the current session but you are required to set the following option in your .vimrc file
```vim
set sessionoptions+=tabpages,globals
```

### Commands

**TabooRename {name}**

Renames the current tab with the name provided.

**TabooOpen {name}**

Opens a new tab and and gives it the name provided.

**TabooReset**

Removes the custom label associated with the current tab.

### Basic options

**g:taboo\_tab\_format**

With this option you can customize the way tabs look like. Below all the available items:

- `%f`: the name of the first buffer open in the tab
- `%a`: the path relative to `$HOME` of the first buffer open in the tab
- `%n`: the tab number, but only on the active tab
- `%N`: the tab number on each tab
- `%w`: the number of windows opened into the tab, but only on the active tab
- `%W`: the number of windows opened into the tab, on each tab
- `%m`: the modified flag

Default: ` %f%m `

**g:taboo\_renamed\_tab\_format**

Same as `g:taboo_tab_format` but for renamed tabs. In addition, you can use the following items:

- `%l`: the custom tab name set with `:TabooRename`

Note that with renamed tabs the items `%f` and `%a` will be evaluated to an empty string.

Default: ` [%f]%m `

**g:taboo\_modified\_tab\_flag**

This option controls how the modified flag looks like.

Default: `*`

**g:taboo\_tabline**

Turn off this option and Taboo won't get in the way of your tabline.

Default: `1`

### Public interface

Taboo provides a couple of public functions that may be used by third party plugins:

- `TabooTabTitle`: this function returns the formatted tab title according to the options `g:taboo_tab_format` and `g:taboo_renamed_tab_format` (for renamed tabs).
- `TabooTabName`: this function returns the name of a renamed tab. If a tab has no name, an empty string is returned.
