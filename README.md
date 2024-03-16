# 🤯 HEAD

> HTML `<head>` 元素的简单指南

[![贡献者](https://img.shields.io/github/contributors/joshbuchea/head.svg?style=for-the-badge)](https://github.com/joshbuchea/HEAD/graphs/contributors)
[![CC0](https://img.shields.io/badge/license-CC0-green.svg?style=for-the-badge)](https://creativecommons.org/publicdomain/zero/1.0/)
[![在 Mastodon 上关注 @joshbuchea](https://img.shields.io/badge/Follow_@joshbuchea-purple?logo=mastodon&logoColor=white&style=for-the-badge)](https://hachyderm.io/@joshbuchea)

## 目录

- [最小推荐](#最小推荐)
- [网页元素](#网页元素)
- [Meta 标签](#Meta-标签)
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
  - [QQ/微信](#qq微信)
- [浏览器 / 平台](#浏览器--平台)
  - [Apple iOS](#apple-ios)
  - [Google Android](#google-android)
  - [Google Chrome](#google-chrome)
  - [Microsoft Internet Explorer](#microsoft-internet-explorer)
- [国内浏览器](#国内浏览器)
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
  - [翻译者](#翻译者)
- [许可](#-许可)

## 最小推荐

以下是任何网页文档（网站/应用程序）的基本元素：

```html
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<!--
  上述 2 个 meta 标签 *必须* 在 <head> 中首先出现
  以确保正确的文档呈现。
  任何其他 head 元素应该在这些标签之后出现。
 -->
<title>页面标题</title>
```

`meta charset` - 定义网站的编码，`utf-8` 是标准

`meta name="viewport"` - 与移动响应相关的视口设置

`width=device-width` - 使用设备的物理宽度（非常适用于移动设备！）

`initial-scale=1` - 初始缩放，1 表示无缩放

**[⬆ 返回顶部](#目录)**

## 网页元素

有效的 `<head>` 元素包括 `meta`、`link`、`title`、`style`、`script`、`noscript` 和 `base`。

这些元素提供了关于文档如何被 Web 技术（例如浏览器、搜索引擎、爬虫等）感知和呈现的信息。

```html
<!--
  设置文档的字符编码，以便
  所有在 UTF-8 空间（如表情符号）中的字符
  能够正确呈现。
-->
<meta charset="utf-8" />

<!-- 设置文档的标题 -->
<title>页面标题</title>

<!-- 为文档中所有相对 URL 设置基本 URL -->
<base href="https://example.com/page.html" />

<!-- 链接到外部 CSS 文件 -->
<link rel="stylesheet" href="styles.css" />

<!-- 用于添加文档内的 CSS -->
<style>
  /* ... */
</style>

<!-- JavaScript & 无 JavaScript 标签 -->
<script src="script.js"></script>
<script>
  // 函数在这里
</script>
<noscript>
  <!-- 无 JS 替代 -->
</noscript>
```

**[⬆ 返回顶部](#目录)**

## Meta 标签

```html
<!--
  下面的 2 个 meta 标签 *必须* 在 <head> 中首先出现
  以确保正确的文档呈现。
  任何其他 head 元素应该在这些标签之后出现。
-->
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />

<!--
  允许控制资源从哪里加载。
  尽早放置在 <head> 中，因为该标签
  仅适用于在其之后声明的资源。
-->
<meta http-equiv="Content-Security-Policy" content="default-src 'self'" />

<!-- Web 应用程序的名称（仅在网站用作应用程序时使用） -->
<meta name="application-name" content="应用程序名称" />

<!-- Chrome、Firefox OS 和 Opera 的主题颜色 -->
<meta name="theme-color" content="#4285f4" />

<!-- 文档的简短描述（限制为 150 个字符） -->
<!-- 此内容 *可能* 用作搜索引擎结果的一部分。 -->
<meta name="description" content="页面描述" />

<!-- 控制搜索引擎的爬取和索引行为 -->
<meta name="robots" content="index,follow" /><!-- 所有搜索引擎 -->
<meta name="googlebot" content="index,follow" /><!-- 仅适用于 Google -->

<!-- 告诉 Google 不显示站点链接搜索框 -->
<meta name="google" content="nositelinkssearchbox" />

<!-- 告诉 Google 不为此文档提供翻译 -->
<meta name="google" content="notranslate" />

<!-- 验证网站所有权 -->
<meta
  name="google-site-verification"
  content="verification_token"
/><!-- Google Search Console -->
<meta
  name="yandex-verification"
  content="verification_token"
/><!-- Yandex Webmasters -->
<meta
  name="msvalidate.01"
  content="verification_token"
/><!-- Bing Webmaster Center -->
<meta name="alexaVerifyID" content="verification_token" /><!-- Alexa Console -->
<meta
  name="p:domain_verify"
  content="code_from_pinterest"
/><!-- Pinterest Console-->
<meta
  name="norton-safeweb-site-verification"
  content="norton_code"
/><!-- Norton Safe Web -->

<!-- 识别用于构建文档的软件（例如 - WordPress、Dreamweaver） -->
<meta name="generator" content="program" />

<!-- 文档主题的简短描述 -->
<meta name="subject" content="文档主题" />

<!-- 根据文档内容给出一般年龄评级 -->
<meta name="rating" content="General" />

<!-- 允许控制如何传递引荐者信息 -->
<meta name="referrer" content="no-referrer" />

<!-- 禁用自动检测和格式化可能的电话号码 -->
<meta name="format-detection" content="telephone=no" />

<!-- 通过设置为 "off" 完全取消 DNS 预取 -->
<meta http-equiv="x-dns-prefetch-control" content="off" />

<!-- 指定文档出现在特定框架中 -->
<meta http-equiv="Window-Target" content="_value" />

<!-- 地理标签 -->
<meta name="ICBM" content="纬度, 经度" />
<meta name="geo.position" content="纬度;经度" />
<meta
  name="geo.region"
  content="国家[-州]"
/><!-- 国家代码（ISO 3166-1）：必需，州代码（ISO 3166-2）：可选；例如 content="US" / content="US-NY" -->
<meta
  name="geo.placename"
  content="城市/镇"
/><!-- 例如 content="New York City" -->

<!-- Web Monetization https://webmonetization.org/docs/getting-started -->
<meta name="monetization" content="$paymentpointer.example" />
```

- 📖 [Google 理解的 Meta 标签](https://support.google.com/webmasters/answer/79812?hl=en)
- 📖 [WHATWG Wiki: MetaExtensions](https://wiki.whatwg.org/wiki/MetaExtensions)
- 📖 [维基百科上的 ICBM](https://en.wikipedia.org/wiki/ICBM_address#Modern_use)
- 📖 [维基百科上的 Geotagging](https://en.wikipedia.org/wiki/Geotagging#HTML_pages)

**[⬆ 返回顶部](#目录)**

## 链接

```html
<!-- 指向外部样式表 -->
<link rel="stylesheet" href="https://example.com/styles.css" />

<!-- 有助于防止出现内容重复的问题 -->
<link rel="canonical" href="https://example.com/article/?page=2" />

<!-- 链接到当前文档的 AMP HTML 版本 -->
<link rel="amphtml" href="https://example.com/path/to/amp-version.html" />

<!-- 链接到指定 Web 应用程序的“安装”凭据的 JSON 文件 -->
<link rel="manifest" href="manifest.json" />

<!-- 链接到文档的作者信息 -->
<link rel="author" href="humans.txt" />

<!-- 引用适用于链接上下文的版权声明 -->
<link rel="license" href="copyright.html" />

<!-- 指向文档中可能使用其他语言的位置 -->
<link rel="alternate" href="https://es.example.com/" hreflang="es" />

<!-- 提供有关作者或其他人的信息 -->
<link rel="me" href="https://google.com/profiles/thenextweb" type="text/html" />
<link rel="me" href="mailto:name@example.com" />
<link rel="me" href="sms:+15035550125" />

<!-- 链接到描述历史兴趣记录、文档或其他资料的集合的文档 -->
<link rel="archives" href="https://example.com/archives/" />

<!-- 在层次结构中链接到顶级资源 -->
<link rel="index" href="https://example.com/article/" />

<!-- 提供自引用 - 在文档有多个可能引用时非常有用 -->
<link
  rel="self"
  type="application/atom+xml"
  href="https://example.com/atom.xml"
/>

<!-- 系列文档中的第一个、最后一个、上一个和下一个文档 -->
<link rel="first" href="https://example.com/article/" />
<link rel="last" href="https://example.com/article/?page=42" />
<link rel="prev" href="https://example.com/article/?page=1" />
<link rel="next" href="https://example.com/article/?page=3" />

<!-- 当第三方服务用于维护博客时使用 -->
<link
  rel="EditURI"
  href="https://example.com/xmlrpc.php?rsd"
  type="application/rsd+xml"
  title="RSD"
/>

<!-- 当另一个 WordPress 博客链接到您的 WordPress 博客或帖子时，形成自动评论 -->
<link rel="pingback" href="https://example.com/xmlrpc.php" />

<!-- 在您在文档中链接到 URL 时通知一个 URL -->
<link rel="webmention" href="https://example.com/webmention" />

<!-- 使用 Micropub 客户端在自己的域中发布 -->
<link rel="micropub" href="https://example.com/micropub" />

<!-- Open Search -->
<link
  rel="search"
  href="/open-search.xml"
  type="application/opensearchdescription+xml"
  title="Search Title"
/>

<!-- 源 -->
<link
  rel="alternate"
  href="https://feeds.feedburner.com/example"
  type="application/rss+xml"
  title="RSS"
/>
<link
  rel="alternate"
  href="https://example.com/feed.atom"
  type="application/atom+xml"
  title="Atom 0.3"
/>

<!-- 预取、预加载、预浏览 -->
<!-- 更多信息：https://css-tricks.com/prefetching-preloading-prebrowsing/ -->
<link rel="dns-prefetch" href="//example.com/" />
<link rel="preconnect" href="https://www.example.com/" />
<link rel="prefetch" href="https://www.example.com/" />
<link rel="prerender" href="https://example.com/" />
<link rel="preload" href="image.png" as="image" />
```

- 📖 [链接关系](https://www.iana.org/assignments/link-relations/link-relations.xhtml)

**[⬆ 返回顶部](#目录)**

## 网站图标

```html
<!-- 适用于 IE 10 及以下 -->
<!-- 将 favicon.ico 放在根目录中 - 无需标签 -->

<!-- 用于我们需要的最高分辨率的图标 -->
<link rel="icon" sizes="192x192" href="/path/to/icon.png" />

<!-- Apple 触摸图标（重用 192px icon.png） -->
<link rel="apple-touch-icon" href="/path/to/apple-touch-icon.png" />

<!-- Safari 固定标签图标 -->
<link rel="mask-icon" href="/path/to/icon.svg" color="blue" />
```

- 📖 [所有关于网站图标（和触摸图标）的信息](https://bitsofco.de/all-about-favicons-and-touch-icons/)
- 📖 [创建固定标签图标](https://developer.apple.com/library/content/documentation/AppleApplications/Reference/SafariWebContent/pinnedTabs/pinnedTabs.html)
- 📖 [网站图标对照表](https://github.com/audreyr/favicon-cheat-sheet)
- 📖 [图标和浏览器颜色](https://developers.google.com/web/fundamentals/design-and-ux/browser-customization/)

**[⬆ 返回顶部](#目录)**

## 社交

### Facebook Open Graph

> 大多数内容在 Facebook 上作为 URL 共享，因此重要的是使用 Open Graph 标记对网站进行标记，以控制内容在 Facebook 上的呈现方式。[有关 Facebook Open Graph 标记的更多信息](https://developers.facebook.com/docs/sharing/webmasters#markup)

```html
<meta property="fb:app_id" content="123456789" />
<meta property="og:url" content="https://example.com/page.html" />
<meta property="og:type" content="website" />
<meta property="og:title" content="内容标题" />
<meta property="og:image" content="https://example.com/image.jpg" />
<meta property="og:image:alt" content="图像中的描述（不是标题）" />
<meta property="og:description" content="描述内容" />
<meta property="og:site_name" content="网站名称" />
<meta property="og:locale" content="en_US" />
<meta property="article:author" content="" />
```

- 📖 [Open Graph 协议](http://ogp.me/)
- 🛠 使用 [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/) 测试您的页面

### Twitter Card

> 使用 Twitter Cards，您可以将丰富的照片、视频和媒体体验附加到推文中，帮助驱动流量到您的网站。[有关 Twitter Cards 的更多信息](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/abouts-cards)

```html
<meta name="twitter:card" content="summary" />
<meta name="twitter:site" content="@site_account" />
<meta name="twitter:creator" content="@individual_account" />
<meta name="twitter:url" content="https://example.com/page.html" />
<meta name="twitter:title" content="内容标题" />
<meta name="twitter:description" content="内容描述少于 200 个字符" />
<meta name="twitter:image" content="https://example.com/image.jpg" />
<meta
  name="twitter:image:alt"
  content="对图像的文本描述，传达图像的基本特性给视力受损的用户。最多 420 个字符。"
/>
```

- 📖 [开始使用卡片 — Twitter Developers](https://dev.twitter.com/cards/getting-started)
- 🛠 使用 [Twitter Card 验证器](https://cards-dev.twitter.com/validator) 测试您的页面

### Twitter Privacy

如果在您的网站中嵌入推文，Twitter 可以使用您网站的信息来为 Twitter 用户定制内容和建议。[有关 Twitter 隐私选项的更多信息](https://dev.twitter.com/web/overview/privacy#what-privacy-options-do-website-publishers-have)。

```html
<!-- 禁止 Twitter 使用您网站的信息进行个性化目的 -->
<meta name="twitter:dnt" content="on" />
```

### Schema.org

```html
<html lang="" itemscope itemtype="https://schema.org/Article">
  <head>
    <link rel="author" href="" />
    <link rel="publisher" href="" />
    <meta itemprop="name" content="内容标题" />
    <meta itemprop="description" content="内容描述少于 200 个字符" />
    <meta itemprop="image" content="https://example.com/image.jpg" />
  </head>
</html>
```

**注意:** 这些 meta 标签需要在 `<html>` 中添加 `itemscope` 和 `itemtype` 属性。

- 📖 [开始使用 - schema.org](https://schema.org/docs/gs.html)
- 🛠 使用[富媒体搜索结果测试](https://search.google.com/test/rich-results)来测试您的页面

### Pinterest

Pinterest 允许您根据[他们的帮助中心](https://help.pinterest.com/en/business/article/prevent-saves-to-pinterest-from-your-site)阻止用户从您的网站保存内容。`description` 是可选的。

```html
<meta
  name="pinterest"
  content="nopin"
  description="对不起，您无法从我的网站保存！"
/>
```

### Facebook Instant Articles

```html
<meta charset="utf-8" />
<meta property="op:markup_version" content="v1.0" />

<!-- 文章的网页版本的URL -->
<link rel="canonical" href="https://example.com/article.html" />

<!-- 用于此文章的样式 -->
<meta property="fb:article_style" content="myarticlestyle" />
```

- 📖 [创建文章 - Instant Articles](https://developers.facebook.com/docs/instant-articles/guides/articlecreate)
- 📖 [代码示例 - Instant Articles](https://developers.facebook.com/docs/instant-articles/reference)

### OEmbed

```html
<link
  rel="alternate"
  type="application/json+oembed"
  href="https://example.com/services/oembed?url=http%3A%2F%2Fexample.com%2Ffoo%2F&amp;format=json"
  title="oEmbed Profile: JSON"
/>
<link
  rel="alternate"
  type="text/xml+oembed"
  href="https://example.com/services/oembed?url=http%3A%2F%2Fexample.com%2Ffoo%2F&amp;format=xml"
  title="oEmbed Profile: XML"
/>
```

- 📖 [oEmbed 格式](https://oembed.com/)

### QQ/微信

用户分享到 QQ 微信的网页将具有格式化的消息

```html
<meta itemprop="name" content="分享标题" />
<meta
  itemprop="image"
  content="http://imgcache.qq.com/qqshow/ac/v4/global/logo.png"
/>
<meta name="description" itemprop="description" content="分享内容" />
```

- 📖 [代码格式文档](http://open.mobile.qq.com/api/mqq/index#api:setShareInfo)

**[⬆ 返回顶部](#目录)**

## 浏览器/平台

### Apple iOS

```html
<!-- 智能应用横幅 -->
<meta
  name="apple-itunes-app"
  content="app-id=APP_ID,affiliate-data=AFFILIATE_ID,app-argument=SOME_TEXT"
/>

<!-- 禁用自动检测和格式化可能的电话号码 -->
<meta name="format-detection" content="telephone=no" />

<!-- 启动图标（180x180像素或更大） -->
<link rel="apple-touch-icon" href="/path/to/apple-touch-icon.png" />

<!-- 启动画面图像 -->
<link rel="apple-touch-startup-image" href="/path/to/launch.png" />

<!-- 启动图标标题 -->
<meta name="apple-mobile-web-app-title" content="App Title" />

<!-- 启用独立（全屏）模式 -->
<meta name="apple-mobile-web-app-capable" content="yes" />

<!-- 状态栏外观（除非启用独立模式，否则无效） -->
<meta name="apple-mobile-web-app-status-bar-style" content="black" />

<!-- iOS 应用程序深层链接 -->
<meta
  name="apple-itunes-app"
  content="app-id=APP-ID, app-argument=http/url-sample.com"
/>
<link rel="alternate" href="ios-app://APP-ID/http/url-sample.com" />
```

- 📖 [配置 Web 应用](https://developer.apple.com/library/content/documentation/AppleApplications/Reference/SafariWebContent/ConfiguringWebApplications/ConfiguringWebApplications.html)

### Google Android

```html
<meta name="theme-color" content="#E64545" />

<!-- 添加到主屏幕 -->
<meta name="mobile-web-app-capable" content="yes" />
<!-- 更多信息：https://developer.chrome.com/multidevice/android/installtohomescreen -->

<!-- Android 应用程序深层链接 -->
<meta name="google-play-app" content="app-id=package-name" />
<link rel="alternate" href="android-app://package-name/http/url-sample.com" />
```

### Google Chrome

```html
<link
  rel="chrome-webstore-item"
  href="https://chrome.google.com/webstore/detail/APP_ID"
/>

<!-- 禁用翻译提示 -->
<meta name="google" content="notranslate" />
```

### Microsoft Internet Explorer

```html
<!-- 强制IE 8/9/10使用其最新的渲染引擎 -->
<meta http-equiv="x-ua-compatible" content="ie=edge" />

<!-- 禁用 Skype 工具栏浏览器扩展自动检测和格式化可能的电话号码 -->
<meta name="skype_toolbar" content="skype_toolbar_parser_compatible" />

<!-- Windows 磁贴 -->
<meta name="msapplication-config" content="/browserconfig.xml" />
```

`browserconfig.xml`的最低要求的 xml 标记：

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

## 国内浏览器

### 360 浏览器

```html
<!-- 选择呈现引擎顺序 -->
<meta name="renderer" content="webkit|ie-comp|ie-stand" />
```

### QQ 移动浏览器

```html
<!-- 将屏幕锁定为指定方向 -->
<meta name="x5-orientation" content="landscape/portrait" />

<!-- 在全屏模式下显示此文档 -->
<meta name="x5-fullscreen" content="true" />

<!-- 文档将以“应用程序模式”（全屏等）显示 -->
<meta name="x5-page-mode" content="app" />
```

### UC 移动浏览器

```html
<!-- 将屏幕锁定为指定方向 -->
<meta name="screen-orientation" content="landscape/portrait" />

<!-- 在全屏模式下显示此文档 -->
<meta name="full-screen" content="yes" />

<!-- 即使在“文本模式”中，UC浏览器也将显示图像 -->
<meta name="imagemode" content="force" />

<!-- 文档将以“应用程序模式”（全屏，禁止手势等）显示 -->
<meta name="browsermode" content="application" />

<!-- 为此文档禁用UC浏览器的“夜间模式” -->
<meta name="nightmode" content="disable" />

<!-- 简化文档以减少数据传输 -->
<meta name="layoutmode" content="fitscreen" />

<!-- 禁用UC浏览器的“在文档中有很多文字时放大字体”功能 -->
<meta name="wap-font-scale" content="no" />
```

- 📖 [UC 浏览器文档](https://www.uc.cn/download/UCBrowser_U3_API.doc)

**[⬆ 返回顶部](#目录)**

## 应用链接

```html
<!-- iOS -->
<meta property="al:ios:url" content="applinks://docs" />
<meta property="al:ios:app_store_id" content="12345" />
<meta property="al:ios:app_name" content="App Links" />

<!-- Android -->
<meta property="al:android:url" content="applinks://docs" />
<meta property="al:android:app_name" content="App Links" />
<meta property="al:android:package" content="org.applinks" />

<!-- 页面回退 -->
<meta property="al:web:url" content="https://applinks.org/documentation" />
```

- 📖 [应用链接文档](https://developers.facebook.com/docs/applinks)

**[⬆ 返回顶部](#目录)**

## 其他资源

- 📖 [HTML5 样板文件文档：HTML](https://github.com/h5bp/html5-boilerplate/blob/master/dist/doc/html.md)
- 📖 [HTML5 样板文件文档：扩展和自定义](https://github.com/h5bp/html5-boilerplate/blob/master/dist/doc/extend.md)

**[⬆ 返回顶部](#目录)**

## 相关项目

- [Atom HTML Head Snippets](https://github.com/joshbuchea/atom-html-head-snippets) - 用于 `HEAD` 片段的 Atom 包
- [Sublime Text HTML Head Snippets](https://github.com/marcobiedermann/sublime-head-snippets) - 用于 `HEAD` 片段的 Sublime Text 包
- [head-it](https://github.com/hemanth/head-it) - 用于 `HEAD` 片段的 CLI 界面
- [vue-head](https://github.com/ktquez/vue-head) - 为 Vue.js 操纵 `HEAD` 标签的元信息

**[⬆ 返回顶部](#目录)**

## 其他格式

- 📄 [PDF](https://gitprint.com/Amery2010/HEAD/blob/master/README.md)

**[⬆ 返回顶部](#目录)**

## 🌐 翻译

- 🇮🇩 [Bahasa](https://github.com/rijdz/HEAD)
- 🇧🇷 [巴西葡萄牙语](https://github.com/Webschool-io/HEAD)
- 🇨🇳 [中文（简体）](https://github.com/Amery2010/HEAD)
- 🇩🇪 [德语](https://github.com/Shidigital/HEAD)
- 🇮🇹 [意大利语](https://github.com/Fakkio/HEAD)
- 🇯🇵 [日语](https://coliss.com/articles/build-websites/operation/work/collection-of-html-head-elements.html)
- 🇰🇷 [韩语](https://github.com/Lutece/HEAD)
- 🇷🇺 [俄语/Русский](https://github.com/Konfuze/HEAD)
- 🇪🇸 [西班牙语](https://github.com/alvaroadlf/HEAD)
- 🇹🇷 [土耳其语/Türkçe](https://github.com/mkg0/HEAD)

**[⬆ 返回顶部](#目录)**

## 🤝 贡献

**开启一个 issue 或一个 pull 请求来提出修改或补充。**

### 指南

**HEAD**存储库由两个分支组成：

#### 1. `master`

该分支包含在[htmlhead.u14.app](https://htmlhead.u14.app/)网站上反映的`README.md`文件。所有关于指南内容的更改应在此文件中进行。

请按照以下步骤进行拉取请求：

{:.list-style-default}

- 一次仅修改一个标记或一个相关的标记集
- 在属性上使用双引号
- 在自闭合元素中不要包含尾随斜杠 - HTML5 规范表示它们是可选的
- 考虑包含支持您更改的文档的链接

#### 2. `gh-pages`

该分支负责[htmlhead.u14.app](https://htmlhead.u14.app/)网站。我们使用[Jekyll](https://jekyllrb.com/)将`README.md`标记文件部署到[GitHub Pages](https://pages.github.com/)。所有与网站相关的修改应在此分支中进行。

在使用此分支之前，您可能会发现回顾[Jekyll 文档](https://jekyllrb.com/docs/home/)并了解 Jekyll 的工作方式会有所帮助。

### 部署到 Vercel

使用 Vercel 部署您自己的页面。

[![使用 Vercel 进行部署](https://vercel.com/button)](https://vercel.com/new/clone?s=https%3A%2F%2Fgithub.com%2FAmery2010%2FHEAD&hasTrialAvailable=1&showOptionalTeamCreation=false&project-name=HEAD&framework=jekyll&totalProjects=1&remainingProjects=1)

## 🌟 贡献者

查看所有超级棒的[贡献者](https://github.com/joshbuchea/HEAD/graphs/contributors) 🤩

## 👤 作者

**Josh Buchea**

- GitHub: [@joshbuchea](https://github.com/joshbuchea)
- Mastodon: [@joshbuchea@hachyderm.io](https://hachyderm.io/@joshbuchea)

### 翻译者

**[子丶言](https://github.com/Amery2010)**

## 💛 支持

如果这个项目对您或您的组织有帮助，请考虑直接支持我的工作：

- 💛 [在 GitHub 上赞助我](https://github.com/sponsors/joshbuchea)
- ⭐️ [在 GitHub 上给这个项目加星](https://github.com/joshbuchea/HEAD)
- 🐙 [在 GitHub 上关注我](https://github.com/joshbuchea)
- 🐘 [在 Mastodon 上关注我](https://hachyderm.io/@joshbuchea)

感谢所有给予帮助的人！🙏

## 📝 许可

[![CC0](https://i.creativecommons.org/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

**[⬆ 返回顶部](#目录)**
