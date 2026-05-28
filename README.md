# Tsumugi — 紡

> AI-powered local text editor for Windows. A clean-room reimagining of
> [Sakura Editor](https://sakura-editor.github.io/) with first-class AI
> assistance built in.

Tsumugi (紡 — "to spin / weave words") runs as a native Windows app
(Tauri 2 shell + WebView2). No browser required, no network required
for editing.

> Formerly known as **Sumi**. Renamed in v1.11.

## Download

**One-click direct download — Windows x64:**

- 📥 **[Tsumugi_1.11.6_x64-setup.exe](https://github.com/foxlabo/tsumugi/releases/download/v1.11.6/Tsumugi_1.11.6_x64-setup.exe)** — NSIS installer (recommended)
- 📥 **[Tsumugi_1.11.6_x64_en-US.msi](https://github.com/foxlabo/tsumugi/releases/download/v1.11.6/Tsumugi_1.11.6_x64_en-US.msi)** — MSI installer

Other versions and full release notes:
[Releases page](https://github.com/foxlabo/tsumugi/releases).

> The GitHub-generated `Source code (zip/tar.gz)` archives attached to
> each release contain only this repo's `README.md` and `LICENSE` —
> ignore those. The Windows installers are the `.exe` / `.msi` links
> above.

The binaries are unsigned, so Windows SmartScreen warns on first
download and first run:

- **In Edge / Chrome**: click the `…` menu on the download warning →
  *Keep*, then *Keep anyway*.
- **On launch**: click *More info* → *Run anyway*.

This is normal for installers from publishers without an
[Authenticode certificate](https://learn.microsoft.com/en-us/windows/win32/seccrypto/cryptography-tools);
the warning will subside as more downloads accumulate.

## Features

### Text editor (Sakura-replacement core)

- **Multiple tabs** with drag-to-reorder, pinning, context menu, inline rename.
- **Syntax highlighting** for 30+ languages via the Monaco engine.
- **Per-tab language switching** from the status bar — useful for
  forcing `.md` into plain text, or vice versa.
- **Automatic character-encoding detection** (UTF-8, UTF-16 LE/BE,
  Shift_JIS, EUC-JP, ISO-2022-JP, GBK, …).
- **Line-ending conversion** between CRLF / LF / CR; auto-detect on open.
- **Find & replace** with full regular-expression support
  (`Ctrl+F` / `Ctrl+H`).
- **Grep across folders** — embedded `ripgrep` with text-export of hits.
- **Bookmarks, rectangular selection** (Alt+drag), multi-cursor
  (Ctrl+click).
- **File watcher** for detecting external changes.

### Markdown

- **Live preview pane** (`Ctrl+Shift+V`).
- **Insertion menu** with 19 built-in snippets + user-defined templates
  (`Ctrl+Alt+M`).
- **Table formatter** — auto-align pipe tables, East-Asian-Width aware
  (`Ctrl+Alt+T`).
- **HTML / PDF / Word (`.docx`) export.**

### Files & navigation

- **File tree sidebar** with right-click menu
  (create / rename / delete / reveal in Explorer).
- **Favourites** for pinning frequently-opened files.
- **Recent files (MRU)** with session restore on launch.
- **Outline panel** — function / heading list for the active file.
- **Split view** of the same file.
- **Windows "Open with..."** — registered as a file-association
  handler for `.txt` / `.md` / `.json` / `.log` / `.env` / `.conf` /
  `.yaml` / `.toml` / `.ini` etc. Right-click any of those in Explorer
  and pick "Open with → Tsumugi".

### Customisation

- **Light / Dark / System theme.**
- **User-defined Markdown snippets** + custom Monarch grammars +
  autocomplete dictionary.
- **Custom keybindings** edited from the in-app settings modal.
- **Default new-file extension** (`.txt` for general use, `.md` for
  notes, …).

### AI panel

The AI panel routes to multiple providers, switchable per ask:

| Provider | Type | Auth |
|---|---|---|
| **OpenAI** | HTTP / SSE | API key |
| **Anthropic** | HTTP / SSE | API key (with prompt caching) |
| **Google Gemini** | HTTP / SSE | API key |
| **OpenAI-compatible** (Ollama / LM Studio / Grok / Together / OpenRouter / Fireworks / vLLM / …) | HTTP / SSE | base URL + optional key |
| **Claude Code CLI** | subprocess | none (uses your Claude Code subscription) |
| **Codex CLI** | subprocess | none (uses your Codex subscription) |
| **Gemini CLI** | subprocess | none |

Optional **"include all open tabs"** mode for cross-file Q&A
(opt-in — defaults off for privacy).

- For full-offline use, run [Ollama](https://ollama.ai) and point the
  "OpenAI-compatible" provider at `http://localhost:11434/v1` — no
  network access required at all.
- API keys are stored locally in the OS app-data folder and are only
  sent to the corresponding provider's own endpoint. Tsumugi has no
  servers and no telemetry.

## Privacy

- 100% local. No telemetry, no analytics, no remote logging.
- The WebView is locked down via a restrictive Content-Security-Policy
  to specific AI-provider endpoints only.
- Saves use a staging temp file + atomic rename + per-canonical-path
  mutex so two concurrent writes never corrupt your file.

## Source code

The source code is hosted privately. The Windows installers attached to
this repository's releases are free to download, install, and
redistribute under the MIT license.

If you're interested in the code (security audit, integration,
licensing enquiries), reach out via the
[issue tracker](https://github.com/foxlabo/tsumugi/issues).

## License

[MIT](LICENSE) — see the LICENSE file for the full text. The license
covers the binary releases; it does not grant access to the source
repository.
