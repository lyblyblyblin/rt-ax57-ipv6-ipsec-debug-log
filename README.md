# RT-AX57 ipv6下的ipsec公网连接失败：排障记录

> 本页面内容由 AI 汇总生成，仅供参考。
> 如内容涉及侵权，请联系邮箱 **lin_yb@88.com**，核实后删除。

## 背景速记

- **问题**：ASUS RT-AX57（固件 3.0.0.4.386_53370）在 IPv6 公网环境下，客户端发起 IPsec IKEv2 连接失败。
- **现象**：strongSwan 日志显示 IKE_SA_INIT 协商完成后，进入 IKE_AUTH 阶段返回 `AUTH_FAILED`，并出现 `no matching peer config found`；客户端地址被解析到运营商 CGNAT 网段。
- **线索**：协商过程出现 DH 组 `INVAL_KE`（服务端请求 CURVE_25519）、证书请求来自路由器内置 Root CA，客户端设备时间已确认准确。
- **结论**：原始笔记为排障采样记录，未给出最终修复方案；本仓库原样保留日志正文与附件，供后续分析复现。

## 文档

| 文档 | 说明 |
|---|---|
| [docs/rt-ax57-ipv6-ipsec.md](docs/rt-ax57-ipv6-ipsec.md) | 笔记正文（ENML → GitHub Markdown，保留标题/列表/代码与日志原文） |

## 附件（原样上传，未解压、未转格式）

| 文件 | 大小 | 类型 |
|---|---|---|
| [01_charon(1).log](logs/01_charon%281%29.log) | 3.2 KB | strongSwan 日志 |
| [02_charon.log](logs/02_charon.log) | 3.2 KB | strongSwan 日志 |
| [03_a6216739.png](images/03_a6216739.png) | 55.6 KB | 截图 |

全部附件均小于 1 MiB，随仓库文件一同上传，未使用 Release 附件。

## 脱敏说明

日志中的公网 IPv6 地址已替换为 `REDACTED_SERVER_IPv6` / `REDACTED_CLIENT_IPv6_A` / `REDACTED_CLIENT_IPv6_B` 占位符（不同地址仍可区分，排障逻辑不受影响）。运营商 CGNAT 段 IPv4、设备固件版本与对外联系邮箱按原样保留。

## 适用环境与注意事项

- 设备：ASUS RT-AX57，固件版本 3.0.0.4.386_53370；服务端 strongSwan。
- 场景：IPv6 公网 / IKEv2 IPsec，客户端为安卓设备。
- 正文日志包含真实公网 IPv6 地址与运营商分配地址，公开发布前请自行评估是否需要脱敏。
- 日志为原始输出，其中的时间戳、地址、证书字段仅用于对应环境下的排障，请勿直接照搬配置。

## 免责声明

本仓库内容由个人笔记自动转换汇总而来，仅供技术交流参考，不构成对任何设备、固件或网络配置的建议。因使用本仓库内容造成的任何后果，由使用者自行承担。如内容涉及侵权，请通过上方邮箱联系删除。
