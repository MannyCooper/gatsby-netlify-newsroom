---
template: blog-post
title: 一日一技？「扩展」并重新认识 macOS 控制中心
slug: /gaming-extravaganza
date: 2020-05-13 12:55
description: 「扩展」、细节、键盘快捷键支持和一些杂谈
featuredImage: "https://cdn.sspai.com/2020/12/29/e8413b09a7a6df2dd035fe64782f9e20.png"
---

<p><article class="message message-immersive is-info">
  <div class="message-body">
    <i class="fas fa-info-circle"></i>
    本文首发于<b>少数派</b>
    <img class="not-gallery-item" src="https://cdn.sspai.com/2019/10/10/55eccb51ac1e4c2ac60ce7ffed8a0618.jpg?imageMogr2/auto-orient/quality/95/thumbnail/!64x64r/gravity/Center/crop/64x64/interlace/1"style="width: 12px; height: 12px; border-top-left-radius: 32px; border-top-right-radius: 32px; border-bottom-right-radius: 32px; border-bottom-left-radius: 32px;" data-src="https://cdn.sspai.com/2019/10/10/55eccb51ac1e4c2ac60ce7ffed8a0618.jpg?imageMogr2/auto-orient/quality/95/thumbnail/!64x64r/gravity/Center/crop/64x64/interlace/1" lazy="loaded"> 👉 <a href="https://sspai.com/post/64238">一日一技？「扩展」并重新认识 macOS 控制中心</a>
  </div>
  <img src="https://cdn.sspai.com/2019/10/10/55eccb51ac1e4c2ac60ce7ffed8a0618.jpg?imageMogr2/auto-orient/quality/95/thumbnail/!64x64r/gravity/Center/crop/64x64/interlace/1"style="border-radius: 60px;
position: absolute;
right: 10px;
top: 10px;
width: 35px;
filter: opacity(0.8);" data-src="https://cdn.sspai.com/2019/10/10/55eccb51ac1e4c2ac60ce7ffed8a0618.jpg?imageMogr2/auto-orient/quality/95/thumbnail/!64x64r/gravity/Center/crop/64x64/interlace/1" lazy="loaded">
</article><p>


嗨，我是**异次元de机智君**，又见面了。

今天要介绍的是 macOS Big Sur 中新加入的**控制中心**。

