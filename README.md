# Log Viewer

A single-file static HTML log viewer. No server, no dependencies — open it in a browser and drop your log files in.

**[Try it live](https://krasnovpavel.github.io/logviewer/)**

---

## Features

### Two-panel layout
View two log sources side by side with a draggable splitter.

### Multi-file support
Each panel can hold multiple log files appended together:
- **Open** — load one or more files (replaces current content)
- **Add** — append more files to the current view
- **Drag & drop** — drop one or multiple files onto a panel
- A separator row shows the filename boundary between each file
- Click the filename label to expand a file list with per-file remove buttons and a **Remove all** option

### Filters
Regex-based include/exclude filters per panel. Active filters show a match count. Filtered-out lines are collapsed into an expandable group showing how many lines are hidden.

### Highlights
Color lines or matched text using regex rules. Configure color, scope (line vs. text), background vs. foreground, and case sensitivity. Default rules highlight `INFO`, `WARN`, `ERROR`, `DEBUG`, and `TRACE` levels.

### Columns
Parse log lines into named columns using a regex with named capture groups (`(?<name>…)`). Configure column visibility and width. Default pattern targets `timestamp [thread] level - message` format.

### Search
`Ctrl+F` opens an in-panel search bar. Navigate matches with `Enter` / `Shift+Enter`. Regex supported.

### Temporal sync
Align two panels by timestamp so scrolling one panel scrolls the other to the same point in time. Configure the timestamp column name, format, and an offset in milliseconds.

### Selection popup
Select any text in a log line to instantly **Show only**, **Hide lines**, **Highlight**, or **Search** for that text.

### Settings export / import
Save all filters, highlights, column config, and sync settings to a JSON file and restore them later.

### Light / dark theme
Toggle between dark (default) and light themes.

---

## Usage

- **Online:** open [krasnovpavel.github.io/logviewer](https://krasnovpavel.github.io/logviewer/) in your browser
- **Offline:** download `index.html` and open it locally — no server or internet connection required

Drop a log file onto a panel or click **Open**, then use the **Filters**, **Highlights**, and **Columns** panels at the bottom to configure the view.

