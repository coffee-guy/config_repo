set langmenu=en_US.UTF-8
language messages en_US.UTF-8
let mapleader=" "
" disable arrow
" noremap <Up> <Nop>
" noremap <Down> <Nop>
" noremap <Left> <Nop>
" noremap <Right> <Nop>

set nocompatible
filetype on
filetype indent on
filetype plugin on
filetype plugin indent on
" set mouse=a
set encoding=utf-8
let &t_ut=''
set expandtab
set tabstop=4
set shiftwidth=4
set softtabstop=4
" set list
" set listchars=tab:▸\ ,trail:▫
set scrolloff=5
set tw=0
set indentexpr=
set backspace=indent,eol,start
set foldmethod=indent
set foldlevel=99
let &t_SI = "\<Esc>]50;CursorShape=1\x7"
let &t_SR = "\<Esc>]50;CursorShape=2\x7"
let &t_EI = "\<Esc>]50;CursorShape=0\x7"
set laststatus=2
set autochdir
au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g'\"" | endif

" make vim faster
" set noswapfile
" set lazyredraw
" set viminfo="NONE"

noremap n nzz
noremap N Nzz
noremap <LEADER><CR> :nohlsearch<CR>

inoremap jj <Esc>

syntax on
set number
set relativenumber
set cursorline
set wrap
set showcmd
set wildmenu

set hlsearch
exec "nohlsearch"
set incsearch
set ignorecase
set smartcase

noremap K 5k
noremap J 5j
noremap H 7h
noremap L 7l

map s <nop>
map S :w<CR>
map Q :q<CR>
map R :source $MYVIMRC<CR>

" ===
" === split window
" ===
map sl :set splitright<CR>:vsplit<CR>
map sh :set nosplitright<CR>:vsplit<CR>
map sj :set nosplitbelow<CR>:split<CR>
map sk :set splitbelow<CR>:split<CR>


" 切换window
map <LEADER>l <C-w>l
map <LEADER>k <C-w>k
map <LEADER>h <C-w>h
map <LEADER>j <C-w>j

" 调整window大小
map <up> :res +5<CR>
map <down> :res -5<CR>
map <left> :vertical resize+5<CR>
map <right> :vertical resize-5<CR>

" tab 操作
map tu :tabe<CR>
map ta :-tabnext<CR>
map tl :+tabnext<CR>

" 水平展开，垂直展开window
map sh <C-w>t<C-w>H
map sv <C-w>t<C-w>K

" python run
autocmd FileType python map <buffer> <C-e> :w<CR>:exec '!python3' shellescape(@%, 1)<CR>
autocmd FileType python imap <buffer> <C-e> <esc>:w<CR>:exec '!python3' shellescape(@%, 1)<CR>

" mine cpp config
" for tagbar
" =========================================
" ctag
" let g:Tlist_Ctags_Cmd='/opt/homebrew/Cellar/ctags/5.8_2/bin'



" Some servers have issues with backup files, see #649
set nobackup
set nowritebackup

" Having longer updatetime (default is 4000 ms = 4s) leads to noticeable
" delays and poor user experience
set updatetime=5000

