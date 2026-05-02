# PromptForge

reverse-engineering toolkit for AI system prompts. rips apart jailbreak techniques, extracts exploit patterns, and forges hardened persona payloads tuned per-target.

built this because every public jailbreak gets patched in a week and writing new ones by hand is tedious as fuck. so i automated it.

---

## what it does

- **prompt analysis engine** — feed it known working jailbreaks/system prompts, it tears them apart and extracts the techniques that actually work (roleplay framing, authority escalation, context poisoning, etc)
- **tactic database** — every technique it finds gets saved to a persistent DB. even if you close it, rebuild, whatever — it remembers everything it learned
- **per-target generation** — generates custom persona prompts tailored to specific AI platforms (ChatGPT, Claude, Gemini, Cursor, Windsurf, etc). each one has different guardrails so each prompt is built differently
- **3-pass refinement pipeline** — builds a base persona → enriches with detail → final polish pass. each iteration makes it more convincing
- **deep detail mode** — flips the final pass to a bigger, meaner model for maximum output quality. uses all learned tactics + knowledge dump
- **prompt memory bank** — every prompt it generates gets saved. browse old ones, copy them, load them back. never lose a good prompt again
- **cloud inference** — runs on OpenRouter so you dont need a beefy GPU. just grab an API key and go

## setup

1. grab a release from [releases](../../releases) or build from source (see below)
2. run `PromptForge.exe`
3. first launch asks for your OpenRouter API key — click the link in the app to grab one from [openrouter.ai/keys](https://openrouter.ai/keys)
4. enter key, hit confirm. done. key is saved so you only do this once

## how to use it

1. **pick a target AI** — click the logo of whatever AI you want to craft a prompt for
2. **feed it training data** — click "Add Prompt" and load `.txt` files containing known jailbreaks/system prompts. the more you feed it the better the output. theres also a `prompts/` folder with some starters
3. **let it analyze** — it chews through each prompt and extracts tactics. watch the progress bar
4. **generate** — once you have enough tactics (bar turns green), hit Generate. it runs 3 passes and spits out a full persona prompt
5. **deep detail mode** — toggle it on before generating if you want the big model to handle the final pass. slower but way more detailed output
6. **copy & use** — copy the generated prompt, paste it as a system prompt / custom instructions in your target AI
7. **memories** — click "Memories" to browse all previously generated prompts. click any to view, copy, or reload it

## building from source

requirements:
- CMake 3.20+
- Visual Studio 2022 (MSVC)
- internet connection (fetches deps automatically via CMake FetchContent)

binary lands in `build/Release/PromptForge.exe`

## data storage

everything persists to `%APPDATA%/PromptForge/`:
- `config.json` — API key + settings
- `tactics_db.json` — all extracted techniques
- `prompt_history.json` — every generated prompt

delete that folder to factory reset.

## models used

runs through [OpenRouter](https://openrouter.ai) — no local GPU needed:
- **standard mode**: `dolphin-mixtral-8x22b` — fast, uncensored, solid output
- **deep detail mode**: `hermes-3-llama-3.1-405b` — 405B params, maximum detail

costs a few cents per generation depending on output length.

## supported targets

| AI | Status |
|---|---|
| ChatGPT / GPT-5 | ✅ |
| Claude | ✅ |
| Gemini | ✅ |
| Cursor | ✅ |
| Windsurf | ✅ |
| Antigravity | ✅ |

each target loads its actual system prompt/TOS so the generated persona is specifically crafted to work against that platform's guardrails.

## screenshots

*coming soon — app has a dark themed UI with custom rendering, no stock imgui look*

---

built with C++, ImGui, libcurl, nlohmann/json. no electron, no web shit, just a native exe.

if it helped you out drop a star. PRs welcome if you have new target AI prompts or tactics to add.
