# Cursor-MXG

Cursor-MXG 是一个桌面工具，用于把固定中转服务中的模型接入 Cursor，并在本机管理中转账户、Keys、模型和调用记录。

本仓库是 **Cursor-MXG 的公开下载与用户文档仓库**。应用源码、构建流程和签名密钥不在本仓库中；这里只保存用户文档、已发布的安装包、更新签名和更新清单。

> Cursor-MXG 是独立项目，与 Cursor 及其开发者无隶属或背书关系。使用中转模型时，请求内容会发送到中转服务，并受该服务的计费和隐私规则约束。

## 下载

前往 [最新版本](https://github.com/xiaomayisjh/cursor-mxg-releases/releases/latest)，展开 **Assets**，按系统选择文件：

- **Windows x64（推荐）**：`Cursor-MXG_<版本>_x64-setup.exe`
- **Windows x64 便携版**：`cursor-mxg-<版本>-windows-amd64.zip`
- **macOS Apple 芯片**：`Cursor-MXG_<版本>_aarch64.app.tar.gz`
- **macOS Intel 芯片**：`Cursor-MXG_<版本>_x64.app.tar.gz`
- **Ubuntu / Debian x64**：`Cursor-MXG_<版本>_amd64.deb`
- **Fedora / RHEL / openSUSE x64**：`Cursor-MXG-<版本>-1.x86_64.rpm`
- **其他 Linux x64**：`Cursor-MXG_<版本>_amd64.AppImage`

`.sig` 文件和 `latest.json`、`update.json`、`portable-latest.json` 是应用自动更新使用的签名与清单，普通用户不需要手动打开。

详细步骤见[安装与更新](docs/installation.md)。

## 快速开始

```text
下载安装 Cursor-MXG
        ↓
登录或注册中转账户
        ↓
创建或确认可用的中转 Key
        ↓
在“模型广场”加入模型
        ↓
在“已加入模型”初始化本地 CA
        ↓
开启“接管 Cursor”并手动重启 Cursor
        ↓
在 Cursor 新对话中选择已加入的模型
```

1. 启动 Cursor-MXG，通过独立登录窗口登录或注册中转账户。
2. 打开 **中转 Keys**，创建或确认一个状态正常、已保存密钥的 Key。
3. 打开 **模型广场**，选择分组和模型，再选择要绑定的 Key。
4. 打开 **已加入模型**，点击 **初始化 CA**，按提示完成本地证书信任。
5. 开启 **接管 Cursor**。保存 Cursor 中的工作，然后手动重启 Cursor。
6. 在 Cursor 中新建对话，选择刚加入的模型。Cursor 的 **Auto** 仍使用官方路由。

完整说明见[首次配置与日常使用](docs/getting-started.md)。

## 用户文档

```text
docs/
├── installation.md       各系统下载、安装、更新与卸载
├── getting-started.md    登录、Key、模型、CA 和接管 Cursor
├── troubleshooting.md    常见故障、系统拦截与反馈信息
└── privacy-security.md   数据流、凭据存储和安全边界
```

- [安装与更新](docs/installation.md)
- [首次配置与日常使用](docs/getting-started.md)
- [故障排查](docs/troubleshooting.md)
- [隐私与安全说明](docs/privacy-security.md)

## 使用须知

- 使用中转模型期间，需要保持 Cursor-MXG 在后台运行；关闭主窗口后，应用仍保留在系统托盘。
- 需要完全退出或卸载时，先在 **已加入模型** 中关闭 **接管 Cursor**，让应用恢复接管前的 Cursor 配置。
- 同一模型绑定到不同 Key 时，会生成相互独立的本地模型；停用或删除 Key 后，应用不会自动切换到另一个 Key。
- 支付创建、第三方身份绑定、TOTP 注册和 Passkey 注册目前不在桌面端提供。服务端功能开关也可能隐藏部分页面。
- 请只从本仓库的 [Releases](https://github.com/xiaomayisjh/cursor-mxg-releases/releases) 下载。不要从不明来源获取安装包或登录令牌。

## 更新

Cursor-MXG 启动后会检查新版本，也可以在 **系统设置 → 软件更新** 中手动检查并安装。更新包由应用内置公钥验证，下载地址指向本仓库的公开 Release。

## 获取帮助

请先查看[故障排查](docs/troubleshooting.md)。问题仍未解决时，可在 [Issues](https://github.com/xiaomayisjh/cursor-mxg-releases/issues) 提交反馈，并附上：

- Cursor-MXG 版本、操作系统和 CPU 架构；
- Cursor 版本；
- 可以复现问题的步骤；
- 完整错误文字和大致发生时间。

请勿提交密码、访问令牌、刷新令牌、完整 API Key、Cookie、私密对话内容或其他敏感数据。

## 本仓库中的更新文件

- `latest.json`：当前 Tauri 桌面更新清单；
- `update.json`：旧版客户端更新清单；
- `portable-latest.json`：Windows 便携更新清单；
- `*.sig`：更新包签名。

这些文件供客户端自动读取。安装包、签名和清单公开可下载，私有源码与构建历史不会发布到本仓库。
