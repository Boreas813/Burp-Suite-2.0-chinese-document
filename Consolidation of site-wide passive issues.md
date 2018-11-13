# 合并被动问题

你是否见过Burp报告成百上千个同一个站点的被动问题？
![](https://portswigger.net/cms/images/86/39/5d843b588215-article-clickjacking_old.png)
这是因为这些问题来自于同一个app的不同位置，有时是全部的response。
这可能是各种原因引起的：

- 开发者的选择，开发者可能并不关心xss。
- template包含跨域脚本或者识别不出来的字符集
- 平台配置问题，例如框架式响应或者未强制性传输加密

新的扫描器会将结果合并到一起：
![](https://portswigger.net/cms/images/ec/d2/c9934c15ec34-article-clickjacking_new.png)
如你所见，310个点击劫持已经变成一个问题了。