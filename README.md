# Cloudflare-VLESS-Deployer: 一站式 VLESS 配置转换与部署神器
## 项目简介
在网络代理与优化的场景里，高效管理 VLESS 配置一直是众多开发者、网络工程师及技术爱好者的核心诉求。本项目 “Cloudflare-VLESS-Deployer” 应运而生，巧妙借助 Cloudflare Workers/Pages 这一前沿平台的强大功能，全力打造一套精简且高效的脚本工具集，旨在一站式解决 VLESS 配置部署以及适配多类型 VPN 代理工具的难题。

## 项目亮点
1. **前沿平台赋能**：依托 Cloudflare Workers/Pages，充分享受 Cloudflare 遍布全球的优质 CDN 网络与强大算力支持。这不仅意味着更低的网络延迟、更高的响应速度，还为 VLESS 配置的稳定运行筑牢根基，无惧流量高峰与地域限制。
2. **多工具适配兼容**：深知用户对于 VPN 代理工具的多元选择，项目突破性地实现将 VLESS 服务器节点配置信息无缝转换至 Clash、Singbox、FlClash 等当下热门工具当中。无论你是 Clash 的忠实粉丝，偏好其简洁直观的规则配置；还是 Singbox 的专业级用户，追求极致性能；亦或是 FlClash 的新手尝鲜者，本项目都能满足你的适配需求。
3. **操作便捷高效**：摒弃复杂繁琐的传统手动配置流程，借助精心编写的脚本，仅需简单几步操作。初次使用者也能在详细的项目文档指引下，迅速上手，轻松完成部署与转换，大幅节省时间与精力成本。

## 功能详解
### 1. VLESS 配置部署
项目内置的脚本模块，精准对接 Cloudflare Workers/Pages 开发接口。用户只需按照既定格式，导入 VLESS 配置详情，脚本便会自动化完成一系列部署动作：从资源初始化、环境搭建，到配置信息上传、校验，全程无需人工干预，高效且准确，确保服务迅速上线，稳定运行。

### 2. 订阅内容转换
对于不同 VPN 代理工具各自的配置规则与语法要求，本项目通过深度解析与智能转换算法，将原始 VLESS 配置一键转化为对应工具可直接使用的订阅内容。例如，面向 Clash，输出适配其 `YAML` 格式的规则集，涵盖代理策略、分流规则等关键要素；针对 Singbox，则生成遵循其特有规范的配置文件，兼顾安全性与性能表现；给 FlClash 用户提供通俗易懂、易于导入的配置文本，方便新手快速上手。

## 使用场景
1. **个人开发者**：独自开发跨境项目、访问海外技术资源时，利用本项目快速搭建稳定 VLESS 代理，打破地域限制，加速开发流程，确保灵感不被卡顿的网络打断。
2. **小型团队协作**：团队成员分散各地，需共享统一高效的网络代理方案。借助 Cloudflare-VLESS-Deployer，可迅速部署内部专属 VLESS 服务，适配成员常用的 VPN 代理工具，保障沟通协作顺畅无阻。
3. **网络技术爱好者**：热衷于钻研各类网络代理技术、测试不同工具性能的玩家们，能利用本项目轻松切换不同配置，对比分析各工具在不同 VLESS 节点下的表现，探索网络优化的无限可能。

## 项目地址与文档
- GitHub 仓库地址：[具体仓库链接]，欢迎各位开发者 Star、Fork，一同参与项目迭代升级。
- 详细使用文档：项目 Wiki 页面完整收录从安装到高级配置的全流程指南，遇到问题还可在 Issues 区反馈交流，我们会有专业团队与热心社区成员为你答疑解惑。

## 技术栈与贡献指南
本项目核心技术涵盖 JavaScript、Node.js，深度调用 Cloudflare Workers API 实现平台交互。若你擅长前端优化、后端脚本编写，或是对 VPN 代理原理有着独到见解，热烈欢迎加入我们的开发团队！贡献指南详见项目根目录下的 `CONTRIBUTING.md` 文件，遵循开源规范，携手共创更强大的网络配置工具。

无论你是追求高效网络体验的普通用户，还是怀揣技术梦想的开发者，Cloudflare-VLESS-Deployer 都将是你探索 VLESS 配置世界的得力助手，快来开启便捷网络之旅吧！ 


