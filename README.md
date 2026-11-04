# Game Mods

安装记录仓库：某个游戏装过哪些 mod、装在哪、怎么验证、怎么卸载。

**这里只记录过程，不分发 mod。** 第三方 mod 的版权属于各自的作者，二进制一律不进本仓库，只留来源链接和校验值。

## 目录结构

```
mods/
  <game-slug>/
    README.md                 游戏级说明：引擎、mod 生态、版本敏感点
    <mod-slug>/
      README.md               人读：安装、验证、卸载、已知问题
      mod.json                机读：来源、版本、依赖、文件校验值
```

## 一条记录包含什么

| 项目 | 说明 |
| --- | --- |
| 来源 | 站点、游戏域名、mod id、作者、原始链接 |
| 版本 | mod 版本 + 对应的游戏构建号 |
| 依赖 | 加载器/框架及其最低版本 |
| 安装位置 | 用 `<game-root>` 占位，只写相对结构 |
| 验证方式 | 进游戏后能观察到什么，怎么算成功 |
| 卸载方式 | 删哪些路径，是否可逆 |
| 已知问题 | 版本失效、冲突、杀软误报等 |

字段定义见 [`docs/record-format.md`](docs/record-format.md)。

## 收录原则

- 只收录**实际验证过**的安装记录，没跑起来的写在 `status: "broken"` 里并注明原因。
- 记录要能被人照着复现，不能只有"装好了"三个字。
- 游戏更新后先判断 mod 形态是否失效，再决定要不要照旧记录。

## 隐私

仓库公开，因此**不含**任何个人路径、账号、机器名或凭据。所有本地路径统一写成 `<game-root>` 这类占位符。协作规则见 [`AGENTS.md`](AGENTS.md)。

## 已有记录

- [Phantom Blade Zero](mods/phantom-blade-zero/README.md)
  - [PBZModLoader](mods/phantom-blade-zero/pbz-mod-loader/README.md) — 脚本 mod 加载器
  - [Map Collectible Markers](mods/phantom-blade-zero/map-collectible-markers/README.md) — 地图收集品标记
