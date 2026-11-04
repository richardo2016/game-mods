# Phantom Blade Zero（影之刃零）

S-GAME Studio，Steam 版。Unreal Engine 5，内容打包使用 IoStore（`.pak` + `.utoc` + `.ucas`）。

## mod 生态

这个游戏的 mod 有两条互不相干的路线，选一条，不要混装：

| 形态 | 位置 | 说明 |
| --- | --- | --- |
| pak 补丁 | `<game-root>/ProjectPBZ/Content/Paks/~mods/` | 传统 UE 补丁包，三件套 `.pak/.utoc/.ucas` |
| 脚本 mod | `<game-root>/ProjectPBZ/PBZModLoader/mods/<id>/main.js` | 需要 [PBZModLoader](pbz-mod-loader/README.md)，走游戏自带 PuerTS |
| Lua mod | `<game-root>/platform/steam/ue4ss/Mods/` | 需要 UE4SS |

## 版本敏感点

**2026-11-04 更新（构建号 26367565）之后，pak 形态的 mod 不再被加载。** 官方改了脚本校验，替换游戏脚本的 pak 会失效。同一时期各 mod 作者陆续把功能迁移到加载器形态，选 mod 时优先看更新时间。

这类更新之后不要直接沿用旧记录，先确认 mod 形态是否还有效。

## 已记录

| mod | 形态 | 状态 |
| --- | --- | --- |
| [PBZModLoader](pbz-mod-loader/README.md) | 加载器 | verified |
| [Map Collectible Markers](map-collectible-markers/README.md) | 脚本 mod | verified |

## 通用注意

- 装/卸 mod 前退出游戏。
- 加载器类 mod 依赖一个代理 DLL（如 `version.dll`）放在主程序同目录。它会被部分杀软当成可疑文件，属于注入型工具的通病；确认来源后再决定是否加排除项。
- 游戏更新后先看加载器有没有跟进版本，再判断 mod 本身。
