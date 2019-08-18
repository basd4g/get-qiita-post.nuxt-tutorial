# chapter02-qiita-post.nuxt-tutorial

## Overview

This is web application to get Qiita's post of tag 'Nuxt.js' , 
and Nuxt.js tutorial project.

Write code based on the book 'Nuxt.js ビギナーズガイド' pp.27-59 in this project.

On commit message, 'pXX hogehoge' mean 'To implement hogehoge on p. XX of the book.'

## How to use

### Get Qiita token

Get Qiita's access token.Scope 'read_qiita' is required.  
(Qiita アクセストークンの発行)[https://qiita.com/settings/tokens/new]

### Clone Repository

    $ git clone https://github.com/basd4g/chapter02-qiita-post.nuxt-tutorial.git
    $ cd chapter02-qiita-post.nuxt-tutorial/

### Set Qiita token to environment variable

    # Install direnv for macOSX.
    $ brew install direnv 
    $ echo 'eval "$(direnv hook bash)"' >> ~/.bashrc

    # Make .envrc and load it.
    $ touch .envrc
    # For example, Qiita token is '0123456789abcdef',
    $ echo "export QIITA_TOKEN=<0123456789abcdef>" > .envrc
    $ direnv allow

### Build and Run

    # If you didn't install yarn,
    $ brew install yarn

    $ yarn
    $ yarn run dev
    # And Open 'http://localhost:3000/' on web browswer.

## Reference

- [Nuxt.js ビギナーズガイド](https://nuxt-beginners-guide.elevenback.jp)
- [ステート | Vuex](https://vuex.vuejs.org/ja/guide/state.html)
