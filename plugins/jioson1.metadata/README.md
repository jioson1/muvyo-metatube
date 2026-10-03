# MetaTube 刮削

对接自部署的 [MetaTube Server](https://github.com/metatube-community)，为 Vyo 媒体库提供影片搜索与元数据刮削。

## 功能

- 影片搜索：按番号或关键词搜索，支持多来源聚合
- 完整元数据：标题、简介、演员、导演、厂牌、类型、评分、上映日期
- 图片刮削：海报与背景图，经 MetaTube 服务端裁剪代理
- 命名模板：自定义标题与副标题的生成规则
- 文本替换：对标题、类型、演员做批量替换
- 来源过滤：多来源结果按优先级过滤与排序
- 自动翻译：通过 MetaTube Server 翻译标题与简介（Google 免费版/百度/Google/DeepL/OpenAI）
- 真实演员名：从 AVBASE 搜索并替换为真实演员名
- 中文字幕徽章：在海报上添加字幕徽章
- 系列标签：将系列名加入类型标签

## 前置条件

1. 部署 [MetaTube Server](https://metatube-community.github.io/wiki/server-deployment/)
2. 在插件设置里填写服务地址与访问令牌

## 文件命名

影片文件按番号命名以获得最佳识别效果，详见 [命名规则](https://metatube-community.github.io/wiki/naming-rules/)。

## 图片说明

图片由 Muvyo 经服务地址代为取回。MetaTube 图片接口无需鉴权，但服务地址建议使用 HTTPS——Muvyo 刮削结果中的图片只接受 HTTPS 地址，内网 HTTP 地址需管理员在 Vyo 中勾选「允许访问这个内网服务」。

## 配置项

| 配置 | 说明 |
|---|---|
| MetaTube Server 地址 | 服务地址（设置页顶部） |
| 访问令牌 | 服务端鉴权令牌，未设置则留空 |
| 图片质量 | JPEG 压缩质量 1-100 |
| 添加导演 | 将导演加入演职员 |
| 显示评分 | 展示社区评分（0-10） |
| 自定义命名 | 启用后使用模板生成标题 |
| 标题模板 | 变量: `{number}` `{title}` `{series}` `{maker}` `{label}` `{director}` `{actors}` `{first_actor}` `{year}` `{month}` `{date}` |
| 副标题模板 | 留空则不设副标题 |
| 标题/类型/演员替换 | 每行一条，等号分隔，留空目标可删除源文本 |
| 来源过滤 | 按优先级保留和排序搜索结果 |
| 自动翻译 | 通过 MetaTube Server 翻译，选择引擎并填写对应密钥 |
| 翻译引擎 | Google 免费版（无需密钥）/ 百度 / Google / DeepL / OpenAI |
| 翻译内容 | 仅标题 / 仅简介 / 标题和简介 |
| 目标语言 | ISO 语言代码，如 zh、en |
| 真实演员名 | 从 AVBASE 搜索并替换（支持 DUGA/FANZA/Getchu/MGS 来源） |
| 中文字幕徽章 | 在海报上添加徽章图片 |
| 添加系列标签 | 将系列名加入类型标签（Muvyo 无合集字段） |
