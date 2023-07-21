# ChatGPT Web

## 更新记录
```shell
1.配置文件切换 openai、azure
2.聊天上下文入库（服务器重启、页面刷新不影响网页聊天的上下文）
3.聊天上下文自动保持最新聊天并小于模型要求的token（一直聊一直爽）
4.网络异常时上下文保持（429也不怕，网络超时也不怕）
5.支持上下文存储到redis
```

## 介绍

支持Azure \ Openai API

配置：
```shell
1. 进入 `service/.env.example` 文件，复制内容到 `service/.env` 文件
# OpenAI API Key
# Azure OpenAI API Key
OPENAI_API_KEY=

# OpenAI API Base URL - https://api.openai.com/v1
# Azure OpenAI API Base URL - https://{deployment_name}.openai.azure.com/openai/deployments/{model}
OPENAI_API_BASE_URL=

更多配置请查看 service/.env.example
```

## 前置要求

### Node

`node` 需要 `^16 || ^18 || ^19`

```shell
node -v
```

### PNPM
如果你没有安装过 `pnpm`
```shell
npm install pnpm -g
```

### 后端

进入文件夹 `/service` 运行以下命令

```shell
pnpm install
```

### 前端
根目录下运行以下命令
```shell
pnpm bootstrap
```

## 测试环境运行
### 后端服务

进入文件夹 `/service` 运行以下命令

```shell
pnpm start
```

### 前端网页
根目录下运行以下命令
```shell
pnpm dev
```



## 打包

### 使用 Docker

#### Docker 参数示例

#### Docker build & Run

```bash
docker build -t chatgpt-web .

# 前台运行
docker run --name chatgpt-web --rm -it -p 127.0.0.1:3002:3002 --env OPENAI_API_KEY=your_api_key chatgpt-web

# 后台运行
docker run --name chatgpt-web -d -p 127.0.0.1:3002:3002 --env OPENAI_API_KEY=your_api_key chatgpt-web

# 运行地址
http://localhost:3002/
```


### 手动打包
#### 后端服务
> 如果你不需要本项目的 `node` 接口，可以省略如下操作

复制 `service` 文件夹到你有 `node` 服务环境的服务器上。

```shell
# 安装
pnpm install

# 打包
pnpm build

# 运行
pnpm prod
```

PS: 不进行打包，直接在服务器上运行 `pnpm start` 也可

#### 前端网页

1、修改根目录下 `.env` 文件中的 `VITE_GLOB_API_URL` 为你的实际后端接口地址

2、根目录下运行以下命令，然后将 `dist` 文件夹内的文件复制到你网站服务的根目录下



```shell
pnpm build
```

