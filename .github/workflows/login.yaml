name: Run Login Script

on:
  workflow_dispatch:
  schedule:
    - cron: "0 0 */3 * *"  # 每三天运行一次，可以根据需求调整时间
  push:
    branches:
      - main
jobs:
  login:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout 仓库代码
        uses: actions/checkout@v2

      - name: 设置 Python 环境
        uses: actions/setup-python@v2
        with:
          python-version: '3.x'  # 设置你希望使用的 Python 版本，建议使用稳定版本

      - name: Create accounts.json from environment variable
        run: echo "$ACCOUNTS_JSON" > accounts.json
        env:
            ACCOUNTS_JSON: ${{ secrets.ACCOUNTS_JSON }}  # 从GitHub Secrets中获取环境变量

      - name: 安装依赖
        run: |
          python -m pip install --upgrade pip
          pip install pyppeteer aiofiles requests
          pip install --upgrade pyppeteer

      - name: 运行登录脚本
        env:
          TELEGRAM_BOT_TOKEN: ${{ secrets.TELEGRAM_BOT_TOKEN }}
          TELEGRAM_CHAT_ID: ${{ secrets.TELEGRAM_CHAT_ID }}
          ACCOUNTS_JSON: ${{ secrets.ACCOUNTS_JSON }}
        run: |
          python login_script.py
