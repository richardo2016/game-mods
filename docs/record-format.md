# 记录格式

每条 mod 记录由两个文件组成：`mod.json`（机读）和 `README.md`（人读）。两者必须一致，冲突时以实际验证结果为准并同时修正。

## 路径

```
mods/<game-slug>/<mod-slug>/mod.json
mods/<game-slug>/<mod-slug>/README.md
```

- `<game-slug>`：小写、连字符，例如 `phantom-blade-zero`。
- `<mod-slug>`：小写、连字符，尽量贴近 mod 原名，例如 `map-collectible-markers`。

## mod.json 字段

| 字段 | 必填 | 说明 |
| --- | --- | --- |
| `id` | ✅ | 与目录名一致 |
| `game` | ✅ | 所属 `<game-slug>` |
| `name` | ✅ | mod 显示名 |
| `type` | ✅ | `pak` / `script-mod` / `loader` / `patch` / `tool` |
| `source.site` | ✅ | 来源站点，例如 `nexusmods` |
| `source.url` | ✅ | 原始页面链接 |
| `source.author` | ✅ | 作者署名 |
| `version` | ✅ | mod 版本号（原样照抄，不改写） |
| `variant` | | 同一版本的不同变体，例如 `fog` / `teleport` |
| `gameBuild` | ✅ | 验证时对应的游戏构建号 |
| `requires` | | 依赖数组：`id` / `version` / `url` |
| `installedAt` | ✅ | 首次安装日期 `YYYY-MM-DD` |
| `status` | ✅ | `recorded` / `verified` / `broken` / `deprecated` |
| `files` | ✅ | 安装产物：`path`（用 `<game-root>` 占位）/ `sha256` / `bytes` |
| `verify` | ✅ | 进游戏后的验证步骤，逐条可观察 |
| `uninstall` | ✅ | 卸载步骤，写清删哪些路径 |
| `notes` | | 已知问题、冲突、版本敏感点 |

## 状态含义

| 状态 | 含义 |
| --- | --- |
| `recorded` | 只记录了安装方式，还没实测 |
| `verified` | 实测通过，`verify` 里每一条都确认过 |
| `broken` | 当前游戏版本下不工作，`notes` 必须写原因 |
| `deprecated` | 有新版本或新方案替代，仅作历史参考 |

## 版本历史

一个 mod 只有**一个目录**，不按版本开子目录。版本差异靠下面两条分工：

| 位置 | 内容 |
| --- | --- |
| `mod.json` 的 `version` / `files` | 只描述**当前这一份**安装状态，唯一版本 |
| `README.md` 的 `## 版本备注` | 全量历史，一行一版 |

版本备注表的固定列：

| 版本 | 日期 | 说明 |
| --- | --- | --- |
| 1.8.0 | 2026-11-04 | 改用加载器形态，功能与 1.7.3 持平 |
| 1.7.3 及更早 | — | pak 形态，当前游戏版本下失效 |

升级时的顺序：

1. 先把旧版本的结论写进版本备注（为什么被替换、在哪个构建号下失效）。
2. 再改 `mod.json` 的 `version`、`files`（新路径与新 SHA256）和 `gameBuild`。
3. 重跑 `verify`，通过后保持 `status: "verified"`；不通过改成 `broken` 并在备注里写原因。

旧信息不要删。同一个 mod 的"哪个版本为什么不能用"，往往比"现在能用的那个"更值钱。

## 示例

```json
{
  "id": "example-mod",
  "game": "example-game",
  "name": "Example Mod",
  "type": "script-mod",
  "source": {
    "site": "nexusmods",
    "url": "https://www.nexusmods.com/examplegame/mods/1",
    "author": "SomeAuthor"
  },
  "version": "1.0.0",
  "gameBuild": "12345678",
  "installedAt": "2026-01-01",
  "status": "verified",
  "requires": [
    { "id": "example-loader", "version": ">=0.1.0", "url": "https://example.com/loader" }
  ],
  "files": [
    {
      "path": "<game-root>/Mods/ExampleMod/main.js",
      "sha256": "0000000000000000000000000000000000000000000000000000000000000000",
      "bytes": 1234
    }
  ],
  "verify": [
    "启动游戏无报错弹窗",
    "按 F 打开面板"
  ],
  "uninstall": [
    "删除 <game-root>/Mods/ExampleMod"
  ],
  "notes": []
}
```

## README.md 建议结构

```markdown
# <mod 名称>

一句话说明它做什么。

## 来源
## 依赖
## 安装
## 验证
## 卸载
## 已知问题
## 版本备注
```
