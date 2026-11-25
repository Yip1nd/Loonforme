# Loonforme 规则溯源图（2026-11-25 核查，未推送）

结论：没有单一源头。Loonforme 的 50 条远程规则最终溯到三类源头：
(a) 社区域名库 v2fly/domain-list-community（PR 维护）
(b) IP 注册机构数据（APNIC 等 RIR）+ MaxMind GeoLite，经 Loyalsoldier/geoip 打包
(c) 个人手工收集（抓包 + 公开清单合并）：blackmatrix7、Nitmi、Aethersailor

## 按引用方拆

### 1. sleepstars.de GeoSite/GeoIP（约 40 条，占绝大多数）
- 形式：Sleepstars/Surge-Geosite-Enhance，基于 Cloudflare Workers 的转换服务
- 数据：Loyalsoldier 提供的 geosite/geoip 数据集，动态转换生成
- 再上游：GeoSite = v2fly/domain-list-community；GeoIP = RIR 分配数据 + Loyalsoldier 整理

### 2. blackmatrix7/ios_rule_script（3 条：Advertising、DouYin、XiaoHongShu）
- 仓库自述：「我们并不生产规则，我们只是开源规则的搬运工」「所有规则数据都来自互联网」
- 生成方式：程序把 source/ 目录下的手工源文件 + 外部清单合并，生成带统计头的文件
- Advertising.list：生成文件头 UPDATED 2026-10-28，总计 291,173 条（DOMAIN-SUFFIX 273,956），明显合并了大型外部广告清单
- DouYin.list：13 条，UPDATED 2025-06-06；XiaoHongShu.list：4 条，同期 —— 小型手工名单

### 3. Nitmi/Nitmi_Rules（6 条自制 list）
- Custom_Direct / Custom_Proxy 文件头明写「来自个人收集，收录 Geosite 尚未覆盖的域名」
- Claude.list：Nitmi 手写 DOMAIN-KEYWORD（claude / datadog / sift 等）
- GeoIP_CN.list：内容只有一行 GEOIP,CN —— 实际数据仍来自 GeoIP 数据库

### 4. Aethersailor/Custom_OpenClash_Rules（Steam_CDN 1 条）
- 文件头注明来源：dogfight360 博客知识库文章，更新日期 2024/8/9

### 5. 数据库文件（非规则）
- geoip-url：Masaiki/GeoIP2-CN（Country.mmdb）
- ipasn-url：P3TERX/GeoLite.mmdb（源头 MaxMind GeoLite2 ASN）

## 对「吸收」的含义
吸收 blackmatrix7 只是把一个搬运层搬回家；真正的根在 v2fly + Loyalsoldier。
若要自给自足，应优先考虑直接引用/镜像这两家，而不是中间聚合者。
