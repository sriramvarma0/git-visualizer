# Git Visualizer

An interactive visual guide to Git commands and repository workflows. Git Visualizer helps developers understand where changes move during common Git operations through an intuitive, interactive map.

---

## Overview

Understanding Git requires a clear mental model of where code resides and how commands transfer snapshots between different environments.

**Git Visualizer** maps Git commands across core repository stages, illustrating source areas, target destinations, and directional data flows in real time.

---

## Features

- **Visual Git Workflow Columns**: Clear side-by-side representation of the primary Git workflow environments.
- **Interactive Command Labels**: Hoverable command pills that highlight associated paths and reveal contextual details.
- **Command Explanations on Hover**: Floating cards that display command syntax, descriptions, and origin/destination stage badges.
- **Highlighting of Related Workflow Paths**: Active connections are visually emphasized while unrelated canvas elements are dimmed.
- **Animated Data-Flow Connections**: Directional SVG dashed-line animations that show the flow of changes between stages.
- **Column Selection and Visual Filtering**: Click any workflow column to filter and isolate all incoming and outgoing commands for that area.
- **Locally Bundled Fonts and Static Assets**: Self-contained web fonts and styles with zero runtime dependencies on external CDNs.

---

## Git Workflow Overview

The visualizer organizes operations across five key stages:

- **Stash**: A temporary storage area used to set aside uncommitted changes (`git stash`, `git stash pop`, `git stash apply`).
- **Workspace**: The local working tree containing your active project files, edits, and untracked files.
- **Staging**: The index where changes are formatted and prepared prior to committing (`git add`, `git diff --staged`).
- **Local Repository**: The committed history and local branch pointers stored on your system (`git commit`, `git reset`, `git switch`).
- **Remote Repository**: The central shared repository hosted on platforms such as GitHub or GitLab (`git fetch`, `git push`, `git pull`, `git clone`).

Commands connect these stages by moving, copying, or comparing changes between them.

---

## Technology and Architecture

Git Visualizer is implemented as a self-contained, static client-side web application:

- **HTML Entry Point**: `index.html` loads styling, font declarations, and the client application container.
- **Compiled JavaScript Bundle**: Standalone compiled application bundle (`assets/index.js`) handling UI rendering, state, and interaction.
- **CSS Stylesheet & Animations**: Stylesheet (`assets/index.css`) providing responsive layout, theme tokens, and custom SVG path animations.
- **Locally Hosted WOFF2 Fonts**: Font files (`DM Sans`, `Playfair Display`, `Space Mono`) served locally via `assets/fonts/fonts.css`.
- **Static Client-Side Architecture**: Executes entirely within the browser with no server-side processing or dynamic backend services.

---

## Project Structure

```
git-visualizer/
├── index.html
├── favicon.svg
├── README.md
├── .gitignore
└── assets/
    ├── index.js
    ├── index.css
    └── fonts/
        ├── fonts.css
        ├── dmsans.woff2
        ├── playfairdisplay.woff2
        └── spacemono.woff2
```

---

## Getting Started

Because the application uses JavaScript ES modules (`<script type="module">`), running it through a local HTTP server is recommended instead of opening `index.html` directly from the filesystem.

### Prerequisites

A modern web browser and a static HTTP server utility (such as Python 3 or Node.js).

### Option 1: Python (Built-in)

From the project root directory, run:

```powershell
python -m http.server 8080
```

Then open your browser and navigate to:

```
http://localhost:8080/
```

### Option 2: Node.js (`npx serve`)

If Node.js is installed, run:

```powershell
npx serve .
```

Open the local address shown in the terminal output (typically `http://localhost:3000`).

---

## Usage

- **Explore Commands**: Hover over any command label to highlight its data-flow path.
- **Read Explanations**: Inspect the popover card to see command syntax, origin/destination stages, and behavioral descriptions.
- **Select Workflow Columns**: Click a column header (such as *Workspace* or *Staging*) to filter the canvas and show only commands touching that stage.
- **Inspect Highlighted Connections**: Follow the animated lines to verify whether changes are staged, committed, shelved, or synchronized.
- **Clear Selection**: Click any blank area on the canvas background to reset filters and restore the full view.

---

## Deployment

Git Visualizer has no build step and can be hosted directly on any static web hosting provider. Ensure that the file structure and relative asset paths remain unchanged.

### GitHub Pages

1. Push the repository to GitHub.
2. In your repository settings, go to **Pages**.
3. Under **Build and deployment**, select **Deploy from a branch**.
4. Set the branch to `main` and the folder to `/ (root)`, then click **Save**.

### Cloudflare Pages

1. Connect your repository in the Cloudflare dashboard.
2. Leave the **Build command** blank.
3. Set the **Build output directory** to `.`.
4. Deploy the site.

### Netlify

1. Connect the repository or drag and drop the folder into Netlify.
2. Leave the **Build command** blank.
3. Set the **Publish directory** to `.`.
4. Deploy the site.

---

## Offline Support

All core assets—including the JavaScript bundle, CSS stylesheets, WOFF2 font files, and SVG favicon—are stored locally in the repository.

- No external CDNs, Google Fonts endpoints, or third-party APIs are requested at runtime.
- The application functions fully offline when loaded via a local HTTP server or cached in a modern browser.

---

## Limitations

- **Production Distribution**: This repository distributes compiled production assets rather than an editable component source tree.
- **No Build Pipeline**: There is no npm package manifest (`package.json`) or automated build workflow included.
- **Educational Guide**: Visual representations and command descriptions provide a high-level conceptual reference and are not a replacement for the [official Git documentation](https://git-scm.com/doc).

---

## Contributing

Contributions to improve documentation, enhance static hosting configurations, or fix relative asset links are welcome.

1. Fork the repository and create a feature branch.
2. Verify visual behavior, animations, and asset loading using a local HTTP server.
3. Submit a Pull Request with a clear summary of your changes.

