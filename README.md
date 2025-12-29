
# Jupiter Biome Config

**用途** ✅

本仓库包含 Jupiter 项目使用的 **Biome** 配置（`biome.json`）。此配置定义了代码格式化、静态检查、文件包含规则以及与 JavaScript/TypeScript 和 CSS 相关的约束与修复策略，旨在统一团队代码风格并提高代码质量。

---

## 主要内容 / Features 🔧

- 使用 `biome` 作为项目的格式化器和 linter。
- 预设了 **formatter**（缩进、行宽、引号风格等）和 **linter**（推荐规则、可疑代码规则、可及性 a11y 规则等）。
- 指定了要包含/排除的文件模式（`files.includes`），避免在二进制、构建产物或第三方包中运行检查。

---

## 快速上手 / Usage 🚀

1. 在项目中安装 Biome（若尚未安装）:

```bash
pnpm add -D @biomejs/biome
```

2. 在项目根目录放置本仓库的 `biome.json`（已包含在本包内），或将其内容合并到你的 `biome.json` 中。

3. 在 package.json 中添加脚本（可选）:

```json
"scripts": {
	"format": "biome format",
	"lint": "biome check"
}
```

然后运行:

```bash
pnpm run format
pnpm run lint
```

---

## 配置说明（关键点） 📋

- **files.includes**：控制 Biome 要检查的文件和要忽略的路径（例如 `node_modules`、`dist`、`build`、`coverage` 等）。
- **formatter**：设置缩进、行宽、换行、引号风格、尾逗号策略等。
- **linter.rules**：启用推荐规则并对特定规则覆盖（如 `noExplicitAny`、`noConsole` 等）。
- **overrides**：针对特定文件类型（如 `*.ts/tsx`）做更严格的规则（例如将 `noExplicitAny` 设置为 `error`）。

如果需要修改规则，以团队共识的方式更新 `biome.json` 并在必要时同步到各个子项目。

---

## 常见变更示例 / Example tweaks

- 将 TypeScript 文件中 `noExplicitAny` 升级为错误：

```json
"overrides": [
	{
		"includes": ["**/*.{ts,tsx}"],
		"linter": { "rules": { "suspicious": { "noExplicitAny": "error" } } }
	}
]
```

---

## 贡献 & 联系 🤝

欢迎提交 PR 或 issue 来改进配置。请在变更中说明动机和影响范围（例如会影响哪些包或 CI 步骤）。

---

## 许可

本仓库使用 **MIT License**，详情见 `package.json` 中的 `license` 字段。

---

## 参考

- Biome 官方文档: https://biomejs.dev/

