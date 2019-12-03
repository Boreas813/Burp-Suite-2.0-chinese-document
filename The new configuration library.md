Burp目前的Spider和Scanner都有自己的全局配置选项。你可以把它们保存为配置文件，这样你可以高效管理配置并在需要的场合加载它们。

在[多重并行扫描](https://github.com/Boreas514/Burp-Suite-2.0-chinese-document/blob/master/Multiple%20parallel%20scans.md)介绍中，需要一种改进的配置管理方法。

进入新的配置库：
![](https://portswigger.net/cms/images/0e/9d/47634176d85a-article-configuration_library.png)

配置库可以让你管理你自己的针对不同任务的配置。你可以创建不同类型扫描的配置。

Burp附带一组默认配置，而配置库包含许多用于公共目的内置配置。当然，你也可以创建你自己的。

在库中创建或编辑配置时，打开相关类型的配置编辑器，你可以在其中选择要定义的区域，并设置所需的选项:
![](https://portswigger.net/cms/images/f6/0d/19c3ac59b05d-article-edit_auditing_configuration.png)

你可以导出或导入配置，其格式与Burp常规配置选项的JSON格式相同。你可以轻松地与其他人协作，并共享其他人认为有用的配置。
