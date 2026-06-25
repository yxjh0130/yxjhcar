---
title: AnZhiYu主题文章配置完全指南（小白必看）
date: 2026-06-25 00:00:00
categories:
  - 博客教程
tags:
  - Hexo
  - AnZhiYu
  - Front Matter
  - 小白教程
description: 超详细的AnZhiYu主题文章Front Matter配置教程，从零开始教你设置封面图、顶部背景、目录、置顶等所有功能。
cover: /media/卡丁车主板刷机接线图（平衡车主板刷卡丁车）/image1.png
top_img: /media/卡丁车主板刷机接线图（平衡车主板刷卡丁车）/image1.png
---

## 一、什么是 Front Matter？

Front Matter 是每篇文章**最开头**用 `---` 包裹起来的那块配置区域。它就像文章的"身份证"，告诉主题这篇文章该长什么样、有哪些功能。

**示例：**

```markdown
---
title: 我的第一篇文章
date: 2026-06-25 00:00:00
categories:
  - 教程
tags:
  - Hexo
  - 博客
description: 这是一篇测试文章
---
```

> **注意：** Front Matter 必须放在文章第一行，以 `---` 开头，以 `---` 结尾。中间的内容就是配置项。

---

## 二、基础配置（必填项）

### 1. title（文章标题）

```yaml
title: 我的文章标题
```

这是文章的标题，会显示在首页、文章页顶部。

### 2. date（发布日期）

```yaml
date: 2026-06-25 09:30:00
```

文章的发布日期，格式为 `年-月-日 时:分:秒`。只写日期也可以：

```yaml
date: 2026-06-25
```

### 3. categories（分类）

```yaml
categories:
  - 教程
  - 前端
```

文章的分类，可以有多个层级。上面的配置表示：属于"教程"分类下的"前端"子分类。

> 如果只有一个分类，也可以简写为 `categories: 教程`

### 4. tags（标签）

```yaml
tags:
  - Hexo
  - 博客
  - 建站
```

文章的标签，可以写多个，用 `-` 开头分行列出。

---

## 三、图片相关配置（重点）

### 5. cover（封面图）

```yaml
cover: /media/你的图片.png
```

**作用：** 文章在**首页列表**、**归档页**、**侧边栏**显示的小封面图。

**示例：**

```yaml
cover: /media/卡丁车刷机/image1.png
```

### 6. top_img（文章顶部大图背景）

```yaml
top_img: /media/你的图片.png
```

**作用：** 打开文章后，**标题后面**那块大图背景。这是最显眼的图片区域。

> 如果没有设置 `top_img`，主题会自动使用 `cover` 作为顶部背景。
> 如果设为 `false`，则关闭顶部背景图：`top_img: false`

---

## 四、文章显示控制

### 7. description（文章摘要/描述）

```yaml
description: 这是一段文章简介，会显示在首页列表中
```

**作用：** 在首页文章列表中显示的文字简介，也用于 SEO 描述。

### 8. toc（目录开关）

```yaml
toc: true   # 显示目录
toc: false  # 隐藏目录
```

**作用：** 控制文章右侧是否显示目录导航。

### 9. toc_number（目录编号）

```yaml
toc_number: true   # 目录显示序号（1. 2. 3.）
toc_number: false  # 目录不显示序号
```

### 10. toc_expand（目录是否展开）

```yaml
toc_expand: true   # 目录默认全部展开
toc_expand: false  # 目录默认折叠，只显示一级标题
```

### 11. comments（评论开关）

```yaml
comments: true   # 允许评论
comments: false  # 关闭评论
```

### 12. aside（侧边栏开关）

```yaml
aside: true   # 显示侧边栏
aside: false  # 隐藏侧边栏
```

---

## 五、首页展示相关

### 13. sticky / top（文章置顶）

```yaml
sticky: 100
```

**作用：** 让文章固定在首页最前面。**数字越大，排得越靠前。**

```yaml
sticky: 1    # 置顶，优先级较低
sticky: 999  # 置顶，优先级最高
```

### 14. swiper_index（首页轮播图）

```yaml
swiper_index: 1
```

**作用：** 将文章放入首页顶部的轮播图区域。**数字越大，排得越靠前。**

### 15. top_group_index（首页推荐分组）

```yaml
top_group_index: 1
```

**作用：** 将文章放入首页推荐分组区域。数字越大越靠前。

---

## 六、高级功能

### 16. copyright（版权声明）

```yaml
copyright: false  # 关闭版权声明
```

### 17. copyright_author / copyright_url（自定义版权信息）

```yaml
copyright_author: 小明
copyright_url: https://example.com
```

### 18. keywords（SEO关键词）

```yaml
keywords:
  - 卡丁车
  - 平衡车
  - 刷机教程
```

**作用：** 设置网页的关键词，有助于搜索引擎收录。

### 19. mathjax / katex（数学公式）

```yaml
mathjax: true   # 启用 MathJax 数学公式
katex: true     # 启用 KaTeX 数学公式（更快）
```

> 二选一即可，不要同时开启。

### 20. password（文章密码保护）

```yaml
password: 123456
```

**作用：** 设置后，访问文章需要输入密码才能查看。

### 21. aplayer（音乐播放器）

```yaml
aplayer: true
```

### 22. updated（更新日期）

```yaml
updated: 2026-06-28 10:00:00
```

---

## 七、完整配置示例

下面是一个包含了常用配置的完整示例，直接复制修改即可：

```yaml
---
title: 我的博客文章标题
date: 2026-06-25 09:00:00
updated: 2026-06-26 15:00:00
categories:
  - 教程
  - Hexo
tags:
  - 博客
  - AnZhiYu
  - 建站教程
description: 这是一篇关于Hexo博客配置的详细教程。
cover: /media/我的文章/cover.png
top_img: /media/我的文章/bg.png
sticky: 100
toc: true
toc_number: true
toc_expand: false
comments: true
aside: true
keywords:
  - Hexo
  - 博客
  - AnZhiYu
---
```

---

## 八、常见问题

**Q1：封面图和顶部背景图有什么区别？**

| 配置项 | 显示位置 | 图片大小 |
|--------|----------|----------|
| `cover` | 首页列表、侧边栏 | 小图（缩略图） |
| `top_img` | 文章页顶部大背景 | 大图（全宽横幅） |

**Q2：图片放在哪里？**

建议所有图片放在 `source/media/` 目录下，每篇文章的图片单独用一个文件夹：

```
source/
  media/
    文章名称A/
      image1.png
      image2.png
    文章名称B/
      photo.png
```

引用时路径为：`/media/文章名称A/image1.png`（注意开头要加 `/`）

**Q3：为什么我的图片显示不出来？**

检查三点：
1. 图片路径是否正确（区分大小写！）
2. 图片是否放在了 `source/` 目录下
3. 路径是否以 `/` 开头

**Q4：置顶文章怎么设置？**

在 Front Matter 中添加 `sticky: 数字`，数字越大越靠前。比如 `sticky: 999` 会排在最前面。

---

> 本文参考自 [AnZhiYu 官方文档](https://docs.anheyu.com/page/front-matter.html)