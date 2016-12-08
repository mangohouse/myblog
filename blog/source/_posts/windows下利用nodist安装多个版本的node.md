title: windows下利用nodist安装多个版本的node
date: 2016-12-01 18:15:30
tags: node,nodist
description: windows下利用nodist安装多个版本的node
---
好久，没有更新博客了，今天因为项目需要，需要在windows下使用多个版本的node，刚开始是想用nvmw的，nvmw虽然挺好用配置也简单，只需  <code>npm install -g nvmw</code> 
但是nvmv只能安装4.0以下的版本，后来找到了nodist，先下载 https://github.com/marcelklehr/nodist/releases/download/v0.8.7/NodistSetup-v0.8.7.exe
安装完成后，找到并用编辑器打开cli.js，然后将distUrl、iojsDistUrl更换成淘宝镜像，（npm安装速度会有质的提升）如下： 
var distUrl = 'https://npm.taobao.org/mirrors/node';
var iojsDistUrl = 'https://npm.taobao.org/mirrors/iojs'; 
然后打开命令行窗口，输入命令： npm config set registry https://registry.npm.taobao.org 
然后nodist 加node的版本号就可以随意安装跟切换了，比如nodist 4.5.5,如未安装该版本会先安装，如已安装直接切换到当前版本

	