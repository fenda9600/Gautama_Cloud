---
type: "inbox"
status: "pending"
source: "web-clipper"
url: "https://gemini.google.com/app/1b951cb3c5788f76"
created: 2026-03-06
---
\> 整合 Antigravity 配置 (MCP 模式) 没有找到配置文件

## Gemini 说

没找到配置文件很正常，因为 **Google Antigravity**（以及它基于的 Claude Desktop 架构）在初次安装时通常不会自动创建这个 `.json` 文件。我们需要手动“无中生有”。

按照以下步骤，在你的 Mac 上精准创建它：

---

### 1\. 定位并创建目录

打开你的 Mac **终端**，执行以下命令来确保配置文件夹存在：

Bash

```
mkdir -p ~/Library/Application\ Support/Google\ Antigravity/
```

### 2\. 创建并编辑配置文件

直接在终端使用 `nano` 编辑器创建这个文件：

Bash

```
nano ~/Library/Application\ Support/Google\ Antigravity/mcp_config.json
```

### 3\. 粘贴配置内容

将下面的代码完整复制并粘贴到弹出的黑色编辑界面中。**注意：** 我已经根据你的信息，把用户名 `fenda9600` 和 IP `163.7.4.107` 填好了：

JSON

```
{
  "mcpServers": {
    "volc-openclaw": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-ssh",
        "ssh",
        "root@163.7.4.107",
        "-i",
        "/Users/fenda9600/.ssh/id_rsa"
      ]
    }
  }
}
```

### 4\. 保存并退出

- 按 **`Control + O`**（保存）。
- 按 **`回车`**（确认文件名）。
- 按 **`Control + X`**（退出编辑器）。

---

### 5\. 在 Antigravity 中激活

1. **彻底退出** Google Antigravity 软件（使用 `Command + Q`，确保它不在后台运行）。
2. **重新打开** Google Antigravity。
3. **寻找“插头”图标**：在对话框的工具栏或者侧边栏，你会看到一个 MCP 扩展图标。如果配置正确，你会看到 `volc-openclaw` 显示为 **Green/Active**。

---

### 验证一刻

现在，你可以对着 Antigravity 里的 Claude 说：

> **“Claude，请调用 volc-openclaw 连接我的服务器，列出 `/root` 目录下所有的文件，看看我的 OpenClaw 源代码在哪。”**