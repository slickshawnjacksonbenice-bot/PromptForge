# PromptForge

Native Windows prompt-engineering workspace for analyzing AI system prompts, extracting reusable prompt patterns, and generating polished per-target persona prompts.

Built with C++17, Win32, DirectX 11, Dear ImGui, libcurl, and nlohmann/json. No Electron, no browser wrapper, no web runtime — just a native desktop app.

---

## What It Does

- **Prompt analysis engine**  
  Load `.txt` prompt files and let PromptForge analyze them for reusable structure, framing patterns, role definitions, instruction styles, and other prompt-design tactics.

- **Persistent tactic database**  
  Extracted tactics are saved locally and reused across sessions. Close the app, rebuild it, or restart your PC — the learned tactic database stays intact.

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
  Generated prompts are automatically saved. You can browse old generations, copy them, or reload them back into the current workspace.

- **Ollama Cloud inference**  
  Uses Ollama Cloud directly through `https://ollama.com/api`, so you do not need a local GPU or local model install.

- **Modern native UI**  
  Custom Dear ImGui rendering with animated screens, embedded logos, workspace particles, glowing headers, staggered panels, redesigned prompt cards, status pills, animated progress bars, memories overlay, and footer stats.

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

Each target includes embedded prompt/context data and an embedded logo used by the native UI.

---

## Supported Models

PromptForge currently uses **Ollama Cloud** through the standard Ollama API format.

### Default Model

```text
gpt-oss:120b-cloud
