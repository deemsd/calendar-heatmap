# Changelog

## 1.7.0 (2026-06-05)

### Bug Fixes

- **字数统计修复**: 修复了中文内容被严重低估的问题。热力图现在按非空白字符统计新增字数，能正确显示中文长文和中英混排内容。

- **Daily Note 日期归属修复**: 修复了 `buildCreatedNotesByDay()` 中每日笔记的字数和数量被归到错误日期的问题。当 Daily Notes 插件预创建笔记文件时（如 6 月 1 日创建 `2026-06-02.md`），插件原使用 `ctime`（文件创建时间）决定归属日期，导致内容被统计到文件创建日而非笔记实际日期。

  Now uses the date from the daily note's filename (`YYYY-MM-DD`) instead of `ctime`, so content is correctly attributed to the note's actual date.

### Features

- **设置页面新增 Daily Note 统计开关**: 在“热力图显示依据”下面新增一个“包含 Daily Note”开关，统一控制新增笔记数量和新增字数是否计入 Daily Note。
