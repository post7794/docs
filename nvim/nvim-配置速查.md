# Neovim 配置速查

## 安装位置

```
~/.config/nvim/
```

## 主题

Kanagawa Wave，配置文件：`lua/plugins/kanagawa.lua`

```lua
require("kanagawa").setup({
    transparent = true,  -- 背景透明，改为 false 关闭
})
vim.cmd.colorscheme("kanagawa-wave")
```

## 快捷键速查

Leader 键：`Space`

### 文件操作

| 快捷键 | 功能 |
|--------|------|
| `Space+e` | 打开/切换 Oil 文件管理器侧边栏 |
| `Space+ff` | 查找文件 |
| `Space+fg` | 全局搜索（Live Grep） |

### 编辑

| 快捷键 | 模式 | 功能 |
|--------|------|------|
| `Space+/` | Normal / Visual | 切换注释 |
| `Space+gf` | Normal / Visual | 格式化代码 |
| `Tab` | Normal | 缩进 |
| `Shift+Tab` | Normal | 反缩进 |
| `Alt+j/k` | Visual | 上下移动选中行 |

### 窗口

| 快捷键 | 功能 |
|--------|------|
| `Ctrl+h/j/k/l` | 跳转到左/下/上/右窗口 |
| `Alt+=/-` | 增减窗口高度 |
| `Alt+,/.` | 增减窗口宽度 |

### Buffer

| 快捷键 | 功能 |
|--------|------|
| `Space+bh` | 上一个 Buffer |
| `Space+bl` | 下一个 Buffer |
| `Space+bd` | 关闭当前 Buffer |

### LSP

| 快捷键 | 功能 |
|--------|------|
| `K` | 悬停文档 |
| `gd` | 跳转到定义 |
| `gD` | 跳转到声明 |
| `gr` | 跳转到引用 |
| `gi` | 跳转到实现 |
| `Space+rn` | 重命名 |
| `Space+ca` | 代码操作 |
| `Space+d` | 行诊断浮窗 |
| `[d` / `]d` | 上/下一个诊断 |

### Rust（.rs 文件）

| 快捷键 | 功能 |
|--------|------|
| `Space+rr` | 运行 target |
| `Space+rd` | 调试 target |
| `Space+rh` | 悬停操作 |
| `Space+re` | 展开宏 |
| `Space+ro` | 打开 Cargo.toml |
| `Space+rp` | 跳转到父模块 |
| `Space+rc` | Crate 依赖图 |
| `Space+rs` | 结构化搜索替换 |

### 折叠

| 快捷键 | 功能 |
|--------|------|
| `zC` | 关闭所有折叠 |
| `zO` | 打开所有折叠 |
| `zp` | 预览折叠内容 |

### 其他

| 快捷键 | 功能 |
|--------|------|
| `Esc` | 清除搜索高亮 |
| `Space+`` ` | 打开/关闭终端 |
| `Esc`（Terminal） | 退出终端模式 |
| `Space+tr` | 切换相对行号 |

### Oil 文件管理器

| 快捷键 | 功能 |
|--------|------|
| `Ctrl+s` | 垂直分屏打开文件 |
| `Enter` | 进入目录 / 打开文件 |
| `q` | 关闭侧边栏 |
| `-` | 返回上级目录 |

隐藏文件默认始终显示。

### Dashboard

| 快捷键 | 功能 |
|--------|------|
| `n` | 新建文件 |
| `f` | 查找文件 |
| `t` | 全局搜索 |
| `u` | 更新插件 |
| `l` | 打开 Lazy |
| `q` | 退出 |

## 插件列表

| 插件 | 功能 |
|------|------|
| blink.cmp | 自动补全 |
| bufferline.nvim | Buffer 标签栏 |
| kanagawa.nvim | 主题 |
| colorizer | 颜色代码高亮 |
| conform.nvim | 代码格式化 |
| fidget.nvim | LSP 进度动画 |
| friendly-snippets | 代码片段集合 |
| fzf-lua | 模糊查找 |
| gitsigns.nvim | Git 标记 |
| indent-blankline | 缩进线 |
| lazy.nvim | 插件管理 |
| lualine.nvim | 状态栏 |
| mason.nvim | LSP/格式化工具管理 |
| mason-tool-installer.nvim | Mason 工具自动安装 |
| mini.nvim | 自动配对/环绕/注释/缩进作用域 |
| noice.nvim | 命令行/通知 UI 美化 |
| nvim-notify | 通知弹窗 |
| nvim-ufo | 代码折叠 |
| oil.nvim | 文件管理器 |
| promise-async | 异步支持（ufo 依赖） |
| rainbow-delimiters | 彩虹括号 |
| render-markdown | Markdown 渲染 |
| rustaceanvim | Rust 增强 |
| snacks.nvim | Dashboard/大文件/快速打开 |
| toggleterm.nvim | 终端 |
| treesitter | 语法高亮 |
| nvim-web-devicons | 图标 |

## LSP 服务器

通过 Mason 自动安装：lua_ls、clangd、pyright、ts_ls、html、cssls、rust_analyzer

## 格式化工具

stylua（Lua）、clang-format（C/C++）、black（Python）、prettier（JS/HTML/CSS）、rustfmt（Rust）

## 前提条件

Arch Linux：
```bash
pacman -S neovim git gcc nodejs npm python unzip go
```
