# Smart Projects

A global project switcher for Visual Studio Code. It keeps one list of your open, recent and discovered projects, shared across every VS Code window.

## Features

**Open projects.** Every open window is listed, so you can jump between them from one place.

**Auto-discovery.** Add folders to `smartProjects.scanDirectories` and the extension finds repositories inside them, up to three levels deep. It recognizes `.git`, `package.json`, `pom.xml` and `.vscode`.

**Live Git status.** Each project shows its branch, with `*` for uncommitted changes. Changes made in one window appear in the others within seconds.

**Pins and tags.** Pin projects to the top. Assign one or more tags to group projects, and filter the list by tag.

**Recent projects.** The last 20 projects you opened, with relative timestamps.

**Language icons and colors.** Projects show an icon for their main language. You can also assign a custom color per project.

**Ignore list.** Forget a project to hide it everywhere. Restore it later from the Ignored Projects view.

**Unified search.** Search across open, recent and discovered projects with `Ctrl+Shift+O` (`Cmd+Shift+O` on macOS), then open the result in the current or a new window.

## Display modes

Set `smartProjects.displayMode` to choose where the project list appears:

| Value | Location |
| --- | --- |
| `quickPick` | Quick pick opened from the status bar (default) |
| `treeView` | Sidebar view |
| `panel` | Bottom panel |
| `statusBar` | One status bar item per open project |
| `statusBarTags` | One status bar item per tag |

## Settings

| Setting | Description | Default |
| --- | --- | --- |
| `smartProjects.displayMode` | Where the project list appears | `quickPick` |
| `smartProjects.scanDirectories` | Folders to scan for projects | `[]` |
| `smartProjects.showGitStatus` | Show branch and uncommitted changes | `true` |
| `smartProjects.useLanguageIcons` | Show language icons | `true` |
| `smartProjects.ignoredProjects` | Paths to hide everywhere | `[]` |
| `smartProjects.pinnedProjects` | Pinned project paths (managed by the extension) | `[]` |
| `smartProjects.projectTags` | Tags per project (managed by the extension) | `{}` |
| `smartProjects.customColors` | Colors per project (managed by the extension) | `{}` |

## Commands

| Command | Shortcut |
| --- | --- |
| Smart Projects: Search All Projects | `Ctrl+Shift+O` / `Cmd+Shift+O` |
| Smart Projects: Show Open Projects | |
| Smart Projects: Show Projects for Tag | |

Other actions, such as pin, tag, color and forget, are available from the buttons and context menu in the Smart Projects views.

## How it works

Each window writes a heartbeat every 10 seconds to a JSON file in your home directory. Windows read the same file to build a shared view, and entries that stop sending heartbeats are removed.

## Building from source

Requires Node.js and VS Code 1.85 or later.

```
git clone https://github.com/andrimishko/vscode-smart-projects.git
cd vscode-smart-projects
npm install
npm run compile
```

Press `F5` in VS Code to launch an Extension Development Host. To build an installable package:

```
npx @vscode/vsce package
code --install-extension smart-projects-0.3.0.vsix
```
