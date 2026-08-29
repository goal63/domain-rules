# Clash 自定义域名规则

本仓库保存 Mihomo/Clash 可远程加载的自定义域名规则。

## 文件说明

- `direct.list`：命中后交给“自定义直连”策略组。
- `proxy.list`：命中后交给“自定义代理”策略组。

## 规则格式

每行填写一条 `classical`（经典）规则，例如：

```text
DOMAIN-SUFFIX,example.com
DOMAIN,api.example.com
DOMAIN-KEYWORD,example
```

- `DOMAIN-SUFFIX`：匹配根域名及其子域名。
- `DOMAIN`：只匹配完整域名。
- `DOMAIN-KEYWORD`：匹配包含指定关键词的域名，范围较宽，请谨慎使用。
- 以 `#` 开头的行为注释。

修改并提交规则后，Mihomo 会按配置中的更新周期重新下载。
