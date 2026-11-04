# Map Collectible Markers

在地图上标出**尚未拾取**的收集品：黑石与琥珀碎片、忆之花、大宝箱、钥匙、挑战、未敲的钟、武器、饰品、药品、升级材料、信件与支线。悬停能看到获取途径，可按类别筛选，可追踪单个目标。

## 来源

- Nexus Mods：<https://www.nexusmods.com/phantombladezero/mods/134>
- 作者：PaulGao
- 版本：1.8.0，变体 **Fog**

## 依赖

- [PBZModLoader](../pbz-mod-loader/README.md) 0.3.6-preview 或更新。1.8.0 起不再以 pak 形态发布，旧的 pak 版本在 2026-11-04 更新后失效。

## 安装

1. 装好 PBZModLoader。
2. 退出游戏。
3. 把 mod 压缩包解压到游戏根目录（含 `ProjectPBZ` 的那层），得到 `<game-root>/ProjectPBZ/PBZModLoader/mods/PBZMapMarkers/main.js`。
4. 在 `<game-root>/ProjectPBZ/PBZModLoader/mods.ini` 的 `[Mods]` 下加一行 `PBZMapMarkers=1`（不写也会被自动发现，写上便于单独开关）。

**同一时间只能装一个变体**：主文件 / Teleport / Fog / Fog Teleport。切换 = 换掉 `main.js` 一个文件。

## 变体区别

| 变体 | 雾区图标 | 点图标传送 |
| --- | --- | --- |
| 主文件 | 显示 | 无 |
| Teleport | 显示 | 有 |
| Fog | 隐藏，清雾后出现 | 无 |
| Fog Teleport | 隐藏，清雾后出现 | 有 |

Fog 适合不想被提前剧透、只想补漏的玩法：清完雾才知道这片区域还剩什么。

## 验证

- 打开地图，未拾取的收集品是图标（Fog 变体下，未清雾区域不显示）。
- `F`：筛选面板，逐类开关，最下方可调图标大小。
- `H`：隐藏 / 恢复全部图标（仅本次游戏会话有效）。
- 对着图标按 `V`：世界里出现追踪标记与距离，拾取后自动结束。
- 手柄：`d-pad ↓` 隐藏开关，`View/Touchpad` 面板，`L3` 追踪。

## 卸载

- 1.8.0：删除 `<game-root>/ProjectPBZ/PBZModLoader/mods/PBZMapMarkers`。
- 旧 pak 版：删除 `~mods` 下的 `PBZMapMarkers_P.pak/.utoc/.ucas`。

不写存档，随时可加可删。

## 已知问题

- 与 UE4SS 版不能共存，会重复显示图标。
- 旧 pak 版本（≤1.7.3）在 2026-11-04 更新后不再加载。
- 游戏改动地图脚本的更新可能让图标失效，需等 mod 跟进；加载器本身也可能需要更新。
- 收集品位置来自游戏自身数据，不覆盖任务/ NPC 直接给的信件（世界里没有落点的那种）。
- 幻术师遗迹的物品画在梅谷湖地图上，同一位置地表可能什么都没有。

## 版本备注

| 版本 | 日期 | 说明 |
| --- | --- | --- |
| 1.8.0 | 2026-11-04 | 因当日更新改用 PBZModLoader 形态，功能与 1.7.3 持平。当前记录对应此版 |
| 1.7.3 及更早 | — | pak 形态，构建号 26367565 起失效 |
