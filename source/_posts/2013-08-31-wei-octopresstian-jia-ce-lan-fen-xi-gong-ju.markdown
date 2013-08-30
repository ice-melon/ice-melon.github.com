---
layout: post
title: "为octopress添加侧栏分析工具"
date: 2013-08-31 01:18
comments: true
categories: 中文 博客建设
---
Ocotopress 已经集成了twitter，脸书等第三方分析链接，只要在_config.yml里配置能搞定。但墙内没人用这些啊，怎么才能高大上？不慎写了鸡汤文读者要分分钟分享到朋友圈才行，吟诗调侃了薛必群老财主读者能够转到weibo里。如果还有小众读者觉得博主写得好想分享到有道笔记等网站，博主也要贴心服务满足读者需求才行。

在[meditic](http://meditic.com/game-of-wild-beast/)的博客里发现了[jiathis](http://www.jiathis.com/)这个工具，很全面，里面还有你找不到的分享平台吗？话不多说过程如下。


首先嵌入jiathis的代码，修改`source/_include/post/sharing.html`，在最后一行的`</div>`前加入如下代码

    {% if site.jiathis %}
    <script type="text/javascript" src="http://v3.jiathis.com/code/jiathis_r.js?uid=1374762077227410&move=0" charset="utf-8"></script>
    {% endif %}

然后在_config.yml中添加jiathis，在文件末尾添加就可

	#jianthis
	jianthis:true

以后不想开分享只要改成false就可。

试了jiathis几种分析方式，只有这个能不改代码完美契合octopress的布局，而且分享图标也最为清爽，不建议再去jianthis网站定制。