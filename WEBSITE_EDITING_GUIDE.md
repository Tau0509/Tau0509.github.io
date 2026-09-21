# Tau0509 个人主页修改指南

网站地址：<https://tau0509.github.io>  
源码仓库：<https://github.com/Tau0509/Tau0509.github.io>

这个网站使用 Academic Pages 和 GitHub Pages。修改仓库中的文件并提交后，GitHub 会自动重新生成网站，通常需要 1–3 分钟。

## 最简单的修改方式：直接在 GitHub 网页编辑

1. 打开源码仓库：<https://github.com/Tau0509/Tau0509.github.io>。
2. 找到需要修改的文件并点击进入。
3. 点击右上角的铅笔图标（Edit this file）。
4. 修改内容。
5. 点击 **Commit changes**，填写简短说明并确认提交。
6. 打开仓库的 **Actions** 页面，等待 `pages build and deployment` 显示绿色成功标记。
7. 访问网站检查结果。如果仍看到旧内容，请强制刷新页面，或在网址末尾临时加上 `?v=2`。

## 网站各部分对应的文件

| 网站内容 | 需要修改的文件 |
| --- | --- |
| 网站名称、个人资料、学校、GitHub 链接 | `_config.yml` |
| 首页正文 | `_pages/about.md` |
| 顶部导航栏 | `_data/navigation.yml` |
| Publications 页面 | `_pages/publications.html` |
| CV 页面 | `_pages/cv.md` |
| Blog 列表页面 | `_pages/year-archive.html` |
| Blog 文章 | `_posts/` 目录中的 Markdown 文件 |
| 头像 | `images/profile.png` |
| 左侧个人资料布局 | `_includes/author-profile.html` |
| 左侧栏样式 | `_sass/layout/_sidebar.scss` |

不要编辑 `_site/` 目录中的文件。它是自动生成的，即使修改也会在下次部署时被覆盖。

## 修改基本资料

打开 `_config.yml`，常用字段如下：

```yaml
title: "Zihaotao"
name: &name "Zihao Tao"
description: &description "Zihao Tao, PhD student at Huazhong University of Science and Technology."

author:
  avatar: "profile.png"
  name: "Zihao Tao"
  bio: "PhD student at Huazhong University of Science and Technology"
  employer: "Huazhong University of Sci. and Tech."
  employer_url: "https://hust.edu.cn"
  github: "Tau0509"
```

修改 YAML 文件时请保留缩进。冒号后的文本建议放在英文双引号中。

## 修改首页

首页内容位于 `_pages/about.md`。文件开头两组 `---` 之间的内容叫 Front Matter，不要删除。正文写在第二个 `---` 之后：

```markdown
---
permalink: /
title: "Zihao Tao"
author_profile: true
---

Hello! I am Zihao Tao, a PhD student at Huazhong University of Science and Technology.

## Research Interests

- Machine learning
- Your second research interest
```

## 修改顶部导航栏

导航栏位于 `_data/navigation.yml`：

```yaml
main:
  - title: "Publications"
    url: /publications/
  - title: "Blog Posts"
    url: /year-archive/
  - title: "CV"
    url: /cv/
```

调整条目的顺序即可改变导航顺序。删除某个条目只会移除导航入口，不一定会删除对应页面。

## 新建 Blog 文章

在 `_posts/` 目录中创建 Markdown 文件。文件名必须使用：

```text
YYYY-MM-DD-英文短标题.md
```

例如：

```text
2026-09-21-my-first-post.md
```

文章模板：

```markdown
---
title: "My First Post"
date: 2026-09-21
permalink: /posts/2026/09/my-first-post/
tags:
  - research
  - notes
---

Write the introduction here.

## Section Title

Write the main text here.

![Image description](/images/example.png)

[External link](https://example.com)
```

提交后，文章会自动出现在 **Blog Posts** 页面。若不希望立即发布，可先把文件放在 `_drafts/` 目录，而不是 `_posts/`。

## 修改或删除 Blog 文章

- 修改：打开 `_posts/` 中对应的 `.md` 文件，编辑后提交。
- 删除：打开文章文件，点击 GitHub 页面右上角的删除图标，然后提交。
- 修改发布日期：同时修改文件名开头的日期和 Front Matter 中的 `date`。
- 修改文章网址：修改 `permalink`。修改后旧网址将失效，已分享的链接也会失效。

## 添加 Publications

每篇论文在 `_publications/` 中对应一个 Markdown 文件。创建示例：

```markdown
---
title: "Paper Title"
collection: publications
category: conferences
permalink: /publication/2026-paper-title
date: 2026-01-01
venue: "Conference Name"
paperurl: "https://example.com/paper.pdf"
citation: "Zihao Tao, Coauthor. Paper Title. Conference Name, 2026."
---

Brief description of the paper.
```

可用的 `category` 包括：

- `books`
- `manuscripts`
- `conferences`

论文 PDF 可以上传到 `files/`，然后将 `paperurl` 写成 `/files/文件名.pdf`。

## 修改 CV

CV 内容位于 `_pages/cv.md`，使用普通 Markdown：

```markdown
## Education

- PhD student, Huazhong University of Science and Technology

## Research Experience

- Project or experience description

## Publications

- Publication information

## Awards

- Award information
```

## 更换头像

1. 准备正方形 PNG 图片。
2. 将文件命名为 `profile.png`。
3. 上传到仓库的 `images/` 目录，覆盖原文件。
4. 建议分辨率为 600 × 600 像素左右，避免文件过大。

如果使用不同文件名，需要同时修改 `_config.yml` 中的：

```yaml
author:
  avatar: "新文件名.png"
```

## Markdown 常用语法

```markdown
# 一级标题
## 二级标题

普通段落。

**粗体**
*斜体*

- 无序列表
- 第二项

1. 有序列表
2. 第二项

[链接文字](https://example.com)
![图片说明](/images/example.png)

`行内代码`
```

## 本地修改方式（可选）

如果使用 Git：

```bash
git clone https://github.com/Tau0509/Tau0509.github.io.git
cd Tau0509.github.io

# 修改文件后
git add .
git commit -m "Update website content"
git push
```

本地预览需要 Ruby 和 Bundler：

```bash
bundle install
bundle exec jekyll serve
```

然后访问 <http://localhost:4000>。

## 发布失败时检查

1. 打开仓库的 **Actions** 页面查看失败任务。
2. 检查 YAML 的缩进、冒号和引号。
3. 检查每个 Markdown 文件开头是否有完整的两组 `---`。
4. 检查 `_posts/` 中的文件名是否以有效日期开头。
5. 恢复最近一次修改后重新提交。

网站代码和历史版本都保存在 GitHub 中。误改后可在文件的 **History** 页面查看旧版本并恢复。
