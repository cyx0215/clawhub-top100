# 淘金小镇 (SkillRush Town)

ClawHub Skill 下载榜 Top100 每日快照，发现潜力 Skill。

## 功能

- 📊 每天自动抓取 ClawHub 下载榜 Top100
- 📈 与历史快照对比，发现排名/下载/星标变化
- 🔥 自动识别潜力 Skill（下载增长、星标增长、排名飙升）
- 🌐 GitHub Pages 静态站浏览

## 数据来源

通过 Convex API 查询 `skills:listPublicPageV4`，按下载量降序排列，分 4 页获取 Top100。

## 本地使用

```bash
# 抓取今日数据
python scripts/clawhub_daily.py --data-dir data

# 指定日期
python scripts/clawhub_daily.py --date 2026-05-06 --data-dir data

# 本地预览
cd site && python -m http.server 8093
# 打开 http://127.0.0.1:8093/
```

## 数据结构

```
data/
├── snapshots/YYYY-MM-DD.json   # 每日快照（完整 Top100 数据）
├── reports/YYYY-MM-DD.md       # 每日 Markdown 日报
├── latest.json                 # 最新快照软链
└── dates.json                  # 日期索引
```

## 自动化

通过 GitHub Actions 每天 UTC 02:00 (北京时间 10:00) 自动运行，数据推送到 `main` 分支。

## 致谢

灵感来自 [AI沃茨](https://mp.weixin.qq.com/s/sMVPbndu87sykzsAq7cXpg) 的淘金小镇文章，原始项目 [LearnPrompt/skillrush-town](https://github.com/LearnPrompt/skillrush-town)。
