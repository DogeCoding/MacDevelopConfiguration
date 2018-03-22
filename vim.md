"set nu! " 显示行号

"去掉vi的一致性"
set nocompatible
"显示行号"
set number
" 隐藏滚动条"    
set guioptions-=r 
set guioptions-=L
set guioptions-=b
"隐藏顶部标签栏"
set showtabline=0
set hidden " 允许在有未保存的修改时切换缓冲区，此时的修改由 vim 负责保存
set guioptions-=T " 隐藏工具栏
set guioptions-=m " 隐藏菜单栏
"设置字体"
set guifont=Monaco:h13         
syntax on    "开启语法高亮"
set background=dark        "设置背景色"
set nowrap    "设置不折行"
set fileformat=unix    "设置以unix的格式保存文件"
set cindent        "设置C样式的缩进格式"
set ts=4 " 设置tab键为四个空格
set tabstop=4    "设置table长度"
set shiftwidth=4        "同上"
set autochdir " 自动切换当前目录为当前文件所在的目录
set scrolloff=5        "距离顶部和底部5行"
set laststatus=2    "命令行为两行"
set fenc=utf-8      "文件编码"
set backspace=2
set mouse=a        "启用鼠标"
set selection=exclusive
set selectmode=mouse,key
set matchtime=5
set ignorecase        "忽略大小写"
set incsearch
set hlsearch        "高亮搜索项"
set noexpandtab        "不允许扩展table"
set whichwrap+=<,>,h,l
set autoread
"set cursorline        "突出显示当前行"
"set cursorcolumn        "突出显示当前列"


nmap <C-j> <C-f>

" Vundle
func! SaveFile()
    exec "w"
endfunc
map  <d-s> :call SaveFile()<CR>
imap <d-s> <ESC>:call SaveFile()<CR>
vmap <d-s> <ESC>:call SaveFile()<CR>

set nocompatible              
filetype off                 
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()


Plugin 'VundleVim/Vundle.vim'

" Plugins
Plugin 'Valloric/YouCompleteMe'

" 自动补全配置
set completeopt=longest,menu	"让Vim的补全菜单行为与一般IDE一致(参考VimTip1228)
autocmd InsertLeave * if pumvisible() == 0|pclose|endif	"离开插入模式后自动关闭预览窗口
inoremap <expr> <CR>       pumvisible() ? "\<C-y>" : "\<CR>"	"回车即选中当前项
"上下左右键的行为 会显示其他信息
inoremap <expr> <Down>     pumvisible() ? "\<C-n>" : "\<Down>"
inoremap <expr> <Up>       pumvisible() ? "\<C-p>" : "\<Up>"
inoremap <expr> <PageDown> pumvisible() ? "\<PageDown>\<C-p>\<C-n>" : "\<PageDown>"
inoremap <expr> <PageUp>   pumvisible() ? "\<PageUp>\<C-p>\<C-n>" : "\<PageUp>"

"youcompleteme  默认tab  s-tab 和自动补全冲突

let g:ycm_confirm_extra_conf=0 "关闭加载.ycm_extra_conf.py提示

let g:ycm_collect_identifiers_from_tags_files=1	" 开启 YCM 基于标签引擎
let g:ycm_min_num_of_chars_for_completion=2	" 从第2个键入字符就开始罗列匹配项
let g:ycm_cache_omnifunc=0	" 禁止缓存匹配项,每次都重新生成匹配项
let g:ycm_seed_identifiers_with_syntax=1	" 语法关键字补全
nnoremap <F5> :YcmForceCompileAndDiagnostics<CR>	"force recomile with syntastic
"nnoremap <leader>lo :lopen<CR>	"open locationlist
"nnoremap <leader>lc :lclose<CR>	"close locationlist
inoremap <leader><leader> <C-x><C-o>
"在注释输入中也能补全
let g:ycm_complete_in_comments = 1
"在字符串输入中也能补全
let g:ycm_complete_in_strings = 1
"注释和字符串中的文字也会被收入补全
let g:ycm_collect_identifiers_from_comments_and_strings = 0

nnoremap <leader>jd :YcmCompleter GoToDefinitionElseDeclaration<CR> " 跳转到定义处


Plugin 'The-NERD-tree'

" 标签导航
Plugin 'majutsushi/tagbar'

" 多文档编辑
" Plugin 'fholgado/minibufexpl'

" 美化状态栏
Plugin 'Lokaltog/vim-powerline'

" 括号匹配高亮
Plugin 'kien/rainbow_parentheses.vim'

" 可视化缩进
Plugin 'nathanaelkane/vim-indent-guides'

" 标志无效空格
Plugin 'bronson/vim-trailing-whitespace'

" 快速移动
Plugin 'easymotion/vim-easymotion'

" 括号匹配跳转
Plugin 'vim-scripts/matchit.zip'

" 宏定义补全
Plugin 'SirVer/ultisnips'
let g:UltiSnipsExpandTrigger = "<tab>"
let g:UltiSnipsJumpForwardTrigger = "<tab>"
let g:UltiSnipsJumpBackwardTrigger="<s-tab>"
"定义存放代码片段的文件夹 .vim/snippets下，使用自定义和默认的，将会的到全局，有冲突的会提示
"let g:UltiSnipsSnippetDirectories=["snippets", "bundle/ultisnips/UltiSnips"]


" Color schemes
Plugin 'tomasr/molokai'
let g:molokai_original = 1
Plugin 'altercation/vim-colors-solarized'
let g:solarized_termcolors=256
let g:solarized_termtrans=1
let g:solarized_contrast="normal"
let g:solarized_visibility="normal"

set t_Co=256

call vundle#end()           
filetype plugin indent on    