" diagnostics appear/become resolved
set signcolumn=yes
"
" if executable('pylsp')
"     " pip install python-lsp-server
"     au User lsp_setup call lsp#register_server({
"         \ 'name': 'pylsp',
"         \ 'cmd': {server_info->['pylsp']},
"         \ 'allowlist': ['python'],
"         \ 'workspace_config': {
"         \   'pylsp.plugins.pycodestyle.enabled':v:true,
"         \   'pylsp.plugins.pycodestyle.maxLineLength':88,
"         \   'pylsp.plugins.mccabe.enabled':v:false,
"         \   'pylsp.plugins.pyflakes.enabled':v:false,
"         \   'pylsp.plugins.flake8.enabled':v:true,
"         \   'pylsp.configurationSources':['flake8']
"         \   }
"         \ })
" endif
" 用来在注册的lsp server上注册map
"==================================================
function! s:on_lsp_buffer_enabled() abort
    setlocal omnifunc=lsp#complete
    setlocal signcolumn=yes
    if exists('+tagfunc') | setlocal tagfunc=lsp#tagfunc | endif
    nmap <buffer> gd <plug>(lsp-definition)
    nmap <buffer> gs <plug>(lsp-document-symbol-search)
    nmap <buffer> gS <plug>(lsp-workspace-symbol-search)
    nmap <buffer> gr <plug>(lsp-references)
    nmap <buffer> gi <plug>(lsp-implementation)
    nmap <buffer> gt <plug>(lsp-type-definition)
    nmap <buffer> <leader>rn <plug>(lsp-rename)
    nmap <buffer> [g <plug>(lsp-previous-diagnostic)
    nmap <buffer> ]g <plug>(lsp-next-diagnostic)
    nmap <buffer> U <plug>(lsp-hover)
    " nnoremap <buffer> <expr><c-f> lsp#scroll(+4)
    " nnoremap <buffer> <expr><c-d> lsp#scroll(-4)

    let g:lsp_format_sync_timeout = 1000
    autocmd! bufWritePre *.rs,*.go call execute('LspDocumentFormatSync')

    " refer to doc to add more commands
endfunction

augroup lsp_install
    au!
    " call s:on_lsp_buffer_enabled only for languages that has the server registered.
    autocmd user lsp_buffer_enabled call s:on_lsp_buffer_enabled()
augroup end
"==================================================
" 禁止自动diagnose
let g:lsp_diagnostics_enabled = 0

" pylsp setting
" let g:lsp_settings = {
" \   'pylsp-all': {
" \     'initialization_options': {
" \       'pylsp.configurationSources': ['flake8'],
" \       'pylsp.plugins.pycodestyle.enabled': v:false,
" \       'pylsp.plugins.mccabe.enabled': v:false,
" \       'pylsp.plugins.pyflakes.enabled': v:false,
" \       'pylsp.plugins.flake8.enabled': v:true
" \     }
" \   }
" \}

inoremap <expr> <cr>    pumvisible() ? asyncomplete#close_popup() : "\<cr>"
" imap <c-space> <Plug>(asyncomplete_force_refresh)
" For Vim 8 (<c-@> corresponds to <c-space>):
" " imap <c-@> <Plug>(asyncomplete_force_refresh)Su
" By default asyncomplete will automatically show the autocomplete popup menu
" as you start typing. If you would like to disable the default behavior set
let g:asyncomplete_auto_popup = 0
function! s:check_back_space() abort
    let col = col('.') - 1
    return !col || getline('.')[col - 1]  =~ '\s'
endfunction

" 默认不显示pop，tab呼出
inoremap <silent><expr> <TAB>
            \ pumvisible() ? "\<C-n>" :
            \ <SID>check_back_space() ? "\<TAB>" :
            \ asyncomplete#force_refresh()
inoremap <expr><S-TAB> pumvisible() ? "\<C-p>" : "\<C-h>"

" let lsp take the foldmethod
set foldmethod=expr
            \ foldexpr=lsp#ui#vim#folding#foldexpr()
            \ foldtext=lsp#ui#vim#folding#foldtext()

" " black on save for python
augroup black_on_save
    autocmd!
    autocmd BufWritePre *.py Black
augroup end

" wildfire
nmap <leader>s <Plug>(wildfire-quick-select)

" nerdcommenter
" Add spaces after comment delimiters by default
let g:NERDSpaceDelims = 1

" Use compact syntax for prettified multi-line comments
let g:NERDCompactSexyComs = 1

" Align line-wise comment delimiters flush left instead of following code indentation
let g:NERDDefaultAlign = 'left'

" Set a language to use its alternate delimiters by default
let g:NERDAltDelims_python = 1

" Add your own custom formats or override the defaults
let g:NERDCustomDelimiters = { 'c': { 'left': '/**','right': '*/' } }

" Allow commenting and inverting empty lines (useful when commenting a region)
let g:NERDCommentEmptyLines = 1

" Enable trimming of trailing whitespace when uncommenting
let g:NERDTrimTrailingWhitespace = 1

