# 博客
这里准备搭建我的个人博客

## 文章数据流
1. 文章数据从文件夹里
2. 到数据库里
3. 到前端页面

## 写文章的步骤
1. 写文章
2. 运行脚本来在文章中添加日期数据 eg：python3 add_article.py
3. 更新数据库里的文章 访问 http://127.0.0.1:8000/renew_article

### 有关文章的映射关系
0. 阅读 model 内容的表结构
1. 项目根目录的 Article 文件夹里的所有文件夹都是 tag，文件夹名位 tag name
2. 所有文章都是 article 上层文件夹就是他的 tag， 其中 title 是文件名， pubdate 和 changedate 分布为文件内容的第一行和第二行，文件正文 content 从第三行开始。

## TODO
- [ ] 支持 markdown
- [x] 扫描 Article 文件夹的文章
- [x] Article 页面
- [x] 侧边栏，罗列三级标签
- [ ] 作者页面
- [x] tag 信息 aritcle list 里

## 设计关键
- 导航栏标签、专辑标签
- 银色为主色调

## 实现细节
### 页面

#### 通用
1. 导航栏：编程、感悟、诗、电影、关于我。
2. 右侧边栏（专辑标签、最新发表）
3. 主体部分：
    - if 主页面:
        - 文章列表。
    - if 单个文章页面:
        - 文章目录结构(md 的标题结构)
        - 文章正文
    - if 关于我:
        - github
        - 知乎
        - coderunion qq 群
        - 脱单时间

### 排版和标签

- 主页文章可以通过标签筛选，可以置顶。
- 标签使用文件夹目录作为标签名
- 导航栏标签分两级，分别用 post 目录下的第一级、第二级目录，专辑标签则用第三级目录（如果有）

### 功能
支持 rss


### 程序编写

每次 push 到 github 会触发服务器端的程序运行，扫描 post 文件夹，将新的文件信息写入到数据库。
