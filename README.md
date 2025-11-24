# 飞利浦 Hue Play HDMI 同步盒

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/hacs/integration)
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-2025.2%2B-green.svg)](https://www.home-assistant.io/)

飞利浦 Hue Play HDMI 同步盒的 Home Assistant 自定义集成，支持 4K 和 8K 型号。

**原版仓库**: [mvdwetering/huesyncbox](https://github.com/mvdwetering/huesyncbox)

## 🚀 快速开始

[![添加HACS仓库](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=buynow2010&repository=Hue-Sync-Box&category=integration)

**一键安装**：点击上方徽章，直接在 HACS 中添加此仓库

## 功能特性

### 🎛️ 设备控制

- **电源开关** - 开启/关闭同步盒
- **灯光同步** - 启用/禁用灯光同步
- **同步强度** - 柔和/适中/高/强烈四档可选
- **同步模式** - 视频/音乐/游戏三种模式
- **HDMI 输入选择** - 切换不同的 HDMI 输入源
- **亮度控制** - 调节灯光亮度
- **娱乐区域选择** - 选择控制的 Hue 灯光区域

### 📊 状态监控

- **HDMI 输入连接状态** - 监控各输入端口连接状态
- **杜比视界兼容** - 开启/关闭杜比视界支持（仅 4K 型号）
- **LED 指示模式** - 设置设备 LED 指示灯模式
- **网桥连接状态** ⁺ - 监控 Hue 网桥连接
- **网桥 ID** ⁺ - 显示连接的 Hue 网桥 ID
- **IP 地址** ⁺ - 显示设备 IP 地址
- **WiFi 信号质量** ⁺ - 监控 WiFi 连接质量
- **内容信息** ⁺ - 显示当前播放内容信息

⁺ 标记的实体默认禁用，可在设置中启用

### ⚙️ 服务（Actions）

| 服务名称 | 说明 |
|---------|------|
| `set_bridge` | 设置同步盒使用的 Hue 网桥 |
| `set_sync_state` | 一次性设置多个同步状态（推荐使用，确保正确顺序且更高效） |

## 行为说明

以下是设备的正常行为（由同步盒硬件决定）：

- 启用灯光同步时会自动开启设备电源
- 设置同步模式时会自动开启电源并启动该模式的灯光同步
- 修改多个设置时顺序很重要（如强度设置会应用到当前选中的模式）
- 使用 `set_sync_state` 服务可避免顺序问题，它会自动处理顺序且更高效

## 系统要求

### Home Assistant

- **版本**: 2025.2.0+
- **Python**: 3.11+

## 安装方式

### 方法一：通过 HACS 安装（推荐）

[![添加HACS仓库](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=buynow2010&repository=Hue-Sync-Box&category=integration)

**一键安装**：点击上方徽章，自动跳转到 HACS 添加页面

**手动添加**：

1. 确保已安装 [HACS](https://hacs.xyz/)
2. 在 HACS 中点击右上角菜单 → **自定义存储库**
3. 添加仓库地址：`https://github.com/buynow2010/Hue-Sync-Box`
4. 类别选择：**集成（Integration）**
5. 点击 **添加**
6. 在 HACS 中搜索 "**飞利浦 Hue Play HDMI 同步盒**"
7. 点击 **下载**
8. 重启 Home Assistant

### 方法二：手动安装

1. 下载本仓库的 [最新版本](https://github.com/buynow2010/Hue-Sync-Box/releases)
2. 解压后将 `custom_components/huesyncbox` 文件夹复制到你的 Home Assistant 配置目录的 `custom_components/` 目录下
3. 重启 Home Assistant

## 配置方式

### 自动发现（推荐）

大多数情况下，Home Assistant 会自动发现网络中的同步盒设备。

在通知中心查看发现的设备，点击配置即可。

### 手动添加

1. 进入 **设置** → **设备与服务**
2. 点击右下角 **+ 添加集成**
3. 搜索 "**飞利浦 Hue Play HDMI 同步盒**" 或 "**Philips Hue Sync Box**"
4. 按照提示完成配置

> **注意**: 请先使用飞利浦 Hue 官方 App 完成同步盒的初始设置，确保设备正常工作后再添加到 Home Assistant。

## 故障排除

### 设备无法被发现

1. **检查网络连接**：确保同步盒和 Home Assistant 在同一网络
2. **检查防火墙**：确保防火墙没有阻止设备发现
3. **手动添加**：尝试通过手动添加方式配置
4. **检查官方 App**：确保设备在官方 Hue App 中正常工作

### 无法连接设备

1. **检查 IP 地址**：确认设备 IP 地址没有变化
2. **重新配置**：删除集成后重新添加
3. **重启设备**：尝试重启同步盒和 Home Assistant
4. **检查固件**：确保同步盒固件是最新版本

### 实体不显示

1. **检查禁用状态**：部分实体默认禁用，需在设备页面手动启用
2. **刷新页面**：清除浏览器缓存或强制刷新（Ctrl+F5）
3. **重新加载集成**：在集成页面点击"重新加载"

### 控制命令无响应

1. **检查设备状态**：确保同步盒在线且正常工作
2. **检查网桥连接**：确保 Hue 网桥连接正常
3. **检查日志**：查看 Home Assistant 日志获取错误信息
4. **使用官方 App 测试**：确认设备在官方 App 中可正常控制

## 更新日志

查看 [Releases](https://github.com/buynow2010/Hue-Sync-Box/releases) 了解详细更新内容。

## 支持与反馈

- **问题反馈**: [GitHub Issues](https://github.com/buynow2010/Hue-Sync-Box/issues)
- **功能请求**: [GitHub Issues](https://github.com/buynow2010/Hue-Sync-Box/issues)

## 友情链接

### 🏠 Home Assistant 中文网

[![Home Assistant 中文网](https://img.shields.io/badge/Home%20Assistant-%E4%B8%AD%E6%96%87%E7%BD%91-blue?style=for-the-badge&logo=home-assistant)](https://www.hasscn.top/)

[**Home Assistant 中文网 (hasscn.top)**](https://www.hasscn.top/) - 最全面的免费 Home Assistant 中文站点，提供：

- 🚀 **Home Assistant OS 极速版** - 专为中国优化的加速版系统
- ⚡ **HACS 极速版** - 使用国内镜像加速插件下载
- 📚 **中文文档教程** - 详细的安装配置指南
- 💬 **社区支持** - 微信公众号：老王杂谈说

**特别适合国内用户使用，解决下载慢、连接困难等问题！**

## 许可证

Apache License 2.0 - 详见 [LICENSE](LICENSE)

## 致谢

- [mvdwetering/huesyncbox](https://github.com/mvdwetering/huesyncbox) - 原作者项目
- [Home Assistant](https://www.home-assistant.io/) - 开源智能家居平台
- [HACS](https://hacs.xyz/) - Home Assistant 社区商店

---

**如果本项目对你有帮助，欢迎 Star 支持！** ⭐
