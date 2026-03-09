# GitOn: Comprehensive Git Power-Tools for VS Code

> ⚠️ **BETA WARNING / USE WITH CAUTION**
> This extension is currently in active development and provides powerful Git mutating features (such as Time Travel, Atomic Staging, and Interactive Rebasing). Please use with caution on production repositories and report any bugs or unexpected behavior!

GitOn is a feature-rich, deeply integrated Git extension designed to supercharge your version control workflow within VS Code and Cursor. It moves beyond standard commit/push operations by providing advanced insights, risk analysis, atomic staging capabilities, and a revolutionary way to traverse file history.

## � Installation & Getting Started

**Get it from the marketplaces:**
- [**VS Code Marketplace**](https://marketplace.visualstudio.com/items?itemName=ParasKoundal.giton)
- [**Open VSX Registry**](https://open-vsx.org/extension/ParasKoundal/giton)

1. Open any Git repository.
2. Check the VS Code Status Bar for the GitOn sync and Impact Score indicators.
3. Open the VS Code Activity Bar and click the GitOn icon to access the Dashboard, Stashes, Drafts, and Branch Hygiene trees.
4. Right-click inside any file to activate **Time Travel (Scrub Bar)**.

---

## �🔥 Core Features

### 1. Time Travel Scrub Bar (Virtual History)
Ever wonder how a file evolved over time? Instead of digging through git logs, right-click any file and select **Time Travel (Scrub Bar)**. 
- **How it works:** Opens a read-only, virtual document alongside a Webview slider in the GitOn sidebar.
- **Usability:** Drag the slider left and right to physically "rewind" and "fast-forward" the code in real-time. Commit details (author, date, message) update instantly below the slider.

### 2. Gutter Blocks (Atomic Hunk Staging & Ghost Stashes)
Gain granular control over what you commit without ever leaving the editor.
- **How it works:** GitOn renders tiny green `+` icons in the editor gutter next to changed code blocks (hunks). 
- **Usability:** 
  - Click the **Stage Hunk** CodeLens to stage just that specific block instantly.
  - Right-click to **Ghost-Stash** the hunk — this removes the code from your working tree but saves it to a persistent side-buffer, keeping your current file clean for atomic commits.
  - Use **Restore Ghost Hunk** from the Command Palette piece it back together later.

### 3. Git Dashboard & Activity Box
A centralized control center for your repository.
- **How it works:** The dashboard summarizes repository status and provides a dynamic Activity Sparkline chart.
- **Usability:** Toggle between Week, Month, and Year views to see a visual graph of your commit frequency. 

### 4. Interactive Blame & CodeLens Annotations
Know exactly who wrote what, without cluttering your screen.
- **How it works:** Provides subtle, non-intrusive `git blame` annotations at the end of the line you are currently editing.
- **Usability:** Adds a CodeLens above function declarations showing "Last edited by X on [Date]". Clicking the CodeLens brings up the recent commit details.

### 5. Commit Heatmap (Tech Debt Radar)
Instantly visualize technical debt and code hotspots.
- **How it works:** Analyzes file history and applies a subtle background color tint to files that are modified extremely frequently (hotspots).
- **Usability:** Disabled by default to keep the editor clean. Toggle it on via the Command Palette (`GitOn: Toggle Heatmap`) to see which files in your workspace are getting touched the most. Red highlights indicate high churn.

### 6. Impact Score (Blast Radius Analyzer)
Don't accidentally break production.
- **How it works:** Analyzes your unstaged changes and calculates a "Risk Score" out of 100 based on the number of files touched, lines changed, and whether you are modifying known "hot" files.
- **Usability:** Always visible in the bottom-left status bar. Click the `$(pulse) Risk: X` item to see a detailed breakdown of why your current changes might be risky.

### 7. Shadow Staging (Drafts)
A safer alternative to `git stash`.
- **How it works:** Allows you to snapshot your current working tree into named "Drafts" without messing with your stash queue or committing half-baked code.
- **Usability:** Managed via the GitOn sidebar under the "Shadow Staging (Drafts)" tree view. Create, apply, or delete drafts with a single click.

### 8. Intelligent Stash & Branch Hygiene
Keep your repository clean effortlessly.
- **How it works:** Dedicated tree views in the GitOn sidebar for managing Stashes and Branches.
- **Usability:** 
  - Apply, Pop, or Drop stashes directly from the UI. 
  - View Branch Hygiene to identify and delete stale or fully merged branches that are cluttering your local environment.

### 9. The "Oops" Button (Safe Undo)
Made a mistake on your last commit?
- **How it works:** Safely undoes the last commit without losing any of your file changes.
- **Usability:** Run `GitOn: Undo Last Commit` to execute a soft reset. The changes remain in your working tree ready to be amended.

### 10. Background Conflict Pre-Detector
Never get surprised by merge conflicts again.
- **How it works:** Silently pings the remote origin in the background to check if coworkers have pushed changes to the files you are currently editing.
- **Usability:** Triggers a VS Code warning notification proactively *before* you attempt to push, saving you from nasty merge conflict headaches.

### 11. Interactive Rebase UI (Drag and Drop)
- **How it works:** A visual, drag-and-drop interface within the GitOn dashboard replacing the complex `git rebase -i` text editor.
- **Usability:** Intuitively squash, reorder, edit, or drop commits by clicking and dragging cards around, eliminating the need to manually edit finicky interactive rebase text files.

---

---

## 🔮 Future Enhancements (Roadmap)
GitOn is already incredibly powerful, but here are some ideas we can implement next to make it the ultimate developer tool:

### 1. "Time-Warp" Safe File Sandbox
- **How it works:** Right-click a folder or file and open a "Sandbox" from a specific commit hash within a temporary Git worktree.
- **Usability:** You can run and execute the historical code alongside your modern code to test past bugs, without ever leaving or dirtying your current Git branch.

### 2. AI Commit "Story" Generator
- **How it works:** Integrates with a local or cloud LLM to read your unstaged diffs and write a full "Commit Story" explaining the rationale behind the code changes.
- **Usability:** Automatically generates meaningful commit messages that explain *why* something changed (not just *what* changed), formatting it beautifully with Markdown and file links to make your repo history read like a clean technical blog.

### 3. The "Oops" Button (Intelligent Panic Undo)
- **How it works:** A massive "Oops" panic button in the GitOn dashboard that safely undoes your last Git action, intelligently determining what went wrong.
- **Usability:** If you just committed locally, it runs a soft reset. If you pushed to remote by accident, it provides a clean UI to execute an interactive rebase (`git rebase -i`), drop the bad commit, and force-push safely—turning complex rescues into a single click.

### 4. Visual "Blast Radius" Analyzer
- **How it works:** Analyzes imports and file dependencies via AST or regex when you modify a core utility file.
- **Usability:** Highlights files in your VS Code explorer tree that *might* be broken by the changes you are about to commit, giving you an immediate visual "Blast Radius" map of your blast area before you break production.

### 5. Git Graph "Playback" / Repository Timelapse
- **How it works:** Visualizes the structural evolution of the repository directory tree over time.
- **Usability:** You hit "Play," and the UI animates folders expanding, files being created (green), and deleted files (red), allowing you to watch the repository grow like a timelapse video without reading raw logs.

### 6. "Ghost" Branch Previews
- **How it works:** GitOn detects when a remote branch is created and offers a "Peek" button to view it via a temporary `git worktree`.
- **Usability:** Click to open a secondary VS Code window tied solely to that branch. Review code, test it locally, and close it when done—without ever having to check out and disrupt your current working branch.

### 7. Smart Conflict Resolution Assistant
- **How it works:** Offers a side-by-side AST (Abstract Syntax Tree) diff to intelligently suggest how to merge code instead of standard text-based merge markers.
- **Usability:** Streamlines the merge process seamlessly using structural language comparisons when the Background Pre-Detector catches incoming merge conflicts.


