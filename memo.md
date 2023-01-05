## ファイル構成

~~例~~
📂 ~/.config/nvim
├── 📁 after
├── 📁 ftplugin
├── 📂 lua
│  ├── 🌑 myluamodule.lua
│  └── 📂 other-modules
│     ├── 🌑 anothermodule.lua
│     └── 🌑 init.lua
├── 📁 pack
├── 📁 plugin
├── 📁 syntax
└── 🇻 init.vim


- ファイルロードは拡張子がいらない
- initは省略可能

## runtimepathについて
runtimepathを自動的に読み込むことができる。
サポートしているファイルは以下の通り

- colors
- compiler
- ftplugin
- ftdetect
- indent
- plugin
- syntax

luaguide-the-vim-namespace

vimの名前空間として、いくつか公開されている。

- vim.inspect:
Luaオブジェクトを人間が読みやすい文字列に変換する(テーブルを調べるのに便利です。)
- vim.regex: LuaからVimの正規表現を使う
- vim.api:
API関数を公開するモジュール(リモートプラグインで使うAPIと同じです)
- vim.ui:
プラグインから利用できる上書き可能な関数
- vim.loop:
Neovimのイベントループ機能を公開するモジュール(LibUVを使います)
- vim.lsp:
組込みのLSPクライアントを操作するモジュール
- vim.treesitter:
tree-sitterライブラリの機能を公開するモジュール

vim.optに付いてのヘルプは以下を参照
:h vim.opt

vimの内部変数について
※set, get, delそれぞれある。vim定義済みv:のみdelなし

vim.api.nvim.get\_var()
vim.api.nvim.buf\_get\_var
vim.api.nvim.win\_get\_var
vim.api.nvim.tabpage\_get\_var
vim.api.nvim.get\_vvar

メタアクセサーは以下の通り
vim.g.{name}
vim.b.{name}
vim.w.{name}
vim.t.{name}
vim.v.{name}
vim.env.{name}

ユーザーコマンドの定義
ユーザーコマンドは、
vim.api.nvim\_create\_user\_command()
で行える。
消す場合は
vim.api.nvim\_del\_user\_command()
で可能となる。
