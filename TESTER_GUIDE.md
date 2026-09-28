# Nodal Preview — tester guide

Nodal is a Windows desktop workspace for AI coding agents and terminals. This is an early **preview** build. Expect rough edges. Thank you for testing it.

## Before you install

| Requirement | Detail |
|---|---|
| System | Windows 10 or 11, 64-bit; or Linux x86_64 (AppImage, see below). Not macOS. |
| Codex CLI | Install with `npm install -g @openai/codex` (needs Node.js). Sign in once with `codex` in a terminal. Nodal uses **your own** ChatGPT/OpenAI account and plan. |
| Smart App Control | If Windows Security → App & browser control → **Smart App Control** is **On**, Windows can block this unsigned preview. Nodal does not ask you to change this setting. |

The installer is **not code-signed**. Windows SmartScreen shows "Windows protected your PC". Select **More info**, then **Run anyway**, only if you downloaded the file from the official link. Compare its SHA-256 with the value on the download page:

```powershell
Get-FileHash .\NodalPreview-0.1.0-setup.exe -Algorithm SHA256
```

Nodal Preview installs as its own app. It does not change any other Nodal install.

### Linux (x86_64)

Download `NodalPreview-0.1.0-x86_64.AppImage` instead. Check it, make it executable, and run it:

```bash
sha256sum NodalPreview-0.1.0-x86_64.AppImage   # must print 164ac3315832f73f0f847aa2cd31b6512726841d641eea260879892400b12652
chmod +x NodalPreview-0.1.0-x86_64.AppImage
./NodalPreview-0.1.0-x86_64.AppImage
```

- Install the Codex CLI the same way (`npm install -g @openai/codex`, then sign in once with `codex`).
- Ubuntu 22.04 and later may need FUSE for AppImages: `sudo apt install libfuse2` (on 24.04: `libfuse2t64`).
- Settings and sessions live under `~/.config/Nodal Preview`. Terminals use your own `$SHELL`.
- The Linux build is checked by automated tests on a clean Ubuntu machine. It has not been checked by hand on every desktop; tray and window behaviour can differ between GNOME, KDE, Wayland and X11.
- This build does not run on macOS, and it does not run on ARM Linux (for example a Linux virtual machine on an Apple-chip Mac).

## What to try

1. **Agent Mode.** Start a new session in a project folder. Ask Codex for a small change.
2. **Writing preview.** While a long answer streams, open the **Writing** disclosure to watch it live.
3. **Steer and queue.** Send a second prompt while the first runs. Watch the label under it: *Steered*, *Queued*, *Sent from queue*.
4. **File cards.** Ask for a new text, HTML or image file. It appears as a card in the conversation and in the side panel's **Files** tab. Try Open, Copy path and Show in Explorer. Scripts need a separate, confirmed **Run**.
5. **Link icons.** Websites, local servers and file links show different icons.
6. **Tab Mode.** Open terminals and split the windows.
7. **Closing.** Press the title-bar X, then Alt+F4. Each asks before closing. Each "Do not ask" choice is separate and can be switched back in **Settings → Advanced → Closing Nodal**. After you confirm, watch the shutdown progress.

## Known limits in this preview

- **Codex only.** Claude and local Ollama models are not in this build.
- Side-panel **Review**, **Terminal**, **Browser** and **Side chat** tabs show "not available yet" placeholders.
- Finished turns do not collapse yet.
- Terminals start PowerShell 7 when installed; otherwise Windows PowerShell 5.1, then Command Prompt. Change it in Settings.
- NodalForge plugins are off in this build.

## Your data

Nodal keeps settings and session lists on your PC under `%APPDATA%\Nodal Preview`. It never shows or stores your provider password or token; Codex keeps its own sign-in. Nodal itself sends no analytics. Prompts go to OpenAI through your own Codex CLI, under the same terms as when you use Codex directly.

## Reporting a problem

Include:

- what you did, what you expected, and what happened;
- the Nodal Preview version (installer name) and Windows version;
- a screenshot, if you can. Remove anything private first.

**Do not** send tokens, API keys, `auth.json` or other credential files.

To uninstall: Windows Settings → Apps → **Nodal Preview** → Uninstall. To remove its data too, delete `%APPDATA%\Nodal Preview`.
