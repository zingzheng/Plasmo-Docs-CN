> 源文档 [Framework](https://docs.plasmo.com/)

# Plasmo 框架

[Plasmo](https://www.plasmo.com/) 框架是骇客为骇客制作的一个强力的浏览器扩展 SDK。构建您的产品，无需担心配置文件编写和构建浏览器扩展时的奇怪特性。

> 它就像浏览器扩展界的 [Next.js](https://nextjs.org/) ！

![CLI Demo](https://www.plasmo.com/assets/plasmo-cli-demo.gif)

## 特性

* 对 [React](https://reactjs.org/) + [Typescript](https://www.typescriptlang.org/) 的一等支持
* [声明式开发](https://docs.plasmo.com/#where-is-the-manifestjson-file)
* [Content Scripts UI](https://docs.plasmo.com/csui)
* [Tab Pages](https://docs.plasmo.com/browser-extension/tab-pages)
* 热重载
* [`.env*` 文件](https://docs.plasmo.com/browser-extension/env)
* 适配[多种浏览器与其manifest](https://docs.plasmo.com/workflows/build#with-specific-target)
* [远程代码打包](https://docs.plasmo.com/workflows/remote-code) (例如：使用 gtag4 )
* [通过BPP自动部署](https://docs.plasmo.com/workflows/submit)
* 对 [Svelte](https://github.com/PlasmoHQ/with-svelte) 和 [Vue](https://github.com/PlasmoHQ/with-vue) 可选支持
* 还有更多! 🚀

## 系统要求

* Node.js 16.x 及以上
* MacOS，Windows，或 Linux
* (强烈推荐) [pnpm](https://pnpm.io/)

## 入门

```
pnpm create plasmo
# OR
yarn create plasmo
# OR
npm create plasmo
```

![file\_structure](https://docs.plasmo.com/screenshots/file\_structure.png)

上面的指令会为您创建一个最简单的 Plasmo 浏览器扩展项目。其目录结构简洁明了：

| 文件名               | 描述                                                                                                              |
| ----------------- | --------------------------------------------------------------------------------------------------------------- |
| `popup.tsx`       | 该文件导出默认的 React 组件，用于渲染扩展的popup页面。 _这就是您在扩展弹出窗口上所需的全部内容！_                                                        |
| `assets`          | Plasmo 会[自动生成一些小的图标](https://docs.plasmo.com/browser-extension/icon)并将它们从 "icon.png" 文件中配置到manifest中            |
| `package.json`    | 平时使用的 Node.js 项目的声明, 其中带有一个[可选的"manifest"属性，用于根据您的需要自定义 Plasmo](https://docs.plasmo.com/customization/manifest) |
| `.prettierrc.cjs` | 配置代码格式化                                                                                                         |
| `.gitignore`      | 老朋友 git ignore 文件                                                                                               |
| `README.md`       | 基础文档                                                                                                            |
| `tsconfig.json`   | TypeScript 配置                                                                                                   |

> 📢 **注意**：如果要在源码模块重使用 `src` 目录，请参考这个[指引](https://docs.plasmo.com/customization/src)

## 开发服务

要获得热加载支持，您需要同通以下命令来开启开发环境的服务：

```
pnpm dev
```

上述命令将监视文件更改并在 `build/chrome-mv3-dev` 中重新生成扩展包

## 生产构建

要打包正式环境扩展，使用：

```
pnpm build
```

这将在 `build/chrome-mv3-prod` 中创建扩展的生产环境版本

## 在 Chrome 中加载扩展

我们计划在未来将其自动化，但目前，这些是您在 Chrome 中加载扩展程序所需采取的步骤。

在浏览器打开 `chrome://extensions` 并激活开发者模式

![https://docs.plasmo.com/screenshots/developer\_mode](https://docs.plasmo.com/screenshots/developer\_mode.png)

点击"加载已解压的扩展程序(Load Unpacked)" 并定位到您的扩展程序的 `build/chrome-mv3-dev` （或 `build/chrome-mv3-prod`）目录

要查看您的popup页面，请单击 Chrome 工具栏上的拼图图标，然后单击您的扩展程序。

> 💡 **进阶技巧** 通过单击 pin 按钮将您的扩展程序固定到 Chrome 工具栏以便于访问。

![pin](https://docs.plasmo.com/screenshots/popup\_example.png)

## manifest.json文件在哪里？

Plasmo 已经将 manifest 文件抽象出来了。该框架根据您源码文件中使用的钩子和代码中导出的配置来自动生成 manifest，类似于 Next.js 使用文件系统和页面组件抽象页面路由和 SSG。

我们将进一步抽象自动权限和基于需求的权限方案，消除手动指定权限的需要！（很快推出）

## 下一步

查看[工作流程章节](https://docs.plasmo.com/workflows)，深入了解如何使用 Plasmo。每个工作流程都附带一个模块化示例，展示了框架的简单性。在我们的 [GitHub 仓库](https://github.com/PlasmoHQ/examples)中查看示例。

根据您对Plasmo的需求 查看[定制章节](https://docs.plasmo.com/customization)相关文档。

要了解如何将 Plasmo 与其他工具（例如 TailwindCSS 或 Firebase）集成，请查看[快速入门章节](https://docs.plasmo.com/quickstarts)中的示例列表。

## 社区

可以在 [Discord](https://www.plasmo.com/s/d) 找到 Plasmo 社区。这是获得 Plasmo 框架使用帮助的恰当渠道。

我们的 行为守则 适用于所有 Plasmo 社区频道。

## 使用Plasmo框架的项目

* [MICE](https://github.com/PlasmoHQ/mice)
