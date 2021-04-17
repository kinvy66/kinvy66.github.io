# Hugo搭建博客


<!--more-->

## Hugo+GitHub Page 搭建个人博客



### 1. 下载安装Hugo

[官方文档](https://gohugo.io/getting-started/installing)  安装方式

```bash

mkdir $HOME/src  
cd $HOME/src
git clone https://github.com/gohugoio/hugo.git
cd hugo
go install --tags extended
```



直接下载EXE包安装

1. [GitHub](https://github.com/gohugoio/hugo/releases)下载最新的Release包

2. 解压包，将包的路径添加到环境变量

3. 查看是否安装成功

   > hugo version		#安装成功会显示hugo的版本







### 2. 搭建博客



1. 创建站点

   > hugo new site Blog     #会在当前文件夹下创建出一个Blog文件夹

![image-20210417170555191](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20210417170555191.png)





2. 添加主题

   Hugo不像Hexo是自带一个默认的主题，Hugo需要自己添加主题

   [主题下载](https://themes.gohugo.io/)

   推荐主题[LoveIt](https://github.com/dillonzq/LoveIt)，将下载的主题放到  `Blog/themes` 文件夹下

   ![image-20210417171115569](C:%5CUsers%5CKinvy%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5Cimage-20210417171115569.png)



 	将Blog目录下的`config.toml` 文件内容替换成[主题文档](https://hugoloveit.com/zh-cn/theme-documentation-basics/)提供的

```toml
baseURL = "http://example.org/"
# [en, zh-cn, fr, ...] 设置默认的语言
defaultContentLanguage = "zh-cn"
# 网站语言, 仅在这里 CN 大写
languageCode = "zh-CN"
# 是否包括中日韩文字
hasCJKLanguage = true
# 网站标题
title = "我的全新 Hugo 网站"

# 更改使用 Hugo 构建网站时使用的默认主题
theme = "LoveIt"

[params]
  # LoveIt 主题版本
  version = "0.2.X"

[menu]
  [[menu.main]]
    identifier = "posts"
    # 你可以在名称 (允许 HTML 格式) 之前添加其他信息, 例如图标
    pre = ""
    # 你可以在名称 (允许 HTML 格式) 之后添加其他信息, 例如图标
    post = ""
    name = "文章"
    url = "/posts/"
    # 当你将鼠标悬停在此菜单链接上时, 将显示的标题
    title = ""
    weight = 1
  [[menu.main]]
    identifier = "tags"
    pre = ""
    post = ""
    name = "标签"
    url = "/tags/"
    title = ""
    weight = 2
  [[menu.main]]
    identifier = "categories"
    pre = ""
    post = ""
    name = "分类"
    url = "/categories/"
    title = ""
    weight = 3

# Hugo 解析文档的配置
[markup]
  # 语法高亮设置 (https://gohugo.io/content-management/syntax-highlighting)
  [markup.highlight]
    # false 是必要的设置 (https://github.com/dillonzq/LoveIt/issues/158)
    noClasses = false
```



同样在Blog目录下新建 `config.yaml` 文件，内容如下

```yaml
---
baseurl: "http://example.org/"
DefaultContentLanguage: "zh-cn"
hasCJKLanguage: true
languageCode: "zh-cn"
title: "Kinvy's 万事屋"
theme: "LoveIt"  

```



3. 添加文章

   > hugo new posts/my-first-post.md   #在Blog路径下执行

![image-20210417171357411](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20210417171357411.png)

生成的文章是在 `/Blog/content/posts` 下，使用Markdown编辑器打开编写内容





4. 本地查看

   > hugo server -D

![image-20210417173655034](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20210417173655034.png)

在浏览器输入给出的地址，即可查看



5. 生成网页

   > hugo    -D 

   生成静态网页，所有生成的网页文件在`./public` 文件夹下，同样部署到GitHub也是只要将这个文件夹push







### 3. 部署到GitHub（Gitee）

1. 创建仓库

   仓库名一定要是==UserName.github.io==  其中UserName是GitHub的用户名，(下图中因为已经有该仓库，所以提示仓库名存在)

   ![image-20210417174811326](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20210417174811326.png)



2. 推送到GitHub

   初始化本地仓库，注意：**要在`Blog/public`下初始化**

   > git init

![image-20210417175415510](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20210417175415510.png)

​		

git仓库的用户名和邮箱配置等步骤省略.....

注意：初始化仓库后要提交一次才可以关联远程仓库



**关联远程仓库**

> git remote add origin https://github.com/Kinvy66/Kinvy66.github.io.git    #关联远程仓库
>
> git push -u origin master				#第一次推送，同时跟踪远程分支

​		





4. 浏览

   在浏览器地址栏输入 `UserName,githu,io` 就可以访问博客