# 如何使用?
## Workers 部署方法
<details>
<summary><code><strong>「 Workers 部署文字教程 」</strong></code></summary>

1. 部署 CF Worker：
   - 在 CF Worker 控制台中创建一个新的 Worker。
   - 将 worker.js 的内容粘贴到 Worker 编辑器中。
   - 将第 4 行 `userID` 修改成你自己的 **UUID** 。

2. 访问订阅内容：
   - 访问 `https://[YOUR-WORKERS-URL]/[UUID]` 即可获取订阅内容。
   - 例如 `https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10` 就是你的通用自适应订阅地址。
   - 例如 `https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub` Base64订阅格式，适用PassWall,SSR+等。
   - 例如 `https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash` Clash订阅格式，适用OpenClash等。
   - 例如 `https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb` singbox订阅格式，适用singbox等。

3. 给 workers绑定 自定义域： 
   - 在 workers控制台的 `触发器`选项卡，下方点击 `添加自定义域`。
   - 填入你已转入 CF 域名解析服务的次级域名，例如:`vless.google.com`后 点击`添加自定义域`，等待证书生效即可。
   - **如果你是小白，你现在可以直接起飞，不用再往下看了！！！**

4. 使用自己的`优选域名`/`优选IP`的订阅内容：
   - 如果你想使用自己的优选域名或者是自己的优选IP。
   - 打开 worker.js 文件，在第 12 行找到 `sub` 变量，将其修改为你部署的订阅生成器地址。例如 `let sub = 'sub.cmliussss.workers.dev';`，注意不要带https等协议信息和符号。
   - 注意，如果您使用了自己的订阅地址，要求订阅生成器的 `sub`域名 和 `[YOUR-WORKER-URL]`的域名 不同属一个顶级域名，否则会出现异常。您可以在 `sub` 变量赋值为 workers.dev 分配到的域名。

</details>

## Pages 上传 部署方法 **最佳推荐!!!** 
<details>
<summary><code><strong>「 Pages 上传文件部署文字教程 」</strong></code></summary>

1. 部署 CF Pages：
   - 下载 main.zip 文件，并点上 Star !!!
   - 在 CF Pages 控制台中选择 `上传资产`后，为你的项目取名后点击 `创建项目`，然后上传你下载好的 main.zip 文件后点击 `部署站点`。
   - 部署完成后点击 `继续处理站点` 后，选择 `设置` > `环境变量` > **制作**为生产环境定义变量 > `添加变量`。
     变量名称填写**UUID**，值则为你的UUID，后点击 `保存`即可。
   - 返回 `部署` 选项卡，在右下角点击 `创建新部署` 后，重新上传 main.zip 文件后点击 `保存并部署` 即可。

2. 访问订阅内容：
   - 访问 `https://[YOUR-PAGES-URL]/[YOUR-UUID]` 即可获取订阅内容。
   - 例如 `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10` 就是你的通用自适应订阅地址。
   - 例如 `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub` Base64订阅格式，适用PassWall,SSR+等。
   - 例如 `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash` Clash订阅格式，适用OpenClash等。
   - 例如 `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb` singbox订阅格式，适用singbox等。
   
3. 给 Pages绑定 CNAME自定义域：视频教程
   - 在 Pages控制台的 `自定义域`选项卡，下方点击 `设置自定义域`。
   - 填入你的自定义次级域名，注意不要使用你的根域名，例如：
     您分配到的域名是 `fuck.cloudns.biz`，则添加自定义域填入 `lizi.fuck.cloudns.biz`即可；
   - 按照 CF 的要求将返回你的域名DNS服务商，添加 该自定义域 `lizi`的 CNAME记录 `edgetunnel.pages.dev` 后，点击 `激活域`即可。
   - **如果你是小白，那么你的 pages 绑定`自定义域`之后即可直接起飞，不用再往下看了！！！**
   
4. 使用自己的`优选域名`/`优选IP`的订阅内容：
   - 如果你想使用自己的优选域名或者是自己的优选IP，可以参考 WorkerVless2sub GitHub 仓库中的部署说明自行搭建。
   - 在 Pages控制台的 `设置`选项卡，选择 `环境变量`> `制作`> `编辑变量`> `添加变量`；
   - 变量名设置为`SUB`，对应的值为你部署的订阅生成器地址。例如 `sub.cmliussss.workers.dev`，后点击 **保存**。
   - 之后在 Pages控制台的 `部署`选项卡，选择 `所有部署`> `最新部署最右的 ...`> `重试部署`，即可。
   - 注意，如果您使用了自己的订阅地址，要求订阅生成器的 `SUB`域名 和 `[YOUR-PAGES-URL]`的域名 不同属一个顶级域名，否则会出现异常。您可以在 `SUB` 变量赋值为 Pages.dev 分配到的域名。

