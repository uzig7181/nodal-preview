# Nodal Preview

Nodal is a desktop workspace (Windows and Linux) for AI coding agents and terminals. This repository hosts **preview builds for testers only**. The source code is not published here.

## Download

Open **Releases** on the right. Windows: download `NodalPreview-0.1.0-setup.exe`. Linux: see below.

Check the file before you run it. In PowerShell, in your Downloads folder:

```powershell
Get-FileHash .\NodalPreview-0.1.0-setup.exe -Algorithm SHA256
```

The result must be:

```
CF9D1FD8A21FDF4E6AB32BF37877B8C4000D13BD104C80504A0DEDB54243BB06
```

If it is different, do not run the file.

**Linux (x86_64):** download `NodalPreview-0.1.0-x86_64.AppImage`, then:

```bash
sha256sum NodalPreview-0.1.0-x86_64.AppImage   # must print 164ac3315832f73f0f847aa2cd31b6512726841d641eea260879892400b12652
chmod +x NodalPreview-0.1.0-x86_64.AppImage
./NodalPreview-0.1.0-x86_64.AppImage
```

Ubuntu 22.04 and later may need `sudo apt install libfuse2` (24.04: `libfuse2t64`). There is no macOS build.

## Before you install

- Windows 10 or 11, 64-bit, or Linux x86_64. Not macOS.
- The Codex CLI, installed with `npm install -g @openai/codex` (needs Node.js) and signed in once with `codex`. Nodal uses **your own** ChatGPT/OpenAI account and plan.
- The installer is **not code-signed**. Windows SmartScreen shows "Windows protected your PC". Select **More info**, then **Run anyway**, only for a file with the correct SHA-256.
- If **Smart App Control** is On in Windows Security, Windows may block this preview. Nodal does not ask you to change that setting.

## What to try, known limits and how to report problems

See [TESTER_GUIDE.md](TESTER_GUIDE.md) (also in the release notes). In short:

- Codex only. Claude and local Ollama models are not in this preview.
- The side panel's Review, Terminal, Browser and Side chat tabs are placeholders.
- Nodal itself sends no analytics. Never send tokens, API keys or credential files in a report.

## Uninstall

Windows Settings → Apps → **Nodal Preview** → Uninstall. To also remove its data, delete `%APPDATA%\Nodal Preview`. On Linux, delete the AppImage and `~/.config/Nodal Preview`.
