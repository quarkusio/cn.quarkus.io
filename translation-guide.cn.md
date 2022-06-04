# cn.quarkus.io 翻译项目翻译指南
cn.quarkus.io 翻译项目正在翻译[quarkus.io](https://quarkus.io)。

## 翻译方法
[quarkus.io](https://quarkus.io)是一个使用 Jekyll 的静态站点，其内容由 asciidoctor (.adoc) 描述。该存储库位于[quarkusio/quarkusio.github.io](https://github.com/quarkusio/quarkusio.github.io )，并在 CC BY 3.0 下发布。在这个项目中，我们使用名为 po4a 的实用程序从 .adoc 文件中提取文本，对其进行翻译，将其写回 .adoc 文件，然后构建它以构建一个中文版网站。该存储库使用 po4a 提取文本、运用翻译记忆库翻译应用程序、机器翻译起草和回写处理的 GitHub Actions工作流自动动化地提取、管理和翻译文本。翻译结果保存在[l10n目录](l10n)。

## 对翻译的贡献
如果您愿意为翻译做出贡献，请在本地克隆此存储库，编辑手头[l10n目录](l10n)下的 .po 文件，然后发送 Pull-Request。您可以在[此处](l10n/stats/translation.csv)查看每个文件的翻译状态。

## 开始翻译的声明
为了避免多个成员同时处理同一个文件和重复劳动，您在开始翻译工作时请使用 GitHub Issue 声明工作开始于哪个文件或范围。当您准备提出Issue时，请检查是否有人已经在现有Issue中声明了同样目的的工作。

### 翻译工作
.po 文件是一个文本文件，各种翻译辅助工具都支持编辑。例如[POEdit](https://poedit.net/)兼容运行在Windows/Mac/Linux，编辑使用方便，全面支持快捷键。

### 翻译目标的自动导入和翻译
待翻译的文件会在[quarkus.io](https://quarkus.io)更新后定期通过GitHub Actions的工作流自动进入本仓库，并生成.po文件。.po文件中会插入翻译存储器中收录的译文，以及使用[quarkus-adoc-po-translator](https://github.com/doc-l10n-kit/quarkus-adoc-po-translator)用DeepL API自动翻译的译文，请作为翻译时的基础来使用。

因为说到底是机器翻译，很多不通顺和不准确的部分被标记为“需要确认”(fuzzy)，只要不去掉“需要确认”标记，翻译的内容就不能被发布。所以，请大家审核并修改译文，去掉“需要确认”的标记。

### 待翻译文件
最终目标是翻译[l10n目录](l10n) 下的所有.po文件，目前优先考虑围绕 [l10n/po/zh_CN/_guides目录](l10n/po/zh_CN/_guides)和[l10n/po/zh_CN/_posts目录](l10n/po/zh_CN/_posts)翻译网站的“手册”和“博客”这些主要内容，后续再翻译其他内容。

请注意可能有多个版本的指南手册在 [l10n/po/zh_CN/_versions目录](l10n/po/zh_CN/_versions)，虽然我们可以在审核合并译文后，自动更新其中的大部分内容，但还是有可能存在部分内容没有翻译，所以希望您能在网站重新部署后，及时查看不同版本下的手册内容，确保都已经正确翻译。

### 免翻译语句的处理
.po 文件可能包含不需要完整翻译的句子，例如源代码和 URL。在这种情况下，无需照原样复制原始文本。请把翻译留空。然后将按原样使用原始文本。

### 翻译细节注意事项
请参考[我们的讨论](https://github.com/quarkusio/cn.quarkus.io/discussions/62)

### 翻译结果预览
当您翻译好.po文件，发送Pull-Request，然后自动在GitHub Actions中建立网站，并在5分钟内发送针对Pull-Request的临时浏览URL。您可以灵活运用临时网站确认翻译结果的预览，来验证翻译效果。

### HTML模板更新支持/翻译
quarkus.io 的内容是用 asciidoctor (.adoc) 编写的，但 Jekyll 的 HTML 模板中包含一些文本。由于无法用 po4a 对 Jekyll 的 HTML 模板中编写的文本进行编程，所以将 po4a 无法处理的文件的副本放在[l10n/override 目录](l10n/override)下并手动翻译此文件，Jekyll 本地化是通过覆盖原始文件来实现的在构建站点时使用这些文件。如果上游侧更新了原始文件，那么复制到[l10n/override目录](l10n/override)侧的文件也需要更新。请注意，现在没有检测并通知上游侧原始文件更新的功能。
