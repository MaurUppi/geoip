# 感谢 

本项目持续修改中，主要目的是使用原项目对于mmdb的融合能力，但我不打算用MaxMind的Country数据库，虽然是daily更新频率。
我打算用db-ip的 [ip-to-country-lite](https://db-ip.com/db/download/ip-to-country-lite)。缺点是Monthly更新频率，优点是数据准确度比MaxMind要高不少。

使用了 Loyalsoldier 的 [Geoip 项目](https://github.com/Loyalsoldier/geoip) 以及其它贡献者
请跳转阅读 原版 [README.md](https://github.com/Loyalsoldier/geoip/blob/master/README.md)



## （原版）简介

本项目每周四自动生成 GeoIP 文件，同时提供命令行界面（CLI）供用户自行定制 GeoIP 文件，包括但不限于 V2Ray dat 格式路由规则文件 `geoip.dat` 和 MaxMind mmdb 格式文件 `Country.mmdb`。

This project releases GeoIP files automatically every Thursday. It also provides a command line interface(CLI) for users to customize their own GeoIP files, included but not limited to V2Ray dat format file `geoip.dat` and MaxMind mmdb format file `Country.mmdb`.

## 与官方版 GeoIP 的区别

- 中国大陆 IPv4 地址数据融合了 [IPIP.net](https://github.com/17mon/china_ip_list/blob/master/china_ip_list.txt) 和 [@gaoyifan/china-operator-ip](https://github.com/gaoyifan/china-operator-ip/blob/ip-lists/china.txt)
- 中国大陆 IPv6 地址数据融合了 MaxMind GeoLite2 和 [@gaoyifan/china-operator-ip](https://github.com/gaoyifan/china-operator-ip/blob/ip-lists/china6.txt)
- 新增类别（方便有特殊需求的用户使用）：
  - `geoip:cloudflare`（`GEOIP,CLOUDFLARE`）
  - `geoip:cloudfront`（`GEOIP,CLOUDFRONT`）
  - `geoip:facebook`（`GEOIP,FACEBOOK`）
  - `geoip:fastly`（`GEOIP,FASTLY`）
  - `geoip:google`（`GEOIP,GOOGLE`）
  - `geoip:netflix`（`GEOIP,NETFLIX`）
  - `geoip:telegram`（`GEOIP,TELEGRAM`）
  - `geoip:twitter`（`GEOIP,TWITTER`）

## 下载地址

> 如果无法访问域名 `raw.githubusercontent.com`，可以使用第二个地址 `cdn.jsdelivr.net`。
> *.sha256sum 为校验文件。

### MaxMind mmdb 格式文件

> 适用于 [Clash](https://github.com/Dreamacro/clash) 和 [Leaf](https://github.com/eycorsican/leaf)。

- **Country.mmdb**：
  - [https://raw.githubusercontent.com/OUZYcn/geoip/release/Country.mmdb](https://raw.githubusercontent.com/OUZYcn/geoip/release/Country.mmdb)
  - [https://cdn.jsdelivr.net/gh/OUZYcn/geoip@release/Country.mmdb](https://cdn.jsdelivr.net/gh/OUZYcn/geoip@release/Country.mmdb)


## License

[CC-BY-SA-4.0](https://creativecommons.org/licenses/by-sa/4.0/)

This product includes GeoLite2 data created by MaxMind, available from [MaxMind](http://www.maxmind.com).

