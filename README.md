# Loonforme — 个人融合版 Loon 配置

curtinp118 干净骨架 + Nitmi 细分组的个人 Loon 配置。

## 导入地址

```
https://raw.githubusercontent.com/Yip1nd/Loonforme/main/Loon_Fusion.conf
```

国内拉取慢可用 jsdelivr 镜像：

```
https://cdn.jsdelivr.net/gh/Yip1nd/Loonforme@main/Loon_Fusion.conf
```

Loon → 配置 → 从 URL 下载配置 → 粘贴上面地址 → 启用。

## 说明

- 49 个策略组：ChatGPT / Copilot / Claude / AI 分开，TikTok、Netflix、Disney+、HBO、PrimeVideo、境外电商、PT、测速均有专属组
- 广告规则在远程规则第一位，国内 CN 规则最后兜底
- SSID 场景切换：指定 WiFi 自动直连，蜂窝数据自动规则分流（配置里把 `YOUR_WIFI_NAME` 换成你家 WiFi 名）
- 插件默认只开 2 个（Block_HTTPDNS、BlockAdvertisers）
- App 级规则直接引用 [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script) 的 Loon 规则（33 条），GeoSite 仅作分类兜底；溯源见 [SOURCES.md](SOURCES.md)
- 本仓库不含任何订阅链接和节点信息，订阅请在 Loon 本地添加

## 致谢

基于 [curtinp118/Loon](https://github.com/curtinp118/Loon) 与 [Nitmi/Nitmi_Rules](https://github.com/Nitmi/Nitmi_Rules)，规则主要来自 blackmatrix7/ios_rule_script 与 GeoSite。
