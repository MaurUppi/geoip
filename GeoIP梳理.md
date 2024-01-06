# GeoIP技术概述

**GeoIP**，或称**IP地理定位技术**，是一种通过分析互联网用户的**IP地址**来确定其大致地理位置的技术。这种技术依赖于一个庞大、不断更新的数据库，记录了各个IP地址与地理位置之间的对应关系。知名服务商如 **MaxMind**、**DB-IP** 和 **ipinfo** 等提供这种数据库的访问和查询服务。

## 主要目的和用途

1. **市场策略和内容定制**
   - 企业和网站管理员可以了解用户的地理分布，制定更加针对性的市场策略和内容。
   - 例如，在线零售商可以根据用户位置展示相应的货币和语言，甚至推荐特定区域的产品。

2. **网络安全**
   - 通过识别来自特定地区的流量，有效防范来自高风险地区的潜在网络攻击。
   - 例如，拒绝来自某些国家的访问请求。

3. **合规性监管**
   - 特别是内容分发和版权受限的媒体服务，需要根据用户所在地的法律法规调整内容提供。
   - 例如，确保视频或音乐服务遵守各地的版权法规。

## 小结

GeoIP技术对于**提升用户体验**、**保障网络安全**以及**确保法律合规性**等方面具有重要意义。随着全球互联网的发展，这种技术的应用将更加广泛和深入。

# 主要GeoIP数据库格式及其区别

GeoIP数据库提供商，如MaxMind、DB-IP等，通常提供多种格式的数据库。这些格式包括但不限于以下几种：

## 1. CSV格式
- **描述**：逗号分隔值（CSV）格式，是一种简单的文本格式，用于存储表格数据。
- **优点**：易于阅读和编辑，可以使用任何文本编辑器或表格处理软件（如Microsoft Excel）打开。
- **缺点**：文件大小通常较大，处理速度可能不如其他格式快。

## 2. MMDB格式 [Specification](https://maxmind.github.io/MaxMind-DB/)
- **描述**：MaxMind首先设计的GeoIP数据库格式，用于GeoIP数据库。
- **优点**：为快速查询而优化，体积相对较小，查询速度快。
- **缺点**：需要专门的解析库或工具来读取，不如CSV格式通用。

### 2.1 MaxMind MMDB
- **数据结构**：使用嵌套数据格式，可能使查询复杂。
- **数据量**：每行数据包含多个翻译，导致数据行较大。

### 2.2 IPinfo MMDB
- **数据结构**：扁平和表格化，提高查询效率。
- **数据库种类**：提供ASN、隐私检测和托管域名等特色数据库。
- **数据格式**：更简单、直接的输出。
- **定制化**：根据客户需求提供定制数据库版本。
- 

## 3. JSON格式
- **描述**：JavaScript对象表示法（JSON）是一种轻量级的数据交换格式。
- **优点**：格式清晰，易于人类阅读和编写，同时也易于机器解析和生成。
- **缺点**：文件大小可能较大，解析速度可能不如二进制格式快。

## 4. XML格式
- **描述**：扩展标记语言（XML）是一种标记语言，用于存储和传输数据。
- **优点**：结构清晰，可扩展性强，被广泛支持。
- **缺点**：文件较大，解析复杂度高，性能较JSON和二进制格式差。

## 5. 二进制格式
- **描述**：专为速度和效率优化的格式，通常为提供商定制。
- **优点**：查询速度快，文件体积小。
- **缺点**：不易于阅读和编辑，需要特定的工具来处理。
- **范例**： https://github.com/rabuchaim/geoip2fast

## 小结
这些格式各有优劣，选择哪种格式取决于特定应用的需求。例如，需要高速查询的应用可能会倾向于使用MMDB或其他二进制格式，而需要人工编辑或查看数据的场景可能更适合CSV或JSON格式。

# 海外主流GeoIP服务商/社区

