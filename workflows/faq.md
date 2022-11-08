> 源文档 [Workflows/FAQ](https://docs.plasmo.com/workflows/faq)

# 工作流程常见问题

## 如何把 Plasmo 升级到最新版本

如果您使用 pnpm， 执行：

```
pnpm up -L plasmo
```

其他包管理器，你需要先删除 lock 文件，然后重新执行 install 命令来获得最新版本的 Plasmo。

或者，您可以通过升级 package.json 中的版本号， 然后运行 install 命令来手动固定 Plasmo 的版本。

## 如果出现报错怎么办？

请使用 --verbose 标志运行 plasmo 并将输出粘贴到[错误报告](https://docs.plasmo.com/bug)的日志部分。这将帮助我们以100倍的速度对问题进行定位 🙏。

## 官方支持的浏览器是什么？

官方支持的目标是：

* `chrome-mv3` (默认)
* `firefox-mv2`

任何chrome内核浏览器（例如：Edge，Brave，Opera等）都是支持的， 例如：

* `edge-mv3`
* `brave-mv3`
* `opera-mv3`

我们将尽快支持 `safari-mv3`, 查看这个 [issue](https://github.com/PlasmoHQ/plasmo/issues/233)
