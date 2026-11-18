# lemon-paperplane-plugin-keymap-emacs

Lemon Paperplane 文件编辑器的 Emacs 快捷键方案（插件 id `keymap-emacs`）。商店插件（不内置，打进随 App 附带的离线商店）。

- editor/keymap-emacs.js：基于 @replit/codemirror-emacs 的 Emacs 键位（C-a/C-e/C-k、标记 C-SPC、剪切环 C-w/M-w/C-y…），另加 C-x C-s 保存、C-x s 全部保存、C-x C-f 快速打开、C-x b 切换标签、C-x k 关闭、M-g g 跳转行；叠加在平台默认方案之上。
- 没有业务逻辑：方案在 `plugin.json` 的 `contributes.keymaps` 里声明；这是纯声明插件：`plugin.json` 不写 `executable`，没有程序，内核从不启动进程。
- JSON 方案格式：`{"bindings": [{"key": "Cmd-d", "command": "deleteLine"}]}`，键名用 CodeMirror 写法（`Cmd`/`Ctrl`/`Alt`/`Shift`，不用 `Mod`，多键序列用空格分隔），`command` 取编辑器命令表 `lemon-paperplane-main/lemon-paperplane-main-editor/COMMANDS.md`。编辑器工程的 `npm test` 会检查方案里的命令都存在。
- module 方案由编辑器工程的 `node scripts/build-lang.mjs keymap-emacs` 生成（CodeMirror 运行时取自编辑器的 `window.cm`）。
