# 缺集订阅桥

这是 MoviePilot「缺集订阅」插件的 Muvyo 配套插件。

## 作用

Muvyo 收到 Vyo 媒体库同步完成事件（`library.sync_completed`）后，本插件会把事件实时转发到 MoviePilot 缺集订阅插件。MP 侧再对比 Vyo 媒体库与 TMDB 集数：

- 全部存在时在插件 UI 记录「全部存在」
- 有缺失时记录「存在缺失」，并可按设置自动添加 MP 订阅
- 无法识别时记录失败记录，便于排查

本插件只处理 `library.sync_completed`，不会把 Muvyo 的资源接收、整理事件（`strm.generated`、`organize.completed` 等）转发给 MP。

## 安装与配置

1. 在 Muvyo 第三方插件中安装本插件。
2. 在插件设置里填写 MoviePilot 地址，例如 `http://127.0.0.1:3000`。
3. 填写 MoviePilot 的 API Token，也就是 MP 首页/设置里的 `API_TOKEN`。
4. 保持 Webhook 路径为 `/api/v1/plugin/EpisodeNoExist/muvyo_webhook`。
5. 打开插件设置里的「接收 Muvyo 事件」开关。

Muvyo 原生插件事件和 Muvyo 的「Webhook 推送」互不依赖，不需要再配置 Webhook 推送地址。

## 工作原理

Muvyo 原生 `webhookEvent` 收到 `library.sync_completed` 后，会以 `POST` 方式把事件、媒体库名称和可用的 TMDB 信息发送到 MP。MP 收到后只按本次事件对应的 Vyo 媒体库检查新增条目，不进行周期全库扫描。

如果 Muvyo 事件本身没有携带具体条目信息，MP 会在该媒体库同步完成后检查尚未有过缺集记录的新条目，并把每个新条目都写入插件 UI。
