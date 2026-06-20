# Penumbra Notes

A fast, native note-taking app—**privacy-first** and **local-first**. Write in rich markdown, organize with tags, track tasks across notes, and keep everything in a local database on your machine—optionally encrypted.

**Current version: v0.6.8** · macOS and Windows

For release-by-release changes and technical documentation, see **[changelog.md](changelog.md)**. Planned work (merge conflicts, hosted sync, app-bound encryption): **[docs/roadmap.md](docs/roadmap.md)**.

### What's new in v0.6.8

- **Click alignment** — Clicks and selections after callouts and code blocks hit the line you see, not one row below.
- **Safer Backspace** — Deleting emphasized text or blank lines no longer merges plain text into ``` fences, callouts, or tables.
- **Code block remove** — Trash icon on plain code fences (like mermaid and tables).
- **Convert to paragraph** — **Format → Convert to paragraph** or toolbar **Paragraph** strips list markers into a normal body line.
- **Wiki-link menu** — Partial title matches accept on click or Enter; arrow keys work while the autocomplete menu is open.
- **Tags** — More reliable `#tag` parsing in notes and filters.

### What's new in v0.6.7

- **Canonical list markdown** — Penumbra writes `-` bullets, `1.` ordered rows, and `- [ ]` tasks consistently; save normalizes `*`/`+` and `1)` variants.
- **Toolbar under headings** — Start a list from the toolbar on the blank line after any heading (section headings, not only the note title).
- **Code hygiene** — Four phases of editor-engine cleanup: performance (depth precompute, decoration scans), hide-completed single source of truth, shared callout CSS, and broader test coverage.
- **Editor fixes** — Gutter line-number alignment after rich-block layout; outline hoist behavior with hidden completed tasks.

### What's new in v0.6.6.9

- **Heading/list entry** — Enter and Arrow Up correctly create a visible intro line under note titles and section headings before the first list, including when completed tasks are hidden.
- **Hide-completed stability** — Typing on that intro line no longer reveals hidden completed tasks.
- **List Enter caret** — Enter on a task keeps the caret on the new task row so typing lands on that row, not the one below.
- **Selection + links** — Drag selection can span list row + paragraph as one range; Enter at end of `[[wiki links]]` no longer splits `]]`.

### What's new in v0.6.6.8

- **Graph view** — Fullscreen; ghost nodes for missing `[[links]]`; **Orphans only** filter; saved drag positions; right-click and local-graph entry points; **⌘⇧G** / **Ctrl+Shift+G**. See [docs/graph-view.md](docs/graph-view.md).
- **Editor gutters** — Line numbers use fixed-width digits and stay aligned after mermaid/table previews; hoist buttons stay level with checkboxes when task text wraps.
- **Lists** — **Enter** on an empty bullet no longer deletes a paragraph before the next list; paragraphs between lists no longer show list indent chrome.
- **Note switching** — Faster swaps without breaking hide-completed, gutters, or decorations past the first screen.

### What's new in v0.6.6.7

- **Graph view** — Title-bar graph icon opens a Cytoscape wiki-link map; click a note to open it. Display options: all notes, sidebar filter, or linked only; force/circle/grid layout; labels, arrows, and bidirectional edges; refreshes when filters change.
- **Note list count** — Notes and Todos list headers show how many records match the current filter.
- **Reciprocal wiki links** — Linking note A to B auto-writes a managed **Linked from:** block at the bottom of B with `[[A]]` (removed when the link is deleted).
- **Lists & clipboard** — Completed tasks paste as `[x]` tasks, not open bullets; **Shift-Tab** outdents indented headings; nested list **Enter** inserts after the parent subtree.
- **Editor polish** — Rich-block and wiki-link delete cleanup; slash-menu keyboard navigation; code-block and decoration performance improvements.

### What's new in v0.6.6.6

- **List paste** — Text pasted under a bullet indents to align with the parent row’s content; loose paragraphs already under a bullet render at the same column.
- **Callouts** — Blank lines inside a callout body delete cleanly with Backspace/Delete (including between other body lines).
- **Auto-archive** — Completing the last open task in a note archives it automatically (same as **Note → Archive note**).

### What's new in v0.6.6.5

- **View source** — **View → View source** (⌘⇧E / Ctrl+Shift+E) or **Preferences → General → Editing view** toggles a read-only flat-markdown view (no WYSIWYG chrome); find still works. Editable source is planned — see [editor-source-mode.md](docs/editor-source-mode.md).
- **Manage tags** — **Edit → Manage tags…** or the pencil in the sidebar **Tags** header renames or merges tag paths across all notes (nested tags move with their parent).
- **Import labels** — **File → Import…** dialogs add an optional batch tag (e.g. `import/bear`) and an `imported/YYYY-MM-DD` date tag so imported notes are easy to filter.
- **Markdown links** — Styled `[text](url)` links with context menu (open, edit URL, copy, remove); external URLs open in the system browser; **Enter** at the end of a link no longer breaks the token.
- **Tags & navigation** — **Clear** in the sidebar Tags header when any tag filter is active; stale filters drop when the last tagged note is trashed; trash/delete focuses the next note in the list.
- **Tasks** — Checkbox click targets align with the painted box (ordered tasks no longer miss left of the marker column).

### What's new in v0.6.6.4

