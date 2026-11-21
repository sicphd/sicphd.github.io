# sicphd 首页维护说明

网站：https://sicphd.github.io/  
网站代码：https://github.com/sicphd/sicphd.github.io

## 当前设计

只有一个首页，标题为 sicphd，下方简单罗列内容仓库，不再区分 Resources 或 Projects，不设导航。当前列出 control-book 和 IELTS-Study；网站自身的代码仓库通过页脚 Source 链接访问。

## 添加、删除或调整仓库

在网站仓库中编辑 `_data/repositories.yml`。例如：

```yaml
- name: control-book
  url: https://github.com/sicphd/control-book
- name: IELTS-Study
  url: https://github.com/sicphd/IELTS-Study
- name: example-repository
  url: https://github.com/sicphd/example-repository
```

最后一项仅为格式示例，确认仓库存在且公开后再添加。每项由 name（显示名称）和 url（链接）组成；按文件中的顺序显示。删除对应两行即可移除入口，调整条目顺序即可排序。不要填写另一账号的资料。

**新建 GitHub 仓库不会自动出现在首页。** 需要把入口加入此文件并提交到 main 分支。首页是静态列表，不依赖浏览器请求 GitHub API。

## 上传文件、图片、Markdown 或 PDF

直接到对应内容仓库上传文件，例如教材放在 control-book、雅思资料放在 IELTS-Study。首页点击仓库名称后进入该仓库查看文件，不在首页逐个列出文件。

Markdown 与图片可放在同一仓库，使用相对路径引用，例如 `![示意图](images/diagram.png)`；同时上传图片并保持文件名大小写一致。PDF 可以用 `[阅读 PDF](papers/note.pdf)` 链接。GitHub 会按其支持的格式预览文件。

网站仓库的 files/ 目录不再自动显示在首页，已有文件不删除。需要引用时添加明确的链接，或将内容维护在对应仓库中。

## 修改标题和样式

- `index.html`：首页标题和列表结构。
- `_data/repositories.yml`：首页仓库入口。
- `assets/css/group.css`：字体、宽度、间距、颜色和手机样式。
- `_layouts/default.html`：网页标题、页脚、样式引用。
- `_config.yml`：站点地址和描述。

修改 CSS 后，可同步更新 default.html 中样式链接的版本参数，帮助浏览器刷新缓存。旧栏目地址保留跳转到首页；不重新创建导航或分类。

## 发布与检查

在 GitHub 中提交到 main 后，等待 Actions 中 pages build and deployment 成功，再刷新网站。检查两个仓库链接和手机布局。如果未更新，先确认提交位于网站仓库 main 分支、部署成功，再强制刷新浏览器。

本次改版只调整网站展示，不修改内容仓库，不搬运其他账号的内容。保留 LICENSE 和 NOTICE.md 中的许可证及来源说明。
