--- 
layout: post 
title: "Invoke JS Beautify in Vim" 
date: 2013-03-01 08:00
comments: true
published: true 
categories: vim, javascript
--- 

Do you really need a plugin for vim to beautify your code? 
<!-- More -->

1) Install js-beautify

    npm install -g js-beautify

2) Map js-beautify to ,ff (if your leader is ,):

    nnoremap <leader>ff :%!js-beautify -j -q -B -f -<CR>

3) Customize the options the way you want

    js-beautify -h #will give you all options

The options above stand for

+ -j  make jshint happy
+ -q  silent, otherwise you get js beautify output in your file
+ -B  Break chained method into seperate lines
+ -f - use STDIN as file

There is no need for a vim plugin to do this for you and this way you can easily customize it the way you want.

Happy vimming!
