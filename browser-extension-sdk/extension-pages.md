# Extension Pages

> 源文档 [Browser Extension SDK/Extension Pages](https://docs.plasmo.com/browser-extension)

## 浏览器扩展页面

扩展页面是浏览器识别的内置页面。包括了扩展的 popup, options 和 newtab 页面。

### 添加 Popup 页面

Popup页面是一个小的对话框窗口，当用户单击浏览器工具栏中的扩展程序图标时会打开它。它是最常见的扩展页面类型。

创建一个导出默认 React 组件的 `popup.tsx` 文件或 `popup/index.tsx` 文件。这样，您的popup就可以使用了 🚀 ！

查看 [with-popup](https://github.com/PlasmoHQ/examples/tree/main/with-popup)

### 添加 Options UI

Option UI 页面旨在为扩展程序的设置和配置提供一个专门的地方。

创建 `options.tsx` 或 `options/index.tsx` 文件用于渲染options界面 👌

查看 [with-options](https://github.com/PlasmoHQ/examples/tree/main/with-options-ui)

### 添加 NewTab 页面

NewTab(新标签页)覆盖默认标签页，通常是浏览器向用户打招呼的方式。

创建一个 `newtab.tsx` 文件或一个 `newtab/index.tsx` 文件，Plasmo 会处理剩下的事情来渲染你的新标签页 🤘！

查看 [with-newtab](https://github.com/PlasmoHQ/examples/tree/main/with-newtab)
