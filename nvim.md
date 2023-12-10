# LazyVim

Custom keymap:

```lua
-- ~/.config/nvim/lua/config/keymaps.lua

local keymap = vim.keymap
local opts = { noremap = true, silent = true }

keymap.set("n", "x", '"_x')

-- Increment/decrement
keymap.set("n", "+", "<C-a>")
keymap.set("n", "-", "<C-x>")

-- Delete a word backwards
keymap.set("n", "dw", 'vb"_d')

-- Select all
keymap.set("n", "<C-a>", "gg<S-v>G")

-- Save with root permission (not working for now)
--vim.api.nvim_create_user_command('W', 'w !sudo tee > /dev/null %', {})

-- Disable continuations
keymap.set("n", "<Leader>o", "o<Esc>^Da", opts)
keymap.set("n", "<Leader>O", "O<Esc>^Da", opts)

-- Jumplist
keymap.set("n", "<C-m>", "<C-i>", opts)

-- New tab
keymap.set("n", "te", ":tabedit")
keymap.set("n", "<tab>", ":tabnext<Return>", opts)
keymap.set("n", "<s-tab>", ":tabprev<Return>", opts)
-- Split window
keymap.set("n", "ss", ":split<Return>", opts)
keymap.set("n", "sv", ":vsplit<Return>", opts)
-- Move window
keymap.set("n", "sh", "<C-w>h")
keymap.set("n", "sk", "<C-w>k")
keymap.set("n", "sj", "<C-w>j")
keymap.set("n", "sl", "<C-w>l")

-- Resize window
keymap.set("n", "<C-w><left>", "<C-w><")
keymap.set("n", "<C-w><right>", "<C-w>>")
keymap.set("n", "<C-w><up>", "<C-w>+")
keymap.set("n", "<C-w><down>", "<C-w>-")

-- Diagnostics
keymap.set("n", "<C-j>", function()
  vim.diagnostic.goto_next()
end, opts)

keymap.set("n", "<leader>r", function()
  require("tristan.utils").replaceHexWithHSL()
end)
```

## General

