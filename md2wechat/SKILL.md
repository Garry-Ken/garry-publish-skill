---
name: md2wechat
description: 将 Markdown 转换为微信公众号兼容的排版 HTML。支持 11 套主题（Mac、Claude、微信原生、GitHub、Dracula 等），图片自动 Base64 打包，表格/列表微信兼容，一键复制到公众号后台。Use when converting markdown to WeChat Official Account HTML, exporting articles for WeChat, or formatting blog posts for WeChat distribution.
argument-hint: "<markdown-file> [theme]"
arguments:
  - file
  - theme
allowed-tools: Bash(node *), Bash(npm *), Bash(pbcopy), Bash(xclip *), Bash(xsel *), Read, Write
---

# Markdown → 微信公众号 HTML 转换

将 Markdown 文件转换为微信公众号兼容的 HTML，自动应用主题样式，结果复制到系统剪贴板。

## 使用方法

用户会提供一个 Markdown 文件路径和可选的主题名称。

**参数：**
- `$file` — Markdown 文件路径（必须）
- `$theme` — 主题 ID（可选，默认 `apple`）

## 可用主题

| 主题 ID | 名称 | 风格 |
|---------|------|------|
| `apple` | Mac 极简白 | 纯净现代，极致留白 |
| `claude` | Claude 燕麦 | 温润燕麦色底，深度长文 |
| `wechat` | 微信原生 | 公众号默认风格 |
| `media` | NYT 纽约时报 | 经典新闻排版 |
| `stripe` | Stripe 硅谷 | 科技感极简 |
| `linear` | Linear 暗夜 | 深色极客风 |
| `notion` | Notion 笔记 | 清爽笔记风 |
| `github` | GitHub 文档 | 开发者文档风 |
| `dracula` | Dracula 暗夜 | 经典暗色配色 |
| `sakura` | 樱花粉 | 柔和粉色系 |
| `cyberpunk` | 赛博朋克 | 霓虹未来感 |

## 执行步骤

1. 读取用户指定的 Markdown 文件
2. 检查转换脚本的依赖是否已安装：

```bash
cd "${CLAUDE_SKILL_DIR}/scripts" && [ -d node_modules ] || npm install --silent
```

3. 运行转换脚本：

```bash
node "${CLAUDE_SKILL_DIR}/scripts/convert.mjs" "<markdown-file-path>" "<theme-id>"
```

脚本会输出转换后的 HTML 到 stdout，同时写入 `/tmp/md2wechat-output.html`。

4. 复制到系统剪贴板：

```bash
# macOS
node "${CLAUDE_SKILL_DIR}/scripts/convert.mjs" "<file>" "<theme>" | pbcopy

# Linux
node "${CLAUDE_SKILL_DIR}/scripts/convert.mjs" "<file>" "<theme>" | xclip -selection clipboard
```

5. 告知用户：
   - 已复制到剪贴板，可直接粘贴到公众号后台
   - 同时保存了一份到 `/tmp/md2wechat-output.html`
   - 使用的主题名称

## 注意事项

- 如果用户没有指定主题，默认使用 `apple`
- 如果用户说「所有主题」或「列出主题」，展示上面的主题表格
- 如果文件路径不存在，提示用户检查路径
- 转换脚本是自包含的，不依赖外部项目
