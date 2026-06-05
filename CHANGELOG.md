# Changelog

## 1.7.0 (2026-06-05)

### Bug Fixes

- **中日文字数统计修复**: 修复了 `getWordCount()` 中 `nonSpaceDelimitedWords` 正则表达式缺少 `[...]` 方括号的问题。缺少方括号导致 CJK 字符范围被解释为字面字符序列，所有中文/日文字符在字数统计中被完全跳过。
  
  Now properly counts each CJK character as one "word" when the heatmap is in "words" mode.

- **Daily Note 日期归属修复**: 修复了 `buildCreatedNotesByDay()` 中每日笔记的字数和数量被归到错误日期的问题。当 Daily Notes 插件预创建笔记文件时（如 6 月 1 日创建 `2026-06-02.md`），插件原使用 `ctime`（文件创建时间）决定归属日期，导致内容被统计到文件创建日而非笔记实际日期。

  Now uses the date from the daily note's filename (`YYYY-MM-DD`) instead of `ctime`, so content is correctly attributed to the note's actual date.

### Features

- **设置页面新增 Daily Note 统计开关**: 增加两个选项：
  - "新增笔记统计包含 Daily Note" — 控制是否将每日笔记计入笔记数量统计
  - "新增字数统计包含 Daily Note" — 控制是否将每日笔记的字数计入字数统计
