# personal-config

个人代理节点订阅托管仓库，包含 VLESS-Reality 节点的 Clash Meta/Mihomo 配置文件和纯文本订阅文件。

---

## 文件说明

| 文件 | 说明 |
|------|------|
| `clash.yaml` | 适用于 Clash Meta / Mihomo / OpenClash 的 YAML 配置文件 |
| `sub.txt` | 适用于通用客户端的 Base64 编码纯文本订阅文件 |

---

## 节点参数说明

在使用前，请将配置文件中的占位符替换为实际节点参数：

| 占位符 | 说明 |
|--------|------|
| `YOUR_SERVER_IP` | 服务器 IP 地址或域名 |
| `YOUR_UUID` | 节点 UUID |
| `YOUR_SNI` | Reality SNI（如 `www.microsoft.com`） |
| `YOUR_PUBLIC_KEY` | Reality 公钥 |
| `YOUR_SHORT_ID` | Reality Short ID |

---

## 订阅链接

将本仓库设为 **Public（公开）** 后，可通过以下地址直接访问原始文件：

### GitHub Raw 地址

```
# Clash Meta / Mihomo 配置
https://raw.githubusercontent.com/xiaomeng365/personal-config/main/clash.yaml

# 纯文本订阅
https://raw.githubusercontent.com/xiaomeng365/personal-config/main/sub.txt
```

### jsDelivr CDN 地址（国内可用）

```
# Clash Meta / Mihomo 配置
https://cdn.jsdelivr.net/gh/xiaomeng365/personal-config@main/clash.yaml

# 纯文本订阅
https://cdn.jsdelivr.net/gh/xiaomeng365/personal-config@main/sub.txt
```

> **注意**：jsDelivr 存在约 12 小时的 CDN 缓存，更新配置后需等待缓存刷新。

---

## 使用说明

### 1. 在 Clash Meta / Mihomo / OpenClash 中导入订阅

1. 打开客户端，进入 **配置** 或 **订阅** 页面。
2. 选择 **从 URL 导入** 或 **添加订阅**。
3. 粘贴 `clash.yaml` 的 Raw 地址，保存并更新。
4. 选择该配置文件后，即可使用代理节点。

### 2. 在支持通用订阅的客户端中导入

1. 打开客户端，进入 **订阅** 或 **服务器** 页面。
2. 选择 **从 URL 导入订阅**。
3. 粘贴 `sub.txt` 的 Raw 地址，确认导入。

### 3. 更新节点配置

1. 编辑本仓库中的 `clash.yaml` 或 `sub.txt`，修改相应参数。
2. 提交（Commit）并推送（Push）到 GitHub。
3. 在客户端中点击 **更新订阅** 即可获取最新配置。

### 4. 更换节点参数后同步更新订阅

1. 获取新节点的完整参数（IP、端口、UUID、Reality 参数等）。
2. 同步修改 `clash.yaml` 中 `proxies` 下的节点字段。
3. 重新生成 Base64 编码的 VLESS 链接，更新 `sub.txt`：
   ```bash
   # 生成 sub.txt 内容
   echo -n 'vless://NEW_UUID@NEW_SERVER:443?encryption=none&flow=xtls-rprx-vision&security=reality&sni=NEW_SNI&fp=chrome&pbk=NEW_PUBLIC_KEY&sid=NEW_SHORT_ID&type=tcp#MyNode' | base64
   ```
4. 提交修改，客户端更新订阅后即生效。

---

## 注意事项

- 本仓库须设置为 **Public（公开）** 才能通过 Raw URL 正常访问。
- 订阅文件中包含节点敏感信息，请勿随意公开传播订阅链接。
- 若订阅链接泄露，应立即更换 UUID、端口或重建节点，并更新此仓库。
- 使用 jsDelivr 时，更新后需等待数分钟至数小时缓存刷新。
- 仅个人使用时，推荐直接使用 GitHub Raw 地址，无需额外部署 Web 服务。
