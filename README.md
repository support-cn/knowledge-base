# 文档仓库说明

本仓库用于维护知识库站点的 Markdown 文档内容。

它会被主工程仓库以 Git Submodule 的方式接入到 `docs/` 目录中，因此这里主要负责内容，不负责站点配置和主题代码。

## 仓库职责

- 负责维护 Markdown 文档内容
- 负责维护文档中使用的图片、附件等静态资源
- 不负责 VitePress 的导航、侧边栏、主题、构建配置

## 关联仓库

- 文档仓库：当前仓库
- 主工程仓库：`https://github.com/support-cn/kb-src.git`

主工程通过 VitePress 的 `srcDir: './docs'` 读取这里的内容。

同时，主工程已经通过 `srcExclude: ['**/README.md']` 排除了本文件，所以这个说明文件不会被当成站点页面渲染。

## 日常修改流程

### 1. 拉取最新内容

```bash
git checkout main
git pull origin main
```

### 2. 修改文档

在当前仓库中直接修改 Markdown、图片或附件内容。

### 3. 提交并推送文档仓库

```bash
git add .
git commit -m "docs: update knowledge base content"
git push origin main
```

### 4. 回到主工程更新子模块指针

文档仓库推送完成后，还需要回到主工程仓库执行：

```bash
git add docs
git commit -m "chore: bump docs submodule"
git push
```

否则其他人在拉取主工程仓库时，拿到的仍然会是旧的文档版本。

## 修改范围说明

适合在当前仓库修改的内容：

- `.md` 文档页面
- 文档图片
- 附件资源
- 文档内部链接

不建议在当前仓库修改的内容：

- VitePress 导航
- VitePress 侧边栏
- 主题样式
- 搜索配置
- 构建脚本

这些内容应在主工程仓库中维护。

## 新增页面时的注意事项

如果这里只新增了 Markdown 文件，页面内容虽然已经存在，但不代表站点导航一定会自动展示。

新增页面后，请同时检查主工程仓库中的以下配置是否需要更新：

- `.vitepress/config.mts` 中的 `nav`
- `.vitepress/config.mts` 中的 `sidebar`

## 协作建议

- 提交文档前先同步远端最新内容，减少冲突
- 尽量使用清晰的文件命名和目录结构
- 文档仓库提交完成后，记得同步更新主工程中的 submodule 指针

这样后续同事在主工程中执行子模块更新时，才能拿到正确版本的文档内容。
