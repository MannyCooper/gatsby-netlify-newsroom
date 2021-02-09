---
template: blog-post
title: 基于腾讯云，给你的 Icarus 博客配上 Twikoo 评论系统
slug: /character-design
date: 2020-05-23 23:40
description: How to draw a character
featuredImage: /assets/twikoo_Cover_light_1-1.png
---

<p><article class="message message-immersive is-info">
  <div class="message-body">
    <i class="fas fa-info-circle"></i>
    本文已被 Twikoo <a href="https://twikoo.js.org/quick-start.html#在-hexo-icarus-主题使用">官方文档</a>收录👌
  </div>
</article><p>

<blockquote>
<p>拖更是不好的。<a class="quote_src" href="https://anzifan.com">异次元de机智君</a></p>
</blockquote>
<article class="message is-info candy-series">   <div class="message-header candy-series-header">  <i class="fas fa-info-circle mr-2"></i>   <p>📚本系列文章，将分成四个板块更新</p>  </div>   <div class="message-body"> 
<ol><li><a href="/post/icarus_to_candy_1/"><strong>基础设计修改</strong></a>
  <span class="icon has-text-success">
  <i class="fas fa-check-square"></i>
</span></li>
<li><a href="/post/icarus_to_candy_2/"><strong>配置 Twikoo 评论</strong></a>
  <span class="icon has-text-success">
  <i class="fas fa-check-square"></i>
</span></li></li>
<li>增加深色模式支持</li>
<li>其他细节与模块</li>
</ol></d/iv> </article>
<style>.candy-series-header {
  justify-content: start !important;
}
  .message.is-info.candy-series{
    width: 50%;
float: right;
margin-left: 20px;
    margin-bottom: 11px !important;
  }
  @media screen and (max-width: 768px){
    .message.is-info.candy-series{
    width: 100%;
float: none;
margin-left: 0;
  }
  }
</style>


