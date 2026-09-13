# 第三方数据与服务 / Third-Party Data and Services

## DB-IP City Lite

**IP Geolocation by DB-IP** — [db-ip.com](https://db-ip.com/)

随完整包附带的 2026 年 9 月 City Lite 数据库来自 DB-IP，许可为 [Creative Commons Attribution 4.0 International（CC BY 4.0）](https://creativecommons.org/licenses/by/4.0/)。数据库未修改，界面优先使用可用的中文名称。IP 地址只能提供近似网络位置，不保证城市级精度或实时性。

The complete package includes the September 2026 DB-IP City Lite database under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). The database is unmodified, and the UI prefers Chinese names when available. IP addresses provide only approximate network locations; city-level accuracy and real-time coverage are not guaranteed.

[官方下载与格式说明 / Official downloads and formats](https://db-ip.com/db/download/ip-to-city-lite)

## Natural Earth

**Made with Natural Earth** — [naturalearthdata.com](https://www.naturalearthdata.com/)

世界底图采用 Natural Earth 1:110m 国家轮廓数据，属于公共领域。地图用于网络来源示意，不用于边界裁定，也不表示设备的精确位置。

The basemap uses Natural Earth 1:110m country outlines, which are in the public domain. It illustrates network sources and is not intended for boundary determination or precise device positioning.

[数据使用说明 / Terms of use](https://www.naturalearthdata.com/about/terms-of-use/) · [数据源 / Dataset](https://github.com/nvkelso/natural-earth-vector/blob/master/geojson/ne_110m_admin_0_countries.geojson)

## 出口 IP 回显服务 / Outbound IP echo services

本机出口检测优先使用 `ipv4.icanhazip.com` 和 `myip.ipip.net`，备用服务为 [ipify](https://www.ipify.org/) 与 [ident.me](https://api.ident.me/)。这些请求只用于获取本次连接的出口地址，不提交入站日志。服务可用性受网络环境及各提供方政策影响，程序与这些提供方不存在背书关系。

Outbound IP detection first uses `ipv4.icanhazip.com` and `myip.ipip.net`, with [ipify](https://www.ipify.org/) and [ident.me](https://api.ident.me/) as alternatives. These requests obtain the address of the outbound connection and do not submit inbound logs. Availability depends on network conditions and each provider's policies. The application is not endorsed by these providers.

MMDB 文件格式说明 / MMDB file format: [MaxMind DB specification](https://maxmind.github.io/MaxMind-DB/).
