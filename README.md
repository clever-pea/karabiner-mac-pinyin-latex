# Mac 自带拼音输入法 LaTeX 符号修复 (Karabiner-Elements)

在使用 macOS 自带的“简体拼音”输入法编写 LaTeX 时，按下 `Shift + 4` 会默认输出全角的 `¥` ，而不是 `$`，按下 `\` 会输出 `、` 等等。这极其影响 LaTeX 公式编辑的效率。

本项目提供了一个基于 [Karabiner-Elements](https://karabiner-elements.pqrs.org/) 的极简、稳定的解决方案。

## 原理说明

通过 Karabiner-Elements 的 `complex_modifications` 规则，在按下特定按键的瞬间，执行以下底层操作：
1. 瞬间切换到英文输入法。
2. 等待 30 毫秒（给系统输入法引擎反应时间）。
3. 输出对应的原生英文字符（如 `$`, `\`, `_`, `^`, `{`, `}`, `<`, `>`）。
4. 等待 30 毫秒。
5. 瞬间切回中文（简体拼音）输入法。

全程在几十毫秒内完成，完全无感。

## 支持修复的符号

* `$` (Shift + 4)
* `\` (Backslash)
* `^` (Shift + 6)
* `_` (Shift + Hyphen)
* `{` (Shift + Open Bracket)
* `}` (Shift + Close Bracket)
* `<` (Shift + Comma)
* `>` (Shift + Period)

## 安装与使用指南

确保你已经安装了 [Karabiner-Elements](https://karabiner-elements.pqrs.org/)。

### 方法一：下载文件（推荐）
1. 下载本项目中的 `mac_pinyin_latex_fix.json` 文件。
2. 按下 `Cmd + Shift + G`，前往 `~/.config/karabiner/assets/complex_modifications/`。
3. 将文件放入该文件夹中，然后在 Karabiner-Elements 中 Enable。

### 方法二：直接复制配置
如果你熟悉 Karabiner 的高级配置，可以直接将以下 JSON 粘贴到你现有规则的 `rules` 数组中：

```json
{
    "description": "macOS自带拼音：LaTeX 全套常用符号无感切英文输出 (含30ms延迟)",
    "manipulators": [
        {
            "conditions": [
                {
                    "input_sources": [{ "language": "^zh" }],
                    "type": "input_source_if"
                }
            ],
            "from": {
                "key_code": "4",
                "modifiers": { "mandatory": ["shift"] }
            },
            "to": [
                { "select_input_source": { "language": "^en" } },
                {
                    "hold_down_milliseconds": 30,
                    "key_code": "vk_none"
                },
                {
                    "key_code": "4",
                    "modifiers": ["left_shift"]
                },
                {
                    "hold_down_milliseconds": 30,
                    "key_code": "vk_none"
                },
                { "select_input_source": { "language": "^zh-Hans" } }
            ],
            "type": "basic"
        },
        {
            "conditions": [
                {
                    "input_sources": [{ "language": "^zh" }],
                    "type": "input_source_if"
                }
            ],
            "from": { "key_code": "backslash" },
            "to": [
                { "select_input_source": { "language": "^en" } },
                {
                    "hold_down_milliseconds": 30,
                    "key_code": "vk_none"
                },
                { "key_code": "backslash" },
                {
                    "hold_down_milliseconds": 30,
                    "key_code": "vk_none"
                },
                { "select_input_source": { "language": "^zh-Hans" } }
            ],
            "type": "basic"
        },
        {
            "conditions": [
                {
                    "input_sources": [{ "language": "^zh" }],
                    "type": "input_source_if"
                }
            ],
            "from": {
                "key_code": "6",
                "modifiers": { "mandatory": ["shift"] }
            },
            "to": [
                { "select_input_source": { "language": "^en" } },
                {
                    "hold_down_milliseconds": 30,
                    "key_code": "vk_none"
                },
                {
                    "key_code": "6",
                    "modifiers": ["left_shift"]
                },
                {
                    "hold_down_milliseconds": 30,
                    "key_code": "vk_none"
                },
                { "select_input_source": { "language": "^zh-Hans" } }
            ],
            "type": "basic"
        },
        {
            "conditions": [
                {
                    "input_sources": [{ "language": "^zh" }],
                    "type": "input_source_if"
                }
            ],
            "from": {
                "key_code": "hyphen",
                "modifiers": { "mandatory": ["shift"] }
            },
            "to": [
                { "select_input_source": { "language": "^en" } },
                {
                    "hold_down_milliseconds": 30,
                    "key_code": "vk_none"
                },
                {
                    "key_code": "hyphen",
                    "modifiers": ["left_shift"]
                },
                {
                    "hold_down_milliseconds": 30,
                    "key_code": "vk_none"
                },
                { "select_input_source": { "language": "^zh-Hans" } }
            ],
            "type": "basic"
        },
        {
            "conditions": [
                {
                    "input_sources": [{ "language": "^zh" }],
                    "type": "input_source_if"
                }
            ],
            "from": {
                "key_code": "open_bracket",
                "modifiers": { "mandatory": ["shift"] }
            },
            "to": [
                { "select_input_source": { "language": "^en" } },
                {
                    "hold_down_milliseconds": 30,
                    "key_code": "vk_none"
                },
                {
                    "key_code": "open_bracket",
                    "modifiers": ["left_shift"]
                },
                {
                    "hold_down_milliseconds": 30,
                    "key_code": "vk_none"
                },
                { "select_input_source": { "language": "^zh-Hans" } }
            ],
            "type": "basic"
        },
        {
            "conditions": [
                {
                    "input_sources": [{ "language": "^zh" }],
                    "type": "input_source_if"
                }
            ],
            "from": {
                "key_code": "close_bracket",
                "modifiers": { "mandatory": ["shift"] }
            },
            "to": [
                { "select_input_source": { "language": "^en" } },
                {
                    "hold_down_milliseconds": 30,
                    "key_code": "vk_none"
                },
                {
                    "key_code": "close_bracket",
                    "modifiers": ["left_shift"]
                },
                {
                    "hold_down_milliseconds": 30,
                    "key_code": "vk_none"
                },
                { "select_input_source": { "language": "^zh-Hans" } }
            ],
            "type": "basic"
        },
        {
            "conditions": [
                {
                    "input_sources": [{ "language": "^zh" }],
                    "type": "input_source_if"
                }
            ],
            "from": {
                "key_code": "comma",
                "modifiers": { "mandatory": ["shift"] }
            },
            "to": [
                { "select_input_source": { "language": "^en" } },
                {
                    "hold_down_milliseconds": 30,
                    "key_code": "vk_none"
                },
                {
                    "key_code": "comma",
                    "modifiers": ["left_shift"]
                },
                {
                    "hold_down_milliseconds": 30,
                    "key_code": "vk_none"
                },
                { "select_input_source": { "language": "^zh-Hans" } }
            ],
            "type": "basic"
        },
        {
            "conditions": [
                {
                    "input_sources": [{ "language": "^zh" }],
                    "type": "input_source_if"
                }
            ],
            "from": {
                "key_code": "period",
                "modifiers": { "mandatory": ["shift"] }
            },
            "to": [
                { "select_input_source": { "language": "^en" } },
                {
                    "hold_down_milliseconds": 30,
                    "key_code": "vk_none"
                },
                {
                    "key_code": "period",
                    "modifiers": ["left_shift"]
                },
                {
                    "hold_down_milliseconds": 30,
                    "key_code": "vk_none"
                },
                { "select_input_source": { "language": "^zh-Hans" } }
            ],
            "type": "basic"
        }
    ]
}
```

## 调节延迟

如果你的 Mac 性能较旧，或者你打字极快，偶尔还是会蹦出中文符号（如 `¥` 或 `……`），说明系统切换输入法需要更多反应时间。

你可以用文本编辑器打开 JSON 文件，搜索 `hold_down_milliseconds": 30`，批量将 `30` 修改为 `50` 或 `70` 即可。如果你觉得打字有轻微卡顿感，也可以将其批量调低为 `20`。