</details>

## Pages GitHub 部署方法
<details>
<summary><code><strong>「 Pages GitHub 部署文字教程 」</strong></code></summary>

1. 部署 CF Pages：
   - 在 Github 上先 Fork 本项目，并点上 Star !!!
   - 在 CF Pages 控制台中选择 `连接到 Git`后，选中 `edgetunnel`项目后点击 `开始设置`。
   - 在 `设置构建和部署`页面下方，选择 `环境变量（高级）`后并 `添加变量`
     变量名称填写**UUID**，值则为你的UUID，后点击 `保存并部署`即可。

2. 访问订阅内容：
   - 访问 `https://[YOUR-PAGES-URL]/[YOUR-UUID]` 即可获取订阅内容。
   - 例如 `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10` 就是你的通用自适应订阅地址。
   - 例如 `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub` Base64订阅格式，适用PassWall,SSR+等。
   - 例如 `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash` Clash订阅格式，适用OpenClash等。
   - 例如 `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb` singbox订阅格式，适用singbox等。

3. 给 Pages绑定 CNAME自定义域
   - 在 Pages控制台的 `自定义域`选项卡，下方点击 `设置自定义域`。
   - 填入你的自定义次级域名，注意不要使用你的根域名，例如：
     您分配到的域名是 `fuck.cloudns.biz`，则添加自定义域填入 `lizi.fuck.cloudns.biz`即可；
   - 按照 CF 的要求将返回你的域名DNS服务商，添加 该自定义域 `lizi`的 CNAME记录 `edgetunnel.pages.dev` 后，点击 `激活域`即可。
   - **如果你是小白，那么你的 pages 绑定`自定义域`之后即可直接起飞，不用再往下看了！！！**

4. 使用自己的`优选域名`/`优选IP`的订阅内容：
   - 如果你想使用自己的优选域名或者是自己的优选IP，可以参考 WorkerVless2sub GitHub 仓库中的部署说明自行搭建。
   - 在 Pages控制台的 `设置`选项卡，选择 `环境变量`> `制作`> `编辑变量`> `添加变量`；
   - 变量名设置为`SUB`，对应的值为你部署的订阅生成器地址。例如 `sub.cmliussss.workers.dev`，后点击 **保存**。
   - 之后在 Pages控制台的 `部署`选项卡，选择 `所有部署`> `最新部署最右的 ...`> `重试部署`，即可。
   - 注意，如果您使用了自己的订阅地址，要求订阅生成器的 `SUB`域名 和 `[YOUR-PAGES-URL]`的域名 不同属一个顶级域名，否则会出现异常。您可以在 `SUB` 变量赋值为 Pages.dev 分配到的域名。

</details>


