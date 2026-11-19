# 松伴

黑客松团队协作应用。注册或访客进入后，可以建队、确认方向、分工、讨论、领任务并做交付核对。

这份仓库只保留当前默认可运行的部分，来自 [Fantacy567/songban](https://github.com/Fantacy567/songban)。未纳入学习平台、规划文档、演示服务和历史页面。

## 启动

需要 Python 3.12。

```sh
python3.12 -m venv .venv
.venv/bin/python -m pip install -r requirements.lock.txt
cp .env.example .env
.venv/bin/python -m uvicorn app.main:app --host 127.0.0.1 --port 8893
```

打开 <http://127.0.0.1:8893/>。健康检查是 <http://127.0.0.1:8893/health>。

不配置模型密钥、短信或邮箱时，页面和团队流程仍可在本机使用。需要这些能力时，把对应项写进 `.env`，不要把真实密钥提交到 Git。

SQLite 默认在 `data/collab.sqlite3`。

## 代码在哪

- `app/main.py`：服务入口、数据库和页面。
- `app/studio.py`、`app/team_core.py`：账号与团队协作，接口前缀 `/api/core`。
- `static/songban.html` 及同目录的 `songban-*.js` / `songban-*.css`：当前前台。
- `static/workbench/`：讨论工作台的已构建页面。
- `plugins/`：个人工具连接器，由网页里的安装流程读取。

版权说明见 [COPYRIGHT.md](COPYRIGHT.md)。
