---
layout: post 
title: 建立VIM的IDE环境
---

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
""                                       Config of vim
""                                       Add by jfgong from 2013/08/04
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" display line number in VIM
set number

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
""                                       Config of plugins for vim
""                                       Add by jfgong from 2012/12/12
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

"""""""""""""""""""""""""""""""""""""
" taglist.vim,默认显示在左侧
"""""""""""""""""""""""""""""""""""""
" 自动开启taglist
let Tlist_Auto_Open =1
" 只剩下taglist窗口时自动退出
let Tlist_Exit_OnlyWindow =1
" 是否显示在窗口右侧
let Tlist_Use_Right\_Window =0

"""""""""""""""""""""""""""""""""""""
" mark.vim,字符标记
"""""""""""""""""""""""""""""""""""""
" \m标记光标处的字符串
" \n取消光标处字符串的标记
" 可以添加自己喜欢的颜色
hi MarkWord1	ctermbg=Cyan	ctermfg=Black	guibg=#8CCBEA	guifg=Black
hi MarkWord2	ctermbg=Green	ctermfg=Black	guibg=#A4E57E	guifg=Black
hi MarkWord3	ctermbg=Yellow	ctermfg=Black	guibg=#FFDB72	guifg=Black
hi MarkWord4	ctermbg=Red	ctermfg=Black	guibg=#FF7272	guifg=Black
hi MarkWord5	ctermbg=Magenta	ctermfg=Black	guibg=#FFB3FF	guifg=Black
hi MarkWord6	ctermbg=Blue	ctermfg=Black	guibg=#9999FF	guifg=Black

"""""""""""""""""""""""""""""""""""""
" autopreview.vim,默认显示在窗口顶端
"""""""""""""""""""""""""""""""""""""
" 自动打开preview窗口
let g:AutoPreview\_enabled =1 
" 使用F5开启关闭preview窗口，你也可以设置成其他的热键
nnoremap <F5> :AutoPreviewToggle<CR> 
inoremap <F5> <ESC>:AutoPreviewToggle<CR>i 
" 每500毫秒刷新一次preview窗口，建议设置在500-1000之间
set updatetime=500

"""""""""""""""""""""""""""""""""""""
" OmniCppComplete.vim,自动补全
"""""""""""""""""""""""""""""""""""""
set nocp
filetype plugin on
" :help omnicppcomplete
" set completeopt=longest,menu		" I really HATE the preview window!!!
" let OmniCpp\_NameSpaceSearch=1		" 0: namespaces disabled
"					" 1: search namespaces in the current buffer [default]
"					" 2: search namespaces in the current  buffer and in included files
" let OmniCpp_GlobalScopeSearch=1	" 0: disabled 1:enabled
" let OmniCpp_ShowAccess=1		" 1: show access
" let OmniCpp_ShowPrototypeInAbbr=1	" 1: display prototype in abbreviation
" let OmniCpp_MayCompleteArrow=1	" autocomplete after ->
" let OmniCpp_MayCompleteDot=1		" autocomplete after .
" let OmniCpp_MayCompleteScope=1	" autocomplete after ::
" let OmniCpp_DefaultNamespaces=["std","GLIBCXX_STD"]
" 
" autocmd FileType python set omnifunc=pythoncomplete#Complete
" autocmd FileType javascript set omnifunc=javascriptcomplete#CompleteJS
" autocmd FileType html set omnifunc=htmlcomplete#CompleteTags
" autocmd FileType css set omnifunc=csscomplete#CompleteCSS
" autocmd FileType xml set omnifunc=xmlcomplete#CompleteTags
" autocmd FileType php set omnifunc=phpcomplete#CompletePHP
" autocmd FileType c set omnifunc=ccomplete#Complete
"
"""""""""""""""""""""""""""""""""""""
" Cscope，需要用户自己安装
"""""""""""""""""""""""""""""""""""""
" 加载符号索引文件cscope.out
cs add cscope.out
"set cscopequickfix=s+,c+,d+,i+,t+,e+
cwindow
nmap <C-_>s :cs find s <C-R>=expand("<cword>")<CR><CR>
nmap <C-_>g :cs find g <C-R>=expand("<cword>")<CR><CR>
nmap <C-_>c :cs find c <C-R>=expand("<cword>")<CR><CR>
nmap <C-_>t :cs find t <C-R>=expand("<cword>")<CR><CR>
nmap <C-_>e :cs find e <C-R>=expand("<cword>")<CR><CR>
nmap <C-_>f :cs find f <C-R>=expand("<cfile>")<CR><CR>
nmap <C-_>i :cs find i ^<C-R>=expand("<cfile>")<CR>$<CR>
nmap <C-_>d :cs find d <C-R>=expand("<cword>")<CR><CR>

"""""""""""""""""""""""""""""""""""""
" quickfix,高版本vim自带，无需安装
"""""""""""""""""""""""""""""""""""""
" 打开quickfix窗口
" set cscope output in quickfix windows
"cwindow
nmap <C-n> :cnext<CR>
nmap <C-p> :cprev<CR>

Posted by randombug @ {{ page.date | date_to_string }}
