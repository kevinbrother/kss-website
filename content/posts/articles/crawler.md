---
title: 爬虫功能
date: 2025-08-15 
---

## 概念

Scraper 和 Crawler 的区别

- Scraper: 从特定页面中提取结构化数据的工具 / 行为。如：针对已获取的页面源码（HTML/JSON 等），通过规则（如 XPath、CSS 选择器）提取目标信息（如商品价格、文章标题）。
- Crawler: 遍历网页的行为。如：从一个起始 URL 出发，自动跟随页面中的链接（如 <a> 标签），逐层探索整个网站或互联网的页面，像 “蜘蛛织网” 一样覆盖大量资源。

## 技术栈

### 技术点，适合探索基础功能，不适合生产的工程级别

- selenium
- puppeteer
- cheerio
- request
- playwright

### 框架

- crawlee (ts/js、 python)
- scrapy (python)

## 由于我做的前端所以选了 crawlee

优势： 功能强大，支持分布式，支持代理池，支持浏览器模拟等
缺点：目前过滤缓存与队列只支持 filesystem 和官方的 apify 云存储方案，社区暂时没有 redis 等中间价的方案支持，需要自己实现

## 目前还没看书
