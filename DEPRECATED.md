# ⚠️ 历史与兼容性 `<head>` 标签

> 本文收录曾出现在 [HEAD 指南](./README.md) 中的旧版平台专用标签、已停止服务的标签，以及已有替代方案的标签。

**这里的标签并非全部已被标准废弃。** 已停止服务或仅适用于旧版平台的内容保留作历史参考；对于仍受支持的兼容性标签，应根据目标浏览器和平台决定是否使用。

## 目录

- [Microsoft Internet Explorer](#microsoft-internet-explorer)
- [Apple Safari](#apple-safari)
- [Apple iOS](#apple-ios)
- [资源提示](#资源提示)
- [链接关系](#链接关系)
- [网站验证](#网站验证)
- [社交](#社交)
- [其他](#其他)

## Microsoft Internet Explorer

Microsoft 已于 [2022 年 6 月 15 日结束 Windows 10 上 IE 11 桌面应用的支持](https://learn.microsoft.com/en-us/lifecycle/announcements/internet-explorer-11-end-of-support-on-windows-10)。以下 IE 专用标签不适用于现代浏览器；只有在维护明确依赖旧版 IE 或 IE 模式的系统时才需要考虑它们。

```html
<!-- 强制 IE 8/9/10 使用可用的最新渲染引擎 -->
<meta http-equiv="x-ua-compatible" content="ie=edge">

<!-- 禁用 Skype 工具栏对可能的电话号码的自动识别与格式化 -->
<meta name="skype_toolbar" content="skype_toolbar_parser_compatible">

<!-- Windows 磁贴配置 -->
<meta name="msapplication-config" content="/browserconfig.xml">
```

`browserconfig.xml` 的最小 XML 示例：

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

Windows 11 的开始菜单已不再使用动态磁贴。新项目通常无需添加这类配置。

## Apple Safari

```html
<!-- Safari 固定标签页图标 -->
<link rel="mask-icon" href="/path/to/icon.svg" color="blue">
```

`mask-icon` 是 Safari 固定标签页使用的专用图标声明，并非通用网站图标的替代品。它属于平台兼容性配置，不能仅因主指南移除了该示例就断言所有 Safari 版本均不再支持。需要兼容该功能时，请参考 [Apple 的固定标签页图标文档](https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/CreatingPinnedTabIcons/CreatingPinnedTabIcons.html)；同时为其他浏览器提供 `rel="icon"`。

## Apple iOS

```html
<!-- Apple 专用的独立显示模式声明 -->
<meta name="apple-mobile-web-app-capable" content="yes">
```

Apple 在 [Safari 17.4 发布说明](https://developer.apple.com/documentation/safari-release-notes/safari-17_4-release-notes) 中建议改用 `mobile-web-app-capable`：

```html
<meta name="mobile-web-app-capable" content="yes">
```

对于 PWA，优先使用 [Web 应用清单](https://developer.mozilla.org/zh-CN/docs/Web/Progressive_web_apps/Manifest) 的 `display` 属性配置显示模式。旧标签可按目标 iOS 版本的兼容性需求保留。

## 资源提示

```html
<!-- 在后台预渲染整个页面 -->
<link rel="prerender" href="https://example.com/">
```

Chrome 已[移除旧的 `rel="prerender"` 实现](https://developer.chrome.com/blog/prerender-pages)。新项目可考虑 [Speculation Rules API（推测规则 API）](https://developer.mozilla.org/en-US/docs/Web/API/Speculation_Rules_API)，并检查目标浏览器的支持情况。

```html
<!-- 禁用浏览器的 DNS 预解析 -->
<meta http-equiv="x-dns-prefetch-control" content="off">
```

`x-dns-prefetch-control` 属于非标准的 DNS 预解析控制机制，支持情况因浏览器而异，不能保证跨浏览器生效。它与主动请求预解析的 `<link rel="dns-prefetch">` 用途不同；请参考 [MDN 文档](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/X-DNS-Prefetch-Control) 后按需使用。

## 链接关系

```html
<!-- 链接当前文档的 AMP HTML 版本 -->
<link rel="amphtml" href="https://example.com/path/to/amp-version.html">
```

Google 已在 2021 年[取消“焦点新闻”对 AMP 的要求](https://developers.google.com/search/blog/2021/04/more-details-page-experience)。这不等于 `amphtml` 链接关系失效；只有维护独立 AMP 页面时才需要此声明，普通页面无需为了搜索展示而新增 AMP 版本。

```html
<!-- 为支持 XML-RPC 的博客编辑器提供服务发现信息 -->
<link rel="EditURI" href="https://example.com/xmlrpc.php?rsd" type="application/rsd+xml" title="RSD">

<!-- 当其他 WordPress 博客链接本站时，支持自动发送引用通知 -->
<link rel="pingback" href="https://example.com/xmlrpc.php">
```

[RSD（Really Simple Discoverability）](https://en.wikipedia.org/wiki/Really_Simple_Discovery) 曾用于 Windows Live Writer 等 XML-RPC 博客编辑器。Pingback 可能被用于 DDoS 放大攻击，使用前应核对服务端的访问控制和 [WordPress 的相关设置](https://make.wordpress.org/core/2015/09/30/xml-rpc-settings-in-4-4/)。现代网站可考虑 [Webmention](https://www.w3.org/TR/webmention/)。

```html
<!-- 链接包含历史记录、文档或其他资料的集合 -->
<link rel="archives" href="https://example.com/archives/">

<!-- 链接层次结构中的顶层资源 -->
<link rel="index" href="https://example.com/article/">
```

这些历史链接关系不属于当前 HTML 标准中常用的链接类型，不应依赖它们产生特定浏览器行为。具体语义与适用范围请分别核对 [HTML 链接类型](https://html.spec.whatwg.org/multipage/links.html#linkTypes) 和 [IANA 链接关系注册表](https://www.iana.org/assignments/link-relations/link-relations.xhtml)。

## 网站验证

```html
<meta name="alexaVerifyID" content="verification_token"><!-- Alexa 控制台 -->
```

[Alexa Internet](https://en.wikipedia.org/wiki/Alexa_Internet) 是网站流量分析服务，与 Amazon Alexa 语音助手不同。该服务已于 2022 年 5 月 1 日关闭，因此此验证标签已无用途。

## 社交

### Twitter Card（可选的平台专用元数据）

```html
<meta name="twitter:card" content="summary">
<meta name="twitter:site" content="@site_account">
<meta name="twitter:creator" content="@individual_account">
<meta name="twitter:url" content="https://example.com/page.html">
<meta name="twitter:title" content="内容标题">
<meta name="twitter:description" content="内容描述（少于 200 个字符）">
<meta name="twitter:image" content="https://example.com/image.jpg">
<meta name="twitter:image:alt" content="向无法查看图片的用户传达图片主要内容的替代文本，最多 420 个字符。">
```

X（原 Twitter）可对部分字段回退使用 [Open Graph](./README.md#open-graph) 元数据，但这并不意味着所有 `twitter:*` 标签均已废弃，或两套标签能完全互换。需要指定卡片类型、账号署名或为 X 单独定制展示时，仍可保留 Twitter Card 标签。请参考 [X 的卡片标记参考](https://developer.x.com/en/docs/x-for-websites/cards/overview/markup)。

### Twitter 隐私选项

```html
<!-- 请求 Twitter 不将网站信息用于个性化推荐 -->
<meta name="twitter:dnt" content="on">
```

这是 Twitter 历史上的“请勿跟踪”声明。不要将它视为可靠的隐私控制，也不要依赖它阻止第三方脚本收集数据；应根据当前嵌入组件的行为和配置处理隐私要求。

### Facebook 应用标识

```html
<meta property="fb:app_id" content="123456789">
```

`fb:app_id` 是 Facebook 的平台专用标识，并非所有 Open Graph 消费者都需要。是否设置应根据 Facebook 应用及分析功能的实际需求，核对 [Meta 分享文档](https://developers.facebook.com/docs/sharing/webmasters/)，而不是将其视为通用 Open Graph 必填项。

### Facebook Instant Articles

```html
<meta charset="utf-8">
<meta property="op:markup_version" content="v1.0">

<!-- 文章的网页版本 URL -->
<link rel="canonical" href="https://example.com/article.html">

<!-- Instant Articles 使用的页面样式名称 -->
<meta property="fb:article_style" content="myarticlestyle">
```

这是旧版 Facebook Instant Articles 的专用标签；该产品已停止支持，不应在新项目中使用。保留此示例便于维护旧内容时识别其用途。

## 其他

```html
<!-- 指定文档显示的目标框架 -->
<meta http-equiv="Window-Target" content="_value">
```

`Window-Target` 是 IE 时代的非标准扩展，现代浏览器不支持这种用法。不要依赖它控制页面的打开位置。