| Key                  | Description                           | Mode                       |
| -------------------- | ------------------------------------- | -------------------------- |
| `<C-h>`              | Go to left window                     | **n**, **t**               |
| `<C-j>`              | Go to lower window                    | **n**, **t**               |
| `<C-k>`              | Go to upper window                    | **n**, **t**               |
| `<C-l>`              | Go to right window                    | **n**, **t**               |
| `<C-Up>`             | Increase window height                | **n**                      |
| `<C-Down>`           | Decrease window height                | **n**                      |
| `<C-Left>`           | Decrease window width                 | **n**                      |
| `<C-Right>`          | Increase window width                 | **n**                      |
| `<A-j>`              | Move down                             | **n**, **i**, **v**        |
| `<A-k>`              | Move up                               | **n**, **i**, **v**        |
| `<S-h>`              | Prev buffer                           | **n**                      |
| `<S-l>`              | Next buffer                           | **n**                      |
| `[b`                 | Prev buffer                           | **n**                      |
| `]b`                 | Next buffer                           | **n**                      |
| `<leader>bb`         | Switch to Other Buffer                | **n**                      |
| `` <leader>` ``      | Switch to Other Buffer                | **n**                      |
| `<esc>`              | Escape and clear hlsearch             | **i**, **n**               |
| `<leader>ur`         | Redraw / clear hlsearch / diff update | **n**                      |
| `n`                  | Next search result                    | **n**, **x**, **o**        |
| `N`                  | Prev search result                    | **n**, **x**, **o**        |
| `<C-s>`              | Save file                             | **i**, **x**, **n**, **s** |
| `<leader>K`          | Keywordprg                            | **n**                      |
| `<leader>l`          | Lazy                                  | **n**                      |
| `<leader>fn`         | New File                              | **n**                      |
| `<leader>xl`         | Location List                         | **n**                      |
| `<leader>xq`         | Quickfix List                         | **n**                      |
| `[q`                 | Previous quickfix                     | **n**                      |
| `]q`                 | Next quickfix                         | **n**                      |
| `<leader>cf`         | Format                                | **n**, **v**               |
| `<leader>cd`         | Line Diagnostics                      | **n**                      |
| `]d`                 | Next Diagnostic                       | **n**                      |
| `[d`                 | Prev Diagnostic                       | **n**                      |
| `]e`                 | Next Error                            | **n**                      |
| `[e`                 | Prev Error                            | **n**                      |
| `]w`                 | Next Warning                          | **n**                      |
| `[w`                 | Prev Warning                          | **n**                      |
| `<leader>uf`         | Toggle auto format (global)           | **n**                      |
| `<leader>uF`         | Toggle auto format (buffer)           | **n**                      |
| `<leader>us`         | Toggle Spelling                       | **n**                      |
| `<leader>uw`         | Toggle Word Wrap                      | **n**                      |
| `<leader>uL`         | Toggle Relative Line Numbers          | **n**                      |
| `<leader>ul`         | Toggle Line Numbers                   | **n**                      |
| `<leader>ud`         | Toggle Diagnostics                    | **n**                      |
| `<leader>uc`         | Toggle Conceal                        | **n**                      |
| `<leader>uh`         | Toggle Inlay Hints                    | **n**                      |
| `<leader>uT`         | Toggle Treesitter Highlight           | **n**                      |
| `<leader>gg`         | Lazygit (root dir)                    | **n**                      |
| `<leader>gG`         | Lazygit (cwd)                         | **n**                      |
| `<leader>qq`         | Quit all                              | **n**                      |
| `<leader>ui`         | Inspect Pos                           | **n**                      |
| `<leader>L`          | LazyVim Changelog                     | **n**                      |
| `<leader>ft`         | Terminal (root dir)                   | **n**                      |
| `<leader>fT`         | Terminal (cwd)                        | **n**                      |
| `<c-/>`              | Terminal (root dir)                   | **n**                      |
| `<c-_>`              | which_key_ignore                      | **n**, **t**               |
| `<esc><esc>`         | Enter Normal Mode                     | **t**                      |
| `<C-/>`              | Hide Terminal                         | **t**                      |
| `<leader>ww`         | Other window                          | **n**                      |
| `<leader>wd`         | Delete window                         | **n**                      |
| `<leader>w-`         | Split window below                    | **n**                      |
| `<leader>w\|`        | Split window right                    | **n**                      |
| `<leader>-`          | Split window below                    | **n**                      |
| `<leader>\|`         | Split window right                    | **n**                      |
| `<leader><tab>l`     | Last Tab                              | **n**                      |
| `<leader><tab>f`     | First Tab                             | **n**                      |
| `<leader><tab><tab>` | New Tab                               | **n**                      |
| `<leader><tab>]`     | Next Tab                              | **n**                      |
| `<leader><tab>d`     | Close Tab                             | **n**                      |
| `<leader><tab>[`     | Previous Tab                          | **n**                      |

## LSP

| Key          | Description            | Mode         |
| ------------ | ---------------------- | ------------ |
| `<leader>cl` | Lsp Info               | **n**        |
| `gd`         | Goto Definition        | **n**        |
| `gr`         | References             | **n**        |
| `gD`         | Goto Declaration       | **n**        |
| `gI`         | Goto Implementation    | **n**        |
| `gy`         | Goto T[y]pe Definition | **n**        |
| `K`          | Hover                  | **n**        |
| `gK`         | Signature Help         | **n**        |
| `<c-k>`      | Signature Help         | **i**        |
| `<leader>ca` | Code Action            | **n**, **v** |
| `<leader>cA` | Source Action          | **n**        |
| `<leader>cr` | Rename                 | **n**        |

## [bufferline.nvim](https://github.com/akinsho/bufferline.nvim.git)[​](https://www.lazyvim.org/keymaps#bufferlinenvim "Direct link to bufferlinenvim")

| Key          | Description                 | Mode  |
| ------------ | --------------------------- | ----- |
| `<leader>bl` | Delete buffers to the left  | **n** |
| `<leader>bo` | Delete other buffers        | **n** |
| `<leader>bp` | Toggle pin                  | **n** |
| `<leader>bP` | Delete non-pinned buffers   | **n** |
| `<leader>br` | Delete buffers to the right | **n** |
| `[b`         | Prev buffer                 | **n** |
| `]b`         | Next buffer                 | **n** |
| `<S-h>`      | Prev buffer                 | **n** |
| `<S-l>`      | Next buffer                 | **n** |

## [neo-tree.nvim](https://github.com/nvim-neo-tree/neo-tree.nvim.git)

| Key          | Description                 | Mode  |
| ------------ | --------------------------- | ----- |
| `<leader>be` | Buffer explorer             | **n** |
| `<leader>e`  | Explorer NeoTree (root dir) | **n** |
| `<leader>E`  | Explorer NeoTree (cwd)      | **n** |
| `<leader>fe` | Explorer NeoTree (root dir) | **n** |
| `<leader>fE` | Explorer NeoTree (cwd)      | **n** |
| `<leader>ge` | Git explorer                | **n** |

## [noice.nvim](https://github.com/folke/noice.nvim.git)

| Key           | Description        | Mode                |
| ------------- | ------------------ | ------------------- |
| `<c-b>`       | Scroll backward    | **n**, **i**, **s** |
| `<c-f>`       | Scroll forward     | **n**, **i**, **s** |
| `<leader>sna` | Noice All          | **n**               |
| `<leader>snd` | Dismiss All        | **n**               |
| `<leader>snh` | Noice History      | **n**               |
| `<leader>snl` | Noice Last Message | **n**               |
| `<S-Enter>`   | Redirect Cmdline   | **c**               |

## [nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter.git)

| Key         | Description         | Mode  |
| ----------- | ------------------- | ----- |
| `<bs>`      | Decrement selection | **x** |
| `<c-space>` | Increment selection | **n** |

## [telescope.nvim](https://github.com/nvim-telescope/telescope.nvim.git)

| Key               | Description              | Mode  |
| ----------------- | ------------------------ | ----- |
| `<leader><space>` | Find Files (root dir)    | **n** |
| `<leader>,`       | Switch Buffer            | **n** |
| `<leader>/`       | Grep (root dir)          | **n** |
| `<leader>:`       | Command History          | **n** |
| `<leader>fb`      | Buffers                  | **n** |
| `<leader>fc`      | Find Config File         | **n** |
| `<leader>ff`      | Find Files (root dir)    | **n** |
| `<leader>fF`      | Find Files (cwd)         | **n** |
| `<leader>fr`      | Recent                   | **n** |
| `<leader>fR`      | Recent (cwd)             | **n** |
| `<leader>gc`      | commits                  | **n** |
| `<leader>gs`      | status                   | **n** |
| `<leader>s"`      | Registers                | **n** |
| `<leader>sa`      | Auto Commands            | **n** |
| `<leader>sb`      | Buffer                   | **n** |
| `<leader>sc`      | Command History          | **n** |
| `<leader>sC`      | Commands                 | **n** |
| `<leader>sd`      | Document diagnostics     | **n** |
| `<leader>sD`      | Workspace diagnostics    | **n** |
| `<leader>sg`      | Grep (root dir)          | **n** |
| `<leader>sG`      | Grep (cwd)               | **n** |
| `<leader>sh`      | Help Pages               | **n** |
| `<leader>sH`      | Search Highlight Groups  | **n** |
| `<leader>sk`      | Key Maps                 | **n** |
| `<leader>sm`      | Jump to Mark             | **n** |
| `<leader>sM`      | Man Pages                | **n** |
| `<leader>so`      | Options                  | **n** |
| `<leader>sR`      | Resume                   | **n** |
| `<leader>ss`      | Goto Symbol              | **n** |
| `<leader>sS`      | Goto Symbol (Workspace)  | **n** |
| `<leader>sw`      | Word (root dir)          | **n** |
| `<leader>sW`      | Word (cwd)               | **n** |
| `<leader>sw`      | Selection (root dir)     | **v** |
| `<leader>sW`      | Selection (cwd)          | **v** |
| `<leader>uC`      | Colorscheme with preview | **n** |

## [todo-comments.nvim](https://github.com/folke/todo-comments.nvim.git)

| Key          | Description              | Mode  |
| ------------ | ------------------------ | ----- |
| `<leader>st` | Todo                     | **n** |
| `<leader>sT` | Todo/Fix/Fixme           | **n** |
| `<leader>xt` | Todo (Trouble)           | **n** |
| `<leader>xT` | Todo/Fix/Fixme (Trouble) | **n** |
| `[t`         | Previous todo comment    | **n** |
| `]t`         | Next todo comment        | **n** |

## [trouble.nvim](https://github.com/folke/trouble.nvim.git)[​](https://www.lazyvim.org/keymaps#troublenvim "Direct link to troublenvim")

| Key          | Description                     | Mode  |
| ------------ | ------------------------------- | ----- |
| `<leader>xL` | Location List (Trouble)         | **n** |
| `<leader>xQ` | Quickfix List (Trouble)         | **n** |
| `<leader>xx` | Document Diagnostics (Trouble)  | **n** |
| `<leader>xX` | Workspace Diagnostics (Trouble) | **n** |
| `[q`         | Previous trouble/quickfix item  | **n** |
| `]q`         | Next trouble/quickfix item      | **n** |

## [yanky.nvim](https://github.com/gbprod/yanky.nvim.git)[​](https://www.lazyvim.org/keymaps#yankynvim "Direct link to yankynvim")

Part of [lazyvim.plugins.extras.coding.yanky](https://www.lazyvim.org/extras/coding/yanky)

| Key         | Description                           | Mode         |
| ----------- | ------------------------------------- | ------------ |
| `<leader>p` | Open Yank History                     | **n**        |
| `<p`        | Put and indent left                   | **n**        |
| `<P`        | Put before and indent left            | **n**        |
| `=p`        | Put after applying a filter           | **n**        |
| `=P`        | Put before applying a filter          | **n**        |
| `>p`        | Put and indent right                  | **n**        |
| `>P`        | Put before and indent right           | **n**        |
| `[p`        | Put indented before cursor (linewise) | **n**        |
| `[P`        | Put indented before cursor (linewise) | **n**        |
| `[y`        | Cycle forward through yank history    | **n**        |
| `]p`        | Put indented after cursor (linewise)  | **n**        |
| `]P`        | Put indented after cursor (linewise)  | **n**        |
| `]y`        | Cycle backward through yank history   | **n**        |
| `gp`        | Put yanked text after selection       | **n**, **x** |
| `gP`        | Put yanked text before selection      | **n**, **x** |
| `p`         | Put yanked text after cursor          | **n**, **x** |
| `P`         | Put yanked text before cursor         | **n**, **x** |
| `y`         | Yank text                             | **n**, **x** |
