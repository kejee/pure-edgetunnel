# 🚀 pure-edgetunnel

> 🛡️ 本项目基于官方开源项目 [cmliu/edgetunnel](https://github.com/cmliu/edgetunnel) 的最新版本 **`v2.1.20260722191426`** 进行脱敏重构与纯净化优化。

---

## ✨ 项目特性

- 🔒 **纯净无后门**：全盘清除了原版的第三方埋点、遥测及隐藏追踪，全闭环运行。
- 📦 **纯本地 HTML 闭环**：所有前端页面（登录页、后台管理页、错误页）直接内嵌到单文件 `_worker.js` 中，无需依赖外部 Pages 托管，无循环重定向与 522 超时问题。
- ⚡ **高性能边缘网关**：支持 VLESS、Trojan、Shadowsocks 等多协议代理。
- 🌐 **可视化后台**：支持在线配置修改、查看日志、动态管理优选 IP 与反代跳板（ProxyIP）。
- 📑 **全自动订阅转换**：支持 Clash, Sing-box, Surge, Quantumult X, Loon 等客户端原生格式一键导出。

---

## 📖 声明与鸣谢

- 感谢原作者 [cmliu](https://github.com/cmliu) 及其开源项目 [edgetunnel](https://github.com/cmliu/edgetunnel) 提供的优秀核心基础。
- 原官方仓库地址：[https://github.com/cmliu/edgetunnel](https://github.com/cmliu/edgetunnel)

---

## 🛠️ 部署指南 (Cloudflare Worker)

### 方式一：GitHub 联动自动部署（推荐）

1. **Fork 或导入仓库**：
   将本项目代码 Fork 或上传导入到你自己的 GitHub 账号（仓库名推荐命名为 `pure-edgetunnel`）。

2. **在 Cloudflare 创建 Worker**：
   - 登录 [Cloudflare Dashboard](https://dash.cloudflare.com)。
   - 进入 `Workers 与 Pages` > `概述` > 点击 `创建`。
   - 选择 `Workers` 页签，点击 `创建 Worker`，填入项目名称并点击 `部署`。

3. **关联 GitHub 自动构建（或直接复制代码）**：
   - 在 Worker 详情页面，点击 `设置` > `变量与绑定` > `环境变量`：
     - **`ADMIN`**：添加环境变量 `ADMIN`，值为你的管理员登录密码（如 `MyPassword123`）。
     - **`UUID`**：（可选）填入你的 UUID（不填则由系统自动算法生成）。
   - 在 `设置` > `变量与绑定` > `KV 命名空间绑定`：
     - 点击 `添加`，变量名称填 **`KV`**（必须为大写），绑定一个你新建的 KV 数据库。

4. **绑定自定义域名**：
   - 点击 `设置` > `触发器` > `自定义域名` > `添加自定义域名`。
   - 填入你已解析在 Cloudflare 的域名（例如 `sub.yourdomain.com` 或你的主域名）。

---

### 方式二：Cloudflare 后台在线复制代码部署

1. 在 Cloudflare 创建 Worker。
2. 点击 `编辑代码`，将仓库根目录下的 `_worker.js` 中的**全部代码**全量复制粘贴到编辑器中。
3. 点击右上角 `保存并部署`（Save and Deploy）。
4. 在 `设置` > `变量` 中配置 `ADMIN` 密码及大写的 `KV` 数据库绑定即可。

---

## 🔐 环境变量说明

| 变量名称 | 必填 | 默认值 | 示例 / 说明 |
| :--- | :---: | :---: | :--- |
| **`ADMIN`** | **是** | 无 | 管理员后台密码（如 `AdminPass123`） |
| **`KV`** | **是** | 无 | KV 数据库绑定名称（**必须全大写 `KV`**） |
| **`UUID`** | 否 | 算法生成 | 用户识别 UUID（格式如 `de0b958f-1a3b-4421-a477-743126f5520e`） |
| **`KEY`** | 否 | 默认密钥 | 加密传输密钥 |
| **`PROXYIP`** | 否 | 无 | 强制指定的跳板落地 IP（解锁 ChatGPT/流媒体） |

---

## ⚠️ 免责声明 (Disclaimer)

1. **用途限制**：本项目仅供个人学术研究、网络技术学习及安全测试使用，请勿用于任何违反使用者所在国家或地区法律法规的用途。
2. **免责保证**：本项目的代码均按“原样”（AS IS）提供。使用者须自行承担因使用、部署或衍生修改该项目所产生的一切法律责任与风险，开发者及贡献者概不承担任何直接或间接责任。
3. **第三方资源**：项目中引用的任何公开开源 API 均来自网络开源社区，项目不对第三方服务的可用性、准确性或安全性作任何形式的担保。

---

## 📝 开源协议

本项目继承原项目的开源协议 [MIT / GPL License](LICENSE)。