太长的文章也是不好的，比如我之前有一篇 Windows 软件推荐文，因为内容太多，已经写了一个多月了，现在看到它就有些恶心（不过肯定会完成的）。所以这篇我会尝试加快脚步去介绍，毕竟 Twikoo 的中文文档目前也比较详细了，其实没什么可写的了，大佬们可以自己[参考](https://twikoo.js.org)。

闲话少说，这篇是 Candy 主题系列的第二篇，每个博客都需要的、~~食之无味弃之可惜的~~评论系统。当然 Candy 主题基于 Icarus 主题，所以对 **Icarus 主题来说也是完全适用的**。

## 为什么选择 Twikoo？

其实 [iMaeGoo](https://www.imaegoo.com) 大佬在官方文档就把理由说的非常清楚了：

>  一个**简洁、安全、免费**的静态网站评论系统，基于腾讯云开发。

「简洁」、「安全」、「免费」、基于国内的云服务，对于一个主体语言是中文的博客来说，还需要更多理由吗？目前的评论系统现状是：「简洁」的，不够安全；「安全」的不一定免费；「免费」的不一定在国内网络环境能很好的访问。

## Twikoo 的特性

作为一款「纯国产」的评论系统，Twikoo 很多特性对于国内博主真的很方便：

1. 采用免费的腾讯云开发，免去二次备案的时间成本；
2. 通过云函数控制敏感信息，防止泄漏；
3. 微信、QQ、邮件…… 多种提醒方式可选；
4. 基于 Akismet 的反垃圾支持；
5. 方便好用的评论管理系统和配置台，直接在博客评论区管理评论和配置其他信息；
6. 博主标示、User Agent 显示、点赞系统、多级评论、支持图片、markdown、Katex 公式……；
7. 活跃、友善的开发者和社区；

除此之外，你还需要明白 Twikoo 是个正在成长中的评论系统，且更新频繁，你可以在这里浏览[开发计划](https://github.com/imaegoo/twikoo/projects/1)。另外，它已被腾讯云官方选为云开发优秀应用。

## 让我们开始吧！

搭建 Twikoo 分两步：

1. 在本地的博客主题中配置 Twikoo；
2. 在腾讯云配置环境和云函数；

在此感谢作者 [iMaeGoo](https://www.imaegoo.com) ，本教程基于它的[魔改版 Icarus](https://github.com/imaegoo/hexo-theme-icarus)，且适用于 Icarus 4.1.1。

### 在本地的博客主题中配置 Twikoo

**第一步：**

在主题目录下 `layout/comment` 中创建 `twikoo.jsx` 并键入：

```jsx twikoo.jsx
const { Component, Fragment } = require('inferno');
const { cacheComponent } = require('hexo-component-inferno/lib/util/cache');

class Twikoo extends Component {
  render() {
    const {
      envId,
      jsUrl,
    } = this.props;
    const js = `twikoo.init({
      envId: '${envId}'
    });`;
    return (
      <Fragment>
        <div id="twikoo" class="content twikoo"></div>
        <script src={jsUrl}></script>
        <script dangerouslySetInnerHTML={{ __html: js }}></script>
      </Fragment>
    );
  }
}

Twikoo.Cacheable = cacheComponent(Twikoo, 'comment.twikoo', (props) => {
  const { comment } = props;
  return {
    envId: comment.envId,
    jsUrl: 'https://cdn.jsdelivr.net/npm/twikoo/dist/twikoo.all.min.js',
  };
});

module.exports = Twikoo;
```

**第二步：**

在 `include/shema/comment` 中创建 `twikoo.json` ，并键入：

```json twikoo.json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "$id": "/comment/twikoo.json",
  "description": "Twikoo comment plugin configurations",
  "type": "object",
  "properties": {
    "type": {
      "type": "string",
      "const": "twikoo"
    },
    "envId": {
      "type": "string",
      "description": "envId from Tencent CloudBase"
    }
  },
  "required": ["type", "envId"]
}  
```

**第三步：**

在 `include/schema/common/comment.json` 中添加 `twikoo.json` 的 `$ref`：

```diff comment.json
        },
         {
             "$ref": "/comment/valine.json"
+        },
+        {
+            "$ref": "/comment/twikoo.json"
         }
     ]
 } 
```

**第四步：**

现在你只需要在 `_config.yml` 文件中  `comment` 部分添加 Twikoo 即可，在 envId 后面请填写你自己的腾讯云环境 ID，这个 ID 你会在下一个板块了解如何获取，现在可以空着：

```yml
comment:
	type: twikoo
	envId: xxxxxxxxxxxxxxx # 腾讯云环境id
	jsUrl: https://cdn.jsdelivr.net/npm/twikoo@0.4.5/dist/twikoo.all.min.js
```

这里需要注意的是最后的 `jsUrl` ，你会发现 twikoo 后面有 @ 版本号。保险起见，目前 twikoo 是需要你手动去更新这个版本号的。如果你不加版本号，这意味着每次都请求最新版本，你可能就必须得及时更新后台云函数了。

感谢评论区提醒👇：

<blockquote>
<p><code>jsUrl</code>中的版本号应该与云函数版本号保持一致<a class="quote_src" href="/post/icarus_to_candy_2/#21ded5cb5ff2db4903ab9cc23c8c4c20">Higurashi-kagome</a></p>
</blockquote>

同样，[更新版本](https://twikoo.js.org/faq.html#如何更新-twikoo-版本)也很简单，后台更新云函数后，改版本号即可。（这里有个坑，建议每次更新版本先删除 `node_modules` 再点击保存并安装依赖）

**第五步（可选）：**

给博客换上 Twikoo 访客计数。在 `layout/common/article.jsx` 中修改 `{/* Visitor counter */}` 部分：

```diff article.jsx
+ {!index ? <span id={url_for(page.link || page.path)} class="level-item twikoo_visitors" data-flag-title={page.title} dangerouslySetInnerHTML={{
-	{!index && plugins && plugins.busuanzi === true ? <span class="level-item" id="busuanzi_container_page_pv" dangerouslySetInnerHTML={{ __html: _p('plugin.visit_count', '<span id="busuanzi_value_page_pv">0</span>')
+	__html: '<i class="far fa-eye"></i>' + _p('plugin.visit_count', '&nbsp;&nbsp;<span id="twikoo_visitors"><i class="fa fa-spinner fa-spin"></i></span>')
}}></span> : null}
```

本地需要修改的部分完成✅

### 在腾讯云配置环境和云函数

### 云环境初始化

我们先来初始化腾讯云环境，使用云开发作为评论后台，每个云开发用户均长期享受 1 个免费的标准型基础版 1 资源套餐，换句话说对于大部分博主来说是免费的。

1. [注册云开发CloudBase](https://curl.qcloud.com/KnnJtUom)
2. 进入[云开发控制台](https://console.cloud.tencent.com/tcb/)，新建环境，请按需配置环境：
   - 环境名称自由填写
   - 推荐选择计费方式`包年包月`，套餐版本`基础班 1`，超出免费额度不会收费
   - 如果提示选择“应用模板”，请选择“空模板”
3. 进入[环境-登录授权](https://console.cloud.tencent.com/tcb/env/login)，启用“匿名登录”；
4. 进入[环境-安全配置](https://console.cloud.tencent.com/tcb/env/safety)，将网站域名添加到“WEB安全域名”；
5. 复制环境 ID，在上一板块中的第四步填写。

### 配置云函数

接下来配置云函数。恭喜你赶上了 Twikoo 的好时代，目前支持的配置方式很多，且更简单，不需要再去踩脚本安装的坑了。

不是我偷懒，这部分官方文档其实说的非常完善且精简了，大家可以直接阅读官方文档的[手把手教程](https://twikoo.js.org/quick-start.html#配置使用)，我这里就引用一下吧：

>1. 进入[环境-云函数](https://console.cloud.tencent.com/tcb/scf/index)，点击“新建云函数”
>2. 函数名称请填写：`twikoo`，创建方式请选择：`空白函数`，运行环境请选择：`Nodejs 10.15`，函数内存请选择：`128MB`，点击“下一步”
>3. 打开 [index.js](https://imaegoo.coding.net/public/twikoo/twikoo/git/files/dev/src/function/twikoo/index.js)，全选代码、复制、粘贴到“函数代码”输入框中，点击“确定”
>4. 创建完成后，点击“twikoo"进入云函数详情页，进入“函数代码”标签，点击“文件 - 新建文件”，输入 `package.json`，回车
>5. 打开 [package.json](https://imaegoo.coding.net/public/twikoo/twikoo/git/files/dev/src/function/twikoo/package.json)，全选代码、复制、粘贴到代码框中，点击“保存并安装依赖”

在这里只有一个建议，尽量采用「① 网页方式」，不要用脚本方式！不要用脚本方式！不要用脚本方式！尤其是在 macOS 下，「授权云开发环境」这步会有些 bug。

---

成功了🎉！你给自己的 Icarus 博客换上了崭崭新的 Twkoo 评论，接下来看看如何管理和配置。

## 配置、管理你的 Twikoo 评论系统

我们来开启管理面板：

1. 进入[环境-登录授权](https://console.cloud.tencent.com/tcb/env/login)，点击“自定义登录”右边的“私钥下载”，下载私钥文件
2. 用文本编辑器打开私钥文件，复制全部内容
3. 你只需要来到最下面的评论区，点击小齿轮 <i class="fas fa-cog"></i> 即可配置更多设置，当然博主是需要登录的，初次进入需要粘贴私钥文件内容，并设置管理员密码。

至于，通知提醒一类的功能，在控制面板中也有相应的引导，我就不在这里废话了。有什么问题欢迎和我交流或查看[官方解答](https://twikoo.js.org/faq.html)。

就这样，结束～

<style>.content {text-align: left !important;}</style>

<a class="tag is-medium" href="mailto:541297173@qq.com?subject=「创造 CANDY 主题，只为更好的交互」一文的封面图授权申请" target="_blank">
<span class="icon" style="word-wrap: break-word;"><i class="fas fa-palette"></i></span>原创封面图，使用需<b>授权</b>，请勿盗用 </a>