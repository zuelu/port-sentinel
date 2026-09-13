# 更新日志 / Changelog

## v1.3.1 — 2026-09-13

### 新增与改进 / Added and improved

- 本机出口 IPv4 直连检测：绑定物理网卡，两个服务回显一致后在地图显示近似本机位置。
  Direct outbound IPv4 detection: bind to a physical interface and place an approximate destination marker after two services agree.
- 支持手动刷新定位、定期更新、网络变化失效，以及无法确认时的非地理落点。
  Manual refresh, periodic checks, invalidation after network changes, and a non-geographic fallback when the location cannot be confirmed.
- 请求不使用系统、HTTP/SOCKS、PAC 或环境变量代理；不通过代理重试。
  Requests do not use system, HTTP/SOCKS, PAC, or environment-variable proxies and never fall back to a proxy.
- 封禁状态改为批量读取，减少规则较多时的等待；退出会取消后续对账和锁等待。
  Batch firewall-state reads reduce waiting with larger rule sets; exit cancels subsequent reconciliation and lock waits.
- 改善大屏小窗口布局和定位失败提示。
  Improved dashboard layout at smaller window sizes and clearer messages when location detection fails.

### 本版本功能 / Included in this release

实时入站端口监控、历史检索与 CSV 导出、按 IP 统计、离线地理位置、全球来源大屏、手动/自动 IP 封禁、黑白名单、限时解除、托盘运行、可选登录自启、分库保存、历史清理和备份。

Live inbound port monitoring, history search and CSV export, per-IP statistics, offline geolocation, a global source dashboard, manual/automatic IP blocking, allow/block lists, timed removal, tray operation, optional startup at sign-in, separate databases, retention cleanup, and backups.

### 使用提示 / Usage notes

界面为简体中文；文档为中英双语。地图展示本机收到的事件，普通连接不等于攻击。地理位置为近似结果，客户端无法彻底排除网关或运营商的透明转发。

The UI is in Simplified Chinese, with bilingual Chinese/English documentation. The map shows events received by this computer; a normal connection is not necessarily an attack. Locations are approximate, and the client cannot completely rule out transparent forwarding by a gateway or ISP.

[下载 v1.3.1 / Download v1.3.1](https://github.com/zuelu/port-sentinel/releases/tag/v1.3.1) · [安装指南 / Installation guide](INSTALL.md)
