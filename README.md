# weather-trigger
定时触发天气 API
非常好，那我来帮你**生成一个完整的 GitHub 项目结构**，这个项目将专门用于触发你部署在 PythonAnywhere 上的天气 API，包含以下内容：

---

## ✅ 项目目标

* 利用 GitHub Actions 定时触发 API
* 无需本地运行，完全基于云端免费运行
* 每 10 分钟获取一次实时天气
* 每 6 小时获取一次未来天气
* 提供清晰的文档说明（`README.md`）

---

## 📁 项目结构如下（项目名建议：`weather-trigger`）

```
weather-trigger/
├── .github/
│   └── workflows/
│       └── weather_trigger.yml     # GitHub Actions 工作流文件
├── README.md                       # 项目说明文件
```

---

### 🔧 `.github/workflows/weather_trigger.yml`

```yaml
name: Trigger Weather API

on:
  schedule:
    - cron: '*/10 * * * *'  # 每10分钟调用一次 fetch 实时天气
    - cron: '0 */6 * * *'   # 每6小时调用一次 forecast 天气
  workflow_dispatch:        # 可手动运行

jobs:
  trigger-weather:
    runs-on: ubuntu-latest
    steps:
      - name: Trigger Real-time Weather Fetch
        run: |
          curl -X POST https://nexus8023.pythonanywhere.com/api/weather/fetch

      - name: Trigger Forecast Weather Fetch
        run: |
          curl -X POST https://nexus8023.pythonanywhere.com/api/weather/forecast
```

---

### 📝 `README.md`

```markdown
# Weather Trigger with GitHub Actions ☁️⏰

本项目用于定时触发部署在 PythonAnywhere 上的天气服务接口，获取实时和未来天气数据。

## 🔧 项目用途

- 每 10 分钟触发一次 `/api/weather/fetch`（实时天气）
- 每 6 小时触发一次 `/api/weather/forecast`（未来天气）
- 通过 GitHub Actions 的免费定时任务执行，无需服务器或本地运行

## 🗂 项目结构

```

.github/workflows/weather\_trigger.yml   # GitHub Actions 工作流文件
README.md                               # 项目说明文档

```

## 🛠 如何使用

### 1️⃣ 创建 GitHub 仓库

1. 登录 GitHub → 创建一个新仓库（例如：`weather-trigger`）
2. 勾选 `Initialize with README`

### 2️⃣ 上传工作流文件

1. 打开你的仓库 → 点击 `Add file` → `Create new file`
2. 文件名填写：`.github/workflows/weather_trigger.yml`
3. 将 [`weather_trigger.yml`](./.github/workflows/weather_trigger.yml) 中的内容复制进去
4. 提交保存

### 3️⃣ 观察定时任务运行

1. 打开你的仓库 → 点上方 `Actions` 标签页
2. 查看任务是否按计划运行
3. 你也可以手动点击 `Run workflow` 来测试任务是否能正常访问你的 API

## ✅ 注意事项

- 你的 Flask 接口必须部署在 PythonAnywhere 或其他公网平台
- PythonAnywhere 免费账户每天有请求频率限制，但对你这个轻量使用完全足够
- GitHub Actions 免费版每月有 2000 分钟，完全覆盖你计划的频率

## 📬 联系

如果你是本项目作者，可以在此添加联系方式或其他说明。
```

---

## ✅ 下一步：怎么使用这份代码

你只需：

1. 登录 GitHub 创建仓库（如 `weather-trigger`）
2. 上传 `.github/workflows/weather_trigger.yml` 和 `README.md`（我可以打包为 zip 也可以一步步教你上传）
3. 每 10 分钟和 6 小时，GitHub 就会帮你触发接口，自动写入天气数据，无需再托管任务在 PythonAnywhere


