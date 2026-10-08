<div align="center">

[简体中文](README.zh-CN.md) · [Русский](README.ru.md) · **English**

<img src="assets/banner.svg?v=1.0-beta" width="100%" alt="Shadowrocket RU-CN routing rules — Russia v1.0 Beta" />

# Shadowrocket-RU-CN-Routing

**For Russian networks · Local services direct · YouTube proxy rules**

An experimental Shadowrocket configuration for use on Russian networks.

**Russia v1.0 Beta · 340 rules · [MIT License](LICENSE)**

[Overview](#overview) · [Routing](#routing) · [Get started](#quick-start) · [Beta notes](#beta) · [Contribute](#contributing) · [Legal & donations](#support)

</div>

---

> [!IMPORTANT]
> **The public repository is live.** The Russia v1.0 Beta profile preserves the supplied routing rules; only its version comment is updated to v1.0 Beta. The configuration file is [Russia.conf](configs/Russia.conf). Its 340 rules have been checked statically; no Shadowrocket runtime or Russian-network testing has been performed. Use the active Raw link below to fetch the file.

<a id="overview"></a>

## What is this project for?

This is a Shadowrocket routing configuration for people **using the internet in Russia who already have their own proxy node or subscription**. It lets you proxy selected international traffic while keeping common Russian and Chinese services on direct connections when your proxy is on.

Russia v1.0 Beta sends listed Russian banks, payment services, government sites, universities, mobile operators, transport, shopping, and media, plus listed Chinese services such as WeChat, Alipay, and Taobao, through **DIRECT**. General Google domains also use DIRECT. YouTube, YouTube Music, X, Instagram, Telegram, and other listed proxy exceptions use **PROXY**. Traffic not matched by earlier domain or regional rules reaches `FINAL,PROXY`.

**DIRECT** uses your normal network connection. **PROXY** uses the node you select in Shadowrocket. This project supplies routing rules; it does not provide a VPN service, proxy nodes, or node subscriptions.

This repository contains the Russia profile only. Its Chinese-service DIRECT rules are part of that Russia profile; the China-mode configuration will be maintained and open-sourced separately by its author.

<a id="routing"></a>

## Routing at a glance

The table describes the rules in the included configuration. It does not guarantee actual service availability.

| Traffic | Russia profile |
| :--- | :---: |
| Russian banks and payment services | **DIRECT** |
| Russian government services and universities | **DIRECT** |
| Russian operators, shopping, transport, education, and media | **DIRECT** |
| Chinese services | **DIRECT** |
| Google services other than YouTube | **DIRECT** |
| YouTube, YouTube Music, and associated `googlevideo` traffic | **PROXY** |
| Otherwise unmatched traffic | **PROXY** (`FINAL,PROXY`) |

The Google direct policy in the Russia configuration covers domains associated with Search, Gmail, Maps, Drive, Translate, Photos, and Play. This is a routing policy, not confirmation that each application works on every network.

### Russia: detailed local routing

The Russia profile lists Russian service domains explicitly by category: banks, payments, government, universities, operators, shopping, transport, education, and media. Broader `.ru`, `.su`, and `.рф` (`xn--p1ai`) domain rules, followed by Russian and Chinese IP geolocation rules (`GEOIP,RU` and `GEOIP,CN`), provide **DIRECT** regional fallbacks.

These categories do not imply exhaustive coverage. Country domains and IP geolocation cannot identify every service or guarantee access.

### Rule order matters

Specific proxy exceptions—including YouTube and its media delivery domains—appear **before** broader Google direct rules and regional fallbacks in the included file. Static checks confirmed this critical ordering. Preserve it when editing: an earlier broad match can send traffic along the wrong route. Otherwise unmatched traffic uses `FINAL,PROXY`.

Some Google domains are shared by several applications. In the original configuration, `ggpht.com` and `www.googleapis.com` inherit **DIRECT**, so complete separation of every YouTube request is not guaranteed.

### What has been checked

Static inspection counted **340 rules**: 333 `DOMAIN-SUFFIX`, 4 `IP-CIDR`, 2 `GEOIP`, and 1 `FINAL`; 291 rules select `DIRECT` and 49 select `PROXY`. No exact duplicate rules, credentials, or proxy-node sections were found. These checks do not establish Shadowrocket compatibility or live connectivity. See the [validation report](docs/VALIDATION.md#en) for scope and limitations.

<a id="quick-start"></a>

## Configuration downloads & setup

**The Russia Beta file is included and ready for local import and testing.** Check the [configuration status](configs/README.md#en) before use. Maintainers can use the [Chinese maintenance guide](PUBLISHING.md) for release and update notes.

| File | Purpose | Availability |
| :--- | :--- | :--- |
| [⬇ Download Russia.conf](https://github.com/Emptydesire/Shadowrocket-RU-CN-Routing/releases/download/v1.0-beta/Russia.conf) | Russia v1.0 Beta attachment | Included; client and network testing pending |

### Import the included Russia Beta

1. Back up your current Shadowrocket configuration and any local edits.
2. Locate [configs/Russia.conf](configs/Russia.conf) in this package. Its routing rules match the supplied file; only the version comment is updated to v1.0 Beta.
3. In Shadowrocket's configuration area, import the local `.conf` file. Interface labels may vary by app version; this import has not been tested in the client.
4. Select the imported profile, use configuration-based routing, and select your own working proxy node.
5. Check a local service, a Google service, and YouTube to confirm that the intended routes work on your network.

For reference, see [GitHub's guide to copying Raw file content](https://docs.github.com/en/repositories/working-with-files/using-files/viewing-and-understanding-files#viewing-or-copying-the-raw-file-content) and the [developer's Shadowrocket listing](https://apps.apple.com/us/app/shadowrocket/id932747118), which describes configuration imports by URL.

### Remote configuration

Download the `.conf` file or add its **Raw** URL in Shadowrocket's configuration area.

This is the active Raw URL for the `main` branch:

```text
https://raw.githubusercontent.com/Emptydesire/Shadowrocket-RU-CN-Routing/main/configs/Russia.conf
```

A configuration URL supplies routing settings; **it is not a proxy-node subscription**. Import your node subscription separately if needed. A branch URL can change as maintainers update it; a commit URL pins one revision. Whether and when remote configurations refresh depends on your client settings. Updates may overwrite local edits, so keep a backup.

<a id="beta"></a>

## Beta notes

Russia v1.0 Beta has **not been tested in Shadowrocket or on Russian networks** during preparation of this package. The included configuration received static inspection only; it is preserved unchanged from the user-supplied source.

- Availability and routing can vary by operator, network restrictions, DNS behavior, application version, and proxy node.
- `DIRECT` expresses a route choice; it does not guarantee that a site will load. In particular, direct access to Google services may fail on some Russian networks.
- A working proxy node is required for `PROXY` traffic. No connectivity, speed, or service-coverage guarantee is provided.
- Review configuration changes before updating, and keep a known working configuration available for rollback.

<a id="contributing"></a>

## Maintenance & contributions

Domain changes, missing services, and routing mistakes are useful reports. Open an issue or pull request with the configuration version, domain, expected route, observed behavior, and enough context to reproduce the problem. Include the app version and network type; sharing an approximate region or operator is optional.

**Remove secrets before sharing evidence:** node credentials, subscription tokens, private configuration URLs, account identifiers, and unrelated browsing history must not appear in issues, screenshots, or logs.

Keep changes focused, explain why a routing decision is needed, and check rule ordering for unintended matches. Update all three language READMEs when behavior changes, clearly distinguish tested behavior from proposed changes, and preserve source attribution. See [CONTRIBUTING.md](CONTRIBUTING.md#en) for the contribution checklist.

<a id="support"></a>

## Legal notice & voluntary donations

### Legal notice

This project is for educational and technical exchange only. It does not encourage, organize, or authorize unlawful or criminal conduct. Users are responsible for ensuring their use complies with applicable laws. Any unlawful or criminal activity independently carried out by a user using this project or its materials is that user's own conduct and does not represent the project or its developer; the user remains responsible for that conduct. Nothing in this notice excludes liability that cannot legally be excluded.

### Voluntary donations

If you wish to support project maintenance, voluntary donations are accepted **only in USDT or USDC** at the addresses below. A donation is not a purchase and does not guarantee any service or reward.

| Network | Address |
| :--- | :--- |
| **Ethereum (ETH)** | `0xba16652ff3fa0d5b726ce1bb97e9c28bc9bc5efc` |
| **BNB Chain** | `0xba16652ff3fa0d5b726ce1bb97e9c28bc9bc5efc` |
| **TRON Chain** | `TFaTEkxQFtF6SV67qhHgg4kPqwHU4ZQgyb` |

Before sending, confirm that the token matches the selected network and check the full recipient address carefully. Blockchain transfers generally cannot be reversed.

[Full notice in all three languages](SUPPORT.md#en)

<a id="license"></a>

## License

Project-authored content is provided under the [MIT License](LICENSE). Third-party rules and other incorporated material retain their original licenses and attribution requirements; importing them does not automatically relicense them under MIT.

This is an independent community project and is not affiliated with or endorsed by Shadowrocket or the services mentioned here.

---

<div align="center">

[简体中文](README.zh-CN.md) · [Русский](README.ru.md) · **English**

</div>
