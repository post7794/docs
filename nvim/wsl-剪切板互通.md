# WSL 剪切板互通配置

WSL 中 Neovim 与 Windows 剪切板互通，使用 win32yank。

## 问题

WSL Arch Linux 默认没有注册 Windows .exe 的 binfmt_misc 入口，导致：
- `win32yank.exe` 报 `cannot execute binary file: Exec format error`
- 所有 `.exe` 程序无法直接在 WSL 中运行

## 解决步骤

### 1. 安装 win32yank

```bash
curl -sL https://github.com/equalsraf/win32yank/releases/latest/download/win32yank-x64.zip -o /tmp/win32yank.zip
cd /tmp && unzip -o win32yank.zip win32yank.exe
mv win32yank.exe /usr/local/bin/
chmod +x /usr/local/bin/win32yank.exe
```

### 2. 注册 WSL interop

检查是否已注册：

```bash
cat /proc/sys/fs/binfmt_misc/WSLInterop
```

如果不存在，手动注册：

```bash
echo ':WSLInterop:M::MZ::/init:PF' > /proc/sys/fs/binfmt_misc/register
```

### 3. 持久化（开机自动注册）

在 `/etc/wsl.conf` 中添加：

```ini
[boot]
systemd=true
command=echo ':WSLInterop:M::MZ::/init:PF' > /proc/sys/fs/binfmt_misc/register
```

### 4. Neovim 配置

在 `lua/options.lua` 中添加：

```lua
-- WSL clipboard support
if vim.fn.has("wsl") == 1 then
    vim.g.clipboard = {
        name = "win32yank",
        copy = {
            ["+"] = "win32yank.exe -i --crlf",
            ["*"] = "win32yank.exe -i --crlf",
        },
        paste = {
            ["+"] = "win32yank.exe -o --lf",
            ["*"] = "win32yank.exe -o --lf",
        },
        cache_enabled = true,
    }
end

opt.clipboard = "unnamedplus"
```

## 验证

```bash
# 测试 win32yank
echo hello from wsl | win32yank.exe -i --crlf
win32yank.exe -o --lf
# 应输出: hello from wsl

# 在 Windows 侧 Ctrl+V 也能粘贴出相同内容
```

在 Neovim 中 `y` 复制后，Windows 里 Ctrl+V 即可粘贴。
