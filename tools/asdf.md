# 运行环境版本管理工具-asdf

## 介绍

在日常开发工作中我们经常会遇到这样的需求，我希望系统中各种编程语言的不同版本共存，比如我一个项目基于`python2`，另一个项目又基于`python3`，这时候你又两个选择，一是官网下载2和3的安装包，二是用[pyenv](https://github.com/pyenv/pyenv)管理不同版本的`python`。如果又要同时安装`php7`和`php8`呢？我之前遇到这种情况时，去网上搜了`php`的版本管理工具，没有很好的选择，后来选择走`homebrew`，同时安装了`php@7.4`和`php`。

我用`pyenv`管理不同的`python`版本，用`jabba`管理不同的`java`版本，用`nvm`管理不同的`nodejs`版本...直到用上了[asdf](https://asdf-vm.com/)，一个可以同时满足我所有需求的工具。

`asdf`使用单个命令行工具管理你的每个项目运行环境。阅读官方的[Getting Started](https://asdf-vm.com/guide/getting-started.html)可以帮助你快速上手。

## 一些小问题及解决方案

### `corepack enable`之后`yarn`和`pnpm`不生效

```shell
asdf reshim nodejs
```

### 全局安装`@nestjs/cli`之后`nest`不生效

```shell
asdf reshim nodejs
```

### 全局安装`jupyterlab`之后`jupyter lab`不生效

```shell
asdf reshim python
```

### `homebrew`更新`asdf`版本后`node`运行报错

```shell
vim `which node`
```
修改`asdf`路径为`/opt/homebrew/opt/asdf/libexec/bin/asdf`

```shell
#!/usr/bin/env bash
# asdf-plugin: nodejs 18.3.0
# asdf-plugin: nodejs 16.15.1
# asdf-plugin: nodejs lts
exec /opt/homebrew/opt/asdf/libexec/bin/asdf exec "node" "$@" # asdf_allow: ' asdf '
```
`npm`或其他报错同理。

