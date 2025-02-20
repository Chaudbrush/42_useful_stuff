# 42_Tools

###
Few links and configs to help me through my journey at 42 School
* **[Vim](##--Vim)**
###

---
## Vim
### - Personal Config
set nu</br>
syntax on</br>
set mouse=a	"Enable mouse</br>
set noswapfile	"Disable swap files</br>
set tabstop=4 "Indentation</br>
set shiftwidth=4</br>
set autoindent</br>
set smartindent</br>
set showmatch</br>
set ruler</br>
set colorcolumn=80</br>
hi colorcolumn ctermbg=180</br>
set list</br>
set listchars=tab:\>\ ,eol:$</br>
inoremap ( ()<left> "Remap keys</br>
inoremap [ []<left></br>
inoremap { {}<left></br>
inoremap ' ''<left></br>
inoremap " ""<left></br>

---

### - Shortcuts
If feeling rusty: [Vim genius](http://www.vimgenius.com/)
- `Ctrl + Z` Get back to shell
- `fg` Get back to vim
- `i` Insert at cursor
- `I` Insert at start of line
- `o` Insert mode line below
- `O` Insert mode line above
- `A` Append at eol
- `0` Go to beginning of line
- `$` Go to eol
- `^` Go to start of first string
- `w` Jump to beginning of next word
- `b` Go back to beginning of previous word
- `e` Jump to end of next word
- `u` Undo
- `Ctrl + r` Redo
- `yy` Copy
- `p` Paste
- `dd` Delete line
- `dw` Delete word
- `x` Delete char
- `r` Replace char
- `:%s/foo/bar/g` Search and replace

###
