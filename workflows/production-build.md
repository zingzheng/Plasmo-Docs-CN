# Production Build

> 源文档 [Workflows/Production Build](https://docs.plasmo.com/workflows/build)

## 创建生产版本

要创建用于分发的生产包，请运行：

```
pnpm build
# OR
npm run build
```

### 生成 zip 压缩包

可以选择向 build 命令提供 `--zip` 标志，以创建准备好上传到网上商店的 zip 包：

```
pnpm build --zip
# OR
npm run build -- --zip
```

### 指定特定目标

`build` 命令接受 `--target` 标志。使用它来指定要构建的浏览器和 manifest 版本组合：

```
plasmo build --target=firefox-mv2
```

最终的包将在 `build/firefox-mv2-prod` 目录中。

官方支持的目标列表，[请查看我们官方支持的浏览器目标章节](https://docs.plasmo.com/workflows/faq#what-are-the-officially-supported-browser-targets)。

### 添加 source maps

默认情况下，Plasmo 不会为您的生产包生成 source map。但是，您可以使用 --source-maps 标志来更改此行为：

```
plasmo build --source-maps
```
