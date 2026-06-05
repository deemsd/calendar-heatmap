# Changelog

## 1.7.0 (2026-06-05)

### Bug Fixes

- **Word count accuracy**: Fixed undercounting for Chinese and mixed-language notes. The heatmap now counts non-whitespace characters for the "new words" metric, so long Chinese articles and mixed Chinese/English notes are represented correctly.

- **Daily Note date attribution**: Fixed daily note counts and word totals being assigned to the wrong day in `buildCreatedNotesByDay()`. Daily notes now use the date from the filename (`YYYY-MM-DD`) instead of filesystem `ctime`, so pre-created notes are attributed to their actual note date.

### Features

- **Daily Note inclusion setting**: Added a single "Include Daily Note" toggle below the heatmap metric setting. It controls whether Daily Notes are included in both new note count and new word count metrics.
