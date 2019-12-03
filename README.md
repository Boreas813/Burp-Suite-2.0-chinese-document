# Burp Suite 2.0 测试版使用指南
![](https://portswigger.net/cms/images/42/58/6583feb8570a-article-burp2_-_article.png)

Burp Suite 2.0 测试版已经对专业人士开放。
这是一次重大更新，包括成吨的新特性，包括如下内容：

- 一个[新的爬虫](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Burp's%20new%20crawler.md)， [全自动session处理](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Automatic%20session%20handling.md), [侦测基于状态的应用](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Detecting%20changes%20in%20application%20state.md)，[使用多重登录状态爬取](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Crawling%20with%20multiple%20logins.md)， 和处理[不稳定的响应内容](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Crawling%20volatile%20content.md)

- 全新的扫描引擎，[自动session处理](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Automatically%20maintaining%20session%20during%20scans.md)， [多阶段扫描](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Multi-phase%20scanning.md)，[改良型已存储输入检测](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Improved%20detection%20of%20stored%20input.md)，[合并全站被动问题](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Consolidation%20of%20site-wide%20passive%20issues.md)， 高效处理[高频插入点](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Frequently%20occurring%20insertion%20points.md)， 以及优秀的[应用错误处理](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Handling%20application%20errors%20during%20scans.md)

- 全新的[动态JavaScript分析器](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Dynamic%20analysis%20of%20JavaScript.md)，大大改进了基于DOM的漏洞检测。

- 全新的[仪表盘](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/The%20new%20dashboard.md)用来监视和控制自动化进程。

- 全新的[扫描启动器](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Launching%20scans.md)，以及[多重并行扫描](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Multiple%20parallel%20scans.md)能力。

- 全新的[实时扫描？(live scanning)。](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Live%20scanning.md)

- 优化[系统资源管理](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Improved%20management%20of%20system%20resources.md)，通过核心任务执行引擎。

- 新的[配置库](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/The%20new%20configuration%20library.md)来存储配置信息。

- 新的[REST API](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Burp's%20new%20REST%20API.md)用来集成其他工具。

- 新的[响应渲染器](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/New%20response%20renderer.md)，它的功能和其他现代浏览器一样好。

## 谨慎使用

Burp现有代码库的重要部分已经被完全重写或者大量修改，还引入了大量新代码。这是一个非常**测试的版本**，我们也希望Burp 2.x通过一个很长的测试周期来发现和解决问题。

你应该去使用它，如果你想尝试一下Burp2.0的前沿功能并能接受下面的内容：
* 有一些bug
* 会漏掉一些Burp1.x能发现的一些漏洞
* 你可能会丢掉工作
* 它可能表现很差
* 我们将发布频繁得令人厌烦的bug修复更新

如果你更追求稳定性和全面性，喜欢一个成熟的产品，并且它的特性集已经非常棒，那么请继续使用Burp 1.x直到我们正式结束测试。

## 产品路线图

发布新的重大版本总是要在等它边完美和让用户获得很酷的新功能之间取得平衡。我们未来几个月会解决如下问题：
* 爬虫程序仍不能正确处理JavaScript导航。我们计划改进这一点，使Burp像真正的浏览器一样。
* 爬虫程序没有尽可能多地并行化它的工作，也没有充分利用配置的最大并发请求限制。解决这个问题将在大多数情况下提高爬行速度。
* 新的爬虫缺少在正常浏览之外发现内容(rebots.txt, HTML注释中的链接等)方面的一些功能。
* 站点地图仍然显示仅基于URL的爬行结果，对于GET请求，每个唯一URL包含一个条目。我们计划提供由爬虫生成的可视化导航图，并在站点地图本身中支持重载url。
* 由爬虫生成的导航图仅在爬取和审计扫描过程中可用。我们计划将这些数据用于其他目的，包括对选定项目的临时审计和手工测试工具如Repeater。
* 我们知道人们需要改进的工具来进行手动WebSockets测试。这些正在筹备中。

当它还在测试阶段，Burp2.x只供购买证书的专业用户使用。在beta阶段之后，我们将向Community Edition用户发布重大更新。


## 后续使用说明

[Burp2.0 爬虫和扫描器在哪里？](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Burp2.0%20Where%20are%20the%20Spider%20and%20Scanner.md)
[Burp2.0 扫描队列在哪？](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Burp2.0%20Where%20is%20the%20scan%20queue.md)
