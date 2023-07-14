---
title: "Why I'm unreachable and maybe you should be too"
alias: 
  - "Why I'm unreachable and maybe you should be too"
created-date: 2023-04-04T16:05:57+0800
type: Simpread
banner: "https://levels.io/content/images/2021/03/Zen-rock-garden-fall-Ryoanji-Temple-Kyoto-Japan.jpeg "
banner_icon: 🔖
tag: 
idx: 19
---

# Why I'm unreachable and maybe you should be too

> [!example]- [🧷内部链接](<http://localhost:7026/unread/19>) [🌐外部链接](<https://levels.io/contact/>)    
> URI:: [🧷](<http://localhost:7026/unread/19>) [🌐](<https://levels.io/contact/>) 
> intURI:: [🧷内部链接](<http://localhost:7026/reading/19>)

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
>  **Description**:: You may have noticed it's practically impossible to contact me. I did that on
purpose so I can spend ......
%%

> [!md] Metadata  
> **标题**:: [Why I'm unreachable and maybe you should be too](https://levels.io/contact/)  
> **日期**:: [[2023-04-04]]  
