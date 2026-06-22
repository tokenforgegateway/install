# TokenForge Gateway 一键安装

公开托管 TokenForge Gateway 的安装脚本。镜像从 GHCR 公开拉取，脚本本身不依赖任何私有资源。

## 安装

**Mac / Linux**

```sh
curl -fsSL https://raw.githubusercontent.com/tokenforgegateway/install/main/install.sh | sh
```

**Windows (PowerShell)**

```powershell
irm https://raw.githubusercontent.com/tokenforgegateway/install/main/install.ps1 | iex
```

脚本会检测架构、拉取 `ghcr.io/tokenforgegateway/tokenforge-gateway`、生成密钥、用 docker compose 起 Postgres + Redis + Gateway，并等待健康检查。

## 选项（环境变量）

| 变量 | 默认 | 说明 |
|--|--|--|
| `TF_VERSION` | `latest` | 镜像版本，如 `1.2.1` |
| `TF_DIR` | `~/tokenforge-gateway` | 安装目录 |
| `TF_PORT` | `3080` | 监听端口 |

```sh
TF_VERSION=1.2.1 curl -fsSL https://raw.githubusercontent.com/tokenforgegateway/install/main/install.sh | sh
```

## 升级

重新运行安装命令并指定新版本号即可；`.env`（含密钥）会被复用，数据不丢。

## 前置要求

- Docker Desktop / Docker Engine
- Docker Compose v2（`docker compose`）
