# PBZModLoader

Phantom Blade Zero 的 JavaScript / TypeScript 脚本 mod 加载器，基于游戏自带的 PuerTS 运行时。它本身不带玩法，只是给其他 mod 提供宿主。

## 来源

- Nexus Mods：<https://www.nexusmods.com/phantombladezero/mods/113>
- 作者：LLKKFF
- 版本：0.3.6-preview（针对 2026-11-04 游戏更新的兼容修复版）

## 依赖

无。mod 反过来依赖它。

## 安装

1. 退出游戏。
2. 把主压缩包**直接解压到含 `ProjectPBZ` 的游戏根目录**，合并 `ProjectPBZ` 与 `platform`，不要多套一层文件夹。
3. 确认代理 DLL 与实际游戏主程序同目录（Steam 版为 `<game-root>/platform/steam/version.dll`，旁边就是 `PBZ.exe`）。
4. 正常从平台客户端启动游戏。

解压后应得到：

```
<game-root>/platform/steam/version.dll
<game-root>/ProjectPBZ/Content/JavaScript/PBZModLoader/bootstrap.js
<game-root>/ProjectPBZ/Content/JavaScript/PBZModLoader/manager.js
<game-root>/ProjectPBZ/PBZModLoader/compiler/tsc.exe
<game-root>/ProjectPBZ/PBZModLoader/mods.ini
<game-root>/ProjectPBZ/PBZModLoader/mods/<mod-id>/main.js
```

## 验证

- 游戏能正常启动到主菜单，没有初始化异常。
- 装了至少一个 mod 时，`<game-root>/ProjectPBZ/PBZModLoader/evidence/<本次运行>/loader.log` 里 `loaded` 计数大于 0。

## 卸载

删除三处：代理 DLL、`ProjectPBZ/PBZModLoader`、`ProjectPBZ/Content/JavaScript/PBZModLoader`。不要删整个 `Content/JavaScript` 目录，里面还有游戏自己的脚本。

## 已知问题

- **预览版**。游戏每次更新都可能需要跟进新版加载器，作者会标在版本说明里。
- `version.dll` 是注入型代理 DLL，部分杀软会报可疑或直接拦截。确认来源是官方发布页之后，再决定是否加排除项；不要从第三方转载站拿这个文件。
- 与"备用入口" DLL（`hid.dll` / `winmm.dll` / `dsound.dll` / `dxgi.dll`）互斥：同一个游戏目录只能放一个加载器入口，且必须保持原文件名。
- mod 目录名只允许字母、数字、下划线、连字符。
- 热重载（Alt+F5）只在游戏前台生效，不会自动监听文件变化。

## 版本备注

| 版本 | 日期 | 说明 |
| --- | --- | --- |
| 0.3.6-preview | 2026-11-04 | 修复当日更新（构建号 26367565）导致的 mod 不加载与菜单初始化异常。当前记录对应此版 |
| 0.3.5-preview | — | 已由作者撤回，不要使用 |
