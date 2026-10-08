# Contributing · 参与维护 · Участие

[简体中文](#zh-cn) · [Русский](#ru) · [English](#en)

<a id="zh-cn"></a>

## 简体中文

欢迎规则修正、网络测试与三语文档改进。仓库发布后，通过 Issues 报告问题，或提交聚焦单一问题的 Pull Request。

### 提交有用的反馈

请说明俄罗斯配置版本或提交、Shadowrocket 版本、测试日期、所在国家或地区、运营商及 Wi-Fi / 移动网络、问题域名、期望与实际策略、复现步骤。地区与运营商可在不影响隐私的范围内提供。连接日志只保留相关片段，去掉节点地址、口令、订阅 URL、令牌、账号和无关访问记录。

### 修改规则时

1. 说明域名对应服务、来源及需要 DIRECT 或 PROXY 的原因。
2. 检查重复规则、宽泛域名冲突和优先级。YouTube 特定 API 例外应位于 Google 通用规则之前。
3. 谨慎修改共享 API、CDN、地区域名与 GEOIP；说明可能影响的其他服务。
4. 导入 Shadowrocket 并检查相关服务的日志；分别记录通过、失败、未测试。不能实测时如实注明。
5. 同步三语 README 与更新日志，保留第三方来源与许可证。

Google 官方列有 YouTube 专用域名（[域名说明](https://knowledge.workspace.google.com/admin/youtube/control-youtube-content-available-to-users)）；同时 YouTube Data API 也使用共享主机 `www.googleapis.com`（[API 参考](https://developers.google.com/youtube/v3/docs)）。因此域名规则不能区分共享主机上的所有业务路径，应将相关影响记录为限制。

[返回中文首页](README.zh-CN.md)

<a id="ru"></a>

## Русский

Приветствуются исправления правил, результаты сетевых тестов и улучшения документации. После публикации репозитория используйте Issues для ошибок и отдельный Pull Request для каждого изменения.

В отчёте укажите версию или коммит конфигурации Russia, версию Shadowrocket, дату, страну или регион, оператора и тип сети, домен, ожидаемый и фактический маршрут, шаги воспроизведения. Сведения о местоположении и операторе можно ограничить ради приватности. Удалите из журналов адреса узлов, пароли, личные ссылки подписок, токены, учётные данные и постороннюю историю соединений.

При изменении правил:

1. Укажите сервис, источник домена и причину выбора DIRECT или PROXY.
2. Проверьте дублирование, пересечения и порядок. Исключения для API YouTube должны предшествовать общим правилам Google.
3. Опишите последствия изменения общих API, CDN, доменных зон и GEOIP.
4. Проверьте импорт и соединения в Shadowrocket; отдельно отметьте успехи, ошибки и то, что не тестировалось.
5. Обновите три README и журнал изменений; сохраните источники и лицензии сторонних материалов.

Google перечисляет [домены YouTube](https://knowledge.workspace.google.com/admin/youtube/control-youtube-content-available-to-users), а [YouTube Data API](https://developers.google.com/youtube/v3/docs) также использует общий хост `www.googleapis.com`. Правила по домену не могут разделить все пути на общем хосте — это ограничение нужно учитывать и документировать.

[Вернуться к русскому README](README.ru.md)

<a id="en"></a>

## English

Routing fixes, network test results, and documentation improvements are welcome. Once the repository is published, report bugs through Issues and keep each pull request focused on one change.

Include the Russia configuration version or commit, Shadowrocket version, test date, country or region, operator and network type, affected domain, expected and observed routes, and reproduction steps. Share regional/operator details only as appropriate for your privacy. Remove node addresses, passwords, private subscription URLs, tokens, account details, and unrelated browsing history from logs.

When changing rules:

1. Identify the service, domain source, and reason for DIRECT or PROXY.
2. Check duplicates, overlapping domains, and order. YouTube API exceptions must precede broader Google rules.
3. Describe effects on shared APIs, CDNs, country domains, and GEOIP rules.
4. Check Shadowrocket import and relevant connections; distinguish passed, failed, and untested cases.
5. Update all three READMEs and the changelog; preserve third-party sources and licenses.

Google documents [YouTube-specific domains](https://knowledge.workspace.google.com/admin/youtube/control-youtube-content-available-to-users), while the [YouTube Data API](https://developers.google.com/youtube/v3/docs) also uses the shared host `www.googleapis.com`. Domain-only rules cannot distinguish every path on a shared host; document the resulting limitations.

[Back to English README](README.md)
