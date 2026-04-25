# blink.cmp 配置速查

## 安装

```lua
{
    "saghen/blink.cmp",
    dependencies = {
        "rafamadriz/friendly-snippets",
    },
    version = "*",
}
```

## 核心配置

```lua
require("blink.cmp").setup({
    keymap = { preset = "super-tab" },
    appearance = { nerd_font_variant = "mono" },

    completion = {
        menu = { border = "rounded" },
        ghost_text = { enabled = true },
        documentation = {
            window = { border = "rounded" },
            auto_show = true,
            auto_show_delay_ms = 200,
        },
    },

    signature = { enabled = true },

    sources = {
        default = { "lsp", "path", "snippets", "buffer" },
        providers = {
            lsp = {
                name = "LSP",
                module = "blink.cmp.sources.lsp",
                fallbacks = {}, -- 始终显示 buffer 补全
            },
        },
    },

    fuzzy = { implementation = "prefer_rust_with_warning" },
})
```

## 常见问题

### Buffer 补全不显示

默认情况下，LSP provider 有 `fallbacks = { "buffer" }`，意味着 buffer 补全只在 LSP 无结果时才出现。
要始终显示 buffer 补全，需设置 `fallbacks = {}`。

来源：https://github.com/saghen/blink.cmp/issues/59

## 快捷键（super-tab 预设）

| 快捷键 | 功能 |
|--------|------|
| `Tab` | 选择下一个 / 确认补全 |
| `Shift+Tab` | 选择上一个 |
| `Ctrl+Space` | 打开补全菜单 / 打开文档 |
| `Ctrl+e` | 关闭补全菜单 |
| `Ctrl+k` | 切换签名帮助 |
