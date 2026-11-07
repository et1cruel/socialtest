# GENNOISE / THAI UNDERGROUND — Content Planner
Personal content-planning workspace for an independent Thai underground music media project. It is an editorial workspace—not a social network, publishing platform, or auto-posting tool.

## Features
- Overview of upcoming content, production, published work, pending plans, deadlines, and tracked events.
- Content calendar with month, week, day, and list views; category/platform filters and title/artist search.
- Five-stage production pipeline: IDEAS → PLANNING → PRODUCTION → READY → PUBLISHED.
- Idea archive with a shortcut to convert an idea into a content plan.
- Artist and music promotion records, plus event tracking and countdowns.
- Editable weekly rhythm and weekly review notes.
- LocalStorage persistence, JSON export/import, and demo reset.
- Responsive editorial workspace with dark/light theme toggle.

## Run locally
No build step, package manager, backend, or API key is required. Open `index.html` in a modern browser. For a more reliable local preview, serve the project folder with any static file server. The site is also ready for GitHub Pages.

## Using the workspace
1. Use the left navigation to open Overview, Calendar, Pipeline, Ideas, Artists & Music, Events, or Weekly Plan.
2. Select **เพิ่มคอนเทนต์** to plan an item. Set its title, category, platform, publish date/time, production deadline, artist, status, priority, links, and notes.
3. Edit or delete a content item by selecting it in the calendar/list or the pipeline card. Deletes ask for confirmation.
4. Add ideas, artist profiles, and events in their respective sections. An idea can be turned into a content plan with **Plan**.
5. Move a pipeline item forward with **MOVE →**. Use the weekly planner to add/remove recurring tasks and write a weekly review.
6. Dashboard task checkmarks are saved locally. They indicate completion of the relevant content deadline task.

## Export / import and backups
- Select the up-arrow button in the top bar to download a JSON backup.
- Select the down-arrow button to import a previously exported JSON file. Import replaces the current workspace after confirmation. Export a backup first.
- Store exported files somewhere separate from the browser/device. Export regularly—especially before clearing browser data or moving to another device.
- Use **↺ คืนค่า DEMO** at the top of Weekly Plan to reset the current workspace (after confirmation). This replaces local data with the built-in sample dataset.

## Editing the starter data
- `data/sample-data.json` is the repository's editable starter dataset. All included names/events/content are clearly marked as fictional DEMO examples.
- On first load, the app fetches `data/sample-data.json` using a relative URL (compatible with GitHub Pages project URLs). If opened directly as a `file://` page or the sample file cannot be read, built-in DEMO defaults are used instead. The app then saves the initialized workspace in LocalStorage.
- Existing browser data takes precedence over starter data. Use **↺ Restore DEMO** at the top of Weekly Plan to reset the current workspace, or clear the LocalStorage key `gennoise-planner-v1` in DevTools.
- Categories can be added, renamed, or removed using **EDIT CATEGORIES** in the calendar; the starter category set and category colors can also be changed in `js/app.js` (`CATEGORIES` and `CAT_COLORS`). When editing the starter defaults, update both `data/sample-data.json` and the matching fallback data in `js/app.js`.

## GitHub Pages deployment
1. Create a GitHub repository and upload/push the contents of this project to the repository root.
2. Open **Settings → Pages**.
3. In **Build and deployment**, choose **Deploy from a branch**.
4. Choose branch `main` and folder `/ (root)`, then save.
5. Wait for the Pages URL shown in Settings → Pages. `index.html` uses relative CSS/JS paths, so repository project URLs under a subdirectory are supported.

There is no compile/build step. Keep the repository root structure (`index.html`, `css/`, `js/`, `data/`).

## LocalStorage limitations
Data is stored only in this browser on this device. It does not sync across browsers or devices, is not encrypted, and can be cleared by browser settings. There is no account, backend, or automatic cloud backup. Use JSON export for portability and backups. The Google Fonts import is optional decoration; local system fonts provide a fallback if it cannot load.

## Data model
The JSON workspace stores `contents`, `ideas`, `artists`, `events`, `weekly`, and `tasks`. Exported JSON is the portable source of truth for backups and imports.

## License / privacy
Personal planning tool. Do not enter sensitive contact details unless appropriate for your local device. Demo data is fictional and must not be treated as real music news, artists, or events.
