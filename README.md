# KVideo 订阅源

`sources.json` 是 KVideo 可直接订阅的源列表（78 条：56 普通 + 22 高级/成人）。

## 订阅地址

```
https://raw.githubusercontent.com/nzoffyt/KVideo/sources/sources.json
```

## KVideo 环境变量

```bash
SUBSCRIPTION_SOURCES='[{"name":"我的源列表","url":"https://raw.githubusercontent.com/nzoffyt/KVideo/sources/sources.json"}]'
```

`SUBSCRIPTION_SOURCES` 会被 `/api/auth` 下发给客户端，服务端配置即可生效，无需 `NEXT_PUBLIC_` 前缀（已实测）。

## 字段说明

| 字段 | 说明 |
| --- | --- |
| `id` | 唯一标识，重复会被去重 |
| `name` | 显示名 |
| `baseUrl` | 采集接口，KVideo 会以 `?ac=detail&wd=关键词&pg=页码` 请求 |
| `group` | `normal` 进普通模式，`premium` 进 /premium 模式 |
| `enabled` | `false` 时不同步启用，但保留在列表里 |
| `priority` | 排序权重，越小越靠前 |

## 维护

直接编辑 `sources.json` 提交到本分支即可，客户端下次加载（同一订阅 5 分钟冷却）自动拉取新列表。

`main` 分支保持与上游 KuekHaoYang/KVideo 一致，不要在这里提交，否则会影响 `git merge --ff-only upstream/main`。
