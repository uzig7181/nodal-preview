# Nodal Preview — tester guide (beta 0.2.0)

Nodal is a Windows desktop workspace for AI coding agents and terminals. This is a **beta** for invited testers. Expect rough edges, and thank you for testing it.

## Before you install

| Requirement | Detail |
|---|---|
| System | Windows 10 or 11, 64-bit. Not macOS or Linux in this beta. |
| A provider | At least one of: **Codex** (`npm install -g @openai/codex`, then sign in once with `codex`), **Claude Code** (install, then sign in once with `claude`; or set `ANTHROPIC_API_KEY` for your user), **Ollama** (install, then `ollama pull <model>`). Nodal uses your own accounts and plans. |
| Smart App Control | If Windows Security → App & browser control → **Smart App Control** is **On**, Windows can block this unsigned beta. Nodal does not ask you to change this setting. |

The installer is **not code-signed**. Windows SmartScreen shows "Windows protected your PC". Select **More info**, then **Run anyway**, only if the SHA-256 matches the value on the download page:

```powershell
Get-FileHash .\NodalPreview-0.2.0-setup.exe -Algorithm SHA256
```

Nodal Preview installs as its own app, with its own data folder. It does not change any other Nodal install.

## First start

1. Nodal starts with **no provider set up**. Choose **Set up** on the provider you use (Codex, Claude or Ollama). Nodal looks for the program only after you choose it.
2. Nodal uses the sign-in that the program already has. It never asks for a password and stores no keys. If a program is signed out, the card says so and offers its own sign-in.
3. To bring in earlier sessions, use **Settings → Providers → Import sessions…** on a card. Nothing is imported unless you choose it. The "Add new sessions automatically" switch asks which existing sessions to add first.

## What to try

1. **Agent Mode.** Start a new session in a project folder and ask for a small change. Try each provider you have.
2. **Approvals.** Set the permission mode to **Manual** and ask for a file change. An approval card appears in the conversation.
3. **Completed turns.** A finished turn folds to "Worked for …", "Done." and the answer. Click the "Worked for" line to see the work.
4. **Review.** A turn that changes files shows a changed-files card. **Review** opens the read-only diff in the side panel; switch to **Working tree** for the project's Git changes.
5. **Side panel tabs.** Open the side panel and use **New tab** for a Terminal, a Web Browser or the File Explorer. Drag the panel edge to resize it; try **Full view**.
6. **Tab Mode.** Switch to Tab Mode and open a window with a Terminal, a Web Browser or the File Explorer.
7. **Files.** In the File Explorer, right-click a file: open text files in a side-panel text tab, HTML in the in-app or your own browser, PDFs in the in-app browser.
8. **Ollama (local).** On the Ollama card, set the context size and check **Loaded models**. The first reply of a model that is not loaded can take a minute.
9. **Claude usage.** In a Claude session, click the usage meter for the plan windows and the cost estimate of this app run.

## Known limits in this beta

- **Side chat** is not available yet.
- **Claude:** a message sent while Claude is working waits for the end of the turn (no live steering). The "Auto" and "Accept edits" modes behave the same.
- **Ollama:** only models with tool support can read or change files. One Ollama reply runs at a time by default (Settings, Providers, Ollama). Ollama drops the oldest part of a very long conversation; Nodal warns when it gets close.
- **Web Browser:** HTTP and HTTPS pages only; downloads, pop-ups and site permission requests are blocked. Browser extensions are not supported.
- The installer is unsigned (see above).

## How to report a problem

Send the owner:

1. What you did, what you expected, and what happened.
2. A screenshot, if it helps.
3. The Nodal version (0.2.0) and your Windows version.

Never send passwords, tokens, API keys, or files from `.codex`, `.claude` or other credential folders. Nodal itself sends no analytics.

## Uninstall

Windows Settings → Apps → **Nodal Preview** → Uninstall. To also remove its data, delete `%APPDATA%\Nodal Preview`. Your provider programs and their sign-ins are not changed.
