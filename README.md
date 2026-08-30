# Mihomo/Clash 自定义域名规则

本仓库保存可由 Mihomo/Clash 远程加载的自定义域名规则。

## 文件说明

| 文件 | 命中后的处理方式 |
| --- | --- |
| `direct.list` | 直接使用 `直连` |
| `proxy.list` | 交给“🚀 自定义代理”策略组 |
| `proxy2.list` | 交给“🚀 自定义代理2”策略组 |

## Raw 地址

- `https://raw.githubusercontent.com/goal63/domain-rules/main/direct.list`
- `https://raw.githubusercontent.com/goal63/domain-rules/main/proxy.list`
- `https://raw.githubusercontent.com/goal63/domain-rules/main/proxy2.list`

## 配置示例

```yaml
rules:
  - RULE-SET,custom_direct_domain,直连
  - RULE-SET,custom_proxy_domain,🚀 自定义代理
  - RULE-SET,custom_proxy2_domain,🚀 自定义代理2

rule-providers:
  custom_direct_domain:
    type: http
    interval: 86400
    behavior: classical
    format: text
    url: "https://raw.githubusercontent.com/goal63/domain-rules/main/direct.list"
  custom_proxy_domain:
    type: http
    interval: 86400
    behavior: classical
    format: text
    url: "https://raw.githubusercontent.com/goal63/domain-rules/main/proxy.list"
  custom_proxy2_domain:
    type: http
    interval: 86400
    behavior: classical
    format: text
    url: "https://raw.githubusercontent.com/goal63/domain-rules/main/proxy2.list"
```

## 规则格式

每行填写一条 `classical`（经典）规则，例如：

```text
DOMAIN-SUFFIX,example.com
DOMAIN,api.example.com
DOMAIN-KEYWORD,example
```

- `DOMAIN-SUFFIX`：匹配根域名及其所有子域名。
- `DOMAIN`：只匹配完整域名。
- `DOMAIN-KEYWORD`：匹配包含指定关键词的域名，范围较宽，请谨慎使用。
- 以 `#` 开头的行为注释。

## 更新方式

配置中的更新周期为 `86400` 秒，即每24小时自动检查一次。修改并提交规则后，也可以在 Mihomo/Nikki 面板中手动刷新对应的规则集，使其立即生效。
