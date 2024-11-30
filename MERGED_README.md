# [README.md](./0001.%20使用%20LICEcap%20在%20macos%20和%20windows%20系统上录制%20gif%20图/README.md)<!-- !======> SEPERATOR <====== -->
# [0001. 使用 LICEcap 在 macos 和 windows 系统上录制 gif 图](https://github.com/Tdahuyou/pc/tree/main/0001.%20%E4%BD%BF%E7%94%A8%20LICEcap%20%E5%9C%A8%20macos%20%E5%92%8C%20windows%20%E7%B3%BB%E7%BB%9F%E4%B8%8A%E5%BD%95%E5%88%B6%20gif%20%E5%9B%BE)

<!-- region:toc -->
- [1. 📒 LICEcap 简介](#1--licecap-简介)
- [2. 📒 LICEcap 的安装和使用步骤](#2--licecap-的安装和使用步骤)
  - [2.1. 安装](#21-安装)
  - [2.2. 使用步骤](#22-使用步骤)
- [3. 💻 使用 LICEcap 截 gif 图的效果展示](#3--使用-licecap-截-gif-图的效果展示)
<!-- endregion:toc -->


## 1. 📒 LICEcap 简介

- LICEcap 是一个非常流行且易于使用的免费工具，可以录制屏幕并保存为 GIF 格式。
- 特点：
  - 免费
  - macos、windows 均支持
  - 可配置录制参数
- LICEcap 实测可用，使用步骤也比较简单，可以在官方文档中点击 view a demo 来快速了解这玩意儿应该如何使用。
  - ![](md-imgs/2024-10-14-10-29-36.png)

## 2. 📒 LICEcap 的安装和使用步骤

### 2.1. 安装

- 访问 [LICEcap 官方网站](https://www.cockos.com/licecap/) 下载 LICEcap。
  - ![](md-imgs/2024-11-30-12-00-23.png)

### 2.2. 使用步骤

![](md-imgs/2024-11-30-12-07-42.png)

1. 打开 LICEcap。
2. 先选择你准备将录制好的 gif 图存放在什么位置，文件名叫什么。
3. 根据实际需要配置录制参数。
   1. 简单点直接使用默认的即可，不需要修改参数配置的值。
4. 将录制的框挪动到你需要录制的位置，点击开始录制，在录制完毕后点击 stop 结束即可。

## 3. 💻 使用 LICEcap 截 gif 图的效果展示

- 下面这是在不同操作系统 macos 和 Windows 中，使用 LICEcap 简单录制的 gif 图。
- Windows 环境：
  - ![](md-imgs/windows-test.gif)
- macOS 环境：
  - ![](md-imgs/macos-test.gif)





# [README.md](./0002.%20Windows%20锁屏快捷键/README.md)<!-- !======> SEPERATOR <====== -->
# [0002. Windows 锁屏快捷键](https://github.com/Tdahuyou/pc/tree/main/0002.%20Windows%20%E9%94%81%E5%B1%8F%E5%BF%AB%E6%8D%B7%E9%94%AE)

<!-- region:toc -->
- [1. 📒 `win L`](#1--win-l)
<!-- endregion:toc -->


## 1. 📒 `win L`

- **win + L**
  - 这是锁定屏幕的最快方式。
  - 按下这个组合键后，你的电脑会立即转到锁屏界面。
  - 如果有设置开机密码，则要求输入密码或其他验证信息才能重新进入系统。



# [README.md](./0003.%20在%20GitHub%20上预览自己的笔记时处理一些默认样式/README.md)<!-- !======> SEPERATOR <====== -->
# [0003. 在 GitHub 上预览自己的笔记时处理一些默认样式](https://github.com/Tdahuyou/pc/tree/main/0003.%20%E5%9C%A8%20GitHub%20%E4%B8%8A%E9%A2%84%E8%A7%88%E8%87%AA%E5%B7%B1%E7%9A%84%E7%AC%94%E8%AE%B0%E6%97%B6%E5%A4%84%E7%90%86%E4%B8%80%E4%BA%9B%E9%BB%98%E8%AE%A4%E6%A0%B7%E5%BC%8F)

<!-- region:toc -->
- [1. 📒 脚本功能简介](#1--脚本功能简介)
- [2. 💻 实现脚本](#2--实现脚本)
<!-- endregion:toc -->

## 1. 📒 脚本功能简介

- 图片尺寸设置为原分辨率的一半大小。
  - 使用的显示器的分辨率是 4k，截出来的图片在 github 上展示的时候，尺寸是实际截屏尺寸的两倍。为了在预览图片的时候，能够和截图时的尺寸一致，因此做了缩小处理。
- 超链接去掉下划线。
  - 感觉去掉下划线更美观。

## 2. 💻 实现脚本

```js
var style = document.createElement('style');

style.innerHTML = `
  .js-snippet-clipboard-copy-unpositioned img {
    /* width: 50% !important; */
  }
  .js-snippet-clipboard-copy-unpositioned a {
    text-decoration: none !important;
  }
`;

var head = document.head || document.getElementsByTagName('head')[0];

head.appendChild(style);

// 选择具有特定类名的所有div元素
const divs = document.querySelectorAll('.js-snippet-clipboard-copy-unpositioned');

divs.forEach(div => {
    // 在每个div中查找所有的img标签
    const images = div.querySelectorAll('img');
    
    images.forEach(img => {
        // 确保图片已经加载完成
        if (img.complete) {
            resizeImage(img);
        } else {
            img.onload = function() {
                resizeImage(img);
            };
        }
    });
});

function resizeImage(image) {
    // 获取原始宽度和高度
    const originalWidth = image.naturalWidth;
    const originalHeight = image.naturalHeight;

    // 设置新的宽度为原始宽度的50%
    const newWidth = originalWidth * 0.5;
    // 保持宽高比的情况下设置新高度
    const newHeight = originalHeight * 0.5;

    // 应用新的尺寸
    image.style.width = newWidth + 'px';
    image.style.height = newHeight + 'px';
}
```

- 可以将脚本丢到 Scripty 插件中，简单配置一下自动加载规则，即可在访问 https://github.com/Tdahuyou/ 自己的 github 仓库数据时自动运行。
  - ![](md-imgs/2024-11-29-23-07-30.png)



# [README.md](./0004.%20chrome%20上的%20Scripty%20插件介绍/README.md)<!-- !======> SEPERATOR <====== -->
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



# [README.md](./0005.%20Snipaste%20截图工具/README.md)<!-- !======> SEPERATOR <====== -->
# [0005. Snipaste 截图工具](https://github.com/Tdahuyou/pc/tree/main/0005.%20Snipaste%20%E6%88%AA%E5%9B%BE%E5%B7%A5%E5%85%B7)

<!-- region:toc -->
- [1. ⏰ 搬运 yuque 上的早期文章](#1--搬运-yuque-上的早期文章)
<!-- endregion:toc -->

## 1. ⏰ 搬运 yuque 上的早期文章




# [README.md](./0006.%20Wgesture%20鼠标手势工具/README.md)<!-- !======> SEPERATOR <====== -->
# [0006. Wgesture 鼠标手势工具](https://github.com/Tdahuyou/pc/tree/main/0006.%20Wgesture%20%E9%BC%A0%E6%A0%87%E6%89%8B%E5%8A%BF%E5%B7%A5%E5%85%B7)

<!-- region:toc -->
- [1. ⏰ 搬运 yuque 上的早期文章](#1--搬运-yuque-上的早期文章)
<!-- endregion:toc -->

## 1. ⏰ 搬运 yuque 上的早期文章



# [README.md](./0007.%20WeRead%20微信读书辅助工具/README.md)<!-- !======> SEPERATOR <====== -->
# [0007. WeRead 微信读书辅助工具](https://github.com/Tdahuyou/pc/tree/main/0007.%20WeRead%20%E5%BE%AE%E4%BF%A1%E8%AF%BB%E4%B9%A6%E8%BE%85%E5%8A%A9%E5%B7%A5%E5%85%B7)

<!-- region:toc -->
- [1. ⏰ 搬运 yuque 上的早期文章](#1--搬运-yuque-上的早期文章)
<!-- endregion:toc -->

## 1. ⏰ 搬运 yuque 上的早期文章



# [README.md](./0008.%20TypingClub%20打字练习工具/README.md)<!-- !======> SEPERATOR <====== -->
# [0008. TypingClub 打字练习工具](https://github.com/Tdahuyou/pc/tree/main/0008.%20TypingClub%20%E6%89%93%E5%AD%97%E7%BB%83%E4%B9%A0%E5%B7%A5%E5%85%B7)

<!-- region:toc -->
- [1. ⏰ 搬运 yuque 上的早期文章](#1--搬运-yuque-上的早期文章)
<!-- endregion:toc -->

## 1. ⏰ 搬运 yuque 上的早期文章



# [README.md](./0009.%20Qwerty%20Learner%20打字练习%20+%20学习外语工具/README.md)<!-- !======> SEPERATOR <====== -->
# [0009. Qwerty Learner 打字练习 + 学习外语工具](https://github.com/Tdahuyou/pc/tree/main/0009.%20Qwerty%20Learner%20%E6%89%93%E5%AD%97%E7%BB%83%E4%B9%A0%20%2B%20%E5%AD%A6%E4%B9%A0%E5%A4%96%E8%AF%AD%E5%B7%A5%E5%85%B7)

<!-- region:toc -->
- [1. ⏰ 搬运 yuque 上的早期文章](#1--搬运-yuque-上的早期文章)
<!-- endregion:toc -->

## 1. ⏰ 搬运 yuque 上的早期文章



# [README.md](./0010.%20SimpRead%20文章收集工具/README.md)<!-- !======> SEPERATOR <====== -->
# [0010. SimpRead 文章收集工具](https://github.com/Tdahuyou/pc/tree/main/0010.%20SimpRead%20%E6%96%87%E7%AB%A0%E6%94%B6%E9%9B%86%E5%B7%A5%E5%85%B7)

<!-- region:toc -->
- [1. ⏰ 搬运 yuque 上的早期文章](#1--搬运-yuque-上的早期文章)
<!-- endregion:toc -->

## 1. ⏰ 搬运 yuque 上的早期文章



# [README.md](./0011.%20TTSmaker%20文本转语音在线工具/README.md)<!-- !======> SEPERATOR <====== -->
# [0011. TTSmaker 文本转语音在线工具](https://github.com/Tdahuyou/pc/tree/main/0011.%20TTSmaker%20%E6%96%87%E6%9C%AC%E8%BD%AC%E8%AF%AD%E9%9F%B3%E5%9C%A8%E7%BA%BF%E5%B7%A5%E5%85%B7)

<!-- region:toc -->
- [1. ⏰ 搬运 yuque 上的早期文章](#1--搬运-yuque-上的早期文章)
<!-- endregion:toc -->

## 1. ⏰ 搬运 yuque 上的早期文章



# [README.md](./0012.%20DeskPins%20windows%20窗口置顶工具/README.md)<!-- !======> SEPERATOR <====== -->
# [0012. DeskPins windows 窗口置顶工具](https://github.com/Tdahuyou/pc/tree/main/0012.%20DeskPins%20windows%20%E7%AA%97%E5%8F%A3%E7%BD%AE%E9%A1%B6%E5%B7%A5%E5%85%B7)

<!-- region:toc -->
- [1. ⏰ 搬运 yuque 上的早期文章](#1--搬运-yuque-上的早期文章)
<!-- endregion:toc -->

## 1. ⏰ 搬运 yuque 上的早期文章



# [README.md](./0013.%20语雀收藏助手/README.md)<!-- !======> SEPERATOR <====== -->
# [0013. 语雀收藏助手](https://github.com/Tdahuyou/pc/tree/main/0013.%20%E8%AF%AD%E9%9B%80%E6%94%B6%E8%97%8F%E5%8A%A9%E6%89%8B)

<!-- region:toc -->
- [1. ⏰ 搬运 yuque 上的早期文章](#1--搬运-yuque-上的早期文章)
<!-- endregion:toc -->

## 1. ⏰ 搬运 yuque 上的早期文章



# [README.md](./0014.%20screen%20brush%20macos%20屏幕画笔工具/README.md)<!-- !======> SEPERATOR <====== -->
# [0014. screen brush macos 屏幕画笔工具](https://github.com/Tdahuyou/pc/tree/main/0014.%20screen%20brush%20macos%20%E5%B1%8F%E5%B9%95%E7%94%BB%E7%AC%94%E5%B7%A5%E5%85%B7)

<!-- region:toc -->
- [1. ⏰ 搬运 yuque 上的早期文章](#1--搬运-yuque-上的早期文章)
<!-- endregion:toc -->

## 1. ⏰ 搬运 yuque 上的早期文章



# [README.md](./9999.%20仓库简介/README.md)<!-- !======> SEPERATOR <====== -->
# [9999. 仓库简介](https://github.com/Tdahuyou/pc/tree/main/9999.%20%E4%BB%93%E5%BA%93%E7%AE%80%E4%BB%8B)

<!-- region:toc -->
- [1. 📒 pc 仓库内容简介](#1--pc-仓库内容简介)
- [2. 🔗 bilibili 视频链接](#2--bilibili-视频链接)
- [3. ⏰ 搬运 yuque 上的工具分享笔记](#3--搬运-yuque-上的工具分享笔记)
<!-- endregion:toc -->

## 1. 📒 pc 仓库内容简介

- 存放和使用个人电脑（macOS、Widnows）相关的笔记。
  - 记录一些个人的使用习惯
  - 记录一些软件的使用分享
  - ……

## 2. 🔗 bilibili 视频链接

- https://space.bilibili.com/407241004
  - 搜【📒 pc】视频合集

## 3. ⏰ 搬运 yuque 上的工具分享笔记

- [工具分享](https://www.yuque.com/tdahuyou/tools)
- 搬运 yuque 上的工具分享笔记，在搬运之前，可以先回看一下自己在 B 站上发布的工具分享系列的视频，将一些目前不再使用的工具分享的视频给下掉，依旧在使用的工具，可以重新录制分享视频。
  - 在新版的视频中，不要过分强调链接，在之前视频中提到的很多链接，现在来看基本都以及失效了。
  - 新版视频的时长控制好，重点讲清楚工具有什么用，以及如何使用，其他不那么重要的内容可以记录在笔记中，视频中快速带过即可。
- 将 yuque 中记录的相关笔记搬运到当前的笔记仓库中。


