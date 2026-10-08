# Static validation · 静态核对 · Статическая проверка

[简体中文](#zh-cn) · [Русский](#ru) · [English](#en)

**2026-10-08 · Russia v2.0 Beta · Static review only**

File / 文件 / Файл: [`configs/Russia.conf`](../configs/Russia.conf)  
Source filename / 原文件名 / Исходное имя: `Shadowrocket-Russia-v2.0-Beta.conf`

SHA-256:

```text
13b3fbb76326ab0141bb1b28f98ea2c1a101648ffccb116181d0b3b5c6967df0
```

<a id="zh-cn"></a>

## 简体中文

**俄罗斯模式原文件已完成静态核对，发布副本保持原文件内容不变。** 本报告只针对上述哈希对应的文件；配置包含中国服务 DIRECT，但本仓库不提供中国模式。

| 检查项 | 结果 |
| :--- | :--- |
| 结构 | `[General]`、`[Rule]`；4 个通用设置项 |
| 规则总数 | **340 条**非空、非注释规则，不等于 340 个服务 |
| 规则类型 | 333 条 `DOMAIN-SUFFIX`、4 条 `IP-CIDR`、2 条 `GEOIP`、1 条 `FINAL` |
| 策略数量 | 291 条 DIRECT；49 条 PROXY，包含 `FINAL,PROXY` |
| 基础结构检查 | 未发现未知规则类型、字段数异常或无效 IPv4 网段；不等于客户端语法验证 |
| 精确重复 | 未发现 |
| 同策略重叠 | 19 条子域规则已被前面的父域同策略规则覆盖；属于无策略冲突的冗余 |
| 相反策略遮蔽 | 未发现后置域名后缀规则被前置父域的相反策略覆盖 |

文件前部的 11 条 YouTube、YouTube Music、API 和视频资源 PROXY 规则位于 Google 通用 DIRECT 规则之前。俄罗斯银行、支付、政府、大学、教育、运营商、交通、电商、媒体及中国服务有显式 DIRECT 规则。后部依次为俄中地区域名 DIRECT、局域网规则、`GEOIP,RU` / `GEOIP,CN` DIRECT，最后是 `FINAL,PROXY`。

通用设置为 `bypass-system = true`、局域网跳过列表、`dns-server = system`、`ipv6 = false`。文件没有配置专用加密 DNS。检查可见文本时，未发现私人节点、口令、令牌、私人订阅 URL、远程规则或脚本 URL；没有代理节点或 MITM 配置段。这是本文件的有限检查结果，不能作为无敏感信息的全面保证。

**已知限制：** `ggpht.com` 与 `www.googleapis.com` 会匹配 DIRECT；YouTube 与 Google 可能共享这些域名上的资源或接口，域名规则不能按业务路径完整隔离。Google 官方 [YouTube Data API 文档](https://developers.google.com/youtube/v3/docs)列出的共享主机即为 `www.googleapis.com`。不能据此声称全部 YouTube 请求都会代理。

**未测试：** Shadowrocket 实际导入、当前客户端兼容性、代理节点连接、俄罗斯运营商网络、DNS 行为、GEOIP 数据库准确性、网站与 App 的完整功能。规则顺序与数量的静态核对不代表服务可达或运行测试通过。

[返回中文 README](../README.zh-CN.md)

<a id="ru"></a>

## Русский

**Исходный профиль Russia прошёл статическую проверку; копия для публикации сохранена без изменений.** Отчёт относится только к файлу с указанным хешем. Китайские сервисы направляются через DIRECT; отдельного профиля для использования в Китае в этом репозитории нет.

| Проверка | Результат |
| :--- | :--- |
| Структура | `[General]`, `[Rule]`; 4 общих параметра |
| Число правил | **340** непустых строк правил без комментариев; это не число сервисов |
| Типы | 333 `DOMAIN-SUFFIX`, 4 `IP-CIDR`, 2 `GEOIP`, 1 `FINAL` |
| Маршруты | 291 DIRECT; 49 PROXY, включая `FINAL,PROXY` |
| Базовая проверка структуры | Не выявлены неизвестные типы, неверное число полей или некорректные IPv4-подсети; это не проверка парсером приложения |
| Точные повторы | Не обнаружены |
| Пересечения с тем же маршрутом | 19 правил поддоменов уже охвачены более ранними правилами родительских доменов; конфликта маршрутов нет |
| Перекрытие противоположным маршрутом | Не обнаружено поздних правил суффиксов, перекрытых более ранним родительским суффиксом с противоположной политикой |

Первые 11 правил PROXY для YouTube, YouTube Music, API и медиаресурсов стоят перед общими правилами Google DIRECT. Присутствуют отдельные DIRECT-правила для российских банков, платежей, государственных сервисов, вузов, образования, операторов, транспорта, торговли, медиа и китайских сервисов. Затем следуют региональные доменные зоны России и Китая, локальные сети, `GEOIP,RU` / `GEOIP,CN` DIRECT и завершающее `FINAL,PROXY`.

Общие параметры: `bypass-system = true`, список обхода для локальных адресов, `dns-server = system`, `ipv6 = false`. Отдельный зашифрованный DNS не настроен. В просмотренном тексте не обнаружены личные узлы, пароли, токены, приватные подписки, URL удалённых правил или скриптов; разделов с прокси-узлами или MITM нет. Это ограниченный результат проверки данного файла, а не полная гарантия отсутствия чувствительных данных.

**Ограничения:** `ggpht.com` и `www.googleapis.com` попадают под DIRECT. Google и YouTube могут использовать общие ресурсы и API на этих доменах; доменные правила не разделяют все пути. Официальная [документация YouTube Data API](https://developers.google.com/youtube/v3/docs) указывает общий хост `www.googleapis.com`. Нельзя утверждать, что все запросы YouTube направляются через прокси.

**Не проверены:** импорт в Shadowrocket, совместимость с текущим клиентом, соединение с узлом, российские сети, поведение DNS, точность базы GEOIP и полная работа сайтов и приложений. Статическая проверка не подтверждает доступность сервисов или успешную работу конфигурации.

[Вернуться к русскому README](../README.ru.md)

<a id="en"></a>

## English

**The original Russia profile has been statically reviewed; the publication copy is unchanged.** This report applies only to the file identified by the hash above. Chinese services use DIRECT; this repository does not provide a separate profile for use in China.

| Check | Result |
| :--- | :--- |
| Structure | `[General]`, `[Rule]`; 4 general settings |
| Rule count | **340** nonblank, noncomment rule lines; not 340 services |
| Rule types | 333 `DOMAIN-SUFFIX`, 4 `IP-CIDR`, 2 `GEOIP`, 1 `FINAL` |
| Policies | 291 DIRECT; 49 PROXY, including `FINAL,PROXY` |
| Basic structural checks | No unknown rule types, unexpected field counts, or invalid IPv4 subnets found; not validation by the app parser |
| Exact duplicates | None found |
| Same-policy overlaps | 19 child-domain rules already covered by earlier parent-domain rules; redundant without conflicting policies |
| Opposite-policy shadowing | No later domain-suffix rule found hidden by an earlier parent suffix with the opposite policy |

The first 11 PROXY rules for YouTube, YouTube Music, APIs, and media resources precede broader Google DIRECT rules. Explicit DIRECT entries cover Russian banks, payments, government services, universities, education, operators, transport, retail, media, and Chinese services. Regional Russian and Chinese suffixes follow, then local networks, `GEOIP,RU` / `GEOIP,CN` DIRECT, and finally `FINAL,PROXY`.

General settings are `bypass-system = true`, a local-address bypass list, `dns-server = system`, and `ipv6 = false`. No dedicated encrypted DNS is configured. Inspection of the visible text found no private nodes, passwords, tokens, private subscription URLs, remote rule URLs, or script URLs; there are no proxy-node or MITM sections. This limited check is not a comprehensive guarantee that the file contains no sensitive information.

**Known limits:** `ggpht.com` and `www.googleapis.com` match DIRECT. Google and YouTube may share resources or APIs on those domains, and domain rules cannot separate every application path. Google's [YouTube Data API reference](https://developers.google.com/youtube/v3/docs) identifies the shared host `www.googleapis.com`. Complete proxy routing of all YouTube requests is not established.

**Not tested:** actual Shadowrocket import, current client compatibility, node connectivity, Russian ISP networks, DNS behavior, GEOIP database accuracy, and complete website or app functionality. Static rule counts and ordering do not establish service availability or successful runtime operation.

[Back to English README](../README.md)
