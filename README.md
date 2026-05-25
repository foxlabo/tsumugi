# Sumi — 墨

> AI-powered local text editor for Windows. A clean-room reimagining of
> [Sakura Editor](https://sakura-editor.github.io/) with first-class AI
> assistance built in.

Sumi runs as a native Windows app (Tauri 2 shell + WebView2). No browser
required, no network required for editing.

## Download

Grab the latest installer from the [Releases page](https://github.com/foxlabo/sumi/releases/latest):

- **`Sumi_1.2.2_x64-setup.exe`** — NSIS installer (recommended, ~3 MB)
- **`Sumi_1.2.2_x64_en-US.msi`** — MSI installer (~4 MB)

The binaries are unsigned, so Windows SmartScreen warns on first download
and first run:

- **In Edge / Chrome**: click the `…` menu on the download warning →
  *Keep*, then *Keep anyway*.
- **On launch**: click *More info* → *Run anyway*.

This is normal for installers from publishers without an
[Authenticode certificate](https://learn.microsoft.com/en-us/windows/win32/seccrypto/cryptography-tools);
the warning will go away once enough downloads accumulate.

## Features

### Text editor (Sakura-replacement core)

- **Multiple tabs** for opening many files at once.
- **Syntax highlighting** for 30+ languages via the Monaco editor engine.
- **Automatic character-encoding detection** (UTF-8, UTF-16 LE/BE,
  Shift_JIS, EUC-JP, ISO-2022-JP, GBK, …).
- **Line-ending conversion** between CRLF / LF / CR; auto-detect on open.
- **Find & replace** with full regular-expression support.
- **Grep across folders** — embedded `ripgrep`.
- **Bookmarks, rectangular selection, multi-cursor** (Alt+Shift+drag).
- **File watcher** for detecting external changes.

### AI

The AI panel routes to **seven providers**, switchable per ask:

| Provider | Type | Auth |
|---|---|---|
| **OpenAI** | HTTP / SSE | API key |
| **Anthropic** | HTTP / SSE | API key (with prompt caching) |
| **Google Gemini** | HTTP / SSE | API key |
| **OpenAI-compatible** (Ollama / LM Studio / Grok / Together / OpenRouter / Fireworks / vLLM / …) | HTTP / SSE | base URL + optional key |
| **Claude Code CLI** | subprocess | none (uses your Claude Code Max subscription) |
| **Codex CLI** | subprocess | none (uses your Codex Plus subscription) |
| **Gemini CLI** | subprocess | none |

- For full-offline use, run [Ollama](https://ollama.ai) and point the
  "OpenAI-compatible" provider at `http://localhost:11434/v1` — no
  network access required.
- API keys are stored locally in `%APPDATA%\sumi\settings.json` and are
  only sent to the corresponding provider's own endpoint.

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

If you're interested in the code (e.g. for security audit, integration,
or licensing inquiries), reach out via the
[issue tracker](https://github.com/foxlabo/sumi/issues).

## License

[MIT](LICENSE) — see the LICENSE file for the full text. The license
covers the binary releases; it does not grant access to the source
repository.
