# Port Sentinel 多语言与语言包指南 / Language & Language Pack Guide

## 即时切换 / Instant switching

在左侧版本号上方选择语言。界面即时更新，不会重新启动监测，也不会改写筛选值、用户输入、原始日志或封禁配置。

Choose a language above the sidebar version number. The interface updates immediately without restarting monitoring or rewriting filters, user input, raw logs, or blocking settings.

程序自动保存最后选择的语言，下次启动恢复。请把软件解压到可写的固定目录，升级时保留同目录的 `ui-language.txt`。

The last language choice is saved automatically and restored on the next launch. Extract the application to a stable, writable folder and retain `ui-language.txt` beside the EXE when upgrading.

## 支持语言 / Supported languages

简体中文第一，英语第二，其他语言按语言包文件名排列。语言选项使用各语言自己的名称，方便寻找。

Simplified Chinese comes first and English second. Other languages follow language-pack filename order. Each option uses its native language name for easy recognition.

| 语言 / Language | 显示名称 / Native name | 语言包 / Pack |
|---|---|---|
| 简体中文 / Simplified Chinese | 简体中文 | zh-CN.json |
| 英语 / English | English | en.json |
| 繁体中文 / Traditional Chinese | 繁體中文 | zh-TW.json |
| 日语 / Japanese | 日本語 | ja.json |
| 韩语 / Korean | 한국어 | ko.json |
| 德语 / German | Deutsch | de.json |
| 法语 / French | Français | fr.json |
| 西班牙语 / Spanish | Español | es.json |
| 葡萄牙语 / Portuguese | Português | pt.json |
| 俄语 / Russian | Русский | ru.json |
| 意大利语 / Italian | Italiano | it.json |
| 土耳其语 / Turkish | Türkçe | tr.json |
| 阿拉伯语 / Arabic | العربية | ar.json |
| 印地语 / Hindi | हिन्दी | hi.json |
| 印度尼西亚语 / Indonesian | Bahasa Indonesia | id.json |
| 越南语 / Vietnamese | Tiếng Việt | vi.json |
| 泰语 / Thai | ไทย | th.json |
| 波兰语 / Polish | Polski | pl.json |
| 荷兰语 / Dutch | Nederlands | nl.json |

## 调整与新增语言包 / Customize or add a pack

语言包为 `Languages` 文件夹中的 UTF-8 JSON 文件，不需要联网。修改已有文件的 `strings` 译文，或复制 `en.json` 后为新语言设置唯一 `code`、原生 `name` 与 `rtl`。重启软件后加载新增或修改的语言包；切换已加载语言不需要重启。

Packs are offline UTF-8 JSON files in the `Languages` folder. Edit translations in `strings`, or copy `en.json` and set a unique `code`, native `name`, and `rtl` for another language. Restart to load added or edited packs; switching between already loaded languages does not require a restart.

`strings` 左侧中文键保持不变，只修改右侧译文。保留 `{0}`、`{1:N0}` 等占位符、数字范围和单位；`code` 采用 `en`、`ja`、`zh-TW` 等语言代码。阿拉伯语的 `rtl` 为 `true`。缺失条目优先回退英文，未安装的语言回退简体中文。

Keep Chinese keys on the left of `strings` unchanged and edit only translations on the right. Preserve placeholders such as `{0}` and `{1:N0}`, numeric ranges, and units. Use language codes such as `en`, `ja`, or `zh-TW`. Arabic uses `rtl: true`. Missing entries fall back to English; an unavailable selected language falls back to Simplified Chinese.

## 状态标签与数据格式 / Badges and data formats

中文标签为红“禁”、绿“白”、灰“黑”、琥珀“待”、橙“异”。其他语言使用紧凑的 B、W、K、P、! 标签，悬停查看对应语言的详情。日期输入统一使用 `yyyy-MM-dd`，IP、端口、地址范围和 TRON 钱包保持原样。

Chinese badges use red 禁, green 白, gray 黑, amber 待, and orange 异. Other languages use compact B, W, K, P, and ! badges; hover for localized details. Date input uses `yyyy-MM-dd` throughout. IPs, ports, address ranges, and the TRON wallet remain unchanged.

地理名称取决于城市数据库提供的语言；没有对应名称时使用英文。部分界面译文来自自动翻译，欢迎在 [Issues](https://github.com/zuelu/port-sentinel/issues) 提交具体措辞建议。

Geographical names depend on languages available in the City database and fall back to English. Some interface translations are machine-generated. Submit specific wording suggestions through [Issues](https://github.com/zuelu/port-sentinel/issues).

[下载 / Download](https://github.com/zuelu/port-sentinel/releases/latest) · [安装使用 / Installation & usage](INSTALL.md) · [项目首页 / Overview](README.md)
