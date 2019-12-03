# Burp2.0 扫描队列在哪里？

Burp1.x有一个相当突出的活动扫描队列视图，你可以监视它以查看扫描进度。这个去哪了？

## Burp1.x

以前，顶级Scanner选项卡可以让你查看进度，点进Scan queue这个tab页中：
![](https://portswigger.net/cms/images/25/ac/d4b31263a79c-article-screen_shot_2018-09-13_at_13.13.54.png)

## Burp2.0

Burp2.0中每个任务单独维护自己的工作队列。仪表盘显示每个任务的进度摘要。如果你需要更多的信息，请点击View details查看：
![](https://portswigger.net/cms/images/c7/1e/8d8ec8d1f44b-article-screen_shot_2018-09-20_at_11.11.53.png)

点击More details打开任务的[任务详情窗口](https://portswigger.net/burp/documentation/desktop/dashboard/task-details)，显示各种信息。对于涉及审计的任务，点击[审计项目](https://portswigger.net/burp/documentation/desktop/scanning/audit-items)选项卡查看工作队列和进度。

你还可以查看有关该人伍德其他信息，包括事件日志，其中显示警报或其他信息，这些信息可能有助于排除网络连接或其他问题:
![](https://portswigger.net/cms/images/2f/2f/fd0390d19bc3-article-screen_shot_2018-09-20_at_11.51.00.png)