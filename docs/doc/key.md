# Rime 按键映射速查表 (Key Binding Reference)

在 Rime 的 `key_binder` 模块中，`accept` 和 `send` 字段支持以下标准按键定义。请注意按键名称**区分大小写**。

---

## 1. 修饰键 (Modifiers)
用于组合键配置，Rime 支持区分左右侧按键。

| 类别 | 按键名称 |
| :--- | :--- |
| **Shift** | `Shift_L`, `Shift_R`, `Shift_Lock` |
| **Control** | `Control_L`, `Control_R` |
| **Alt / Opt** | `Alt_L`, `Alt_R` |
| **系统键** | `Super_L`, `Super_R` (Win/Cmd), `Caps_Lock` |
| **其他** | `Meta_L`, `Meta_R`, `Hyper_L`, `Hyper_R` |

---

## 2. 功能与导航键 (Function & Navigation)
控制输入法翻页、光标移动及基本操作。

| 分类 | 按键名称 |
| :--- | :--- |
| **基础编辑** | `BackSpace` (退格), `Tab`, `Linefeed` (换行), `Clear`, `Delete`, `Insert` |
| **确认/取消** | `Return` (回车), `space` (空格), `Escape` (退出), `Pause`, `Sys_Req` |
| **翻页** | `Page_Up` (或 `Prior`), `Page_Down` (或 `Next`) |
| **导航** | `Up`, `Down`, `Left`, `Right` (方向键), `Home`, `End`, `Begin` |
| **其他** | `Select`, `Print`, `Execute`, `Undo`, `Redo`, `Menu`, `Find`, `Cancel`, `Help`, `Break` |

---

## 3. 符号按键 (Symbols)
在映射非字母数字的按键时，需使用以下标准名称。

| 符号 | Rime 名称 | 符号 | Rime 名称 |
| :--- | :--- | :--- | :--- |
| `!` | `exclam` | `[` | `bracketleft` |
| `"` | `quotedbl` | `\` | `backslash` |
| `#` | `numbersign` | `]` | `bracketright` |
| `$` | `dollar` | `^` | `asciicircum` |
| `%` | `percent` | `_` | `underscore` |
| `&` | `ampersand` | `` ` `` | `grave` |
| `'` | `apostrophe` | `{` | `braceleft` |
| `(` | `parenleft` | `\|` | `bar` |
| `)` | `parenright` | `}` | `braceright` |
| `*` | `asterisk` | `~` | `asciitilde` |
| `+` | `plus` | `,` | `comma` |
| `-` | `minus` | `.` | `period` |
| `/` | `slash` | `:` | `colon` |
| `;` | `semicolon` | `<` | `less` |
| `=` | `equal` | `>` | `greater` |
| `?` | `question` | `@` | `at` |

---

## 4. 数字小键盘 (Keypad)
小键盘区域的按键具有独立的 `KP_` 前缀。

| 分类 | 按键名称 |
| :--- | :--- |
| **数字** | `KP_0` - `KP_9` |
| **运算** | `KP_Add` (+), `KP_Subtract` (-), `KP_Multiply` (*), `KP_Divide` (/), `KP_Decimal` (.) |
| **导航** | `KP_Up`, `KP_Down`, `KP_Left`, `KP_Right`, `KP_Home`, `KP_End`, `KP_Begin` |
| **翻页** | `KP_Page_Up` (或 `KP_Prior`), `KP_Page_Down` (或 `KP_Next`) |
| **其他** | `KP_Space`, `KP_Tab`, `KP_Enter`, `KP_Delete`, `KP_Insert`, `KP_Equal` |

---

## 5. 配置示例 (YAML)
在 `default.custom.yaml` 中应用映射的语法参考：

```yaml
key_binder:
  bindings:
    # 使用 Control + 句号 切换中英文标点
    - { accept: "Control+period", toggle: ascii_punct, when: always }
    # 使用分号下翻页
    - { accept: semicolon, send: Page_Down, when: has_menu }
    # 将小键盘回车映射为普通回车
    - { accept: KP_Enter, send: Return, when: composing }