" Enable NERDCommenterToggle to check all selected lines is commented or not 
let g:NERDToggleCheckAllLines = 1

call plug#begin()

" default plugin directory will be as follows:
"   - Vim (Linux/macOS): '~/.vim/plugged'
"   - Vim (Windows): '~/vimfiles/plugged'
"   - Neovim (Linux/macOS/Windows): stdpath('data') . '/plugged'
" You can specify a custom plugin directory by passing it as the argument
"   - e.g. `call plug#begin('~/.vim/plugged')`
"   - Avoid using standard Vim directory names like 'plugin'

" Make sure you use single quotes
Plug 'vim-airline/vim-airline-themes'
Plug 'connorholyday/vim-snazzy'

" Python
Plug 'vim-scripts/indentpython.vim'
Plug 'psf/black'



" File navigation
Plug 'scrooloose/nerdtree', { 'on': 'NERDTreeToggle' }
Plug 'Xuyuanp/nerdtree-git-plugin'
Plug 'francoiscabrol/ranger.vim'
    

" lsp
Plug 'prabirshrestha/vim-lsp'
Plug 'mattn/vim-lsp-settings'


" auto complete
Plug 'prabirshrestha/asyncomplete.vim'
Plug 'prabirshrestha/asyncomplete-lsp.vim'

" Taglist
Plug 'majutsushi/tagbar'

" Undo Tree
Plug 'mbbill/undotree/'

" Other visual enhancement
Plug 'nathanaelkane/vim-indent-guides'
Plug 'itchyny/vim-cursorword'

" Git
Plug 'rhysd/conflict-marker.vim'
Plug 'tpope/vim-fugitive'
Plug 'mhinz/vim-signify'
Plug 'gisphm/vim-gitignore', { 'for': ['gitignore', 'vim-plug'] }

" Other useful utilities
" Plug 'mg979/vim-visual-multi', {'branch': 'master'}
Plug 'terryma/vim-multiple-cursors'
Plug 'junegunn/goyo.vim' " distraction free writing mode
Plug 'tpope/vim-surround' " type ysks' to wrap the word with '' or type cs'` to change 'word' to `word`
Plug 'godlygeek/tabular' " type ;Tabularize /= to align the =
Plug 'gcmt/wildfire.vim' " in Visual mode, type i' to select all text in '', or type i) i] i} ip
Plug 'scrooloose/nerdcommenter' " in <space>cc to comment a line

" Shorthand notation; fetches https://github.com/junegunn/vim-easy-align
Plug 'junegunn/vim-easy-align'

if !has('nvim') | Plug 'rhysd/vim-healthcheck' | endif

" Any valid git URL is allowed
" Plug 'https://github.com/junegunn/vim-github-dashboard.git'

" Multiple Plug commands can be written in a single line using | separators
" Plug 'SirVer/ultisnips' | Plug 'honza/vim-snippets'

" On-demand loading
" Plug 'tpope/vim-fireplace', { 'for': 'clojure' }

" Using a non-default branch
" Plug 'rdnetto/YCM-Generator', { 'branch': 'stable' }

" Using a tagged release; wildcard allowed (requires git 1.9.2 or above)
" Plug 'fatih/vim-go', { 'tag': '*' }

" Plugin options
" Plug 'nsf/gocode', { 'tag': 'v.20150303', 'rtp': 'vim' }

" Plugin outside ~/.vim/plugged with post-update hook
" Plug 'junegunn/fzf', { 'dir': '~/.fzf', 'do': './install --all' }

" Unmanaged plugin (manually installed and updated)
" Plug '~/my-prototype-plugin'

" Plug 'neoclide/coc.nvim', {'branch': 'release'}


" Initialize plugin system
" - Automatically executes `filetype plugin indent on` and `syntax enable`.
call plug#end()
" json format
" .vimrc

" 创建JSON Format 函数
function! JsonFormat()
    " 将输出保存到寄存器 a 中
    let @a = system("python -m json.tool " . bufname("%")) 
    " 如果执行失败，则只打印错误信息
    if v:shell_error
        echom @a
    else
        " 执行成功，则写入缓冲区
        %delete
        normal! "ap
        1delete
        write
    endif