对于它的基础用法，少数派编辑部已经在第一时间 [介绍过了](https://sspai.com/post/62640)，我只挑没提到的来说说。

本文你将看到：

1. 控制中心的「扩展」
2. 关于控制中心的更多细节
3. 通过键盘快捷键启动控制中心
4. 我对控制中心的理解

为什么「一日一技」后要跟问号？因为可能太过简单了，算不上「技」。

那为什么我还要写？因为我发现作为一个新特性似乎没有人在谈论。（还是因为太过简单了吧……）

万一有人需要但还不知道呢？总而言之，一起来看看吧。

## 真没想到，控制中心还能「扩展」？

这是我翻「 系统偏好设置」的时候无意间看到的……

打开「系统偏好设置」-「程序坞与菜单栏」，找到「其他模块」，现在你可以把「辅助功能快捷键」、「电池」、「快速用户切换」也一并加在控制中心里了。

![目前只有这三个是可选的](https://cdn.sspai.com/2020/12/26/5e429557da390b210b5d59e5c0cead3d.png)

我们来把它们都打开，看看效果。



<a class="gallery-item" target="_blank" rel="noopener" href="https://cdn.sspai.com/2020/12/26/bdd2e96fdee13dc80c0b752249a207ab.png" style=""><img src="https://cdn.sspai.com/2020/12/26/bdd2e96fdee13dc80c0b752249a207ab.png" alt="img" style="width: 45%;display: inline-block;margin-right: 10px;"></a><a class="gallery-item" target="_blank" rel="noopener" href="https://cdn.sspai.com/2020/12/26/afefc80a6e90449b106bc47fc37a5ae9.png" style="display: inline;"><img src="https://cdn.sspai.com/2020/12/26/afefc80a6e90449b106bc47fc37a5ae9.png"  style="width: 50%;display: inline-block;"></a><p class="has-text-centered is-size-6 caption">左：原版，右：「扩展」后</p>



现在你可以直接在菜单栏右上角的控制中心中访问电池电量信息、辅助功能和切换用户了。这三个新增按钮与其它组件的选单逻辑保持一致。

## 更多细节，别忘了它的二级选单

少数派上的所有相关文章都只是在强调你可以将图标拖拽到菜单栏使用，忽略了一个也很重要的二级选单支持，简单来说它才是真正实现「控制」这一词的核心，否则控制中心只是一个展示窗口。

如果我们把图标都从控制中心拖到菜单栏，那我们还要控制中心干嘛？不如叫它「收纳中心」了。当然，我并不是在试图强行扭转你长久以来的使用逻辑，但我们至少可以对这个新特性更加了解，再做出选择。

苹果在控制中心里确确实实地做了二级选单，这意味着你可以点击其中一个图标进行更多的设置。这个选单是和原有的菜单栏图标选单内容一致的，但很细节的是**你可以通过再次点击控制中心图标或点击功能标题返回一级选单**，在这个过程中你可以看到缩放动画——这说明在控制中心的交互逻辑里，是把这些控制按钮当作装在一大盒子里一个个小盒子来看待的，它们之间是有层级和包含关系的。

<img src="https://cdn.sspai.com/2020/12/29/f7c0076426ed6d857c85c5a893ab1add.gif" style="height:500px" /><p class="has-text-centered is-size-6 caption">动效体现了控制中心的逻辑，你可以点击一次选单操作多个设置<p>

这个交互逻辑事实上大部分时候会让用户多一次点击操作，我相信这也是为什么很多老用户不会去用它的原因，但你得到了一个更可能简洁的菜单栏，且合理的分块让一些设置更直观更好找，是空间换时间。而且在一些需要调整多个设置的场景下，比如同时滑动调整音量和切歌，控制中心所需要的点击数是比传统菜单栏要少的。

## 来给控制中心加个键盘快捷键

遗憾的是，目前官方并不支持任何键盘快捷键操作控制中心，这对于桌面端难免有些不友好，但是别担心，机智君也帮你准备了 AppleScript +「自动操作」的教程和之前 [介绍过](https://sspai.com/post/64173) 的 Keysmith 宏指令来部分解决这一尴尬。

### AppleScript +「自动操作」

**第一步：** 打开系统自带的「自动操作」，并创建「快速操作」。

![强调一下，必须得是「快速操作」，别选错了。](https://cdn.sspai.com/2020/12/29/fdaedc30ce66b23e4bc00e24a0ab2e43.png)

**第二步： ** 在左侧搜索 AppleScript 并将「运行 AppleScript」拖动到右侧，在窗体中键入：

```AppleScript
tell application "System Events"
    tell process "ControlCenter"
        tell menu bar item "控制中心" of menu bar 1
            click
        end tell
    end tell
end tell
```

并保存，记得取一个自己记得住的名字，比如「打开控制中心」。

<img src="https://cdn.sspai.com/2020/12/29/ea4346a536b0797e0f4adc4fce5267d2.png"/><p class="has-text-centered is-size-6 caption"><kbd>⌘ Cmd</kbd> + <kbd>S</kbd> 快捷保存</p>

**第三步：** 打开系统偏好设置-键盘，选择「快捷键」标签，点击左侧的「服务」。在「通用」中找到你刚刚命名的快速操作，并点击右侧「无」来录制键盘快捷键。

![这样就可以快捷键控制了](https://cdn.sspai.com/2020/12/29/686f815f4a43536e056ef26df9e48866.png)

#### 此法的局限

这个方法也有局限，还挺恶心的——你必须在「隐私」-「辅助功能」设置中把你希望此快捷键生效的应用都勾选，否则会报错：

<img src="https://cdn.sspai.com/2020/12/29/a09248827e770a15f1b2771a16c7bb05.png" alt="类似这样" style="width: 450px;" />

这也太麻烦了！当然，既然是基于 AppleScript 你完全可以通过其它自动化应用来激活，这样就不会有这种问题了，比如 BetterTouchTool 等。

### Keysmith 宏指令

你也可以选择我此前介绍的 Keysmith，你可以在 [这里](https://sspai.com/post/64173) 获得详细介绍。我就不多说明制作过程了，需要的朋友可以直接点击 [链接](https://www.icloud.com/iclouddrive/04rFdye3Rw51bEw86gfFSgBFg) 获取我制作的一些基于 Keysmith 的控制中心自动指令，直接导入 Keysmith 使用。

![我简单制作了四种指令](https://cdn.sspai.com/2020/12/29/168ccf994166ba514ad39c54a4fe0cdb.png)

------





不过目前来看，任何方法都有一个问题：控制中心本身不支持键盘操作，我们不能在通过快捷键打开控制中心后继续用键盘选中、确认组件或返回一级选单等。

相信苹果会解决的。

## 我到底为什么介绍控制中心

好吧，我承认这未免有些「标题党」。毕竟这些内容远远达不到「扩展」的程度，但我还是想好好说说我为什么写它。

### 它缘何诞生?

事先说好，理论上来说 macOS 和 iOS 不会融合，Mac 也暂时不会支持触屏，对于这一点有疑问的可以从很多方面获知这一信息：比如 2018 年的 WWDC、iPadOS 命名的诞生、CNET News 对 Craig Federighi 的 [采访](https://v.youku.com/v_show/id_XMTc4NTEzMTUxMg==.html) 等。

**那为什么苹果会选择在 macOS 新版本拥抱 iOS/iPadOS 的视觉和部分交互呢？**

![「神似」](https://cdn.sspai.com/2020/12/29/bbde15cb517ba2c442dcd4fc59453f0f.png)

我想更多是出于**品牌辨识度和学习成本**的考虑——对于一个完全不了解苹果产品线的潜在用户来说，看到 iPadOS 和 macOS 的程序坞，大概心里就会觉得它们出自一家之手。而这在某种程度上也可以帮助 iPhone 和 iPad 用户更平滑地接受 macOS，缓解他们先入为主的畏难心理。

> 控制中心？哦，和 iOS/iPadOS 上的一样，用来快捷控制系统设置的，都是通过右上角调出，那我会了。
>
> 程序坞？哦，和 iPadOS 上长的一样，可以拖动来放置软件，点一下就能启动了。

其次便是为了打通多个平台做准备。这点不用我多说，看看 ARM Mac 的势头，明眼人都能获悉了。不过具体打通方式可能需要一篇长文分析，我在此就不发表拙见了。

------





当然部分老用户们可能并不喜欢，他们对新系统的要求可能是「保持我的使用习惯」和「更多新特性」，但遗憾的是这两者有时会有些矛盾。说服或淘汰还是妥协老用户，这些我说了不算，而是苹果应该抉择的。

至少在 macOS Big Sur 上可以「菜单栏」、「控制中心」双添加，苹果选择了妥协。不过以后呢？**提前意识到这一趋势，让我们对自己的设备使用和选择更有掌控力。**

### 有对比就有伤害，更强的第三方解决方案

本文其实是我拿官方的控制中心「抛砖引玉」一下，相信很多 Power User 对于控制中心的不满来自于它超低可自定义性。在这一方面，第三方解决方案就自由的多，为了防止偏题，就不在本文详细展开了。我将会在近期介绍这个基于 BetterTouchTool 的第三方控制中心预设，名为 [MCC](https://community.folivora.ai/t/macos-control-center-mcc/13058)。感兴趣的朋友可以点击链接提前了解，或关注我之后的介绍文。

![最后，来张图吊吊胃口](https://cdn.sspai.com/2020/12/29/4f4923ecafe18d0d2ebf0da8e04076e6.jpeg)

### 扩展阅读（并不代表本人赞成）：

[Here’s Why Control Center Is MacOS Big Sur’s Best Feature | Digital Trends](https://www.digitaltrends.com/computing/control-center-best-feature-macos-big-sur/)