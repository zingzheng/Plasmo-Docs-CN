# Content Scripts

> 源文档 [Browser Extension SDK/Content Scripts](https://docs.plasmo.com/browser-extension/content-scripts)

## Content Scripts

Content Scripts 运行在web页面上下文的一个"独立世界"中。这使得来自各种扩展的多个Content scripts可以共存，而不会在执行中相互冲突。

#### 用例：

* 从当前网页抓取数据
* 从当前网页中选择、查找和样式化元素
* [将 UI 元素注入当前网页](https://docs.plasmo.com/browser-extension/content-scripts-ui)
* [将代码注入"主世界"上下文](https://docs.plasmo.com/browser-extension/content-scripts#injecting-into-the-main-world)

### 新增一个简单的content script

> **注意：** 由于 Plasmo 的默认 Typescript 配置将所有源文件视为模块，如果您的代码中没有任何导入或导出，您必须在文件的开头添加 `export {}`。(创建第一个content script 时，您将看到此警告！)

创建一个导出空对象的 `content.ts` 文件

```
export {}
console.log(
  "You may find that having is not so pleasing a thing as wanting. This is not logical, but it is often true."
)
```

刷新浏览器并打开任何网页，然后打开其检查器(控制台)：

![content script](https://docs.plasmo.com/screenshots/2022-09-26-11-01-08.png)

完整例子请查看 [with-content-script](https://github.com/PlasmoHQ/examples/tree/main/with-content-script)

### 添加多个 content scripts

为多个content script创建 `contents` 目录，并在其中添加您的`content script`。确保他们的名字描述了他们的作用！

有关示例，请参见 [with-many-content-scripts](https://github.com/PlasmoHQ/examples/tree/main/with-many-content-scripts)

### 配置

有时，您希望在特定页面上运行 content script。您可以通过从 content script 导出配置对象来提供自定义配置：

```
import type { PlasmoContentScript } from "plasmo"
 
export const config: PlasmoContentScript = {
  matches: ["<all_urls>"],
  all_frames: true
}
```

通过 `PlasmoContentScript` 类型，使用此配置对象变得轻而易举 🥳。

要了解有关配置和每个属性的更多信息，[check out Chrome's official documentation](https://developer.chrome.com/docs/extensions/mv3/content\_scripts/#static-declarative)

### 注入"主世界"

如果您希望在 content script 访问 `window` 对象， 你必须将代码注入到"主世界"。

目前无法通过 `content_scripts` mainifest 字段以声明方式将内容脚本注入主世界。

相反，Chrome 提供了一个 `chrome.scripting.executeScript API`，让您可以将 content script 注入主世界。首先，将 scripting 权限添加到您的 manifest 中：

```
{
  "permissions": ["scripting"]
}
```

然后，通过从后台 service worker 调用 `chrome.scripting.executeScript` 将您的content script注入主世界：

```
chrome.scripting.executeScript(
  {
    target: {
      tabId // the tab you want to inject into
    },
    world: "MAIN", // MAIN to access the window object
    func: windowChanger // function to inject
  },
  () => {
    console.log("Background script got callback after injection")
  }
)
```

对于 `func` ，您可以从项目中传入一个 Typescript 函数，当您的扩展打包时，该函数会自动转换为 JavaScript 函数。

有关示例，请参见 [with-main-world-content-script-injection](https://github.com/PlasmoHQ/examples/tree/main/with-main-world-content-script-injection)

### 导入资源

要将外部资源导入您的content script， 您可以使用 [`url:`方案：](https://docs.plasmo.com/browser-extension/import#url)

```
import myFile from "url:./path/to/my/file/something.js"
```

`url:` 方案将自动解析 something.js 资源并将其添加到构建包中的 web\_accessible\_resources 声明中。上面的 `myFile` 变量将是一个包含目标资源 URL 的字符串：

```
> console.log(myFile)
 
chrome-extension://<your chrome ext id>/something.eb20bc99.js?1656000646313
```

或者，您可以使用 `data-base64` 或 `data-text` 方案将资源直接导入并嵌入到您的代码中。对于小资源，这些方案应该运作良好。

> 注意：请参阅 [有关 \~ 导入解析的说明](https://docs.plasmo.com/workflows/faq#tilde-import-resolution)
