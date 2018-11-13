# 启动扫描

之前的几天我们介绍了[并行扫描](https://portswigger.net/blog/multiple-parallel-scans)， [高效管理系统资源](https://portswigger.net/blog/improved-management-of-system-resources)和[新的配置库](https://portswigger.net/blog/the-new-configuration-library)。今天我们看一下如何启动扫描。

首先是一些术语。在过去，我们讨论了爬取(意思是发现内容)和扫描(意思是测试漏洞)。在未来，我们正在做一个微妙的改变。所有这些都是扫描的。扫描包括内容爬取和漏洞审计。当你读这篇文章的时候，你会清楚为什么这个变化是有意义的。

您可以通过在Burp内的任意位置选择项目并从上下文菜单中选择"Scan"选项来启动扫描。(这将替换先前的上下文菜单选项，被动扫描、主动扫描或爬取)。还会有一个突出的"New scan"按钮，可以让你在没有进行选择的情况下启动扫描。

打开启动扫描界面：
![](https://portswigger.net/cms/images/cb/1f/46c1ab1c5e64-article-scan_launcher.png)

启动器让你选择一个扫描类型：
![](https://portswigger.net/cms/images/b9/90/06d5341e6886-article-scan_launcher_-_scan_type.png)

如果扫描包括爬取，那么你必须在URLs to Scan表格里指定一个目标：
![](https://portswigger.net/cms/images/51/11/6ed9085d9fe3-article-scan_launcher_-_urls_to_scan.png)

如果扫描包括审计您已经选择的项目，那么这些项目会列出，并可以根据各种标准合并这些项目:
![](https://portswigger.net/cms/images/b7/96/50a8eb54ae2b-article-scan_launcher_-_items_to_scan.png)

到现在，你可以不再设置任何东西直接启动扫描，或者接着设置其他选项。

你可以选择一个或多个配置用于扫描，从你的[配置库](https://portswigger.net/blog/the-new-configuration-library)中选择它们，或在运行中指定:
![](https://portswigger.net/cms/images/17/37/fe1304b2031d-article-scan_launcher_-_scan_configuration.png)

如果选择了多个配置，这些配置将依次应用，以确定使用的最终配置。每个配置可以或多或少，为多个区域或仅一个区域定义设置。这个功能允许您首先应用一个通用配置(例如，首选的通用扫描设置)，然后再应用一个指定的配置(例如，对这个特定应用程序有用的一些特定选项)。

您还可以提供应用登录凭证，该凭证应用于在[爬取期间登录](https://portswigger.net/blog/crawling-with-multiple-logins):
![](https://portswigger.net/cms/images/17/e5/15e325dcaf9a-article-scan_launcher_-_application_login.png)

你可以指定[资源池](https://portswigger.net/blog/improved-management-of-system-resources)：
![](https://portswigger.net/cms/images/ed/4e/5300219ed2f2-article-scan_launcher_-_resource_pool.png)

聪明的读者会注意到，Burp现有的被动扫描和主动扫描之间的区别正在消失。在即将到来的更新中，扫描只是扫描。当然，你仍然可以执行只审核被动问题的扫描，通过将扫描配置设置为只检查被动问题来实现:
![](https://portswigger.net/cms/images/62/c3/527af5c4cc57-article-scan_launcher_-_passive_audit.png)

以统一的方式处理被动扫描和主动扫描的好处是现在两者都将使用相同的UI，允许同时监视和控制被动扫描:
![](https://portswigger.net/cms/images/df/86/100ab9b80ffe-article-scan_launcher_-_passive_audit_items.png)
