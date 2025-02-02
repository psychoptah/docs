---
prev:
  text: Installation
  link: /en-US/manual/starter/
next:
  text: About Koishi Console
  link: /en-US/manual/console/
---

# Install for Container

::: warning
Docker 等容器化软件是以服务生产环境而开发的应用平台，在使用此类软件部署之时，我们相信你已经掌握了运维一台服务器所必须的知识，同时也理解了容器化的概念与相关软件的基础操作。如若不然，在除路由器或 NAS 等特殊环境外，请 [选择其他安装方式](./index.md)。
:::

Koishi 提供了 [Docker](https://hub.docker.com/r/koishijs/koishi) 镜像，方便你在容器中运行 Koishi。你需要首先安装 [Podman](https://podman.io) 或 [Docker](https://www.docker.com) 来运行容器。

## Start container

Start container with the following command:

::: tabs code
```podman
podman run -p 5140:5140 koishijs/koishi
```
```docker
docker run -p 5140:5140 koishijs/koishi
```
:::

Many plugins depend on [koishi-plugin-pupeteer](https://www.npmjs.com/package/koishi-plugin-puppeteer) to render images, so the default image includes Chromium. If you don't need Chromium to be included, we also offer a lite version:

::: tabs code
```podman
podman run -p 5140:5140 koishijs/koishi:latest-lite
```
```docker
docker run -p 5140:5140 koishijs/koishi:latest-lite
```
:::

On startup, the Koishi console will be bound to the 5140 port.

如果你需要持久化，请使用 `-v /some/place:/koishi` 来映射 Koishi 的文件。

If you want to switch the time zone, use `-e TZ=Asia/Shanghai`.

::: tip
Koishi 本体及其插件都可以控制台完成更新。在持久化文件过后更新容器仅会更新 Chromium 和 Node.js 等的版本。
:::

## Install Plugins

在容器正常运行时，可以通过在浏览器中访问 `http://宿主机地址:5140` 在控制台中安装和启用插件。若无法访问请检查你的防火墙配置是否正确。
