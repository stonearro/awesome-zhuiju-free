# README 第一屏优化清单

> 本文档记录 README 头部区域的所有待优化项。完成一项打一个勾。

---

## 第一批：立即可做

### 徽章区

- [x] **加入 GitHub Stars 徽章**
  - 位置：大徽章行，排第一位
  - 代码：
    ```markdown
    <a href="https://github.com/laoma2053/awesome-zhuiju-free/stargazers">
      <img src="https://img.shields.io/github/stars/laoma2053/awesome-zhuiju-free?style=for-the-badge&color=yellow" alt="GitHub Stars">
    </a>
    ```
  - 效果：Stars 数字实时展示，是最强社会证明

- [x] **删除 `Validate data` CI 徽章（从头部移走）**
  - 当前位置：第二排徽章行
  - 原因：这是维护者用的 CI 状态，对普通访客无意义
  - 处理方式：移到 README 底部"技术说明"区，或删除

- [x] **删除 `issues X open` 徽章**
  - 当前位置：第二排徽章行
  - 原因："X open" 对新访客传递负面信号（有未解决的问题）
  - 处理方式：直接删除

- [x] **删除 `PRs welcome` 徽章（可选）**
  - 当前位置：第二排徽章行
  - 原因：这条信息在导航链接的"贡献指南"里已有体现，重复
  - 处理方式：删除，或并入大徽章行

- [ ] **加入 FOSSA 许可证扫描徽章**
  - 位置：大徽章行或第二排小徽章位置
  - 前置步骤：访问 https://fossa.com → 用 GitHub 登录 → 导入仓库 → 自动生成徽章代码
  - 说明：开源项目免费，扫描后显示 `license scan passing`，增加项目可信度（截图参考项目已有此徽章）

- [x] **统一为单排大徽章**
  - 目标效果：`[⭐ Stars] [网站 ZHUIJU.ME] [已收录 N 个资源] [可用性检测 每日执行]` 四个并排
  - 原因：当前两排不同风格的徽章视觉断层，统一后更整洁

---

### 描述文字区

- [x] **将长段描述替换为 emoji 短句列表**
  - 当前：一段两行的流水账长句，信息密度高，扫一眼抓不到重点
  - 改为（参考）：
    ```
    🎬 在线影视 · 影视APP · 字幕资源
    📦 网盘搜索 · 磁力 BT · TVBox配置 · IPTV 订阅源
    ✅ 每日自动检测可用性，资源不是死列表
    🔓 完全开源，无广告，社区共同维护
    ```

---

### 导航链接区

- [x] **删除"查看完整数据"导航链接**
  - 当前：`浏览精选资源 · 推荐新资源 · 报告失效 · 查看完整数据 · 贡献指南`
  - 原因：`resources.json` 是技术文件，普通用户点进去会困惑
  - 处理方式：删除该链接，或移到 README 底部

- [x] **加入加星引导语**
  - 位置：导航链接下方
  - 内容：`觉得有用？点个 ⭐ Star 支持一下，帮助更多追剧党发现这里。`
  - 原因：大量高星仓库都有这类克制的引导，对转化率有实际效果

---

### 新增模块

- [x] **加入"为什么选这个列表"对比表格**
  - 位置：分割线之后、`## 精选资源` 之前
  - 目的：回答新访客"这个和其他导航站有什么区别"的疑问
  - 内容参考：

    | | 普通导航站 | 本项目 |
    |---|---|---|
    | 广告 | 有 | 无 |
    | 资源失效 | 无人管 | 每日自动检测 |
    | 是否开源 | 否 | 是，数据公开 |
    | 参与贡献 | 不行 | Issue 直接提交 |

- [x] **加入 Ask DeepWiki 按钮**
  - 位置：大徽章行下方，单独一行或与其他工具按钮并排
  - 代码：
    ```markdown
    [![Ask DeepWiki](https://deepwiki.com/badge.svg)](https://deepwiki.com/laoma2053/awesome-zhuiju-free)
    ```
  - 说明：DeepWiki 免费，自动索引仓库内容，让访客可以直接对话式查询资源

- [x] **建立 Gitee 镜像并加入链接**
  - 前置步骤：注册 Gitee → 新建仓库 → 开启"强制同步"从 GitHub 自动镜像
  - Gitee 地址规划：`https://gitee.com/laoma2053/awesome-zhuiju-free`
  - README 加入内容：
    ```markdown
    > 国内访问：[Gitee 镜像](https://gitee.com/laoma2053/awesome-zhuiju-free)（与 GitHub 实时同步）
    ```
  - 位置：README 顶部 `<div align="center">` 内，副标题下方
  - 原因：追剧用户中非开发者占比高，GitHub 在国内访问不稳定，Gitee 镜像能显著扩大实际可访问人群

---

## 第二批：获得外部认可后添加

> 以下徽章需要先提交并被对应平台收录，收录后平台会提供官方 embed 代码。

- [ ] **加入 HelloGitHub 推荐卡片**
  - 前置条件：提交 HelloGitHub → 被收录
  - 提交地址：https://hellogithub.com/periodical
  - 位置：加在对比表格上方或大徽章行下方
  - 效果参考：`RECOMMEND BY HelloGitHub ▲N`（带官方 logo 的大卡片）

- [x] **加入 Trendshift 排名卡片**
  - 前置条件：提交 Trendshift → 被收录
  - 提交地址：https://trendshift.io
  - 位置：与 HelloGitHub 卡片并排
  - 效果参考：`#N Repository Of The Day / Year`（带 Trendshift logo 的大卡片）

- [x] **加入 Repobeats 活跃度图表**
  - 前置步骤：访问 https://repobeats.axiom.co → 用 GitHub 登录 → 选择仓库 → 生成嵌入代码
  - 位置：README 底部，`## 精选资源` 之后或单独的"项目状态"区块
  - 说明：展示 Issue 热度、Contributor 活跃度、Commit 频率，让访客看到"这个项目有人在维护"
  - 开源免费

---

## 完成后的第一屏结构（目标态）

```
标题：Awesome Zhuiju Free
副标题：追剧不踩坑，资源有人测
国内访问：Gitee 镜像链接                ← 新增，方便国内用户

emoji 短句描述（4行）

─────────────────────────────
[⭐ Stars] [网站] [已收录] [每日检测]   ← 单排大徽章
[FOSSA license scan]                    ← 许可证扫描小徽章
[Ask DeepWiki]                          ← 工具按钮
─────────────────────────────
[HelloGitHub 卡片] [Trendshift 卡片]    ← 荣誉卡片（待收录后加）
─────────────────────────────

浏览精选资源 · 推荐新资源 · 报告失效 · 贡献指南
觉得有用？点个 ⭐ 支持一下

---（分割线）

为什么选这个列表（对比表格）

---（分割线）

## 精选资源

...（精选资源内容）...

---（分割线）

Repobeats 活跃度图表                    ← 新增，放 README 底部
```

---

*每完成一项，在对应条目前的 `[ ]` 改为 `[x]`。*
