本周我们会发布一系列博客帮助用户从1.x迁移至2.0。我们将介绍在Burp2.0中以不同方式工作的各种特性并帮助你找到和使用这些新特性。

首先，爬虫和扫描工具从Burp主要窗口中移除了

## Burp1.x

Burp1.x的顶级tab选项卡中就有Spider和Intruder，你可以在上下文菜单中向它们发送选定的内容：
![](https://portswigger.net/cms/images/b0/d2/1d7374c4adb6-article-screen_shot_2018-09-14_at_14.02.05.png)

## Burp2.0

Burp2.0把它们移到了基于任务的模块中。

一种方法是点击仪表盘tab中的New scan按钮，它会打开一个向导页面让你配置扫描细节：
![](https://portswigger.net/cms/images/88/2a/229561eb8d25-article-screen_shot_2018-09-14_at_14.14.50.png)

每个扫描都有自己的配置设置。例如，对于爬虫任务，你可以配置爬虫优化、爬虫限制、登录选项和错误处理：
![](https://portswigger.net/cms/images/93/50/40d9996cecf4-article-screen_shot_2018-09-17_at_11.37.20.png)

这些配置可以被保存到配置库中。

使用新的基于人伍德模型，你可以配置多个并行扫描，每个扫描都有自己的设置，并独立监视和控制每个任务。这为你提供了更多的功能和灵活性，这是以前的单例顶级工具不能实现的。