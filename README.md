# Muvyo MetaTube 插件仓库

这是一个 Muvyo 第三方插件仓库。在 Muvyo「第三方插件 → 插件仓库」添加本仓库地址即可安装。

## 插件

- **MetaTube 刮削** — 对接自部署的 MetaTube Server，为 Vyo 媒体库提供影片搜索与元数据刮削。
- **缺集订阅桥** — 接收 Muvyo 原生的 Vyo `library.sync_completed` 事件，实时转发到 MoviePilot 缺集订阅插件，由 MP 对比 Vyo 媒体库与 TMDB 集数并记录/订阅缺失季。

## 开发者

源码放 `src/<插件ID>/`（manifest.json、main.js、README.md），只留本地，不上传。

- 签名：`python3 mv_addon.py sign ./src/metatube.metadata -o .`
- 签名：`python3 mv_addon.py sign ./src/jioson1.vyo-missing -o .`
- 仓库签名：`python3 .claude/skills/muvyo-addon-publish/scripts/sign_index.py sign --key repo-signing.pem`
- 提交：`git add -A index.json index.json.sig plugins`

开发说明见 https://github.com/thsrite/muvyo-addon-guide
