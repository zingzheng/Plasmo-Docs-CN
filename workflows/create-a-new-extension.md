# Create a New Extension

> 源文档 [Workflows/Create a New Extension](https://docs.plasmo.com/workflows)

## 创建一个新的扩展

> 📢 **注意**：如果要在源码模块重使用 `src` 目录，请参考这个[指引](https://docs.plasmo.com/customization/src)

要运行交互式初始化向导，请使用以下命令：

```
pnpm create plasmo
# OR
yarn create plasmo
# OR
npm create plasmo
```

要跳过命名提示，请提供名称作为参数：

```
pnpm create plasmo "My Awesome Extension"
# OR
yarn create plasmo "My Awesome Extension"
# OR
npm create plasmo "My Awesome Extension"
```

> ⭐ **注意**： 您可以使用 `pnpm i -g plasmo` 将 plasmo CLI 作为全局命令安装 (可用您最喜欢的包管理器替换pnpm)

### 特定的入口文件

默认项目只包含一个 (popup)\[https://docs.plasmo.com/browser-extension#adding-a-popup-page] 入口文件。但是，您可以通过使用 entry 参数和逗号分隔的入口文件列表来自定义入口，以包含在您的初始项目中。

要查看所有可用的入口文件，请查看此[目录](https://github.com/PlasmoHQ/plasmo/tree/main/packages/init/entries)。

要使用此标志，请选择您希望在项目中看到的入口文件，省略其扩展名，并将其提供给 --entry 标志：

```
pnpm create plasmo --entry=options,newtab,contents/inline
# OR
npm create plasmo -- --entry=options,newtab,contents/inline
```

上面的命令将会创建一个包含 多个[option 页面](https://docs.plasmo.com/browser-extension#adding-the-options-ui)，一个[newtab 页面](https://docs.plasmo.com/browser-extension#adding-a-new-tab-page) 和一个 [带有UI界面的内联content script页面](broken-reference)

> ⚠️ **注意**: `npm` 不会将参数传递给它的子命令。因此，在指定 plasmo 的参数和标志之前，您必须提供一个 -- 来。

### 带示例的模板

更强大的是，plasmo 可以基于我们[示例](https://github.com/PlasmoHQ/examples/)中的项目创建一个新项目。选择一个您想使用的示例，并在运行 `create plasmo` 命令时将其用为标志：

```
pnpm create plasmo --with-env
# OR
npm create plasmo -- --with-env
```

以上将使用您指定的 [with-env](https://github.com/PlasmoHQ/examples/tree/main/with-env) 示例生成一个项目。

### 加载扩展

我们计划在未来将其自动化，但目前，这些是您在 Chrome 中加载扩展程序所需采取的步骤。

在浏览器打开 `chrome://extensions` 并激活开发者模式

![https://docs.plasmo.com/screenshots/developer\_mode](https://docs.plasmo.com/screenshots/developer\_mode.png)

点击"加载已解压的扩展程序(Load Unpacked)" 并定位到您的扩展程序的 `build/chrome-mv3-dev` （或 `build/chrome-mv3-prod`）目录

要查看您的popup页面，请单击 Chrome 工具栏上的拼图图标，然后单击您的扩展程序

> 💡 **进阶技巧** 通过单击 pin 按钮将您的扩展程序固定到 Chrome 工具栏以便于访问。

![pin](https://docs.plasmo.com/screenshots/popup\_example.png)
