---
layout: post
title: "Vundle the Bundler of Vim"
date: 2016-07-27 00:40:34 +0530
comments: true
categories: ["Vim"]
---

I use vim like text editor since after my college. I allways appreciate vim and I really don’t want change to another one.

##How I manage my plugin around the time

Vim is really powerfull with this plugins. You need really quick use it. It’s really important to manage it. All around the time, I change how I manage it with new technique inside vim or develop by other developper.

##Handmade management

In start of my vim usage, I manage my plugin by copying file in different directory. I put in versionning my .vimrc and .vim. But this technique can be hard to maintain in time. The installation is not really simple and know if you need update or not is hard too. So the evolution of plugins become rare.

##Vimball management

In vim evolution, the vimball management system was implemented. With this vimball, you can more easily install plugin and know which version you use. So you can improve your plugins management. But to know if a new version is available, you need go to vimscript.org and check each of your plugins. The update become rare too.

##Git-submodule management

With github, all plugins become a git repository. We can check all new commit on our favorite plugin. I start to link all plugin in a new submodule and link file in good directory. The update was really simple and my plugins can be up to date. But the installation become really hard.

##Janus management

Yehuda Katz and Carl Lerche start a new project call [janus](https://github.com/carlhuda/janus). This project’s goal is an easy plugin management by rake task. In this Rakefile, you can see the list of your plugin and with some rake task you can install it and update it. This project was really great. It start with a bunch of plugins pre-configure and good if you start using vim and you are not aware with what plugin can be good to you. But in time, the management can be a little tricky with version of janus. So it’s a really good project to start vim.

##Pathogen management, the first vim plugin to manage you plugins

To closed of janus’s released, [Tim Pope](https://github.com/tpope) ( a very important vim plugin developper ) release [Pathogen](https://github.com/tpope/vim-pathogen). This plugin help to manage your vim plugin directly in your vimrc file. I don’t really use it. But a lot of people say it’s a really good plugin. There are a lot of fork of janus trying to use pathogen directly.

##Vundle management

Now, someone told me about a very good plugin to manage his vim’s plugin, [Vundle](https://github.com/gmarik/Vundle.vim). As Pathogen, the plugin management is do directly in your vimrc. His usage is really simple and well designed. If you are a ruby guy and use already [Bundler](http://gembundler.org/), you can easily understand how works Vundle and how use it. Vundle is directly inspired of this project.

#Using Vundle

##Install Vundle

To install vundle, you just need clone the project’s repository in your .vim directory and add 2 lignes in your vimrc file

    mkdir ~/.vim/bundle
    git clone https://github.com/gmarik/vundle.git ~/.vim/bundle/vundle

Vundle makes it very easy to manage Vim plugins. You just need to specify a few rows along the lines of Bundle "user/plugin" in your .vimrc and then issue :BundleInstall to start the installation.

You can also run :BundleUpdate and :BundleClean

##New .vimrc

Both NERDTree and Syntastic are quite slow. I could probably manage without them but what would be the fun in that?

    set nocompatible
    filetype off

    set rtp+=~/.vim/bundle/vundle/
    call vundle#rc()

    " Let Vundle manage Vundle
    Bundle 'gmarik/vundle'

    " My Bundles
    Bundle 'tpope/vim-sensible'
    Bundle 'tpope/vim-surround'
    Bundle 'tpope/vim-fugitive'
    Bundle 'tpope/vim-rails'
    Bundle 'tpope/vim-rake'
    Bundle 'nanotech/jellybeans.vim'
    Bundle 'Lokaltog/vim-powerline'
    Bundle 'scrooloose/syntastic'
    Bundle 'scrooloose/nerdtree'
    Bundle 'kien/ctrlp.vim'
    Bundle 'rking/ag.vim'
    Bundle 'kana/vim-textobj-user'
    Bundle 'nelstrom/vim-textobj-rubyblock'
    Bundle 'slim-template/vim-slim'

    filetype plugin indent on

    let mapleader=","

    color jellybeans

    set cursorline
    set expandtab
    set modelines=0
    set shiftwidth=2
    set clipboard=unnamed
    set synmaxcol=128
    set ttyscroll=10
    set encoding=utf-8
    set tabstop=2
    set nowrap
    set number
    set expandtab
    set nowritebackup
    set noswapfile
    set nobackup
    set hlsearch
    set ignorecase
    set smartcase

    " Automatic formatting
    autocmd BufWritePre *.rb :%s/\s\+$//e
    autocmd BufWritePre *.go :%s/\s\+$//e
    autocmd BufWritePre *.haml :%s/\s\+$//e
    autocmd BufWritePre *.html :%s/\s\+$//e
    autocmd BufWritePre *.scss :%s/\s\+$//e
    autocmd BufWritePre *.slim :%s/\s\+$//e

    au BufNewFile * set noeol
    au BufRead,BufNewFile *.go set filetype=go

    " No show command
    autocmd VimEnter * set nosc

    " Quick ESC
    imap jj <ESC>

    " Jump to the next row on long lines
    map <Down> gj
    map <Up>   gk
    nnoremap j gj
    nnoremap k gk

    " format the entire file
    nmap <leader>fef ggVG=

    " Open new buffers
    nmap <leader>s<left>   :leftabove  vnew<cr>
    nmap <leader>s<right>  :rightbelow vnew<cr>
    nmap <leader>s<up>     :leftabove  new<cr>
    nmap <leader>s<down>   :rightbelow new<cr>

    " Tab between buffers
    noremap <tab> <c-w><c-w>

    " Switch between last two buffers
    nnoremap <leader><leader> <C-^>

    " Resize buffers
    if bufwinnr(1)
      nmap Ä <C-W><<C-W><
      nmap Ö <C-W>><C-W>>
      nmap ö <C-W>-<C-W>-
      nmap ä <C-W>+<C-W>+
    endif

    " NERDTree
    nmap <leader>n :NERDTreeToggle<CR>
    let NERDTreeHighlightCursorline=1
    let NERDTreeIgnore = ['tmp', '.yardoc', 'pkg']

    " Syntastic
    let g:syntastic_mode_map = { 'mode': 'passive' }
    let g:syntastic_ruby_exec = '~/.rvm/rubies/ruby-2.0.0-p0/bin/ruby'

    " CtrlP
    nnoremap <silent> t :CtrlP<cr>
    let g:ctrlp_working_path_mode = 2
    let g:ctrlp_by_filename = 1
    let g:ctrlp_max_files = 600
    let g:ctrlp_max_depth = 5

    " Go programming
    set rtp+=/usr/local/Cellar/go/1.0.3/misc/vim

    " Quit with :Q
    command -nargs=0 Quit :qa!

##Ubuntu fix
In ubuntu you may not get the proper color pallet on the screen . You may have to export the terminal color please refer this link: (http://unix.stackexchange.com/questions/1045/getting-256-colors-to-work-in-tmux)

##And a small .gvimrc

I like to keep the main part of the config in .vimrc in order to have as few differences between the GUI and CLI versions of MacVim.

      " MacVim GUI mode
    if has("gui_macvim")
      set guifont=Monaco:h13
      set guioptions=aAce
      set fuoptions=maxvert,maxhorz
      set noballooneval

      " resize current buffer by +/- 5
      nnoremap <M-Right> :vertical resize +5<CR>
      nnoremap <M-Left>  :vertical resize -5<CR>
      nnoremap <M-Up>    :resize -5<CR>
      nnoremap <M-Down>  :resize +5<CR>

      " Command+Option+Right for next
      map <D-M-Right> :tabn<CR>
      " Command+Option+Left for previous
      map <D-M-Left> :tabp<CR>

      " Automatically resize splits
      " when resizing MacVim window
      autocmd VimResized * wincmd =
    endif


#My vimrc

If you want see my own vimrc your can see it on one of my [github
repository](https://github.com/jogiranjith/vim-conf). With the Vundle help, it’s really simple to understand what plugin I really use. All is in only one file.


