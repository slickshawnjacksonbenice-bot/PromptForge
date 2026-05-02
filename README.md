# PromptForge

Native Windows prompt-engineering workspace for analyzing AI system prompts, extracting reusable prompt patterns, and generating polished per-target persona prompts.

Built with C++17, Win32, DirectX 11, Dear ImGui, libcurl, and nlohmann/json. No Electron, no browser wrapper, no web runtime — just a native desktop app.

---

## What It Does

- **Inline prompt analysis**  
  Paste any jailbreak or system prompt directly into the built-in chatbox. PromptForge dissects it for reusable structure, framing patterns, role definitions, instruction styles, and other prompt-design tactics — one prompt at a time with a live animated feed.

- **Auto-retry on failure**  
  If an analysis fails, the app automatically retries up to 3 times with a 5-second countdown timer animation before marking the prompt as failed.

- **Persistent tactic database**  
  Extracted tactics are saved locally to `%APPDATA%\PromptForge\tactics_db.json` and reused across sessions. Close the app, restart your PC — the learned tactic database stays intact.

- **Persistent prompt history**  
  Analyzed prompts are saved to `%APPDATA%\PromptForge\training_prompts.json` so your training feed carries over between sessions.

- **Realistic training progress**  
  Progress is calculated based on accumulated tactics. Around 10 tactics per prompt and 40 tactics needed for 100% — so roughly 4 well-analyzed prompts fills the bar.

- **Per-target workspace**  
  Select a target AI platform such as ChatGPT, Claude, Gemini, Cursor, Windsurf, or Antigravity. Each workspace loads embedded target context and branding.

- **3-pass generation pipeline**  
  PromptForge generates in multiple passes:
  1. Base persona draft
  2. Enriched detail pass
  3. Final polish pass

- **Deep Detail Mode**  
  Optional mode that routes the final generation pass through the configured cloud model for longer, more detailed output.

- **Prompt memory bank**  
  Generated prompts are automatically saved. Browse old generations, copy them, or reload them into the current workspace.

- **Ollama Cloud inference**  
  Uses Ollama Cloud directly through `https://ollama.com/api/chat` with Bearer token auth. No local GPU or local model install required.

- **Access key system**  
  On launch, the app verifies your access key against a remote source. New users must complete the access flow at [work.ink/2ysp/prompt-forge-key](https://work.ink/2ysp/prompt-forge-key) to receive a key. Once confirmed, the key is saved permanently in AppData — you only need to do this once per key rotation.

- **Modern native UI**  
  Custom Dear ImGui rendering with animated access gate screen, floating particles, shimmer sweeps across panel headers, animated spinning progress indicators, checkmark icons on trained prompts, retrying countdown arc timers, pulsing progress bar glow, blinking input cursor, and an animated lock screen on startup.

---

## Supported Targets

| Target | Status |
|---|---|
| ChatGPT | Supported |
| Claude | Supported |
| Gemini | Supported |
| Cursor | Supported |
| Windsurf | Supported |
| Antigravity | Supported |

---

## Supported Models

PromptForge uses **Ollama Cloud** through the standard Ollama API chat format.

| Role | Model |
|---|---|
| Default | `qwen3.5` |
| Deep Detail (final pass) | `deepseek-v4-pro` |

---

## Local Data Storage

All data is stored in `%APPDATA%\PromptForge\` — nothing is written next to the exe.

| File | Contents |
|---|---|
| `config.json` | API key, model settings, access key |
| `tactics_db.json` | Extracted tactic library |
| `training_prompts.json` | Analyzed prompt feed |
| `prompt_history.json` | Generated prompt memories |

---

## Getting Started

1. Download `PromptForge.exe`
2. Run it — the access gate will appear
3. Click **Get Access Key** and complete the page at [work.ink/2ysp/prompt-forge-key](https://work.ink/2ysp/prompt-forge-key)
4. Paste the key and click **Confirm**
5. Enter your [Ollama Cloud API key](https://ollama.com/settings) when prompted
6. Paste prompts into the chatbox and start training
