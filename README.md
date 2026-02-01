# Apprise - 懒猫云应用

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![LazyCat Cloud](https://img.shields.io/badge/LazyCat-Cloud-blue)](https://lazycat.cloud)

Apprise 是一个强大的推送通知服务,支持几乎所有主流平台的通知推送。

## ✨ 功能特性

- 📱 **多平台支持**: 支持 70+ 种通知服务(钉钉、企业微信、Telegram、Slack 等)
- 🔧 **灵活配置**: 支持 YAML、JSON 等多种配置格式
- 🎛️ **管理界面**: 提供 Web 管理界面,方便配置和测试
- 🔌 **插件系统**: 支持自定义插件扩展
- 📎 **附件支持**: 支持发送附件(图片、文件等)

## 📦 安装说明

### 通过懒猫应用商店安装

1. 打开懒猫云控制台
2. 进入应用商店
3. 搜索 "Apprise"
4. 点击安装

### 配置参数

安装时需要配置以下参数:

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| 工作进程数 | 数字 | 1 | 处理通知的工作进程数量 (1-10) |
| 启用管理模式 | 布尔 | true | 是否启用 Web 管理界面 |

## 🚀 使用指南

### 访问管理界面

安装完成后,通过以下地址访问:

```
https://apprise.你的懒猫域名
```

### API 使用

发送通知的基本 API:

```bash
# 发送简单文本通知
curl -X POST https://apprise.你的懒猫域名/notify \
  -d "urls=mailto://user:pass@gmail.com" \
  -d "body=Hello World"

# 发送带标题的通知
curl -X POST https://apprise.你的懒猫域名/notify \
  -d "urls=tgram://bottoken/ChatID" \
  -d "title=重要通知" \
  -d "body=这是通知内容"
```

### 配置文件管理

配置文件存储在 `/lzcapp/var/config` 目录:

```yaml
# apprise.yml
urls:
  - mailto://user:pass@gmail.com
  - tgram://bottoken/ChatID
  - dingding://token
```

### 插件管理

自定义插件放置在 `/lzcapp/var/plugin` 目录:

```python
# /lzcapp/var/plugin/my_plugin.py
from apprise.plugins.NotifyBase import NotifyBase

class NotifyMyService(NotifyBase):
    # 自定义插件实现
    pass
```

## 📚 支持的通知服务

### 国内常用服务

- **钉钉**: `dingding://token`
- **企业微信**: `wxwork://corpid/agentid/secret`
- **飞书**: `feishu://token`
- **Server酱**: `schan://sendkey`

### 国际主流服务

- **Telegram**: `tgram://bottoken/ChatID`
- **Slack**: `slack://TokenA/TokenB/TokenC`
- **Discord**: `discord://WebhookID/WebhookToken`
- **Email**: `mailto://user:pass@domain.com`

### 更多服务

完整支持列表请访问: https://github.com/caronc/apprise/wiki

## 🔧 高级配置

### 调整工作进程数

根据通知量调整进程数:

- **轻量使用** (< 100 通知/天): 1 个进程
- **中等使用** (100-1000 通知/天): 2-3 个进程
- **重度使用** (> 1000 通知/天): 4-10 个进程

### 持久化存储

应用使用以下目录存储数据:

```
/lzcapp/var/config  - 配置文件
/lzcapp/var/plugin  - 自定义插件
/lzcapp/var/attach  - 附件文件
```

## 📖 常见问题

### Q: 如何添加新的通知服务?

A: 在管理界面中点击 "Add Service",选择服务类型并填写配置参数。

### Q: 发送失败怎么办?

A: 检查以下几点:
1. 服务配置是否正确
2. 网络连接是否正常
3. 查看应用日志排查错误

### Q: 支持批量发送吗?

A: 支持。在 API 中指定多个 `urls` 参数即可同时发送到多个服务。

## 🔗 相关链接

- **官方网站**: https://github.com/caronc/apprise
- **文档**: https://github.com/caronc/apprise/wiki
- **懒猫开发者文档**: https://developer.lazycat.cloud

## 📄 许可证

MIT License - 详见 [LICENSE](https://github.com/caronc/apprise/blob/master/LICENSE)

## 🤝 贡献

欢迎提交问题和改进建议!

---

**开发者**: Chris Caron
**懒猫云适配**: LazyCat Community
**版本**: 1.0.0
# apprise-lzcapp
