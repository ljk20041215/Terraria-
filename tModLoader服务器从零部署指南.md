---
title: tModLoader服务器从零部署指南
date: 2025-12-11 20:29:17
tags: [Terraria, 服务器搭建, tModLoader, 游戏服务器, 教程]
categories: 游戏服务器搭建
---

## 一、准备工作

在开始之前，请确保你已经：
- 拥有一台**云服务器**（如阿里云、腾讯云、AWS等，推荐至少2核4GB配置）ps:博主使用的版本是Ubuntu 22.04 LTS
- 已经**登录到服务器**并拥有sudo权限
- 本地电脑已安装**SSH客户端**（如Terminal、PuTTY等）

## 二、系统基础配置

### 1. 更新系统包

- sudo apt update && sudo apt upgrade -y

## 三、创建专用目录

- mkdir -p ～/terraria_server
- cd ～/terraria_server

## 四、下载并安装tModLoader

### 1.下载
该命令只是例子，具体下载版本请根据本地电脑上的tModLoader版本确定。
- wget https://github.com/tModLoader/tModLoader/releases/download/v2025.04.3.0/tModLoader.zip

### 2.安装
- unzip tModLoader.zip

### 3.设置执行权限
- chmod +x start-tModLoaderServer.sh

## 五、首次启动（第一次运行会下载.NET环境）
- ./start-tModLoaderServer.sh -nosteam
重要提示：首次启动时会有一段时间看起来"卡住"，这是正在下载.NET环境，请耐心等待，不要中断进程。

## 六、mod的添加

### 1.找到Mods文件夹
- sudo find / -type d -name "Mods" 2>/dev/null | grep -i terraria

### 2.将本地下载好的mod上传到云服务器
- scp "本地路径/*.tmod" 用户名@服务器IP:Mods目录路径/

## 注意事项
云服务器特别提示：除了服务器本地防火墙，还需要在云服务商控制台的安全组规则中开放相应的端口
