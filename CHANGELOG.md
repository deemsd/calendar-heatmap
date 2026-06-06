# Changelog

## 1.8.0 (2026-06-06)

### English Release Notes

#### New Features

- **Custom heatmap thresholds**: Added settings for custom word-count and note-count heatmap thresholds. Users can now tune the three color levels to match their own writing volume instead of relying on fixed defaults.
- **Monthly activity summary**: Added a monthly summary below the calendar showing the number of notes created and words added in the currently displayed month.

#### Bug Fixes

- **More reliable first-click navigation**: Fixed an issue where the first click on a calendar date could be consumed by Obsidian pane activation, requiring a second click to open the daily note.
- **Marketplace metadata warning**: Updated the plugin description so it no longer starts with the plugin name, addressing the Obsidian marketplace warning.

#### Improvements

- **Calendar header alignment**: Refined the month title and navigation controls so the header is visually centered and the right arrow aligns with the calendar grid.

### 中文发布说明

#### 新功能

- **热力图阈值自定义**：设置页新增“新增字数阈值”和“新增笔记篇数阈值”，用户可以按自己的写作量调整三档颜色深浅，不再只能使用固定默认值。
- **本月统计汇总**：日历下方新增本月统计，显示当前月份新增了多少篇笔记、多少字。

#### 修复

- **修复日期首次点击不跳转的问题**：修复了 Obsidian 侧边栏激活逻辑可能吞掉第一次点击，导致需要点第二次日期才会打开每日笔记的问题。
- **修复市场元数据警告**：更新插件描述，避免 description 以插件名称开头，解决 Obsidian 市场提示。

#### 优化

- **优化日历顶部对齐**：调整月份标题和左右导航的位置，让“本月”和箭头视觉上居中，并让右箭头与日历方格右边线对齐。

## 1.7.1 (2026-06-05)

### English Release Notes

#### Bug Fixes

- **Reduced sidebar flicker while editing**: Fixed an issue where every Markdown file modification invalidated the full created-notes heatmap cache and triggered a full vault-wide word-count rebuild. This could make the calendar panel visibly flicker while typing in Obsidian, especially in larger vaults.

#### Performance

- **Incremental heatmap updates**: The plugin now tracks each Markdown file's contribution to the created-notes heatmap and updates only the changed file after edits, instead of rereading all Markdown files.
- **Debounced modify refreshes**: Rapid consecutive `modify` events are now batched with a short debounce, reducing repeated calendar redraws while typing.
- **Cleaner create/delete handling**: File creation and deletion paths now use the incremental heatmap cache when possible and avoid unnecessary full-cache invalidation.

### 中文发布说明

#### 修复

- **减少编辑时侧栏闪烁**：修复了任意 Markdown 文件修改都会清空“新增笔记/新增字数”热力图缓存，并触发全库重新统计字数的问题。这个问题会导致在 Obsidian 输入时，左侧 Calendar Heatmap 面板出现明显闪烁，尤其是在笔记数量较多的库中。

#### 性能优化

- **增量更新热力图**：插件现在会记录每个 Markdown 文件对热力图的贡献，编辑后只重新统计被修改的文件，不再重新读取全部 Markdown 文件。
- **合并高频修改事件**：对连续的 `modify` 事件增加短时间防抖，减少输入过程中的重复刷新。
- **优化新建/删除文件刷新**：新建和删除文件时优先使用增量缓存更新，减少不必要的全量缓存失效。

## 1.7.0 (2026-06-05)

### Bug Fixes

- **Word count accuracy**: Fixed undercounting for Chinese and mixed-language notes. The heatmap now counts non-whitespace characters for the "new words" metric, so long Chinese articles and mixed Chinese/English notes are represented correctly.

- **Daily Note date attribution**: Fixed daily note counts and word totals being assigned to the wrong day in `buildCreatedNotesByDay()`. Daily notes now use the date from the filename (`YYYY-MM-DD`) instead of filesystem `ctime`, so pre-created notes are attributed to their actual note date.

### Features

- **Daily Note inclusion setting**: Added a single "Include Daily Note" toggle below the heatmap metric setting. It controls whether Daily Notes are included in both new note count and new word count metrics.
