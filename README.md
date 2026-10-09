# Random Task

**Never run out of things to build or try.** Pick your field, press a button, and get a fresh hands-on task: a weekend project for a developer, a bench experiment for a chemist, a circuit for an electronics hobbyist, or anything else you type in.

<!-- Add a screenshot here: ![Random Task screenshot](screenshots/main.png) -->

## What you get

- A new task every time, with a title, a short description, steps and a time estimate
- Fields built in (Developer, Electronics, Chemistry) plus a free-text box for any other field: Biology, Music, Mechanical, Design...
- An effort filter: 1 hour, a weekend, or a week
- Saved tasks, so you can keep the ones you like
- No repeats: the app remembers what it recently showed you
- Works offline with a built-in task list

## Install

> **Coming soon** to the Chrome Web Store, Microsoft Edge Add-ons and Firefox Add-ons.
>
> Until then, see [Install from source](#install-from-source).

After installing, click the Random Task icon in your toolbar. The app opens in a full browser tab.

## How to use it

1. Click the extension icon.
2. Choose a field, or type your own.
3. Optionally set how much time you have.
4. Press **Give me a task**.
5. Press **Save** on tasks you want to keep.

## AI-generated tasks

With AI turned on, every task is generated for you and is different each time. Without it, the app uses the built-in list.

Right now AI needs your own Anthropic API key (**AI settings** in the sidebar). The key is stored only in your browser. A hosted version that needs no key is planned (see the roadmap).

## Privacy

- No analytics and no tracking.
- Settings, saved tasks and your API key stay in your browser's local storage.
- When AI is on, only the field you chose and the effort level are sent to the AI service to generate the task.

---

## For developers

### Install from source

1. Clone the repo:
   ```bash
   git clone git@github.com:tosek4/RandomTask.git
   ```
2. Open `chrome://extensions` (or `edge://extensions`) and turn on **Developer mode**.
3. Click **Load unpacked** and select the project folder.

### Project structure

```
RandomTask/
├── manifest.json   # Extension config (Manifest V3)
├── background.js   # Opens the full-screen page on icon click
├── app.html        # Main page
├── app.css         # Styles
├── app.js          # UI logic, AI call, local fallback
├── tasks.json      # Built-in fallback tasks
└── README.md
```

### Adding built-in tasks

Edit `tasks.json`. Each category is an array of tasks, and new categories appear automatically as chips:

```json
{
  "Developer": [
    { "title": "Build a CLI to-do app", "description": "Ship add, list and done commands.", "time": "A weekend" }
  ]
}
```

### API key safety

Never hardcode an API key in the source or commit one to Git. For a public release, requests should go through your own backend (for example a Cloudflare Worker) so the key stays on the server.

### Tech

JavaScript, HTML and CSS with no build step. Chrome Extension Manifest V3. Anthropic Messages API (`claude-haiku-5-5`).

## Roadmap

- [ ] Backend proxy so users do not need their own key
- [ ] Saved tasks page
- [ ] Daily task notification
- [ ] Difficulty levels
- [ ] Firefox build
- [ ] Publish to Chrome Web Store, Edge Add-ons and Firefox Add-ons

## License

MIT (add a `LICENSE` file before publishing).