1. **[MaxMind](https://www.maxmind.com/)** 提供广泛使用的GeoIP数据库和服务。
   - 提供Lite、Commercial许可的离线数据库
   - 需要注册使用API key方式下载
   - Lite 两周更新频率
   - Lite许可：[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

2. **[IPinfo](https://ipinfo.io/)** 以其API服务和定制数据库而知名。
   - 提供Free、Commercial许可的离线数据库
   - Free 版：`IP to ASN`、`IP to Country`、`IP to Country + IP to ASN`
   - 可以申请API Key，便于使用URL方式直接访问
   - 或者访问[cnartlu/geoip2](https://github.com/cnartlu/geoip2/releases) 自动化下载ipinfo.io的免费版数据文件，执行时间段为每日的 3.30 11.30 19.30

3. **[DB-IP](https://db-ip.com/)** 提供IP地址数据库和相关服务。
   - 提供Lite、Commercial许可的离线数据库
   - Lite 月度更新频率
   - **不**需要注册，需要手动点击checkbox接受协议，才可以下载
   - **或访问 [MaurUppi/Downloader for DB-IP.com Databases](https://github.com/MaurUppi/downloader)， 可以直接下载**，自动检查频率为 每日的 1:00，DP-IP有更新就有Release
   - Lite许可：[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

4. **[IP2Location](https://www.ip2location.com/)** 另一家提供GeoIP服务和数据的公司。
   - Is an open source geolocation database with limited accuracy.
   - Lite 版[入口](https://lite.ip2location.com/login)
   - Lite 版提供`IP2Location Database`, `IP2Proxy Database`, `ASN Database`
   - Lite `IP2Location Database` 能够提供到的最详细版本: IP-COUNTRY-REGION-CITY-LATITUDE-LONGITUDE-ZIPCODE-TIMEZONE

5. **[ip-api.com](https://ip-api.com/)** 仅提供web接口
   - 提供Free、Pro、Enterprise的服务/数据级别
   - Free不需要API Key即可访问，但是限制每分钟45次访问

6. **其它公开服务** 仅提供部分的公开信息
   - [OpenGeoFeed](https://opengeofeed.org/) 
   - [RouteViews](https://www.routeviews.org/routeviews/): AS number from ipv4 address [Update: every 2 hours]
   - [IPtoASN](https://iptoasn.com/)  [Update: Hourly]
   - [ip-location-db](https://github.com/sapics/ip-location-db) [资源整合]
   - [IPFire Firewall](https://www.ipfire.org/) maintains a [geoip database in a custom format](https://git.ipfire.org/?p=location/location-database.git;a=summary), which notably includes IP categorization, such as is-anycast.


# 中国大陆GeoIP服务商/社区

1. **[IPIP.net](https://www.ipip.net/)**
   - 提供IP地址的地理位置、运营商信息等商用服务。
   - 社区版：[china_ip_list](https://github.com/17mon/china_ip_list)
   - 社区版 一般每季度更新一次
   - 社区版 许可：[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

2. **[纯真网络](https://cz88.net/)**
   - 提供IP地址查询服务，包括地理位置和运营商信息。
   - 提供商用服务，也有社区离线版

3. **百度地图API**
   - 提供IP定位服务，适用于网站和移动应用。

4. **高德地图API**
   - 提供IP定位功能，适用于多种应用场景。

5. **腾讯位置服务**
   - 提供基于IP的位置服务，支持多种开发平台。

6. **苍狼山庄** 不是服务商，但是知名的社区。 第一手数据，**每日**更新
   - [ISP IP地址](https://ispip.clang.cn/)
   - 每日更新的电信IP段,联通IP段,移动IP段,铁通IP段,教育网IP段,长城宽带/鹏博士IP段,ISP IP
   - 自动生成脚本下载地址：https://soft.clang.cn/ispip/

7. **[IP 地址库](https://github.com/metowolf/iplist/)** 第一手数据，**每周**更新
   - IP CIDRs List / IP 地址列表
   - 数据基于 纯真社区版 `离线数据库`分类
   - 每周 [metowolf/qqwry.ipdb](https://github.com/metowolf/qqwry.ipdb) 版本随 [metowolf/qqwry.dat](https://github.com/metowolf/qqwry.dat) 上游同步更新
   - 多被使用的资源：[中国 (CN) IPv4](https://raw.githubusercontent.com/metowolf/iplist/master/data/country/CN.txt)

8. **[中国运营商IP地址库](https://github.com/gaoyifan/china-operator-ip/)** 第一手数据，**每日**更新
   - 中国运营商IPv4/IPv6地址库-每日更新 [统计信息](https://github.com/gaoyifan/china-operator-ip/blob/ip-lists/stat)
   - > 在国内，BGP/ASN数据分析的商业服务只有一个ipip.net，是目前运营商IP库准确度最高的服务商，我认为没有之一
   - IP列表（CIDR格式）
   - 多被使用的资源：[china.txt IPv4](https://github.com/gaoyifan/china-operator-ip/blob/ip-lists/china.txt), [china6.txt IPv6](https://github.com/gaoyifan/china-operator-ip/blob/ip-lists/china6.txt)

9. **其它我没太搞明白的**，但应该也是第一手数据
   - [chnroutes2](https://github.com/misakaio/chnroutes2)， **每小时**更新
     - 数据格式：[mmdb](https://raw.githubusercontent.com/misakaio/chnroutes2/master/chnroutes.mmdb). [txt](https://raw.githubusercontent.com/misakaio/chnroutes2/master/chnroutes.txt)
     - This project uses BGP feed from various sources to provide more accurate and up-to-date CN routes.
     - We update it **hourly** from our route collector.
     - licensed under [CC-BY-SA](https://creativecommons.org/licenses/by-sa/2.0/).
   - [nchnroutes](https://github.com/dndx/nchnroutes) <-- 最近更新是三年前
     - Similar to chnroutes, but instead generates routes that are **not** originating from Mainland China and generates result in BIRD static route format
     - Both IPv4 and IPv6 are supported.

# 基础工具Toolbox（这是后边资源整合的基础）

1. **MaxMind Official resources**
   - [Official Client APIs](https://dev.maxmind.com/geoip/docs/databases#client-apis)
   - [Developed libraries](https://github.com/maxmind)

2. **[DB-IP API is exposed via RESTful](https://db-ip.com/api/doc.php)**

3. **[GeoIP2 Reader for Go](github.com/oschwald/geoip2-golang)** 其它语言的实现版本不一一列举了。
   - 支持MaxMind、DB-IP的mmdb格式，Lite及Commercial版本
   - [func getDBType](https://github.com/oschwald/geoip2-golang/blob/fbe22892b33824e127ef49e61e84812d8d5497a6/reader.go#L277-L313)

4. **[Build your own GeoIP .mmdb!](https://github.com/safing/mmdbmeld)**
   - 输入格式：CSV
   - 输出格式：MMDB
   - [config-example.yml](https://github.com/safing/mmdbmeld/blob/master/config-example.yml)
   - Earlier entries are overwritten by later entries.


# 资源整合方案

1. **[ip-location-db](https://github.com/sapics/ip-location-db)**
   - ip to location database by ASN, GeoFeed, Whois, iptoasn.com, db-ip lite, GeoLite2
   - CSV 格式

2. **[IP Geolocation DB](https://github.com/HostByBelle/IP-Geolocation-DB)**
   - IP Geolocation DBs automatically built into the mmdb format **daily**
   - mmdb 格式

3. **[alecthw/mmdb_china_ip_list](https://github.com/alecthw/mmdb_china_ip_list)**
   - 这个是Openclash的GeoIP更新功能，内置的数据源之一
   - 输入：
     - `china_ip_list`、`纯真CN`、`Clang.CN`和`ali AS37963`发布的中国IP列表
     - 还有 [blackmatrix7/ios_rule_script/CloudCN.list](https://github.com/alecthw/mmdb_china_ip_list/blob/af13b4ce17ea596363b629407dc11b0231ca5a55/.github/workflows/daily-build.yml#L78-L81)
     - 包含 IPv4、IPv6（Clang）
     - **叠加到** MaxMind官方Lite（社区版）`Country.mmdb`数据库。
   - 输出：MaxMind `Country.mmdb`、`Country.mmdb lite` 

4. **[Loyalsoldier/geoip](https://github.com/Loyalsoldier/geoip)**
   - 估计不少这个应该用人不少
   - 输入：
     - `IPIP.net 社区版`、`中国运营商IP地址库（gaoyifan/china-operator-ip）` 包含 IPv4、IPv6
     - `gstatic IPv4/v6`、`fastly IPv4/v6`、`cloudfront IPv4/v6`、`cloudflare IPv4/v6`、`telegram IPv4/v6`、`netflix` CIDRs，[来源代码](https://github.com/Loyalsoldier/geoip/blob/bf51d6afac442fec800bb15f2d7545a1e3bba262/.github/workflows/build.yml#L41-L46C197)
     - MaxMind官方Lite（社区版）`GeoLite2-Country-Locations-en.csv`、`GeoLite2-Country-Blocks-IPv4.csv`、`GeoLite2-Country-Blocks-IPv6.csv` 数据库。
   - 输出：MaxMind `Country.mmdb`以及 V2Ray dat `geoip.dat`
     - `geoip:netflix（GEOIP,NETFLIX）`、`geoip:twitter（GEOIP,TWITTER）` 对应的CIDRs是怎么来的，还没有搞懂。

5. **[JohnnySun/geoip](https://github.com/JohnnySun/geoip)**
   - 上游是[Loyalsoldier/geoip]
   - 替换MaxMind `GeoLite2-Country.mmdb` 为 IPInfo.io 的 `Free IP to Country` 数据库
   - **注意** ipinfo的mmdb和MaxMind的mmdb有差异，Johnny做了改动的。

6. **[zealic/autorosvpn](https://github.com/zealic/autorosvpn)**
   - 利用 China IP address list (chnroutes.txt) 为 **RouterOS** 生成类似 `GeoIP:CN` 的列表。

7. **[PaPerseller/chn-iplist](https://github.com/PaPerseller/chn-iplist)**
   - 利用 **Chnroutes rules** 生成符合 routers、Shadowrocket、Quantumult、acl、v2rayNG、v2rayN、pac、Qv2ray、SagerNet、v2rayA、RouterOS、sing-box、v2ray config file.的可用信息
   - 数据源也是 [IPIP.net 社区版 china_ip_list](https://github.com/17mon/china_ip_list)、[中国运营商IP地址库](https://github.com/gaoyifan/china-operator-ip/)


# 推荐用哪个？

## 不打算买商用数据库/服务的，只(bai)能(piao)是用GitHub资源

1. **自己从零构建**
   - 这没啥好说，原材料都给你了，你各自捣鼓就好。

2. **复用MaxMind、DB-IP、IPINFO等官方资源**
   - 这也没啥好说的，上边都列给你了。

3. **资源整合方案用哪个**
   - 这个恐怕得根据你用到什么地方，例如Clash、Surge、V2ray还是其它例如RouterOS
   - 但基于最近的研究与使用体验，我的意见
     
      | 类型 | 数据库 | 文件大小 |
    	|-----|-----|-----|
    	| **Country level**   |我**倾向**使用ipinfo.io数据源         |
    	| MaxMind    | GeoLite2-Country_20231222.mmdb    |6.02 MB (6,320,117 bytes)     |
    	| IPINFO.io  | Free IP to Country.mmdb Jan 05, 2024     |31.7 MB (33,267,411 bytes)     |
    	| DB-IP.com     |dbip-country-lite-2023-12.mmdb     |7.44 MB (7,811,137 bytes)     |
    	| **City level**    |我**推荐**DB-IP.com          |
    	| MaxMind      |GeoLite2-City.mmdb     |66.3 MB (69,591,332 bytes)     |
      | DB-IP.com    |dbip-city-lite-2023-12.mmdb | 93.0 MB (97,576,399 bytes) |

4. **City Level 信息准确度的对比**
   - 查询同样一个IP `89.160.20.128` 返回的经纬度
     - dp-ip city-lite 返回 `59.3293,18.0686`
     
       ![89 160 20 128_dp-ip](https://github.com/MaurUppi/geoip/assets/47710598/98764edc-06f1-4661-bd17-bbe0344b424f)

     - MaxMind GeoLite2-City 返回 `59.3247,18.056`
     
       ![89 160 20 128_GeoLite2](https://github.com/MaurUppi/geoip/assets/47710598/dff32ab3-0b61-43c3-bb54-998f556d8c05)

   - 查询另外一个IP `103.167.135.39`
     - dp-ip city-lite 返回 `22.2782,114.176` 并显示城市 Wan Chai (下图路线右上的点）
     - MaxMind GeoLite2-City 返回 `22.2578,114.1657` 没有城市信息，，，（中下部箭头所指位置）
    
       ![103 167 135 39](https://github.com/MaurUppi/geoip/assets/47710598/66b9009d-311b-4e98-97f9-32e2f026a330)

       
# TODO 

- City Level的整合版
   - **dp-ip city-lite** 作为海外数据源
   - **国内数据整合**
     - [xiangyuecn/AreaCity-JsSpider-StatsGov](https://github.com/xiangyuecn/AreaCity-JsSpider-StatsGov)
       - 提供城市中心经纬度
     - [IP 地址库 - 市级 IP 段](https://github.com/metowolf/iplist?tab=readme-ov-file#%E5%B8%82%E7%BA%A7-ip-%E6%AE%B5)
       - 提供城市级别 IP 段
