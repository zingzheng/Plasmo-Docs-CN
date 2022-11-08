# Tab Pages

> 源文档 [Browser Extension SDK/Tab Pages](https://docs.plasmo.com/browser-extension/tab-pages)

## Tab Pages

> 译：暂称为标签页 或者 Tab页

标签页是 Plasmo 框架独有的功能。不同于 [扩展页面](https://docs.plasmo.com/browser-extension), 标签页只是您的扩展包附带的常规网页。扩展通常从扩展页面以编程方式重定向到或打开这些页面。当您想要更精细的路由设置或用于身份验证的专用页面时，请使用标签页。

添加标签页：

1. 在源码目录创建 `tabs` 文件夹 （根目录或 `src`）
2. 创建一个 `.tsx` 文件，例如 `delta-flyer.tsx`
3. 导出一个default的 React 组件：

```
function DeltaFlyerPage() {
  return (
    <div
      style={{
        display: "flex",
        flexDirection: "column",
        padding: 16
      }}>
      <h2>Delta Flyer Tab</h2>
 
      <p>This tab is only available on the Delta Flyer page.</p>
    </div>
  )
}
 
export default DeltaFlyerPage
```

您的标签页将在扩展包中的 /tabs 路径下。它可以在浏览器中使用如下url进行访问：

```
chrome-extension://<extension-id>/tabs/delta-flyer.html
```

![tab page](https://docs.plasmo.com/screenshots/2022-09-25-22-18-58.png)

更多细节查看 [rfc-182](https://github.com/PlasmoHQ/plasmo-test/tree/main/rfc/rfc-182-tabs)
