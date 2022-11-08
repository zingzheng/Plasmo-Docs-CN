> 源文档 [Workflows/Development Server](https://docs.plasmo.com/workflows/dev)

# 开启开发服务

设置项目后，进入你的项目目录并执行：

```
pnpm dev
# OR
npm run dev
# OR
plasmo dev
```

Plasmo 将为您的扩展创建一个开发包和一个实时重新加载的开发服务, 在文件更改时自动更新您的扩展包并在源代码更改时重新加载您的浏览器。它还在扩展名前面加上 `DEV |`并使图标变为灰度以区分开发包和正式包。

## 指定特定的目标（浏览器）

`dev` 命令接受 `--target` 标志。使用它来指定要开发的浏览器和 manifest 版本组合：

```
plasmo dev --target=firefox-mv2
```

最终的包将在 `build/firefox-mv2-dev` 目录中。

官方支持的目标列表，[请查看我们官方支持的浏览器目标章节](https://docs.plasmo.com/workflows/faq#what-are-the-officially-supported-browser-targets)。

## 移除 source maps

默认情况下，Plasmo 在开发期间为您的扩展生成 source maps。如果您需要禁用此功能，可以使用 --no-source-maps 标志：

```
plasmo dev --no-source-maps
```

当您的依赖项不能很好地与 source maps 一起使用时，这很有用。
