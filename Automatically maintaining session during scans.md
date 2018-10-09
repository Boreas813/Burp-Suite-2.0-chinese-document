在之前的几天，我们介绍了Burp的[新爬虫](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Burp's%20new%20crawler.md)可以处理现代app带来的多变的挑战。但是爬虫只是这个故事的一部分。我们想爬取app的内容定位功能函数，是因为我们想审计这些内容和功能的安全漏洞。

Burp现在的扫描器（旧版）包含一个世界一流的扫描引擎，他可以精准审计广泛的漏洞。但是审计带有session传递的app时就显得力不从心。结合现在的爬虫（旧版），扫描器在简易cookie的系统工作的很好，但在更多复杂情况下会失效。你可以通过手动设置session处理规则来提高表现，但其实是脏乱差。

如果让扫描器可以在审计中自动处理session，让用户完全不用手工设置会怎样呢？在典型app情况下，Burp会扩大攻击面,发现更多的漏洞。

我们重写了扫描器的核心逻辑来做这件事。当审计通过新爬虫开始时，新的扫描器会沿着爬虫给出的导航图进行扫描，同时在审计中自动处理session。

让我们看看这是如何工作的。

当Burp开始审计单个请求时，他首先确定爬虫起始点到这个请求的最短路径。举个例子：

![](https://portswigger.net/cms/images/f4/a8/32ede8d7798f-article-auditing-8.png)

Burp会选择最高效的路径，重复发送相同的请求，这些请求带有有效的session。这个操作是通过首先重走一遍爬虫的路径来获取新鲜的session token，然后测试几个路径来检验session是否生效。

在许多情况下，最后的请求被一直重新发送是有可能的。因为请求没有包含任何session token在里面：

![](https://portswigger.net/cms/images/7a/a2/6d39f99c4dd2-article-auditing-9.png)

或者因为session token是可以多次使用的cookie：

![](https://portswigger.net/cms/images/6a/f9/69747a18b15c-article-auditing-10.png)

或者虽然请求包含cookie和csrf token，但是csrf token可以被重放：

![](https://portswigger.net/cms/images/e5/a9/4d5b954d16a6-article-auditing-11.png)

在极端情况下，每一步请求都被一个单独使用的token保护。这种情况通常出现在高安全级别的app中，导航路径被明确控制的情况下。在这种情况下，最可靠的重放请求进行审计的方式是从起点开始走完全程：

![](https://portswigger.net/cms/images/d4/ac/03456dfd4913-article-auditing-13.png)

到目前，Burp已经可以高效的重放带有session的请求进行审计。但是在审计过程中Burp会发送不同的请求，包含全部的payload扫描漏洞。许多原因会让这些请求session失效。一个显然的例子就是web防火墙扫描到payload然后阻断session。

为了解决这种情况，当新的扫描器发送各种审计代码时，他会监听app的响应确保有效的session被维持。如果Burp确认session有效，他在审计完成后会设置一个检查点。如果Burp确认session已经失效，他会回滚到最后一个检查点然后从那里恢复。这个逻辑确保了session管理开销的最小化，并且如果session经常丢失的话避免循环：

![](https://portswigger.net/cms/images/68/c7/795ab7bbd106-article-auditing-14.png)

总而言之Burp的新扫描器有如下变化：

- 自动获取有效session
- 当session失效时优雅的恢复
- 扫描时扩大成吨的攻击面
- 用户不再需要设置复杂的宏指令和session处理规则
