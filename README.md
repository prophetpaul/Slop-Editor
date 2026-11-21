# Pavel the Slop Editor

**Clean up the slop. Keep the good bits.**

Pavel is a zero-dependency, single-file visual HTML editor built for humans cleaning up AI-generated pages, comparing multiple design iterations side by side, and collaborating on static HTML without a build step or backend. Everything runs 100% locally in your browser—nothing is ever uploaded.

---

## Features

- **Inline Text Rewriting**: Double-click any text block on the page to edit it directly in place, with quick formatting controls for **Bold**, *Italic*, and <u>Underline</u>.
- **Drag-and-Drop Image Replacement**: Double-click or drop an image file onto any `<img>`, `<picture>`, inline `<svg>`, or CSS `background-image` element. Oversized photos (>1.2 MB) are automatically resized to keep your HTML file lightweight, and mismatched aspect ratios are fitted cleanly with `object-fit: cover`.
- **Cross-Tab Style-Preserving Copy & Paste**: Open multiple versions of a page in tabs, copy a section (`Ctrl/Cmd + C`) from one, and paste it (`Ctrl/Cmd + V`) into another—even if the pages use completely different stylesheets or conflicting class names. Pavel extracts the matching CSS rules, custom properties (`--vars`), `@font-face`, `@keyframes`, `@property`, SVG `<use>` symbols, and local assets, isolating them in a `display: contents` wrapper so the pasted block keeps its original look without breaking the rest of the page. *(You can also paste without styles to adopt the destination page's theme.)*
- **Built-In Threaded Comments**: Switch to **Comment** mode or open the **Comments** tab to pin feedback to specific elements or the page as a whole, reply to threads, and mark items resolved. Comments are stored inside the HTML file itself in an inert `<script type="application/json" id="pavel-review">` block, and can be stripped anytime with **Download a copy without comments**.
- **Shared Folder & Live Sync**: When opened via the File System Access API (Chrome/Edge), Pavel writes changes directly back to disk, auto-saves comments, and polls every 3 seconds for updates made by teammates (e.g., over OneDrive, SharePoint sync, or Dropbox)—automatically merging comment threads and alerting you if both sides edited the page.
- **Element Inspector & Responsive Preview**: Navigate DOM breadcrumbs, reorder siblings, duplicate or delete elements, adjust colors, font size, and alignment, edit link targets and form placeholders, inspect/edit raw element HTML, pause runaway page scripts, and preview across **Desktop**, **Tablet** (`820px`), and **Mobile** (`390px`) widths.

---

## Getting Started

1. Download `Pavel the Slop Editor.html` and open it in any modern web browser.
2. Load your files in one of four ways:
   - **Open HTML files**: Select one or more `.html` / `.htm` files to open in tabs.
   - **Open folder**: Mount an entire site directory so relative stylesheets, fonts, and images resolve automatically.
   - **Drag & drop**: Drop `.html` files or a site folder anywhere onto the window.
   - **Try the demo**: Click **"try the two demo versions"** on the welcome screen to open two contrasting landing page versions and test copying sections between them.

---

## How It Works

Pavel maintains two synchronized representations of every open page:

1. **Clean Source DOM (`srcDoc`)**: Parsed from your file on open without executing scripts. Every edit is applied here, ensuring runtime JavaScript mutations, `<noscript>` tags, and editor UI overlays never leak into your saved file.
2. **Live Preview `iframe`**: Renders your page with its own scripts and styles active. Elements share matching `data-pavel-id` attributes so visual edits map accurately back to the clean source.

---

## Keyboard Shortcuts

| Shortcut | Action |
| :--- | :--- |
| **Double-click** | Rewrite text or replace an image |
| `Enter` | Edit the selected element |
| `Esc` | Finish typing or deselect |
| `Delete` / `Backspace` | Remove the selected element |
| `Ctrl/Cmd + C` / `X` / `V` | Copy / Cut / Paste element (with styles across tabs) |
| `Ctrl/Cmd + D` | Duplicate selected element |
| `Alt/Option + ↑` / `↓` | Move element up or down among siblings |
| `Ctrl/Cmd + Z` | Undo |
| `Ctrl/Cmd + Shift + Z` *(or `Ctrl + Y`)* | Redo |
| `Ctrl/Cmd + S` | Save file |
| `Ctrl/Cmd + Shift + S` | Save as… |
| `Ctrl/Cmd + O` | Open HTML files |
| `Ctrl/Cmd + Enter` | Post the comment you are writing |

---

## Browser Compatibility

- **All modern browsers** (Chrome, Edge, Firefox, Safari): Full visual editing, cross-tab style-isolated copy/paste, drag-and-drop file/folder loading, and downloading saved or comment-free HTML files.
- **Chromium browsers** (Chrome, Edge): Adds direct in-place saving, native folder handles, and automatic background merging when collaborating on a shared file via the File System Access API.
