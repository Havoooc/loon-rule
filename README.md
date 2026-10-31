# loon-rule

自用 Loon 插件与分流规则，按选择独立维护。

## 策略图标

`icons/` 中的全球、家宽和代理图标来自 [Koolson/Qure](https://github.com/Koolson/Qure)，供 Loon 策略组引用。

## 插件

- [银行 App VPN 兼容](https://raw.githubusercontent.com/Havoooc/loon-rule/main/plugins/bank-vpn-compat.lpx)
- [东方财富去广告](https://raw.githubusercontent.com/Havoooc/loon-rule/main/plugins/eastmoney-adblock.lpx)
- [金十数据去广告](https://raw.githubusercontent.com/Havoooc/loon-rule/main/plugins/jin10-adblock.lpx)
- [米家去广告](https://raw.githubusercontent.com/Havoooc/loon-rule/main/plugins/mijia.lpx)

银行兼容无需 MitM；东方财富、金十数据和米家需开启 MitM 并在设备上信任 Loon CA。插件最低声明版本为 Loon 3.5.1 (978)，功能仍须在实际 App 中确认。不要与其他同类插件重复启用。

## 分流规则

- [自定义代理（Grok Bot / Grok / xAI）](https://raw.githubusercontent.com/Havoooc/loon-rule/main/rules/custom-proxy.list)

- [Red Pocket AT&T Wi-Fi Calling](https://raw.githubusercontent.com/Havoooc/loon-rule/main/rules/redpocket-att-wificalling.list)

- [自定义直连](https://raw.githubusercontent.com/Havoooc/loon-rule/main/rules/custom-direct.list)
- [中银香港直连](https://raw.githubusercontent.com/Havoooc/loon-rule/main/rules/bochk-direct.list)
- [香港及美国券商](https://raw.githubusercontent.com/Havoooc/loon-rule/main/rules/hk-us-broker.list)

在配置的 `[Remote Rule]` 中引用：

```ini
https://raw.githubusercontent.com/Havoooc/loon-rule/main/rules/custom-proxy.list, policy=你的AI策略, tag=自定义代理, enabled=true
https://raw.githubusercontent.com/Havoooc/loon-rule/main/rules/redpocket-att-wificalling.list, policy=你的美国家宽策略, tag=AT&T Wi-Fi Calling, enabled=true
https://raw.githubusercontent.com/Havoooc/loon-rule/main/rules/custom-direct.list, policy=DIRECT, enabled=true
https://raw.githubusercontent.com/Havoooc/loon-rule/main/rules/bochk-direct.list, policy=DIRECT, enabled=true
https://raw.githubusercontent.com/Havoooc/loon-rule/main/rules/hk-us-broker.list, policy=你的券商策略, enabled=true
```

将“你的券商策略”替换为现有策略名称。自定义直连与中银香港独立保留并走 DIRECT；券商规则由富途和香港/美国券商列表合并、按完整规则行去重，不带固定出口策略。引用顺序决定优先级。

Wi-Fi Calling 规则需将“你的美国家宽策略”替换为真实策略组名称，并选择美国家宽节点；建议放在其他远程规则之前。此列表仅覆盖 Red Pocket GSMA（AT&T），不适用于其他运营商。规则本身不启用系统通话流量接管，也不保证注册成功；手机端仍需确认 Loon 接管了通话流量，且所选路径支持 UDP。

自定义代理包含已确认的 Grok Bot 聊天域名 `cursor.sh`、`cursorvm.com` 及 Grok / xAI 的 `grok.com`、`x.ai`（均含子域名）。将“你的AI策略”替换为现有代理策略名称，建议选美国家宽；该规则还会影响这些域名的其他服务，并非仅匹配 Bot。

## 来源

插件最初从 Surge 模块转换；旧 loon 分支现仅保留迁移说明。规则迁自 [rule 分支](https://github.com/Havoooc/surge-rules/tree/rule)。原有引用继续可用，本次未修改设备配置。
