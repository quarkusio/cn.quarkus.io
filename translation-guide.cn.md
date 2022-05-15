# quarkus.io 翻译项目翻译指南
quarkus.io 翻译项目正在翻译[quarkus.io](https://quarkus.io)。

## 翻译方法
[quarkus.io](https://quarkus.io)是一个使用 Jekyll 的静态站点，其内容由 asciidoctor (.adoc) 描述。该存储库位于[quarkusio/quarkusio.github.io](https://github.com/quarkusio/quarkusio.github.io )，并在 CC BY 3.0 下发布。在这个项目中，我们使用名为 po4a 的实用程序从 .adoc 文件中提取文本，对其进行翻译，将其写回 .adoc 文件，然后构建它以构建一个中文版网站。使用 po4a 提取文本、使用翻译记忆库的翻译应用程序、机器翻译起草和回写处理的工作流程由该存储库的 GitHub Actions 自动化，提取的文本管理翻译文本。它保存在[l10n目录](l10n)。

## 对翻译的贡献
如果您愿意为翻译做出贡献，请在本地克隆此存储库，编辑手头[l10n目录](l10n)下的 .po 文件，然后发送 Pull-Request。您可以在[此处](l10n/stats/translation.csv)查看每个文件的翻译状态。

## 开始翻译的声明
为了避免多个成员同时处理同一个文件和重复工作时的浪费，开始翻译工作时，请使用 GitHub Issue 开始工作于哪个文件或范围，请声明。相反，当您提出问题时，请检查是否有人已经在现有问题中声明了对目标的工作。

### 翻译工作
.po 文件是一个文本文件，但各种翻译辅助工具都支持编辑。例如[POEdit](https://poedit.net/)兼容Windows/Mac/Linux运行，快捷键范围广泛，编辑时使用方便。

### 翻译目标的自动导入和翻译
当[quarkus.io](https://quarkus.io)更新时，要翻译的文件会通过 GitHub Actions 的工作流程自动导入到此存储库中，并创建 .po 文件。存储在翻译记忆库中的现有译文和 DeepL API 使用[quarkus-adoc-po-translator](https://github.com/doc-l10n-kit/quarkus-adoc-po-translator)自动翻译的译文将被插入到 .po 文件中，因此请在翻译时将其用作翻译...

但是，由于是机器翻译，所以有很多不自然的部分，例如，并且标记为“需要确认”（模糊），除非“需要确认”标记被标记，否则不会反映为翻译。删除... 请检查并更正翻译并删除“需要确认”标记。

### 待翻译文件
最终目标是翻译[l10n目录](l10n) 下的所有.po文件，目前优先考虑围绕 [l10n/po/zh_CN/_guides目录](l10n/po/zh_CN/_guides)和[l10n/po/ja_JP/_posts目录](l10n/po/ja_JP/_posts)翻译网站的“手册”和“博客”这些主要内容，后续再翻译其他内容。

### 免翻译语句的处理
.po 文件可能包含不需要完整翻译的句子，例如源代码和 URL。在这种情况下，无需照原样复制原始文本。请把翻译留空。然后将按原样使用原始文本。

### 翻译结果预览
如果你翻译 .po 文件并得到一个 pull-request，该站点将使用 GitHub Actions 自动构建，并且您可以临时浏览该站点的 URL 将作为评论发送到 GitHub 上的 pull-request 大约 5分钟... 您可以从该临时站点查看翻译结果的预览，因此请使用它。

### HTML模板更新支持/翻译
quarkus.io 的内容是用 asciidoctor (.adoc) 编写的，但 Jekyll 的 HTML 模板中包含一些文本。由于无法用 po4a 对 Jekyll 的 HTML 模板中编写的文本进行编程，所以将 po4a 无法处理的文件的副本放在[l10n/override 目录](l10n/override)下并手动翻译此文件，Jekyll 本地化是通过覆盖原始文件来实现的在构建站点时使用这些文件。如果上游侧更新了原始文件，那么复制到[l10n/override目录](l10n/override)侧的文件也需要更新。请注意，现在没有检测并通知上游侧原始文件更新的功能。
