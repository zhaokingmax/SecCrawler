<h1 align="center">
SecCrawler
</h1>


![SecCrawler](https://socialify.git.ci/Le0nsec/SecCrawler/image?font=Inter&language=1&logo=https%3A%2F%2Favatars.githubusercontent.com%2Fu%2F66706544&owner=1&pattern=Floating%20Cogs&theme=Dark)

<h4 align="center">
一个方便安全研究人员获取每日安全日报的爬虫和推送程序，目前爬取范围包括先知社区、安全客、Seebug Paper、跳跳糖、奇安信攻防社区、棱角社区、洞见微信聚合，持续更新中。
</h4>

<p align="center">
  <a href="https://github.com/Le0nsec/SecCrawler/issues">
    <img src="https://img.shields.io/github/issues/Le0nsec/SecCrawler?style=flat-square">
  </a>
  <a href="https://github.com/Le0nsec/SecCrawler/network/members">
    <img src="https://img.shields.io/github/forks/Le0nsec/SecCrawler?style=flat-square">
  </a>
  <a href="https://github.com/Le0nsec/SecCrawler/stargazers">
    <img src="https://img.shields.io/github/stars/Le0nsec/SecCrawler?style=flat-square">
  </a>
  <a href="https://github.com/Le0nsec/SecCrawler/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/Le0nsec/SecCrawler?style=flat-square">
  </a>
  <a href="https://github.com/RichardLitt/standard-readme">
    <img src="https://img.shields.io/badge/readme%20style-standard-brightgreen.svg?style=flat-square">
  </a>
  <a href="https://github.com/Le0nsec/SecCrawler/releases">
    <img src="https://img.shields.io/github/v/release/Le0nsec/SecCrawler?include_prereleases&style=flat-square">
  </a>
</p>




## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Install](#install)
- [Config](#config)
- [Demo](#demo)
- [Contributing](#contributing)
- [License](#license)


## Introduction

SecCrawler 是一个跨平台的方便安全研究人员获取每日安全日报的爬虫和机器人推送程序，目前爬取范围包括先知社区、安全客、Seebug Paper、跳跳糖、奇安信攻防社区、棱角社区、洞见微信聚合，机器人推送范围包括企业微信机器人、飞书机器人、钉钉机器人、Server酱、HexQBot（QQ群机器人）、WgpSecBot（微信机器人），持续更新中。

程序使用yml格式的配置文件，第一次使用时请使用`-init`参数在当前文件夹生成默认配置文件，在配置文件中设置爬取的网站和推送机器人相关配置，目前包括在内的网站和推送的机器人在[Features](#features)中可以查看，可以设置每日推送的整点时间以及是否开启API。

```text

  _____            _____                    _           
 / ____|          / ____|                  | |          
| (___   ___  ___| |     _ __ __ ___      _| | ___ _ __ 
 \___ \ / _ \/ __| |    | '__/ _  \ \ /\ / / |/ _ \ '__|
 ____) |  __/ (__| |____| | | (_| |\ V  V /| |  __/ |   
|_____/ \___|\___|\_____|_|  \__,_| \_/\_/ |_|\___|_|   							  
SecCrawler dev

Options:
  -c file
    	the config file to be used, or generate a config file with the specified name with -init (default "config.yml")
  -help
    	print help info
  -init
    	generate a config file
  -test
    	stop after running once
  -version
    	print version info

```

- 使用`-h/-help`查看详细命令：
- 使用`-c`指定使用的配置文件，或者配合`-init`生成指定文件名的配置文件
- 使用`-test`参数执行一次程序后退出
- [API文档](https://www.apifox.cn/apidoc/shared-b613c4fc-56a6-4724-831f-4c1ac5547ab5)
- 注意请求API需要带上Authorization头

如果开启了定时任务，程序使用定时任务每天根据设置好的时间整点自动运行，编辑好相关配置后后台运行即可，示例运行命令：


```sh
$ nohup ./SecCrawler >> run.log 2>&1 &
# 或者使用screen
$ screen ./SecCrawler
$ ctrl a+d / control a+d # 回到主会话
```


注：由于在爬取先知安全社区时程序使用了 Selenium，用户需要手动下载`ChromeDriver`和`Chrome`浏览器。


ChromeDriver镜像站：http://npm.taobao.org/mirrors/chromedriver/


- Windows和Mac用户在[下载Chrome](https://www.google.cn/chrome/)并安装后，下载对应chrome版本的ChromeDriver并在配置文件`config.yml`中指定ChromeDriver的路径
- Linux用户在下载Chrome（链接如下）并安装后，同上编辑配置文件
    - [Debian/Ubuntu(64位.deb)](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)
    - [Fedora/openSUSE(64位.rpm)](https://dl.google.com/linux/direct/google-chrome-stable_current_x86_64.rpm)


> Chrome浏览器可以访问`chrome://version/`查看版本

> 命令行可以使用`google-chrome-stable --version`查看版本


程序旨在帮助安全研究者自动化获取每日更新的安全文章，适用于每日安全日报推送，爬取的安全社区网站范围和支持推送的机器人持续增加中，欢迎在[issues](https://github.com/Le0nsec/SecCrawler/issues)中提供宝贵的建议。


:rocket: 目前 SecCrawler 已在MacOS Apple silicon 、Ubuntu 20.04运行测试通过。

## Features

支持的爬取网站列表：

- [x] [先知安全社区](https://xz.aliyun.com/)
- [x] [安全客](https://www.anquanke.com/knowledge) (安全知识专区)
- [x] [Seebug Paper](https://paper.seebug.org/)
- [x] [棱角安全社区](https://forum.ywhack.com/forum-59-1.html)
- [x] [跳跳糖](https://tttang.com/)
- [x] [奇安信攻防社区](https://forum.butian.net/community/all/newest)
- [x] [洞见微信聚合](http://wechat.doonsec.com/)
  

支持的推送机器人列表：

- [x] [企业微信群机器人](https://work.weixin.qq.com/api/doc/90000/90136/91770)
- [x] [HexQBot](https://github.com/Am473ur/HexQBot) (QQ群机器人 自建)
- [x] [Server酱](https://sct.ftqq.com/)
- [x] [飞书群机器人](https://open.feishu.cn/document/ukTMukTMukTM/ucTM5YjL3ETO24yNxkjN)
- [x] [钉钉群机器人](https://open.dingtalk.com/document/robots/custom-robot-access)
- [x] [WgpSecBot](https://bot.wgpsec.org)
- [ ] [pushplus](http://pushplus.hxtrip.com/)

## Install

你可以在[Releases](https://github.com/Le0nsec/SecCrawler/releases)下载最新的SecCrawler。


或者从源码编译：


```sh
$ git clone https://github.com/Le0nsec/SecCrawler.git
$ cd SecCrawler
$ go build .
```


## Config
`config.yml`配置文件模板注释：

```yml
# 设置Selenium使用的ChromeDriver路径，支持相对路径或绝对路径（如果不爬取先知社区可以不用设置）
ChromeDriver: ./chromedriver/linux64

Proxy:
  ProxyUrl: http://127.0.0.1:7890
  CrawlerProxyEnabled: false # 开启爬虫代理
  BotProxyEnabled: false # 开启请求机器人代理

Cron:
  enabled: false
  time: 11 # 设置定时任务每天整点爬取推送时间，范围 0 ~ 23（整数）

Api:
  enabled: false
  debug: false
  host: 127.0.0.1
  port: 8080
  auth: auth_key_here # 请求api需要带上Authorization头

Crawler:
  # 棱角社区
  # https://forum.ywhack.com/forum-59-1.html
  EdgeForum:
    enabled: false
  # 先知安全技术社区
  # https://xz.aliyun.com/
  XianZhi:
    enabled: false
  # SeebugPaper（知道创宇404实验室）
  # https://paper.seebug.org/
  SeebugPaper:
    enabled: false
  # 安全客
  # https://www.anquanke.com/
  Anquanke:
    enabled: false
  # 跳跳糖
  # http://tttang.com/
  Tttang:
    enabled: false
  # 奇安信攻防社区
  # https://forum.butian.net/community/all/newest
  QiAnXin:
    enabled: false
  # 洞见微信聚合
  # http://wechat.doonsec.com/
  DongJian:
    enabled: false

Bot:
  # 企业微信群机器人
  # https://work.weixin.qq.com/api/doc/90000/90136/91770
  WecomBot:
    enabled: false
    key: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
    timeout: 2
  # 飞书群机器人
  # https://open.feishu.cn/document/ukTMukTMukTM/ucTM5YjL3ETO24yNxkjN
  FeishuBot:
    enabled: false
    key: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
    timeout: 2
  # 钉钉群机器人
  # https://open.dingtalk.com/document/robots/custom-robot-access
  DingBot:
    enabled: false
    token: xxxxxxxxxxxxxxxxxxxx
    timeout: 2
  # HexQBot
  # https://github.com/Am473ur/HexQBot
  HexQBot:
    enabled: false
    api: http://xxxxxx.com/send
    qqgroup: 0
    key: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
    timeout: 2
  # Server酱
  # https://sct.ftqq.com/
  ServerChan:
    enabled: false
    sendkey: xxxxxxxxxxxxxxxxxxxx
    timeout: 2
  # WgpSecBot
  # https://bot.wgpsec.org/
  WgpSecBot:
    enabled: false
    key: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
    timeout: 2

```

## Demo

<p align="center">
  <img src="https://user-images.githubusercontent.com/66706544/146009777-d64c1ae8-03b6-4da3-82ff-a4a47b17dcf9.png" />
  <img src="https://user-images.githubusercontent.com/66706544/154257622-6d8bb37e-e312-48b8-a4f3-96b145a32555.png" />
</p>


## Contributing


如果您有高质量的安全社区网站希望被爬取，或者想推荐被广泛使用的推送机器人，欢迎联系我微信和邮箱：`leonsec[at]h4ck.fun`或提交[issue](https://github.com/Le0nsec/SecCrawler/issues)和[PR](https://github.com/Le0nsec/SecCrawler/pulls)。


<img src="https://user-images.githubusercontent.com/66706544/155312764-6baef289-7490-43f7-a64f-48b576ab6675.jpg" width = "300" alt="" align=center />




## License


[GNU General Public License v3.0](https://github.com/Le0nsec/SecCrawler/blob/main/LICENSE)
