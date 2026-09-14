# Port Sentinel 安装使用指南 / Installation & User Guide

本指南介绍如何安装 Windows 端口监控软件、查看 3389/RDP 连接日志、配置 IP 自动封禁，以及管理离线地理库与日志保留。

This guide explains how to install the Windows port monitor, inspect port 3389/RDP connection logs, configure automatic IP blocking, and manage offline geolocation data and log retention.

[下载 / Download](https://github.com/zuelu/port-sentinel/releases/latest) · [项目首页 / Overview](README.md) · [更新日志 / Changelog](CHANGELOG.md)

## 安装要求 / Requirements

- Windows 10/11 x64，.NET Framework 4.8 或更新版本。/ Windows 10/11 x64 with .NET Framework 4.8 or later.
- 管理员权限，用于网卡捕获及防火墙规则管理。/ Administrator permission for network-interface capture and firewall-rule management.
- 一个可写的固定目录，并为地理库、日志和备份保留空间。/ A stable, writable folder with space for the geolocation database, logs, and backups.

界面支持 19 种语言，以下说明保留中文名称及英文对照。软件无需 Python 或 Npcap。地理库约 121 MB，日志体积取决于流量和保留天数。

The UI supports 19 languages. Instructions show Chinese control labels with English equivalents for reference. Python and Npcap are not required. The geolocation database is approximately 121 MB; log size depends on traffic and retention settings.

## 下载与启动 / Download and launch

1. 打开 [Releases](https://github.com/zuelu/port-sentinel/releases/latest)，下载完整的 `PortSentinel-v1.4.0-windows-x64.zip`。
   Open [Releases](https://github.com/zuelu/port-sentinel/releases/latest) and download the complete `PortSentinel-v1.4.0-windows-x64.zip`.
2. 先完整解压，不要直接在 ZIP 内运行程序。
   Extract the archive completely; do not run the application from inside the ZIP.
3. 保持 `PortSentinel.exe`、`GeoData/dbip-city-lite.mmdb` 与 `Languages` 文件夹的相对位置不变。
   Keep `PortSentinel.exe` and `GeoData/dbip-city-lite.mmdb` in their extracted relative locations.
4. 双击 EXE，在 Windows 提示时允许管理员运行。程序启动后开始采集本机入站事件。
   Double-click the EXE and grant administrator permission when prompted. Collection of local inbound events starts after launch.

Release 中也提供单独的 `PortSentinel.exe`。首次使用建议选择完整 ZIP；仅下载 EXE 时，基础监测仍可运行，但需要另行导入城市 MMDB 才能显示地理位置，并保留 `Languages` 文件夹才能选择其他语言。

The release also includes a standalone `PortSentinel.exe`. Choose the complete ZIP for a first installation. With only the EXE, basic monitoring is available, but a City MMDB must be supplied separately for geolocation, and the `Languages` folder is needed to select additional languages.

## 切换语言与记住选择 / Switch language and remember your choice

在左侧版本号上方打开语言下拉框。选择后界面即时更新，监测继续运行。程序会在同目录保存 `ui-language.txt`；关闭到托盘和完全退出均不丢失选择，再次启动自动恢复。升级时保留此文件并更新 `Languages` 文件夹。

Open the language selector above the sidebar version number. The interface updates immediately while monitoring continues. The application saves `ui-language.txt` beside the EXE. Hiding to the tray or exiting completely retains your choice, which is restored at the next launch. Keep this file and update the `Languages` folder when upgrading.

日期输入仍使用 `yyyy-MM-dd`，端口、IP、用户备注和日志中的原始值不随界面语言改变。语言包缺少条目时回退英文，语言包不可用时回退简体中文。更多信息见[语言包指南 / Language pack guide](LANGUAGES.md)。

Dates still use `yyyy-MM-dd`. Ports, IPs, user notes, and stored raw values do not change with the UI language. Missing translation entries fall back to English; unavailable language packs fall back to Simplified Chinese. See the [language pack guide](LANGUAGES.md) for details.

## 查看端口与 RDP 连接日志 / View port and RDP connection logs

1. 打开“实时监测”，在“本机端口”输入 `3389`，点击“筛选”；留空或点击“全部端口”查看其他端口。
   Open **实时监测 (Live Monitor)**, enter `3389` under **本机端口 (Local Port)**, and click **筛选 (Filter)**. Leave it blank or choose **全部端口 (All Ports)** to include other ports.
2. 实时列表只显示最新 100 条事件。“暂停画面”只暂停显示，“停止监测”才会停止采集。
   The live list displays the latest 100 events. **暂停画面 (Pause Display)** pauses only the view; **停止监测 (Stop Monitoring)** stops collection.
3. 双击记录查看连接过程。到“历史日志”组合日期、端口、IP、协议或状态条件，点击“查询”并按需导出 CSV。
   Double-click a record to inspect its connection timeline. In **历史日志 (History)**, combine date, port, IP, protocol, or state filters, search, and export a CSV if needed.
4. 打开“IP 统计”查看每个来源的连接尝试总数，选择 IP 后查看它的历史日志。
   Open **IP 统计 (IP Statistics)** to see attempt totals per source, then select an IP to inspect its history.

日期格式为 `yyyy-MM-dd`，结束日期包含当天，留空表示不限制。历史列表每页 100 条，筛选作用于全部记录而非当前页。TCP 已连接表示传输连接建立，不表示账号认证成功。

Dates use `yyyy-MM-dd`; the end date includes that entire day, and an empty field means no limit. History is paginated at 100 records per page, with filters applied to all records rather than just the current page. “TCP established” means the transport connection exists, not that account authentication succeeded.

<a id="blocking"></a>
## 手动封禁、自动封禁与黑白名单 / Manual blocks, automatic rules, and lists

### 手动封禁 / Manual blocking

在列表中右键来源 IP，选择“封禁此 IP”，或打开“封禁管理”输入单个 IP、CIDR 网段或起止范围。设置时长后核对确认内容，再执行封禁。选中记录可提前解除。

Right-click a source IP and select **封禁此 IP (Block this IP)**, or open **封禁管理 (Block Management)** and enter an address, CIDR network, or address range. Set a duration, review the confirmation, and apply the block. Select an existing entry to remove it early.

### 自动规则 / Automatic rules

1. 打开“自动封禁”，输入规则名称、本机端口、统计窗口、次数阈值及封禁时长。
   Open **自动封禁 (Automatic Blocking)** and enter a rule name, local ports, time window, threshold, and block duration.
2. 选择“入站尝试（含扫描）”或“TCP 已连接”计数方式，保存并启用规则。
   Choose inbound attempts, including probes, or established TCP connections as the counting mode; save and enable the rule.
3. 确认阈值适合正常用户流量后，再开启自动封禁总开关。
   Verify that the threshold is appropriate for legitimate traffic before enabling the master automatic-blocking switch.

窗口支持 1–86,400 秒；示例 `3389,22` 表示合计这两个端口的连接次数，不是只封禁这两个端口。触发后会封禁该 IP 的全部入站端口和协议。总开关与监测同时开启时才执行新的自动判断；停用规则不会解除已经存在的封禁。

The window supports 1–86,400 seconds. For example, `3389,22` combines counts for those two ports; it does not limit the resulting block to those ports. A triggered IP block covers all inbound ports and protocols. New automatic decisions require both the master switch and monitoring to be active; disabling a rule does not remove existing blocks.

### 黑白名单与状态标签 / Allow/block lists and badges

在“黑白名单”中新增或删除可信地址和持续封禁范围。白名单优先于本软件的封禁策略，但不会覆盖其他软件或系统策略。与手动封禁或黑名单冲突时，先处理冲突条目。

Use **黑白名单 (Allow/Block Lists)** to add or remove trusted addresses and persistent block ranges. The allowlist takes priority within Port Sentinel, but does not override other software or system policies. Resolve conflicting manual blocks or blocklist entries first.

| 标签 / Badge | 含义 / Meaning |
|---|---|
| 红色“禁” / Red 禁 | 当前匹配本软件已核对的启用规则，且活动防火墙具备生效条件。 / Matches an enabled application-managed rule with active firewall profiles capable of enforcing it. |
| 绿色“白” / Green 白 | 命中白名单。 / Matches the allowlist. |
| 灰色“黑” / Gray 黑 | 命中黑名单。 / Matches the blocklist. |
| 琥珀“待” / Amber 待 | 等待处理、配置受限或到期待清理。 / Pending work, limited configuration, or expiry cleanup. |
| 橙色“异” / Orange 异 | 读取或规则状态异常。 / A read or rule-state problem. |

悬停查看详情。历史列表的标签显示当前封禁/名单状态，不是事件发生时的快照。远程管理前应确认自己的管理地址和恢复通道；Windows 防火墙或组策略可能影响规则是否生效。

Hover for details. Badges in history show the current block/list state, not a snapshot from the time of the event. Confirm your administration address and recovery access before changing remote-access rules; Windows Firewall and Group Policy may affect enforcement.

## 全球大屏与本机出口定位 / Global dashboard and outbound IP location

“全球来源”展示本机收到的来源事件。使用 F11 全屏，Esc 返回；双击右侧记录查看详情。内网、回环、保留和无法定位的地址仍保留在日志中，但不会被猜测到地图某个城市。

**全球来源 (Global Sources)** displays source events received by this computer. Use F11 for fullscreen, Esc to return, and double-click a record on the right for details. Private, loopback, reserved, and unlocated addresses remain in logs but are not assigned a guessed city on the map.

“刷新本机定位”通过物理网卡进行两个服务的直连出口 IPv4 核对。成功后使用离线库确定近似落点。检测不使用应用代理，也不会为成功而切换到代理；遇到 VPN/TUN 路由或两家回显不一致时显示未确认。上游透明转发和城市定位误差无法完全排除。

**刷新本机定位 (Refresh Local Location)** checks the outbound IPv4 through direct physical-interface connections to two services. When they agree, the offline database supplies an approximate marker. Detection does not use application proxies or fall back to one; VPN/TUN routes or conflicting responses remain unconfirmed. Transparent forwarding upstream and city-level location errors cannot be ruled out completely.

## 历史清理与备份 / Retention and backups

打开“存储维护”，设置保留最近多少天，范围 1–36,500 天。自动清理默认关闭，预设 30 天；可以先用“预览并清理”确认范围，或保存自动清理配置。软件运行时每分钟检查，每次成功清理至少间隔 24 小时。

Open **存储维护 (Storage Maintenance)** and choose a retention period from 1 to 36,500 days. Automatic cleanup is off by default, with a 30-day preset. Use **预览并清理 (Preview and Clean)** to review the scope, or save an automatic policy. While the app runs, the policy is checked every minute and successful cleanups are at least 24 hours apart.

清理会短暂停止采集、保存队列、备份并回收数据库空间，然后恢复原采集状态；暂停期间可能出现采集缺口。有效封禁、当前名单及配置保留。累计 IP 次数只统计仍保留的历史，因此会随清理减少。

Cleanup briefly stops collection, flushes the queue, creates the selected backup, reclaims database space, and resumes the previous collection state. There may be a capture gap during the pause. Active blocks, current lists, and settings remain. Per-IP totals count only retained history and therefore decrease after cleanup.

“立即完整备份”生成流量、配置、审计库及布局文件的一致性备份。自动备份保留最近 3 组完整备份，手动备份不自动删除。建议把重要备份另存到其他磁盘。

**立即完整备份 (Back Up Now)** creates consistent copies of the traffic, settings, and audit databases together with the layout file. The latest three complete automatic backups are retained; manual backups are not automatically deleted. Copy important backups to another disk.

## 托盘、自启与升级 / Tray, startup, and updates

关闭主窗口会隐藏至系统托盘。双击托盘图标可恢复；右键“退出端口监测”才会停止程序。退出时会取消后续对账，等待正在执行的单条规则操作完成并保存队列。

Closing the main window hides it to the system tray. Double-click the tray icon to restore it; use **退出端口监测 (Exit Port Sentinel)** from the tray menu to stop the app. Exit cancels subsequent reconciliation checks, finishes any in-progress individual rule operation, and flushes the queue.

“采集与存储”页可手动开启当前用户登录自启。更新前先退出旧版并备份，再替换程序文件，保留原数据文件。文件名或路径改变后，请重新保存自启设置，让它指向新 EXE。

Use **采集与存储 (Collection & Storage)** to enable startup at the current user's sign-in. Before updating, exit the old version and create a backup, then replace the application files while retaining your data files. If the filename or folder changes, save the startup setting again so it points to the new EXE.

## 常见问题排查 / Troubleshooting

- **没有新记录 / No new records:** 确认监测已启动、具备管理员权限并且实际收到入站流量；检查“采集与存储”的能力状态。/ Confirm collection is running with administrator permission and that inbound traffic is actually arriving; check capability status in Collection & Storage.
- **没有防火墙阻断日志 / No firewall-drop logs:** 对应 Windows 审核事件可能尚未启用；程序不会把缺失的事件虚构为零攻击。/ The corresponding Windows audit events may not be enabled; missing events are not proof of zero attacks.
- **地理位置不显示 / No geolocation:** 保持 GeoData 在 EXE 旁边，或在存储维护导入可信的 City MMDB。/ Keep GeoData beside the EXE, or import a trusted City MMDB in Storage Maintenance.
- **出口检测失败 / Outbound IP detection fails:** 检查直连网络及物理接口；程序不会用代理结果替代。/ Check direct connectivity and the physical interface; proxy results are not substituted.
- **数据库不可用 / Database unavailable:** 先退出程序并保留当前文件，再从同一组完整备份恢复；不要把旧 WAL 文件与恢复后的数据库混用。/ Exit and preserve the current files before restoring one complete backup set; do not mix old WAL files with restored databases.

<a id="uninstall"></a>
## 卸载 / Uninstall

1. 解除不再需要的手动和自动封禁，删除需要撤销的黑名单条目。
   Remove unwanted manual/automatic blocks and delete blocklist entries you no longer want enforced.
2. 在程序中关闭登录自启，保存需要保留的日志和备份。
   Disable startup at sign-in in the app, and save any logs or backups you need.
3. 从托盘彻底退出，再删除程序文件。
   Exit completely through the tray menu, then delete the application files.

只删除 EXE 不会自动撤销系统防火墙规则。限时解除依赖系统计划任务，关机或休眠可能使执行延后至系统恢复。

Deleting the EXE alone does not undo system firewall rules. Timed removal relies on scheduled tasks; shutdown or sleep may delay execution until the system resumes.
