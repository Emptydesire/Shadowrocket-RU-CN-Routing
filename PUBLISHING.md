# 发布准备说明

当前文件包已包含俄罗斯原配置与三语文档，可上传为开源项目初稿。尚未通过 GitHub 发布，也未在客户端或俄罗斯当地网络实测。

## 文件结构

```text
Shadowrocket-RU-CN-Routing/
├── README.md                 # English · 默认仓库首页
├── README.zh-CN.md           # 简体中文
├── README.ru.md              # Русский
├── LICENSE                  # MIT
├── SUPPORT.md               # 三语法律声明与自愿捐赠说明
├── CONTRIBUTING.md          # 三语贡献指南
├── CHANGELOG.md              # 尚未发布的变更
├── PUBLISHING.md             # 本说明
├── .gitignore
├── assets/
│   └── banner.svg            # 自带横幅
├── configs/
│   ├── Russia.conf           # 用户提供的原文件，内容未修改
│   └── README.md             # 三语配置说明
└── docs/
    └── VALIDATION.md         # 三语静态核对报告
```

本仓库仅测试俄罗斯场景，兼顾中国服务直连。中国模式将由维护者单独开源，不需要在本仓库补充中国配置。

## 1. 创建仓库并上传

在自己的 GitHub 账户或目标组织下创建公开仓库 `Shadowrocket-RU-CN-Routing`，将本文件夹的**内容**上传到仓库根目录，保留子目录。避免再包一层同名文件夹。已有同名仓库时，先核对现有文件并合并。

建议仓库简介：

```text
Shadowrocket for Russia · 俄罗斯网络分流 · Правила для России · Russian & Chinese services DIRECT · v2.0 Beta
```

默认首页为 English，中文与俄语入口均在顶部。

## 2. 确认配置与测试状态

已收录 `configs/Russia.conf`，与用户提供的原文件字节一致。340 条规则的结构、关键顺序与潜在敏感信息已静态核对，详情见 [核对报告](docs/VALIDATION.md#zh-cn)。

仍需在 Shadowrocket 中实际导入，选择自己的节点，检查俄罗斯机构、中国服务、Google 与 YouTube 的匹配日志。按 [贡献指南](CONTRIBUTING.md#zh-cn) 记录实际通过、失败和未测试的范围；不要将静态检查写成网络测试通过。后续引入第三方规则时核对来源与许可。

## 3. 启用真实 Raw 链接

文件上传后，进入 GitHub 文件页面，使用 **Raw** 或原始文件下载按钮取得链接。将三语 README 中的 `OWNER` 与 `REF` 模板替换为真实信息，并增加对应 Raw 下载链接。

```text
https://raw.githubusercontent.com/OWNER/Shadowrocket-RU-CN-Routing/REF/configs/Russia.conf
```

这是占位格式。`REF` 为实际分支、标签或提交：分支用于持续更新，固定提交便于复现版本。复制 GitHub 提供的 Raw 地址可减少拼写错误，不要使用 `github.com/.../blob/...` 预览页地址。

在未登录状态确认链接返回预期配置纯文本，再从 Shadowrocket 下载、启用并检查匹配。参考 [GitHub 官方 Raw 文件说明](https://docs.github.com/en/repositories/working-with-files/using-files/viewing-and-understanding-files#viewing-or-copying-the-raw-file-content)。

## 4. 标注 Beta 发布

发布成功后同步三语 README、配置说明和更新日志中的 GitHub 状态，添加真实仓库链接。若创建 Russia v2.0 Beta 的 GitHub Release，应标记为 **Pre-release** 并说明测试范围与已知限制。

保留共享 Google / YouTube 域名与地区兜底限制；没有当地实测时继续明确标注，不声称所有服务可达。

[返回中文首页](README.zh-CN.md)
