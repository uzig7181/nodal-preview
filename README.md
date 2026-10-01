# Nodal Preview

![Downloads](https://img.shields.io/github/downloads/uzig7181/nodal-preview/total)

Nodal is a Windows desktop workspace for AI coding agents and terminals. It runs **Codex (ChatGPT)**, **Claude Code** and local **Ollama** models side by side, with a tabbed side panel for terminals, a web browser, a file explorer and a read-only change review.

This repository hosts **beta builds for invited testers**. The source code is not published here.

## Download (beta 0.2.0)

Open **Releases** on the right and download `NodalPreview-0.2.0-setup.exe` (Windows 10 or 11, 64-bit).

Check the file before you run it. In PowerShell, in your Downloads folder:

```powershell
Get-FileHash .\NodalPreview-0.2.0-setup.exe -Algorithm SHA256
```

The result must be:

```
2B82D06C69B3EA3F953901BBDA255B372E1F1AC4A70CFFCBFCB3E0F5EBD04723
```

If it is different, do not run the file.

This beta is Windows only. The older 0.1.0 preview (Codex only) is still listed under Releases.

## Before you install

- **At least one provider program**, installed and signed in on this PC. Nodal uses **your own** accounts and plans and stores no passwords or keys:
  - **Codex:** `npm install -g @openai/codex` (needs Node.js), then sign in once with `codex`.
  - **Claude Code:** install Claude Code, then sign in once with `claude`. An API key works too: set `ANTHROPIC_API_KEY` for your user before you start Nodal.
  - **Ollama:** install Ollama and pull at least one model (for example `ollama pull granite4:3b`). It runs on your own PC.
- The installer is **not code-signed**. Windows SmartScreen shows "Windows protected your PC". Select **More info**, then **Run anyway**, only for a file with the correct SHA-256.
- If **Smart App Control** is On in Windows Security, Windows may block this beta. Nodal does not ask you to change that setting.

## First start

Nodal starts with **no provider set up** and adds no sessions by itself. Open the setup panel (or Settings → Providers), choose **Set up** on the provider you use, and Nodal finds the program and the sign-in you already have. Nothing is imported until you choose it.

## What to try, known limits and how to report problems

See [TESTER_GUIDE.md](TESTER_GUIDE.md). In short:

- Side chat is not in this beta yet.
- Nodal itself sends no analytics. Never send tokens, API keys or credential files in a report.

## Uninstall

Windows Settings → Apps → **Nodal Preview** → Uninstall. To also remove its data, delete `%APPDATA%\Nodal Preview`. Your Codex, Claude Code and Ollama programs and sign-ins are not changed.
