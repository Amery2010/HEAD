# 🤯 HEAD

> HTML `<head>` 元素的简单指南

[![Contributors](https://img.shields.io/github/contributors/joshbuchea/head.svg?style=for-the-badge)](https://github.com/joshbuchea/HEAD/graphs/contributors)
[![CC0](https://img.shields.io/badge/license-CC0-green.svg?style=for-the-badge)](https://creativecommons.org/publicdomain/zero/1.0/)
[![Follow @joshbuchea on Twitter](https://img.shields.io/badge/Follow_@joshbuchea-blue?logo=twitter&logoColor=white&style=for-the-badge)](https://twitter.com/joshbuchea)

## 目录

- [最小推荐](#最小推荐)
- [网页元素](#网页元素)
- [Meta 标签](#meta-标签)
- [链接](#链接)
- [网站图标](#网站图标)
- [社交](#社交)
  - [Facebook Open Graph](#facebook-open-graph)
  - [Twitter Card](#twitter-card)
  - [Twitter Privacy](#twitter-privacy)
  - [Schema.org](#schemaorg)
  - [Pinterest](#pinterest)
  - [Facebook Instant Articles](#facebook-instant-articles)
  - [OEmbed](#oembed)
  - [QQ/微信](#qqwechat)
- [浏览器 / 平台](#浏览器--平台)
  - [Apple iOS](#apple-ios)
  - [Google Android](#google-android)
  - [Google Chrome](#google-chrome)
  - [Microsoft Internet Explorer](#microsoft-internet-explorer)
- [国内的浏览器](#国内的浏览器)
  - [360 浏览器](#360-浏览器)
  - [QQ 移动浏览器](#qq-移动浏览器)
  - [UC 移动浏览器](#uc-移动浏览器)
- [应用链接](#应用链接)
- [其他资源](#其他资源)
- [相关项目](#相关项目)
- [其他格式](#其他格式)
- [翻译](#-翻译)
- [贡献](#-贡献)
  - [贡献者](#贡献者)
- [作者](#-作者)
- [许可](#-许可)

## 最小推荐

以下是构成任何 Web 页面（网站/应用程序）的基本要素：

```html
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<!--
  以上 2 个 meta 标签 *必须* 放在 <head> 标签内 最前面，以确保正确的文档呈现；
  其他任何 head 元素 *必须* 在这些标签之后。
-->
<title>页面标题</title>
```

**meta charset** - 定义网站的编码格式，默认为 `utf-8`。

**meta name="viewport"** - 与移动端设备响应式有关的视口设置。

**width=device-width** 表示它将使用设备的物理宽度（而不是缩放），这对于移动设备友好的页面来说是很有帮助。

**initial-scale=1** 默认缩放，1 表示不缩放

**[⬆ 返回顶部](#目录)**

## 网页元素

有效的 `<head>` 元素包括 `meta`、`link`、`title`、`style`、`script`、`noscript` 和 `base`。

这些元素提供了如何通过如浏览器，搜索引擎，网络爬虫等网络技术来感知和呈现文档的信息。

```html
<!-- 设置此文档的字符编码，以便 UTF-8 范围中的所有字符（如 emoji）都能正确显示 -->
<meta charset="utf-8">

<!-- 设置文档标题 -->
<title>页面标题</title>

<!-- 设置文档中所有相对链接的基础链接 -->
<base href="https://example.com/page.html">

<!-- 链接一个外部 CSS 文件 -->
<link rel="stylesheet" href="styles.css">

<!-- 用于文档内的 CSS -->
<style>
  /* ... */
</style>

<!-- JavaScript & No-JavaScript 标签 -->
<script>
  // function(s) go here
</script>
<noscript>
  <!--无 JS 时显示-->
</noscript>
```

**[⬆ 返回顶部](#目录)**

## Meta 标签

```html
<!--
  以上 2 个 meta 标签 *必须* 放在 head 之前，以确保正确的文档呈现；
  其他任何 head 元素 *必须* 在这些标签之后。
  † 如果你的项目需要支持 Internet Explorer 11 之前的版本，请使用 content="ie-edge" 标签。
-->
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">

<!-- 允许控制资源从何处加载。在 <head> 中尽可能地靠前放置，因为该标签仅适用于在其之后声明的资源。-->
<meta http-equiv="Content-Security-Policy" content="default-src 'self'">

<!-- Web 应用的名称（仅当网站被用作为一个应用时才使用）-->
<meta name="application-name" content="应用名称">

<!-- Chrome、Firefox OS 和 Opera 的主题颜色 -->
<meta name="theme-color" content="#4285f4">

<!-- 针对页面的简短描述（限制 150 字符）-->
<!-- 此内容*可能*被用作搜索引擎结果的一部分。 -->
<meta name="description" content="一个页面描述">

<!-- 控制搜索引擎的抓取和索引行为 -->
<meta name="robots" content="index,follow"><!-- 所有搜索引擎 -->
<meta name="googlebot" content="index,follow"><!-- 仅对 Google 有效 -->

<!-- 告诉 Google 不显示网站链接的搜索框 -->
<meta name="google" content="nositelinkssearchbox">

<!-- 告诉 Google 不提供此页面的翻译 -->
<meta name="google" content="notranslate">

<!-- 验证网址所有权 -->
<meta name="google-site-verification" content="verification_token"><!-- Google Search Console -->
<meta name="yandex-verification" content="verification_token"><!-- Yandex Webmasters -->
<meta name="msvalidate.01" content="verification_token"><!-- Bing Webmaster Center -->
<meta name="alexaVerifyID" content="verification_token"><!-- Alexa Console -->
<meta name="p:domain_verify" content="code from pinterest"><!-- Pinterest Console -->
<meta name="norton-safeweb-site-verification" content="norton code"><!-- Norton Safe Web -->

<!-- 确定用于构建页面的软件（如 - WordPress、Dreamweaver）-->
<meta name="generator" content="program">

<!-- 关于你的网站主题的简短描述 -->
<meta name="subject" content="你的网站主题">

<!-- 基于网站内容给出一般的年龄分级 -->
<meta name="rating" content="General">

<!-- 允许控制 referrer 信息如何传递 -->
<meta name="referrer" content="no-referrer">

<!-- 禁用自动检测和格式化可能的电话号码 -->
<meta name="format-detection" content="telephone=no">

<!-- 通过设置为 "off" 完全退出 DNS 预取 -->
<meta http-equiv="x-dns-prefetch-control" content="off">

<!-- 指定要显示在一个特定框架中的页面 -->
<meta http-equiv="Window-Target" content="_value">

<!-- 地理标签 -->
<meta name="ICBM" content="latitude, longitude">
<meta name="geo.position" content="latitude;longitude">
<meta name="geo.region" content="country[-state]"><!-- 国家代码 (ISO 3166-1): 强制性, 州代码 (ISO 3166-2): 可选; 如 content="US" / content="US-NY" -->
<meta name="geo.placename" content="city/town"><!-- 如 content="New York City" -->
<meta name="monetization" content="$paymentpointer.example"><!-- 网络货币化 https://webmonetization.org/docs/getting-started -->
```

- 📖 [Google 可以识别的 Meta 标签](https://support.google.com/webmasters/answer/79812?hl=zh-Hans)
- 📖 [WHATWG Wiki: Meta 拓展](https://wiki.whatwg.org/wiki/MetaExtensions)
- 📖 [ICBM - 维基百科](https://en.wikipedia.org/wiki/ICBM_address#Modern_use)
- 📖 [地理标记 - 维基百科](https://en.wikipedia.org/wiki/Geotagging#HTML_pages)

**[⬆ 返回顶部](#目录)**

## 链接

```html
<!-- 指向一个外部 CSS 样式表 -->
<link rel="stylesheet" href="https://example.com/styles.css">

<!-- 有助于防止出现内容重复的问题 -->
<link rel="canonical" href="https://example.com/article/?page=2">

<!-- 链接到当前文档的一个 AMP HTML 版本 -->
<link rel="amphtml" href="https://example.com/path/to/amp-version.html">

<!-- 链接到一个指定 Web 应用程序“安装”凭据的 JSON 文件 -->
<link rel="manifest" href="manifest.json">

<!-- 链接到关于页面所有者的信息 -->
<link rel="author" href="humans.txt">

<!-- 指向一个适用于链接内容的版权申明 -->
<link rel="license" href="copyright.html">

<!-- 给出可能的你的另一种语言的文档位置参考 -->
<link rel="alternate" href="https://es.example.com/" hreflang="es">

<!-- 提供了关于作者或其他人的信息 -->
<link rel="me" href="https://google.com/profiles/thenextweb" type="text/html">
<link rel="me" href="mailto:name@example.com">
<link rel="me" href="sms:+15035550125">

<!-- 链接到一个描述历史记录、文档或其他具有历史意义的材料的集合的文档 -->
<link rel="archives" href="https://example.com/archives/">

<!-- 链接到层次结构中的顶级资源 -->
<link rel="index" href="https://example.com/article/">

<!-- 提供了自我引用 - 当文档有多个可能的引用时非常有用 -->
<link rel="self" type="application/atom+xml" href="https://example.com/atom.xml">

<!-- 分别是一系列页面中的第一个，最后一个，上一个和下一个页面 -->
<link rel="first" href="https://example.com/article/">
<link rel="last" href="https://example.com/article/?page=42">
<link rel="prev" href="https://example.com/article/?page=1">
<link rel="next" href="https://example.com/article/?page=3">

<!-- 当使用第三方服务来维护博客时使用 -->
<link rel="EditURI" href="https://example.com/xmlrpc.php?rsd" type="application/rsd+xml" title="RSD">

<!-- 当另一个 WordPress 博客链接到你的 WordPress 博客或文章时形成一个自动化的评论 -->
<link rel="pingback" href="https://example.com/xmlrpc.php">

<!-- 当你在自己的页面上链接到一个 url 时通知它 -->
<link rel="webmention" href="https://example.com/webmention">

<!-- 启用通过 Micropub 客户端发布你的域名 -->
<link rel="micropub" href="https://example.com/micropub">

<!-- 打开搜索 -->
<link rel="search" href="/open-search.xml" type="application/opensearchdescription+xml" title="Search Title">

<!-- Feeds -->
<link rel="alternate" href="https://feeds.feedburner.com/example" type="application/rss+xml" title="RSS">
<link rel="alternate" href="https://example.com/feed.atom" type="application/atom+xml" title="Atom 0.3">

<!-- 预取，预载，预浏览 -->
<!-- 更多信息：https://css-tricks.com/prefetching-preloading-prebrowsing/ -->
<link rel="dns-prefetch" href="//example.com/">
<link rel="preconnect" href="https://www.example.com/">
<link rel="prefetch" href="https://www.example.com/">
<link rel="prerender" href="https://example.com/">
<link rel="preload" href="image.png" as="image">
```

- 📖 [链接关系](https://www.iana.org/assignments/link-relations/link-relations.xhtml)

**[⬆ 返回顶部](#目录)**

## 网站图标

```html
<!-- 针对 IE 10 及以下版本 -->
<!-- 如果将 `favicon.ico` 放在根目录下，则无需标签 -->

<!-- 我们目前需要提供的最大的网站图标尺寸 -->
<link rel="icon" sizes="192x192" href="/path/to/icon.png">

<!-- Apple 触摸图标 (尺寸同样是 192x192) -->
<link rel="apple-touch-icon" href="/path/to/apple-touch-icon.png">

<!-- Safari 固定选项卡图标 -->
<link rel="mask-icon" href="/path/to/icon.svg" color="blue">
```

- 📖 [所有关于网站图标（和触摸图标）的信息](https://bitsofco.de/all-about-favicons-and-touch-icons/)
- 📖 [创建固定选项卡图标](https://developer.apple.com/library/content/documentation/AppleApplications/Reference/SafariWebContent/pinnedTabs/pinnedTabs.html)
- 📖 [网站图标对照表](https://github.com/audreyr/favicon-cheat-sheet)
- 📖 [网址图标 & 浏览器颜色表](https://developers.google.com/web/fundamentals/design-and-ux/browser-customization/)

**[⬆ 返回顶部](#目录)**

## 社交

### Facebook Open Graph
> 大多数内容以 URL 的形式共享到 Facebook，因此使用 Open Graph 标签标记您的网站以控制您的内容在 Facebook 上的显示方式就显得非常重要了。[更多关于 Facebook 开放图谱标记的信息](https://developers.facebook.com/docs/sharing/webmasters#markup)

> 大多数内容都是作为 URL 分享到 Facebook 的，因此，使用 Open Graph 标签标记网站来控制内容在 Facebook 上的显示方式显得尤为重要。[有关 Facebook Open Graph 标签的更多信息](https://developers.facebook.com/docs/sharing/webmasters#markup) 


```html
<meta property="fb:app_id" content="123456789">
<meta property="og:url" content="https://example.com/page.html">
<meta property="og:type" content="website">
<meta property="og:title" content="Content Title">
<meta property="og:image" content="https://example.com/image.jpg">
<meta property="og:image:alt" content="A description of what is in the image (not a caption)">
<meta property="og:description" content="Description Here">
<meta property="og:site_name" content="Site Name">
<meta property="og:locale" content="en_US">
<meta property="article:author" content="">
```

- 📖 [Open Graph 协议](https://ogp.me/)
- 🛠 [页面验证 - Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/)

### Twitter Card
> 借助 Twitter 卡片，您可以将丰富的照片、视频和媒体体验附加到推文中，从而帮助您的网站增加流量。[更多关于 Twitter 卡片的信息](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/abouts-cards)

> 使用 Twitter Card，您可以将丰富的照片、视频和媒体资源附加到推文上，以帮助增加网站的访问量。[有关 Twitter Card 的更多信息](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/abouts-cards)

```html
<meta name="twitter:card" content="summary">
<meta name="twitter:site" content="@site_account">
<meta name="twitter:creator" content="@individual_account">
<meta name="twitter:url" content="https://example.com/page.html">
<meta name="twitter:title" content="Content Title">
<meta name="twitter:description" content="Content description less than 200 characters">
<meta name="twitter:image" content="https://example.com/image.jpg">
<meta name="twitter:image:alt" content="A text description of the image conveying the essential nature of an image to users who are visually impaired. Maximum 420 characters.">
```

- 📖 [名片入门指南 - Twitter 开发者](https://dev.twitter.com/cards/getting-started)
- 🛠 [页面验证 - Twitter Card Validator](https://cards-dev.twitter.com/validator)

### Twitter Privacy
如果你在自己的网站中嵌入了推文，Twitter 可以使用你网站上的信息为 Twitter 用户定制内容和建议。 [更多关于 Twitter 隐私选项的信息](https://dev.twitter.com/web/overview/privacy#what-privacy-options-do-website-publishers-have).
```html
<!-- 禁止 Twitter 使用你网站上的信息用于提供个性化的目的 -->
<meta name="twitter:dnt" content="on">
```

### Schema.org

```html
<html lang="" itemscope itemtype="https://schema.org/Article">
  <head>
    <link rel="author" href="">
    <link rel="publisher" href="">
    <meta itemprop="name" content="内容标题">
    <meta itemprop="description" content="内容描述少于 200 个字符">
    <meta itemprop="image" content="https://example.com/image.jpg">
```

**注意:** 这些 meta 标签需要在 `<html>` 中添加 `itemscope` 和 `itemtype` 属性。

- 📖 [入门 - schema.org](https://schema.org/docs/gs.html)
- 🛠 使用[多结果测试](https://search.google.com/test/rich-results)测试您的页面 

### Pinterest

根据他们的[帮助中心](https://help.pinterest.com/en/business/article/prevent-saves-to-pinterest-from-your-site)可知，Pinterest 允许你禁止他人保存你网站里的内容。`description` 为可选。

```html
<meta name="pinterest" content="nopin" description="Sorry, you can't save from my website!">
```

### Facebook Instant Articles

```html
<meta charset="utf-8">
<meta property="op:markup_version" content="v1.0">

<!-- 你的文章的 Web 版网址 -->
<link rel="canonical" href="https://example.com/article.html">

<!-- 用于该文章的样式 -->
<meta property="fb:article_style" content="myarticlestyle">
```

- 📖 [创建文章 - Instant Articles](https://developers.facebook.com/docs/instant-articles/guides/articlecreate)
- 📖 [代码示例 - Instant Articles](https://developers.facebook.com/docs/instant-articles/reference)

### OEmbed

```html
<link rel="alternate" type="application/json+oembed"
  href="https://example.com/services/oembed?url=http%3A%2F%2Fexample.com%2Ffoo%2F&amp;format=json"
  title="oEmbed Profile: JSON">
<link rel="alternate" type="text/xml+oembed"
  href="https://example.com/services/oembed?url=http%3A%2F%2Fexample.com%2Ffoo%2F&amp;format=xml"
  title="oEmbed Profile: XML">
```

- 📖 [oEmbed 格式](https://oembed.com/)

### QQ/微信

用户将网页分享到 QQ 或微信会带有指定信息。

```html
<meta itemprop="name" content="分享标题">
<meta itemprop="image" content="http://imgcache.qq.com/qqshow/ac/v4/global/logo.png">
<meta name="description" itemprop="description" content="分享描述">
```
- 📖 [分享格式文档](http://open.mobile.qq.com/api/mqq/index#api:setShareInfo)


**[⬆ 返回顶部](#目录)**

## 浏览器 / 平台

### Apple iOS

```html
<!-- 智能应用 Banner -->
<meta name="apple-itunes-app" content="app-id=APP_ID,affiliate-data=AFFILIATE_ID,app-argument=SOME_TEXT">

<!-- 禁用自动检测和格式化可能的电话号码 -->
<meta name="format-detection" content="telephone=no">

<!-- 添加到主屏幕 -->
<!-- 启动图标 (大于等于 180x180px) -->
<link rel="apple-touch-icon" href="/path/to/apple-touch-icon.png">

<!-- 启动屏幕图片 -->
<link rel="apple-touch-startup-image" href="/path/to/launch.png">

<!-- 启动图标的标题 -->
<meta name="apple-mobile-web-app-title" content="应用标题">

<!-- 启用独立（全屏）模式 -->
<meta name="apple-mobile-web-app-capable" content="yes">

<!-- 状态栏外观（除非启用独立模式，否则无效） -->
<meta name="apple-mobile-web-app-status-bar-style" content="black">

<!-- iOS 应用深层链接 -->
<meta name="apple-itunes-app" content="app-id=APP-ID, app-argument=http/url-sample.com">
<link rel="alternate" href="ios-app://APP-ID/http/url-sample.com">
```

- 📖 [配置 Web 应用程序](https://developer.apple.com/library/content/documentation/AppleApplications/Reference/SafariWebContent/ConfiguringWebApplications/ConfiguringWebApplications.html)

### Google Android

```html
<meta name="theme-color" content="#E64545">

<!-- 添加到主屏幕 -->
<meta name="mobile-web-app-capable" content="yes">
<!-- 更多信息：https://developer.chrome.com/multidevice/android/installtohomescreen -->
```

### Google Chrome

```html
<link rel="chrome-webstore-item" href="https://chrome.google.com/webstore/detail/APP_ID">

<!-- 禁用翻译提示 -->
<meta name="google" content="notranslate">
```

### Microsoft Internet Explorer

```html
<!-- 强制 IE 8/9/10 使用其最新的渲染引擎 -->
<meta http-equiv="x-ua-compatible" content="ie=edge">

<!-- 通过 Skype Toolbar 浏览器扩展功能禁用自动检测和格式化可能的电话号码 -->
<meta name="skype_toolbar" content="skype_toolbar_parser_compatible">

<!-- Windows 磁贴 -->
<meta name="msapplication-config" content="/browserconfig.xml">
```

最低要求的的 `browserconfig.xml` 配置：

```xml
<?xml version="1.0" encoding="utf-8"?>
<browserconfig>
  <msapplication>
    <tile>
      <square70x70logo src="small.png"/>
      <square150x150logo src="medium.png"/>
      <wide310x150logo src="wide.png"/>
      <square310x310logo src="large.png"/>
    </tile>
  </msapplication>
</browserconfig>
```

- 📖 [浏览器配置模式参考](https://msdn.microsoft.com/en-us/library/dn320426.aspx)

**[⬆ 返回顶部](#目录)**

## 国内的浏览器

### 360 浏览器

```html
<!-- 选择渲染引擎 -->
<meta name="renderer" content="webkit|ie-comp|ie-stand">
```

### QQ 移动浏览器

```html
<!-- 在指定方向上锁定屏幕（锁定横/竖屏） -->
<meta name="x5-orientation" content="landscape/portrait">
<!-- 全屏显示此页面 -->
<meta name="x5-fullscreen" content="true">
<!-- 页面将以“应用模式”显示（全屏等）-->
<meta name="x5-page-mode" content="app">
```

### UC 移动浏览器

```html
<!-- 在指定方向上锁定屏幕（锁定横/竖屏） -->
<meta name="screen-orientation" content="landscape/portrait">

<!-- 全屏显示此页面 -->
<meta name="full-screen" content="yes">

<!-- 即使在“文本模式”下，UC 浏览器也会显示图片 -->
<meta name="imagemode" content="force">

<!-- 页面将以“应用模式”显示（全屏、禁止手势等） -->
<meta name="browsermode" content="application">

<!-- 在此页面禁用 UC 浏览器的“夜间模式” -->
<meta name="nightmode" content="disable">

<!-- 简化页面，减少数据传输 -->
<meta name="layoutmode" content="fitscreen">

<!-- 禁用的 UC 浏览器的功能，“当此页面中有较多文本时缩放字体” -->
<meta name="wap-font-scale" content="no">
```

- 📖 [UC 浏览器文档](https://www.uc.cn/download/UCBrowser_U3_API.doc)

**[⬆ 返回顶部](#目录)**

## 应用链接

```html
<!-- iOS -->
<meta property="al:ios:url" content="applinks://docs">
<meta property="al:ios:app_store_id" content="12345">
<meta property="al:ios:app_name" content="App Links">

<!-- Android -->
<meta property="al:android:url" content="applinks://docs">
<meta property="al:android:app_name" content="App Links">
<meta property="al:android:package" content="org.applinks">

<!-- 页面回退 -->
<meta property="al:web:url" content="https://applinks.org/documentation">
```

- 📖 [应用链接文档](https://developers.facebook.com/docs/applinks)

**[⬆ 返回顶部](#目录)**

## 其他资源

- 📖 [HTML5 样板文档：HTML 标签](https://github.com/h5bp/html5-boilerplate/blob/master/dist/doc/html.md)
- 📖 [HTML5 样板文档：扩展和定制](https://github.com/h5bp/html5-boilerplate/blob/master/dist/doc/extend.md)

**[⬆ 返回顶部](#目录)**

## 相关项目

- [Atom HTML Head 片段](https://github.com/joshbuchea/atom-html-head-snippets) - Atom `HEAD` 片段包
- [Sublime Text HTML Head 片段](https://github.com/marcobiedermann/sublime-head-snippets) - Sublime Text `HEAD` 片段包
- [head-it](https://github.com/hemanth/head-it) - `HEAD` 片段的 CLI 接口
- [vue-head](https://github.com/ktquez/vue-head) - 在 Vue.js 中操作 `HEAD` 标签的 meta 信息

**[⬆ 返回顶部](#目录)**

## 其他格式

- 📄 [PDF](https://gitprint.com/joshbuchea/HEAD/blob/master/README.md)

**[⬆ 返回顶部](#目录)**

## 🌐 翻译

- 🇺🇸 [英语/English](https://github.com/joshbuchea/HEAD)
- 🇨🇳 [简体中文/Chinese (Simplified)](https://github.com/Amery2010/HEAD)
- 🇩🇪 [德语/German](https://github.com/Shidigital/HEAD)
- 🇮🇩 [印尼语/Bahasa](https://github.com/rijdz/HEAD)
- 🇧🇷 [巴西葡萄牙语/Brazilian Portuguese](https://github.com/Webschool-io/HEAD)
- 🇮🇹 [意大利语/Italian](https://github.com/Fakkio/HEAD)
- 🇯🇵 [日语/Japanese](https://coliss.com/articles/build-websites/operation/work/collection-of-html-head-elements.html)
- 🇰🇷 [韩语/Korean](https://github.com/Lutece/HEAD)
- 🇷🇺 [俄罗斯语/Russian/Русский](https://github.com/Konfuze/HEAD)
- 🇪🇸 [西班牙语/Spanish](https://github.com/alvaroadlf/HEAD)
- 🇹🇷 [土耳其语/Turkish/Türkçe](https://github.com/mkg0/HEAD)

**[⬆ 返回顶部](#目录)**

## 🤝 贡献

**开启一个 issue 或一个 pull 请求来提出修改或补充。**

### 指南

** HEAD ** 仓库由两个分支组成：

#### 1、`master`

对该分支包含的 `README.md` 文件的修改会自动反映在 [htmlhead.dev](https://htmlhead.dev/) 网站上。 所有对照表内容的更改都应该针对此文件。

请按照下列步骤 pull 请求：

- 只修改一个标签，或一次一组相关的标签
- 对属性使用双引号
- 请不要在自我闭合的元素中使用斜线 —— 即便 HTML5 规范中说，他们是可选的
- 考虑在文档中加入链接以支持你所提到的变化

#### 2. `gh-pages`

该分支负责 [htmlhead.dev](https://htmlhead.dev/) 网站。我们使用 [Jekyll](https://jekyllrb.com/) 通过 [GitHub Pages](https://pages.github.com/) 服务来部署 `README.md` Markdown 文件。所有网站相关的修改必须集中在这里。

你可能需要通过 [Jekyll 文档](https://jekyllrb.com/docs/home/) 来了解 Jekyll 是如何在该分支上工作的。

### 贡献者

列出所有超级棒的 [贡献者们](https://github.com/joshbuchea/HEAD/graphs/contributors).

## 👤 作者

**Josh Buchea**

- Twitter: [@joshbuchea](https://twitter.com/joshbuchea)
- Github: [@joshbuchea](https://github.com/joshbuchea)

### 翻译者

**[子丶言](https://xiangfa.org/)**


## 表达您的支持

如果这个项目对您有帮助，请 ⭐️ 这个仓库！

<a href="https://www.patreon.com/joshbuchea">
  <img src="https://c5.patreon.com/external/logo/become_a_patron_button@2x.png" width="160">
</a>

## 📝 许可

![CC0](https://i.creativecommons.org/p/zero/1.0/88x31.png "CC0")

**[⬆ 返回顶部](#目录)**
