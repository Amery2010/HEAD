# 🤯 HEAD

> HTML `<head>` 元素的简单指南

[![贡献者](https://img.shields.io/github/contributors/joshbuchea/head.svg?style=for-the-badge)](https://github.com/joshbuchea/HEAD/graphs/contributors)
[![CC0](https://img.shields.io/badge/license-CC0-green.svg?style=for-the-badge)](https://creativecommons.org/publicdomain/zero/1.0/)
[![在 Mastodon 上关注 @joshbuchea](https://img.shields.io/badge/Follow_@joshbuchea-purple?logo=mastodon&logoColor=white&style=for-the-badge)](https://hachyderm.io/@joshbuchea)

## 目录

- [最小推荐](#最小推荐)
- [网页元素](#网页元素)
- [推荐排列顺序](#推荐排列顺序)
- [Meta 标签](#meta-标签)
- [链接](#链接)
- [脚本](#脚本)
- [网站图标](#网站图标)
- [社交](#社交)
  - [Open Graph](#open-graph)
  - [Schema.org](#schemaorg)
  - [Google JSON-LD 结构化数据](#google-json-ld-结构化数据)
  - [Pinterest](#pinterest)
  - [OEmbed](#oembed)
  - [QQ/微信](#qq微信)
  - [Dublin Core](#dublin-core)
  - [联邦宇宙（Fediverse）](#联邦宇宙fediverse)
- [浏览器与平台](#浏览器与平台)
  - [Apple iOS](#apple-ios)
  - [Google Android](#google-android)
  - [Google Chrome](#google-chrome)
- [国内浏览器](#国内浏览器)
  - [360 浏览器](#360-浏览器)
  - [QQ 移动浏览器](#qq-移动浏览器)
  - [UC 移动浏览器](#uc-移动浏览器)
- [应用链接](#应用链接)
- [历史与兼容性标签](#历史与兼容性标签)
- [其他资源](#其他资源)
- [相关项目](#相关项目)
- [翻译](#-翻译)
- [贡献](#-贡献)
  - [指南](#指南)
  - [本地预览](#本地预览)
  - [部署到 Vercel](#部署到-vercel)
  - [上游同步](#上游同步)
- [贡献者](#-贡献者)
- [作者](#-作者)
  - [译者](#译者)
- [支持](#-支持)
- [许可](#-许可)

## 最小推荐

以下是网页文档（网站或应用程序）必需的基本元素：

```html
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<!--
  上述两个 meta 标签应尽早出现在 <head> 中，以确保文档正确渲染。
  其他 head 元素应放在这两个标签之后。
-->
<title>页面标题</title>
```

`meta charset` — 定义文档的字符编码，通常使用 `utf-8`。

`meta name="viewport"` — 设置视口，影响移动端的响应式布局。

`width=device-width` — 将视口宽度设为设备宽度（以 CSS 像素计），适合移动端布局。

`initial-scale=1` — 设置初始缩放比例，`1` 表示不缩放。

## 网页元素

`<head>` 中可使用的元素包括 `meta`、`link`、`title`、`style`、`script`、`noscript` 和 `base`。

这些元素提供文档信息，帮助浏览器、搜索引擎和爬虫等理解、处理及渲染页面。

```html
<!--
  设置文档的字符编码，确保 UTF-8 字符（例如表情符号）正确显示。
-->
<meta charset="utf-8">

<!-- 设置文档标题 -->
<title>页面标题</title>

<!-- 设置文档中所有相对 URL 的基准 URL -->
<base href="https://example.com/page.html">

<!-- 链接外部 CSS 文件 -->
<link rel="stylesheet" href="styles.css">

<!-- 添加文档内的 CSS -->
<style>
  /* ... */
</style>

<!-- JavaScript 与禁用 JavaScript 时的替代内容 -->
<script src="script.js"></script>
<script>
  // 在此编写函数
</script>
<noscript>
  <!-- 禁用 JavaScript 时显示的替代内容 -->
</noscript>
```

## 推荐排列顺序

为了兼顾性能与文档的正确渲染，建议按以下顺序排列 `<head>` 中的元素。除字符编码的位置要求外，这不是强制顺序；若通过 `<meta>` 设置内容安全策略（CSP），应将它放在需要受该策略约束的资源之前。

1. `<meta charset>` — 字符编码声明；**必须**完整出现在文档的前 1024 字节内
2. `<meta name="viewport">` — 视口设置；尽早声明，以保证响应式布局正确渲染
3. `<title>` — 文档标题；放在编码和视口设置之后，减少可能的重新渲染
4. 其他 `<meta>` 标签（如 description、robots）
5. Open Graph 等社交元数据标签
6. `<link rel="canonical">` 及其他 `<link>` 标签（不含样式表与资源提示）
7. `<link rel="preconnect">` / `<link rel="dns-prefetch">` — 资源提示；尽早声明，充分利用提前建立连接的机会
8. `<link rel="stylesheet">` — 外部 CSS；样式表应放在脚本之前
9. `<link rel="icon">` — 网站图标
10. `<script>` — 脚本；尽可能使用 `defer` 或 `async`，避免阻塞页面渲染

```html
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">

  <title>页面标题</title>

  <meta name="description" content="页面描述">
  <!-- 其他元数据标签 -->

  <!-- Open Graph 等社交元数据标签 -->
  <meta property="og:title" content="页面标题">
  <!-- 其他社交元数据标签 -->

  <link rel="canonical" href="https://example.com/page.html">
  <!-- 其他链接标签（不含样式表与资源提示） -->

  <link rel="preconnect" href="https://example.com">
  <link rel="dns-prefetch" href="https://example.com">

  <link rel="stylesheet" href="styles.css">

  <link rel="icon" href="favicon.ico">

  <script defer src="script.js"></script>
</head>
```

## Meta 标签

```html
<!--
  以下两个 meta 标签应尽早出现在 <head> 中，以确保文档正确渲染。
  其他 head 元素应放在这两个标签之后。
-->
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">

<!--
  控制资源允许加载的来源。
  应尽早放在 <head> 中，因为该标签仅影响其后声明的资源。
-->
<meta http-equiv="Content-Security-Policy" content="default-src 'self'">

<!-- Web 应用程序名称（仅在网站作为应用程序使用时设置） -->
<meta name="application-name" content="应用程序名称">

<!-- Chrome、Firefox OS 和 Opera 使用的主题色 -->
<meta name="theme-color" content="#4285f4">

<!-- 声明页面支持的配色方案（浅色、深色或两者） -->
<meta name="color-scheme" content="light dark">

<!-- 文档的简短描述（建议控制在 150 个字符以内） -->
<!-- 这段内容可能出现在搜索结果摘要中。 -->
<meta name="description" content="页面描述">

<!-- 控制搜索引擎的抓取和索引行为 -->
<meta name="robots" content="index,follow"><!-- 所有搜索引擎 -->
<meta name="googlebot" content="index,follow"><!-- 仅 Google -->

<!-- 告诉 Google 不显示站点链接搜索框（Google 已停止展示此功能） -->
<meta name="google" content="nositelinkssearchbox">

<!-- 告诉 Google 不为此文档提供翻译 -->
<meta name="google" content="notranslate">

<!-- 验证网站所有权 -->
<meta name="google-site-verification" content="verification_token"><!-- Google Search Console -->
<meta name="yandex-verification" content="verification_token"><!-- Yandex Webmasters -->
<meta name="msvalidate.01" content="verification_token"><!-- Bing Webmaster Center -->
<meta name="p:domain_verify" content="code_from_pinterest"><!-- Pinterest Console-->
<meta name="norton-safeweb-site-verification" content="norton_code"><!-- Norton Safe Web -->

<!-- 标识生成文档的软件（例如 WordPress、Dreamweaver） -->
<meta name="generator" content="program">

<!-- 文档主题的简短描述 -->
<meta name="subject" content="文档主题">

<!-- 根据文档内容提供一般年龄分级 -->
<meta name="rating" content="General">

<!-- 控制如何传递来源页面信息（Referer） -->
<meta name="referrer" content="no-referrer">

<!-- 禁用对可能的电话号码的自动识别与格式化 -->
<meta name="format-detection" content="telephone=no">

<!-- 地理位置标签 -->
<meta name="ICBM" content="纬度, 经度"><!-- 地理坐标（纬度、经度），以十进制度数表示；例如 content="48.8566, 2.3522" -->
<meta name="geo.position" content="纬度;经度"><!-- 地理坐标；纬度与经度用分号分隔 -->
<meta name="geo.region" content="国家[-地区]"><!-- 国家代码（ISO 3166-1）必填，地区代码（ISO 3166-2）可选；例如 content="US" / content="US-NY" -->
<meta name="geo.placename" content="城市/城镇"><!-- 例如 content="New York City" -->

<!-- Web Monetization（Web 变现） https://webmonetization.org/docs/getting-started -->
<meta name="monetization" content="$paymentpointer.example">
```

**注意：** 浏览器不会直接利用这些地理位置标签。它们用于帮助搜索引擎、爬虫和基于位置的服务理解页面内容与地理位置的关系。`ICBM`（名称源自 ICBM 地址约定）和 `geo.position` 都使用十进制度数表示坐标；前者用逗号分隔，后者用分号分隔。`geo.region` 使用 ISO 代码标识国家及可选地区，`geo.placename` 则提供便于阅读的地名。

- 📖 [Google 支持的 Meta 标签](https://developers.google.com/search/docs/crawling-indexing/special-tags?hl=zh-cn)
- 📖 [WHATWG Wiki: MetaExtensions](https://wiki.whatwg.org/wiki/MetaExtensions)
- 📖 [维基百科：ICBM 地址](https://en.wikipedia.org/wiki/ICBM_address#Modern_use)
- 📖 [维基百科：地理标记](https://en.wikipedia.org/wiki/Geotagging#HTML_pages)

## 链接

```html
<!-- 链接外部样式表 -->
<link rel="stylesheet" href="https://example.com/styles.css">

<!-- 指定规范 URL，帮助避免重复内容问题 -->
<link rel="canonical" href="https://example.com/article/?page=2">

<!-- 链接 Web 应用清单，推荐用它定义 PWA 的名称、图标、主题色和显示模式等元数据 -->
<link rel="manifest" href="manifest.json">

<!-- 链接文档作者的信息 -->
<link rel="author" href="humans.txt">

<!-- 链接适用于当前文档的版权或许可声明 -->
<link rel="license" href="copyright.html">

<!-- 链接文档的其他语言版本 -->
<link rel="alternate" href="https://es.example.com/" hreflang="es">

<!-- 提供作者或其他人的身份信息。
     可用于分布式身份验证方式 RelMeAuth。
     详见 https://microformats.org/wiki/RelMeAuth -->
<link rel="me" href="https://google.com/profiles/thenextweb" type="text/html">
<link rel="me" href="mailto:name@example.com">
<link rel="me" href="sms:+15035550125">

<!-- 提供指向自身的引用，适合存在多个引用地址的文档 -->
<link rel="self" type="application/atom+xml" href="https://example.com/atom.xml">

<!-- 分别链接系列文档中的上一篇和下一篇 -->
<link rel="prev" href="https://example.com/article/?page=1">
<link rel="next" href="https://example.com/article/?page=3">

<!-- 当文档链接到其他页面时，可通过 Webmention 通知对方。
     详见 https://webmention.net -->
<link rel="webmention" href="https://example.com/webmention">

<!-- 允许使用 Micropub 客户端向自己的域名发布内容。
     详见 https://indieweb.org/Micropub -->
<link rel="micropub" href="https://example.com/micropub">

<!-- 为网站配置 IndieAuth，以自己的域名进行身份验证。
     详见 https://indieauth.net。 -->
<link rel="token_endpoint" href="https://example.com/token">
<link rel="authorization_endpoint" href="https://example.com/auth">

<!-- OpenSearch 搜索描述 -->
<link rel="search" href="/open-search.xml" type="application/opensearchdescription+xml" title="搜索标题">

<!-- 订阅源 -->
<link rel="alternate" href="https://feeds.feedburner.com/example" type="application/rss+xml" title="RSS">
<link rel="alternate" href="https://example.com/feed.atom" type="application/atom+xml" title="Atom 0.3">

<!-- DNS 预解析、预连接、预取与预加载 -->
<!-- 详见： https://css-tricks.com/prefetching-preloading-prebrowsing/ -->
<link rel="dns-prefetch" href="//example.com/">
<link rel="preconnect" href="https://www.example.com/">
<link rel="prefetch" href="https://www.example.com/">

<link rel="preload" href="image.png" as="image">
```

**注意：** 推荐使用 [Web 应用清单](https://developer.mozilla.org/zh-CN/docs/Web/Progressive_web_apps/Manifest)（`manifest.json`），在一个文件中跨平台声明可安装 Web 应用的属性，包括 `name`、`icons`、`theme_color` 和 `display`，减少对各平台专用 `<meta>` 标签的依赖。

- 📖 [链接关系](https://www.iana.org/assignments/link-relations/link-relations.xhtml)
- 📖 [Web 应用清单（MDN）](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Manifest)

## 脚本

```html
<!--
  对于普通脚本，可在适当情况下将 <script> 放在 <body> 末尾。
  放在 <head> 中时，以下属性可控制加载与执行行为：
-->

<!-- 阻塞 HTML 解析，直到脚本下载并执行完成 -->
<script src="script.js"></script>

<!-- 与 HTML 解析并行下载，下载完成后尽快执行；执行时可能中断解析 -->
<script async src="script.js"></script>

<!-- 与 HTML 解析并行下载，在文档解析完成后按顺序执行 -->
<script defer src="script.js"></script>

<!-- 对于经典外部脚本，现代浏览器优先采用 async；defer 为不支持 async 的旧浏览器提供回退 -->
<script async defer src="script.js"></script>

<!-- 内联脚本 -->
<script>
  // 在此编写函数
</script>

<!-- 子资源完整性（SRI）：通过 integrity 校验下载内容，防止资源被意外篡改；这里的哈希仅为示例 -->
<script src="https://example.com/script.js" integrity="sha384-oqVuAfXRKap7fdgcCY5uykM6+R9GqQ8K/uxy9rx7HNQlGYl1kPzQho1wx4JwY8wC"></script>
```

**注意：** 以上加载顺序说明针对经典外部脚本。`defer` 不影响没有 `src` 的经典内联脚本；`type="module"` 脚本默认延后执行。使用跨域 SRI 校验时，资源服务器还需要支持 CORS，通常应配合 `crossorigin="anonymous"`。

- 📖 [async 与 defer 属性的区别](https://www.growingwiththeweb.com/2014/02/async-vs-defer-attributes.html)
- 📖 [子资源完整性（SRI）](https://developer.mozilla.org/en-US/docs/Web/Security/Defenses/Subresource_Integrity)

## 网站图标

```html
<!-- 对于 IE 10 及更早版本 -->
<!-- 将 favicon.ico 放在根目录，无需额外标签 -->

<!-- 提供所需最高分辨率的网站图标 -->
<link rel="icon" sizes="192x192" href="/path/to/icon.png">

<!-- Apple 触摸图标（可复用 192px 的 icon.png） -->
<link rel="apple-touch-icon" href="/path/to/apple-touch-icon.png">
```

- 📖 [网站图标与触摸图标详解](https://bitsofco.de/all-about-favicons-and-touch-icons/)
- 📖 [网站图标速查表](https://github.com/audreyfeldroy/favicon-cheat-sheet)
- 📖 [图标与浏览器颜色](https://web.dev/articles/icons-and-browser-colors)

## 社交

### Open Graph

> [Open Graph 协议](https://ogp.me/) 是控制内容在社交平台分享时如何呈现的事实标准。它最初由 Facebook 创建，如今已被 LinkedIn、X（缺少 Twitter Card 标签时可作为回退）、Discord、Slack、iMessage、Mastodon、Bluesky 和 WhatsApp 等主要平台使用。

```html
<meta property="og:url" content="https://example.com/page.html">
<meta property="og:type" content="website">
<meta property="og:title" content="内容标题">
<meta property="og:image" content="https://example.com/image.jpg">
<meta property="og:image:alt" content="描述图片内容的替代文本（不是图片标题）">
<meta property="og:description" content="内容描述">
<meta property="og:site_name" content="网站名称">
<meta property="og:locale" content="zh_CN">
<meta property="article:author" content="">
```

- 📖 [Open Graph 协议](https://ogp.me/)
- 🛠 使用 [Facebook 分享调试器](https://developers.facebook.com/tools/debug/) 或 [LinkedIn 帖子检查器](https://www.linkedin.com/post-inspector/) 检查页面。

### Schema.org

```html
<html lang="zh-CN" itemscope itemtype="https://schema.org/Article">
    <head>
      <link rel="author" href="">
      <link rel="publisher" href="">
      <meta itemprop="name" content="内容标题">
      <meta itemprop="description" content="内容描述（少于 200 个字符）">
      <meta itemprop="image" content="https://example.com/image.jpg">
    </head>
    <body>
      <!-- 文章内容 -->
    </body>
</html>
```

**注意：** 这些元数据标签需要配合 `<html>` 上的 `itemscope` 和 `itemtype` 属性使用。

- 📖 [schema.org 入门](https://schema.org/docs/gs.html)
- 🛠 使用 [富媒体搜索结果测试](https://search.google.com/test/rich-results) 检查页面。

### Google JSON-LD 结构化数据

以下 JSON-LD 示例描述一个组织，可帮助 Google 理解网站所代表的实体，并支持知识图谱等搜索展示（例如搜索结果右侧常见的品牌信息面板）。添加结构化数据并不保证一定出现这种展示：

```html
<script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "Organization",
    "name": "yourbrand.com",
    "url": "https://www.yourbrand.com/",
    "logo": "https://www.yourbrand.com/logo.png",
    "sameAs": [
      "https://www.facebook.com/yourbrand",
      "https://twitter.com/yourbrand",
      "https://uk.pinterest.com/yourbrand/",
      "https://www.instagram.com/yourbrand/",
      "https://www.linkedin.com/company/yourbrand-com"
    ]
  }
</script>
```

### Pinterest

根据 [Pinterest 帮助中心](https://help.pinterest.com/en/business/article/prevent-saves-to-pinterest-from-your-site)，可使用以下标签阻止用户将网站内容保存到 Pinterest。`description` 属性可选。

```html
<meta name="pinterest" content="nopin" description="抱歉，无法从本网站保存内容！">
```

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

这些元数据可用于设置网页分享到 QQ 或微信时展示的标题、图片和描述。

```html
<meta itemprop="name" content="分享标题">
<meta itemprop="image" content="http://imgcache.qq.com/qqshow/ac/v4/global/logo.png">
<meta name="description" itemprop="description" content="分享内容">
```

- 📖 [代码格式文档](https://open.mobile.qq.com/api/mqq/index#api:setShareInfo)

### Dublin Core

[Dublin Core](https://www.dublincore.org/) 是由 Dublin Core 元数据倡议组织（DCMI）维护、以 [ISO 15836](https://www.iso.org/standard/71339.html) 标准化的元数据词汇表。它定义了用于描述资源的 15 个核心元素，广泛应用于数字图书馆、机构知识库、学术出版和政府门户。在 HTML 中使用时，先声明 DC 命名空间，再以带 `DC.` 前缀的 `<meta>` 标签添加所需元素。

```html
<!-- 声明 Dublin Core 命名空间 -->
<link rel="schema.DC" href="https://purl.org/dc/elements/1.1/">

<meta name="DC.title" content="页面标题">
<meta name="DC.creator" content="作者姓名">
<meta name="DC.subject" content="关键词;主题">
<meta name="DC.description" content="页面内容的简短描述">
<meta name="DC.publisher" content="发布者名称">
<meta name="DC.contributor" content="贡献者姓名">
<meta name="DC.date" content="YYYY-MM-DD">
<meta name="DC.type" content="Text">
<meta name="DC.format" content="text/html">
<meta name="DC.identifier" content="https://example.com/page.html">
<meta name="DC.source" content="https://example.com/original-source">
<meta name="DC.language" content="zh-CN">
<meta name="DC.relation" content="https://example.com/related">
<meta name="DC.coverage" content="空间或时间覆盖范围">
<meta name="DC.rights" content="版权所有者名称">
```

- 📖 [Dublin Core 元数据元素集](https://www.dublincore.org/specifications/dublin-core/dces/)
- 📖 [在 HTML 中使用 Dublin Core](https://www.dublincore.org/specifications/dublin-core/dcq-html/)

### 联邦宇宙（Fediverse）

Mastodon 等部分联邦宇宙软件允许通过元数据标签声明作者账号，并在网站链接预览中显示作者署名。除添加标签外，还需要在 Mastodon 的“设置 → 公开个人资料 → 验证 → 作者署名”中，将网站域名加入允许列表。

```html
<meta name="fediverse:creator" content="@handle@example.org">
```

## 浏览器与平台

### Apple iOS

```html
<!-- 智能应用横幅 -->
<meta name="apple-itunes-app" content="app-id=APP_ID,affiliate-data=AFFILIATE_ID,app-argument=SOME_TEXT">

<!-- 禁用对可能的电话号码的自动识别与格式化 -->
<meta name="format-detection" content="telephone=no">

<!-- 主屏幕图标（180 × 180px 或更大） -->
<link rel="apple-touch-icon" href="/path/to/apple-touch-icon.png">

<!-- 启动画面图片 -->
<link rel="apple-touch-startup-image" href="/path/to/launch.png">

<!-- 主屏幕图标标题 -->
<meta name="apple-mobile-web-app-title" content="应用标题">

<!-- 启用独立显示模式（不显示浏览器界面） -->
<meta name="mobile-web-app-capable" content="yes">

<!-- 状态栏样式（仅在独立显示模式下生效） -->
<meta name="apple-mobile-web-app-status-bar-style" content="black">

<!-- 适配刘海屏（iPhone X 及后续机型）；在现有 viewport 标签中添加 viewport-fit=cover -->
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">

<!-- iOS 应用深度链接 -->
<meta name="apple-itunes-app" content="app-id=APP-ID, app-argument=http/url-sample.com">
<link rel="alternate" href="ios-app://APP-ID/http/url-sample.com">
```

- 📖 [配置 Web 应用](https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/SafariWebContent/ConfiguringWebApplications/ConfiguringWebApplications.html)

**注意：** 对于渐进式 Web 应用（PWA），推荐使用 [Web 应用清单](https://developer.mozilla.org/zh-CN/docs/Web/Progressive_web_apps/Manifest)（`<link rel="manifest">`）跨平台配置应用名称、显示模式和图标。Apple 专用标签仍可作为兼容旧版 iOS 的回退；具体支持情况取决于浏览器和系统版本。

### Google Android

```html
<meta name="theme-color" content="#E64545">

<!-- 添加到主屏幕 -->
<meta name="mobile-web-app-capable" content="yes">
<!-- 详见： https://developer.chrome.com/multidevice/android/installtohomescreen -->

<!-- Android 应用深度链接 -->
<meta name="google-play-app" content="app-id=package-name">
<link rel="alternate" href="android-app://package-name/http/url-sample.com">
```

**注意：** 推荐通过 [Web 应用清单](https://developer.mozilla.org/zh-CN/docs/Web/Progressive_web_apps/Manifest) 配置应用的 `theme_color` 和独立显示模式。页面上的 `theme-color` 元数据仍有用途，例如设置当前页面的浏览器界面颜色，也可为不支持清单主题色的浏览器提供回退。

### Google Chrome

```html
<link rel="chrome-webstore-item" href="https://chrome.google.com/webstore/detail/APP_ID">

<!-- 禁用翻译提示 -->
<meta name="google" content="notranslate">
```

## 国内浏览器

### 360 浏览器

```html
<!-- 指定渲染引擎的优先顺序 -->
<meta name="renderer" content="webkit|ie-comp|ie-stand">
```

### QQ 移动浏览器

```html
<!-- 将屏幕锁定为指定方向 -->
<meta name="x5-orientation" content="landscape/portrait">

<!-- 以全屏方式显示文档 -->
<meta name="x5-fullscreen" content="true">

<!-- 以“应用模式”显示文档（全屏等） -->
<meta name="x5-page-mode" content="app">
```

### UC 移动浏览器

```html
<!-- 将屏幕锁定为指定方向 -->
<meta name="screen-orientation" content="landscape/portrait">

<!-- 以全屏方式显示文档 -->
<meta name="full-screen" content="yes">

<!-- 即使处于“文字模式”，UC 浏览器也显示图片 -->
<meta name="imagemode" content="force">

<!-- 以“应用模式”显示文档（全屏、禁用手势等） -->
<meta name="browsermode" content="application">

<!-- 禁用 UC 浏览器对此文档的“夜间模式” -->
<meta name="nightmode" content="disable">

<!-- 简化文档以减少数据传输 -->
<meta name="layoutmode" content="fitscreen">

<!-- 禁用 UC 浏览器在文档文字较多时自动放大字体的功能 -->
<meta name="wap-font-scale" content="no">
```

- 📖 [UC 浏览器文档](https://www.uc.cn/download/UCBrowser_U3_API.doc)

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

<!-- Web 回退地址 -->
<meta property="al:web:url" content="https://applinks.org/documentation">
```

- 📖 [应用链接](https://developers.facebook.com/docs/applinks)

## 历史与兼容性标签

对于旧版平台专用、已停止服务或已有替代方案的标签（例如 IE 兼容设置、Alexa 验证和 Twitter Card），请参阅 [历史与兼容性标签](./DEPRECATED.md)。其中部分标签仍受支持，并不意味着它们全部已被标准废弃。

## 其他资源

- 📖 [HTML5 Boilerplate 文档：HTML](https://github.com/h5bp/html5-boilerplate/blob/main/docs/html.md)
- 📖 [HTML5 Boilerplate 文档：扩展与定制](https://github.com/h5bp/html5-boilerplate/blob/main/docs/extend.md)

## 相关项目

- [Atom HTML Head Snippets](https://github.com/joshbuchea/atom-html-head-snippets) - 用于 `HEAD` 代码片段的 Atom 扩展
- [Sublime Text HTML Head Snippets](https://github.com/marcobiedermann/sublime-head-snippets) - 用于 `HEAD` 代码片段的 Sublime Text 扩展
- [head-it](https://github.com/hemanth/head-it) - 用于 `HEAD` 代码片段的命令行工具
- [vue-head](https://github.com/ktquez/vue-head) - 在 Vue.js 中管理 `<head>` 元数据

## 🌐 翻译

- [印度尼西亚语](https://github.com/rijdz/HEAD)
- [孟加拉语](https://github.com/AveyBD/HEAD)
- [巴西葡萄牙语](https://github.com/Webschool-io/HEAD)
- [中文（简体）](https://github.com/Amery2010/HEAD)
- [德语](https://github.com/Shidigital/HEAD)
- [意大利语](https://github.com/Fakkio/HEAD)
- [日语](https://coliss.com/articles/build-websites/operation/work/collection-of-html-head-elements.html)
- [韩语](https://github.com/Lutece/HEAD)
- [马来语](https://github.com/shoen1x/HEAD)
- [俄语 / Русский](https://github.com/Konfuze/HEAD)
- [西班牙语](https://github.com/alvaroadlf/HEAD)
- [土耳其语 / Türkçe](https://github.com/mkg0/HEAD)
- [乌克兰语](https://github.com/Shramkoweb/HEAD)

## 🤝 贡献

**欢迎通过 issue 或 pull request 提出修改或补充。**

### 指南

上游 **HEAD** 仓库的内容与网站分别维护在两个分支中：

#### 1. `master`

上游该分支包含 [htmlhead.dev](https://htmlhead.dev/) 使用的 `README.md`。指南内容的修改应在此文件中进行。本中文仓库的内容展示在 [htmlhead.u14.app](https://htmlhead.u14.app/)，请在当前 `master` 分支维护中文翻译。

提交 pull request 时，请遵循以下约定：

{:.list-style-default}

- 每次修改一个标签或一组相关标签
- 属性值使用双引号
- HTML 空元素不要添加末尾斜杠（XML 示例仍须遵循 XML 语法）
- 尽可能提供支持修改内容的文档链接

#### 2. `gh-pages`

上游该分支负责 [htmlhead.dev](https://htmlhead.dev/) 网站，使用 [Jekyll](https://jekyllrb.com/) 将 `README.md` 部署到 [GitHub Pages](https://pages.github.com/)。上游的网站相关修改在此分支进行。本中文仓库当前 `master` 分支也包含 Jekyll 站点文件；请根据本仓库实际部署方式修改。

修改网站前，建议先阅读 [Jekyll 文档](https://jekyllrb.com/docs/home/)，了解其工作方式。

### 本地预览

使用本仓库的 `Gemfile` 安装依赖后，在仓库根目录运行：

```sh
bundle install
bundle exec jekyll serve
```

随后在本地浏览器中打开 Jekyll 输出的地址。修改 `README.md` 后，Jekyll 会重新生成页面。

若使用 Ruby 3.3 且出现 Logger 的 `@level_override` 错误，可在本地依赖配置中固定 `logger` 为 `1.5.3`，并确保加载的是该版本。这是 Jekyll 4.2 与新版 Logger 的兼容问题，不是翻译内容导致的构建错误。

### 部署到 Vercel

可以通过 Vercel 部署自己的中文页面：

[![使用 Vercel 进行部署](https://vercel.com/button)](https://vercel.com/new/clone?s=https%3A%2F%2Fgithub.com%2FAmery2010%2FHEAD&hasTrialAvailable=1&showOptionalTeamCreation=false&project-name=HEAD&framework=jekyll&totalProjects=1&remainingProjects=1)

### 上游同步

本译文依据 [joshbuchea/HEAD](https://github.com/joshbuchea/HEAD) 的 [`de1304e`](https://github.com/joshbuchea/HEAD/commit/de1304eeb62feb6bec90c28fc78fe29d2500d606) 更新。同步时应同时检查 `README.md` 和 `DEPRECATED.md`，保留本仓库的中文站点配置与译者信息，并核对目录、示例和参考链接。涉及浏览器兼容性的结论应以对应平台的文档为准。

## 🌟 贡献者

查看所有优秀的上游[贡献者](https://github.com/joshbuchea/HEAD/graphs/contributors) 🤩

## 👤 作者

**Josh Buchea**

- GitHub: [@joshbuchea](https://github.com/joshbuchea)
- Mastodon: [@joshbuchea@hachyderm.io](https://hachyderm.io/@joshbuchea)

### 译者

**子丶言**

- GitHub：[@Amery2010](https://github.com/Amery2010)
- 网站：[xiangfa.org](https://xiangfa.org)

## 💛 支持

如果这个项目帮助到了你或你的组织，可以考虑支持原作者：

- 💛 [在 GitHub 上赞助作者](https://github.com/sponsors/joshbuchea)
- ⭐️ [在 GitHub 上为项目加星](https://github.com/joshbuchea/HEAD)
- 🐙 [在 GitHub 上关注作者](https://github.com/joshbuchea)
- 🐘 [在 Mastodon 上关注作者](https://hachyderm.io/@joshbuchea)

感谢每一份支持！🙏

— Josh

## 📝 许可

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)
