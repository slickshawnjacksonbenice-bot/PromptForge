# PromptForge

Native Windows prompt-engineering workspace for analyzing AI system prompts, extracting reusable prompt patterns, and generating polished per-target persona prompts.

Built in C++ with Dear ImGui, DirectX 11, libcurl, and nlohmann/json. No Electron, no browser wrapper, no web runtime — just a native desktop app.

---

## What It Does

- **Prompt analysis engine**  
  Load `.txt` prompt files and let PromptForge analyze them for reusable structure, framing patterns, role definitions, instruction styles, and other prompt-design tactics.

- **Persistent tactic database**  
  Extracted tactics are saved locally and reused across sessions. Close the app, rebuild it, or restart your PC — the learned tactic database stays intact.

- **Per-target workspace**  
  Select a target AI platform such as ChatGPT, Claude, Gemini, Cursor, Windsurf, or Antigravity. Each workspace loads the relevant embedded system prompt/TOS context for that target.

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
  Custom Dear ImGui rendering with animated screens, embedded target logos, workspace particles/embers, glowing headers, staggered panel animations, redesigned training prompt cards, status pills, animated progress bars, memories overlay, and workspace footer stats.

---

## Setup

1. Download a release from [Releases](../../releases), or build from source.
2. Run `AI_Prompt_Forge.exe`.
3. On first launch, enter your Ollama Cloud API key.
4. If you need a key, click **Get API Key** in the app or visit: [https://ollama.com/settings/keys](https://ollama.com/settings/keys)
5. Hit **Confirm**. Your key is saved locally.

You can also provide the key through the environment variable:

```powershell
$env:OLLAMA_API_KEY="your_key_here"
PromptForge accepts pasted keys in plain form, Bearer ... form, or Authorization: Bearer ... form.

How To Use
Pick a target AI
Click a target logo on the main screen.
Load training prompts
Use Add Prompt to select .txt files, or Fetch Local to scan local prompt files bundled near the executable.
Let analysis run
PromptForge processes each file and updates the training feed. If cloud analysis is unavailable, prompts are still added to the list instead of breaking the workflow.
Review extracted tactics
Extracted patterns appear in the right-side workspace panel.
Generate
Once the progress bar is ready, click Generate Prompt.
Use Deep Detail Mode if needed
Toggle Deep Detail before generating for a more detailed final pass.
Copy or save output
Generated prompts appear in the output panel and are automatically saved to Memories.
Browse Memories
Click Memories to view previous generations, copy them, or load them back into the workspace.
Models Used
PromptForge currently uses Ollama Cloud.

Default model:

text
gpt-oss:120b-cloud
Deep Detail Mode also defaults to:

text
gpt-oss:120b-cloud
The client talks directly to:

text
https://ollama.com/api/generate
with Bearer authentication.

Supported Targets
Target	Status
ChatGPT	Supported
Claude	Supported
Gemini	Supported
Cursor	Supported
Windsurf	Supported
Antigravity	Supported
Each target includes embedded prompt/context data and an embedded logo used by the native UI.

Building From Source
Requirements
Windows
Visual Studio 2022 with MSVC
CMake 3.20+
Internet connection for CMake FetchContent
Dependencies
Fetched automatically by CMake:

Dear ImGui
libcurl
nlohmann/json
