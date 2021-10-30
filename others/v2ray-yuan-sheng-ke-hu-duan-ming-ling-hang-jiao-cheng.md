# V2Ray 原生客户端命令行教程

## 安装

### macOS

首先安装 macOS 下的 [Homebrew](https://brew.sh) 包管理工具。之后参见[官方 homebrew 项目](https://github.com/v2ray/homebrew-v2ray)运行下列命令完成安装。

```bash
brew tap v2ray/v2ray
brew install v2ray-core
```

### Linux

参考 V2Ray [官方文档](https://github.com/v2fly/fhs-install-v2ray)，运行下列命令完成安装。

```bash
bash <(curl -L https://raw.githubusercontent.com/v2fly/fhs-install-v2ray/master/install-release.sh)
```

## 配置

新建文件 config.json，复制已下文本并粘贴。修改其中的_**`节点地址`**_和 _**`V2Ray UUID`**_。为自己需要使用的节点地址和服务唯一 UUID（在 AgentNEO 服务详情「服务设置」一栏中可以看到）。

```javascript
{
  "inbounds": [
    {
      "port": 1080,
      "protocol": "socks",
      "sniffing": {
        "enabled": true,
        "destOverride": ["http", "tls"]
      },
      "settings": {
        "auth": "noauth"
      }
    }
  ],
  "outbounds": [
    {
      "protocol": "vmess",
      "settings": {
        "vnext": [
          {
            "address": "**节点地址**",
            "port": 443,
            "users": [
              {
                "id": "**V2Ray UUID**",
                "alterId": 1
              }
            ]
          }
        ]
      },
      "streamSettings": {
        "network": "ws",
        "security": "tls",
        "wsSettings": {
          "path": "/v2"
        }
      }
    }
  ]
}
```

## 运行

确认上述 _**`config.json`**_ 文件路径，例如 _**`/home/root/config.json`**_。运行命令 _**`v2ray -config /home/root/config.json`**_ 即可启动 V2Ray 客户端。

客户端启动后即可看到本地的 socks 代理端口为指定的 _**`1080`**_，自行配置系统（或软件的代理）指向本地端口（_**`127.0.0.1:1080`**_）即可。
