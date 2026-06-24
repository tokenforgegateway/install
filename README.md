# TokenForge Install

TokenForge Gateway 的公开安装入口。

## 安装

**Mac / Linux**

```sh
curl -fsSL https://raw.githubusercontent.com/tokenforgegateway/tokenforge-install/main/install.sh | sh
```

**Windows (PowerShell)**

```powershell
irm https://raw.githubusercontent.com/tokenforgegateway/tokenforge-install/main/install.ps1 | iex
```

脚本会检测架构、拉取 `ghcr.io/tokenforgegateway/tokenforge-gateway`、生成密钥、用 docker compose 起 Postgres + Redis + Gateway，并等待健康检查。

## 选项（环境变量）

| 变量 | 默认 | 说明 |
|--|--|--|
| `TF_VERSION` | `latest` | 镜像版本，如 `1.2.1` |
| `TF_DIR` | `~/tokenforge-gateway` | 安装目录 |
| `TF_PORT` | `3080` | 监听端口 |

```sh
TF_VERSION=1.2.1 curl -fsSL https://raw.githubusercontent.com/tokenforgegateway/tokenforge-install/main/install.sh | sh
```

## 升级

重新运行安装命令并指定新版本号即可；`.env`（含密钥）会被复用，数据不丢。

## 前置要求

- Docker Desktop / Docker Engine
- Docker Compose v2（`docker compose`）

本仓只包含 TokenForge Gateway 的公开安装脚本。TokenForge Server 不在本仓发布。

安装脚本由 `tokenforge` 主仓的 Gateway release workflow 自动同步；启用同步前需要在主仓配置 `INSTALL_REPO_TOKEN`。请勿在本仓手工维护脚本逻辑。
