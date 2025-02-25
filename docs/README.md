# Quarkus.io网站基于Jekyll

## 入门指南

这些指令会给你一份Quarkus.io网站的副本，启动并运行在本地机器上，用于开发和测试。

### 安装

#### Using Docker

1. Install [Docker Desktop](https://docs.docker.com/install/).

2. Fork the [project repository](https://github.com/quarkusio/quarkusio.github.io), then clone your fork:


        git clone git@github.com:YOUR_USER_NAME/quarkusio.github.io.git

3. 切换到工程目录：


        cd quarkusio.github.io

4. Run Docker Compose:


        docker compose up

    > **Note:** The startup process may take several minutes, depending on your system. During this time, you might see logs with warnings or configuration messages (e.g., AutoPages and asciidoctor warnings). This is normal behavior as Jekyll builds the site. Once the server is running, you will see output like this:

    ```
    jekyll-1  |   Server address: http://0.0.0.0:4000/
    jekyll-1  |   Server running... press ctrl-c to stop.
    ```

    If any error occurs mentioning a name conflict, try:

        docker compose up --force-recreate

5. Now browse to [http://localhost:4000](http://localhost:4000).

#### Using a local Ruby environment
[Jekyll 静态站点生成器文档](https://jekyllrb.com/docs/).

1. Install a full [Ruby development environment](https://jekyllrb.com/docs/installation/). If you use `rvm`, run: `rvm use 3.2.3`.

2. 安装 [bundler](https://jekyllrb.com/docs/ruby-101/#bundler)  [gems](https://jekyllrb.com/docs/ruby-101/#gems)

  
        gem install bundler

3. 将 [项目 repository](https://github.com/quarkusio/quarkusio.github.io)打分支，然后克隆您的 fork.

  
        git clone git@github.com:YOUR_USER_NAME/quarkusio.github.io.git

4. 切换到工程目录：

  
        cd quarkusio.github.io

5. 使用bundler获取各自版本中所需的所有gems


        bundle install

6. 构建站点并使其在本地服务器上可用

  
        ./serve.sh

   Or if you want it faster and okay to not have guides included use the following:

        ./serve-noguides.sh


7. 现在用浏览器访问 http://localhost:4000


> 如果您在上述过程中遇到任何意外错误，请参阅 [排错](https://jekyllrb.com/docs/troubleshooting/#configuration-problems) 页面或者 [需求](https://jekyllrb.com/docs/installation/#requirements) 页面，因为您可能会错过开发headers或其他先决条件。

**更多关于使用Jekyll，请参考 [Jekyll循序渐进教程](https://jekyllrb.com/docs/step-by-step/01-setup/).**

### 部署到GitHub页面

The website deployment is automatically performed by GitHub Actions (when commits are pushed to the `main` branch).
If for some reason you need to deploy from your local machine, follow these instructions:

1. 安装 [act](https://github.com/nektos/act#installation) 可执行文件本地运行GitHub Actions

2. 运行 `act -s GITHUB_TOKEN=<GITHUB_TOKEN>`，其中 *<GITHUB_TOKEN>* 需要替换为允许您推送到 https://github.com/quarkusio/quarkusio.github.io repository 的令牌。


## 写博客

> **NOTE:** Using generative AI in *assisting* writing is fine, but please don't use it to write entire posts. 
> Used badly, generative AI has a tendency to use complex words and phrasing. This makes 
the content hard to read and understand. Always review your blog with a human reader in mind, make sure it's factually correct and especially keep the human touch and opinions in the content.

写博客：

- create an author entry in [_data/authors.yaml](https://github.com/quarkusio/quarkusio.github.io/blob/main/_data/authors.yaml)

  - 你可以使用您已经在 [Gravatar service](https://gravatar.com) 注册的电子邮件，在Linux运行 `echo -n your@email.org | md5sum` 或在macOS运行 `echo -n your@email.org | md5` 获得`emailhash` 。

     
- create an blog entry under [_posts](https://github.com/quarkusio/quarkusio.github.io/tree/main/_posts)

  - the file name is `yyyy-mm-dd-slug.adoc` Set the date to the same value in the asciidoc preamble.

- `tags` 应该谨慎使用，因为存档页面是为它们创建的。以下是一些你可以尝试遵循的基本规则：

  - `quarkus-release` 用于Quarkus发布博客

  - `announcement` 用于具有一定影响的一般公告。

  - `extension` 用于与特定扩展相关的博客。

  - `user-story` 用于用户/公司采用Quarkus的故事。

  - `development-tips` 用于带有使用Quarkus或Quarkus本身开发提示的博客。 

  - 如果你的帖子与该技术有显著的相关性，可以添加一个技术细节，比如 `kafka`。

  - 标记是由空格分隔的列表 `tags:extension grpc`

  - 标签必须英文小写

- it's in asciidoc format, there is an example as shown with [2019-06-05-quarkus-and-web-ui-development-mode.adoc](https://github.com/quarkusio/quarkusio.github.io/blob/main/_posts/2019-06-05-quarkus-and-web-ui-development-mode.adoc)

  - Be aware that the `date` attribute in the asciidoc preamble defines when the article will be published. Add a `--future` flag when testing locally to ensure the article is included in the generated site. 

- send a pull request against the main branch and voilà




## Translations/Localization (l10n)

The primary site (quarkus.io) is written in English. 

There are separate repositories for community driven localized versions of quarkus.io:

- [ja.quarkus.io](https://github.com/quarkusio/ja.quarkus.io) for Japanese

- [cn.quarkus.io](https://github.com/quarkusio/cn.quarkus.io) for Chinese (simplified)

- [es.quarkus.io](https://github.com/quarkusio/es.quarkus.io) for Spanish

- [pt.quarkus.io](https://github.com/quarkusio/pt.quarkus.io) for Brazilian Portuguese


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

Please read [CONTRIBUTING.md](https://github.com/quarkusio/quarkusio.github.io/tree/main/CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

**重要：** 指南保存在主Quarkus仓库中，合并请求应该提交到那里：
https://github.com/quarkusio/quarkus/tree/main/docs/src/main/asciidoc.

## 许可证

本网站是根据 [知识共享署名许可协议 3.0](https://creativecommons.org/licenses/by/3.0/) 维护。
