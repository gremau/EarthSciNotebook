# Vim tips

Notes on using Vim effectively.

 **See also:** [General programming
        page](programming), [the Awk page](awk),
        [Textfile tips](textfiles).

#### .vimrc

The *\~/.vimrc* file is where vim looks first for settings when starting
up. *\~/.gvimrc* can be used to set options in the GUI version of Vim.
*.vimrc* is read first.

#### Encrypting files

Files can be encrypted using the -x flag. Typing:

vim -x `<filename>

will prompt for a password and then open a new or existing file in
encrypted mode. This file will subsequently be saved in encrypted form
and will require a password to open it again. An already open file can
also be encrypted with *:X*. The default level of encryption is not so
secure (zip), so there are options to change that.

:set cryptmethod?         # Display the current encryption algorithm
:set cryptmethod=blowfish # Set to the much more secure blowfish cipher.
`

#### Diffing files (Vimdiff)

Vim (gvim) can be used to diff two or more files and merge changes
between them (see [vimdiff
docs](http://vimdoc.sourceforge.net/htmldoc/diff.html)). Use:

vimdiff `<file1>`<file2>

The files will show up side by side (vertical split, use *-o* for
horizontal), with changes highlighted in pink/red, and they can then be
edited. *viewdiff* or *gviewdiff* is used to open a read-only diff view.
Diff view can also be started from within a vim session (see docs). Once
started, these are the basic commands for merging changes:

* **do** - Get changes from other window into the current window.
* **dp** - Put the changes from current window into the other window.
* **]c** - Jump to the next change.
* **[c** - Jump to the previous change.
* **Ctrl W + Ctrl W** - Switch to the other split window.`

#### Search/Replace strange unicode characters

Sometimes there are funky non-standard characters in file that don't
display, print, or are simply undesired. For example, hyphens, minus
signs, and dashes have a number of permutations and it is best to use
them consistently. They frequently get mixed up in text files,
especially when copying from strange formats (i.e. Word, Excel, etc.).

- Place cursor over the funky character and type `*`ga`*`. This gives ascii value in decimal, hexidecimal, and octal format.
- Form a search/replace command using the ascii value, prepended by some regexp syntax:.
  * `*`%dNN`*is the symbol for a decimal ascii code, where `*`NN`*is the first code given by `*`ga`*`.
  * `*`%xNN`*is the symbol for a hexidecimal ascii code.
  * `*`%oNN`*is the symbol for an octal ascii code.
  * Use `*`%uNN`*for multibyte characters.
  * Don't forget to escape this (with a \)!`

For example, say there is a funky minus sign in my file. I *ga* over it
and it has the hex value of 2212. I can then search and replace it with
regular hyphen-minus using:

:%s/\%x2212/-/g`

#### Tabs and tabkey behaviour

I prefer 4 columns of whitespace for each indent in a file, and I prefer
to use spaces for this, not tabs. This means pressing the <Tab> should
give a defined number of spaces. This can be set in *\~.vimrc*.

set expandtab       "When `<tab>key is pressed, insert spaces, not hard tabs.
set tabstop=4       "Number of columns per tab
set softtabstop=4   "Match to tabstop unless expandtab is unset, then it may set to use tabs + spaces
set shiftwidth=4    "Number of columns for indent and autoindent`

When editing a file with different tab settings, *retab* will change all
tabs to the settings in *.vimrc*. A hard tab can be inserted by pressing
<Ctrl-V><Tab>.