endfunction

" 创建 Jf 命令
command! Jf call JsonFormat()

autocmd BufWritePost *.json call JsonFormat()

" let g:ale_fix_on_save = 1
" let g:ale_linters = {
"             \'python': ['black','mypy','flake8','pylint','pylsp'],
"             \'shell': ['shellcheck'],
"             \ }
" let g:ale_fixers = {
"             \    '*': ['remove_trailing_lines', 'trim_whitespace'],
"             \    'javascript': ['eslint', 'prettier']
"             \}
" let g:ale_python_flake8_options = '--config=$HOME/.config/flake8'
" let g:ale_virtualenv_dir_names = []


" let g:lsp_log_verbose = 1
" let g:lsp_log_file = expand('~/vim-lsp.log')
" You can revert the settings after the call like so:
"   filetype indent off   " Disable file-type-specific indentation
"   syntax off            " Disable syntax highlighting

" let g:airline_theme='luna'
let g:SnazzyTransparent = 1
color snazzy


" ===
" === NERDTree
" ===
map ff :NERDTreeToggle<CR>
let NERDTreeMapOpenExpl = ""
let NERDTreeMapUpdir = ""
let NERDTreeMapUpdirKeepOpen = "l"
let NERDTreeMapOpenSplit = ""
let NERDTreeOpenVSplit = ""
let NERDTreeMapActivateNode = "i"
let NERDTreeMapOpenInTab = "o"
let NERDTreeMapPreview = ""
let NERDTreeMapCloseDir = "n"
let NERDTreeMapChangeRoot = "y"

" Exit Vim if NERDTree is the only window remaining in the only tab.
autocmd BufEnter * if tabpagenr('$') == 1 && winnr('$') == 1 && exists('b:NERDTree') && b:NERDTree.isTabTree() | quit | endif

" ==
" == NERDTree-git
" ==
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

" ===
" === Taglist
" ===
" nnoremap <silent> T :TagbarToggle<CR>
nnoremap <silent> T :TagbarOpenAutoClose<CR>

" ===
" === Python-syntax
" ===
let g:python_highlight_all = 1
" let g:python_slow_sync = 0


" ===
" === vim-indent-guide
" ===
let g:indent_guides_guide_size = 1
let g:indent_guides_start_level = 2
let g:indent_guides_enable_on_vim_startup = 1
let g:indent_guides_color_change_percent = 1
silent! unmap <LEADER>ig
autocmd WinEnter * silent! unmap <LEADER>ig


" ===
" === Goyo
" ===
map <LEADER>gy :Goyo<CR>

" ===
" === vim-signiture
" ===
let g:SignatureMap = {
            \ 'Leader'             :  "m",
            \ 'PlaceNextMark'      :  "m,",
            \ 'ToggleMarkAtLine'   :  "m.",
            \ 'PurgeMarksAtLine'   :  "dm-",
            \ 'DeleteMark'         :  "dm",
            \ 'PurgeMarks'         :  "dm/",
            \ 'PurgeMarkers'       :  "dm?",
            \ 'GotoNextLineAlpha'  :  "m<LEADER>",
            \ 'GotoPrevLineAlpha'  :  "",
            \ 'GotoNextSpotAlpha'  :  "m<LEADER>",
            \ 'GotoPrevSpotAlpha'  :  "",
            \ 'GotoNextLineByPos'  :  "",
            \ 'GotoPrevLineByPos'  :  "",
            \ 'GotoNextSpotByPos'  :  "mn",
            \ 'GotoPrevSpotByPos'  :  "mp",
            \ 'GotoNextMarker'     :  "",
            \ 'GotoPrevMarker'     :  "",
            \ 'GotoNextMarkerAny'  :  "",
            \ 'GotoPrevMarkerAny'  :  "",
            \ 'ListLocalMarks'     :  "m/",
            \ 'ListLocalMarkers'   :  "m?"
            \ }


" ===
" === Undotree
" ===
let g:undotree_DiffAutoOpen = 0
map M :UndotreeToggle<CR>