# 变量说明
| 变量名 | 示例 | 必填 | 备注 |  |
|--------|---------|-|-----|-----|
| UUID | `90cd4a77-141a-43c9-991b-08263cfe9c10` |✅| Powershell -NoExit -Command "[guid]::NewGuid()"|  |
| KEY | `token` |❌| 动态UUID秘钥，使用变量`KEY`的时候，将不再启用变量`UUID`|  |
| TIME | `7` |❌| 动态UUID有效时间(默认值:`7`天)|  |
| UPTIME | `3` |❌| 动态UUID更新时间(默认值:北京时间`3`点更新) |  |
| PROXYIP | `proxyip.fxxk.dedyn.io:443` |❌| 备选作为访问CFCDN站点的代理节点(支持自定义ProxyIP端口, 支持多ProxyIP, ProxyIP之间使用`,`或`换行`作间隔) |  |
| SOCKS5  | `user:password@127.0.0.1:1080` |❌| 优先作为访问CFCDN站点的SOCKS5代理(支持多socks5, socks5之间使用`,`或`换行`作间隔) ||
| GO2SOCKS5  | `blog.cmliussss.com`,`*.ip111.cn`,`*google.com` |❌| 设置`SOCKS5`变量之后，可设置强制使用socks5访问名单(`*`可作为通配符，`换行`作多元素间隔) ||
| ADD | `icook.tw:2053#官方优选域名` |❌| 本地优选TLS域名/优选IP(支持多元素之间`,`或`换行`作间隔) ||
| ADDAPI | [https://raw.github.../addressesapi.txt](https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesapi.txt) |❌| 优选IP的API地址(支持多元素之间`,`或 换行 作间隔) ||
| ADDNOTLS | `icook.hk:8080#官方优选域名` |❌| 本地优选noTLS域名/优选IP(支持多元素之间`,`或`换行`作间隔) ||
| ADDNOTLSAPI | [https://raw.github.../addressesapi.txt](https://raw.githubusercontent.com/cmliu/CFcdnVmess2sub/main/addressesapi.txt) |❌| 优选IP的API地址(支持多元素之间`,`或 换行 作间隔) ||
| ADDCSV | [https://raw.github.../addressescsv.csv](https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv) |❌| iptest测速结果(支持多元素, 元素之间使用`,`作间隔) ||
| DLS | `8` |❌| `ADDCSV`测速结果满足速度下限 ||
| TGTOKEN | `6894123456:XXXXXXXXXX0qExVsBPUhHDAbXXX` |❌| 发送TG通知的机器人token | 
| TGID | `6946912345` |❌| 接收TG通知的账户数字ID | 
| SUB | `VLESS.fxxk.dedyn.io` | ❌ | 优选订阅生成器域名 |  |
| SUBAPI | `SUBAPI.fxxk.dedyn.io` |❌| clash、singbox等 订阅转换后端 |  |
| SUBCONFIG | [https://raw.github.../ACL4SSR_Online_Full_MultiMode.ini](https://raw.githubusercontent.com/cmliu/ACL4SSR/main/Clash/config/ACL4SSR_Online_Full_MultiMode.ini) |❌| clash、singbox等 订阅转换配置文件 |  |
| SUBEMOJI | `false` |❌| 订阅转换是否启用Emoji(默认`true`) | |
| SUBNAME | `edgetunnel` |❌| 订阅名称 | |
| RPROXYIP | `false` |❌| 设为 true 即可强制获取订阅器分配的ProxyIP(需订阅器支持)|  |
| URL302 | `https://t.me/CMLiussss` |❌| 主页302跳转(支持多url, url之间使用`,`或`换行`作间隔, 小白别用) |  |
| URL | `https://blog.cmliussss.com` |❌| 主页反代伪装(支持多url, url之间使用`,`或`换行`作间隔, 乱设容易触发反诈) |  |
| CFPORTS | `2053`,`2096`,`8443` |❌| CF账户标准端口列表 |  |


## 注意事项
### **关于`KEY`与`UUID`：**
- 填入`KEY`变量后，将停用`UUID`变量，请确保**二者选其一使用**！
1. 填写`KEY`后，您的**永久订阅**地址为：`https://[YOUR-URL]/[YOUR-KEY]`；
2. 使用动态`UUID`订阅时：
   - 动态`UUID`需手动在永久订阅配置页内获得；
   - 临时订阅地址为：`https://[YOUR-URL]/[动态UUID]`；
   - 订阅有效时间为：**1个`TIME`周期**；
   - 节点可使用时间：**2个`TIME`周期**，即动态`UUID`失效后，节点仍可使用1个额外周期，但无法继续更新订阅。

### **关于`SOCKS5`与`PROXYIP`：**
- 填入`SOCKS5`后，将停用`PROXYIP`。请确保**二者选其一使用**！

### **关于`SUB`与`ADD*`变量：**
- 填入`SUB`后，将停用由`ADD*`类变量生成的订阅内容。请确保**二者选其一使用**！

### **当`SUB`和`ADD*`均为空时：**
- 脚本将自动生成基于CF随机IP的线路，每次更新订阅时会生成不同的随机IP，确保您的订阅不会失联！


# 实用技巧
本项目提供灵活的订阅配置方案，支持通过URL参数快速自定义订阅内容。
- 示例订阅地址： `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10` 

1. 更换**订阅生成器**的订阅地址

   快速切换订阅生成器至 `VLESS.fxxk.dedyn.io`：
   ```url
   https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub=VLESS.fxxk.dedyn.io
   ```

2. 更换**PROXYIP**的订阅地址

   快速更换PROXYIP为 `proxyip.fxxk.dedyn.io`：
   ```url
   https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?proxyip=proxyip.fxxk.dedyn.io
   ```

3. 更换**SOCKS5**的订阅地址

   快速设置SOCKS5代理为 `user:password@127.0.0.1:1080`：
   ```url
   https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?socks5=user:password@127.0.0.1:1080
   ```

- 通过提交多个参数快速修改的订阅地址

   例如同时修改**订阅生成器**和**PROXYIP**：
   ```url
   https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub=VLESS.fxxk.dedyn.io&proxyip=proxyip.fxxk.dedyn.io
   ```

4. 该项目部署的节点可通过节点PATH(路径)的方式，使用指定的`PROXYIP`或`SOCKS5`！！！**

- 指定 `PROXYIP` 案例
   ```url
   /proxyip=proxyip.fxxk.dedyn.io
   /?proxyip=proxyip.fxxk.dedyn.io
   /proxyip.fxxk.dedyn.io (仅限于域名开头为'proxyip.'的域名)
   ```

- 指定 `SOCKS5` 案例
   ```url
   /socks5=user:password@127.0.0.1:1080
   /?socks5=user:password@127.0.0.1:1080
   /socks://dXNlcjpwYXNzd29yZA==@127.0.0.1:1080
   /socks5://user:password@127.0.0.1:1080
   ```

5. **当你的`ADDAPI`可作为`PROXYIP`时，可在`ADDAPI`变量末位添加`?proxyip=true`，即可在生成节点时使用优选IP自身作为`PROXYIP`**
- 指定 `ADDAPI` 作为 `PROXYIP` 案例
   ```url
   https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesapi.txt?proxyip=true
   ```


# 优选IP：
| IP 地址或域名 | 端口 | 备注 |
| ---- | ---- | ---- |
| 104.26.13.42 | 443 | IPV4-🇭🇰香港 |
| hk.tgds.eu.org | 2096 | hk.tgds.eu.org-🇭🇰 |
| jp.tgds.eu.org | 2096 | jp.tgds.eu.org-🇯🇵 |
| us.tgds.eu.org | 2096 | us.tgds.eu.org-🇺🇸 |
| eu1.tgds.eu.org | 2096 | EU1-🇪🇺欧盟 |
| eu2.tgds.eu.org | 2096 | EU2-🇪🇺欧盟 |
| 172.67.68.204 | 443 | 🇭🇰香港01 |
| 104.26.12.42 | 443 | 🇭🇰香港02 |
| 172.67.68.204 | 2053 | 🇭🇰香港03 |
| 104.18.36.122 | 2053 | 🇭🇰香港04 |
| 1.1.1.91 | 443 | 🇯🇵日本-1-(CloudFlare数据中心) |
| 1.1.1.75 | 443 | 🇯🇵日本-2-(CloudFlare数据中心) |
| japan.com | 443 | 🌐japan.com |
| brazil.com | 443 | 🌐brazil.com |
| paizipai.top | 8443 | 🌐paizipai.top |
| tennis-point.de | 2053 | 🌐tennis-point.de |
| [2606:4700:10::6816:3045] | 443 | 🗽IPV6-1 |
| [2606:4700:3034::ac43:8e08] | 443 | 🗽IPV6-2 |
| [2606:4700:3033::ac43:a3fc] | 443 | 🗽IPV6-3 |


# 已适配客户端
### Windows
   - [v2rayN](https://github.com/2dust/v2rayN)
   - clash.meta（[FlClash](https://github.com/chen08209/FlClash)，[mihomo-party](https://github.com/mihomo-party-org/mihomo-party)，[clash-verge-rev](https://github.com/clash-verge-rev/clash-verge-rev)，[Clash Nyanpasu](https://github.com/keiko233/clash-nyanpasu)）
### IOS
   - Surge，小火箭
   - sing-box（[SFI](https://sing-box.sagernet.org/zh/clients/apple/)）
### 安卓
   - clash.meta（[ClashMetaForAndroid](https://github.com/MetaCubeX/ClashMetaForAndroid)，[FlClash](https://github.com/chen08209/FlClash)）
   - sing-box（[SFA](https://github.com/SagerNet/sing-box)）
### MacOS
   - clash.meta（[FlClash](https://github.com/chen08209/FlClash)，[mihomo-party](https://github.com/mihomo-party-org/mihomo-party)）