- **Note switching** — Faster opens with live-content handoff, deferred WYSIWYG chrome, and batched note load; less flash when reusing the editor between notes.
- **Multi-line toolbar** — Heading, paragraph, and list-type changes apply to every selected row, not just the caret line.
- **Callouts** — New callouts relocate off list rows, code fences, and headings onto a valid line below the block; nested list inserts land after the parent item’s full subtree (see [editor-callouts.md](docs/editor-callouts.md)).
- **Slash menu** — Expanded block list with sections and a callout submenu; `/` is removed on pick or Esc; undo after a slash command closes the menu and strips the restored `/` token (redo still restores the insert).
- **List indents** — 2-space GFM marker step enforced; odd leading spaces snap on load/save and during Tab/outdent/Enter (see [editor-lists.md](docs/editor-lists.md)).
- **Fold & tasks** — Folded completed parents no longer look darker than siblings; outline fold spans include loose body and nested list children; hide-completed scope matches export.

### What's new in v0.6.6.3

- **Ordered lists (WebKit)** — List numbers render reliably in the native app via SVG marker labels; ordered-task rows center the number and align checkbox clicks with the painted box.
- **Tasks** — Checking a task stamps `@done` in one undo step; checkbox clicks and typing `x` both restore cleanly with undo.
- **Typing** — List marker chrome no longer rebuilds on every keystroke during bursts, reducing visual jiggle while typing.
- **Docs** — List editor guide updated for CM6-only behavior and expected deviations from the retired Rich editor.

### What's new in v0.6.6.2

- **Housekeeping** — Legacy `briar` storage keys and CSS class names renamed to `penumbra`; dead Crepe/Milkdown editor CSS removed (~2,700 lines).
- **Editor mount** — CM6 mount styles now target `penumbra-editor-mount` (fixes a class mismatch with `markdownEditor.css`).

### What's new in v0.6.6.1

- **Editor fixes** — List-toolbar multi-paragraph conversion preserves blank lines; sidebar preview skips implicit titles and image-only notes; mermaid **Edit source** reliably reveals the fence.
- **Tests** — Full suite green after Phase 3 cutover.

### What's new in v0.6.6

- **Phase 3 — Crepe retired** — CodeMirror 6 is the only editor. Milkdown/Crepe and ~130 ProseMirror plugins removed; bundle no longer ships `@milkdown/*`.
- **Migration** — Preferences no longer offers Rich vs Markdown; existing `editorMode=rich` settings migrate to markdown on load. Note content on disk is unchanged.
- **Session** — `editorSession.js` is the CM6 session (`createEditorSession`); shared `editorBridge` contract unchanged for menus, todos, and inspector.

### What's new in v0.6.5.9

- **Markdown (beta) typing performance** — Input-first editing: WYSIWYG chrome and rich-block widgets defer rebuilds during typing bursts; autosave/history flush only after a real pause (~650ms). Tier **0–7** debug switch isolates latency (`localStorage penumbra.cmTier`).
- **Save coalescing** — Live content, stats, inspector TOC, and debounced persist are batched so sidebar/search work does not run on every keystroke.
- **Perf diagnostics** — Optional CM6 markers (`localStorage penumbraCmPerf=1`) for engineering bisects.

### What's new in v0.6.5.8

