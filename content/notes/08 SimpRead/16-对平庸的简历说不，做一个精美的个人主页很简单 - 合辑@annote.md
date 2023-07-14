---
title: "对平庸的简历说不，做一个精美的个人主页很简单 - 合辑"
alias: 
  - "对平庸的简历说不，做一个精美的个人主页很简单 - 合辑"
created-date: 2023-03-31T10:13:31+0800
type: Simpread
banner: "https://cdn.sspai.com/attachment/origin/2016/06/22/333988.png "
banner_icon: 🔖
tag: 
idx: 16
---

# 对平庸的简历说不，做一个精美的个人主页很简单 - 合辑

> [!example]- [🧷内部链接](<http://localhost:7026/unread/16>) [🌐外部链接](<https://sspai.com/post/34380>)    
> URI:: [🧷](<http://localhost:7026/unread/16>) [🌐](<https://sspai.com/post/34380>) 
> intURI:: [🧷内部链接](<http://localhost:7026/reading/16>)

%%
> [!example]+ **Comments**  
> ```dataview
> TABLE 
>     WITHOUT ID
>     link(Source, dateformat(date(Source), "yyyy-MM-dd")) as Date___, 
>     regexreplace(rows.Comments,"^@@\[\[.+?\]\]\s","") as "Comments"
> FROM "journals"
> WHERE  contains(cmnt, this.file.name)
> FLATTEN cmnt as Comments
> WHERE contains(Comments, this.file.name)
> GROUP BY file.link as Source
> SORT rows.file.day desc
> ```
>  **Description**:: 自媒体与自我营销的兴起，使得轻量级个人网站的需求日益显现：我们需要一个集成化的个人门户平台，它不需要很复杂很专业，但在我们需要进行自我推荐时，它能简单地帮我们介绍自己。
%%

> [!md] Metadata  
> **标题**:: [对平庸的简历说不，做一个精美的个人主页很简单 - 合辑](https://sspai.com/post/34380)  
> **日期**:: [[2023-03-31]]  
