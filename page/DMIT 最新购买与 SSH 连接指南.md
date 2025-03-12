# DMIT 最新购买与 SSH 连接指南

对于初次接触 DMIT 的用户，可能在注册、购买以及使用过程中会遇到一些问题。本文将提供一份详细的教程，帮助您快速完成购买流程，并学会如何通过 SSH 连接您的 VPS。

👉 [【推荐收藏】2025年 DMIT 最新优惠活动整理汇总 - 每日更新可用优惠套餐](https://bit.ly/dmit_coupon)

## 如何购买 DMIT VPS

以下是购买 DMIT VPS 的具体操作步骤：

### 1. 注册账号
打开 [DMIT 官网](https://bit.ly/dmit_coupon)。页面右上角支持语言选择，可以切换至中文。不过，本教程以英文界面为例。点击右上角的 **Sign Up**，进入注册页面完成账号注册。

### 2. 新建服务器实例
注册成功后，进入账户后台。点击顶部的 **Create** -> **Server**，开始新建实例。

### 3. 选择套餐
在套餐选择页面推荐选择 **PVM.LAX.sPro.CREATOR** 套餐，该套餐提供 **Cloudflare Magic Transit** 加持的 5Tbps+ DDoS 防护和三网回程 CN2 GIA。选择完毕后，点击页面底部的 **Continue** 进入下一步。

### 4. 配置服务器
在自定义配置页面，您可以根据需求调整账单周期（注意：使用优惠码后更改账单周期会恢复原价）、设置 root 密码以及选择系统镜像。如果需要更高性能，可以在页面底部升级配置。

### 5. 优惠码与结算
确认套餐配置后，输入优惠码并点击 **Validate Code** 验证，之后进入下一步。

### 6. 选择支付方式
DMIT 支持多种支付方式，包括信用卡、PayPal、Stripe、支付宝等。推荐使用支付宝或者 PayPal。选择适合您的支付方式并点击 **Checkout**，完成支付流程。

支付完成后，您购买的 VPS 即开始创建，通常需要等待 3 分钟左右便可开通，同时您会收到邮件通知。

## 如何连接 SSH

DMIT 强制使用 SSH 密钥登录，而非密码。这种方式更安全，但操作略有门槛。以下是详细步骤：

### 1. 下载 SSH 密钥
首次开通 VPS 后，系统会弹出 **SSH Key** 对话框。点击 **Download private key** 下载密钥并妥善保存。如果您关闭了对话框，可以通过后台的 **SSH Key Management** 按钮重新下载或上传密钥。

### 2. 使用 SSH 工具连接
您可以选择使用 XShell、PuTTY、MobaXterm 等工具进行连接。DMIT 官网提供了相关工具的使用教程（如 [如何通过 XShell 使用 SSH Key 连接 DMIT](https://bit.ly/dmit_coupon)）。

更熟悉命令行操作的用户，也可以使用 Terminal 或 Windows Terminal 进行连接。

### 3. 连接方法
解压您下载的密钥文件，其中的 `id_rsa.pem` 是私钥文件。以下是基于 SSH 命令的连接流程：

命令格式：
bash
ssh -i /path/to/key root@[ip address] -p [port]


示例：
假设您的密钥文件路径为 `D:\temp\ssh_rsa_keys\private_key\id_rsa.pem`，IP 地址为 `10.0.0.1`，可输入以下命令：
bash
ssh -i D:/temp/ssh_rsa_keys/private_key/id_rsa.pem root@10.0.0.1 -p 22


### 4. 修复密钥文件权限错误
如果出现 `bad permissions` 错误，需调整私钥文件权限：
1. 右键点击 `id_rsa.pem` -> 属性 -> 安全 -> 高级。
2. 修改所有者为当前用户。
3. 禁用继承，并删除所有继承权限。
4. 添加当前用户的完全控制权限。

调整好后再次执行 SSH 命令便可成功连接。

到这里，您便完成了 VPS 的购买和 SSH 连接，后续便可以开始正常使用您的服务器。