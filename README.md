# cloudflare-docker-proxy

![deploy](https://github.com/ciiiii/cloudflare-docker-proxy/actions/workflows/deploy.yaml/badge.svg)

[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/ciiiii/cloudflare-docker-proxy)

> If you're looking for proxy for helm, maybe you can try [cloudflare-helm-proxy](https://github.com/ciiiii/cloudflare-helm-proxy).

## Deploy

1.单击“Deploy With Workers”按钮
2.按照说明进行分叉和部署
3.根据需要更新路线

[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/ciiiii/cloudflare-docker-proxy)

## Routes configuration tutorial

1. 使用cloudflare worker host：仅支持代理1个注册表
   ```javascript
   const routes = {
     "${workername}.${username}.workers.dev/": "https://registry-1.docker.io",
   };
   ```
2. 使用自定义域：支持按主机路由代理多个注册表
   - host your domain DNS on cloudflare
   - add `A` record of xxx.example.com to `192.0.2.1`
   - deploy this project to cloudflare workers
   - add `xxx.example.com/*` to HTTP routes of workers
   - add more records and modify the config as you need
   ```javascript
   const routes = {
     "docker.henxidou.com": "https://registry-1.docker.io",
     "quay.henxidou.com": "https://quay.io",
     "gcr.henxidou.com": "https://k8s.gcr.io",
     "k8s-gcr.henxidou.com": "https://k8s.gcr.io",
     "ghcr.henxidou.com": "https://ghcr.io",
   };
   ```

