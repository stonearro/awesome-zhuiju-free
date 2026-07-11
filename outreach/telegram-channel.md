# Telegram 频道建立指南

> 核心价值：把访客变成长期订阅者。流量引来了不沉淀就流失了。
> Telegram 频道对非 GitHub 用户更友好，普通追剧党更容易订阅。

---

## 一、为什么选 Telegram

| | Telegram 频道 | GitHub Watch | 微信群 |
|---|---|---|---|
| 门槛 | 低（有 App 即可） | 需要 GitHub 账号 | 需要好友邀请 |
| 触达率 | 高（推送通知） | 低（容易关掉） | 高但嘈杂 |
| 可自动化 | ✅ 可接 GitHub Actions | ✅ | ❌ |
| 适合受众 | 普通用户 + 技术用户 | 纯技术用户 | 普通用户 |
| 管理成本 | 极低（单向广播） | 无 | 高（回复、管理） |

---

## 二、频道创建步骤

### 2.1 基本信息设置

1. 打开 Telegram → 新建频道
2. 频道名称：`Awesome 追剧 Free`（或直接用 `追剧不踩坑`）
3. 频道类型：**Public**（公开，方便搜索和链接分享）
4. 频道用户名（URL）：建议设置为 `@awesome_zhuiju` 或 `@zhuiju_free`
5. 头像：用项目 Logo 或 zhuiju.me 的截图
6. 简介（About）：
   ```
   免费无广告追剧资源导航，每日自动检测可用性。
   
   GitHub：https://github.com/laoma2053/awesome-zhuiju-free
   网站：https://zhuiju.me
   
   订阅本频道获取资源更新播报。
   ```

### 2.2 在 README 和网站加入频道入口

README 的导航链接行加入 Telegram 链接：

```markdown
**[浏览精选资源](#精选资源)** · **[推荐新资源](...)** · **[报告失效](...)** · **[贡献指南](CONTRIBUTING.md)** · **[Telegram 频道](https://t.me/你的频道用户名)**
```

同时在大徽章行加一个 Telegram 徽章：

```markdown
<a href="https://t.me/你的频道用户名">
  <img src="https://img.shields.io/badge/Telegram-订阅频道-2CA5E0?style=for-the-badge&logo=telegram" alt="Telegram">
</a>
```

---

## 三、自动化：GitHub Actions → Telegram 推送

这是核心价值：每次资源更新或每日检测完成后，自动推送消息到频道，**零人工干预**。

### 3.1 创建 Telegram Bot

1. 在 Telegram 搜索 `@BotFather`
2. 发送 `/newbot`，按提示设置名称
3. 拿到 **Bot Token**（格式类似 `123456789:AAF...`）
4. 把 Bot 加入你的频道并设为管理员（可发消息权限）
5. 获取频道 Chat ID：
   - 公开频道直接用 `@频道用户名`（如 `@awesome_zhuiju`）

### 3.2 添加 GitHub Secrets

在 GitHub 仓库 → Settings → Secrets and variables → Actions，新增：

| Secret 名称 | 值 |
|---|---|
| `TELEGRAM_BOT_TOKEN` | BotFather 给的 Token |
| `TELEGRAM_CHAT_ID` | `@你的频道用户名` 或数字 Chat ID |

### 3.3 每日检测完成后自动推送

修改 `.github/workflows/check-availability.yml`，在 commit 步骤之后加入推送步骤：

```yaml
      - name: Send Telegram notification
        if: success()
        uses: appleboy/telegram-action@master
        with:
          to: ${{ secrets.TELEGRAM_CHAT_ID }}
          token: ${{ secrets.TELEGRAM_BOT_TOKEN }}
          format: markdown
          message: |
            📊 *每日可用性检测完成*
            
            检测时间：${{ env.TODAY }}（北京时间）
            
            详细结果见 README 或 [availability.json](https://github.com/laoma2053/awesome-zhuiju-free/blob/main/reports/availability.json)
            
            [👉 查看完整资源列表](https://zhuiju.me)
```

> 注意：需要在 workflow 里提前设置 `TODAY` 环境变量：
> ```yaml
>       - name: Set date
>         run: echo "TODAY=$(TZ='Asia/Shanghai' date +'%Y-%m-%d')" >> $GITHUB_ENV
> ```

### 3.4 新增资源时自动推送

修改 `.github/workflows/issue-to-resource-pr.yml`，在发布资源后加通知：

```yaml
      - name: Send Telegram notification for new resource
        if: steps.review.outputs.action == 'approved'
        uses: appleboy/telegram-action@master
        with:
          to: ${{ secrets.TELEGRAM_CHAT_ID }}
          token: ${{ secrets.TELEGRAM_BOT_TOKEN }}
          format: markdown
          message: |
            ✅ *新增资源：${{ steps.review.outputs.resource_name }}*
            
            感谢社区贡献！资源已通过审核并加入数据库。
            
            [👉 查看所有资源](https://zhuiju.me)
```

---

## 四、频道内容运营策略

### 发什么（内容类型）

| 类型 | 频率 | 示例 |
|---|---|---|
| 每日检测摘要 | 每天（自动） | "今日检测：X 个可访问，Y 个失效" |
| 新增资源播报 | 有新资源时（自动） | "新增：XXX，分类：在线影视" |
| 月度更新汇总 | 每月一次（手动） | 本月新增/下架资源汇总 |
| 资源失效提醒 | 不定期（手动） | "XXX 已连续3天无法访问，已标红" |
| 临时公告 | 偶尔（手动） | 维护通知、重大更新 |

### 不发什么

- 不发广告
- 不发无关内容
- 不做互动游戏（频道定位是播报，不是社群）

---

## 五、推广频道的方法

1. **README 徽章** — 上面已说，加在大徽章行
2. **CONTRIBUTING.md** — 在底部加一行 "订阅 Telegram 频道获取资源更新"
3. **Issue 自动回复** — 每次有人提新 Issue，issue-to-resource-pr.yml 的回复里加上频道地址
4. **发帖时附带** — 所有对外宣传帖子里都提一句 "Telegram 频道订阅资源更新通知"

---

## 六、执行清单

- [ ] 创建 Telegram 公开频道，设置用户名和简介
- [ ] 创建 Telegram Bot，获取 Token
- [ ] 在 GitHub Secrets 中添加 Bot Token 和 Chat ID
- [ ] 修改 `check-availability.yml` 加入每日推送步骤
- [ ] 修改 `issue-to-resource-pr.yml` 加入新资源推送步骤
- [ ] README 导航栏加入 Telegram 频道链接
- [ ] README 徽章行加入 Telegram 徽章
- [ ] 在所有宣传文案里加上频道链接
