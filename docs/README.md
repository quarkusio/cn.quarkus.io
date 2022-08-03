# Quarkus.io网站基于Jekyll

## 入门指南

这些指令会给你一份Quarkus.io网站的副本，启动并运行在本地机器上，用于开发和测试。

### 安装

[Jekyll 静态站点生成器文档](https://jekyllrb.com/docs/).

1. 安装完整的 [Ruby开发环境](https://jekyllrb.com/docs/installation/)。如果你使用 `rvm`, 运行: `rvm use 2.7.1`.

2. 安装 [bundler](https://jekyllrb.com/docs/ruby-101/#bundler)  [gems](https://jekyllrb.com/docs/ruby-101/#gems)

  
        gem install bundler

3. 将 [项目 repository](https://github.com/quarkusio/quarkusio.github.io)打分支，然后克隆您的 fork.

  
        git clone git@github.com:YOUR_USER_NAME/quarkusio.github.io.git

4. 切换到工程目录：

  
        cd quarkusio.github.io

5. 使用bundler获取各自版本中所需的所有gems


        bundle install

6. 构建站点并使其在本地服务器上可用

  
        bundle exec jekyll serve

7. 现在用浏览器访问 http://localhost:4000


> 如果您在上述过程中遇到任何意外错误，请参阅 [排错](https://jekyllrb.com/docs/troubleshooting/#configuration-problems) 页面或者 [需求](https://jekyllrb.com/docs/installation/#requirements) 页面，因为您可能会错过开发headers或其他先决条件。

**更多关于使用Jekyll，请参考 [Jekyll循序渐进教程](https://jekyllrb.com/docs/step-by-step/01-setup/).**

### 部署到GitHub页面

网站部署由GitHub Actions自动执行(当提交被推送到 `develop` 分支时)。
如果由于某些原因需要从本地机器进行部署，请遵循以下说明：


1. 安装 [act](https://github.com/nektos/act#installation) 可执行文件本地运行GitHub Actions

2. 运行 `act -s GITHUB_TOKEN=<GITHUB_TOKEN>`，其中 *<GITHUB_TOKEN>* 需要替换为允许您推送到 https://github.com/quarkusio/quarkusio.github.io repository 的令牌。


## 写博客

写博客：

- 创建一个作者条目在 [_data/authors.yaml](https://github.com/quarkusio/quarkusio.github.io/blob/develop/_data/authors.yaml)

  - 你可以使用您已经在 [Gravatar service](https://gravatar.com) 注册的电子邮件，在Linux运行 `echo -n your@email.org | md5sum` 或在macOS运行 `echo -n your@email.org | md5` 获得`emailhash` 。

     
- 创建一个博客条目在 [_posts](https://github.com/quarkusio/quarkusio.github.io/tree/develop/_posts)

  - 文件名格式 `yyyy-mm-dd-slug.adoc`

- `tags` 应该谨慎使用，因为存档页面是为它们创建的。以下是一些你可以尝试遵循的基本规则：

  - `quarkus-release` 用于Quarkus发布博客

  - `announcement` 用于具有一定影响的一般公告。

  - `extension` 用于与特定扩展相关的博客。

  - `user-story` 用于用户/公司采用Quarkus的故事。

  - `development-tips` 用于带有使用Quarkus或Quarkus本身开发提示的博客。 

  - 如果你的帖子与该技术有显著的相关性，可以添加一个技术细节，比如 `kafka`。

  - 标记是由空格分隔的列表 `tags:extension grpc`

  - 标签必须英文小写

- 它是asciidoc格式的，有一个示例显示 [2019-06-05-quarkus-and-web-ui-development-mode.adoc](https://github.com/quarkusio/quarkusio.github.io/blob/develop/_posts/2019-06-05-quarkus-and-web-ui-development-mode.adoc)

  - 请注意，asciidoc序言中的 `date` 属性定义了文章将于何时发布。在写文章时使用当前日期进行本地测试，然后在提交之前切换到实际的目标日期。 

- 对开发分支发送一个博客的合并请求


## Translations/Localization (l10n)

The primary site (quarkus.io) is written in English. 

There are separate repositories for community driven localized versions of quarkus.io:

- [ja.quarkus.io](https://github.com/quarkusio/ja.quarkus.io) for Japanese

- [cn.quarkus.io](https://github.com/quarkusio/cn.quarkus.io) for Chinese (simplified)

- [es.quarkus.io](https://github.com/quarkusio/es.quarkus.io) for Spanish


If you want to contribute to those efforts read the README in those projects. If you would like to
start another translation, please open an issue in this main repo.

#### Enable DNS for l10n site

Once a localized site has enough of its content translated, DNS needs to be enabled. To do that get one of the Red Hat admins to submit
a ticket to IT asking for XX domain:

```
We need a CNAME record set up for XX.quarkus.io to have it serve out GitHub pages. 

The CNAME record for XX.quarkus.io should point to "quarkusio.github.io.".
```

See Step 5 on https://docs.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site for more information.

## 贡献

请参考 [CONTRIBUTING.md](https://github.com/quarkusio/quarkusio.github.io/blob/master/CONTRIBUTING.md) 关于我们的行为准则的细节，以及提交合并请求给我们的过程。

**重要：** 指南保存在主Quarkus仓库中，合并请求应该提交到那里：
https://github.com/quarkusio/quarkus/tree/main/docs/src/main/asciidoc.

## 许可证

本网站是根据 [知识共享署名许可协议 3.0](https://creativecommons.org/licenses/by/3.0/) 维护。
