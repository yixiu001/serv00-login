## serv00自动化批量保号，自定义时间自动登录一次面板，并且用“推送加”发送消息到微信

利用github Action以及python脚本实现

### 将代码fork到你的仓库并运行的操作步骤

#### 1. Fork 仓库

1. **访问原始仓库页面**：
    - 打开你想要 fork 的 GitHub 仓库页面。

2. **Fork 仓库**：
    - 点击页面右上角的 "Fork" 按钮，将仓库 fork 到你的 GitHub 账户下。

#### 2. 设置 GitHub Secrets

1. **配置 GitHub Secrets**
    - 转到你 fork 的仓库页面。
    - 点击 `Settings`，然后在左侧菜单中选择 `Secrets and variables`。
    - 添加以下 Secrets：
        - `ACCOUNTS_JSON`: 包含账号信息的 JSON 数据：
        - 
          ```json
          [
              {
                  "username": "user1",
                  "password": "pass1",
                  "panelnum": "服务器号，比如s5.serv00.com的就是5"
              },
              {
                  "username": "user2",
                  "password": "pass2",
                  "panelnum": "服务器号，比如s5.serv00.com的就是5"
              }
          ]
          ```
    - **“推送加TOKEN”获取方法**：
    - 在https://pushplus.plus/ 中申请TOKEN。
    - 添加以下 Secrets：
      - `PUSHPLUS_TOKEN`: 你的 推送加TOKEN。

#### 3. 启动 GitHub Actions

1. **配置 GitHub Actions**
    - 在你的 fork 仓库中，进入 `Actions` 页面。
    - 如果 Actions 没有自动启用，点击 `Enable GitHub Actions` 按钮以激活它。

2. **运行工作流**
    - GitHub Actions 将会根据你设置的定时任务（例如每三天一次）自动运行脚本。
    - 如果需要手动触发，可以在 Actions 页面手动运行工作流。

### 注意事项

- **保密性**: Secrets 是敏感信息，请确保不要将它们泄露到公共代码库或未授权的人员。
- **更新和删除**: 如果需要更新或删除 Secrets，可以通过仓库的 Secrets 页面进行管理。

通过以上步骤，你就可以成功将代码 fork 到你的仓库下并运行它了。
