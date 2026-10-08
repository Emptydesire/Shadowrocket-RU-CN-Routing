# 维护与版本发布说明

本仓库已在 GitHub 公开：<https://github.com/Emptydesire/Shadowrocket-RU-CN-Routing>。默认分支为 `main`，原文件以 `configs/Russia.conf` 发布。此说明记录后续维护流程；不表示已经完成 Shadowrocket 导入或俄罗斯当地网络测试。

## 文件结构

```text
Shadowrocket-RU-CN-Routing/
├── README.md                 # English · 默认仓库首页
├── README.zh-CN.md           # 简体中文
├── README.ru.md              # Русский
├── LICENSE                  # MIT
├── SUPPORT.md               # 三语法律声明与自愿捐赠说明
├── CONTRIBUTING.md          # 三语贡献指南
├── CHANGELOG.md              # 变更记录
├── PUBLISHING.md             # 本说明
├── .gitignore
├── assets/banner.svg
├── configs/
│   ├── Russia.conf           # 用户提供的原文件，内容未修改
│   └── README.md             # 三语配置说明
└── docs/VALIDATION.md        # 三语静态核对报告
```

本仓库仅发布俄罗斯使用配置，兼顾中国服务直连。中国模式由维护者单独开源。

## 当前状态

- 公开 GitHub 仓库：[Emptydesire/Shadowrocket-RU-CN-Routing](https://github.com/Emptydesire/Shadowrocket-RU-CN-Routing)。
- [Russia v2.0 Beta 原配置](https://raw.githubusercontent.com/Emptydesire/Shadowrocket-RU-CN-Routing/main/configs/Russia.conf) 已收录，SHA-256 与提供的原文件相同。
- 静态核对了 340 条规则、关键规则顺序及文件中的凭据风险。报告见 [docs/VALIDATION.md](docs/VALIDATION.md)。
- 尚未在 Shadowrocket 中导入，也未在俄罗斯运营商网络中进行实际测试。未创建正式 GitHub Release 或版本标签。

## 更新配置

1. 只在确认域名来源与所需路由后调整规则。YouTube 专用 PROXY 例外应放在 Google 通用 DIRECT 规则之前，并留意共享的 Google API 与媒体域名。
2. 检查变更没有加入节点、订阅、凭据或未经许可的第三方规则。
3. 在 Shadowrocket 导入，查看连接日志并按运营商记录实际通过、失败和未测项目。只做静态检查时，不要描述成真实网络测试通过。
4. 同步三语 README、`configs/README.md`、`docs/VALIDATION.md` 与 `CHANGELOG.md`，写清楚测试范围和已知限制。
5. 更新默认分支后，固定的 `main` Raw 地址会提供最新配置；需要复现实验时，请使用对应的 Git commit SHA 构造固定版本链接。

当前 Raw 下载地址：

```text
https://raw.githubusercontent.com/Emptydesire/Shadowrocket-RU-CN-Routing/main/configs/Russia.conf
```

## 创建正式 Beta Release 时

若维护者决定创建 GitHub Release，将其标记为 **Pre-release**，记录对应提交、测试范围、已知限制和完整配置来源。创建前再次确认 README、原文件链接与更新日志一致。

[返回中文首页](README.zh-CN.md)
