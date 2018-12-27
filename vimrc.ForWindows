" File: .vimrc
" Author: AntonyBonn
" Last Modified: 九月 04, 2016
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                               General Setting                               "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" This line should not be removed as it ensures that various options are
" properly set to work with the Vim-related packages available in Debian.
runtime! debian.vim

if filereadable("/etc/vim/vimrc.local") "载入全局设定
  source /etc/vim/vimrc.local
endif
set nocompatible "设置不完全兼容vi
source $VIMRUNTIME/vimrc_example.vim
set nu! "显示行号
set encoding=utf-8 "编码设定
set langmenu=zh_CN.UTF-8
source $VIMRUNTIME/delmenu.vim
source $VIMRUNTIME/menu.vim
language message zh_CN.UTF-8
if has("win32") || has("win64") "字体设置
	set guifont=Consolas:h12:cDEFAULT
else
	set guifont=Monaco\ 10 
endif
if has("win32") || has("win64")
    set linespace=-1 "设置行间距
else
    set linespace=-1 "设置行间距
endif
set lines=35 columns=118 "设置启动窗口大小
if has("syntax") "语法高亮 (Vim5之后的版本支持高亮)
  syntax on
endif
colorscheme desert "设置主题色
"colorscheme solarized
"colorscheme molokai
"colorscheme phd
set history=500 "设置命令历史行数 
filetype on                      " 侦测文件类型  
filetype indent on               " 针对不同的文件类型采用不同的缩进格式  
filetype plugin on               " 针对不同的文件类型加载对应的插件  
filetype plugin indent on "启用自动补全
set mouse=a " 使能鼠标
set autowrite " 在像:next和:make等命令前自动保存
if has("autocmd") " 重新打开文件时跳转到last position
  au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g'\"" | endif
endif
set showcmd         " 未完成的指令也显示
set scrolloff=3     " 在上下移动光标时，光标的上方或下方至少会保留显示的行数
set showmatch		" 在输入成对的括号时，Vim 会帮助你跳转并高亮一下匹配的括号,然后回到你正在输入的位置
set matchtime=1     "showmatch匹配时间最多100ms
set hlsearch        "高亮显示所有匹配项
" 设置快捷键将选中文本块复制至系统剪贴板
vnoremap <leader>y "+y
" 设置快捷键将系统剪贴板内容粘贴至 vim
nmap <leader>p "+p
" 定义快捷键关闭当前分割窗口
nmap <leader>q :q<CR>
" 定义快捷键保存当前窗口内容
nmap <leader>w :w<CR>
" 让配置变更立即生效
autocmd BufWritePost $MYVIMRC source $MYVIMRC

"设置ctags
set autochdir
set tags=tags;/

set fileformat=unix
""""""""
" 折叠 "
""""""""
setl foldenable "设置折叠
set foldcolumn=3 "设置折叠区域的宽度
setlocal foldlevel=1 "设置折叠层数
set foldlevelstart=99 "打开文件是默认不折叠代码
"空格键打开关闭折叠
nnoremap <space> za 
autocmd filetype c,cpp  setl foldmethod=syntax "设置C，C++文件自动折叠和格式
""""""""
" 缩进 "
""""""""
"设置Tab代表的字符数
set tabstop=4
"设置自动缩进字符数
set shiftwidth=4
"设置自动缩进
set autoindent
"让 vim 把连续数量的空格视为一个制表符
set softtabstop=4
""""""""""""""""""""""""""""
"  状态行（命令行）的显示  "
""""""""""""""""""""""""""""
set cmdheight=1          " 命令行（在状态行下）的高度，默认为1 
set ruler                " 右下角显示光标位置的状态行  
set laststatus=2         " 开启状态栏信息   
set wildmenu             " 增强模式中的命令行自动完成操作  
""""""""""
"  查找  "
""""""""""
set hlsearch                 " 开启高亮显示结果  
set incsearch                " 开启实时搜索功能  
set smartcase		         " smart matching(当模式中有大写字母时对大小写敏感)
""""""""""""""""""""""""
"       自动匹配       "
""""""""""""""""""""""""
if &filetype == 'c' || &filetype == 'cpp'
	:inoremap < <><ESC>i
