# 微信读书和 Notion 同步

![](https://raw.githubusercontent.com/Parantric/picture-bed/main/202307151329909.jfif)


本项目通过 Github Action 按照设定的时间同步微信读书划线到Notion。

预览效果：https://book.malinkang.com

**注意：请不要在 Page 里面添加自己的笔记，有新的笔记的时候会删除原笔记重新添加。**

## 使用说明

1. 获取微信读书的 Cookie
    * 浏览器打开 https://weread.qq.com/
    * 微信扫码登录确认，提示没有权限忽略即可
    * 按F12进入开发者模式，依次点 Network -> Doc -> Headers-> cookie。复制 Cookie 字符串;
2. 获取 NotionToken
    * 浏览器打开https://www.notion.so/my-integrations
    * 点击New integration 输入name提交
    * 点击show，然后copy
3. 复制[这个Notion模板](https://malinkang.notion.site/a7794117392d4625ace722f78742afca?v=0a9551b0702649fa9913ff4f3758ace0)，删掉所有的数据，并点击右上角设置，Connections 添加你创建的Integration。
4. 获取 NotionDatabaseID
    * 打开Notion数据库，点击右上角的Share，然后点击Copy link
    * 获取链接后比如 https://www.notion.so/malinkang/1b78f0fd0d03484caa00154285ffec0c?v=7ed7e3fbe69043a28d2847e76f075d99&pvs=4 中间的1b78f0fd0d03484caa00154285ffec0c就是DatabaseID
5. 在Github的Secrets中添加以下变量
    * 打开你fork的工程，点击Settings->Secrets and variables->New repository secret
    * 添加以下变量
        * WEREAD_COOKIE
        * NOTION_TOKEN
        * NOTION_DATABASE_ID
6. 🔔 注意：使用 cron 表达式的设置执行时间的时候，默认时区是 UTC 标准时区(英国或者冰岛时区)，在设置的时候需要在原来的基础上 +8 个小时才是中国时区的时间。
7. [🔛 启动任务界面直达](https://github.com/Parantric/weread_to_notion/actions/workflows/weread.yml){:target="_blank"}

## 🔗参考

[github cron 表达式](https://github.com/chiupam/tutorial/blob/master/Loon/Plus/cron.md)

[GitHub Actions 的工作流语法(官方)](https://docs.github.com/zh/actions/using-workflows/workflow-syntax-for-github-actions)
