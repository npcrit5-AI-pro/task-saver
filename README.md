# Task Saver: a simple browser to-do list

Task Saver is a tiny to-do list app in **one HTML file** (`task.html`). You can add tasks, tick them off, and delete them. Your list is saved in your browser with `localStorage`, so it is still there after you refresh or close the page.

It uses plain **HTML, CSS, and JavaScript**. There's nothing to install, no server, and no account.

---

## Features

- **Add tasks:** type in the box and click **Add**, or press **Enter**
- **Mark tasks complete:** click a task's text to cross it out. Click again to undo.
- **Delete tasks:** click the red **Delete** button next to a task
- **Saved automatically:** every change is saved to your browser's `localStorage`
- **Ignores empty tasks:** blank or spaces-only input is not added
- **Clean, minimal look:** a single white card on a light background

---

## Tutorial

### 1. Get the file

**Option A, download:** on the GitHub page, click **`task.html`**, then the **Download raw file** button (the down-arrow icon). Or click **Code → Download ZIP** and unzip it.

**Option B, git:**

```bash
git clone https://github.com/npcrit5-AI-pro/task-saver.git
cd task-saver
```

### 2. Open it

Double-click **`task.html`**. It opens in your default web browser (Chrome, Edge, Firefox, Safari...).

You can also drag the file into an open browser window, or from a terminal run:

- Windows: `start task.html`
- macOS: `open task.html`
- Linux: `xdg-open task.html`

### 3. Use it

1. The page shows a card titled **My Tasks** with a text box that says *Add a new task...*. The box is already selected, so you can start typing.
2. Type a task, for example `Buy milk`, and press **Enter** (or click the green **Add** button). It appears in the list below.
3. **Finished a task?** Click its text. It turns gray with a line through it. Click again to un-finish it.
4. **Don't need it any more?** Click the red **Delete** button on that row.
5. Close the tab or refresh. When you open `task.html` again in the **same browser**, your tasks are still there.

### 4. Optional: put it on the web

Because it's a single static file, you can host it anywhere that serves HTML, for example GitHub Pages (Settings → Pages → deploy from the `main` branch). GitHub Pages looks for `index.html`, so either rename a copy to `index.html` or open `https://<user>.github.io/task-saver/task.html` directly. Each visitor gets their own private list in their own browser.

---

## Configuration

There are no settings, environment variables, or API keys.

| What | Value |
|---|---|
| Storage | Browser `localStorage` |
| Storage key | `tasks` |
| Data format | JSON array of `{ "text": "...", "completed": true/false }` |

To change colors or sizes, edit the `<style>` block at the top of `task.html`.

---

## Troubleshooting

**My tasks disappeared**
`localStorage` belongs to one browser on one device, and to the exact place the file was opened from. Tasks won't carry over if you:
- open the file in a **different browser** or on **another computer**,
- **move or rename** the file or its folder (some browsers treat that as a different site),
- use a **private / incognito window** (cleared when you close it),
- **clear your browsing data** / site data.

**Tasks don't save at all**
Some browsers limit `localStorage` for files opened straight from disk (`file://`). If that happens, try another browser or serve the folder locally:

```bash
python -m http.server 8000
```

Then open <http://localhost:8000/task.html>.

**Pressing Enter does nothing**
Make sure the text box has something in it (empty or spaces-only tasks are ignored) and that you clicked into the box first.

**I want to back up or move my list**
Open the browser's developer tools (F12) → **Console**, run `copy(localStorage.getItem('tasks'))`, and paste the result somewhere safe. To restore it in another browser, open `task.html` there, then run `localStorage.setItem('tasks', '<paste here>')` in the Console and refresh.

---

## Project structure

```
task-saver/
├── task.html   # The whole app: HTML, CSS, and JavaScript
└── README.md
```
