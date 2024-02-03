## 微软azure文本转语音 音频下载

> [!CAUTION]
> 这个用的接口被微软干掉了。。。请看（原本是本项目配套文章的）<https://blog.yfi.moe/post/azure-tts-trial/>这篇文章开头来寻找可能的替代方案。

*Demo* : <https://ttsdemo.yfi.moe/>

教程：<https://blog.yfi.moe/post/azure-tts-trial/>

Cf Workers: <https://github.com/yy4382/azure-tts/blob/main/cf_worker.js>

docker image 请用 yunfinibol/azure-tts:main

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fyy4382%2Fazure-tts&project-name=azure-tts)

> 以下为原项目的README.md

---

> *本文由GitHub Copilot 生成*

### 1. 介绍

本项目是基于微软azure的文本转语音服务，通过调用微软azure的api接口，将文本转换为语音，然后下载到本地。

### 2. 安装说明

#### 利用Cloudflare Workers部署

1. 新建一个 Cloudflare Worker

2. 将 [cf_worker.js](https://github.com/x-dr/tts/blob/main/cf_worker.js) 中的代码复制到 Cloudflare Worker 中并部署即可

<img src="https://img1.131213.xyz/file/23f45cf2a989a13842839.png" width="600px">

> 修改前端
 
`https://raw.githubusercontent.com/x-dr/cf_pages/main/tts.html` 是前端代码 ，想修改的自己修改cf_worker.js中的下面行就行

```javascript
    const html = await fetch("https://raw.githubusercontent.com/x-dr/cf_pages/main/tts.html")
```

***

#### 利用docker部署

1. 下载docker镜像

```bash
docker pull gindex/tts-azure:latest
```

2. 运行容器

```bash
docker run -itd \
           --name tts \
            -p 3035:3035 \
           --restart=always \
           gindex/tts-azure:latest
```

3. 访问地址

```bash
http://ip:3035/
```


***

#### 利用Vercel部署


[![Deploy with Vercel](https://vercel.com/button?utm_source=busiyi&utm_campaign=oss)](https://vercel.com/new/clone?utm_source=busiyi&utm_campaign=oss&repository-url=https://github.com/x-dr/tts)

#### 利用Linux服务器部署

1. 安装nodejs (如果已经安装过nodejs则跳过此步骤)

```bash
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs
```

2. 安装git (如果已经安装过git则跳过此步骤)

```bash
sudo apt-get install git
```

3. 下载项目

```bash
git clone https://github.com/x-dr/tts.git
```

4. 安装依赖

```bash
cd tts
npm install
```

5. 运行项目

```bash
node index.js
```

6. 访问地址

```bash
http://ip:3035/
```

### 3. 使用说明


### Star History

[![Star History Chart](https://api.star-history.com/svg?repos=x-dr/tts&type=Date)](https://star-history.com/#x-dr/tts&Date)