"   :inoremap > <c-r>=ClosePair('>')<CR>  
    :inoremap ` ``<ESC>i 
endif
"function ClosePair(char)  
"    if getline('.')[col('.')-1] == a:char  
"        return "\<Right>"
"    else  
"        return a:char
"    endif  
"endf

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                              For WINDOWS gvim                               "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

if has("win32") || has("win64")
	filetype off
    source $VIMRUNTIME/mswin.vim
    behave mswin

    set diffexpr=MyDiff()
    function MyDiff()
      let opt = '-a --binary '
      if &diffopt =~ 'icase' | let opt = opt . '-i ' | endif
      if &diffopt =~ 'iwhite' | let opt = opt . '-b ' | endif
      let arg1 = v:fname_in
      if arg1 =~ ' ' | let arg1 = '"' . arg1 . '"' | endif
      let arg2 = v:fname_new
      if arg2 =~ ' ' | let arg2 = '"' . arg2 . '"' | endif
      let arg3 = v:fname_out
      if arg3 =~ ' ' | let arg3 =yournamerg3 . '"' | endif
      let eq = ''
      if $VIMRUNTIME =~ ' '
        if &sh =~ '\<cmd'ournameyoyourname
          let cmd = '""' . $VIMRUNTIME . '\diff"'
          let eq = '"'
        else
          let cmd = substitute($VIMRUNTIME, ' ', '" ', '') . '\diff"'
        endif
      else
        let cmd = $VIMRUNTIME . '\diff'
      endif
      silent execute '!' . cmd . ' ' . opt . arg1 . ' ' . arg2 . ' > ' . arg3 . eq
    endfunction
else
	let $VIMRUNTIME = "/usr/share/vim/vim74"
endif

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                            General Map Settings                             "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" 定义快捷键的前缀，即<leader>
" let mapleader="\"
"""""""""
"  Map  "
"""""""""
"Ctrl+a小写转大写
inoremap <C-u> <esc>gUiwea
"<F11>新建tab
map <F11> :tabnew <CR>
"<F12>关闭标签
map <F12> :close <CR>
"Ctrl+s保存
map <C-s> :w <CR>
"Ctrl+a全选
map <C-a> ggv <S-g>
"上下左右
inoremap <A-j> <Down>
inoremap <A-k> <Up>
inoremap <A-l> <Right>
inoremap <A-h> <Left>
"退出:ESC!
inoremap jk <Esc>
"分屏移动
map <c-j> <c-w>j
map <c-k> <c-w>k
map <c-l> <c-w>l
map <c-h> <c-w>h

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                                   编译运行调试                              "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" F5编译和运行C程序，C++程序,Java程序，Python程序，shell程序，F9 gdb调试
" 请注意，下述代码在windows下使用会报错，需要去掉./这两个字符
if has("win32") || has("win64")
	map <F5> :call CompileRunGcc()<CR>
	func! CompileRunGcc()
	    exec "w"
	    if &filetype == 'c'
	        exec "!g++ % -o %<"
	        exec "! %<"
	    elseif &filetype == 'cpp'
	        exec "!g++ % -o %<"
	        exec "! %<"
	    elseif &filetype == 'java' 
	        exec "!javac %" 
	        exec "!java %<"
	    elseif &filetype == 'sh'
	        :!%
	    endif
	endfunc
	map <F8> :call Rungdb()<CR>  
	func! Rungdb()  
	    exec "w"  
	    exec "!g++ % -g -o %<"  
	    exec "!gdb %<"  
	endfunc  
else
	map <F5> :call CompileRunGcc()<CR>
	func! CompileRunGcc()
	    exec "w"
	    if &filetype == 'c'
			exec "!gcc % -g -o %<"
			exec "! ./%<"
	    elseif &filetype == 'cpp'
	        exec "!g++ % -g -o %<"
			exec "! ./%<"
	    elseif &filetype == 'java' 
	        exec "!javac %"
			exec ":cd %:p:h"
	        exec "!java %<"
        elseif &filetype == 'py'
            exec "!python %"
	    elseif &filetype == 'sh'
	        exec "!chmod a+x %"
			exec "!./%"
	    endif
	endfunc
	
	map <f9> :call Debug()<cr>
	func!  Debug()
		exec "w"
		if &filetype == 'c'
			exec "!gcc % -o %< -gstabs+"
			exec "!gdb %<"
		elseif &filetype == 'cpp'
			exec "!g++ % -o %< -gstabs+"
			exec "!gdb %<"
		endif
	endfunc

endif

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                               For the VUNDLE                                "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

set nocompatible              " 去除VI一致性,必须
filetype off                  " 必须

if has("win32") || has("win64")
    "Vundle的路径
    set rtp+=$VIM/vimfiles/bundle/Vundle.vim
    "插件的安装路径
    call vundle#begin('$VIM/vimfiles/bundle/')
else
    " 设置包括vundle和初始化相关的runtime path
    set rtp+=~/.vim/bundle/Vundle.vim
    call vundle#begin()
    " 另一种选择, 指定一个vundle安装插件的路径
    "call vundle#begin('~/some/path/here')
endif

" 让vundle管理插件版本,必须
Plugin 'VundleVim/Vundle.vim'

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                               Plugin Examples                               "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" 以下范例用来支持不同格式的插件安装.
" 请将安装插件的命令放在vundle#begin和vundle#end之间.

" Github上的插件
" 格式为 Plugin '用户名/插件仓库名'
"Plugin 'tpope/vim-fugitive'

" 来自 http://vim-scripts.org/vim/scripts.html 的插件
" Plugin '插件名称' 实际上是 Plugin 'vim-scripts/插件仓库名' 只是此处的用户名可以省略
"Plugin 'L9'

" 由Git支持但不再github上的插件仓库 Plugin 'git clone 后面的地址'
"Plugin 'git://git.wincent.com/command-t.git'

" 本地的Git仓库(例如自己的插件) Plugin 'file:///+本地插件仓库绝对路径'
"Plugin 'file:///home/gmarik/path/to/plugin'

" 插件在仓库的子目录中.
" 正确指定路径用以设置runtimepath. 以下范例插件在sparkup/vim目录下
"Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}

" 安装L9，如果已经安装过这个插件，可利用以下格式避免命名冲突
"Plugin 'ascenator/L9', {'name': 'newL9'}

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                                 Own Plugins                                 "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

""""""""""""
"  Others  "
""""""""""""
"a.vim - Alternate Files quickly (.c --> .h etc)
Plugin 'vim-scripts/a.vim'
""""""""""
"  格式  "
""""""""""
"代码折叠
Plugin 'tmhedberg/SimpylFold'
"Python 自动缩进
Plugin 'vim-scripts/indentpython.vim'
"每次保存文件时Vim都会检查代码的语法
Plugin 'scrooloose/syntastic'
"PEP8代码风格检查<F7>
Plugin 'nvie/vim-flake8'
"按照pep8标准自动格式化<F8>
Plugin 'tell-k/vim-autopep8'
""""""""""
"  文件  "
""""""""""
"集成git,在原本命令前面加上G
Plugin 'tpope/vim-fugitive'
"Powerline是一个状态栏插件，可以显示当前的虚拟环境、Git分支、正在编辑的文件等信息
"这个插件是用Python编写的，支持诸如zsh、bash、tmux和IPython等多种环境
"Plugin 'Lokaltog/powerline', {'rtp': 'powerline/bindings/vim/'}
"Poweline增强版
Plugin 'vim-airline/vim-airline'
"文件树形结构浏览
Plugin 'scrooloose/nerdtree'
"多文件共享nerdtree
Plugin 'jistr/vim-nerdtree-tabs'
"nerdtree显示git状态插件
Plugin 'Xuyuanp/nerdtree-git-plugin'
"查看本地文件修改历史记录
Plugin 'vim-scripts/Gundo'
""""""""""
"  查找  "
""""""""""
"Ctrl+P搜索任何文件
Plugin 'kien/ctrlp.vim'
"LookupFile插件
Plugin 'vim-scripts/lookupfile'
Plugin 'vim-scripts/genutils' " Lookupfile所必须的插件
"列出当前文件中的所有宏, 全局变量, 函数名等
Plugin 'vim-scripts/taglist.vim'
"比taglist更适合c++使用，函数能够按类区分，支持按类折叠显示等
Plugin 'majutsushi/tagbar'
"Grep for VIM
Plugin 'EasyGrep'
""""""""""
"  补全  "
""""""""""
"YouCompleteMe
Bundle 'Valloric/YouCompleteMe'
"使YouCompleteMe支持Javascript补全
"Plugin 'ternjs/tern_for_vim'
"括号和引号自动补全
Plugin 'jiangmiao/auto-pairs'
""""""""""""""
"  markdown  "
""""""""""""""
"markdown 高亮插件
Plugin 'godlygeek/tabular' "必须的支持
Plugin 'plasticboy/vim-markdown'
"markdown 实时预览插件
Plugin 'suan/vim-instant-markdown'
""""""""""""""
"  代码片段  "
""""""""""""""
"自动补全代码块插件
Plugin 'sirver/UltiSnips'
"预设代码集合补全
Plugin 'honza/vim-snippets'
""""""""""""
"  Python  "
""""""""""""
"Rope is a Python Library
Plugin 'python-rope/ropevim'
"查看python模块的 docstrings 信息
Plugin 'vim-scripts/pydoc.vim'
""""""""""""
"  Matlab  "
""""""""""""
"Contains a set of files useful to edit Matlab files.
"Included is :
"1) Syntax highlighting
"2) Correct setting to use the matchit.vim script (extension of the % command to match if/end, for/end,... blocks)
"3) Correct indentation
"4) Integration of mlint (Matlab code checker) with the :make command
"5)Tag support
"6) Help file
Plugin 'vim-scripts/MatlabFilesEdition'
"""""""""""
"  LaTeX  "
"""""""""""
"FEATURES
"   Document compilation with latexmk
"   Compilation of selected part of document
"   Support for several PDF viewers with forward search
"      MuPDF
"      Zathura
"      Okular
"      qpdfview
"      SumatraPDF
"      Other viewers are supported through a general interface
"   Completion of citations, labels, and file names for figures
"   Document navigation through
"      table of content
"      table of labels
"   Word count (through texcount)
"   Motions
"      Move between sections with [[, [], ][, ]]
"      Move between matching delimiters with %
"   Text objects
"      ic ac Commands
"      id ad Delimiters
"      ie ae LaTeX environments
"      i$ a$ Inline math structures
"   Other mappings
"      Delete the surrounding command or environment with dsc/dse/ds$
"      Change the surrounding command or environment with csc/cse/cs$
"      Toggle starred environment with tse
"      Toggle between e.g. () and \left(\right) with tsd
"      Close the current environment/delimiter in insert mode with ]]
"      Insert new command with <F7>
"      Convenient insert mode mappings for faster typing of e.g. maths
"   Improved folding (:h 'foldexpr')
"   Improved indenta2ion (:h 'indentexpr')
"   Improved syntax highlighting
"      Highlight matching delimiters
"      Support for biblatex/natbib package
"      Support for cleveref package
"      Support for listings package
"      Support for minted package
"      Support for dot2tex with nested syntax highlighting
"   Support for multi-file project packages
"      import
"      subfiles
Plugin 'lervag/vimtex'
""""""""""
"  VHDL  "
""""""""""
"Plugin 'suoto/vim-hdl'
""""""""""
"  ToDo  "
""""""""""
""""""""""""""
"  主题风格  "
""""""""""""""
"素雅 solarized（https://github.com/altercation/vim-colors-solarized ）
Plugin 'altercation/vim-colors-solarized'
"多彩 molokai（https://github.com/tomasr/molokai ）
Plugin 'tomasr/molokai'
"复古 phd（http://www.vim.org/scripts/script.php?script_id=3139 ）
Plugin 'vim-scripts/phd'
"C++语法高亮
Plugin 'octol/vim-cpp-enhanced-highlight'
"接口与实现快速切换
Plugin 'derekwyatt/vim-fswitch'
"书签可视化(按mm收藏代码行)
Plugin 'kshenoy/vim-signature'
"Plugin 'vim-scripts/BOOKMARKS—Mark-and-Highlight-Full-Lines'
Plugin 'vim-scripts/indexer.tar.gz'
Plugin 'vim-scripts/DfrankUtil'
Plugin 'vim-scripts/vimprj'
Plugin 'dyng/ctrlsf.vim'
Plugin 'terryma/vim-multiple-cursors'
Plugin 'scrooloose/nerdcommenter'
Plugin 'derekwyatt/vim-protodef'
Plugin 'fholgado/minibufexpl.vim'
Plugin 'gcmt/wildfire.vim'
Plugin 'Lokaltog/vim-easymotion'
Plugin 'lilydjwg/fcitx.vim'
Plugin 'othree/xml.vim'

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" 你的所有插件需要在下面这行之前
call vundle#end()            " 必须
filetype plugin indent on    " 必须 加载vim自带和插件相应的语法和文件类型相关脚本
"
" 简要帮助文档
" :PluginList       - 列出所有已配置的插件
" :PluginInstall    - 安装插件,追加 `!` 用以更新或使用 :PluginUpdate
" :PluginSearch foo - 搜索 foo ; 追加 `!` 清除本地缓存
" :PluginClean      - 清除未使用插件,需要确认; 追加 `!` 自动批准移除未使用插件
"
" 查阅 :h vundle 获取更多细节和wiki以及FAQ
" 将你自己对非插件片段放在这行之后

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                            YouCompleteMe 自动补全配置                       "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

let g:ycm_global_ycm_extra_conf='~/.vim/bundle/YouCompleteMe/third_party/ycmd/cpp/ycm/.ycm_extra_conf.py'
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"让Vim的补全菜单行为与一般IDE一致(参考VimTip1228)
set completeopt=longest,menu	
"离开插入模式后自动关闭预览窗口
autocmd InsertLeave * if pumvisible() == 0|pclose|endif	
"回车即选中当前项
inoremap <expr> <CR>       pumvisible() ? "\<C-y>" : "\<CR>"
"上下左右键的行为 会显示其他信息
inoremap <expr> <Down>     pumvisible() ? "\<C-n>" : "\<Down>"
inoremap <expr> <Up>       pumvisible() ? "\<C-p>" : "\<Up>"
inoremap <expr> <PageDown> pumvisible() ? "\<PageDown>\<C-p>\<C-n>" : "\<PageDown>"
inoremap <expr> <PageUp>   pumvisible() ? "\<PageUp>\<C-p>\<C-n>" : "\<PageUp>"
"youcompleteme  默认tab  s-tab 和自动补全冲突
"let g:ycm_key_list_select_completion=['<c-n>']
let g:ycm_key_list_select_completion = ['<Down>']
"let g:ycm_key_list_previous_completion=['<c-p>']
let g:ycm_key_list_previous_completion = ['<Up>']
let g:ycm_confirm_extra_conf=0 "关闭加载.ycm_extra_conf.py提示
let g:ycm_collect_identifiers_from_tags_files=1	" 开启 YCM 基于标签引擎
let g:ycm_min_num_of_chars_for_completion=1 " 从第1个键入字符就开始罗列匹配项
let g:ycm_cache_omnifunc=0	" 禁止缓存匹配项,每次都重新生成匹配项
let g:ycm_seed_identifiers_with_syntax=1	" 语法关键字补全
"force recomile with syntastic
nnoremap yfcd :YcmForceCompileAndDiagnostics<CR>
"nnoremap <leader>lo :lopen<CR>	"open locationlist
"nnoremap <leader>lc :lclose<CR>	"close locationlist
inoremap <leader><leader> <C-x><C-o>
"在注释输入中也能补全
let g:ycm_complete_in_comments = 1
"在字符串输入中也能补全
let g:ycm_complete_in_strings = 1
"注释和字符串中的文字也会被收入补全
let g:ycm_collect_identifiers_from_comments_and_strings = 0
"跳转到定义处
nnoremap <leader>gd :YcmCompleter GoToDefinitionElseDeclaration<CR>
"设置error和warning的提示符
let g:ycm_error_symbol = '>>'
let g:ycm_warning_symbol = '>*'

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                                 syntastic配置                               "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

let g:syntastic_error_symbol = ">!"
let g:syntastic_warning_symbol = ">>"

let g:syntastic_check_on_open=1 " 载入时检查错误
let g:syntastic_check_on_wq=1 " 保存时检查错误
let g:syntastic_enable_highlighting=1
let g:syntastic_cpp_include_dirs = ['/usr/include/']
let g:syntastic_cpp_remove_include_errors = 1
let g:syntastic_cpp_check_header = 1
let g:syntastic_cpp_compiler = 'clang++'
let g:syntastic_cpp_compiler_options = '-std=c++11 -stdlib=libstdc++'
let g:syntastic_python_checkers=['pyflakes'] " 使用pyflakes,速度比pylint快
let g:syntastic_javascript_checkers = ['jsl', 'jshint']
let g:syntastic_html_checkers=['tidy', 'jshint']
" 修改高亮的背景色, 适应主题
highlight SyntasticErrorSign guifg=white guibg=black

" to see error location list
let g:syntastic_always_populate_loc_list = 1 " 自动载入错误到 the location list
let g:syntastic_auto_loc_list = 0
let g:syntastic_loc_list_height = 5
function! ToggleErrors()
    let old_last_winnr = winnr('$')
    lclose
    if old_last_winnr == winnr('$')
        " Nothing was closed, open syntastic error location panel
        Errors
    endif
endfunction
nnoremap <leader>s :call ToggleErrors()<cr>
" nnoremap <leader>sn :lnext<cr>
" nnoremap <leader>sp :lprevious<cr>

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                                 lookupfile 配置                             "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

let g:LookupFile_MinPatLength = 2               "最少输入2个字符才开始查找
let g:LookupFile_PreserveLastPattern = 0        "不保存上次查找的字符串
let g:LookupFile_PreservePatternHistory = 1     "保存查找历史
let g:LookupFile_AlwaysAcceptFirst = 1          "回车打开第一个匹配项目
let g:LookupFile_AllowNewFiles = 0              "不允许创建不存在的文件
if filereadable("./filenametags")                "设置tag文件的名字
let g:LookupFile_TagExpr = '"./filenametags"'
endif

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                                 nerdtree配置                               "
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" 显示行号
let NERDTreeShowLineNumbers=1
" 是否显示隐藏文件
let NERDTreeShowHidden=0
" 设置宽度
let NERDTreeWinSize=30
" 在终端启动vim时，共享NERDTree
let g:nerdtree_tabs_open_on_console_startup=1
" 忽略一下文件的显示
let NERDTreeIgnore=['\.pyc','\~$','\.swp']
" 显示书签列表
let NERDTreeShowBookmarks=1

let g:NERDTreeIndicatorMapCustom = {
    \ "Modified"  : "✹",
    \ "Staged"    : "✚",
    \ "Untracked" : "✭",
    \ "Renamed"   : "➜",
    \ "Unmerged"  : "═",
    \ "Deleted"   : "✖",
    \ "Dirty"     : "✗",
    \ "Clean"     : "✔︎",
    \ "Unknown"   : "?"
    \ }

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                                  taglist配置                                "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

let Tlist_Ctags_Cmd='ctags'
let Tlist_Show_One_File=1           	"不同时显示多个文件的tag，只显示当前文件的
let Tlist_WinWidt =32					"设置taglist的宽度
let Tlist_Exit_OnlyWindow=1         	"如果taglist窗口是最后一个窗口，则退出vim
"let Tlist_Use_Right_Window=1			"在右侧窗口中显示taglist窗口
let Tlist_Use_Left_Windo =1        		"在左侧窗口中显示taglist窗口

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                                  tagbar配置                                 "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

"nmap <Leader>tb :TagbarToggle<CR>		"快捷键设置
let g:tagbar_ctags_bin='ctags'			"ctags程序的路径
let g:tagbar_width=24				"窗口宽度的设置
"设置tagbar的窗口显示的位置,为左边 
let g:tagbar_left=1
map <F3> :Tagbar<CR>
autocmd BufReadPost *.cpp,*.c,*.h,*.hpp,*.cc,*.cxx,*.* call tagbar#autoopen() 	"如果是c语言的程序的话，tagbar自动开启

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                                 NERDTree配置                                "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

"F2开启和关闭树
map <F2> :NERDTreeToggle<CR>
let NERDTreeChDirMode=1
let NERDChristmasTree=1
"显示书签
let NERDTreeShowBookmarks=1
"设置忽略文件类型
let NERDTreeIgnore=['\~$', '\.pyc$', '\.swp$']
"窗口大小
let NERDTreeWinSize=32
"窗口位置
let NERDTreeWinPos="right"
"确定是否改变Vim的CWD
let NERDTreeChDirMode=1

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                                  cscope配置                                 "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

nmap <C-_>s :cs find s <C-R>=expand("<cword>")<CR><CR>
nmap <C-_>g :cs find g <C-R>=expand("<cword>")<CR><CR>
nmap <C-_>c :cs find c <C-R>=expand("<cword>")<CR><CR>
nmap <C-_>t :cs find t <C-R>=expand("<cword>")<CR><CR>
nmap <C-_>e :cs find e <C-R>=expand("<cword>")<CR><CR>
nmap <C-_>f :cs find f <C-R>=expand("<cfile>")<CR><CR>
nmap <C-_>i :cs find i <C-R>=expand("<cfile>")<CR><CR>
nmap <C-_>d :cs find d <C-R>=expand("<cword>")<CR><CR>

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                                 autopep8配置                                "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

if &filetype == 'py'
    let g:autopep8_disable_show_diff=1
endif

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                                   Gundo配置                                 "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

map <leader>g :GundoToggle<CR>

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                                 vim-fswitch                                 "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" *.cpp 和 *.h 间切换
nmap <silent> <Leader>sw :FSHere<cr>

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                                    C和C++                                   "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                                   Python                                    "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

"Vim doesn't realize that you are in a virtualenv so it wont give you code completion for libraries only installed there. Add the following script to your ~/.vimrc to fix it:
" Add the virtualenv's site-packages to vim path
py << EOF
import os.path
import sys
import vim
if 'VIRTUAL_ENV' in os.environ:
    project_base_dir = os.environ['VIRTUAL_ENV']
    sys.path.insert(0, project_base_dir)
    activate_this = os.path.join(project_base_dir, 'bin/activate_this.py')
    execfile(activate_this, dict(__file__=activate_this))
EOF

"支持PEP8风格的缩进
"au BufNewFile,BufRead *.py
set tabstop=4
set softtabstop=4
set shiftwidth=4
set textwidth=79
set expandtab
set autoindent

"高亮
let python_highlight_all=1

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"                                    shell                                    "
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

