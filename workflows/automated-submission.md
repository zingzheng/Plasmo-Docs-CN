> 源文档 [Workflows/Automated Submission](https://docs.plasmo.com/workflows/submit)

# 提交扩展

Plasmo 框架附带一个方便的 GitHub Action，称为 [Browser Platform Publish](http://bpp.browser.market/) 或 BPP。此服务将自动将您的扩展发布到所有受支持的浏览器扩展市场。它默认需要手动触发运行，但更改其配置可以使其在每次推送时运行。

要开始发布您的 Plasmo 扩展，需要在 `keys.json` 文件配置 schema：

```
{
  "$schema": "https://raw.githubusercontent.com/PlasmoHQ/bpp/v2/keys.schema.json"
}
```

如果您的编辑器支持 [JSON 模式](https://json-schema.org/)，则此模式很有帮助。确保仅声明有效的提交凭据。否则，将失败。

> 注：归功于我们的老朋友 `.gitignore`, git 会忽略该文件。

请参阅此[token 指南](https://github.com/PlasmoHQ/bms/blob/main/tokens.md)以了解有关提交所需token的更多信息。最后的配置大概如下所示：

```
{
  "$schema": "https://raw.githubusercontent.com/plasmo-corp/bpp/v2/keys.schema.json",
  "chrome": {
    "clientId": "123",
    "refreshToken": "789",
    "extId": "abcd",
    "clientSecret": "efgh"
  },
  "edge": {
    "clientId": "aaaaaaa-aaaa-bbbb-cccc-dddddddddddd",
    "clientSecret": "abcdefg",
    "productId": "aaaaaaa-aaaa-bbbb-cccc-dddddddddddd",
    "accessTokenUrl": "https://login.microsoftonline.com/aaaaaaa-aaaa-bbbb-cccc-dddddddddddd/oauth2/v2.0/token"
  }
}
```

复制此配置，并将其添加到 名为 `SUBMIT_KEYS` 的 [github 仓库密钥](https://docs.github.com/en/actions/security-guides/encrypted-secrets#creating-encrypted-secrets-for-a-repository)

然后，在需要提交新的扩展版本时，在 GitHub 上手动触发action！