- **Archive** — **Note → Archive note** / **Unarchive**; sidebar **Archive** filter; archived notes are read-only, excluded from All/Todos/Journal/search by default, and tagged with reserved `#archive` for export.
- **Rich blocks (Markdown beta)** — Editable **table** preview (pencil → cells, add/remove rows/columns); **image** form editor (description, URL, **Replace image…**, resize handle); unified **↑**/**↓** navigation across tables, images, mermaid, and block math.
- **Done** — Shared **Done** button on every rich-block preview bar to save and exit edit mode (no need to click outside).
- **Continue below blocks** — Click empty space below the last block or press **↓** at the end to add/focus a blank line for typing.

### What's new in v0.6.5.7

- **Task completion dates (`@done`)** — Checking a task stamps `@done(YYYY-MM-DD)` on the line (Markdown beta and Rich editor); unchecking removes it. Powers the Journal **Tasks completed** section and **Completed only** Todos view.
- **Journal** — Collapsible **Tasks completed** section under **Tasks due**; week-strip markers now show ○ notes, ● tasks due, and ◦ tasks completed (any combination).
- **Todos display** — **View → Tasks in notes & Todos**: **Open only**, **Open and completed**, or **Completed only** (`@done` tasks). **Done** sort in the Todos sidebar. Preference: **General → Tasks in notes & Todos**.
- **Vault backup** — **File → Database → Backup vault…** (ZIP: database + `.penumbra` attachments) and **Backup database…** (SQLite snapshot only).
- **Tag sort** — Cycle button in the sidebar **Tags** header: name A→Z / Z→A, count high→low / low→high (`A↑`, `A↓`, `#↓`, `#↑`).

### What's new in v0.6.5.6

- **Rich blocks (Markdown beta)** — Mermaid live preview, KaTeX math (`$…$` / `$$…$$`), GFM table preview, and image preview with resize. Pencil icon on each preview jumps into source; mermaid hides the duplicate code-block chrome while previewing.
- **WYSIWYG polish (Markdown beta)** — Highlights hide `==` markers; callouts render as cards (title field, fold button, hidden blockquote syntax). Click and drag-select on lines below headings, lists, and callouts align with the painted text (spacing uses in-line `padding-top`, not margins).
- **Core editing (Markdown beta)** — Autosave updates the live-content buffer for todos/search; tab switches flush pending edits; **Enter** on the note title commits and moves to the body (matches rich editor).
- **Callout UX** — Collapse keeps line numbers aligned; **Enter** exits below from the last body row (plain paragraph, no `>` continuation); **↑**/**↓** step through header/body/gaps; delete guards on the first body row; click the header row to edit the title; type label is an italic placeholder until you type; arrow keys and **⌘←**/**⌘→** work in the title field.
- **Inspector TOC** — Click a heading in the TOC panel to jump the beta editor to that section.
- **Preferences** — **Outline → Line numbers (Markdown beta)** toggles the CM6 gutter.

### What's new in v0.6.5.5

- **Phase 2 complete** — The opt-in **Markdown (beta)** editor (CodeMirror 6 + PenumbraMarkdown engine) ships lists, tasks, find/replace, outline fold/hoist, autocomplete, slash menu, callouts, highlights, and a format toolbar. **Rich (default)** is unchanged until Phase 3.
- **Outline** — Section fold, list hoist on every row, paragraph intro-run hoist before task lists, persisted fold state per note; hide completed tasks integrates with outline hiding.
- **Docs** — **[docs/editor-markdown-outline-gutter.md](docs/editor-markdown-outline-gutter.md)** documents fold vs hoist rules for the beta gutter.

### What's new in v0.6.5.4

- **Phase 2 midpoint** — Markdown (beta) gains task checkbox clicks, sidebar complete, list row cycle (**⌘⇧X**), Tab/Shift-Tab list indent, and find/replace. Crepe remains the default editor.

### What's new in v0.6.5.3

- **Phase 1 complete** — Read-side features use the markdown engine: todo extraction, inspector TOC (beta), sidebar preview/search, live-content search while editing, and a markdown outline fold map for Phase 2.

### What's new in v0.6.5.2

- **Phase 0 complete** — PenumbraMarkdown engine now exposes `parse()`, `serialize()`, nested BlockMap indexing, and round-trip tests for wiki links, highlights, callouts, and lists. Export HTML shares the same remark processor.

### What's new in v0.6.5.1

- **Phase 0 list toggles** — Row **bullet**, **numbered**, **task**, and **cycle** changes in the Rich editor now go through the markdown engine first (`src/lib/markdown/`), fixing nested-list regressions when converting ordered rows to bullets (e.g. Meeting outline item 3).
- **Crepe-aware reindent** — Engine preserves deep nested children under bullet parents when Crepe serializes 2- or 3-space indents.

### What's new in v0.6.5

- **Markdown editor (beta)** — **Preferences → General → Editor** offers an opt-in **Markdown (beta)** mode: source editing in CodeMirror with the same save pipeline as the rich editor. **Rich (default)** is unchanged (Crepe WYSIWYG).
- **Editor migration plan** — **[docs/editor-migration-markdown-engine.md](docs/editor-migration-markdown-engine.md)** documents the phased move to a markdown-authoritative engine; Phase 2 (beta CM6 editor) is complete in v0.6.5.6.

### What's new in v0.6.4

- **Outline fold fixes** — Collapsing a bullet row shows **one line** of that row (not the whole paragraph). Foldable paragraphs above a list clip to one line when collapsed. Escaped lines and nested lists under the last row in a section hide correctly.
- **Stability** — Fixed empty bullet rows after fold (chevron with no label) and an editor hang that could occur after opening a note.

### What's new in v0.6.3

- **Recovery bundle** — **Preferences → Sync server → Encryption**: export/import a password-protected `.penumbra-recovery.zip` with your vault sync key and collection join secrets (recommended over copying the raw E2E key alone).
- **E2E recovery key** — **Show/Hide E2E recovery key** on the encryption row; label **E2E recovery key (save offline)** when visible.
- **Print preview** — Long notes show stacked letter-size pages with **Page X of Y** labels; pagination matches system print margins more closely.

### What's new in v0.6.2

- **Assistant** — **Inspector → Assistant** chats about the open note via local **Ollama**; configure model and optional Tavily web research in **Preferences → Assistant**.
- **Collections** — **Leave collection** confirms before acting; **Left collections (rejoin)** lists ids in **Sync server** inspector and **Preferences**; rejoin uses saved passphrases; **Show all collections** lists joined, local, and server-discovered groups.
- **Sharing UI** — Share id hidden from menus and inspector; collection id remains for join/rejoin. **Copy** buttons reset after two seconds.
- **Docs** — **[docs/keys-and-secrets.md](docs/keys-and-secrets.md)** catalogs keychain items, E2E keys, and sync credentials.

### What's new in v0.6.1

- **Recovery kit** — **Show E2E recovery key** in **Preferences → Sync server → Encryption** displays the kit again after first setup (store it offline for new devices).
- **Sync clarity** — Toasts and the **Sync server** activity log include note titles when a specific note is involved.
- **Edit-aware sync** — Backup and shared notes do not push while you are actively editing; push runs when you leave the note.
- **Sync menu** — Removed per-note backup **Push/Pull** (sync is automatic). Activity log uses menu-aligned labels and local timestamps.
- **Inspector** — Rail highlight stays on the panel you selected (no silent fallback to **Journal** when a note-only panel is unavailable).

### What's new in v0.6.0

- **Shared collection sync** — Edits in a shared collection on one machine now sync reliably to others via auto-sync and **Sync → Sync collection**. Conflicts prompt only when the server actually advanced since your last sync and your local copy differs; if you're ahead locally, the app pushes instead.
- **Collection sync status** — Sidebar dots per collection (syncing, pending, up to date, error, conflict), a status-bar summary when shared sync is on, and per-collection lines in the **Sync server** inspector.
- **Mandatory E2E** — Sync always encrypts payloads end-to-end; there is no non-encrypted sync mode. A **recovery kit** is shown when you first connect a vault.
- **Editor** — Paragraph lines below a list align consistently with the first line (not only the first paragraph in the run).

### What's new in v0.5.9

- **E2E encrypted sync** — **Preferences → Sync server**: opt-in **Encrypt sync payloads (E2E)** per vault. Note bodies are encrypted before upload; the server stores ciphertext only. Enabling shows a one-time **recovery kit** to save offline. Requires a sync server with API **v2** (migration 005).
- **Shared subscription sync** — **Sync shared subscriptions automatically** in **Preferences → Sync server** reconciles collections in the background (push after idle, pull on open). Notes not in a collection stay manual — see the table below.
- **Lists** — **Enter** twice on an empty row in the middle of a list inserts a plain paragraph between the halves. Numbered lists renumber correctly after a split; selecting a continuation block and pressing **numbered list** restarts at **1.**, **2.**, **3.** Outline list markers and nested alignment are tighter.
- **Sharing UI** — **Share note…** and **Join shared collection…** flows updated; **Sync server** inspector shows more vault and subscription detail.

### What's new in v0.5.8

- **Backup sync & shared sync** — Clear split between private vault backup and cross-vault sharing. **Preferences → Sync server** toggles **Enable backup sync** and **Enable shared sync** independently; each note uses one path (shared wins over backup).
- **Sync menu** — New top-level **Sync** menu (between **Outline** and **Help**) when connected: share/join/subscription actions, backup and shared push/pull, and **Sync server settings…**. **Alt+S** opens it when visible.
- **Sync server inspector** — Vault-wide connection, capabilities, backup summary, and subscription reconcile on the inspector rail (hidden when not connected). Per-note sync state stays in **Statistics**.
- **Note list** — Context menu: **Share note…** (when shared sync is enabled).
- **Inspector** — Hidden or unavailable panels fall back to **Journal** (e.g. disconnecting while **Sync server** is open).

### What's new in v0.5.7

- **Tasks in notes** — **View → Tasks in notes & Todos** chooses **Open only**, **Open and completed**, or **Completed only** (`@done` tasks). In **Open only**, finished rows hide in the editor unless a completed parent still has open nested tasks (muted until the subtree is done or you switch mode).
- **Tags footer** — **↑** / **↓** and **Enter** select tag suggestions when adding tags below the editor.
- **Status bar** — Shows the database file name; hover for the full path.
- **Version history** — **Changes** diff vs the current note in the inspector; **Expand** opens a larger preview/diff modal.
- **Menus** — Shorter **Edit** and **View** labels; **File → Import…** submenu (like **Export…**); **Privacy blur**, **Completed tasks**, and layout toggles in **View**; **dark mode** and **tabs** only in **Preferences → General** (title bar still toggles theme).
- **About** — **Help → About Penumbra** with tagline *Private by default. Markdown at heart. Yours alone.*

### What's new in v0.5.6

- **Lists** — Select several body paragraphs and use the toolbar **bullet** or **numbered** button to merge them into one list (same as **task**). Each row keeps a proper paragraph shell for caret and indent.
- **Tag filters** — Active filter pills in the sidebar show **×** to remove one tag; **Clear** appears in the Tags header when any tag filter is active. **Clear filter** was removed from the note list header.
- **Accessibility** — Preferences tabs, note list rows, journal month picker, and the note context menu satisfy Svelte a11y checks (clean production build).

### What's new in v0.5.5

- **Lists** — Tasks on the line below the note title use Milkdown’s wrap path (caret stays in the task row). Multi-line **task** merges keep proper row structure so every checklist line supports caret, checkbox, and **Tab** indent.
- **Contributors** — List/task editing conventions documented in [docs/editor-lists.md](docs/editor-lists.md).

### What's new in v0.5.4

- **Penumbra Notes** — App rebrand with new icons, window title, and bundle id **`com.penumbra.notes`** (macOS app data: `~/Library/Application Support/com.penumbra.notes/`).
- **Note tags** — Tags live in note metadata and are edited in a **Tags** footer below the editor (add, remove, click to filter the sidebar). Typing `#` still opens autocomplete; choosing a tag adds it to the note without leaving a hashtag in the body. Optional **mirror** adds a trailing `#tag` line in markdown (**Preferences → General**).
- **Outline** — Top-level **paragraphs** with content below them can fold like section headings (chevron hides blocks until the next heading). Lists under `##` sections align consistently; fold/hoist no longer blocks clicking task checkboxes or list row text.
- **Lists** — **Tab** / **Shift+Tab** indent and outdent **nested** list items; **Shift+Tab** on a top-level row no longer turns a task into a plain paragraph. Select several lines and use the toolbar **task** button to make one checklist of sibling `- [ ]` rows (every row remains editable). Tasks on the line below the note title use the same reliable wrap path as other body lines.
- **List row toggle polish** — Row-level list type changes now target the current nested row (not the parent level), numbered row toggles keep sequential numbering, and toggling back to bullet/numbered auto-merges split fragments so you do not need delete/backspace to rejoin.
- **Task checkboxes** — Bullet and ordered task markers toggle reliably with outline chevrons and hoist enabled.
- **Blank line above a list** — **↑** at the start of the first list row inserts a paragraph above the list (e.g. between the title and a list).
- **Tasks in the editor** — Checked `- [x]` rows use strikethrough (like **Todos**). **Open only** hides completed rows unless a completed parent still has open nested tasks—the parent stays visible but muted until you finish the subtree or change the display mode.
- **Linked from** — Backlinks panel is collapsible and stays **collapsed** when there are no backlinks.
- **Autocomplete near the screen edge** — Tag, wiki, date, and slash menus stay on screen (flip above the caret when there is no room below).
- **Database dialogs** — **Open** / **Create database** default to your **Documents** folder.
- **Version history** — Inspector panel refreshes only when a new revision is saved (no flash on every keystroke).
- **Privacy blur** — **View → Privacy blur** (shortcut unchanged: **⌘⇧B** / **Ctrl+Shift+B**).

### What's new in v0.5.2

- **Highlight** — Obsidian-style `==highlight==` in the editor; toggle from the floating toolbar or top bar, **⌘⌥H** / **Ctrl+Alt+H**, and reliable paste from markdown; HTML/PDF export renders `<mark>`.
- **Stability** — Fixed store module import cycles so settings and inspector tests load cleanly; note list date grouping tests use a stable clock.

### What's new in v0.5.1

- **Journal** — Week/day navigation, **Jump to…** month/year picker, week-strip markers (○ / ● / ◉), and collapsible **Tasks due**, **Notes**, and **Upcoming** (see [Inspector panels](#inspector-panels)).
- **Preferences** — Sidebar layout: **General**, **Reminders**, **Privacy**, **Inspector**, **Outline**, **Sync server**; inspector rail order and backlinks location on the **Inspector** pane.
- **Inspector** — Shared panel styling, refreshed rail and panel chrome, clearer section labels across panels.

---

## At a glance

- **Beautiful writing** — WYSIWYG markdown editor with headings, lists, tasks, tables, math, images, code, Mermaid diagrams, Obsidian-style callouts, and `==highlight==` marks.
- **Tags & search** — Per-note tags in metadata (footer editor + sidebar tree); `#` autocomplete; nested sidebar folders; search titles, body, tags, or tasks.
- **Todos in one place** — Open, all, or completed-only tasks from every note, grouped by note, with due dates, `@done` completion dates, and reminders.
- **Note links** — `[[Note Title]]` links between notes; backlinks can be shown below the editor or in the inspector.
- **Outline tools** — Collapse sections and lists, indent guides, and “hoist” to focus on one branch.
- **Right inspector** — Outline, Statistics, Version history, Reminders, Journal, and optional **Assistant** in a resizable right rail (panels load on demand).
- **Local AI assistant (optional)** — Ask questions about the open note via **Ollama** on your machine. Setup: **[docs/ai-assistant-ollama-guide.md](docs/ai-assistant-ollama-guide.md)**.
- **Your data, local** — SQLite database file; optional passphrase encryption. No cloud account required.
- **Optional backup sync** — Back up marked notes to your own **[penumbra-notes-sync-api](penumbra-notes-sync-api/)** server (e.g. on Fly.io); manual push/pull or automatic sync per note. See **[docs/penumbra-notes-sync-api-self-host.md](docs/penumbra-notes-sync-api-self-host.md)** to deploy a server.
- **Shared notes & subscriptions** — Link notes across different vaults and group them under named subscriptions on the same server. User guide: **[docs/sharing-and-subscriptions-guide.md](docs/sharing-and-subscriptions-guide.md)**.
- **Privacy blur** — Hide editor and inspector behind an opaque overlay (**⌘⇧B**) for shoulder-surfing; separate from locking the database.

---

## The workspace

| Area | What it does |
|------|----------------|
| **Sidebar** | Tag tree with sort cycle (**A↑** / **A↓** / **#↓** / **#↑**), multi-tag filter (**All** / **Any**), **Recent notes** (up to five), **All notes**, **Todos**, **Untagged**, **Backup sync** and **Shared notes** (when sync enabled), **Trash** |
| **Note list** | Search, **Sort by** (updated / created / title), date-grouped rows, pin notes, keyboard navigation (↑/↓, Enter), resize |
| **Editor** | The active note with toolbar, tabs (optional), find/replace, **Tags** footer, **Linked from** (backlinks) |
| **Inspector** | Optional right rail: Outline, Statistics, Sync server (when connected), Version history, Reminders, Journal (and optional Backlinks) |
| **Menus** | **File** (**Import…**, **Export…**, database), **Edit**, **View**, **Outline**, **Sync** (when connected), **Help** (shortcuts, about) |

Layout: **View** (sidebar, inspector, status bar, privacy blur, tasks display mode, line spacing, quick open, focus search) or overlapping items in **Preferences**. **Dark mode** and **tabs** are in **File → Preferences… → General** (title bar still toggles theme with **Ctrl/Cmd+D**). Inspector rail, outline chrome, reminders, and sync server settings have their own preference panes. Outline commands: **Outline** menu.

Toggle the inspector from **View → Inspector** or the title-bar inspector icon (left of theme).

---

## Inspector panels

Panels share consistent section labels and spacing. The rail highlights the active panel; each panel title uses an accent underline.

- **Outline** — Table of contents for the active note; click a heading to jump the editor to that section.
- **Statistics** — Live words/chars/lines, reading time, open tasks, tags, created/updated metadata, and per-note sync ids/state.
- **Sync server** — When connected: server URL, vault id, backup/shared capabilities, marked-note counts, and subscription reconcile (rail icon hidden when disconnected).
- **Version history** — Browse automatic snapshots and restore an earlier revision (**File → Version history…**).
- **Reminders** — Open due tasks grouped by **Overdue**, **Today**, and **Upcoming**; click to open and focus.
- **Journal** — Calendar-style view for a single day (see below).
- **Backlinks** — When enabled below the editor or in **File → Preferences… → Inspector**, **Linked from** lists notes that link here (collapsible; collapsed when empty).

### Journal

- **Navigate** — `«` / `»` move by week; `‹` / `›` move by day. The toolbar shows **month and day** (e.g. May 31). **Today** jumps to the current date. **Jump to…** opens a year stepper and 12-month grid (keeps the same day-of-month when possible; clamps at month end).
- **Week strip** — Seven days for the week containing the selected date; tap a day to select it. Markers under a day summarize activity (table below).
- **Sections** (top to bottom, each collapsible; open/closed state is saved per database):
  - **Tasks due** — Open tasks with a due date on the selected day; click to open the note and focus the task.
  - **Tasks completed** — Tasks with `@done(YYYY-MM-DD)` on the selected day (strikethrough in the list).
  - **Notes** — Notes that mention the selected date with `@YYYY-MM-DD` in prose (not on task lines).
  - **Upcoming** — Next dated notes and tasks after the selected day.

**Week strip markers** (shown side by side when multiple apply)

| Marker | Meaning |
|--------|---------|
| ○ (hollow ring) | Note `@YYYY-MM-DD` in prose |
| ● (solid accent dot) | Open task due that day |
| ◦ (small muted dot) | Task completed that day (`@done`) |

Tips:
- Use the inspector icon to quickly show/hide the rail while writing.
- Collapse sections you do not need to keep the panel compact.
- The inspector remembers open state, width, active panel, and icon order per database (**File → Preferences… → Inspector**).

## Preferences

**File → Preferences…** uses a sidebar:

| Pane | Settings |
|------|----------|
| **General** | Sidebar, dark mode, status bar, editor tabs, line spacing, tasks in notes & Todos (open / all / completed only), optional tag mirror line |
| **Reminders** | System notifications for task due dates |
| **Privacy** | Hide note content (blur) scope and shortcut |
| **Inspector** | Backlinks below editor vs inspector; reorder rail panels |
| **Outline** | Indent guides, fold chevrons, hoist button |
| **Sync server** | Server URL, API key, backup/shared capabilities, automatic sync |

The dialog keeps a stable size while switching panes. Your last pane is remembered for the session.

---

## Writing & formatting

- **Headings** — Use the style menu or `Ctrl/Cmd+Alt+1`–`6`; type `#` + space at line start.
- **Tasks** — `- [ ] ` for checklists; they show up in the **Todos** sidebar. Completing a task adds `@done(YYYY-MM-DD)` on that line (removed when unchecked). Use the toolbar **task** control (checkbox icon) on the current line, or **select several lines** and click **task** once to turn them into sibling checklist rows. See [Lists & tasks](#lists--tasks) if lines look misaligned or checkboxes stop responding.
- **Tags** — Per-note tags in the **Tags** footer (chips, add field, click a chip to filter the sidebar). **Edit → Manage tags…** renames or merges tags vault-wide. Type `#` in the body for autocomplete; picking a tag adds it to note metadata (the in-progress `#token` is removed). Hashtags you type manually in prose are not added automatically. Optional **Mirror note tags as a trailing #tag line** in **Preferences → General**. Select multiple tags in the sidebar; use **All** or **Any** when two or more are active; **Clear** resets filters.
- **Dates** — Type `@` for presets and a calendar; use on task lines for due dates and reminders.
- **Slash menu** — In an empty paragraph, type `/` for heading, task, code, divider, or callout blocks.
- **Code blocks** — Use standard markdown fences (`` ```json ``, `` ```javascript ``, `` ```rust ``, etc.) so the language dropdown and highlighting apply—especially when pasting from other apps. Custom formats like `</> Json` are not recognized. See **[docs/code-blocks.md](docs/code-blocks.md)**.
- **Callouts** — Colored note/tip/warning boxes (`> [!note]` style) with optional titles and fold.
- **Highlight** — Wrap text in `==highlight==` (Obsidian-style), or select text and use the floating toolbar, **⌘⌥H** / **Ctrl+Alt+H**, or the top-bar highlight control.
- **Links** — `[[Another Note]]` wiki links open linked notes (autocomplete after `[[`). Markdown `[label](url)` links are styled in the editor; right-click for open, edit URL, copy, or remove; external URLs open in your default browser.

---

## Outline: fold, hoist, and collapsed sections

- **Fold (▼ / ▶)** — Collapse a **section heading**, a **paragraph** with content below it (until the next heading), or a **nested list item** to hide everything under it. Shortcut: **Ctrl/Cmd+Shift+.** (**Outline → Fold line**); **Fold all** / **Unfold all** in the **Outline** menu.
- **Hoist (◎)** — Temporarily show only one heading or list branch. **Outline → Hoist here** or **Ctrl/Cmd+Shift+H**; **Unhoist** with **Ctrl/Cmd+Shift+0** or **Outline → Unhoist**.
- **Collapsed sections** — Close a section chevron to hide its body. Press **Enter** at the end of the heading to add lines without expanding; click the empty area **below your note** to jump to the end and keep typing.
- **Note title** — The first heading in a note is the title (no fold/hoist on that line).
- **Blank line above a list** — Put the caret at the **start of the first list row** and press **↑** to insert a paragraph above the list (e.g. between the title and a list). Same **↑** behavior works on the first line of code blocks and other barrier blocks.

Turn off chevrons or hoist buttons in **File → Preferences… → Outline** if you prefer a cleaner gutter; shortcuts and the **Outline** menu still work.

---

## Lists & tasks

### What you should see

A **checklist under a section** is one list: every row shares the same marker column (checkbox, bullet, or number), then the text. **Tab** indents a row under the one above; **Shift+Tab** moves an **indented** row back out one level.

**Separate paragraphs** look like normal body lines—no shared checkbox column, uneven spacing, and **Tab** does not nest them as list items. Only some lines may appear in **Todos** if only some were ever tasks.

### Quick fixes

| Problem | What to do |
|--------|------------|
| Several lines should be one checklist | **Select all lines** → toolbar **task** (checkbox) |
| One line should be a task | Caret on the line → **task** |
| Row is nested too deep | **Shift+Tab** until it lines up with siblings |
| Row should nest under the line above | **Tab** |
| Cannot click or type in tasks | Expand any **▶** fold on the section or list row; turn off **hoist** (◉) if the rest of the note is hidden |
| Still wrong after editing | Select the block → **task** again, or paste clean markdown (see below) |

Example markdown for five sibling tasks:

```markdown
## Do

- [ ] line one
- [ ] line two
- [ ] line three
```

**Export markdown** (**File → Export…**) to verify structure: sibling tasks repeat `- [ ]` at the **same** indent; separate paragraphs have blank lines between them and no leading `-`.

---

## Todos & reminders

- Open **Todos** in the sidebar to see tasks from every note (filtered by display mode).
- **Tasks display** — **View → Tasks in notes & Todos** or **Preferences → General**: **Open only** (default), **Open and completed**, or **Completed only** (tasks with `@done`). **Open only** hides completed `- [x]` rows in the editor and Todos list except muted completed parents with open nested tasks. Sort by **Done** to order completed tasks by `@done` date.
- Check off from the list, or click task text to open the note at that line. Completion stamps `@done(today)` on the task line.
- Add `@2025-06-15` or `@2025-06-15T14:30` on the same line as a task for a due date.
- Penumbra Notes can send **system notifications** when a reminder is due (enable when prompted on macOS).

---

## Organizing notes

- **Version history** — **File → Version history…** opens the **Version history** inspector panel to browse snapshots, preview or diff against the current note (**Changes**), expand in a large modal, and restore an earlier revision.
- **Pin** important notes so they stay at the top of the list.
- **Trash** — Soft delete, restore, or delete permanently; empty trash when ready.
- **Import** — **File → Import…** → Markdown (files or folders) or TextBundle/TextPack. Optional **batch tag** and **import date tag** (`imported/YYYY-MM-DD`) label every note in that import session.
- **Export** — PDF, HTML, Markdown (all notes or by tag, with optional YAML `tags:` frontmatter from metadata), or TextBundle from **File → Export…**; **Print** for preview. With tag mirror enabled, exported markdown can also include a trailing `#tag` line in the body.

---

## Sync server (optional)

Penumbra Notes can sync **individual notes** you mark to a server running **[penumbra-notes-sync-api](penumbra-notes-sync-api/)** — typically on [Fly.io](https://fly.io). You host the server and API key. A **hosted multi-tenant** sync product (sign-in, MFA, per-account isolation) is on the [roadmap](docs/roadmap.md) but not shipped yet.

1. Deploy **penumbra-notes-sync-api** using **[docs/penumbra-notes-sync-api-self-host.md](docs/penumbra-notes-sync-api-self-host.md)** (file list + Fly.io steps).
2. In Penumbra Notes: **File → Preferences… → Sync server** — enter server URL and API key, **Save connection**, enable **Enable backup sync** and/or **Enable shared sync** as needed. Turn on **Back up marked notes automatically** for background backup sync. The API key is stored in the **system keychain**, not in your notes database or config files.
3. In the note list, click the **server icon** on each note to mark it for backup (or use the context menu).
4. Use **Backup sync** in the sidebar to see only marked notes. With **Back up marked notes automatically** on, changes push after you stop editing and pull when you open a note.

Sync requires an unlocked database. Conflicts show a dialog to keep your copy or use the server version.

### Shared notes and subscriptions (v0.6.0+)

Cross-vault sharing uses the same server and API key, but is separate from backup sync:

1. **Sync → Share note…** — link one note to other vaults by adding it to a **collection** (or enable backup sync for the same vault on other devices).
2. **Sync → Join shared collection…** on another vault (paste the **collection id**).
3. **Sync → New shared collection…** — create a named group; use **Sync → Sync collection** to import notes others have added.

**Sync menu** (when connected; **Alt+S** / **⌥S**): see **[docs/sharing-and-subscriptions-guide.md](docs/sharing-and-subscriptions-guide.md#sync-menu-reference)** for each item, when it is enabled, and how to use it.

| Command | Purpose |
|---------|---------|
| **Share note…** | Share the open note (collection or backup path), or view/add collection membership |
| **Sync collection** | Reconcile one collection — import notes others added (open a note in the group or select it in the sidebar) |
| **Remove from collection…** | Stop sharing the open note on this vault, or move it to another collection |
| **Leave collection…** | This vault leaves the whole collection (open a note in that group first) |
| **Join shared collection…** | Join by collection id; includes **Rejoin on this vault** for collections you left |
| **New shared collection…** | Create a new collection |
| **Sync server settings…** | **Preferences → Sync server** |

There are no per-note backup or shared **Push** / **Pull** items — sync runs automatically.

**Automatic sync**

| Kind | When it syncs |
|------|----------------|
| **Backup-marked notes** (server icon) | **Back up marked notes automatically** on: push after you leave the note (not while actively editing), pull when you open the note |
| **Shared notes in a collection** | **Sync shared subscriptions automatically** on: background reconcile, push after idle, pull on open |
| **Shared notes not in a collection** | Push after you leave the note; pull when you open the note |

Use **Sync → Sync collection** to manually reconcile a collection (e.g. import new notes added by others).

Full walkthrough: **[docs/sharing-and-subscriptions-guide.md](docs/sharing-and-subscriptions-guide.md)**.

---

## Privacy & storage

- **First launch** — If no vault is open, Penumbra Notes shows a welcome screen with **Open database…** and **Create database…**. Your last opened vault reopens automatically on later launches.
- **Notes vault** — Each collection of notes is a single **`.db`** file (SQLite, optional SQLCipher). Open, create, move, **close**, or **backup** the active vault from **File → Database** (**Backup vault…** includes `.penumbra` attachments; **Backup database…** is SQLite only).
- **App settings** — Global data (which vault was last opened, window size, sync server URL, sync registration per vault) is stored in **`penumbra-notes-system.db`** in the app config folder. On macOS that folder is `~/Library/Application Support/com.penumbra.notes/` (`penumbra-notes-system.db` and a small `config.json` bootstrap file).
- **Encryption** — Optional SQLCipher passphrase (**File → Enable encryption…**). **Lock database** (encrypted vaults) keeps the path and requires your passphrase again; **Close database** unloads the vault entirely.
- **Privacy blur** — **View → Privacy blur** or **⌘⇧B** / **Ctrl+Shift+B** (customizable in **Preferences → Privacy**). Opaque overlay on the editor and/or inspector for the current session only; not a substitute for encryption.
- Per-vault UI settings (sort order, view options, inspector layout) are stored inside the active **`.db`** file.

---

## Keyboard shortcuts

| Action | Windows / Linux | macOS |
|--------|-----------------|-------|
| New note | Ctrl+N | ⌘N |
| Save | Ctrl+S | ⌘S |
| Quick open | Ctrl+K | ⌘K |
| Focus search | Ctrl+L | ⌘L |
| Privacy blur | Ctrl+Shift+B | ⌘⇧B |
| View source (read-only) | Ctrl+Shift+E | ⌘⇧E |
| Note list: move / open | ↑ / ↓, Enter | ↑ / ↓, Enter |
| Find in note | Ctrl+F | ⌘F |
| Replace… | Ctrl+Alt+F | ⌘⌥F |
| Duplicate | Ctrl+Shift+D | ⌘⇧D |
| Pin / unpin | Ctrl+Shift+P | ⌘⇧P |
| Move to Trash | Ctrl+Backspace | ⌘⌫ |
| Import Markdown (File → Import…) | Ctrl+I | ⌘I |
| Print | Ctrl+P | ⌘P |
| Toggle sidebar | Ctrl+\\ | ⌘\\ |
| Toggle inspector | View menu / title-bar button | View menu / title-bar button |
| Toggle theme | Ctrl+D | ⌘D |
| Fold outline line | Ctrl+Shift+. | ⌘⇧. |
| Fold / unfold all | Outline menu | Outline menu |
| Hoist branch | Ctrl+Shift+H | ⌘⇧H |
| Unhoist | Ctrl+Shift+0 | ⌘⇧0 |
| Close tab (when tabs on) | Ctrl+W | ⌘W |
| Cycle tabs | Ctrl+Tab | ⌘Tab |
| Heading 1–6 | Ctrl+Alt+1 … 6 | ⌘⌥1 … 6 |
| Indent list (nest row) | Tab | Tab |
| Outdent list (nested row only) | Shift+Tab | ⇧Tab |
| Open menu | Alt+F / E / V / O / S / H | Alt+F / E / V / O / S / H |

Press **Escape** to close open menus, or open **Help → Keyboard shortcuts** for the full list (including **Edit → Restore** in Trash view). More detail is in **[changelog.md](changelog.md)**.

---

## Building from source

Developers: see **[changelog.md](changelog.md)** for prerequisites, `npm run tauri:dev`, tests, project layout, and the full feature specification.

```bash
npm install
npm run tauri:dev    # development
npm run tauri build  # production installer
```
