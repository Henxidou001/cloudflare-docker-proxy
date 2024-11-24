# cloudflare-docker-proxy

![deploy](https://github.com/ciiiii/cloudflare-docker-proxy/actions/workflows/deploy.yaml/badge.svg)

[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/ciiiii/cloudflare-docker-proxy)

> 如果你正在寻找Helm的代理，也许你可以尝试 [cloudflare-helm-proxy](https://github.com/ciiiii/cloudflare-helm-proxy).

## 部署

1.单击“Deploy With Workers”按钮
2.按照说明进行分叉和部署
3.根据需要更新路线

[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/ciiiii/cloudflare-docker-proxy)

## 路线配置教程

1. 使用cloudflare worker host：仅支持代理1个注册表
   ```javascript
   const routes = {
     "${workername}.${username}.workers.dev/": "https://registry-1.docker.io",
   };
   ```
2. 使用自定义域：支持按主机路由代理多个注册表
   - 在cloudflare上托管您的域名DNS
   - 将xxx.example.com的“A”记录添加到“192.0.2.1”中
   - 将此项目部署到cloudflare workers
   - 将“xxx.example.com/*”添加到workers的HTTP路由中
   - 添加更多记录并根据需要修改配置
   ```javascript
   const routes = {
     "docker.henxidou.com": "https://registry-1.docker.io",
     "quay.henxidou.com": "https://quay.io",
     "gcr.henxidou.com": "https://k8s.gcr.io",
     "k8s-gcr.henxidou.com": "https://k8s.gcr.io",
     "ghcr.henxidou.com": "https://ghcr.io",
   };
   ```

