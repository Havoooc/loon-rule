# loon-rule

自用 Loon 插件与分流规则，按选择独立维护。

## 插件

- [银行 App VPN 兼容](https://raw.githubusercontent.com/Havoooc/loon-rule/main/plugins/bank-vpn-compat.lpx)
- [东方财富去广告](https://raw.githubusercontent.com/Havoooc/loon-rule/main/plugins/eastmoney-adblock.lpx)
- [米家去广告](https://raw.githubusercontent.com/Havoooc/loon-rule/main/plugins/mijia.lpx)

银行兼容无需 MitM；东方财富和米家需开启 MitM 并在设备上信任 Loon CA。插件最低声明版本为 Loon 3.5.1 (978)，功能仍须在实际 App 中确认。不要与其他同类插件重复启用。

## 分流规则

- [自定义直连](https://raw.githubusercontent.com/Havoooc/loon-rule/main/rules/custom-direct.list)
- [中银香港直连](https://raw.githubusercontent.com/Havoooc/loon-rule/main/rules/bochk-direct.list)
- [香港及美国券商](https://raw.githubusercontent.com/Havoooc/loon-rule/main/rules/hk-us-broker.list)

在配置的 `[Remote Rule]` 中引用：

```ini
https://raw.githubusercontent.com/Havoooc/loon-rule/main/rules/custom-direct.list, policy=DIRECT, enabled=true
https://raw.githubusercontent.com/Havoooc/loon-rule/main/rules/bochk-direct.list, policy=DIRECT, enabled=true
https://raw.githubusercontent.com/Havoooc/loon-rule/main/rules/hk-us-broker.list, policy=你的券商策略, enabled=true
```

将“你的券商策略”替换为现有策略名称。自定义直连与中银香港独立保留并走 DIRECT；券商规则由富途和香港/美国券商列表合并、按完整规则行去重，不带固定出口策略。引用顺序决定优先级。

## 来源

插件迁自 [surge-rules 的 loon 分支](https://github.com/Havoooc/surge-rules/tree/loon/plugins)，仅更新仓库主页；规则迁自 [rule 分支](https://github.com/Havoooc/surge-rules/tree/rule)。原有引用继续可用，本次未修改设备配置。
