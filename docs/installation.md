# 安装与更新

## 安装前准备

使用 Cursor-MXG 前，请确认：

- 已安装并至少启动过一次 Cursor；
- 拥有可用的中转账户，或能够在登录窗口中完成注册；
- 网络能够访问 GitHub Releases、中转控制台和模型接口；
- 当前系统和 CPU 架构与安装包匹配。

所有正式安装包都发布在本仓库的 [Releases](https://github.com/xiaomayisjh/cursor-mxg-releases/releases)。建议始终从[最新版本](https://github.com/xiaomayisjh/cursor-mxg-releases/releases/latest)下载。

## Windows x64

### 安装版（推荐）

1. 下载 `Cursor-MXG_<版本>_x64-setup.exe`。
2. 双击安装程序并完成安装。
3. 从开始菜单启动 Cursor-MXG。

当前安装包可能没有 Windows 商业代码签名，因此 SmartScreen 可能显示“Windows 已保护你的电脑”。确认下载地址属于 `github.com/xiaomayisjh/cursor-mxg-releases` 后，可选择 **更多信息 → 仍要运行**。如果无法确认来源，请取消安装。

### 便携版

1. 下载 `cursor-mxg-<版本>-windows-amd64.zip`。
2. 将压缩包完整解压到当前用户有写入权限的固定目录，例如 `D:\Apps\Cursor-MXG`。
3. 运行目录中的 `cursor-mxg.exe`。
4. 后续不要随意移动或删除正在使用的程序文件；自动更新需要替换该可执行文件。

不要直接在压缩包预览窗口中运行程序，也不要把便携版放在只读目录中。

## macOS

先确认 Mac 的处理器：打开 **苹果菜单 → 关于本机**。

- Apple M 系列芯片：下载 `Cursor-MXG_<版本>_aarch64.app.tar.gz`；
- Intel 芯片：下载 `Cursor-MXG_<版本>_x64.app.tar.gz`。

安装步骤：

1. 解压 `.app.tar.gz` 文件。
2. 将 `Cursor-MXG.app` 移到 **应用程序** 文件夹。
3. 首次启动时，按住 Control 点击应用，选择 **打开**，再确认启动。

当前应用可能没有 Apple 公证。如果 macOS 仍阻止打开，请先确认文件来自本仓库，然后在 **系统设置 → 隐私与安全性** 中允许打开。仅在确认下载来源无误后，才使用终端移除隔离标记：

```bash
xattr -dr com.apple.quarantine /Applications/Cursor-MXG.app
```

## Linux x64

当前 Linux 发布包仅提供 x86_64 / amd64 架构。

### Ubuntu / Debian

下载 `.deb` 后安装：

```bash
sudo apt install ./Cursor-MXG_<版本>_amd64.deb
```

### Fedora / RHEL

下载 `.rpm` 后安装：

```bash
sudo dnf install ./Cursor-MXG-<版本>-1.x86_64.rpm
```

### AppImage

下载 `.AppImage` 后执行：

```bash
chmod +x Cursor-MXG_<版本>_amd64.AppImage
./Cursor-MXG_<版本>_amd64.AppImage
```

如果 AppImage 报 FUSE 相关错误，请安装发行版提供的 FUSE 运行库，或优先使用适合当前发行版的 `.deb` / `.rpm` 包。

## 首次启动

首次运行时，系统可能要求网络访问权限。初始化本地 CA 时还可能要求管理员权限，以便让系统或 Cursor 信任本地证书。Cursor-MXG 不会在登录窗口之外要求输入中转账户密码。

安装完成后，继续阅读[首次配置与日常使用](getting-started.md)。

## 自动更新

Cursor-MXG 会在启动、窗口重新获得焦点、网络恢复时检查更新，并在持续运行期间定期检查。也可以打开 **系统设置 → 软件更新**，手动执行：

1. 点击 **检查更新**；
2. 有新版本时点击安装；
3. 等待应用完成下载、签名验证和替换；
4. 按界面提示重新启动应用。

应用使用内置公钥验证更新签名。更新清单和安装包均从本公开仓库下载，不需要访问私有源码仓库。

如果自动更新失败，可退出 Cursor-MXG，从 [Releases](https://github.com/xiaomayisjh/cursor-mxg-releases/releases/latest) 手动下载新版安装包。便携版用户应先备份当前目录，再把新版解压到有写入权限的位置。

## 完全退出

关闭主窗口不会退出后台进程，应用会继续保留在系统托盘。需要完全退出时：

1. 如果正在接管 Cursor，先打开 **已加入模型**，关闭 **接管 Cursor**；
2. 确认 Cursor 配置已经恢复；
3. 在系统托盘中右键 Cursor-MXG，选择 **退出**。

接管期间直接退出会停止本机代理，但 Cursor 可能仍指向该代理，从而导致请求失败。

## 卸载

卸载前务必先关闭 **接管 Cursor**。

- Windows 安装版：在 **设置 → 应用 → 已安装的应用** 中卸载 Cursor-MXG；
- Windows 便携版：退出程序后删除便携目录；
- macOS：退出程序后把 `Cursor-MXG.app` 移到废纸篓；
- Linux：使用发行版包管理器卸载，AppImage 用户直接删除文件。

卸载应用不等同于删除中转账户或服务端数据。需要删除或停用 Key 时，请在卸载前通过 **中转 Keys** 页面操作。
