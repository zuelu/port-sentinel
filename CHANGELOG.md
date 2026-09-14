# 更新日志 / Changelog

## v1.5.0 — 2026-09-14

- 新增每次启动一次的 GitHub 正式版检测，发现新版时提供提示和下载入口；托盘启动显示通知，不自动下载或安装。
  Added one stable GitHub release check per launch, with an update prompt and download link. Tray startup uses a notification; download and installation remain manual.
- 检测失败不影响监测，不需要 GitHub key，也不发送日志、地址清单或封禁配置。
  Check failures do not interrupt monitoring. No GitHub key is needed, and logs, address lists, and blocking settings are not sent.
- 作者信息新增可点击的仓库地址，保留联系方式、网站与 TRON 打赏钱包。
  Added a clickable repository link to the author section, retaining contacts, website, and the TRON donation wallet.
- 包含动态列表、下拉选项、日志说明、时长、规则条件、大屏、采集和存储状态的19语言覆盖修复。
  Includes 19-language fixes for dynamic lists, dropdowns, event details, durations, rule conditions, dashboards, capture capabilities, and storage states.

升级请同时更新 EXE 与 `Languages`，保留数据库、地理库和 `ui-language.txt`。

Update both the EXE and `Languages`, retaining databases, geolocation data, and `ui-language.txt`.

[下载 v1.5.0 / Download v1.5.0](https://github.com/zuelu/port-sentinel/releases/tag/v1.5.0)

## v1.4.1 — 2026-09-14

- 修复实时监测、历史日志、IP统计、封禁、自动规则和名单列表中动态状态及来源的漏译，刷新、滚动与新增记录继续使用所选语言。
  Fixed untranslated dynamic states and sources in live, history, IP statistics, block, rule, and list views. Refreshing, scrolling, and new records retain the selected language.
- 补齐19种语言的事件说明、封禁状态、数值时长、规则条件和采集能力模板。
  Completed event-detail, block-state, numeric-duration, rule-condition, and capture-capability templates in all 19 languages.
- 修复下拉选项、大屏动态提示、存储状态和详情窗口的漏译。
  Fixed untranslated dropdown labels, dynamic dashboard messages, storage states, and detail windows.
- 默认规则名跟随界面语言；用户改写的规则名和备注保持原样。时区显示改用稳定的系统ID和实际UTC偏移。
  The suggested rule name follows the interface language, while user-edited names and notes stay unchanged. Timezone display uses a stable system ID and actual UTC offset.

升级请同时更新 EXE 和 `Languages` 文件夹；保留数据库、地理库及 `ui-language.txt`。

Update both the EXE and the `Languages` folder. Retain databases, geolocation data, and `ui-language.txt`.

[下载 v1.4.1 / Download v1.4.1](https://github.com/zuelu/port-sentinel/releases/tag/v1.4.1)

## v1.4.0 — 2026-09-14

- 新增 19 种界面语言与离线 JSON 语言包，简体中文第一、英语第二。
  Added 19 interface languages and offline JSON language packs, with Simplified Chinese first and English second.
- 左侧版本号上方即时切换语言，页面、列表状态、提示、确认按钮与托盘菜单同步更新，无需重启监测。
  Switch instantly above the sidebar version number. Pages, list states, prompts, confirmation buttons, and tray menus update without restarting monitoring.
- 自动记住最后选择的语言，完全退出后再次启动自动恢复。
  The last language selection is saved automatically and restored after a complete exit and relaunch.
- 地理名称使用数据库中可用的对应语言；长译文导航支持换行，阿拉伯语文字支持从右至左显示。
  Geographical names use available localized database names. Long navigation labels wrap, and Arabic text supports right-to-left display.
- 作者区新增可复制的 TRON 打赏地址。
  Added a selectable TRON donation address to the author section.
- 原有监测、筛选、统计、封禁、名单、存储与自启功能保持不变。
  Existing monitoring, filtering, statistics, blocking, lists, storage, and startup behavior is unchanged.

部分语言使用自动翻译；日期输入仍为 `yyyy-MM-dd`，原始日志与用户输入不改写。

Some languages use machine-generated translations. Date input remains `yyyy-MM-dd`, and raw logs and user input are not rewritten.

[下载 v1.4.0 / Download v1.4.0](https://github.com/zuelu/port-sentinel/releases/tag/v1.4.0) · [语言包指南 / Language pack guide](LANGUAGES.md)

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
