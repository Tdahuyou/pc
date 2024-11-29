# [0004. chrome 上的 Scripty 插件介绍](https://github.com/Tdahuyou/pc/tree/main/0004.%20chrome%20%E4%B8%8A%E7%9A%84%20Scripty%20%E6%8F%92%E4%BB%B6%E4%BB%8B%E7%BB%8D)

<!-- region:toc -->
- [1. 🔗 Scripty 在线配置](#1--scripty-在线配置)
- [2. 📒 使用说明](#2--使用说明)
- [3. 🔍 插件作者 abhisheksatre](#3--插件作者-abhisheksatre)
- [4. 🔗 常见的替代工具 Tampermonkey - 油猴插件](#4--常见的替代工具-tampermonkey---油猴插件)
- [5. 📒 Scripty vs. Tampermonkey](#5--scripty-vs-tampermonkey)
<!-- endregion:toc -->

## 1. 🔗 Scripty 在线配置

- https://scripty.abhisheksatre.com/#/
  - 所有脚本都可以配置在这里边。
  - ![](md-imgs/2024-11-29-23-31-01.png)

## 2. 📒 使用说明

- **使用的前提**：要求懂一些 JavaScript，能够根据自己的需求编写网站脚本。
- **开/关**：需要用的时候将开关打开，不需要用的时候直接关闭掉即可。
- **如何使用**：以 0003 为例，简单说明一下 Scripty 的基本使用。
  - 下面这张图来源于 0003
    - ![](md-imgs/2024-11-29-23-07-30.png)
  - Name：脚本名称，可以随意填写。
  - Javascript Code：脚本内容，这里填写脚本代码。
  - Run script if：这部分填写的是脚本的运行条件，比如图中的配置就是网址中包含 `https://github.com/Tdahuyou` 这个字符串的都满足条件。
  - Trigger：配置触发脚本的时机，比如图片中配置的就是在页面完成加载之前，自动执行脚本。

## 3. 🔍 插件作者 abhisheksatre

- https://www.abhisheksatre.com/
  - 作者的 blog
- https://github.com/abhisheksatre
  - 作者的 github

## 4. 🔗 常见的替代工具 Tampermonkey - 油猴插件

- [Tampermonkey](https://tampermonkey.net/)

## 5. 📒 Scripty vs. Tampermonkey

- 两个工具都有在使用，都挺不错的。
- Tampermonkey 的功能应该是比 Scripty 强大不少的，受众应该也比 Scripty 多。
- 截止目前（2024 年 11 月 29 日 23:43:46）个人更倾向于使用 Scripty，感觉它的页面更加干净，配置起来更方便，功能也基本够用了。