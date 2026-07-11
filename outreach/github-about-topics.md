# GitHub About & Topics 优化清单

> 在仓库右上角齿轮图标处编辑。完成一项打一个勾。

---

## About 描述

### 当前内容

```
免费无广告追剧资源导航，每日自动检测可用性。收录无广告在线影视、影视App、网盘搜索、磁力与 BT、字幕、TVBox、影视仓配置地址、IPTV 订阅源和会员拼团。
```

### 问题

- 没有体现"开源 + 社区维护"这个核心差异点（普通导航站做不到）
- "影视App" 大小写不统一，应为 "影视APP"
- 结尾罗列了太多分类，信息密度过高，可以压缩

### 建议修改为

```
免费无广告追剧资源导航，每日自动检测可用性。收录在线影视、影视APP、网盘搜索、磁力 BT、字幕、TVBox / 影视仓配置地址、IPTV 订阅源。开源，社区共同维护。
```

**修改点：**
- 删去重复的"无广告"（标题已有）
- 压缩分类列表
- 结尾加"开源，社区共同维护"——这是与其他导航站的本质区别

- [x] 更新 About 描述

---

## Website

当前：`zhuiju.me` ✅ 已填写，无需修改。

---

## Topics

### 当前 Topics（15 个）

`media-player` `subtitles` `chinese` `awesome-list` `iptv` `tvbox` `movie-guide`
`free-streaming` `streaming-guide` `daily-check` `magnet-search` `movie-resources`
`bt-search` `cloud-drive-search` `awesome-zhuiju-free`

### 建议删除（3 个，用来腾出位置）

| Topic | 原因 |
|---|---|
| `daily-check` | 不是用户会搜索的词，发现性低 |
| `streaming-guide` | 与 `free-streaming`、`movie-guide` 重叠 |
| `awesome-zhuiju-free` | 仓库名本身作为 Topic 无助于被发现 |

### 建议新增（4 个）

| Topic | 原因 |
|---|---|
| `free` | 极高频搜索词，很多同类项目都有 |
| `movie` | 比 `movie-guide` 更短、搜索量更大 |
| `no-ads` | 项目核心卖点，差异化标签 |
| `tvbox-config` | 中国用户高频搜索词，精准匹配目标受众 |

### 优化后的 Topics（16 个）

```
awesome-list  chinese  free  movie  iptv  tvbox  tvbox-config
free-streaming  movie-guide  movie-resources  magnet-search  bt-search
cloud-drive-search  subtitles  media-player  no-ads
```

- [x] 删除 3 个低效 Topic
- [x] 新增 4 个高效 Topic

---

## 操作步骤

1. 打开 https://github.com/laoma2053/awesome-zhuiju-free
2. 点击右上角"About"旁边的 ⚙️ 齿轮图标
3. 修改 Description 为建议内容
4. 在 Topics 栏逐一删除和添加
5. 点击 Save changes
